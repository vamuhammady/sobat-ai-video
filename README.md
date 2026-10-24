# Sobat AI Video — browser-first MVP

## Mulai tanpa instalasi
Buka `index.html` di Chrome atau Edge. Upload video milik sendiri, atur rasio 9:16/16:9/1:1, pilih satu dari 5 preset, ubah teks/font/size/alignment, nyalakan/matikan subtitle manual, lalu Export.

## Publikasikan dengan URL gratis
1. Buat akun GitHub.
2. Buat repository baru bernama `sobat-ai-video` (Public jika memakai GitHub Pages gratis).
3. Upload file `index.html` ke root repository.
4. Buka Settings → Pages → Build and deployment → Deploy from a branch → main / (root) → Save.
5. Setelah deployment selesai, URL biasanya `https://USERNAME.github.io/sobat-ai-video/`.

Alternatif: upload `index.html` ke Cloudflare Pages melalui direct upload. Jangan unggah API key di frontend.

## Kemampuan yang benar-benar ada
- Local video upload dan preview di canvas
- 9:16, 16:9, 1:1 (crop-to-fill)
- 5 template teks, font, ukuran, warna, alignment, posisi
- Subtitle manual statis (on/off)
- Browser speech synthesis untuk mendengarkan teks (preview saja)
- Export WebM browser-side menggunakan MediaRecorder (real-time, dukungan audio sumber tergantung browser)
- Download frame PNG
- Save/load pengaturan JSON (video sumber tidak termasuk)
- Layout responsif desktop dan HP

## Batasan penting
- Tidak ada AI generation sungguhan, API Omni/Veo/Kling, atau Google Drive OAuth. Tombolnya ditandai belum terhubung.
- MP4, timed subtitles, auto captions, TTS yang masuk hasil export, trim, dan penyimpanan Drive belum tersedia.
- File video tidak diunggah ke server aplikasi. Jika nantinya integrasi provider AI diaktifkan, media dapat diproses dan disimpan sementara di server provider menurut kebijakannya.
- WebM bisa membutuhkan konversi ke MP4 sebelum upload di platform tertentu.
- Browser HP tertentu mungkin tidak mendukung captureStream/MediaRecorder dengan baik. Gunakan Chrome desktop untuk uji pertama.
- Proyek disimpan sebagai JSON tanpa media, dan pengguna perlu upload ulang file sumber.
