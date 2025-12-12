# GSG-Reporting

<p align="center">
  <strong>Sistem Pelaporan Shift & Loading untuk Operasional Pengantongan Pupuk</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Laravel-12-red?style=flat-square&logo=laravel" alt="Laravel">
  <img src="https://img.shields.io/badge/Livewire-3-pink?style=flat-square" alt="Livewire">
  <img src="https://img.shields.io/badge/PHP-8.3-blue?style=flat-square&logo=php" alt="PHP">
  <img src="https://img.shields.io/badge/Bootstrap-5-7952B3?style=flat-square&logo=bootstrap" alt="Bootstrap">
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white" alt="MySQL">
</p>

---

## 📋 Tentang Aplikasi

**GSG-Reporting** adalah aplikasi web untuk mengelola dan memantau aktivitas kerja shift, pencatatan loading (pengangkutan), dokumentasi foto, serta pelaporan produksi pada operasional pengantongan pupuk. Aplikasi ini memudahkan pengawas, admin, dan tim monitoring dalam melakukan pelaporan harian secara real-time.

## ✨ Fitur Utama

### Manajemen Shift & Kerja

-   🔐 **Multi-Role Authentication** - Admin, Pengawas, Monitoring
-   📍 **Manajemen Lokasi** - Kelola lokasi kerja (Gipsum, Kaptan, NCG)
-   ⏰ **Manajemen Shift** - 3 Shift kerja (Pagi/Siang/Malam) dengan dukungan overnight shift
-   📊 **Dashboard Real-time** - Pantau status shift dan loading secara langsung
-   🎯 **Pemilihan Shift Otomatis** - Deteksi shift berdasarkan jam kerja saat ini

### Pencatatan & Dokumentasi

-   🚛 **Pencatatan Loading (Muat)** - Input Plat Nomor, Tonase, dan foto bukti muat
-   📸 **Foto Sample** - Upload foto timbang dan foto kadar air
-   🏭 **Foto Aktifitas** - Dokumentasi aktivitas Gipsum, Kaptan, dan NCG
-   📦 **Manajemen OLT/OKT** - Input pengurangan bag (OLT) dan tambahan bag (OKT)
-   ✏️ **Edit Data Muat** - Koreksi data muat yang sudah diinput

### Pelaporan & Monitoring

-   📈 **Live Report** - Lihat data real-time per shift
-   📅 **History Schedule** - Riwayat jadwal shift yang sudah selesai
-   📋 **Monitoring Data** - Pantau semua data per lokasi dan tanggal
-   📊 **My Report** - Laporan pribadi pengawas
-   🔔 **Notifikasi Toastr** - Feedback real-time untuk setiap aksi

### Fitur Produksi

-   🏭 **Hasil Produksi** - Input dan update hasil produksi per shift
-   📦 **Stok Management** - Tracking stok awal dan stok akhir
-   💼 **Bag Damage & Dump** - Pencatatan bag rusak dan dump
-   ⏱️ **Tombol Tutup Shift** - Aktif 1 jam sebelum waktu berakhir shift

## 🛠️ Tech Stack

| Komponen  | Teknologi                               |
| --------- | --------------------------------------- |
| Framework | Laravel 12                              |
| PHP       | 8.3+                                    |
| Frontend  | Livewire v3, Bootstrap 5, AdminUIUX     |
| Database  | MySQL / SQLite                          |
| JS Libs   | jQuery, SweetAlert2, Toastr, DataTables |
| Icons     | Bootstrap Icons                         |

## 🚀 Instalasi

### Persyaratan

-   PHP >= 8.3
-   Composer
-   Node.js & NPM (optional)
-   MySQL / SQLite

### Langkah Instalasi

```bash
# Clone repository
git clone <repository-url> GSG-Reporting
cd GSG-Reporting

# Install dependencies
composer install
npm install

# Setup environment
cp .env.example .env
php artisan key:generate

# Konfigurasi database di .env
# DB_CONNECTION=mysql
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=gsg_reporting
# DB_USERNAME=root
# DB_PASSWORD=

# Database migration & seeding
php artisan migrate
php artisan db:seed  # (opsional)

# Link storage untuk foto
php artisan storage:link

# Build assets (jika menggunakan vite)
npm run build

# Jalankan server
php artisan serve
```

## 💻 Development

```bash
# Jalankan Laravel server
php artisan serve

# Optimize aplikasi
php artisan optimize

# Clear cache
php artisan cache:clear
php artisan view:clear
php artisan config:clear
```

## 👥 User Roles

| Role           | Akses                                                                           |
| -------------- | ------------------------------------------------------------------------------- |
| **Admin**      | Full access - Dashboard, Reporting, Setting (User, Location, Shift), Monitoring |
| **Pengawas**   | Dashboard, Foto/Muat Input, My Report, History Schedule, Profile                |
| **Monitoring** | Dashboard (View Only), Reporting Management, History Schedule, Monitoring Data  |

## 📁 Struktur Proyek

```
GSG-Reporting/
├── app/
│   ├── Http/Controllers/      # API Controllers (ReportController)
│   ├── Livewire/              # Komponen Livewire
│   │   ├── Auth/              # Login
│   │   ├── Inc/               # Navbar, Sidebar, NavBottom
│   │   ├── Dashboard.php      # Dashboard utama (82KB)
│   │   ├── *Management.php    # CRUD modules
│   │   └── MonitoringData.php # Monitoring per lokasi
│   └── Models/                # Eloquent Models
│       ├── User.php
│       ├── Location.php
│       ├── Shift.php
│       ├── JobShift.php
│       ├── Loading.php
│       ├── FotoSimple.php
│       └── FotoActivity.php
│
├── database/migrations/       # Database migrations
├── public/assets/Dashboard/   # CSS, JS, Images
├── resources/views/           # Blade templates
├── routes/web.php             # Route definitions
└── storage/app/public/        # Uploaded files
```

## 📖 Dokumentasi

Untuk dokumentasi teknis lengkap, lihat [TechDoc.md](./TechDoc.md) yang mencakup:

-   Database Schema dengan ERD
-   Alur Kerja Aplikasi (Flowchart)
-   Panduan Pengguna per Role
-   API Routes lengkap
-   Changelog

## 🔧 Konfigurasi Shift

Aplikasi mendukung 3 shift standar:

| Shift   | Jam Kerja     | Keterangan                               |
| ------- | ------------- | ---------------------------------------- |
| Shift 1 | 07:00 - 15:00 | Shift Pagi                               |
| Shift 2 | 15:00 - 23:00 | Shift Siang                              |
| Shift 3 | 23:00 - 07:00 | Shift Malam (Overnight/kemarin-hari ini) |

## 📄 License

[MIT License](LICENSE)

---

<p align="center">
  Made with ❤️ by GSG Developer Team
</p>
