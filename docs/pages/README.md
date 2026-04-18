# Dokumentasi Halaman — KuruAi

Deskripsi setiap halaman yang tersedia di KuruAi.

---

## Landing Page — `/`

Halaman utama yang dapat diakses tanpa login.

**Konten:**
- Hero section dengan animasi chat demo
- Banner iklan (carousel auto-slide)
- Section fitur unggulan (4 card)
- Preview harga subscription
- Section cara kerja (3 langkah)
- FAQ accordion
- CTA section
- Footer multi-kolom

**Fitur teknis:**
- Chat demo animasi otomatis (4 skenario bergantian)
- Dark/light mode toggle (tersimpan ke localStorage)
- Responsive mobile-first

---

## Login — `/login`

**Fields:**
- Email / Username
- Password
- Remember me (30 hari)

**Fitur:**
- Login via Google OAuth 2.0
- Auto-redirect ke `/talk/UID` setelah berhasil
- Error handling dengan pesan ramah

---

## Register — `/register`

**Fields:**
- Username (3-30 karakter, unik)
- Email (harus valid, unik)
- Password (min 6 karakter)
- Konfirmasi password

**Flow:**
1. Isi form → Submit
2. OTP dikirim via email (Brevo SMTP)
3. Verifikasi OTP (berlaku 10 menit)
4. Akun aktif → redirect ke chat

**Fitur:**
- Daftar via Google OAuth (tanpa OTP)
- Validasi real-time

---

## Chat — `/talk/{UID}`

Halaman utama aplikasi. Hanya bisa diakses oleh pemilik UID.

**Fitur sidebar:**
- Daftar sesi chat (maks 40 sesi terakhir)
- Buat sesi baru
- Rename / hapus sesi
- Badge inbox unread
- Link ke profil, settings, pricing, shop, about
- Toggle dark/light mode

**Fitur chat:**
- Kirim pesan teks
- Attach gambar untuk dianalisis AI (vision)
- Generate gambar inline (ketik `/img [deskripsi]`)
- Retry pesan terakhir
- Hapus pesan individual
- Typing indicator
- Auto-scroll ke pesan terbaru
- Markdown rendering (bold, italic, code, heading, list)

**Mode AI:**
- Chat biasa (default)
- Coding (auto-detect keyword)
- Math (auto-detect keyword)
- Roleplay (aktif jika user memulai format `*aksi*`)

---

## Pricing — `/pricing`

Halaman langganan. Wajib login.

**Konten untuk user Free:**
- 3 card tier (Free / Premium / VIP)
- Tombol upgrade untuk tier berbayar
- Info penggunaan hari ini

**Konten untuk subscriber aktif:**
- Status langganan saat ini dengan badge tier
- Tanggal kedaluwarsa
- Sisa hari
- Progress bar penggunaan
- Tombol perpanjang / upgrade

**Khusus VIP:**
- "VIP Lounge" dengan background gradient custom
- Pilihan 10 warna border profil dengan preview real-time

---

## Checkout — `/checkout?plan={plan_key}`

Halaman pembayaran 2-step. Wajib login.

**Step 1 — Pilih metode:**
- Informasi akun (email read-only, nomor HP opsional)
- Pilihan metode pembayaran:
  - E-wallet: QRIS Universal, GoPay, ShopeePay
  - Virtual Account: BCA, BNI, BRI, Mandiri Bill, Permata
- Syarat & ketentuan (collapsible)
- 2 checkbox persetujuan
- Tombol lanjut

**Step 2 — Bayar:**
- QR Code (untuk QRIS/GoPay/ShopeePay) atau Nomor VA
- Countdown timer (30 menit untuk QR, 24 jam untuk VA)
- Auto-check pembayaran setiap 6 detik
- Tombol "Sudah bayar, cek sekarang"
- Popup sukses + confetti saat terkonfirmasi

---

## Status Pembayaran — `/payment_finish?order_id={id}`

Halaman hasil setelah checkout. 3 state:

**Berhasil (paid):**
- Icon centang hijau dengan pulse ring
- Nama paket + tanggal kedaluwarsa
- Confetti animation
- Tabel detail order
- Tombol "Mulai Chat"

**Menunggu (pending):**
- Icon jam berputar kuning
- Instruksi lanjut
- Tombol "Selesaikan Pembayaran"

**Gagal (failed):**
- Icon X merah
- Tombol "Coba Lagi"

---

## Error Pembayaran — `/payment_error?reason={reason}`

Halaman khusus untuk error payment. Reason:
- `cancel` — User membatalkan
- `expire` — Waktu habis
- `deny` — Ditolak provider
- `fraud` — Terdeteksi mencurigakan
- `unknown` — Error tidak diketahui

**Konten:**
- Icon + warna sesuai severity (amber untuk cancel/expire, merah untuk deny/fraud)
- Chip reason label
- Deskripsi yang human-friendly
- 3 tips langkah selanjutnya
- Detail order (jika ada)
- Tombol coba lagi + WhatsApp admin

---

## Profil — `/profile`

Lihat profil dan statistik. Wajib login.

**Info yang ditampilkan:**
- Avatar + nama + username
- Badge tier (Free/Premium/VIP)
- Tanggal bergabung
- Statistik: total chat, gambar, sesi
- Penggunaan hari ini vs limit
- Status langganan

---

## Settings — `/settings`

Edit profil dan preferensi. Wajib login.

**Section yang tersedia:**
- **Avatar:** Upload/hapus foto profil
- **Informasi:** Nama tampilan, bio, usia (dibatasi 1x/7 hari)
- **Email:** Ganti email dengan verifikasi OTP baru
- **VIP Border:** Pilih warna border (khusus VIP)
- **Nickname AI:** Nama panggilan khusus untuk AI
- **Danger Zone:** Hapus akun permanen

---

## About — `/about`

Tentang aplikasi. Wajib login.

**Konten:**
- Hero dengan logo + versi
- Statistik live (total user, chat, gambar)
- Deskripsi aplikasi
- Grid fitur
- Daftar tier subscription
- Tech stack
- Timeline changelog (diambil dari database)
- Karakter Kurumi Tokisaki

---

## Shop — `/shop`

Toko digital. Wajib login.

Tampilan embedded webview ke URL toko eksternal (Lynk/Linktree).
URL dikonfigurasi dari admin panel.

---

## Contact — `/contact`

Halaman kontak. Bisa diakses tanpa login.

- Link WhatsApp admin
- Link Instagram
- Link toko digital

---

## Terms — `/terms`

Syarat & ketentuan layanan. Publik.

## Privacy — `/privacy`

Kebijakan privasi. Publik.

---

*Halaman admin (`/admin`) tidak didokumentasikan karena bersifat internal.*
