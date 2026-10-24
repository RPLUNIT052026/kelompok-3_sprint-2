# ARSITEKTUR SISTEM — ClosetGirls TriftShop

## 1. Diagram Arsitektur

```mermaid
graph TB
    subgraph PRESENTASI[Lapisan Presentasi]
        A[Browser - HTML + CSS + JavaScript]
        A1[Halaman Pengguna - Beranda, Katalog, Detail Produk]
        A2[Halaman Pengguna - Keranjang & Checkout]
        A3[Halaman Admin - Kelola Produk & Pesanan]
    end

    subgraph APLIKASI[Lapisan Aplikasi]
        B[Backend Sistem ClosetGirls TriftShop]
        B1[Autentikasi & Role Pengguna]
        B2[Manajemen Produk & Kategori]
        B3[Manajemen Keranjang]
        B4[Manajemen Pesanan & Stok]
        B5[Proses Pembayaran]
    end

    subgraph DATA[Lapisan Data]
        C[(Database)]
        C1[(Users)]
        C2[(Products)]
        C3[(Orders)]
        C4[(Order Details)]
        C5[(Payments)]
    end

    subgraph EKSTERNAL[Layanan Eksternal]
        D[Simulasi Pembayaran - Dummy]
        E[Payment Gateway - Future]
        F[Notifikasi Pesanan - Future]
    end

    A --> A1
    A --> A2
    A --> A3

    A -->|HTTP Request| B

    B --> B1
    B --> B2
    B --> B3
    B --> B4
    B --> B5

    B -->|Query / CRUD| C

    C --> C1
    C --> C2
    C --> C3
    C --> C4
    C --> C5

    B -->|Konfirmasi Pembayaran| D
    E -.->|Future| B
    B -.->|Future| F
```

---

# 2. Penjelasan Layer

| Layer                 | Komponen                              | Fungsi                                                                                                                |
| --------------------- | ------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Presentasi**        | HTML, CSS, JavaScript                 | Menampilkan halaman website seperti beranda, katalog produk, detail produk, keranjang, checkout, dan dashboard admin. |
| **Aplikasi**          | Backend Sistem                        | Memproses request pengguna, autentikasi, pengelolaan produk, keranjang, pesanan, stok, dan pembayaran.                |
| **Data**              | Database                              | Menyimpan data pengguna, produk thrift, kategori, pesanan, detail pesanan, dan pembayaran.                            |
| **Layanan Eksternal** | Simulasi Pembayaran / Payment Gateway | Digunakan untuk proses dan konfirmasi pembayaran. Payment gateway dapat dikembangkan pada tahap berikutnya.           |

### Gambaran sederhananya:

```text
        PENGGUNA / ADMIN
               ↓
          WEBSITE
       (HTML, CSS, JS)
               ↓
           BACKEND
               ↓
           DATABASE
               ↓
      Data Produk & Pesanan
               ↓
     SIMULASI PEMBAYARAN
```

Jadi pengguna **tidak langsung mengakses database**. Semua permintaan diproses terlebih dahulu oleh sistem/backend.

---

# 3. Alur Komunikasi

## 3.1 Alur Pembelian Produk

```mermaid
sequenceDiagram
    participant U as Pengguna
    participant B as Browser
    participant S as Backend
    participant D as Database
    participant P as Pembayaran

    U->>B: Membuka katalog produk
    B->>S: Request data produk
    S->>D: Mengambil data produk
    D-->>S: Data produk tersedia
    S-->>B: Menampilkan katalog
    B-->>U: Produk ditampilkan

    U->>B: Pilih produk & tambah ke keranjang
    B->>S: Request tambah keranjang
    S->>D: Simpan data keranjang
    D-->>S: Keranjang tersimpan
    S-->>B: Konfirmasi berhasil

    U->>B: Checkout
    B->>S: POST /api/order
    S->>D: Cek stok produk
    D-->>S: Stok tersedia
    S->>D: Simpan data pesanan
    S->>P: Minta proses pembayaran
    P-->>S: Pembayaran berhasil
    S->>D: Update status pesanan
    S->>D: Update stok produk
    S-->>B: Detail pesanan
    B-->>U: Pesanan berhasil
```

---

## 3.2 Alur Admin Menambah Produk

```mermaid
sequenceDiagram
    participant A as Admin
    participant B as Browser
    participant S as Backend
    participant D as Database

    A->>B: Login sebagai admin
    B->>S: Kirim data login
    S->>D: Validasi akun
    D-->>S: Role = admin
    S-->>B: Login berhasil

    A->>B: Isi form produk
    B->>S: POST /api/products
    S->>S: Validasi data produk
    S->>D: INSERT data produk
    D-->>S: Data berhasil disimpan
    S-->>B: Konfirmasi berhasil
    B-->>A: Produk tampil di katalog
```

---

# 4. Rancangan Tabel Database

```mermaid
erDiagram
    USERS ||--o{ ORDERS : membuat
    PRODUCTS ||--o{ ORDER_DETAILS : dipesan
    ORDERS ||--|{ ORDER_DETAILS : memiliki
    ORDERS ||--o| PAYMENTS : memiliki
    CATEGORIES ||--o{ PRODUCTS : memiliki

    USERS {
        int id PK
        string username
        string password_hash
        string role
        string email
    }

    CATEGORIES {
        int id PK
        string nama_kategori
    }

    PRODUCTS {
        int id PK
        int category_id FK
        string nama_produk
        string deskripsi
        int harga
        int stok
        string ukuran
        string kondisi
        string foto
    }

    ORDERS {
        int id PK
        int user_id FK
        int total_harga
        string status
        string alamat
        datetime created_at
    }

    ORDER_DETAILS {
        int id PK
        int order_id FK
        int product_id FK
        int jumlah
        int harga
    }

    PAYMENTS {
        int id PK
        int order_id FK
        int jumlah
        string metode
        string status
        datetime paid_at
    }
```

### Penjelasan singkat database

* **USERS** → menyimpan data akun pengguna dan admin.
* **CATEGORIES** → menyimpan kategori pakaian/produk thrift.
* **PRODUCTS** → menyimpan informasi produk yang dijual.
* **ORDERS** → menyimpan data pesanan pengguna.
* **ORDER_DETAILS** → menyimpan rincian produk yang ada dalam pesanan.
* **PAYMENTS** → menyimpan informasi pembayaran.

---

# 5. Teknologi yang Digunakan

| Komponen            | Teknologi                | Alasan                                                              |
| ------------------- | ------------------------ | ------------------------------------------------------------------- |
| **Frontend**        | HTML + CSS + JavaScript  | Digunakan untuk membangun tampilan dan interaksi website.           |
| **Backend**         | Python + Flask           | Digunakan untuk menangani request dan logika sistem.                |
| **Database**        | SQLite                   | Ringan dan mudah digunakan untuk project skala kecil/menengah.      |
| **Keamanan**        | Password Hashing         | Password pengguna tidak disimpan dalam bentuk teks biasa.           |
| **Pembayaran**      | Simulasi / Dummy Payment | Memudahkan proses demonstrasi tanpa membutuhkan akun merchant asli. |
| **Version Control** | Git + GitHub             | Digunakan untuk menyimpan dan mengelola source code project.        |
| **Diagram**         | Mermaid                  | Digunakan untuk membuat diagram arsitektur, sequence, dan ERD.      |
| **Desain UI/UX**    | Figma                    | Digunakan untuk membuat rancangan antarmuka website.                |

---

# 6. Kelebihan Arsitektur Ini

* **Modular** — setiap bagian sistem memiliki fungsi yang berbeda sehingga lebih mudah dikembangkan.
* **Sederhana** — menggunakan teknologi yang relatif ringan dan sesuai untuk project mahasiswa.
* **Terstruktur** — frontend, backend, dan database memiliki pembagian tugas yang jelas.
* **Mudah dikembangkan** — sistem dapat ditambahkan fitur seperti payment gateway dan notifikasi pada tahap berikutnya.
* **Mudah dikelola** — admin dapat mengelola produk, stok, dan pesanan melalui sistem.
* **Lebih aman** — terdapat autentikasi pengguna dan pembagian role antara pengguna dan admin.
* **Mendukung pengembangan bertahap** — fitur dasar dapat dibuat terlebih dahulu kemudian dikembangkan sesuai kebutuhan.

---
