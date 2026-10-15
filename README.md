# Jadwal Harian

Jadwal dua kolom: hari dan task di kiri, waktu di kanan. Bisa dipasang di layar utama Android seperti aplikasi, dan tetap bisa dibuka tanpa internet.

## Isi folder

| File | Fungsi |
|---|---|
| `index.html` | Aplikasinya |
| `firebase-config.js` | Tempat mengisi kode Firebase agar jadwal tersinkron antar perangkat |
| `sw.js` | Membuat aplikasi bisa dibuka offline |
| `manifest.webmanifest` dan tiga file `icon-*.png` | Membuat aplikasi bisa dipasang di layar utama |
| `PANDUAN-FIREBASE.md` | Panduan lengkap menyamakan jadwal di HP dan laptop |

## Langkah 1. Menayangkan di GitHub Pages (gratis)

1. Di github.com, buat repositori baru bernama `jadwal-harian`, pilih **Public**, lalu **Create repository**.
2. Klik **uploading an existing file**, lalu seret semua file di dalam folder ini (bukan foldernya) ke halaman unggah. Klik **Commit changes**.
3. Buka **Settings → Pages**. Pilih **Deploy from a branch**, branch **main**, folder **/ (root)**, lalu **Save**.
4. Tunggu 1 sampai 3 menit. Alamatnya `https://NAMA-GITHUB-ANDA.github.io/jadwal-harian/`.

## Langkah 2. Memasang di Android

Buka alamat tadi di Chrome Android, ketuk menu ⋮, lalu pilih **Instal aplikasi** (atau **Tambahkan ke layar utama**).

## Langkah 3. Menyamakan jadwal di semua perangkat

Ikuti `PANDUAN-FIREBASE.md`. Tanpa langkah ini, aplikasi tetap berfungsi, tetapi jadwal hanya tersimpan di perangkat yang dipakai.

## Memindahkan jadwal yang sudah ada

Jangan unggah file jadwal pribadi ke GitHub, karena repositorinya publik. Simpan di HP, buka aplikasi, ketuk **Impor**, lalu pilih filenya. Gunakan **Ekspor** sesekali untuk menyimpan cadangan.

## Memperbarui aplikasi

Ganti file di repositori (**Add file → Upload files**, nama file yang sama akan tertimpa), lalu ubah angka versi di bagian atas `sw.js` (misalnya `jadwal-harian-v3`) supaya HP mengambil versi baru. Setelah itu tutup aplikasi dan buka lagi dua kali. Jangan menimpa `firebase-config.js` yang sudah Anda isi, kecuali Anda mengisinya lagi.
