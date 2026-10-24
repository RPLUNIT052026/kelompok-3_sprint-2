# Setup Kode - ClosetGirls TriftShop

Folder ini menandakan proyek ClosetGirls TriftShop siap masuk tahap development.

## Struktur Rencana

```text
closetgirls-triftshop/
├── backend/
│   ├── controllers/       # Logika alur sistem
│   │   ├── auth/
│   │   ├── products/
│   │   ├── cart/
│   │   ├── orders/
│   │   └── payments/
│   ├── models/             # Model data
│   │   ├── User
│   │   ├── Product
│   │   ├── Category
│   │   ├── Order
│   │   └── Payment
│   ├── routes/             # Endpoint API
│   └── config/             # Konfigurasi database & environment
│
├── frontend/
│   ├── pages/              # Halaman aplikasi
│   │   ├── home/
│   │   ├── catalog/
│   │   ├── product-detail/
│   │   ├── cart/
│   │   ├── checkout/
│   │   └── order-history/
│   ├── components/         # Komponen UI
│   │   ├── navbar/
│   │   ├── product-card/
│   │   ├── search-filter/
│   │   └── status-badge/
│   └── assets/             # Gambar, icon & style
│
├── database/
│   └── schema.sql          # Skema database
│
└── docs/                   # Dokumen project
    ├── function-point/
    ├── project-chapter/
    ├── flowchart/
    ├── erd/
    └── architecture/
````

## Skema Database (Rencana)

| Tabel           | Keterangan                                                |
| --------------- | --------------------------------------------------------- |
| `users`         | Data pengguna dan admin                                   |
| `categories`    | Data kategori pakaian thrift                              |
| `products`      | Data produk seperti nama, harga, ukuran, kondisi dan stok |
| `orders`        | Data pesanan yang dibuat oleh pengguna                    |
| `order_details` | Detail produk yang terdapat dalam setiap pesanan          |
| `payments`      | Data pembayaran dan status pembayaran                     |

## Fitur Utama (Rencana)

* Registrasi & login pengguna
* Katalog produk thrift
* Pencarian dan filter produk
* Detail produk
* Keranjang belanja
* Checkout
* Pembayaran
* Riwayat pesanan
* Pengelolaan stok produk
* Dashboard admin
* Kelola produk dan kategori
* Kelola pesanan dan status pembayaran

## Alur Utama Sistem

```text
Login
  ↓
Home / Katalog
  ↓
Pilih Produk
  ↓
Detail Produk
  ↓
Tambah ke Keranjang
  ↓
Checkout
  ↓
Pembayaran
  ↓
Pembayaran Berhasil
  ↓
Pesanan Tersimpan
  ↓
Riwayat Pesanan
```

## Status

* [x] Struktur folder dirancang
* [x] Skema database dirancang
* [x] Fitur utama ditentukan
* [x] Alur sistem dirancang
* [ ] Implementasi kode
* [ ] Testing
* [ ] Deployment

````
