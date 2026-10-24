# RANCANGAN UX/UI — ClosetGirls TriftShop

## 1. Tujuan Desain

Merancang antarmuka **ClosetGirls TriftShop** yang mudah digunakan untuk mencari, melihat, dan membeli produk thrift secara online. Desain dibuat sederhana, rapi, dan memudahkan pengguna dalam melihat informasi produk seperti foto, harga, ukuran, kondisi, stok, serta status pesanan.

Selain untuk pembeli, antarmuka admin dirancang untuk memudahkan pengelolaan produk, kategori, dan pesanan.

---

# 2. User Flow

### Alur Pembeli

```mermaid
graph LR
    A[Login] --> B[Beranda / Katalog]
    B --> C[Detail Produk]
    C --> D[Keranjang]
    D --> E[Checkout]
    E --> F[Pembayaran]
    F --> G[Konfirmasi Pesanan]
    B --> H[Riwayat Pesanan]
    G --> H
```

### Alur Admin

```mermaid
graph LR
    A[Login] --> B[Dashboard Admin]
    B --> C[Kelola Produk]
    B --> D[Kelola Kategori]
    B --> E[Daftar Pesanan]
    C --> F[Tambah / Edit / Hapus Produk]
    D --> G[Tambah / Edit / Hapus Kategori]
    E --> H[Lihat Detail Pesanan]
```

---

# 3. Wireframe Halaman

### A. Halaman Login

```text
┌──────────────────────────────────────┐
│                                      │
│         CLOSETGIRLS TRIFTSHOP       │
│                                      │
│   ┌────────────────────────────────┐ │
│   │ Username                       │ │
│   └────────────────────────────────┘ │
│   ┌────────────────────────────────┐ │
│   │ Password                       │ │
│   └────────────────────────────────┘ │
│                                      │
│   ┌────────────────────────────────┐ │
│   │           [ LOGIN ]            │ │
│   └────────────────────────────────┘ │
│                                      │
└──────────────────────────────────────┘
```

---

### B. Halaman Beranda / Katalog Produk

```text
┌──────────────────────────────────────────────────────────────────┐
│  ClosetGirls      [Beranda] [Produk] [Riwayat] [Logout]         │
├──────────────────────────────────────────────────────────────────┤
│  Cari produk: [ __________________ ]  [ Cari ]                   │
│                                                                  │
│  Kategori: [Semua v]    Harga: [Semua v]    [ Filter ]          │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐  │
│  │     FOTO         │ │     FOTO         │ │     FOTO         │  │
│  │                  │ │                  │ │                  │  │
│  │ Vintage Blouse   │ │ Denim Jacket     │ │ Pleated Skirt    │  │
│  │ Atasan           │ │ Outer            │ │ Rok              │  │
│  │ Rp 75.000        │ │ Rp 120.000       │ │ Rp 85.000        │  │
│  │ [ Tersedia ]     │ │ [ Tersedia ]     │ │ [ Tersedia ]     │  │
│  │ [ Detail ]       │ │ [ Detail ]       │ │ [ Detail ]       │  │
│  └──────────────────┘ └──────────────────┘ └──────────────────┘  │
│                                                                  │
│                    < 1  2  3  4 >                               │
└──────────────────────────────────────────────────────────────────┘
```

---

### C. Halaman Detail Produk

```text
┌──────────────────────────────────────────────────────────────────┐
│  <- Kembali             DETAIL PRODUK                            │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌────────────────────┐     Nama      : Vintage Blouse           │
│  │                    │     Kategori  : Atasan                  │
│  │       FOTO         │     Harga     : Rp 75.000               │
│  │      PRODUK        │     Ukuran    : M                        │
│  │                    │     Kondisi   : Sangat Baik              │
│  └────────────────────┘     Stok      : 1                        │
│                                                                  │
│  Deskripsi :                                                     │
│  Blouse vintage dengan kondisi baik dan masih layak digunakan.   │
│                                                                  │
│                              [ MASUKKAN KERANJANG ]              │
└──────────────────────────────────────────────────────────────────┘
```

---

### D. Halaman Keranjang

```text
┌──────────────────────────────────────────────────────────────────┐
│  <- Kembali                KERANJANG                             │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Produk             Harga       Jumlah       Subtotal            │
│  ─────────────────────────────────────────────────────────────── │
│  Vintage Blouse     Rp 75.000      1         Rp 75.000          │
│  Denim Jacket       Rp 120.000     1         Rp 120.000         │
│                                                                  │
├──────────────────────────────────────────────────────────────────┤
│  Total Harga : Rp 195.000                                        │
│                                                                  │
│                       [ LANJUT CHECKOUT ]                        │
└──────────────────────────────────────────────────────────────────┘
```

---

### E. Halaman Checkout & Pembayaran

```text
┌──────────────────────────────────────────────────────────────────┐
│  <- Kembali             CHECKOUT                                 │
├──────────────────────────────────────────────────────────────────┤
│  RINGKASAN PESANAN                                               │
│                                                                  │
│  Vintage Blouse       Rp 75.000                                  │
│  Denim Jacket         Rp 120.000                                 │
│                                                                  │
│  Total Bayar          Rp 195.000                                 │
├──────────────────────────────────────────────────────────────────┤
│  ALAMAT PENGIRIMAN                                               │
│  [ ______________________________________________ ]              │
│                                                                  │
│  METODE PEMBAYARAN (SIMULASI)                                    │
│  ( ) Transfer Bank    ( ) E-Wallet    ( ) QRIS                   │
│                                                                  │
├──────────────────────────────────────────────────────────────────┤
│                 [ BATAL ]    [ BAYAR SEKARANG ]                  │
└──────────────────────────────────────────────────────────────────┘
```

---

### F. Halaman Pembayaran Berhasil

```text
┌──────────────────────────────────────────────────────────────────┐
│                    PESANAN BERHASIL                              │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ✓ PEMBAYARAN BERHASIL                                          │
│                                                                  │
│  No. Pesanan : #CG-0012                                         │
│  Status      : [ PAID ]                                         │
│                                                                  │
│  DETAIL PESANAN                                                  │
│  Vintage Blouse       Rp 75.000                                  │
│  Denim Jacket         Rp 120.000                                 │
│                                                                  │
│  Total                 Rp 195.000                                │
│                                                                  │
│  Alamat :                                                        │
│  Jl. Contoh No. 10, Langsa                                      │
│                                                                  │
├──────────────────────────────────────────────────────────────────┤
│              [ Lihat Riwayat ]   [ Kembali ke Katalog ]          │
└──────────────────────────────────────────────────────────────────┘
```

---

### G. Halaman Riwayat Pesanan

```text
┌──────────────────────────────────────────────────────────────────┐
│  <- Kembali             RIWAYAT PESANAN                          │
├──────────────────────────────────────────────────────────────────┤
│  Filter: [Status v] [Tanggal] [Cari]                             │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  No. Order | Produk          | Total    | Status  | Aksi         │
│  ----------|-----------------|----------|---------|------------- │
│  #CG-0012  | Vintage Blouse  | 75.000   | Paid    | Lihat        │
│  #CG-0011  | Denim Jacket    | 120.000  | Pending | Bayar        │
│  #CG-0009  | Pleated Skirt   | 85.000   | Batal   | Lihat        │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

### H. Dashboard Admin

```text
┌──────────────────────────────────────────────────────────────────┐
│  Dashboard Admin    [Produk] [Kategori] [Pesanan] [Logout]      │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐│
│  │   PRODUK    │ │   STOK      │ │    ORDER    │ │    ORDER    ││
│  │   AKTIF     │ │   TERSEDIA  │ │   PENDING   │ │    PAID     ││
│  │     24      │ │     18      │ │      3      │ │     12      ││
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘│
│                                                                  │
├──────────────────────────────────────────────────────────────────┤
│  Pesanan Terbaru                                                 │
│                                                                  │
│  No. Order | Pembeli | Total       | Status                     │
│  ----------|---------|-------------|----------------------------│
│  #CG-0012  | Aisy    | Rp 195.000  | Paid                       │
│  #CG-0011  | Anisa   | Rp 120.000  | Pending                    │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

### I. Halaman Kelola Produk — Admin

```text
┌──────────────────────────────────────────────────────────────────┐
│  <- Dashboard          KELOLA PRODUK                             │
├──────────────────────────────────────────────────────────────────┤
│  [ + Tambah Produk ]             Cari: [ _____________ ]         │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ID | Produk          | Kategori | Harga   | Stok | Aksi         │
│  ---|-----------------|----------|---------|------|------------- │
│  01 | Vintage Blouse  | Atasan   | 75.000  | 1    | Edit Hapus   │
│  02 | Denim Jacket    | Outer    | 120.000 | 1    | Edit Hapus   │
│                                                                  │
├──────────────────────────────────────────────────────────────────┤
│  FORM PRODUK BARU                                                 │
│                                                                  │
│  Nama Produk : [ __________________________ ]                    │
│  Kategori    : [ Atasan / Outer / Rok / ... v ]                  │
│  Harga       : [ Rp __________ ]                                 │
│  Stok        : [ ______ ]                                        │
│  Ukuran      : [ ______ ]                                        │
│  Kondisi     : [ ______ ]                                        │
│  Foto        : [ Pilih File ]                                    │
│  Deskripsi   : [ __________________________ ]                    │
│                                                                  │
│                     [ BATAL ]  [ SIMPAN PRODUK ]                 │
└──────────────────────────────────────────────────────────────────┘
```

---

### J. Halaman Kelola Kategori — Admin

```text
┌──────────────────────────────────────────────────────────────────┐
│  <- Dashboard          KELOLA KATEGORI                           │
├──────────────────────────────────────────────────────────────────┤
│  [ + Tambah Kategori ]             Cari: [ __________ ]          │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ID | Nama Kategori | Deskripsi                 | Aksi            │
│  ---|---------------|---------------------------|----------------│
│  01 | Atasan        | Produk atasan wanita     | Edit Hapus      │
│  02 | Outer         | Jaket dan outer          | Edit Hapus      │
│  03 | Rok           | Berbagai jenis rok      | Edit Hapus      │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

---

# 4. Palet Warna & Indikator

Untuk ClosetGirls, warna dibuat lebih sesuai dengan konsep **thrift fashion** dan tetap mudah dibaca.

| Elemen          | Warna      | Kode      | Keterangan                            |
| --------------- | ---------- | --------- | ------------------------------------- |
| Primary         | Pink Dusty | `#D88C9A` | Tombol dan elemen utama               |
| Secondary       | Cream      | `#F8F1E7` | Background                            |
| Text            | Dark Brown | `#3E302B` | Teks utama                            |
| Tersedia / Paid | Hijau      | `#28A745` | Produk tersedia / pembayaran berhasil |
| Pending         | Kuning     | `#FFC107` | Menunggu pembayaran                   |
| Batal / Habis   | Merah      | `#DC3545` | Pesanan dibatalkan / stok habis       |

---

# 5. Komponen UI Utama

| Komponen                 | Fungsi                                                      |
| ------------------------ | ----------------------------------------------------------- |
| **Navbar**               | Navigasi ke Beranda, Produk, Riwayat, dan Logout            |
| **Kolom Cari & Filter**  | Mencari produk berdasarkan nama, kategori, dan harga        |
| **Product Card**         | Menampilkan foto, nama, harga, ukuran, dan status produk    |
| **Badge Status**         | Menampilkan status produk atau pesanan dengan label visual  |
| **Detail Produk**        | Menampilkan informasi lengkap produk thrift                 |
| **Keranjang**            | Menampilkan produk yang akan dibeli sebelum checkout        |
| **Form Checkout**        | Mengisi alamat dan melakukan konfirmasi pesanan             |
| **Form Pembayaran**      | Memilih metode pembayaran simulasi dan melakukan pembayaran |
| **Riwayat Pesanan**      | Menampilkan daftar transaksi dan status pesanan             |
| **Dashboard Admin**      | Menampilkan ringkasan produk dan pesanan                    |
| **Form Kelola Produk**   | Menambah, mengubah, dan menghapus produk                    |
| **Form Kelola Kategori** | Menambah, mengubah, dan menghapus kategori                  |

---
