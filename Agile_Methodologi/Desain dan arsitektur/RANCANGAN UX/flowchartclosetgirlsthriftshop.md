# FLOWCHART APLIKASI — ClosetGirls TriftShop

## Alur Utama Sistem (Pembeli)

```mermaid
graph TD
    A([Mulai]) --> B[Buka Website]
    B --> C[Halaman Login]
    C --> D[Input Username dan Password]
    D --> E{Validasi Login?}

    E -->|Tidak| F[Tampilkan Pesan Error]
    F --> C

    E -->|Ya| G{Role?}

    G -->|Admin| Z[Ke Alur Admin]
    G -->|User| H[Halaman Beranda]

    H --> I[Lihat Katalog Produk]
    I --> J[Cari atau Filter Produk]
    J --> K[Pilih Produk]
    K --> L[Lihat Detail Produk]

    L --> M{Produk Masih Tersedia?}

    M -->|Tidak| N[Tampilkan Pesan Stok Habis]
    N --> I

    M -->|Ya| O[Masukkan ke Keranjang]
    O --> P[Lihat Keranjang]
    P --> Q{Lanjut Checkout?}

    Q -->|Tidak| I
    Q -->|Ya| R[Input Alamat dan Data Pesanan]

    R --> S[Konfirmasi Pesanan]
    S --> T[Buat Order Pending]

    T --> U[Proses Pembayaran Simulasi]
    U --> V{Pembayaran Berhasil?}

    V -->|Tidak| W[Order Dibatalkan]
    W --> I

    V -->|Ya| X[Update Status Order Paid]
    X --> Y[Kurangi Stok Produk]
    Y --> AA[Simpan Data Pembayaran]
    AA --> AB[Tampilkan Detail Pesanan]
    AB --> AC[Simpan ke Riwayat Pesanan]

    AC --> AD{User Logout?}

    AD -->|Tidak| H
    AD -->|Ya| AE([Selesai])
```

---

# Alur Admin

```mermaid
graph TD
    A([Login sebagai Admin]) --> B[Dashboard Admin]
    B --> C{Pilih Menu}

    C -->|Kelola Produk| D[Tambah, Ubah, atau Hapus Produk]
    C -->|Kelola Kategori| E[Tambah, Ubah, atau Hapus Kategori]
    C -->|Lihat Pesanan| F[Tampilkan Daftar Pesanan]

    D --> G[Validasi Data Produk]
    G --> H{Data Valid?}

    H -->|Tidak| I[Tampilkan Pesan Error]
    I --> D

    H -->|Ya| J[Simpan Perubahan ke Database]

    E --> K[Validasi Data Kategori]
    K --> L{Data Valid?}

    L -->|Tidak| M[Tampilkan Pesan Error]
    M --> E

    L -->|Ya| N[Simpan Kategori ke Database]

    F --> O[Filter Pesanan Berdasarkan Status]
    O --> P[Lihat Detail Pesanan]

    J --> Q{Logout?}
    N --> Q
    P --> Q

    Q -->|Tidak| B
    Q -->|Ya| R([Selesai])
```

---

# Penjelasan Alur

1. **Mulai** — User atau admin membuka website ClosetGirls TriftShop.
2. **Login** — Pengguna memasukkan username dan password.
3. **Validasi Login** — Sistem memeriksa data login. Jika salah, pengguna kembali ke halaman login.
4. **Cek Role** — Sistem membedakan pengguna sebagai **User** atau **Admin**.
5. **Katalog Produk** — User dapat melihat berbagai produk thrift yang tersedia.
6. **Cari dan Filter** — User dapat mencari atau memfilter produk berdasarkan kategori maupun informasi produk.
7. **Detail Produk** — User melihat informasi produk seperti nama, harga, ukuran, kondisi, stok, dan foto.
8. **Cek Ketersediaan** — Sistem memastikan produk masih tersedia sebelum dimasukkan ke keranjang.
9. **Keranjang** — Produk yang dipilih masuk ke keranjang sebelum melakukan checkout.
10. **Checkout** — User mengisi alamat dan melakukan konfirmasi pesanan.
11. **Order Pending** — Sistem membuat pesanan dengan status `pending`.
12. **Pembayaran** — Sistem menjalankan proses pembayaran secara simulasi.
13. **Pembayaran Berhasil** — Jika berhasil, status order berubah menjadi `paid`.
14. **Update Stok** — Stok produk dikurangi setelah pembayaran berhasil.
15. **Riwayat Pesanan** — Data transaksi disimpan sehingga user dapat melihat riwayat pesanannya.
16. **Alur Admin** — Admin dapat mengelola produk, kategori, dan melihat pesanan.
17. **Logout** — Sistem kembali selesai ketika user atau admin melakukan logout.

---

# Diagram Alur Data

Ini aku sesuaikan juga dengan **arsitektur yang tadi**, jadi bukan lagi Flask khusus toko akun game, tetapi sistem ClosetGirls:

```mermaid
sequenceDiagram
    participant U as User
    participant B as Browser
    participant F as Backend
    participant D as Database
    participant P as Pembayaran Simulasi

    U->>B: Buka Website
    B->>F: Request Katalog Produk
    F->>D: Ambil Produk Tersedia
    D-->>F: Data Produk
    F-->>B: Data Katalog
    B-->>U: Tampilkan Produk

    U->>B: Pilih Produk
    B->>F: Request Detail Produk
    F->>D: Ambil Data Produk
    D-->>F: Detail Produk
    F-->>B: Detail Produk
    B-->>U: Tampilkan Detail

    U->>B: Checkout
    B->>F: POST Order
    F->>D: Cek Stok Produk
    D-->>F: Stok Tersedia

    F->>D: Simpan Order Pending
    F->>P: Proses Pembayaran
    P-->>F: Status Pembayaran Berhasil

    F->>D: Update Order menjadi Paid
    F->>D: Kurangi Stok Produk
    F->>D: Simpan Data Pembayaran

    F-->>B: Detail Pesanan
    B-->>U: Tampilkan Konfirmasi Pesanan

    Note over B,D: Stok diperbarui setelah pembayaran berhasil
```
