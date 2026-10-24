
# Sistem Penjualan Online Closet Girls Thriftshop

## A. Perhitungan Function Point (FP)

Function Point digunakan untuk memperkirakan ukuran dan kompleksitas aplikasi berdasarkan fitur yang direncanakan.

### 1. Identifikasi Komponen Fungsional

| No | Komponen | Tipe | Kompleksitas | Bobot |
|---|---|---|---|---:|
| 1 | Registrasi dan login pelanggan/admin | EI | Low | 3 |
| 2 | Tambah produk ke keranjang | EI | Low | 3 |
| 3 | Checkout dan pembuatan pesanan | EI | Average | 4 |
| 4 | Kelola data produk oleh admin | EI | Average | 4 |
| 5 | Upload bukti pembayaran | EI | Low | 3 |
| 6 | Tampilan katalog produk thrift | EO | Average | 5 |
| 7 | Notifikasi status pesanan | EO | Average | 5 |
| 8 | Laporan penjualan untuk admin | EO | Average | 5 |
| 9 | Pencarian dan filter produk | EQ | Low | 3 |
| 10 | Detail produk | EQ | Low | 3 |
| 11 | Riwayat pesanan pelanggan | EQ | Low | 3 |
| 12 | Data produk dan stok | ILF | Low | 7 |
| 13 | Data pengguna | ILF | Low | 7 |
| 14 | Data pesanan dan transaksi | ILF | Average | 10 |
| 15 | Integrasi ongkir dan pembayaran eksternal | EIF | Average | 7 |

### 2. Ringkasan Unadjusted Function Point

| Tipe Komponen | Jumlah | Bobot Rata-rata | Total |
|---|---:|---:|---:|
| External Input (EI) | 5 | 3,4 | 17 |
| External Output (EO) | 3 | 5 | 15 |
| External Inquiry (EQ) | 3 | 3 | 9 |
| Internal Logical File (ILF) | 3 | 8 | 24 |
| External Interface File (EIF) | 1 | 7 | 7 |
| **Total UFP** | | | **72** |

### 3. Value Adjustment Factor (VAF)

VAF diasumsikan netral sebesar 1,0.

Rumus:

FP = UFP × VAF

FP = 72 × 1,0 = **72 Function Point**

## B. Product Backlog

| ID | User Story | Prioritas |
|---|---|---|
| US-01 | Sebagai pelanggan, saya ingin melihat katalog produk beserta foto dan harganya. | Tinggi |
| US-02 | Sebagai pelanggan, saya ingin mencari dan memfilter produk berdasarkan kategori, ukuran, dan harga. | Tinggi |
| US-03 | Sebagai pelanggan, saya ingin melihat detail kondisi, ukuran, dan ketersediaan produk. | Tinggi |
| US-04 | Sebagai pelanggan, saya ingin mendaftar dan login agar data dan pesanan tersimpan. | Sedang |
| US-05 | Sebagai pelanggan, saya ingin menambahkan produk ke keranjang dan melakukan checkout. | Tinggi |
| US-06 | Sebagai pelanggan, saya ingin mengunggah bukti pembayaran dan menerima notifikasi pesanan. | Sedang |
| US-07 | Sebagai admin, saya ingin mengelola data produk dan stok. | Tinggi |
| US-08 | Sebagai admin, saya ingin melihat laporan penjualan. | Sedang |
| US-09 | Sebagai pelanggan, saya ingin melihat riwayat pesanan. | Rendah |
| US-10 | Sebagai pelanggan, saya ingin menghitung ongkos kirim berdasarkan alamat tujuan. | Rendah |

## C. Sprint 1 Backlog

| Task | Deskripsi | Penanggung Jawab |
|---|---|---|
| Project Charter | Menyusun latar belakang, tujuan, ruang lingkup, dan struktur tim. | Ketua |
| Perhitungan Function Point | Mengestimasi ukuran aplikasi berdasarkan fitur yang direncanakan. | Anggota 1 |
| Product Backlog dan Sprint 1 Backlog | Menyusun daftar User Stories dan target Sprint 1. | Anggota 2 |
| Rancangan UX/UI | Membuat wireframe katalog, keranjang, dan halaman admin awal. | Anggota 3 |
| Rancangan Sistem | Membuat flowchart, diagram arsitektur, dan ERD. | Ketua/Anggota |
| Inisialisasi Kode Proyek | Menyiapkan struktur folder dan boilerplate awal. | Ketua |

