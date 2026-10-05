# SCRIPT VIDEO INDIVIDU — Kelompok 2 UMKMku

> **Durasi:** Maksimal 3 menit per orang
> **Format:** Tampilkan wajah (webcam) + screen recording aplikasi/kode
> **Tujuan:** Menjelaskan kontribusi individu terhadap **dokumen** dan **implementasi perangkat lunak**

---

## Ringkasan Pembagian Kontribusi

| Anggota | Dokumen | Implementasi (Coding) |
|---|---|---|
| **Rifaldy** | Dokumen Analisis PL | Backend — API, Database, Autentikasi |
| **RD. Fariz** | Dokumen Proses Bisnis | Halaman Dashboard & Laporan |
| **Farhan** | Dokumen Perancangan PL | Halaman Produk & Stok |
| **Faiz** | Dokumen Pengujian PL | Halaman Kasir / Penjualan (POS) |
| **Rasyid** | Dokumen Proses Bisnis (flowchart) | Halaman Login, Register, Pengaturan, Layout |

---

---

## 1. MOHAMAD RIFALDY FIRDAUS (10123095)

**Bagian Dokumen:** Dokumen Analisis Kebutuhan Perangkat Lunak
**Bagian Implementasi:** Backend — REST API, Database, Autentikasi

### Naskah Video:

> *[Buka dengan webcam, perkenalan]*

"Assalamu'alaikum, perkenalkan nama saya Mohamad Rifaldy Firdaus, NIM 10123095, dari Kelompok 2. Saya akan menjelaskan kontribusi saya dalam pengembangan aplikasi UMKMku."

---

> *[Tampilkan dokumen Analisis di layar]*

**BAGIAN DOKUMEN — Analisis Kebutuhan PL (~1 menit)**

"Untuk bagian dokumentasi, saya mengerjakan **Dokumen Analisis Kebutuhan Perangkat Lunak**. Dokumen ini berisi beberapa bagian utama:"

"**Pertama, Analisis Data.** Saya mengidentifikasi 5 entitas data utama yang dibutuhkan sistem, yaitu: Data Pengguna (Users), Data Kategori, Data Produk, Data Transaksi, dan Data Item Transaksi. Masing-masing sudah didefinisikan atribut-atributnya secara lengkap."

"**Kedua, Pemodelan Data.** Saya membuat ERD menggunakan Chen's Notation yang menggambarkan relasi antar entitas — misalnya satu Pengguna bisa Membuat banyak Kategori, satu Kategori bisa Memiliki banyak Produk, dan satu Transaksi Terdiri Dari banyak Detail Item. Lalu saya juga membuat Physical Data Model yang menggambarkan struktur tabel lengkap dengan tipe data dan foreign key."

"**Ketiga, Analisis Kebutuhan Fungsional.** Saya mendefinisikan 4 kebutuhan fungsional utama, yaitu: KK-1 untuk manajemen akun, KK-2 untuk CRUD produk dan kategori, KK-3 untuk sistem kasir POS, dan KK-4 untuk laporan dashboard. Masing-masing dilengkapi Diagram Konteks, DFD Level 0, Spesifikasi Proses, Flowchart, dan Kamus Data."

"**Keempat, Analisis Kebutuhan Non-Fungsional,** mencakup kebutuhan perangkat lunak, perangkat keras, dan brainware. Karena aplikasi ini berbasis cloud, pengguna cukup menggunakan browser dan koneksi internet."

---

> *[Tampilkan kode di VS Code / browser]*

**BAGIAN IMPLEMENTASI — Backend (~1.5 menit)**

"Untuk bagian implementasi, saya mengerjakan seluruh **backend** aplikasi UMKMku menggunakan **Laravel 12**."

> *[Buka folder `backend/database/migrations/`]*

"**Pertama, Database.** Saya merancang dan membuat 5 tabel utama melalui Laravel Migration, yaitu: `users`, `categories`, `products`, `transactions`, dan `transaction_items`. Struktur tabelnya sesuai dengan ERD yang ada di Dokumen Analisis — misalnya tabel `products` memiliki kolom `price` bertipe DECIMAL 12,2 untuk harga jual, `cost_price` untuk harga modal, `stock` untuk stok, dan `min_stock` untuk batas minimum stok."

> *[Buka file `routes/api.php`]*

"**Kedua, REST API.** Saya membangun 7 endpoint API, di antaranya: `POST /register` dan `POST /login` untuk autentikasi, `apiResource` untuk Products dan Categories yang otomatis menyediakan CRUD, `GET dan POST /transactions` untuk transaksi, dan `GET /dashboard` untuk data ringkasan."

> *[Buka file `AuthController.php`]*

"**Ketiga, Autentikasi.** Saya menggunakan **Laravel Sanctum** untuk sistem token-based authentication. Saat user login, sistem memvalidasi email dan password, lalu menghasilkan token yang digunakan frontend untuk mengakses semua API yang dilindungi middleware `auth:sanctum`."

> *[Buka file `TransactionController.php`]*

"**Keempat, Business Logic Transaksi.** Ini bagian yang paling kritis. Saat transaksi dibuat, sistem menggunakan `DB::beginTransaction()` untuk memastikan atomicity. Sistem mengecek kepemilikan produk, memvalidasi stok mencukupi, menghitung subtotal dan profit per item, lalu mengurangi stok dengan `$product->decrement('stock')`. Jika ada error, semua di-rollback. Nomor invoice juga di-generate otomatis dengan format TRX-00001."

"Demikian kontribusi saya. Terima kasih."

---

---

## 2. RD. FARIZ NUR SYAWALUDDIN (10124445)

**Bagian Dokumen:** Dokumen Proses Bisnis
**Bagian Implementasi:** Halaman Dashboard & Laporan

### Naskah Video:

> *[Buka dengan webcam, perkenalan]*

"Assalamu'alaikum, perkenalkan nama saya RD. Fariz Nur Syawaluddin, NIM 10124445, dari Kelompok 2. Saya akan menjelaskan kontribusi saya dalam proyek UMKMku."

---

> *[Tampilkan dokumen Proses Bisnis di layar]*

**BAGIAN DOKUMEN — Proses Bisnis (~1 menit)**

"Saya mengerjakan **Dokumen Proses Bisnis** yang mendefinisikan seluruh alur operasional sistem UMKMku."

"Dalam dokumen ini, saya mengidentifikasi **6 proses bisnis utama:**"

"**PR-01 — Manajemen Kategori Produk**, yaitu proses pengelompokan jenis barang. Input-nya berupa nama kategori, dan output-nya data kategori tersimpan di database."

"**PR-02 — Pencatatan Data Produk & Stok**, yaitu proses penambahan produk baru lengkap dengan harga dan stok. Di sini ada batasan bahwa harga dan stok harus berupa bilangan asli."

"**PR-03 — Manajemen Akun & Autentikasi**, mencakup registrasi, login, dan manajemen profil. Email harus unik, dan jika akun dihapus, seluruh data ikut terhapus."

"**PR-04 — Proses Transaksi Kasir POS**, yaitu proses pencatatan penjualan. Batasannya, jumlah yang dibeli tidak boleh melebihi stok yang tersedia."

"**PR-05 — Pencatatan Riwayat Transaksi**, yaitu sistem mencatat histori setiap transaksi yang berhasil secara otomatis dan bersifat immutable — tidak bisa diubah."

"**PR-06 — Pembuatan Laporan Analitik**, yaitu dashboard yang mengakumulasi data penjualan menjadi ringkasan arus kas."

"Saya juga mendefinisikan satu stakeholder utama, yaitu **USR-1 Pemilik Usaha**, yang bertanggung jawab atas seluruh input data. Setiap proses bisnis dilengkapi dengan **visualisasi flowchart** menggunakan diagram Mermaid."

---

> *[Buka aplikasi di browser — halaman Dashboard]*

**BAGIAN IMPLEMENTASI — Dashboard & Laporan (~1.5 menit)**

"Untuk implementasi, saya mengerjakan **halaman Dashboard dan halaman Laporan**."

> *[Tunjukkan halaman Dashboard]*

"**Dashboard** adalah halaman utama setelah login. Di bagian atas terdapat **4 kartu ringkasan**: Total Penjualan Hari Ini, Laba Hari Ini, Jumlah Produk, dan Produk Hampir Habis. Setiap kartu menampilkan icon dan nilai yang diambil langsung dari data transaksi."

"Di bawahnya ada **grafik Pendapatan vs Pengeluaran** yang bisa difilter berdasarkan Hari Ini, 7 Hari Terakhir, atau Bulan Ini. Grafik ini menggunakan library **Recharts**."

"Di sisi kanan ada panel **Transaksi Terbaru** yang menampilkan jam, nomor transaksi, total, dan status. Dan di bagian bawah ada **Perhatian Stok** yang menampilkan produk dengan stok di bawah batas minimum."

> *[Pindah ke halaman Laporan]*

"**Halaman Laporan** memiliki **2 tab**. Tab pertama, **Penjualan**, menampilkan total penjualan, jumlah transaksi, grafik tren penjualan harian menggunakan AreaChart, dan tabel riwayat transaksi lengkap."

"Tab kedua, **Laba Rugi**, menampilkan kartu Pendapatan, Modal (HPP), dan Laba Bersih. Ada juga grafik bar chart yang membandingkan Pendapatan vs Modal per hari. Untuk fitur cetak laporan, kami menggunakan fitur Print bawaan browser."

"Demikian kontribusi saya. Terima kasih."

---

---

## 3. FARHAN FAREL NAULI TANJUNG (10124347)

**Bagian Dokumen:** Dokumen Perancangan Perangkat Lunak
**Bagian Implementasi:** Halaman Produk & Stok

### Naskah Video:

> *[Buka dengan webcam, perkenalan]*

"Assalamu'alaikum, perkenalkan nama saya Farhan Farel Nauli Tanjung, NIM 10124347, dari Kelompok 2. Saya akan menjelaskan kontribusi saya."

---

> *[Tampilkan dokumen Perancangan di layar]*

**BAGIAN DOKUMEN — Perancangan PL (~1 menit)**

"Saya mengerjakan **Dokumen Perancangan Perangkat Lunak** yang terbagi menjadi 5 bagian."

"**Pertama, Perancangan Data.** Saya menjabarkan struktur 5 tabel database secara detail — `users`, `categories`, `products`, `transactions`, dan `transaction_items`. Setiap tabel dilengkapi informasi nama field, tipe data, panjang data, kunci (Primary Key / Foreign Key), dan keterangan fungsinya. Contohnya, tabel `products` memiliki field `price` bertipe DECIMAL(12,2) sebagai harga jual, dan `min_stock` bertipe INT sebagai batas minimum stok untuk memicu peringatan."

"**Kedua, Perancangan Arsitektur Menu.** Saya membuat diagram hierarki menu mulai dari Halaman Login/Daftar, masuk ke Menu Utama (Dashboard), lalu bercabang ke 4 kelompok: Kelola Data (Kategori & Produk), Transaksi (Kasir POS), Laporan Keuangan, dan Sistem (Pengaturan Usaha)."

"**Ketiga, Perancangan Antarmuka.** Saya menyiapkan wireframe prototipe untuk 7 halaman utama: Login, Daftar, Dashboard, Produk, Kasir, Laporan, dan Pengaturan."

"**Keempat, Perancangan Pesan.** Saya mendefinisikan 3 jenis pesan sistem: M01 untuk Peringatan Stok Menipis, M02 untuk Konfirmasi Transaksi, dan M03 untuk Konfirmasi Hapus Akun. Masing-masing dilengkapi logo, isi pesan, dan tombol aksi."

"**Kelima, Jaringan Semantik** yang menggambarkan aliran navigasi antar halaman dan pesan-pesan yang muncul di setiap titik interaksi."

---

> *[Buka aplikasi di browser — halaman Produk]*

**BAGIAN IMPLEMENTASI — Produk & Stok (~1.5 menit)**

"Untuk implementasi, saya mengerjakan **halaman Produk & Stok**."

> *[Tunjukkan halaman Produk]*

"Halaman ini adalah pusat manajemen barang dagangan. Di bagian atas ada **toolbar** dengan fitur pencarian produk, filter berdasarkan kategori, dan tombol Tambah Produk."

"Ada juga **toggle tampilan** — pengguna bisa memilih antara **Table View** yang menampilkan data dalam bentuk tabel, atau **Card View** yang menampilkan produk dalam bentuk kartu visual."

> *[Klik tombol Tambah Produk]*

"Saat tombol **Tambah Produk** diklik, muncul modal form yang berisi field: Nama Produk, SKU, Kategori (dengan dropdown yang bisa menambah kategori baru), Satuan, Harga Jual, Harga Modal, Stok Awal, dan Minimum Stok. Ada **validasi** di setiap field — misalnya harga jual tidak boleh lebih kecil dari harga modal."

> *[Tunjukkan status produk]*

"Setiap produk memiliki **status otomatis**: Tersedia jika stok masih cukup, Stok Menipis jika stok sudah mendekati atau di bawah batas minimum, dan Habis jika stok nol. Status ini ditampilkan sebagai badge berwarna."

"Untuk setiap produk, ada **aksi Edit dan Hapus**. Saat edit, form yang sama muncul dengan data yang sudah terisi. Dan fitur hapus dilengkapi konfirmasi terlebih dahulu."

> *[Tunjukkan tab Riwayat Mutasi jika ada, atau jelaskan]*

"Stok produk akan otomatis berkurang ketika ada transaksi penjualan yang berhasil di halaman Kasir."

"Demikian kontribusi saya. Terima kasih."

---

---

## 4. MUHAMMAD FAIZ RIZQULLAH (10124330)

**Bagian Dokumen:** Dokumen Pengujian Perangkat Lunak
**Bagian Implementasi:** Halaman Penjualan / Kasir (POS)

### Naskah Video:

> *[Buka dengan webcam, perkenalan]*

"Assalamu'alaikum, perkenalkan nama saya Muhammad Faiz Rizqullah, NIM 10124330, dari Kelompok 2. Saya akan menjelaskan kontribusi saya."

---

> *[Tampilkan dokumen Pengujian di layar]*

**BAGIAN DOKUMEN — Pengujian PL (~1 menit)**

"Saya mengerjakan **Dokumen Pengujian Perangkat Lunak** yang berisi skenario pengujian Black Box Testing untuk seluruh modul aplikasi UMKMku."

"Saya membuat **tabel test case** yang mencakup pengujian untuk setiap modul:"

"**Modul Login & Register** — saya menguji skenario login dengan kredensial benar dan salah, registrasi dengan email yang sudah terdaftar, dan registrasi dengan data valid."

"**Modul Produk** — saya menguji tambah produk dengan data lengkap, tambah produk dengan field kosong, edit produk, dan hapus produk."

"**Modul Kasir / Penjualan** — saya menguji proses checkout dengan stok mencukupi, checkout dengan stok habis, dan konfirmasi transaksi."

"**Modul Dashboard & Laporan** — saya menguji apakah data ringkasan tampil dengan benar setelah ada transaksi, dan filter periode berjalan sesuai."

"**Modul Pengaturan** — saya menguji simpan perubahan data usaha dan hapus akun."

"Setiap test case berisi kode, skenario, langkah pengujian, hasil yang diharapkan, hasil aktual, dan status Berhasil atau Gagal. Hasilnya, **seluruh test case berhasil** sesuai ekspektasi."

---

> *[Buka aplikasi di browser — halaman Penjualan/Kasir]*

**BAGIAN IMPLEMENTASI — Kasir POS (~1.5 menit)**

"Untuk implementasi, saya mengerjakan **halaman Penjualan atau Kasir POS**."

> *[Tunjukkan layout 2 kolom]*

"Halaman kasir menggunakan **layout 2 kolom**. Di kolom kiri ada **daftar produk** yang bisa dicari menggunakan search bar. Setiap produk ditampilkan dalam bentuk kartu yang menunjukkan nama, harga jual, dan sisa stok. Produk yang stoknya habis akan ditandai dan **tidak bisa dipilih**."

> *[Klik salah satu produk]*

"Saat produk diklik, produk masuk ke **keranjang belanja** di kolom kanan. Di keranjang, pengguna bisa mengatur jumlah (qty) dengan tombol plus dan minus. Sistem otomatis menghitung **subtotal per item** dan **total keseluruhan** secara real-time."

> *[Klik tombol Selesaikan Penjualan]*

"Ketika tombol **Selesaikan Penjualan** ditekan, muncul **modal konfirmasi** yang menampilkan total belanja dan jumlah item. Pengguna bisa memilih Batal atau Ya, Selesaikan."

> *[Konfirmasi transaksi]*

"Setelah dikonfirmasi, sistem mengirim data ke backend melalui API. Backend akan **memvalidasi stok**, **menghitung profit** (selisih harga jual dan harga modal), **mengurangi stok otomatis**, dan **menyimpan transaksi beserta detail item-nya**. Lalu muncul **modal sukses** yang menampilkan nomor transaksi otomatis seperti TRX-00001."

"Transaksi yang berhasil langsung tampil di Dashboard dan Laporan."

"Demikian kontribusi saya. Terima kasih."

---

---

## 5. RASYID KUSUMA (10124335)

**Bagian Dokumen:** Dokumen Proses Bisnis (Flowchart & Visualisasi)
**Bagian Implementasi:** Halaman Login, Register, Pengaturan, dan Layout (Sidebar + TopNav)

### Naskah Video:

> *[Buka dengan webcam, perkenalan]*

"Assalamu'alaikum, perkenalkan nama saya Rasyid Kusuma, NIM 10124335, dari Kelompok 2. Saya akan menjelaskan kontribusi saya."

---

> *[Tampilkan dokumen Proses Bisnis bagian visualisasi]*

**BAGIAN DOKUMEN — Flowchart Proses Bisnis (~1 menit)**

"Saya berkontribusi pada **Dokumen Proses Bisnis**, khususnya pada bagian **Visualisasi Proses Bisnis** — yaitu pembuatan 6 flowchart untuk setiap proses."

"**Flowchart PR-01**, Manajemen Kategori — alurnya dimulai dari masuk menu kategori, input nama, validasi data, lalu simpan ke database."

"**Flowchart PR-02**, Pencatatan Produk — pengguna masuk ke menu produk, input harga dan stok, sistem memvalidasi format angka, lalu simpan."

"**Flowchart PR-03**, Manajemen Akun — pengguna mengisi form registrasi, sistem cek apakah email sudah ada, jika unik maka akun dibuat dan akses login diberikan."

"**Flowchart PR-04**, Transaksi Kasir — pengguna pilih produk, input jumlah, sistem cek stok, jika cukup maka hitung total dan selesaikan transaksi, stok otomatis berkurang."

"**Flowchart PR-05**, Riwayat Transaksi — setelah transaksi selesai, sistem generate payload, format jadi struk/nota, simpan histori ke database."

"**Flowchart PR-06**, Laporan Analitik — pengguna akses dashboard, sistem ambil data histori, kalkulasi omset, lalu tampilkan grafik visual."

"Semua flowchart dibuat menggunakan **diagram Mermaid** agar bisa dirender secara digital."

---

> *[Buka aplikasi di browser]*

**BAGIAN IMPLEMENTASI — Login, Register, Pengaturan, Layout (~1.5 menit)**

"Untuk implementasi, saya mengerjakan **halaman Login, Register, Pengaturan, serta komponen layout aplikasi**."

> *[Tunjukkan halaman Login]*

"**Halaman Login** memiliki form dengan field email dan password. Saat login berhasil, sistem menerima token dari backend Laravel Sanctum, menyimpannya, dan mengarahkan pengguna ke Dashboard. Jika kredensial salah, muncul pesan error."

> *[Tunjukkan halaman Daftar]*

"**Halaman Daftar (Register)** memiliki form yang lebih lengkap: Nama Lengkap, Nama Usaha, Email, Password, dan Konfirmasi Password. Setelah registrasi berhasil, pengguna diarahkan ke halaman Login."

> *[Tunjukkan halaman Pengaturan]*

"**Halaman Pengaturan** menampilkan data profil usaha yang bisa diubah: Nama Usaha, Nama Pemilik, Nomor Telepon, dan Alamat. Ada tombol **Simpan Perubahan** yang menampilkan toast sukses. Di bagian bawah juga ada opsi **Hapus Akun** yang dilengkapi modal konfirmasi — jika dikonfirmasi, seluruh data pengguna akan dihapus secara permanen."

> *[Tunjukkan Sidebar dan TopNav]*

"Terakhir, saya juga mengerjakan **komponen layout** yang digunakan di seluruh halaman. **Sidebar** berisi menu navigasi: Dashboard, Produk & Stok, Penjualan, Laporan, Pengaturan, dan tombol Keluar. Sidebar bisa di-collapse untuk tampilan yang lebih luas. **Top Navigation** menampilkan nama usaha dan nama pemilik yang diambil dari profil pengguna."

"Demikian kontribusi saya. Terima kasih."

---

---

## TIPS UNTUK SEMUA ANGGOTA

1. **Pahami bagianmu** — Baca dan pahami dokumen + coba pakai fitur yang jadi bagianmu, jangan cuma baca script.
2. **Screen recording** — Gunakan OBS, Loom, atau Xbox Game Bar (Windows) untuk rekam layar.
3. **Tampilkan wajah** — Aktifkan webcam di pojok kecil agar terlihat lebih meyakinkan.
4. **Jangan baca teks** — Jelaskan dengan kata-kata sendiri, buat senatural mungkin.
5. **Cek durasi** — Latihan dulu, pastikan tidak lebih dari 3 menit.
6. **Pastikan audio jelas** — Gunakan headset atau mikrofon yang layak.
