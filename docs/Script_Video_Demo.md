# SCRIPT VIDEO DEMO PERANGKAT LUNAK — UMKMku

> **Durasi:** Maksimal 10 menit
> **Format:** Screen recording (rekam layar) + narasi suara
> **Tujuan:** Mendemokan seluruh fitur aplikasi UMKMku dari awal hingga akhir
> **Perekam:** Mohamad Rifaldy Firdaus (10123095)

---

## PERSIAPAN SEBELUM REKAM

Sebelum mulai merekam, pastikan:

1. ✅ Aplikasi sudah berjalan (atau buka URL production)
2. ✅ Siapkan **1 akun baru** untuk demo register (belum terdaftar)
3. ✅ Siapkan **1 akun lama** yang sudah punya data produk & transaksi (untuk menunjukkan dashboard yang sudah terisi)
4. ✅ Browser dalam keadaan bersih (tutup tab lain)
5. ✅ Resolusi layar 1920x1080 (Full HD)
6. ✅ Mikrofon/headset siap

### Strategi Demo:
- **Login pakai akun lama dulu** → tunjukkan dashboard, produk, laporan yang sudah terisi data
- **Lalu demo alur lengkap:** tambah produk baru → transaksi kasir → lihat perubahan di dashboard & laporan

---

---

## BAGIAN 1 — PEMBUKA (~30 detik)

> *[Tampilkan halaman Login di browser]*

**Narasi:**

"Assalamu'alaikum warahmatullahi wabarakatuh. Perkenalkan, kami dari **Kelompok 2**. Video ini adalah demo aplikasi **UMKMku** — sebuah aplikasi web kasir dan manajemen stok yang dirancang khusus untuk pelaku Usaha Mikro, Kecil, dan Menengah."

"Aplikasi ini dibangun menggunakan **Next.js** untuk frontend, **Laravel 12** untuk backend REST API, dan **MySQL** sebagai database. Aplikasi sudah dideploy secara online dan bisa diakses melalui browser."

---

---

## BAGIAN 2 — REGISTER & LOGIN (~1 menit)

### 2a. Register

> *[Klik link "Daftar" / buka halaman Register]*

**Narasi:**

"Untuk mulai menggunakan UMKMku, pengguna perlu membuat akun terlebih dahulu. Di halaman **Daftar**, pengguna diminta mengisi:"

> *[Isi form satu per satu sambil narasi]*

- "**Nama Lengkap** — misalnya kita isi 'Budi Santoso'"
- "**Nama Usaha** — misalnya 'Warung Budi Jaya'"
- "**Email** — misalnya 'budi@demo.com'"
- "**Password** dan **Konfirmasi Password**"

> *[Klik tombol Daftar]*

"Setelah semua terisi, klik tombol **Daftar**. Sistem akan memvalidasi data — email harus unik dan belum terdaftar. Jika berhasil, pengguna diarahkan ke halaman Login."

### 2b. Login

> *[Di halaman Login, masukkan email & password akun LAMA yang sudah punya data]*

**Narasi:**

"Sekarang kita login. Masukkan email dan password, lalu klik **Masuk**. Sistem akan memverifikasi kredensial melalui backend Laravel dan memberikan token autentikasi menggunakan **Laravel Sanctum**."

> *[Login berhasil, masuk ke Dashboard]*

"Login berhasil. Kita langsung diarahkan ke halaman **Dashboard**."

---

---

## BAGIAN 3 — DASHBOARD (~1.5 menit)

> *[Tampilkan halaman Dashboard secara keseluruhan]*

**Narasi:**

"Ini adalah **Dashboard** — halaman utama yang menampilkan ringkasan kondisi usaha."

### Kartu Ringkasan

> *[Arahkan kursor ke masing-masing kartu]*

"Di bagian atas ada **4 kartu ringkasan**:"

- "**Total Penjualan Hari Ini** — menampilkan total omset penjualan pada hari ini."
- "**Laba Hari Ini** — menampilkan total keuntungan bersih, yaitu selisih antara harga jual dan harga modal."
- "**Jumlah Produk** — total produk yang terdaftar di katalog."
- "**Produk Hampir Habis** — jumlah produk yang stoknya sudah di bawah batas minimum."

### Grafik

> *[Scroll ke bagian grafik]*

"Di bawahnya ada **grafik Pendapatan vs Pengeluaran**."

> *[Klik filter "Hari Ini", lalu "7 Hari Terakhir", lalu "Bulan Ini"]*

"Grafik ini bisa difilter berdasarkan periode: **Hari Ini**, **7 Hari Terakhir**, atau **Bulan Ini**. Data grafik akan berubah secara otomatis sesuai filter yang dipilih."

### Panel Kanan

> *[Arahkan ke panel kanan]*

"Di sisi kanan ada panel **Aktivitas Terbaru** yang menampilkan transaksi-transaksi terakhir — lengkap dengan jam, nomor transaksi, total belanja, dan statusnya."

### Perhatian Stok

> *[Tunjukkan bagian Perhatian Stok jika ada]*

"Di bagian bawah ada **Perhatian Stok** yang otomatis menampilkan daftar produk yang stoknya sudah menipis atau habis. Ini membantu pemilik usaha untuk segera melakukan restok."

---

---

## BAGIAN 4 — PRODUK & STOK (~2 menit)

> *[Klik menu "Produk & Stok" di Sidebar]*

**Narasi:**

"Sekarang kita masuk ke halaman **Produk & Stok**. Halaman ini adalah pusat pengelolaan seluruh barang dagangan."

### Tampilan Tabel

> *[Tunjukkan tabel produk]*

"Secara default, produk ditampilkan dalam bentuk **tabel** yang berisi: Nama Produk, SKU, Kategori, Harga Modal, Harga Jual, Stok, Minimum Stok, dan Status."

"Status produk otomatis ditentukan oleh sistem — **Tersedia** jika stok masih cukup, **Stok Menipis** jika sudah mendekati batas minimum, dan **Habis** jika stok nol."

### Tampilan Kartu

> *[Klik toggle Card View]*

"Pengguna juga bisa beralih ke **tampilan kartu** untuk melihat produk dalam format visual yang lebih ringkas."

### Search & Filter

> *[Ketik nama produk di search bar]*

"Fitur **pencarian** memungkinkan pengguna mencari produk berdasarkan nama secara cepat."

> *[Pilih salah satu kategori di filter]*

"Dan ada **filter kategori** untuk menampilkan produk dari kategori tertentu saja."

### Tambah Produk

> *[Klik tombol "Tambah Produk"]*

**Narasi:**

"Untuk menambah produk baru, klik tombol **Tambah Produk**. Muncul form modal yang berisi:"

> *[Isi form sambil narasi]*

- "**Nama Produk** — misalnya 'Kopi Susu Gula Aren'"
- "**SKU** — kode unik produk, misalnya 'KS-001'"
- "**Kategori** — bisa memilih dari kategori yang sudah ada atau membuat kategori baru langsung dari sini"
- "**Satuan** — misalnya 'gelas'"
- "**Harga Modal** — misalnya Rp 8.000"
- "**Harga Jual** — misalnya Rp 15.000"
- "**Stok Awal** — misalnya 50"
- "**Minimum Stok** — misalnya 10, artinya sistem akan memberi peringatan jika stok di bawah angka ini"

> *[Klik Simpan]*

"Klik **Simpan** dan produk langsung muncul di tabel."

### Edit Produk

> *[Klik ikon Edit pada salah satu produk]*

"Untuk mengedit, klik ikon **Edit**. Form yang sama akan muncul dengan data yang sudah terisi. Kita bisa mengubah harga, stok, atau data lainnya, lalu klik Simpan."

### Hapus Produk

> *[Klik ikon Hapus pada salah satu produk — tapi JANGAN hapus produk yang mau dipakai demo kasir]*

"Untuk menghapus, klik ikon **Hapus**. Sistem akan menampilkan konfirmasi terlebih dahulu sebelum menghapus data secara permanen."

---

---

## BAGIAN 5 — PENJUALAN / KASIR POS (~2 menit) ⭐

> *[Klik menu "Penjualan" di Sidebar]*

**Narasi:**

"Sekarang kita masuk ke fitur utama — halaman **Penjualan** atau **Kasir POS**."

### Layout

"Halaman ini menggunakan **layout dua kolom**. Kolom kiri menampilkan **daftar produk** yang tersedia untuk dijual. Kolom kanan adalah **keranjang belanja**."

### Memilih Produk

> *[Klik 2-3 produk dari kolom kiri]*

"Untuk menambahkan produk ke keranjang, cukup **klik kartu produk** di kolom kiri. Produk langsung masuk ke keranjang di kanan."

"Setiap kartu produk menampilkan nama, harga jual, dan sisa stok. Produk yang stoknya habis akan ditandai dan **tidak bisa diklik**."

### Mengatur Jumlah

> *[Klik tombol + dan - untuk mengubah qty]*

"Di keranjang, kita bisa mengatur **jumlah (qty)** dengan tombol plus dan minus. Sistem otomatis menghitung **subtotal per item** dan **total keseluruhan** secara real-time."

> *[Tunjukkan total di bagian bawah keranjang]*

"Total belanja ditampilkan di bagian bawah keranjang."

### Menghapus Item

> *[Klik tombol X pada salah satu item]*

"Jika ingin menghapus item dari keranjang, klik tombol **X** di samping item tersebut."

### Menyelesaikan Transaksi

> *[Klik tombol "Selesaikan Penjualan"]*

"Setelah semua produk sudah sesuai, klik tombol **Selesaikan Penjualan**."

> *[Muncul modal konfirmasi]*

"Sistem menampilkan **modal konfirmasi** yang menunjukkan total belanja dan jumlah item. Pengguna bisa memilih **Batal** atau **Ya, Selesaikan**."

> *[Klik "Ya, Selesaikan"]*

"Kita klik **Ya, Selesaikan**."

> *[Muncul modal sukses]*

"Transaksi berhasil! Sistem menampilkan **notifikasi sukses** dengan nomor transaksi otomatis, misalnya **TRX-00003**."

"Di balik layar, yang terjadi adalah:"
- "Sistem menghitung **total penjualan dan profit**"
- "**Stok produk otomatis berkurang** sesuai jumlah yang terjual"
- "**Riwayat transaksi** tersimpan di database"
- "Data **Dashboard dan Laporan** otomatis diperbarui"

---

---

## BAGIAN 6 — LAPORAN (~1.5 menit)

> *[Klik menu "Laporan" di Sidebar]*

**Narasi:**

"Sekarang kita lihat halaman **Laporan**. Halaman ini memiliki **2 tab**."

### Tab Penjualan

> *[Pastikan tab Penjualan aktif]*

"Tab pertama adalah **Laporan Penjualan**."

> *[Arahkan ke kartu-kartu ringkasan]*

"Di bagian atas ada kartu **Total Penjualan** dan **Jumlah Transaksi** pada periode yang dipilih."

> *[Tunjukkan grafik]*

"Di bawahnya ada **grafik tren penjualan** yang menampilkan pergerakan omset harian dalam bentuk area chart."

> *[Scroll ke tabel riwayat]*

"Dan di bagian bawah ada **tabel riwayat transaksi** yang menampilkan: nomor transaksi, tanggal, jumlah item, total belanja, metode pembayaran, dan status."

### Tab Laba Rugi

> *[Klik tab "Laba Rugi"]*

"Tab kedua adalah **Laporan Laba Rugi**."

> *[Tunjukkan kartu-kartu]*

"Di sini ada 3 kartu utama: **Pendapatan** (total omset), **Modal/HPP** (Harga Pokok Penjualan), dan **Laba Bersih** (selisih pendapatan dikurangi modal)."

> *[Tunjukkan grafik bar chart]*

"Grafik bar chart di bawah membandingkan **Pendapatan vs Modal** per hari, sehingga pemilik usaha bisa melihat apakah usahanya untung atau rugi."

### Cetak Laporan

> *[Klik tombol cetak / tekan Ctrl+P]*

"Untuk mencetak laporan, pengguna bisa klik tombol **cetak** atau tekan Ctrl+P. Sistem akan membuka dialog print bawaan browser, dan pengguna bisa memilih **Save as PDF** untuk menyimpannya sebagai file PDF."

> *[Tutup dialog print]*

---

---

## BAGIAN 7 — PENGATURAN (~30 detik)

> *[Klik menu "Pengaturan" di Sidebar]*

**Narasi:**

"Terakhir, ada halaman **Pengaturan** untuk mengelola data profil usaha."

> *[Tunjukkan form]*

"Di sini pengguna bisa mengubah **Nama Usaha**, **Nama Pemilik**, **Nomor Telepon**, dan **Alamat**."

> *[Ubah salah satu data, lalu klik Simpan]*

"Setelah diubah, klik **Simpan Perubahan** dan muncul notifikasi bahwa data berhasil disimpan."

> *[Scroll ke bawah, tunjukkan tombol Hapus Akun]*

"Di bagian bawah juga tersedia opsi **Hapus Akun**. Jika diklik, sistem akan menampilkan konfirmasi dan memperingatkan bahwa **seluruh data usaha akan terhapus secara permanen** dan tidak bisa dikembalikan."

---

---

## BAGIAN 8 — VERIFIKASI DATA & PENUTUP (~30 detik)

> *[Kembali ke halaman Dashboard]*

**Narasi:**

"Jika kita kembali ke **Dashboard**, kita bisa lihat bahwa data sudah terupdate. Total penjualan dan laba sudah bertambah setelah transaksi yang tadi kita buat, dan grafik juga sudah menampilkan data terbaru."

"Demikian demo aplikasi **UMKMku** dari Kelompok 2. Aplikasi ini membantu pelaku UMKM untuk mengelola produk, mencatat penjualan, memantau stok, dan melihat laporan keuangan — semuanya dalam satu dashboard yang sederhana dan mudah digunakan."

"Terima kasih. Wassalamu'alaikum warahmatullahi wabarakatuh."

---

---

## ESTIMASI WAKTU

| Bagian | Durasi |
|---|---|
| 1. Pembuka | ~30 detik |
| 2. Register & Login | ~1 menit |
| 3. Dashboard | ~1.5 menit |
| 4. Produk & Stok | ~2 menit |
| 5. Penjualan / Kasir POS | ~2 menit |
| 6. Laporan | ~1.5 menit |
| 7. Pengaturan | ~30 detik |
| 8. Penutup | ~30 detik |
| **TOTAL** | **~8.5 menit** |

> Masih ada sisa ~1.5 menit jika perlu menjelaskan lebih detail atau ada jeda.

---

## TIPS REKAMAN

1. **Pakai OBS Studio** atau **Xbox Game Bar** (Win+G) untuk screen recording
2. **Resolusi 1080p** minimal agar tulisan terbaca jelas
3. **Zoom in browser** (Ctrl + =) jika perlu agar elemen UI terlihat lebih besar
4. **Jangan terlalu cepat** — beri jeda 1-2 detik setiap kali berpindah halaman
5. **Narasi natural** — tidak perlu baca script kata per kata, yang penting poin-poinnya tersampaikan
6. **Siapkan data** — pastikan sudah ada beberapa produk dan transaksi sebelum rekam agar dashboard tidak kosong saat pertama kali ditunjukkan
