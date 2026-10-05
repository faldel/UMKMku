# DOKUMENTASI ANALISIS KEBUTUHAN PERANGKAT LUNAK

<table>
  <tr>
    <td width="25%"><b>DIBUAT UNTUK</b></td>
    <td width="5%">:</td>
    <td width="70%">Aplikasi Pencatatan Stok, Penjualan Kasir, dan Pemantauan Arus Kas Harian</td>
  </tr>
  <tr>
    <td><b>DIBUAT OLEH</b></td>
    <td>:</td>
    <td>
      Kelompok 2<br><br>
      1. RD. Fariz Nur Syawaluddin (10124445)<br>
      2. Mohamad Rifaldy Firdaus (10123095)<br>
      3. Farhan Farel Nauli Tanjung (10124347)<br>
      4. Muhammad Faiz Rizqullah (10124330)<br>
      5. Rasyid Kusuma (10124335)
    </td>
  </tr>
  <tr>
    <td><b>NAMA SOFTWARE</b></td>
    <td>:</td>
    <td>UMKMku</td>
  </tr>
</table>

## VERSI DOKUMEN

<table>
  <tr>
    <td width="25%"><b>Versi</b></td>
    <td width="5%">:</td>
    <td width="70%">1.0</td>
  </tr>
  <tr>
    <td><b>Tanggal</b></td>
    <td>:</td>
    <td>2 Agustus 2026</td>
  </tr>
  <tr>
    <td><b>Divalidasi oleh</b></td>
    <td>:</td>
    <td>RD. Fariz Nur Syawaluddin</td>
  </tr>
  <tr>
    <td><b>Tanda Tangan</b></td>
    <td>:</td>
    <td><br><br><br></td>
  </tr>
</table>

<br>

---

## ANALISIS DATA

### 1. Identifikasi Data

| Nomor Data | Nama Data | Atribut | Keterangan |
| :--- | :--- | :--- | :--- |
| **Dt-01** | Data Pengguna (Users) | `id`, `name`, `business_name`, `email`, `password` | Data autentikasi dan identitas pemilik usaha yang mengelola sistem. |
| **Dt-02** | Data Kategori | `id`, `user_id`, `name`, `description` | Data klasifikasi kelompok produk yang dibuat oleh pengguna. |
| **Dt-03** | Data Produk | `id`, `user_id`, `category_id`, `name`, `price`, `stock` | Data master barang yang dijual di kasir, memuat harga dan ketersediaan stok fisik. |
| **Dt-04** | Data Transaksi | `id`, `user_id`, `receipt_number`, `total_amount`, `payment_method`, `created_at` | Data rekam jejak penjualan (nota) beserta total pendapatan per transaksi. |
| **Dt-05** | Data Item Transaksi | `id`, `transaction_id`, `product_id`, `quantity`, `price`, `subtotal` | Data rincian barang apa saja yang dibeli pada satu transaksi tertentu. |

### 2. Pemodelan Data (ERD)

**Gambar 1: Model ER Konseptual (Chen's Notation)**

```mermaid
%%{init: {"flowchart": {"curve": "linear"}}}%%
flowchart TD
    classDef entity fill:#fff,stroke:#333,stroke-width:1px,color:#000;
    classDef attr fill:#fff,stroke:#333,stroke-width:1px,color:#000;
    classDef rel fill:#fff,stroke:#333,stroke-width:1px,color:#000;

    %% Entities
    E1[PENGGUNA]:::entity
    E2[KATEGORI]:::entity
    E3[PRODUK]:::entity
    E4[TRANSAKSI]:::entity
    E5[DETAIL TRANSAKSI]:::entity

    %% Relationships
    R1{MEMBUAT}:::rel
    R2{MEMILIKI}:::rel
    R3{MELAKUKAN}:::rel
    R4{TERDIRI DARI}:::rel
    R5{TERJUAL DI}:::rel

    %% Attributes Pengguna
    A1_1([id]):::attr
    A1_2([nama_lengkap]):::attr
    A1_3([nama_usaha]):::attr
    A1_4([email]):::attr
    A1_1 --- E1
    A1_2 --- E1
    A1_3 --- E1
    A1_4 --- E1

    %% Attributes Kategori
    A2_1([id]):::attr
    A2_2([nama_kategori]):::attr
    A2_1 --- E2
    A2_2 --- E2

    %% Attributes Produk
    A3_1([id]):::attr
    A3_2([nama_produk]):::attr
    A3_3([harga]):::attr
    A3_4([stok]):::attr
    A3_1 --- E3
    A3_2 --- E3
    A3_3 --- E3
    A3_4 --- E3

    %% Attributes Transaksi
    A4_1([id]):::attr
    A4_2([no_struk]):::attr
    A4_3([total_harga]):::attr
    A4_1 --- E4
    A4_2 --- E4
    A4_3 --- E4

    %% Attributes Detail Transaksi
    A5_1([id]):::attr
    A5_2([jumlah_barang]):::attr
    A5_3([subtotal]):::attr
    A5_1 --- E5
    A5_2 --- E5
    A5_3 --- E5

    %% Connections (Cardinality)
    E1 ---|1| R1 ---|N| E2
    E2 ---|1| R2 ---|N| E3
    E1 ---|1| R3 ---|N| E4
    E4 ---|1| R4 ---|N| E5
    E3 ---|1| R5 ---|N| E5
```

**Gambar 2: Diagram Relasi Database (Physical Data Model)**

```mermaid
erDiagram
    USERS ||--o{ CATEGORIES : "mengelola"
    USERS ||--o{ PRODUCTS : "mengelola"
    USERS ||--o{ TRANSACTIONS : "melakukan"
    CATEGORIES ||--o{ PRODUCTS : "memiliki"
    TRANSACTIONS ||--|{ TRANSACTION_ITEMS : "terdiri dari"
    PRODUCTS ||--o{ TRANSACTION_ITEMS : "terjual pada"

    USERS {
        bigint id PK
        string name
        string business_name
        string email
        timestamp email_verified_at
        string password
        string remember_token
        timestamp created_at
        timestamp updated_at
    }
    CATEGORIES {
        bigint id PK
        bigint user_id FK
        string name
        string description
        timestamp created_at
        timestamp updated_at
    }
    PRODUCTS {
        bigint id PK
        bigint user_id FK
        bigint category_id FK
        string name
        string sku
        string unit
        decimal price
        decimal cost_price
        integer stock
        integer min_stock
        timestamp created_at
        timestamp updated_at
    }
    TRANSACTIONS {
        bigint id PK
        bigint user_id FK
        decimal total_amount
        decimal total_profit
        string payment_method
        string status
        timestamp created_at
        timestamp updated_at
    }
    TRANSACTION_ITEMS {
        bigint id PK
        bigint transaction_id FK
        bigint product_id FK
        integer quantity
        decimal price
        decimal subtotal
        decimal cost_price
        timestamp created_at
        timestamp updated_at
    }
```

<br>

---

## ANALISIS KEBUTUHAN FUNGSIONAL

### 1. Identifikasi Kebutuhan Fungsional

| Kode Kebutuhan | Deskripsi Kebutuhan |
| :--- | :--- |
| **KK-1** | Sistem harus dapat memfasilitasi pembuatan akun baru (Registrasi), proses masuk (Login), dan menghapus akun beserta seluruh data relasinya secara permanen. |
| **KK-2** | Pemilik Usaha dapat melakukan pencatatan, pembaruan, dan penghapusan terhadap data Kategori Barang dan Data Produk secara terstruktur. |
| **KK-3** | Sistem harus menyediakan antarmuka Kasir (POS) yang mampu menghitung total belanja dan memotong stok produk secara otomatis saat transaksi berhasil. |
| **KK-4** | Sistem harus mampu merekapitulasi riwayat transaksi harian dan menyajikannya dalam bentuk laporan grafik analitik (Dashboard). |

### 2. Diagram Konteks

**Gambar 2: Diagram Konteks (Context Diagram)**

```mermaid
%%{init: {"flowchart": {"curve": "stepAfter"}}}%%
flowchart LR
    classDef default fill:#fff,stroke:#333,stroke-width:1px,color:#000;
    
    USR[Pemilik Usaha]
    SYS((SISTEM UMKMku))
    
    USR --->|"1. Data Kredensial Akun\n2. Data Produk & Kategori\n3. Input Transaksi Kasir"| SYS
    SYS --->|"1. Status Autentikasi (Token)\n2. Peringatan Stok Kurang\n3. Laporan Omset & Riwayat"| USR
```

### 3. Data Flow Diagram (DFD Level 0)

**Gambar 3: DFD Level 0**

```mermaid
flowchart LR
    classDef default fill:#fff,stroke:#333,stroke-width:1px,color:#000;
    
    %% Entitas Eksternal
    USR[Pemilik Usaha]
    
    %% Proses
    P1((1.0 Kelola Akun))
    P2((2.0 Kelola Barang))
    P3((3.0 Kelola Transaksi))
    P4((4.0 Kelola Laporan))
    
    %% Data Store
    D1[(D1 Data Users)]
    D2[(D2 Data Barang)]
    D3[(D3 Data Transaksi)]
    
    %% Alur dari Entitas ke Proses
    USR --->|"Data Registrasi"| P1
    P1 --->|"Token / Status"| USR
    
    USR --->|"Input Data Barang"| P2
    P2 --->|"Data Barang"| USR
    
    USR --->|"Input Penjualan"| P3
    P3 --->|"Struk Transaksi"| USR
    
    USR --->|"Request Laporan"| P4
    P4 --->|"Grafik Dashboard"| USR
    
    %% Alur dari Proses ke Data Store
    P1 --->|"Simpan Data"| D1
    D1 --->|"Validasi Akun"| P1
    
    P2 --->|"Simpan Stok"| D2
    D2 --->|"Data Stok"| P2
    
    P3 --->|"Potong Stok"| D2
    P3 --->|"Simpan Histori"| D3
    
    D3 --->|"Data Histori"| P4
```

### 4. Spesifikasi Proses

#### PROSES 1.0 - Kelola Akun & Autentikasi
<table>
  <tr><td width="25%"><b>No Urut.</b></td><td width="25%"><b>Proses</b></td><td width="50%"><b>Keterangan</b></td></tr>
  <tr><td rowspan="7"><b>PROSES 1</b></td><td><b>No. Proses</b></td><td>1.0</td></tr>
  <tr><td><b>Nama Proses</b></td><td>Kelola Akun & Autentikasi Pengguna</td></tr>
  <tr><td><b>Source (sumber)</b></td><td>Pemilik Usaha (User)</td></tr>
  <tr><td><b>Input</b></td><td>Data Registrasi (Email, Kata Sandi, Nama Usaha)</td></tr>
  <tr><td><b>Output</b></td><td>Akses masuk sistem (Token) atau Peringatan Error</td></tr>
  <tr><td><b>Destination (tujuan)</b></td><td>D1 Data Users, Pemilik Usaha</td></tr>
  <tr>
    <td><b>Logika Proses</b></td>
    <td>1. User menginput form registrasi/login.<br>2. Sistem memvalidasi ketersediaan email di D1.<br>3. Jika valid, sistem menyimpan data ke D1.<br>4. Sistem menampilkan status berhasil dan memberikan akses (Token).</td>
  </tr>
</table>

**Flowchart Proses 1**
```mermaid
%%{init: {"flowchart": {"curve": "linear"}}}%%
flowchart TD
    classDef default fill:#fff,stroke:#333,stroke-width:1px,color:#000;
    
    Start([Mulai])
    Input[/Data Registrasi atau Login/]
    Proses[Sistem Memvalidasi Input]
    Cek{Email Valid / Unik?}
    Simpan[Simpan Akun ke D1]
    Output[\Akses Diberikan / Token\]
    End([Selesai])
    
    Start --> Input
    Input --> Proses
    Proses --> Cek
    Cek -- Tidak --> Input
    Cek -- Ya --> Simpan
    Simpan --> Output
    Output --> End
```

<br>

#### PROSES 2.0 - Kelola Barang & Kategori
<table>
  <tr><td width="25%"><b>No Urut.</b></td><td width="25%"><b>Proses</b></td><td width="50%"><b>Keterangan</b></td></tr>
  <tr><td rowspan="7"><b>PROSES 2</b></td><td><b>No. Proses</b></td><td>2.0</td></tr>
  <tr><td><b>Nama Proses</b></td><td>Kelola Data Barang & Kategori</td></tr>
  <tr><td><b>Source (sumber)</b></td><td>Pemilik Usaha (User)</td></tr>
  <tr><td><b>Input</b></td><td>Data Kategori dan Data Produk (Harga, Stok)</td></tr>
  <tr><td><b>Output</b></td><td>Ketersediaan stok dan data barang ter-update</td></tr>
  <tr><td><b>Destination (tujuan)</b></td><td>D2 Data Kategori & Produk, Pemilik Usaha</td></tr>
  <tr>
    <td><b>Logika Proses</b></td>
    <td>1. User menginput data kategori atau produk baru.<br>2. Sistem memvalidasi format angka (harga/stok).<br>3. Sistem menyimpan data ke D2.<br>4. Sistem menampilkan notifikasi produk berhasil ditambahkan.</td>
  </tr>
</table>

**Flowchart Proses 2**
```mermaid
%%{init: {"flowchart": {"curve": "linear"}}}%%
flowchart TD
    classDef default fill:#fff,stroke:#333,stroke-width:1px,color:#000;
    
    Start([Mulai])
    Input[/Data Kategori & Produk Baru/]
    Proses[Sistem Memvalidasi Format Data]
    Cek{Format Angka Valid?}
    Simpan[Simpan ke Database D2]
    Output[\Notifikasi Berhasil & Stok Update\]
    End([Selesai])
    
    Start --> Input
    Input --> Proses
    Proses --> Cek
    Cek -- Tidak --> Input
    Cek -- Ya --> Simpan
    Simpan --> Output
    Output --> End
```

<br>

#### PROSES 3.0 - Kelola Transaksi Kasir
<table>
  <tr><td width="25%"><b>No Urut.</b></td><td width="25%"><b>Proses</b></td><td width="50%"><b>Keterangan</b></td></tr>
  <tr><td rowspan="7"><b>PROSES 3</b></td><td><b>No. Proses</b></td><td>3.0</td></tr>
  <tr><td><b>Nama Proses</b></td><td>Kelola Transaksi Kasir POS</td></tr>
  <tr><td><b>Source (sumber)</b></td><td>Pemilik Usaha (User)</td></tr>
  <tr><td><b>Input</b></td><td>Pilihan produk dan kuantitas (Qty) belanja</td></tr>
  <tr><td><b>Output</b></td><td>Pengurangan stok di D2, Pencatatan riwayat di D3</td></tr>
  <tr><td><b>Destination (tujuan)</b></td><td>D2 Data Produk, D3 Data Transaksi, Pemilik Usaha</td></tr>
  <tr>
    <td><b>Logika Proses</b></td>
    <td>1. User memilih produk untuk dijual.<br>2. Sistem mengecek ketersediaan stok fisik di D2.<br>3. Sistem menjumlahkan total tagihan otomatis.<br>4. Setelah dibayar, sistem memotong stok D2 dan mencatat histori penjualan ke D3.</td>
  </tr>
</table>

**Flowchart Proses 3**
```mermaid
%%{init: {"flowchart": {"curve": "linear"}}}%%
flowchart TD
    classDef default fill:#fff,stroke:#333,stroke-width:1px,color:#000;
    
    Start([Mulai])
    Input[/Input Barang Belanja & Qty/]
    Proses[Sistem Mengecek Ketersediaan]
    Cek{Stok Mencukupi?}
    Simpan[Potong Stok D2 & Simpan Histori D3]
    Output[\Generate Struk Transaksi\]
    End([Selesai])
    
    Start --> Input
    Input --> Proses
    Proses --> Cek
    Cek -- Tidak --> Input
    Cek -- Ya --> Simpan
    Simpan --> Output
    Output --> End
```

<br>

#### PROSES 4.0 - Kelola Laporan & Dashboard
<table>
  <tr><td width="25%"><b>No Urut.</b></td><td width="25%"><b>Proses</b></td><td width="50%"><b>Keterangan</b></td></tr>
  <tr><td rowspan="7"><b>PROSES 4</b></td><td><b>No. Proses</b></td><td>4.0</td></tr>
  <tr><td><b>Nama Proses</b></td><td>Kelola Laporan Analitik & Dashboard</td></tr>
  <tr><td><b>Source (sumber)</b></td><td>D3 Data Transaksi</td></tr>
  <tr><td><b>Input</b></td><td>Permintaan akses laporan dari User</td></tr>
  <tr><td><b>Output</b></td><td>Grafik omset harian dan daftar riwayat transaksi</td></tr>
  <tr><td><b>Destination (tujuan)</b></td><td>Pemilik Usaha (User)</td></tr>
  <tr>
    <td><b>Logika Proses</b></td>
    <td>1. User membuka halaman Dashboard.<br>2. Sistem mengambil data rekapitulasi penjualan dari D3.<br>3. Sistem mengkalkulasi total omset dan jumlah produk terjual.<br>4. Laporan disajikan dalam bentuk antarmuka visual grafik/tabel.</td>
  </tr>
</table>

**Flowchart Proses 4**
```mermaid
%%{init: {"flowchart": {"curve": "linear"}}}%%
flowchart TD
    classDef default fill:#fff,stroke:#333,stroke-width:1px,color:#000;
    
    Start([Mulai])
    Input[/Akses Halaman Dashboard/]
    Proses[Sistem Menarik Data dari D3]
    Cek{Data Transaksi Tersedia?}
    Simpan[Kalkulasi Omset Harian]
    Output[\Tampilkan Grafik Visual\]
    End([Selesai])
    
    Start --> Input
    Input --> Proses
    Proses --> Cek
    Cek -- Tidak --> Output
    Cek -- Ya --> Simpan
    Simpan --> Output
    Output --> End
```

### 5. Kamus Data

| Nama | Data Produk |
| :--- | :--- |
| **Where used / how used** | Proses 2.0 Kelola Data Barang & Kategori |
| **Deskripsi** | Menyimpan informasi master barang yang akan dijual di kasir. |
| **Struktur Data** | `id` + `user_id` + `category_id` + `name` + `sku` + `unit` + `price` + `cost_price` + `stock` + `min_stock` + `timestamps` |
| **Penjelasan per struktur data** | `id` = [Integer] Auto Increment PK<br>`user_id` = [Integer] Relasi Pemilik<br>`category_id` = [Integer] Relasi Kategori<br>`name` = [String] Nama Barang<br>`sku` = [String] Kode SKU<br>`unit` = [String] Satuan Barang<br>`price` = [Decimal] Harga Jual<br>`cost_price` = [Decimal] Harga Modal<br>`stock` = [Integer] Stok Tersedia<br>`min_stock` = [Integer] Batas Minimum Stok |

<br>

---

## ANALISIS KEBUTUHAN NON FUNGSIONAL

### 1. Analisis Kebutuhan Perangkat Lunak

**a. Perangkat lunak yang ada di sistem berjalan (Fakta)**
| No | Nama Perangkat Lunak | Spesifikasi yang ada |
| :--- | :--- | :--- |
| 1 | Sistem Operasi | Windows 10 / 11 |
| 2 | Browser | Google Chrome / Microsoft Edge |
| 3 | Code Editor | Visual Studio Code |

**b. Kebutuhan minimum perangkat lunak**
| No | Nama Perangkat Lunak | Spesifikasi minimum |
| :--- | :--- | :--- |
| 1 | Sistem Operasi | Windows, macOS, atau Linux (Bebas) |
| 2 | Browser | Google Chrome, Safari, Firefox (Modern Browser) |
| 3 | Kebutuhan Jaringan | Akses Internet Stabil (Aplikasi Cloud-based) |

**c. Kesimpulan:**
Karena UMKMku telah dideploy secara penuh ke Cloud (Vercel, Render, Aiven), pengguna akhir (Pemilik Usaha) tidak memerlukan instalasi *web server* lokal (XAMPP) maupun *database*. Selama pengguna memiliki *modern browser* dan koneksi internet, aplikasi dapat langsung digunakan.

### 2. Analisis Kebutuhan Perangkat Keras

**a. Perangkat keras yang ada di sistem berjalan**
| No | Nama Perangkat Keras | Spesifikasi yang ada |
| :--- | :--- | :--- |
| 1 | Laptop / PC | Prosesor standar, RAM minimal 4 GB |
| 2 | Perangkat Jaringan | Modem / Wi-Fi Router |
| 3 | Handphone | Smartphone iOS / Android |

**b. Kebutuhan minimum perangkat keras**
| No | Nama Perangkat Keras | Spesifikasi minimum |
| :--- | :--- | :--- |
| 1 | Laptop / Tablet / HP | Perangkat apa pun yang memiliki layar dan peramban web (browser). |
| 2 | Perangkat Jaringan | Koneksi seluler atau Wi-Fi standar. |

**c. Kesimpulan:**
Sistem berbasis antarmuka web yang sangat ringan dan responsif. Tidak dibutuhkan pengadaan perangkat keras (hardware) khusus seperti komputer kasir ber-spesifikasi tinggi, karena aplikasi berjalan mulus di *smartphone* atau *laptop* biasa.

### 3. Analisis Kebutuhan Perangkat Pikir (Brainware)

**a. Perangkat Pikir yang ada di sistem berjalan**
| Stakeholder | Tanggung Jawab | Tingkat Pendidikan | Tingkat Keterampilan | Pengalaman Menggunakan Komputer |
| :--- | :--- | :--- | :--- | :--- |
| **Pemilik Usaha (User)** | Melakukan input data kategori, produk, transaksi penjualan, dan melihat laporan omset. | Minimal SMA / Sederajat | Mampu mengoperasikan aplikasi kasir sederhana dan mengakses browser internet. | Terbiasa menggunakan aplikasi di smartphone dan browser internet dasar. |

**b. Kebutuhan perangkat pikir**
| Pengguna Sistem | Hak Akses | Tingkat Keterampilan | Pengalaman Harus Dimiliki | Jenis Pelatihan yang Diberikan |
| :--- | :--- | :--- | :--- | :--- |
| **Pemilik Usaha (User)** | Akses Penuh (Manajemen Barang, Transaksi, Laporan, Akun) | Mampu mengoperasikan peramban web (*web browser*) di HP atau Laptop. | Pemahaman dasar tentang stok barang dan perhitungan jual beli. | Pelatihan cara menambahkan barang, memproses transaksi kasir, dan membaca grafik dashboard. |

**c. Kesimpulan:**
Sistem UMKMku dirancang dengan pendekatan *User-Friendly* dan *Minimalist*. Pemilik usaha tidak memerlukan kemampuan IT tingkat lanjut. Dengan keterampilan operasional HP/Komputer dasar, pengguna dapat langsung menjalankan operasional kasirnya secara efektif tanpa panduan yang rumit.
