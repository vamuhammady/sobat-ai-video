# Sobat AI Video v2.0 — Rencana integrasi video

## Status

- GitHub Pages: antarmuka editor statis.
- Video lokal: upload dan preview.
- Trim: kontrol in/out dan penerapan ke ekspor berbasis MediaRecorder bila didukung.
- URL video langsung: fetch browser, hanya jika CORS mengizinkan.
- YouTube, TikTok, Instagram Reels: **belum mendukung download otomatis**.
- Safari iPhone: ekspor hasil edit belum terjamin karena dukungan captureStream/MediaRecorder.
- Backend: belum dipasang atau di-deploy.

## Arsitektur yang disarankan

1. Frontend GitHub Pages untuk UI, upload, trim, teks dan preview.
2. Backend terpisah untuk autentikasi, pemeriksaan izin dan status pekerjaan.
3. Impor hanya melalui URL file langsung atau integrasi platform yang mengizinkan akses/unduhan, dengan persetujuan pemilik atau lisensi yang sesuai. Embed publik tidak berarti ada izin download.
4. Penyimpanan sementara dengan masa retensi singkat dan batas ukuran.
5. Pekerja FFmpeg untuk trim, overlay dan MP4 H.264/AAC agar hasil dapat dibuka di Safari.
6. Endpoint job status dan unduhan bertanda tangan, dengan pembersihan otomatis.

## API rancangan (belum diimplementasikan)

- POST /api/import — {sourceUrl, authorizationEvidence?}, mengembalikan jobId atau alasan tidak didukung.
- POST /api/export — upload sumber atau referensi file yang sah + pengaturan edit, mengembalikan jobId.
- GET /api/jobs/:jobId — status/progress/error.
- GET /api/jobs/:jobId/download — URL hasil sementara.

## Batasan penting

- Tidak menjanjikan download dari setiap URL publik YouTube/TikTok/Instagram.
- Jangan memasukkan token API atau rahasia di index.html/GitHub Pages.
- Backend dan FFmpeg memerlukan hosting/biaya operasional; pilih penyedia dan otorisasi sebelum deployment.
- Jangan menampilkan tombol download platform sebagai aktif sebelum integrasi diuji end-to-end.

## Uji penerimaan berikutnya

1. Upload MP4 dari Foto/File pada Safari iPhone.
2. Preview, seek, set in/out, teks/subtitle dan simpan JSON.
3. Ekspor MP4 melalui backend, cek audio-video sinkron.
4. Uji impor URL yang memang memberikan akses unduhan dan izin.
5. Uji pesan penolakan yang jelas untuk link platform tanpa izin unduhan.
