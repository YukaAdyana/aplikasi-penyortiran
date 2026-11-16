# PRD — Aplikasi Sortir Dokumen

Status: Draf untuk validasi  
Tanggal: 16 November 2026

## 1. Ringkasan

Aplikasi ini membantu pengusaha yang kewalahan mengelola banyak dokumen untuk mengelompokkan file berdasarkan jenis dokumen dan menemukannya kembali dengan cepat. Kebutuhan pengguna mencakup semua jenis file. Versi awal diusulkan mendukung penyimpanan berbagai format, dengan pembacaan isi dan penyortiran otomatis pada format tertentu terlebih dahulu.

## 2. Latar belakang

Pengguna sasaran memiliki terlalu banyak dokumen dan belum memiliki solusi yang sesuai untuk mengelolanya. Masalah utama yang ingin diselesaikan adalah lamanya menemukan dokumen yang dibutuhkan.

Pengguna meminta penyortiran berdasarkan jenis dokumen. Dalam draf ini, jenis dokumen diartikan sebagai kategori bisnis seperti invoice, kontrak, dan surat, sedangkan format file berarti PDF, DOCX, JPG, dan sebagainya. Penafsiran ini perlu divalidasi sebelum pengembangan.

## 3. Tujuan dan ukuran keberhasilan

**Tujuan utama:** mempercepat pencarian dokumen milik usaha.

Target berikut merupakan usulan awal, bukan hasil pengukuran. Baseline diukur melalui tugas pencarian yang sama sebelum dan setelah menggunakan aplikasi.

| Ukuran | Target uji coba yang diusulkan |
|---|---|
| Waktu menemukan dokumen yang benar | Median waktu turun minimal 50% dibanding cara pengguna saat ini |
| Keberhasilan pencarian | Minimal 90% tugas pencarian selesai dalam 60 detik |
| Ketepatan penyortiran otomatis | Minimal 85% dokumen dalam format dan kategori yang didukung masuk kategori yang benar sebelum koreksi pengguna |

Evaluasi dilakukan setelah empat minggu penggunaan oleh kelompok uji coba. Jumlah peserta, jumlah file, dan kategori uji perlu disepakati setelah melihat contoh dokumen pengguna.

## 4. Segmen pengguna

**Segmen utama:** pemilik usaha yang perlu menemukan dokumen untuk menjalankan kegiatan bisnis, tetapi kesulitan karena jumlah dokumen terlalu banyak.

**Pengguna pendukung, sebagai asumsi:** staf administrasi yang memasukkan dan merapikan dokumen untuk pemilik usaha. Kebutuhan kerja bersama dapat menyusul setelah alur pengguna utama terbukti membantu.

Versi awal memprioritaskan satu pemilik akun yang mengelola dokumen satu usaha. Besarnya koleksi, perangkat yang dipakai, serta kebutuhan akses tanpa internet belum diketahui.

## 5. Proposisi nilai

- **Siapa:** pengusaha yang kewalahan mengelola dokumen usahanya.
- **Mengapa:** perlu menemukan dokumen yang tepat dengan cepat agar pekerjaan tidak tertunda.
- **Kondisi sebelumnya:** belum memiliki solusi yang sesuai. Dugaan bahwa pengguna mencari lewat folder, nama file, atau membuka dokumen satu per satu perlu dikonfirmasi.
- **Cara solusi membantu:** menyarankan kategori dokumen, menyediakan koreksi kategori, serta memungkinkan pencarian melalui nama, isi yang berhasil dibaca, dan filter.
- **Kondisi setelahnya:** pengguna dapat menemukan dan membuka dokumen yang benar dengan lebih sedikit langkah dan waktu.
- **Alternatif:** pengelompokan folder dan pencatatan manual adalah alternatif yang perlu diuji terhadap cara kerja pengguna saat ini. Alasan memilih aplikasi ini harus dibuktikan melalui pencarian yang lebih cepat dan kategori yang mudah diperbaiki.

**Pernyataan nilai:** “Temukan dokumen usaha dengan cepat melalui pengelompokan berdasarkan jenis dan pencarian dalam satu tempat.”

## 6. Solusi dan kebutuhan versi awal

### Alur utama

Pengguna mengunggah beberapa file → aplikasi memproses setiap file → aplikasi menyarankan jenis dokumen → pengguna memeriksa hasil yang perlu ditinjau → dokumen tersedia untuk dicari, disaring, dan dibuka atau diunduh.

Dokumen yang sudah masuk tetap dapat dicari berdasarkan nama meskipun pembacaan isi belum selesai.

### Fitur wajib dan kriteria penerimaan

| Fitur | Perilaku dan kriteria penerimaan |
|---|---|
| Unggah banyak file | Pengguna dapat memilih beberapa file sekaligus. Status berhasil, sedang diproses, atau gagal ditampilkan per file. Satu kegagalan tidak membatalkan file lain. Batas ukuran ditampilkan sebelum unggah. |
| Penyortiran berdasarkan jenis | Kategori awal yang diusulkan: invoice/tagihan, kuitansi/bukti pembayaran, kontrak/perjanjian, surat, laporan, dan lainnya. Setiap dokumen memiliki satu kategori utama yang bisa diubah pengguna. |
| Pembacaan isi | Usulan cakupan awal: PDF berbasis teks, DOCX, XLSX, TXT, serta JPG/PNG dan PDF hasil pindai melalui pengenalan teks (OCR). Teks hasil pembacaan digunakan untuk pencarian dan saran kategori. |
| Peninjauan hasil | Dokumen dengan hasil klasifikasi yang tidak meyakinkan diberi status “Perlu ditinjau”. Pengguna dapat mengganti kategori tanpa mengubah file asli. Ambang keyakinan ditentukan melalui pengujian contoh dokumen. |
| Pencarian dan filter | Pencarian mencakup nama file dan isi yang berhasil dibaca. Hasil dapat difilter berdasarkan kategori, format, tanggal unggah, dan status pemrosesan. File uji harus ditemukan melalui nama dan, jika pembacaan berhasil, kata yang ada di dalamnya. |
| Hasil pencarian yang jelas | Setiap hasil menampilkan nama, kategori, format, dan tanggal unggah; cuplikan teks ditampilkan jika tersedia. Pengguna dapat membuka pratinjau format yang didukung atau mengunduh file asli. |
| Format yang belum didukung | File tetap dapat disimpan dan dicari berdasarkan nama serta kategori manual, selama memenuhi batas unggahan. Aplikasi menjelaskan jika isi tidak dapat dibaca atau pratinjau tidak tersedia. |
| Perlindungan dokumen | Akun memerlukan autentikasi. Pengguna hanya dapat mengakses dokumen miliknya. Penghapusan memerlukan konfirmasi, dan proses klasifikasi tidak mengubah file asli. |

### Asumsi dan pertanyaan terbuka

- Aplikasi web diusulkan agar dapat diakses dari komputer dan ponsel; pilihan platform belum dikonfirmasi.
- “Semua jenis file” diartikan sebagai penyimpanan berbagai format, bukan jaminan semua isi file bisa dibaca. Arsip, file terenkripsi, audio, video, serta format khusus memerlukan aturan penanganan tersendiri.
- Kategori bisnis dan daftar format awal perlu diuji dengan contoh dokumen nyata. Jika “jenis” berarti format file, rancangan kategori perlu disesuaikan.
- Volume file, ukuran maksimum, kapasitas penyimpanan, dan target kecepatan pencarian harus ditetapkan sebelum implementasi berdasarkan kebutuhan pengguna.
- Lokasi penyimpanan, pencadangan, pemulihan, masa simpan, serta penggunaan layanan pemrosesan pihak ketiga perlu diputuskan sebelum dokumen usaha diunggah dalam uji coba.
- Bahasa dokumen dan kualitas hasil pindai belum diketahui; keduanya dapat memengaruhi hasil pencarian dan klasifikasi.

## 7. Cakupan rilis

**Versi awal:** unggah banyak file, kategori dokumen, pembacaan format awal, peninjauan dan koreksi kategori, pencarian, filter, serta akses file asli dalam satu akun usaha.

**Rilis berikutnya:** penambahan format berdasarkan kebutuhan nyata, kategori buatan pengguna, impor dari sumber lain, dan akses beberapa anggota usaha dengan pembagian hak akses.

**Di luar versi awal:** memindai kertas langsung dari perangkat pemindai, mengedit isi dokumen, tanda tangan digital, akuntansi otomatis, dan kemampuan memahami isi seluruh format file.

## 8. Rencana rilis dan validasi

1. **Validasi kebutuhan:** kumpulkan contoh dokumen dengan izin pengguna, petakan kategori, dan ukur waktu pencarian saat ini.
2. **Prototipe alur:** uji unggah, koreksi kategori, dan pencarian bersama calon pengguna sebelum membangun seluruh fitur.
3. **Bangun versi awal:** terapkan format dan kategori yang disepakati, lalu verifikasi dengan kumpulan dokumen uji yang mewakili kebutuhan pengguna.
4. **Uji coba empat minggu:** ukur waktu pencarian, keberhasilan menemukan file, dan ketepatan kategori; catat penyebab kegagalan.
5. **Keputusan rilis:** perluas penggunaan setelah target pencarian tercapai dan masalah akses maupun kehilangan file telah diselesaikan. Jika belum tercapai, prioritaskan perbaikan berdasarkan penyebab kegagalan uji.

Durasi pengembangan belum dapat diperkirakan secara andal sebelum volume dokumen, format prioritas, pilihan penyimpanan, dan kapasitas tim diketahui.
