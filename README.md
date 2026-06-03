# Contributing to PosyanduApp

Terima kasih sudah berminat berkontribusi pada PosyanduApp. Dokumen ini menjelaskan langkah awal dari cloning repositori sampai kontribusi kode siap dikirim melalui GitHub.

## 1. Persiapan Awal

1. Pastikan komputer Anda sudah terpasang:
   - PHP 8.3 atau lebih baru
   - Composer
   - Node.js (versi terbaru yang stabil)
   - Git

2. Clone repositori dari GitHub:

```bash
git clone <repository-url>
cd posyanduApp
```

> Ganti `<repository-url>` dengan alamat repositori PosyanduApp di GitHub.

## 2. Instalasi Dependensi

Jalankan perintah berikut dari folder project:

```bash
composer install
npm install
```

## 3. Konfigurasi Lingkungan

1. Salin file lingkungan:

```bash
cp .env.example .env
```

2. Jika Anda memakai Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

3. Buat `APP_KEY` baru:

```bash
php artisan key:generate
```

4. Jika memakai database SQLite, buat file database:

```bash
mkdir -p database
copy NUL database\database.sqlite
```

Jika memakai database MySQL / MariaDB, sesuaikan pengaturan di file `.env`:

```dotenv
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=posyanduapp
DB_USERNAME=root
DB_PASSWORD=
```

## 4. Migrasi dan Seed Data

Jalankan migrasi untuk menyiapkan tabel database:

```bash
php artisan migrate
```

Jika Anda ingin menambahkan data awal, tambahkan seeder terlebih dahulu lalu jalankan:

```bash
php artisan db:seed
```

## 5. Build Aset Frontend

Untuk membuat file `manifest.json` dan aset CSS/JS:

```bash
npm run build
```

Untuk menjalankan mode pengembangan dengan watch/live reload:

```bash
npm run dev
```

## 6. Menjalankan Aplikasi Secara Lokal

Jika ingin melihat aplikasi di browser:

```bash
php artisan serve
```

Buka `http://127.0.0.1:8000` di browser.

## 7. Workflow Kontribusi GitHub

1. Buat branch baru dari `main` atau `master`:

```bash
git checkout -b feature/nama-fitur
```

2. Kerjakan perubahan Anda.
3. Tambahkan dan commit perubahan:

```bash
git add .
git commit -m "Menambahkan fitur X pada PosyanduApp"
```

4. Push branch ke remote:

```bash
git push origin feature/nama-fitur
```

5. Buat Pull Request di GitHub dan jelaskan perubahan yang dilakukan.

## 8. Menjalankan Tes

Untuk memeriksa apakah kode berjalan baik:

```bash
composer test
```

Jika Anda ingin membersihkan konfigurasi cache sebelum tes:

```bash
php artisan config:clear
php artisan test
```

## 9. Best Practices

- Gunakan bahasa Indonesia yang jelas untuk komentar dan pesan commit.
- Ikuti konvensi Laravel untuk struktur kode dan nama class.
- Pastikan `resources/views` tetap rapi dan mudah dipahami.
- Jangan commit file `.env` atau file build yang bersifat sementara.
- Jika menambahkan dependensi baru, jalankan kembali `composer install` atau `npm install`.

## 10. Catatan Tambahan

- Project ini menggunakan Laravel 13 dan Vite.
- Frontend menggunakan Tailwind CSS dengan `resources/css/app.css`.
- Tampilan awal berada di `resources/views/welcome.blade.php`.

Jika Anda menemui masalah, silakan buka issue di GitHub atau diskusikan langsung di Pull Request.
