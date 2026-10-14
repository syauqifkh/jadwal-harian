# Jadwal Harian

Jadwal dua kolom: hari dan task di kiri, waktu di kanan. Bisa dipasang di layar utama Android seperti aplikasi, dan tetap bisa dibuka tanpa internet.

## Cara menayangkan di GitHub Pages (gratis)

1. Masuk ke github.com, lalu buat repositori baru: tombol **New**.
   - Nama: `jadwal-harian`
   - Pilih **Public** (GitHub Pages gratis hanya untuk repositori publik).
   - Klik **Create repository**.
2. Di halaman repositori, klik **uploading an existing file**.
3. Ekstrak file zip ini, lalu seret **semua file di dalam folder** (`index.html`, `sw.js`, `manifest.webmanifest`, dan tiga file ikon `.png`) ke halaman unggah. Klik **Commit changes**.
4. Buka **Settings → Pages**.
   - Source: **Deploy from a branch**
   - Branch: **main**, folder **/ (root)**, lalu **Save**.
5. Tunggu 1 sampai 2 menit. Alamat aplikasi muncul di halaman yang sama:
   `https://NAMA-GITHUB-ANDA.github.io/jadwal-harian/`

## Memasang di Android

1. Buka alamat tadi di **Chrome** Android.
2. Ketuk menu ⋮, lalu **Instal aplikasi** (atau **Tambahkan ke layar utama**).
3. Ikon "Jadwal" muncul di layar utama.

## Memindahkan jadwal Anda yang sekarang

Jangan unggah file jadwal pribadi ke GitHub, karena repositorinya publik.

1. Simpan file `jadwal-saya.json` di HP.
2. Buka aplikasi, ketuk **Impor**, lalu pilih file itu.

Gunakan **Ekspor** sesekali untuk mengunduh cadangan. Data disimpan di HP tempat aplikasi dibuka, jadi HP dan komputer memiliki jadwal yang terpisah. Impor file cadangan untuk memindahkannya.

## Memperbarui aplikasi

Ganti file di repositori (**Add file → Upload files**), lalu ubah angka versi di bagian atas `sw.js` (misalnya `jadwal-harian-v2`) supaya HP mengambil versi baru.
