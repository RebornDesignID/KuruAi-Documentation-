# API Reference — KuruAi

Base URL: `https://kuruai.gt.tc/api`

Semua request membutuhkan sesi login yang valid (cookie session).
Request POST wajib menyertakan CSRF token di field `_csrf`.

---

## Autentikasi

KuruAi menggunakan session-based authentication. Login terlebih dahulu via `/login`, kemudian semua request otomatis membawa cookie session.

### Rate Limiting

| Scope | Limit |
|-------|-------|
| Global per IP | 200 req/menit |
| Chat | 30 req/menit |
| Generate gambar | 10 req/menit |
| Update profil | 10 req/5 menit |
| Ganti email | 3 req/jam |

---

## Chat

### `POST /api` — action: `chat`

Kirim pesan ke AI dan dapatkan respons streaming.

**Request:**
```
action      = "chat"
message     = string (pesan user)
session_id  = int (ID sesi chat, opsional — auto-create jika kosong)
image_data  = base64 string (opsional, untuk analisis gambar)
_csrf       = string (CSRF token)
```

**Response:** `text/event-stream` (Server-Sent Events)
```
data: {"type":"token","content":"Hei! "}
data: {"type":"token","content":"Ada yang "}
data: {"type":"done","session_id":42,"message_id":123}
```

**Error response:**
```json
{"ok": false, "error": "Limit chat harian kamu sudah habis."}
```

---

### `POST /api` — action: `new_session`

Buat sesi chat baru.

**Request:**
```
action = "new_session"
_csrf  = string
```

**Response:**
```json
{"ok": true, "session_id": 43, "title": "Chat Baru"}
```

---

### `GET /api` — action: `load_session`

Load semua pesan dari satu sesi.

**Request (query string):**
```
action     = "load_session"
session_id = int
```

**Response:**
```json
{
  "ok": true,
  "messages": [
    {"id": 1, "role": "user",      "content": "Hei!", "created_at": "2026-04-18 10:00:00"},
    {"id": 2, "role": "assistant", "content": "Hei~ Ada yang bisa aku bantu?", "created_at": "2026-04-18 10:00:01"}
  ]
}
```

---

### `POST /api` — action: `delete_session`

Hapus satu sesi beserta semua pesannya.

**Request:**
```
action     = "delete_session"
session_id = int
_csrf      = string
```

**Response:**
```json
{"ok": true}
```

---

### `POST /api` — action: `rename_session`

Ganti judul sesi chat.

**Request:**
```
action     = "rename_session"
session_id = int
title      = string (maks 60 karakter)
_csrf      = string
```

**Response:**
```json
{"ok": true}
```

---

## Generate Gambar

### `POST /api` — action: `generate_image`

Generate gambar dari deskripsi teks.

**Request:**
```
action     = "generate_image"
prompt     = string (deskripsi gambar dalam bahasa apapun)
session_id = int (opsional, untuk menyimpan ke riwayat sesi)
_csrf      = string
```

**Response:**
```json
{
  "ok": true,
  "url": "https://image.pollinations.ai/prompt/...",
  "prompt": "anime girl in forest",
  "image_id": 15
}
```

**Error (limit habis):**
```json
{"ok": false, "error": "Limit gambar harian kamu sudah habis (5/5)."}
```

---

## Profil & Akun

### `GET /api` — action: `usage`

Cek penggunaan hari ini.

**Response:**
```json
{
  "ok": true,
  "chat_used": 23,
  "chat_limit": 60,
  "img_used": 2,
  "img_limit": 5,
  "subscription": "free"
}
```

---

### `POST /api` — action: `update_profile`

Update informasi profil.

**Request:**
```
action       = "update_profile"
display_name = string (opsional, maks 60 karakter)
bio          = string (opsional, maks 300 karakter)
age          = int    (opsional, 10-99)
_csrf        = string
```

**Rate limit:** Maksimal sekali per 7 hari untuk field nama/bio/usia.

**Response:**
```json
{"ok": true, "message": "Profil berhasil diperbarui!"}
```

---

### `POST /api` — action: `upload_avatar`

Upload foto profil (via ImgBB).

**Request:**
```
action = "upload_avatar"
avatar = file (image/jpeg atau image/png, maks 2MB)
_csrf  = string
```

**Response:**
```json
{"ok": true, "avatar_url": "https://i.ibb.co/..."}
```

---

### `POST /api` — action: `update_border_color`

Ganti warna border VIP (hanya untuk subscriber VIP).

**Request:**
```
action     = "update_border_color"
border_key = string (purple|red|blue|green|gold|aurora|sunset|ocean|forest|fire)
_csrf      = string
```

**Response:**
```json
{"ok": true}
```

---

## Inbox

### `GET /api` — action: `get_inbox`

Ambil semua pesan inbox user.

**Response:**
```json
{
  "ok": true,
  "messages": [
    {
      "id": 5,
      "subject": "Selamat datang di KuruAi!",
      "body": "Hai~ Selamat bergabung...",
      "is_read": 0,
      "created_at": "2026-04-18 09:00:00"
    }
  ],
  "unread_count": 1
}
```

---

### `GET /api` — action: `inbox_unread_count`

Cek jumlah pesan belum dibaca (untuk badge notifikasi).

**Response:**
```json
{"ok": true, "count": 3}
```

---

### `POST /api` — action: `mark_inbox_read`

Tandai pesan inbox sebagai sudah dibaca.

**Request:**
```
action     = "mark_inbox_read"
message_id = int (atau "all" untuk tandai semua)
_csrf      = string
```

**Response:**
```json
{"ok": true}
```

---

## Kode Error Umum

| Kode | Arti |
|------|------|
| `401` | Belum login |
| `403` | CSRF token tidak valid |
| `429` | Rate limit terlampaui |
| `500` | Kesalahan server |

```json
{"ok": false, "error": "Pesan error dalam bahasa Indonesia"}
```

---

## Webhook Midtrans

### `POST /payment_callback`

Diterima otomatis dari Midtrans setelah pembayaran berhasil/gagal.
Tidak perlu dipanggil manual.

**Verifikasi signature:**
```
SHA512(order_id + status_code + gross_amount + server_key)
```

**Status yang ditangani:**
- `capture` + `fraud_status: accept` → Aktifkan langganan
- `settlement` → Aktifkan langganan
- `deny` / `cancel` / `expire` / `failure` → Tandai order gagal

---

*Dokumentasi ini hanya mencakup endpoint publik. Endpoint admin tidak didokumentasikan.*
