Ini adalah website HMPS-MI yang dibuat oleh saya sendiri, Muhammad Azmi Rahman Nasution dalam rangka mengikuti perlombaan MI-Techno Design
Untuk dewan juri berikut adalah rangkaian cara-cara mengakses project ini:

Panduan Akses dan Penyiapan Proyek

1.Sebelum memulai, pastikan layanan berikut telah terinstal dan berjalan:

PHP (Disarankan versi 8.1 atau lebih tinggi)

Composer

MySQL 2. Prosedur Penyiapan

Jalankan perintah-perintah berikut di direktori utama proyek Anda:

A. Instal Dependensi

Langkah ini mengambil semua paket PHP yang diperlukan.

composer install

B. Konfigurasi Lingkungan dan Kunci

Ini membuat berkas .env yang diperlukan dan menghasilkan kunci aplikasi unik.

cp .env.example .env
php artisan key:generate

C. Konfigurasi Basis Data

PENTING: Berkas .env harus diperbarui dengan kredensial MySQL yang valid untuk basis data website_pemenang (atau nama basis data aktual Anda).

Buka berkas .env yang baru dibuat.

Perbarui detail koneksi basis data. Server harus dikonfigurasi dengan kata sandi, atau gunakan pengaturan kata sandi kosong sementara yang telah kita selesaikan:

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=website_pemenang
DB_USERNAME=root
DB_PASSWORD=KATA_SANDI_ROOT_MYSQL_ANDA

Hapus cache konfigurasi untuk memuat kredensial baru:

php artisan config:clear

D. Jalankan Migrasi dan Seed Data

Karena proyek mengandalkan seeders, kami akan mengatur ulang basis data sepenuhnya untuk memastikan semua tabel dan data awal dimuat dengan benar.

php artisan migrate:fresh --seed

Catatan: Flag --seed secara otomatis menjalankan seeders basis data, mengisi tabel dengan data uji (users, divisions, dll.).

E. Perbaiki Tautan Penyimpanan (Storage Link)

Langkah penting ini memastikan gambar yang diunggah ke folder penyimpanan dapat diakses oleh peramban (browser), yang memperbaiki masalah ikon gambar yang rusak sebelumnya.

php artisan storage:link

3.  Mengakses Aplikasi

A. Mulai Local Server

php artisan serve

B. Akses URL

Setelah server berjalan, aplikasi dapat diakses di URL berikut:
http://127.0.0.1:8000

Catatan

Halaman Utama Publik

http://127.0.0.1:8000/

Tampilan situs web yang dapat diakses publik.

Dasbor Admin

http://127.0.0.1:8000/admin

C. Kredensial Admin (Dari Seeders)

Jika seeders berhasil dijalankan, Anda biasanya dapat masuk menggunakan pengguna bawaan yang disediakan oleh proses seeding proyek. Kredensial bawaan yang umum adalah:

Nama: Admin

Email: admin@hmps.mi

password: password123

(Harap periksa berkas database/seeders proyek jika kredensial ini tidak berfungsi.)

Catatan Pemecahan Masalah: Jika Anda mengalami "500 Server Error," harap periksa berkas storage/logs/laravel.log untuk kesalahan MySQL spesifik. Jika "Access denied" berlanjut, verifikasi DB_PASSWORD dalam berkas .env.

Jika ada kendala dalam akses website dan pengelolaan website mohon untuk mengubungi saya.
Untuk dewan juri saya mengucapkan terimakasih
