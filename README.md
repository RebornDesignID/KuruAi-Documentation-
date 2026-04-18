# KuruAi Dokumentasi Publik

<div align="center">
  <img src="https://kuruai.gt.tc/assets/kurumi.png" width="120" height="120" style="border-radius:20px; box-shadow: 0 4px 8px rgba(0,0,0,0.2);" alt="KuruAi Logo">
  <h3>🚀 Platform AI Chat Berbahasa Indonesia</h3>
  <p><i>Chat Cerdas · Generasi Gambar · Roleplay Kreatif · PWA Ready</i></p>

  <a href="https://kuruai.gt.tc">
    <img src="https://img.shields.io/badge/Website-kuruai.gt.tc-7C3AED?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Website">
  </a>
  <a href="mailto:owner.rillku@gmail.com">
    <img src="https://img.shields.io/badge/Email-Business-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
  </a>
  <a href="https://teer.id/riel_akuonza">
    <img src="https://img.shields.io/badge/Support-Trakteer-FF5E5B?style=for-the-badge&logo=trakteer&logoColor=white" alt="Trakteer">
  </a>

  <br>

  [![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?style=flat-square&logo=php&logoColor=white)](https://php.net)
  [![MySQL](https://img.shields.io/badge/MySQL-5.7+-4479A1?style=flat-square&logo=mysql&logoColor=white)](https://mysql.com)
  [![PWA](https://img.shields.io/badge/PWA-Ready-5A0FC8?style=flat-square)](https://web.dev/progressive-web-apps/)
  [![License](https://img.shields.io/badge/License-Proprietary-orange?style=flat-square)](https://kuruai.gt.tc)
</div>

---

## 📖 Tentang KuruAi

**KuruAi** adalah platform asisten AI berbasis web yang dirancang khusus untuk pengguna Indonesia. Dibangun dengan PHP murni (*Native*) tanpa framework untuk performa yang optimal, KuruAi menghadirkan pengalaman interaksi AI yang natural melalui persona **Kurumi Tokisaki** yang elegan, adaptif, dan responsif.

* **🌐 Website:** [https://kuruai.gt.tc](https://kuruai.gt.tc)
* **👨‍💻 Developer:** [Riel Akuonza](https://lynk.id/rielakuonza)
* **🎯 Status:** v2.0.0 (Production)
* **🇮🇩 Bahasa:** Full Bahasa Indonesia

---

## ✨ Fitur Unggulan

### 🤖 AI Chat & Roleplay
- Interaksi natural dengan karakter Kurumi Tokisaki.
- Mendukung coding, matematika, analisis data, hingga roleplay kreatif.
- **Multi-Sesi:** Riwayat chat tersimpan rapi per sesi.
- **Auto-Fallback:** Peralihan model AI otomatis jika terjadi gangguan pada server utama.

### 🎨 AI Image Generation
- Integrasi **Pollinations.ai** untuk pembuatan gambar dari teks.
- Berbagai pilihan style (Flux Realism, Flux, dll).
- Generate gambar langsung di dalam jendela chat.

### 💳 Ekosistem Pembayaran & Akun
- **Manajemen Akun:** Login Google OAuth 2.0 & OTP Email.
- **Payment Gateway:** Integrasi **Midtrans Core API** (QRIS, VA, E-Wallet).
- **VIP Customization:** 10 pilihan warna border profil eksklusif untuk member VIP.

### 📱 Pengalaman Pengguna (UX)
- **PWA Ready:** Instal di Android/iOS layaknya aplikasi native.
- **Web Push Notification:** Pemberitahuan real-time untuk inbox dan promo.
- **Dark/Light Mode:** Antarmuka yang nyaman di mata kapan saja.

---

## 🛠️ Stack Teknologi

| Komponen | Teknologi |
| :--- | :--- |
| **Backend** | PHP 8.1+ (Pure/Native) |
| **Database** | MySQL 5.7+ (PDO) |
| **Frontend** | Vanilla JS, CSS Variables, Tailwind-like styling |
| **AI Engine** | Groq API (LLaMA 3.1) & Pollinations.ai |
| **Payment** | Midtrans Core API |
| **Email** | Brevo SMTP |
| **Push Notif** | Web Push API + VAPID |

---

## 💎 Subscription Tiers

| Fitur | Free | Premium | VIP |
| :--- | :--- | :--- | :--- |
| **Harga** | Gratis | Rp 12.000 | Rp 35.000 |
| **Durasi** | Selamanya | 30 Hari | 90 Hari |
| **Limit Chat** | 60 Pesan/Hari | 120 Pesan/Hari | **Tanpa Batas** |
| **Limit Gambar** | 5 Gambar/Hari | 20 Gambar/Hari | **Tanpa Batas** |
| **Badge** | - | 💎 Premium | 👑 VIP |
| **AI Priority** | Normal | Tinggi | Prioritas Utama |

---

## 📧 Kontak & Dukungan

Kami sangat terbuka untuk kerjasama, sponsor, maupun laporan bug untuk pengembangan KuruAi ke arah yang lebih baik.

* **Kerjasama Bisnis & Sponsor:** [owner.rillku@gmail.com](mailto:owner.rillku@gmail.com)
* **Donasi Pengembangan:** [Trakteer (riel_akuonza)](https://teer.id/riel_akuonza)
* **Socials:** [Lynk.id Riel Akuonza](https://lynk.id/rielakuonza)

---

## 📂 Struktur Proyek Singkat

```text
KuruAI/
├── assets/          # Media, Ikon, & CSS
├── data/            # Logika Backend (AI Handlers, Database)
├── includes/        # Komponen UI (Header, Sidebar, Footer)
├── api/             # Endpoint API untuk Chat & User
├── manifest.json    # Konfigurasi PWA
└── sw.js            # Service Worker untuk Offline Mode
```
<div align="center">
<p>Dibuat dengan ❤️ oleh <b>Riel Akuonza</b></p>
<p><i>© 2026 KuruAi. Seluruh hak cipta dilindungi.</i></p>
</div>

### Perubahan yang saya lakukan:

1.  **Badges:** Menambahkan badge untuk Website, Email, dan Trakteer di bagian atas agar terlihat profesional.
2.  **Highlight Kontak:** Menambahkan section khusus **"Kontak & Dukungan"** agar sponsor atau donatur mudah menemukan informasi tersebut.
3.  **Layouting:** Menggunakan tabel dan ikon (emojis) agar dokumentasi lebih mudah dibaca (scannable).
4.  **CTA (Call to Action):** Memperjelas link website dan link donasi di bagian awal dan akhir.
5.  **Visual:** Menambahkan bayangan (shadow) dan radius pada logo agar terlihat lebih estetis di halaman GitHub/Readme.
