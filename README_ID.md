# Japanese Learning Center — Android build package

Paket ini membungkus aplikasi belajar HTML v6 menjadi aplikasi Android menggunakan Capacitor.

## Status yang sebenarnya
- Konten web v6 sudah dimasukkan ke `www/index.html`.
- Konfigurasi Capacitor dan workflow GitHub Actions sudah disiapkan.
- Proyek Android native akan dibuat otomatis di GitHub Actions saat workflow dijalankan.
- **APK belum dibuat di paket ini.** APK baru tersedia setelah workflow GitHub selesai dengan status sukses.
- Aplikasi saat ini bekerja offline dan menyimpan progress di penyimpanan lokal aplikasi. Belum ada login atau sinkronisasi cloud.

## Cara menghasilkan APK hanya dengan tablet Android
1. Unduh dan ekstrak ZIP ini.
2. Buka GitHub melalui browser tablet dan masuk/daftar akun.
3. Buat repository baru, misalnya `japanese-learning-center-android`.
4. Unggah seluruh isi folder proyek ini ke repository, termasuk folder tersembunyi `.github/workflows`.
   - Pastikan file workflow berada di `.github/workflows/build-apk.yml`.
   - Jika upload lewat browser tidak menampilkan folder tersembunyi, buat folder `.github/workflows` di repository dan tambahkan `build-apk.yml` melalui fitur Add file.
5. Buka tab **Actions** pada repository.
6. Pilih workflow **Build Android APK**, lalu tekan **Run workflow**. Jika workflow belum terlihat, pastikan file workflow sudah ada di branch `main`.
7. Tunggu sampai proses selesai dengan tanda hijau **Success**.
8. Buka hasil run workflow tersebut, cari bagian **Artifacts**, lalu unduh `Japanese-Learning-Center-debug-APK`.
9. Ekstrak ZIP artifact dan temukan `app-debug.apk`.
10. Ketuk APK untuk memasang. Android mungkin meminta izin memasang aplikasi dari browser/file manager yang kamu gunakan. Aktifkan izin hanya untuk sumber yang kamu percaya, lalu lanjutkan pemasangan.

## Bila build gagal
- Buka run yang gagal pada tab Actions.
- Periksa langkah yang berwarna merah dan pesan error terakhir.
- Jangan membagikan token, password, signing key, atau secret pribadi ke chat.
- Jika repository dibuat private, pastikan Actions diizinkan di pengaturan repository.

## Build APK lokal (jika suatu saat memakai komputer)
Memerlukan Node.js 20+, Java 21, dan Android SDK:
```bash
npm install
npx cap add android
npx cap sync android
cd android
./gradlew assembleDebug
```
Hasil debug APK:
`android/app/build/outputs/apk/debug/app-debug.apk`

## Tentang rilis
`app-debug.apk` cocok untuk instalasi dan pengujian pribadi. Untuk distribusi luas/Play Store, perlu build release, signing key yang dijaga aman, pengujian kompatibilitas, kebijakan privasi, dan peninjauan Play Console. Jangan membagikan debug APK sebagai rilis produksi.

## Batasan aplikasi saat ini
- Penyimpanan lokal perangkat, bukan cloud.
- Belum ada autentikasi/login.
- Materi kosakata dan kanji belum merupakan daftar resmi lengkap JLPT.
- Konten ringkasan merupakan materi belajar orisinal, bukan salinan buku Minna no Nihongo.
