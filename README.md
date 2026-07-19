# 🛡️ masifa-ipblacklist - Hybrid IP Blacklist for MikroTik

[![Automated Sync](https://shields.io)](https://github.com)
[![MikroTik RouterOS](https://shields.io)](https://mikrotik.com)
[![License](https://shields.io)](LICENSE)

**masifa-ipblacklist** adalah proyek otomatisasi keamanan siber (*Cybersecurity*) yang dirancang khusus untuk melindungi router **MikroTik** dari berbagai serangan siber global seperti Bruteforce, Port Scanning, Web Attack, Malicious Bot, dan Spam.

Data IP dalam repositori ini diekstraksi secara *real-time* langsung dari database firewall MikroTik produksi yang terintegrasi dengan 3 intelijen ancaman dunia: **AbuseIPDB**, **Spamhaus**, dan **IPSum**.

---

## 🚀 Fitur Unggulan

* **Multi-Sumber Intelijen:** Gabungan otomatis dari ancaman paling aktif di internet.
* **Proteksi Jalur Tol (Bypass CDN):** Seluruh IP resmi **Cloudflare (IPv4 & IPv6)** telah disaring secara matematis agar website Anda terhindar dari *False Positive* (Error 521).
* **Performa Tinggi (Hemat CPU):** Dioptimalkan untuk langsung diaplikasikan pada **Firewall Raw Prerouting** MikroTik.
* **Pembaruan Berkala:** Sinkronisasi otomatis setiap **24 jam sekali**.

---

## 💾 Tautan Unduhan Langsung (Raw Txt)

Bagi sesama teknisi jaringan atau sysadmin, Anda dapat mengambil daftar IP mentah (*clean text*) yang selalu diperbarui untuk skrip otomatisasi Anda melalui tautan berikut:

👉 **[Download Raw Blocklist](https://raw.githubusercontent.com/fwahyui/masifa-ipblacklist/refs/heads/main/blocklist.txt)**

---

## 🛠️ Cara Implementasi di MikroTik RouterOS v7

Untuk performa paling optimal dan hemat beban CPU, sangat disarankan untuk memasukkan daftar ini ke dalam menu **Firewall Raw**. 

### 1. Ambil Data Menggunakan Script MikroTik
Buka **New Terminal** di Winbox Anda, lalu buat skrip otomatis untuk mengunduh daftar ini:

```mikrotik
/system script
add name=Download_Masifa_Blacklist source={
    /tool fetch url="[https://githubusercontent.com](https://raw.githubusercontent.com/fwahyui/masifa-ipblacklist/refs/heads/main/blocklist.txt)" mode=https dst-path=blocklist.txt
    # Tambahkan logika parsing lokal Anda di sini jika diperlukan
}
```

### 2. Aturan Blokir di Firewall Raw (Wajib)
Jalankan perintah ini agar MikroTik langsung membuang paket dari penyerang di lapisan paling awal sebelum membebani *Connection Tracking*:

```mikrotik
/ip firewall raw
add chain=prerouting src-address-list=IP_Wajib_Blokir action=drop comment="DROP IP WAJIB BLOKIR - MASIFA HYBRID BLOCKLIST"
```

---

## ☕ Dukung Proyek Ini (Donasi & Kemitraan)

Proyek ini dikembangkan dan dikelola secara mandiri demi keamanan komunitas internet di Indonesia. Jika proyek ini berhasil mengamankan server atau router perusahaan Anda dari serangan siber, Anda dapat memberikan dukungan via:

* **Trakteer / Saweria:** `[Masukkan Link Saweria/Trakteer Anda di Sini]`
* **GitHub Sponsors:** Aktif di profil GitHub ini.

### 💼 Layanan Konsultasi & Jasa Privat (Kompersil)
Jika Anda membutuhkan bantuan profesional untuk:
* Instalasi skrip otomatisasi integrasi aaPanel/Linux ke MikroTik CHR.
* Hardening keamanan router MikroTik perusahaan/ISP.
* Konfigurasi jaringan tingkat lanjut (*Routing*, BGP, QoS Traffic Shaping).

Silakan hubungi saya secara komersial melalui **Email Bisnis:** `admin@masifa.ocm`

---
*Dibuat dengan 💻 dan dikelola dengan penuh dedikasi dari Indonesia.*
