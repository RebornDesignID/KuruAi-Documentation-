# KuruAi Dokumentasi Publik

<div align="center">
  <img src="https://kuruai.gt.tc/assets/kurumi.png" width="100" height="100" style="border-radius:16px" alt="KuruAi Logo">
  <h3>Platform AI Chat berbahasa Indonesia</h3>
  <p>Chat cerdas · Generasi gambar · Roleplay kreatif · Subscription tiers</p>

  [![Website](https://img.shields.io/badge/Website-kuruai.gt.tc-7C3AED?style=flat-square)](https://kuruai.gt.tc)
  [![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?style=flat-square&logo=php)](https://php.net)
  [![MySQL](https://img.shields.io/badge/MySQL-5.7+-4479A1?style=flat-square&logo=mysql)](https://mysql.com)
  [![PWA](https://img.shields.io/badge/PWA-Ready-5A0FC8?style=flat-square)](https://web.dev/progressive-web-apps/)
</div>

---

## 📖 Daftar Isi

- [Tentang KuruAi](#tentang-kurulai)
- [Fitur](#fitur)
- [Teknologi](#teknologi)
- [Halaman & Fitur](#halaman--fitur)
- [Subscription Tiers](#subscription-tiers)
- [API Endpoint](#api-endpoint)
- [Struktur Folder](#struktur-folder)
- [Changelog](#changelog)

---

## Tentang KuruAi

KuruAi adalah platform asisten AI berbasis web untuk pengguna Indonesia. Dibangun dengan PHP murni tanpa framework, KuruAi menghadirkan pengalaman chat AI yang natural dengan karakter **Kurumi Tokisaki** — elegan, adaptif, dan menyenangkan.

**Dibuat oleh:** [Riel Akuonza](https://lynk.id/rielakuonza)
**Versi saat ini:** 2.0.0
**Bahasa utama:** Indonesia 🇮🇩

---

## Fitur

### 🤖 AI Chat
- Chat natural berbahasa Indonesia dengan karakter Kurumi
- Mendukung roleplay, coding, matematika, dan analisis umum
- Multi-sesi — riwayat chat tersimpan per sesi
- Fallback otomatis antar model AI jika satu gagal

### 🎨 Generasi Gambar
- Text-to-image menggunakan Pollinations.ai
- Mendukung style: flux-realism, flux, dan lainnya
- Inline generation langsung di chat

### 👤 Manajemen Akun
- Registrasi & login dengan email + OTP verifikasi
- Login via Google OAuth 2.0
- Upload & ganti avatar (via ImgBB)
- VIP border profil dengan 10 pilihan warna

### 💳 Pembayaran
- Integrasi Midtrans Core API
- Metode: QRIS, GoPay, ShopeePay, BCA/BNI/BRI/Mandiri/Permata VA
- Auto-aktivasi setelah pembayaran terkonfirmasi
- Webhook callback untuk real-time update

### 📱 PWA (Progressive Web App)
- Bisa diinstall di HP seperti app native
- Offline fallback page
- Push notification untuk inbox & promo
- Service Worker caching aset statis

### 🔔 Notifikasi & Inbox
- Web Push Notification
- Inbox internal (pesan dari admin)
- Badge counter real-time di sidebar
- Toast notification untuk pesan baru

---

## Teknologi

| Layer | Teknologi |
|-------|-----------|
| Backend | PHP 8.1+ (no framework) |
| Database | MySQL 5.7+ via PDO |
| Frontend | Vanilla JS + CSS Variables |
| Font | Plus Jakarta Sans + DM Sans + JetBrains Mono + Sora |
| AI Chat | Groq API (LLaMA 3.1) |
| AI Gambar | Pollinations.ai |
| Payment | Midtrans Core API |
| Email | Brevo SMTP |
| Avatar | ImgBB API |
| Auth Sosial | Google OAuth 2.0 |
| Push Notif | Web Push API + VAPID |
| Hosting Demo | InfinityFree |

---

## Halaman & Fitur

Lihat dokumentasi detail di folder [`docs/pages/`](docs/pages/):

| Halaman | URL | Deskripsi |
|---------|-----|-----------|
| Landing | `/` | Halaman utama dengan hero, fitur, harga, FAQ |
| Login | `/login` | Login email + Google OAuth |
| Register | `/register` | Daftar akun baru + Google OAuth |
| Chat | `/talk/UID` | Antarmuka chat utama |
| Pricing | `/pricing` | Halaman langganan & upgrade |
| Checkout | `/checkout` | Pembayaran Midtrans |
| Profile | `/profile` | Lihat profil & statistik |
| Settings | `/settings` | Edit profil, avatar, VIP border |
| About | `/about` | Tentang app + changelog |
| Shop | `/shop` | Toko digital |

---

## Subscription Tiers

| | Free | Premium | VIP |
|-|------|---------|-----|
| **Harga** | Gratis | Rp 12.000 | Rp 35.000 |
| **Durasi** | Selamanya | 30 hari | 90 hari |
| **Chat/hari** | 60 pesan | 120 pesan | Tidak terbatas |
| **Gambar/hari** | 5 gambar | 20 gambar | Tidak terbatas |
| **Border profil** | ✗ | Ungu glowing | 10 pilihan warna |
| **Badge profil** | ✗ | 💎 Premium | 👑 VIP |
| **Prioritas AI** | Normal | Lebih cepat | Tertinggi |

---

## API Endpoint

Lihat dokumentasi lengkap di [`docs/api/`](docs/api/):

Semua request ke `/api` menggunakan `POST` dengan `Content-Type: multipart/form-data`.
CSRF token wajib disertakan di semua request POST (kecuali yang dikecualikan).

### Endpoint Publik (butuh login)

| Action | Method | Deskripsi |
|--------|--------|-----------|
| `chat` | POST | Kirim pesan chat |
| `new_session` | POST | Buat sesi chat baru |
| `load_session` | GET | Load pesan sesi tertentu |
| `delete_session` | POST | Hapus sesi chat |
| `rename_session` | POST | Rename judul sesi |
| `generate_image` | POST | Generate gambar dari teks |
| `usage` | GET | Cek penggunaan hari ini |
| `update_profile` | POST | Update nama/bio/usia |
| `upload_avatar` | POST | Upload foto profil |
| `delete_avatar` | POST | Hapus foto profil |
| `change_email` | POST | Ganti email (butuh verifikasi) |
| `delete_account` | POST | Hapus akun permanen |
| `update_border_color` | POST | Ganti border VIP |
| `get_inbox` | GET | Ambil pesan inbox |
| `mark_inbox_read` | POST | Tandai pesan sebagai dibaca |
| `save_nickname` | POST | Simpan nickname untuk AI |

---

## Struktur Folder

```
KuruAI/
├── assets/              # Aset publik (gambar, ikon)
├── data/                # Backend PHP (diproteksi)
│   └── app/             # AI handlers & model registry
├── includes/            # Komponen UI reusable
├── manifest.json        # PWA manifest
├── sw.js                # Service Worker
└── offline.html         # Halaman offline
```

> Kode sumber lengkap tersedia di repository private.
> Untuk kolaborasi atau lisensi, hubungi [Riel Akuonza](https://lynk.id/rielakuonza).

---

## Changelog

Lihat [`docs/CHANGELOG.md`](docs/CHANGELOG.md) untuk riwayat perubahan lengkap.

### v2.0.0 (April 2026)
- Migrasi payment gateway dari Duitku ke **Midtrans Core API**
- Tambah halaman **Settings** terpisah dari Profile
- Redesign halaman payment (checkout, finish, error)
- PWA lengkap: manifest + service worker + offline page
- Meta OG tags untuk preview link di WhatsApp/Telegram
- Tambah tabel `user_meta` di database schema
- Dark/light mode toggle (default: light)

### v1.5.0
- Integrasi Google OAuth 2.0
- Multi-model AI dengan fallback otomatis
- Web Push Notification
- Admin panel dengan manajemen paket, user, dan changelog

### v1.0.0
- Rilis awal KuruAi
- Chat AI dengan karakter Kurumi
- Sistem subscription Free/Premium/VIP

---

<div align="center">
  <p>Dibuat dengan ♥ oleh <a href="https://lynk.id/rielakuonza">Riel Akuonza</a></p>
  <p><em>© 2026 KuruAi. Seluruh hak cipta dilindungi.</em></p>
</div>
