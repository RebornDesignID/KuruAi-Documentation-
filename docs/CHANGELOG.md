# Changelog — KuruAi

Semua perubahan signifikan pada KuruAi dicatat di sini.
Format mengikuti [Keep a Changelog](https://keepachangelog.com/).

---

## [2.0.0] — April 2026

### Added
- Halaman **Settings** terpisah dari Profile
  - Upload/ganti/hapus avatar
  - Edit info profil dengan rate limit 1x/7 hari
  - Ganti email dengan verifikasi OTP
  - Pilih warna VIP border (10 pilihan)
  - Nickname khusus untuk AI
  - Hapus akun
- **PWA (Progressive Web App)** lengkap
  - `manifest.json` dengan shortcut ke Chat dan Pricing
  - Service Worker dengan offline caching & push notification
  - Halaman `offline.html` dengan auto-reload saat koneksi kembali
- **Meta OG tags** lengkap di semua halaman (WhatsApp/Telegram preview)
- **Dark/light mode** dynamic theme-color
- Tabel `user_meta` di database untuk menyimpan preferensi user
- File `config.example.php` sebagai template konfigurasi
- **Redesign halaman payment:**
  - Checkout: card bersih, animasi halus, step indicator
  - Payment Finish: confetti burst saat sukses, pulse ring animasi
  - Payment Error: tips langkah selanjutnya, severity color coding

### Changed
- Migrasi payment gateway dari **Duitku** ke **Midtrans Core API**
  - Support QRIS, GoPay, ShopeePay, BCA/BNI/BRI/Mandiri/Permata VA
  - Webhook callback untuk auto-aktivasi
- Font **Sora** ditambahkan untuk halaman payment
- `.gitignore` diperbarui (tambah `data/db.php`, `*.bak`, `.env`)

### Fixed
- Bug `check_payment` di checkout: URL tidak menyertakan `&plan=`
- Theme-color meta tag sekarang dynamic (ungu light, dark untuk dark mode)

---

## [1.5.0] — Maret 2026

### Added
- **Google OAuth 2.0** untuk login dan registrasi
- **Multi-model AI** dengan fallback otomatis antar provider
  - Groq API (LLaMA 3.1) — primary
  - OpenRouter — fallback 1
  - Google AI Studio — fallback 2
  - Cloudflare Workers AI — fallback 3
- **Web Push Notification** via VAPID
  - Push notif untuk inbox baru dan promo
  - Badge counter real-time di sidebar
- **Admin Panel** fitur baru:
  - Manajemen paket subscription (CRUD)
  - Broadcast inbox ke semua user
  - Push notification ke tier tertentu
  - Riwayat order & konfirmasi manual
  - Changelog management
- **VIP Lounge** di halaman Pricing dengan 10 pilihan border
- Retry pesan terakhir di chat
- Hapus pesan individual

### Changed
- Sidebar diperbarui dengan badge unread count
- Pricing page redesign untuk subscriber aktif

---

## [1.2.0] — Februari 2026

### Added
- **Generate gambar inline** di chat (command `/img`)
- Analisis gambar (upload foto untuk dianalisis AI)
- Riwayat gambar di profil
- Limit penggunaan berdasarkan tier dari database (bukan hardcoded)
- Rate limiting per endpoint di `api.php`

### Changed
- Model registry dipindah ke `data/app/model_plans.php`
- Sistem limit chat dan gambar sekarang dari tabel `subscription_plans`

---

## [1.1.0] — Januari 2026

### Added
- **OTP email verifikasi** saat registrasi (via Brevo SMTP)
- **Remember me** cookie (30 hari)
- Inbox internal untuk pesan dari admin
- Multi-sesi chat (maks 40 sesi)
- Rename & hapus sesi

### Fixed
- Session handling lebih aman dengan `session_regenerate_id`
- CSRF protection di semua form POST

---

## [1.0.0] — Desember 2025

### Added
- Rilis awal KuruAi
- Chat AI dengan karakter Kurumi Tokisaki
- Sistem subscription Free / Premium / VIP
- Dark mode
- Profil user dengan avatar
- Landing page dengan FAQ dan pricing
- Admin panel dasar

---

*Untuk detail teknis lebih lanjut, lihat commit history di repository.*
