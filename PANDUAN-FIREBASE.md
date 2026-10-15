# Panduan Firebase: menyamakan jadwal di HP dan laptop

Firebase gratis untuk pemakaian sekecil ini dan tidak perlu kartu kredit. Kerjakan dari komputer. Seluruhnya sekitar 15 menit.

Tampilan Firebase kadang berubah. Nama menu biasanya tetap sama, jadi cari tulisannya.

## Bagian A. Membuat proyek Firebase

1. Buka **console.firebase.google.com** dan login dengan akun Google Anda.
2. Klik **Create a project** (atau **Add project**).
3. Isi nama proyek, misalnya `jadwal-harian`, lalu klik **Continue**.
4. Kalau ada pertanyaan Google Analytics, matikan tombolnya (tidak diperlukan), lalu klik **Create project**.
5. Tunggu sampai muncul "Your new project is ready", lalu klik **Continue**.

## Bagian B. Mendaftarkan aplikasi web dan menyalin kodenya

6. Di halaman utama proyek, klik ikon web **`</>`** (tulisannya "Web").
7. Isi **App nickname** dengan `jadwal`.
8. **Jangan** centang "Also set up Firebase Hosting". Klik **Register app**.
9. Muncul kotak kode berisi `const firebaseConfig = { ... };`. Yang Anda butuhkan hanya baris-baris di antara tanda `{` dan `}`:
   ```
   apiKey: "AIza...",
   authDomain: "jadwal-harian-xxxx.firebaseapp.com",
   projectId: "jadwal-harian-xxxx",
   storageBucket: "...",
   messagingSenderId: "...",
   appId: "1:...:web:..."
   ```
   Biarkan halaman ini terbuka. Kalau tertutup, kode yang sama ada di **⚙ Project settings → General → Your apps**, di bagian **SDK setup and configuration**, pilih **Config**.

## Bagian C. Mengisi firebase-config.js

10. Buka repositori `jadwal-harian` Anda di github.com.
11. Klik file **firebase-config.js**, lalu klik ikon pensil (**Edit this file**).
12. Hapus baris-baris di dalam tanda `{ }` (dari `apiKey: "ISI_API_KEY",` sampai `appId: "ISI_APP_ID"`), lalu tempel baris-baris dari Firebase tadi. Tanda `{` di atas dan `};` di bawah jangan dihapus.
13. Klik **Commit changes**, lalu **Commit changes** lagi di kotak yang muncul.

Kode ini boleh terlihat publik. Yang menjaga jadwal Anda adalah login dan aturan di Bagian E.

## Bagian D. Mengaktifkan login email

14. Di menu kiri Firebase, buka **Build → Authentication**, lalu klik **Get started**.
15. Buka tab **Sign-in method**, lalu klik **Email/Password**.
16. Aktifkan tombol pertama (**Enable**). Tombol "Email link (passwordless sign-in)" biarkan mati. Klik **Save**.

## Bagian E. Membuat database dan aturan keamanan

17. Di menu kiri, buka **Build → Firestore Database**, lalu klik **Create database**.
18. Kalau ada pilihan edisi, pilih **Standard**.
19. Pilih lokasi **asia-southeast2 (Jakarta)** kalau ada. Lokasi tidak bisa diubah nanti. Klik **Next**.
20. Pilih **Start in production mode**, lalu klik **Create**. Tunggu sampai selesai.
21. Buka tab **Rules**. Hapus semua isinya, lalu tempel ini:
    ```
    rules_version = '2';
    service cloud.firestore {
      match /databases/{database}/documents {
        match /schedules/{uid} {
          allow read, write: if request.auth != null && request.auth.uid == uid;
        }
      }
    }
    ```
22. Klik **Publish**.

Aturan ini membuat setiap akun hanya bisa membaca dan menulis jadwalnya sendiri. Jangan memakai "test mode": database akan terbuka untuk semua orang.

## Bagian F. Memakai di HP dan laptop

23. Buka aplikasi (alamat `https://NAMA-GITHUB-ANDA.github.io/jadwal-harian/`) di laptop. Muat ulang dengan Ctrl+F5.
24. Klik **Masuk** di bagian atas. Isi email dan password (minimal 6 karakter), lalu klik **Buat akun baru**. Cukup sekali.
25. Klik **Impor** dan pilih `jadwal-saya.json`. Status di atas berubah menjadi **Tersinkron**.
26. Di HP, buka aplikasi, ketuk **Masuk**, isi email dan password yang sama, lalu ketuk **Masuk**. Jadwal Anda muncul. Mulai sekarang perubahan di satu perangkat muncul di perangkat lain dalam beberapa detik.

## Tambahan yang disarankan: matikan pendaftaran akun baru

Setelah akun Anda dipakai di semua perangkat, matikan pendaftaran supaya orang lain tidak bisa membuat akun di proyek Anda:

27. Buka **Authentication → Settings → User actions**.
28. Matikan **Enable create (sign-up)**, lalu simpan.

Anda tetap bisa **Masuk** di perangkat baru dengan akun yang sudah ada. Kalau menu itu tidak ada di tampilan Anda, lewati saja.

## Cara kerjanya

- Jadwal disimpan di akun Anda dan juga di tiap perangkat. Tanpa internet, aplikasi tetap bisa dipakai. Perubahan terkirim otomatis saat online lagi.
- Bila dua perangkat mengubah jadwal pada saat yang sama, yang terakhir tersimpan yang dipakai. Hindari mengedit di dua perangkat sekaligus.
- Keluar dari akun tidak menghapus jadwal di perangkat itu.
- Kuota gratis Firebase (sekitar 20.000 penyimpanan dan 50.000 pembacaan per hari) jauh di atas kebutuhan satu orang.

## Kalau ada masalah

| Yang muncul | Penyebab dan solusi |
|---|---|
| Tombol **Masuk** tidak muncul | `firebase-config.js` belum diisi atau masih ada tulisan `ISI_`. Ulangi Bagian C, lalu muat ulang dengan Ctrl+F5. Di HP, tutup aplikasi lalu buka lagi dua kali. |
| "Kode di firebase-config.js salah" | Ada yang terpotong saat disalin. Salin ulang dari Firebase. |
| "Pendaftaran atau login email belum diaktifkan" | Ulangi Bagian D. |
| "Ditolak server. Periksa aturan Firestore" | Aturan di langkah 21 belum dipasang atau belum di-Publish. |
| "Database Firestore belum dibuat" | Ulangi Bagian E, langkah 17 sampai 20. |
| "Email atau password salah" | Periksa ketikan. Gunakan **Lupa password** untuk mengatur ulang lewat email. |
| Perubahan tidak muncul di perangkat lain | Pastikan kedua perangkat memakai email yang sama dan status menunjukkan **Tersinkron**. |
