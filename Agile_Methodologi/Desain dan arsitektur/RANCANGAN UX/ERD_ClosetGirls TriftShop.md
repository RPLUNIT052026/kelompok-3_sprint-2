# ERD — ClosetGirls TriftShop

## 1. Entity Relationship Diagram

```mermaid
erDiagram
    USERS ||--o{ ORDERS : membuat
    CATEGORIES ||--o{ PRODUCTS : memiliki
    ORDERS ||--|{ ORDER_DETAILS : memiliki
    PRODUCTS ||--o{ ORDER_DETAILS : dipesan
    ORDERS ||--o| PAYMENTS : memiliki

    USERS {
        int id PK
        string username
        string email
        string password_hash
        string role
    }

    CATEGORIES {
        int id PK
        string nama_kategori
        string deskripsi
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
        string alamat
        string status
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
        string metode
        int jumlah
        string status
        datetime paid_at
    }
```

## 2. Penjelasan Entitas

| Entitas           | Fungsi                                                                                   |
| ----------------- | ---------------------------------------------------------------------------------------- |
| **USERS**         | Menyimpan data pengguna dan admin.                                                       |
| **CATEGORIES**    | Menyimpan kategori produk thrift seperti atasan, bawahan, outer, dan lainnya.            |
| **PRODUCTS**      | Menyimpan data produk yang dijual, seperti nama, harga, ukuran, kondisi, stok, dan foto. |
| **ORDERS**        | Menyimpan data pesanan yang dibuat oleh pengguna.                                        |
| **ORDER_DETAILS** | Menyimpan rincian produk dalam setiap pesanan.                                           |
| **PAYMENTS**      | Menyimpan informasi pembayaran dari pesanan.                                             |

## 3. Relasi Antar Entitas

| Relasi                       | Keterangan                                               |
| ---------------------------- | -------------------------------------------------------- |
| **USERS → ORDERS**           | Satu pengguna dapat membuat banyak pesanan.              |
| **CATEGORIES → PRODUCTS**    | Satu kategori dapat memiliki banyak produk.              |
| **ORDERS → ORDER_DETAILS**   | Satu pesanan memiliki satu atau lebih detail produk.     |
| **PRODUCTS → ORDER_DETAILS** | Satu produk dapat terdapat pada beberapa detail pesanan. |
| **ORDERS → PAYMENTS**        | Satu pesanan memiliki informasi pembayaran.              |

## 4. Struktur Database

```text
USERS
  │
  │ membuat
  ↓
ORDERS ───────────→ PAYMENTS
  │
  │ memiliki
  ↓
ORDER_DETAILS
  ↑
  │ dipesan
  │
PRODUCTS
  ↑
  │ memiliki
  │
CATEGORIES
```
