# Email Otomatis PRO

PWA mobile sederhana untuk mengelola kontak, membuat email, menyimpan template, menjadwalkan email, melihat riwayat, dan mengimpor kontak CSV.

## Isi paket
- `index.html`, `styles.css`, `app.js`: aplikasi web.
- `manifest.webmanifest`, `sw.js`, `icon.svg`: dukungan PWA.
- `gas/Code.gs`: backend Google Apps Script.

## A. Publikasikan frontend melalui GitHub Pages
1. Unggah seluruh isi folder utama repository GitHub (file `index.html` harus berada di root, bukan di dalam subfolder).
2. Buka repository > Settings > Pages.
3. Pada Build and deployment pilih Deploy from a branch.
4. Pilih branch `main`, folder `/ (root)`, lalu Save.
5. Tunggu alamat Pages muncul. Buka alamat tersebut menggunakan Chrome Android.

## B. Siapkan backend Google Apps Script
1. Buka https://script.google.com menggunakan akun Google yang akan mengirim email.
2. Buat New project, beri nama Email Otomatis PRO.
3. Hapus kode contoh, lalu tempel isi file `gas/Code.gs`.
4. Simpan. Pilih fungsi `setup` lalu tekan Run. Berikan izin Google yang diminta.
5. Buka Deploy > New deployment > pilih Web app.
6. Execute as: Me. Who has access: Anyone. Deploy, lalu izinkan akses jika diminta.
7. Salin URL Web app yang berakhiran `/exec`.
8. Di PWA buka Pengaturan, tempel URL tersebut, tekan Simpan lalu Uji Koneksi.

## C. Pasang di Android
1. Buka URL GitHub Pages menggunakan Chrome.
2. Tekan menu Chrome (⋮).
3. Pilih Add to Home screen / Tambahkan ke layar utama.

## Penting sebelum digunakan
- Paket ini adalah fondasi aplikasi yang dapat dijalankan setelah frontend dan backend dipasang; bukan layanan email tanpa batas.
- Backend memakai endpoint JSONP berbasis GET agar dapat dipanggil dari GitHub Pages tanpa konfigurasi CORS. Ini cocok untuk uji coba pribadi, bukan sistem publik/produksi.
- Siapa pun yang mengetahui URL Web App yang disetel sebagai akses Anyone berpotensi memanggil fungsi backend. Jangan menyimpan data sensitif atau membagikan URL. Untuk penggunaan publik perlu autentikasi dan backend yang lebih aman.
- Pengiriman mengikuti kuota Gmail/Google Apps Script dan kebijakan Google. Jangan mengirim spam; kirim hanya kepada penerima yang menyetujui.
- Pengiriman terjadwal diperiksa pemicu setiap menit. Waktu aktual dapat terlambat.
- Auto-retry disediakan untuk jadwal gagal hingga 3 percobaan. Pengiriman langsung tidak otomatis diulang.
- CSV yang didukung memakai pemisah koma dan header `nama,email`. File Excel (.xlsx) perlu disimpan sebagai CSV terlebih dahulu.
- HTML email: isi dapat berupa HTML sederhana. Gambar sebaiknya memakai URL gambar publik; lampiran gambar lokal belum disediakan.
- Pengulangan berdasarkan tanggal khusus belum menjadi kontrol di antarmuka; jadwal satu kali berfungsi. Untuk pengulangan kompleks, perlu pengembangan lanjutan di backend.
- Notifikasi saat ini berupa status dalam aplikasi dan permintaan izin notifikasi browser; pemberitahuan push ketika aplikasi tertutup belum disediakan.
- Sebelum mengirim ke banyak orang, lakukan tes dengan email milik sendiri.
