# KuruAi Dokumentasi Publik

<div align="center">
  <img src="https://kuruai.gt.tc/assets/kurumi.png" width="100" height="100" style="border-radius:16px" alt="KuruAi Logo">
  <h3>Platform AI Chat Berbahasa Indonesia</h3>
  <p>Chat cerdas · Generasi gambar · Roleplay kreatif · Subscription tiers</p>

  [![Website](https://img.shields.io/badge/Website-kuruai.gt.tc-7C3AED?style=flat-square)](https://kuruai.gt.tc)
  [![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?style=flat-square&logo=php)](https://php.net)
  [![MySQL](https://img.shields.io/badge/MySQL-5.7+-4479A1?style=flat-square&logo=mysql)](https://mysql.com)
  [![PWA](https://img.shields.io/badge/PWA-Ready-5A0FC8?style=flat-square)](https://web.dev/progressive-web-apps/)
</div>

---

## 🌐 Live Website  
👉 https://kuruai.gt.tc  

---

## 📖 Daftar Isi

- [Tentang KuruAi](#tentang-kuruai)
- [Fitur](#fitur)
- [Teknologi](#teknologi)
- [Halaman & Fitur](#halaman--fitur)
- [Subscription Tiers](#subscription-tiers)
- [API Endpoint](#api-endpoint)
- [Struktur Folder](#struktur-folder)
- [Dukungan & Kolaborasi](#dukungan--kolaborasi)
- [Changelog](#changelog)

---

## Tentang KuruAi

**KuruAi** adalah platform asisten AI berbasis web yang dirancang khusus untuk pengguna Indonesia.  
Dibangun tanpa framework, fokus pada performa, efisiensi, dan pengalaman chat yang terasa hidup.

Karakter utama terinspirasi dari **Kurumi Tokisaki** — elegan, adaptif, dan interaktif.

- **Versi:** 2.0.0  
- **Bahasa utama:** Indonesia 🇮🇩  

👤 **Developer:**  
[Riel Akuonza](https://linktr.ee/rielakuonza)

---

## Fitur

### 🤖 AI Chat
- Chat natural bahasa Indonesia
- Support roleplay, coding, matematika, analisis
- Multi-session chat (riwayat tersimpan)
- Auto fallback model AI

### 🎨 Generasi Gambar
- Text-to-image (Pollinations.ai)
- Support berbagai style
- Generate langsung di chat

### 👤 Manajemen Akun
- Login email + OTP
- Google OAuth 2.0
- Upload avatar (ImgBB)
- Custom VIP border

### 💳 Pembayaran
- Midtrans Core API
- QRIS, E-Wallet, Virtual Account
- Auto aktivasi + webhook real-time

### 📱 PWA
- Install seperti aplikasi
- Offline support
- Push notification
- Caching asset

### 🔔 Notifikasi
- Web Push Notification
- Inbox internal
- Real-time badge & toast

---

## Teknologi

| Layer | Teknologi |
|-------|-----------|
| Backend | PHP 8.1+ (No Framework) |
| Database | MySQL 5.7+ (PDO) |
| Frontend | Vanilla JS + CSS |
| AI Chat | Groq API (LLaMA 3.1) |
| AI Gambar | Pollinations.ai |
| Payment | Midtrans |
| Email | Brevo SMTP |
| Auth | Google OAuth 2.0 |
| Hosting | InfinityFree |

---

## Halaman & Fitur

| Halaman | URL | Deskripsi |
|---------|-----|-----------|
| Landing | `/` | Halaman utama |
| Login | `/login` | Login user |
| Register | `/register` | Daftar akun |
| Chat | `/talk/UID` | Chat AI |
| Pricing | `/pricing` | Paket langganan |
| Checkout | `/checkout` | Pembayaran |
| Profile | `/profile` | Profil user |
| Settings | `/settings` | Pengaturan akun |
| Shop | `/shop` | Toko digital |

---

## Subscription Tiers

| | Free | Premium | VIP |
|-|------|---------|-----|
| Harga | Gratis | Rp 12.000 | Rp 35.000 |
| Durasi | Selamanya | 30 hari | 90 hari |
| Chat | 60/hari | 120/hari | Unlimited |
| Gambar | 5/hari | 20/hari | Unlimited |
| Badge | ✗ | 💎 | 👑 |
| Prioritas | Normal | Tinggi | Maksimal |

---

## API Endpoint

Semua endpoint berada di `/api` dan menggunakan `POST`.

Contoh fitur API:
- Chat AI
- Generate gambar
- Manajemen sesi
- Update profil
- Inbox system

📂 Detail lengkap: `docs/api/`

---

## Struktur Folder
KuruAI/
├── assets/
├── data/
│ └── app/
├── includes/
├── manifest.json
├── sw.js
└── offline.html


---

## 🤝 Dukungan & Kolaborasi

KuruAi terbuka untuk kerja sama, sponsor, maupun pengembangan lebih lanjut.

### 📩 Kontak Bisnis
📧 owner.rillku@gmail.com  

### 💖 Donasi (Support Development)
👉 https://teer.id/riel_akuonza  

---

## Changelog

### v2.0.0 (April 2026)
- Migrasi ke Midtrans
- Redesign UI payment
- PWA full support
- Dark/Light mode
- Struktur database baru

### v1.5.0
- Google OAuth
- Multi-model AI
- Push notification

### v1.0.0
- Initial release

---

<div align="center">
  <p><strong>KuruAi</strong> — Build simple, think big.</p>
  <p>Dibuat oleh <a href="https://linktr.ee/rielakuonza">Riel Akuonza</a></p>
  <p><em>© 2026 All rights reserved</em></p>
</div>
