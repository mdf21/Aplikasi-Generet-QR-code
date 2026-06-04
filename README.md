# Pembuat QR Code Sekolah Sederhana

Aplikasi web sederhana untuk membuat QR Code kustom dengan opsi menambahkan logo, memilih warna, dan menyimpan riwayat pembuatan lokal.

**Fitur utama**
- Buat QR dari teks atau URL.
- Tambah logo (PNG/JPEG) yang ditempatkan di tengah QR.
- Pilih warna foreground QR.
- Simpan riwayat pembuatan di perangkat (localStorage) dan ekspor ke Excel.
- Unduh QR resolusi tinggi sebagai PNG.

**Cara menjalankan (pengembangan/desktop)**
- Buka file `index.html` di peramban (double-click atau buka via `File -> Open`).
- Tidak diperlukan server; aplikasi berjalan sepenuhnya di sisi klien.

**Langkah cepat penggunaan**
1. Isi kolom "Tautan / Teks".
2. (Opsional) Pilih logo PNG/JPEG (maks 2MB).
3. Pilih warna QR (pastikan kontras dengan latar putih).
4. Klik "Buat QR Code" dan kemudian "Unduh Gambar" untuk menyimpan.

**Catatan keamanan & privasi**
- Hanya format gambar PNG/JPEG yang diterima untuk logo; SVG ditolak untuk mencegah kemungkinan injeksi.
- Riwayat disimpan secara lokal di `localStorage` pada perangkat pengguna. Data tidak dikirim ke server.
- Telah diimplementasikan mitigasi XSS pada tampilan riwayat (penggunaan `textContent` dan pembuatan elemen DOM alih-alih `innerHTML`).
- Terdapat contoh `Content-Security-Policy` meta tag untuk membatasi sumber eksternal; sesuaikan CSP sebelum dipakai di produksi.

**Rekomendasi untuk produksi**
- Bundle dependency (Tailwind, FontAwesome, SheetJS, QR library) secara lokal atau gunakan SRI (`integrity` + `crossorigin`) untuk mengurangi risiko supply-chain.
- Pindahkan skrip inline ke file JS terpisah dan hapus `unsafe-inline` dari CSP.
- Jika aplikasi akan menerima URL dari pengguna yang digunakan di lingkungan sekolah, pertimbangkan whitelist domain atau pemeriksaan domain untuk mencegah link berbahaya.
- Untuk penanganan file upload yang lebih aman, lakukan validasi/konversi server-side bila memungkinkan.

**Troubleshooting**
- Jika tampilan tidak ter-styling: bersihkan cache atau muat ulang keras (Ctrl+Shift+R). Pastikan koneksi internet mengizinkan CDN jika masih memakai CDN.
- Jika unggahan logo ditolak: periksa format file dan ukuran (<= 2MB).

**File utama**
- `index.html` — antarmuka dan logika utama.

