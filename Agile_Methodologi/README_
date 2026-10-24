# 📄 Proposal Proyek — Digital Twin Sistem Monitoring Toko Closet Girls Thrift Shop

## 1. Latar Belakang

Closet Girls Thrift Shop menjual pakaian preloved yang sangat sensitif terhadap kondisi lingkungan. Kelembapan tinggi dapat memicu jamur dan bau apek pada pakaian, suhu yang terlalu panas membuat pengunjung tidak nyaman berbelanja, dan area toko yang ramai atau sepi tidak terpantau dengan baik. Selama ini pemilik toko masih memantau kondisi secara manual sehingga masalah sering baru diketahui setelah pakaian rusak atau pelanggan mengeluh.

Diperlukan sistem yang dapat merepresentasikan kondisi fisik toko dan area penyimpanan secara digital (digital twin) agar pemilik dapat memantau dan mengambil tindakan lebih cepat.

## 2. Tujuan

- Memantau kondisi toko (suhu, kelembapan, kualitas udara, jumlah pengunjung/occupancy) secara real-time
- Memantau kondisi area penyimpanan/gudang pakaian agar terhindar dari jamur dan bau apek
- Merepresentasikan kondisi tersebut dalam bentuk digital twin (dashboard visual denah toko)
- Memberikan notifikasi otomatis saat kondisi toko atau gudang tidak ideal

## 3. Keputusan Sprint 1

### a. Agile Methodology
- Metodologi yang digunakan: **Scrum**
- Durasi sprint: ± 1 bulan per sprint (mengikuti timeline Sp1–Sp5)
- Role tim: 1 orang sebagai **Scrum Master** (koordinator), sisanya **Development Team**
- Tools tracking task: **GitHub Projects**

### b. UX Design
- Dashboard dirancang dengan wireframe sederhana (Figma/sketsa) sebelum masuk development
- Elemen utama dashboard:
  - Panel suhu (angka + indikator warna: hijau/kuning/merah)
  - Panel kelembapan (area toko dan gudang)
  - Status occupancy (jumlah pengunjung: sepi/normal/ramai)
  - Denah toko digital (zona rak pakaian berubah warna sesuai kondisi)
  - Notifikasi/alert (contoh: banner "Kelembapan gudang tinggi, risiko jamur")
- Alur pengguna: buka dashboard → lihat kondisi toko & gudang real-time → menerima notifikasi jika ada anomali → pemilik mengambil tindakan (nyalakan kipas/AC, buka ventilasi, pindahkan stok)

### c. Project Setup
- Struktur folder awal repository:

```
closet-girls-digital-twin/
├── data-generator/     # Python script simulasi data sensor
├── backend/            # Flask / Node.js (API penerima data)
├── dashboard/          # HTML + JS + Chart.js
├── docs/               # Proposal, wireframe, dokumentasi
├── .gitignore
└── README.md
```

- Tech stack awal: Python Dummy Data Generator (data), Flask/Node.js (backend), HTML/JS + Chart.js (dashboard awal)

## 4. Arsitektur Sistem

### a. Physical Object (Sumber Data)
- **Opsi 1 (Hardware):** Sensor DHT11/DHT22 (suhu & kelembapan) + sensor gas (MQ-135, untuk kualitas udara/bau) + sensor gerak PIR (pengunjung), terhubung ke mikrokontroler ESP32/ESP8266/Arduino. Sensor dipasang di area toko dan gudang.
- **Opsi 2 (Tanpa Hardware):** Dummy Data Generator menggunakan Python script yang mensimulasikan data sensor toko dan gudang

### b. Digital Twin (Representasi Digital)
- Dashboard UI berbasis web (contoh: Grafana, ThingSpeak, atau dashboard custom)
- Denah toko 2D yang menampilkan zona (rak atasan, rak bawahan, area fitting, kasir, gudang) dengan warna sesuai kondisi
- (Opsional, jika waktu memungkinkan) Visualisasi 3D toko menggunakan Three.js/Unity, berubah warna sesuai kondisi (misal merah = lembap/panas)

### c. Fitur Tambahan
- Prediksi tingkat kenyamanan berbelanja dan risiko jamur berdasarkan data sensor
- Notifikasi otomatis, contoh: "Kelembapan gudang di atas 70%, disarankan menyalakan kipas atau dehumidifier"
- Riwayat data harian/mingguan untuk melihat jam ramai dan pola kondisi toko

## 5. Tech Stack (Rencana Awal)

| Komponen | Teknologi |
|----------|-----------|
| Sumber Data | ESP32 + DHT22 + PIR + MQ-135 / Python Dummy Data |
| Backend | (isi sesuai kesepakatan tim, contoh: Node.js/Flask) |
| Database | (contoh: Firebase/MySQL/InfluxDB) |
| Dashboard | Grafana / Dashboard custom (HTML+JS/Three.js) |
| Komunikasi | MQTT / HTTP REST API |

## 6. Rencana Sprint

| Sprint | Bulan | Fokus |
|--------|-------|-------|
| Sp1 | September | Tentukan arsitektur (hardware/dummy), UX dashboard, setup repo |
| Sp2 | October | Backend penerima data + dashboard dasar (suhu, kelembapan, pengunjung) |
| Sp3 | November | Fitur notifikasi & prediksi kenyamanan/risiko jamur, refinement |
| Sp4 | December | Testing, upgrade visual denah toko 2D/3D (jika sempat) |
| Sp5 | December | Final testing, bug fixing, persiapan demo Expo |

## 7. Anggota Tim

| Nama | NIM | Peran |
|------|-----|-------|
| ... | ... | Scrum Master |
| ... | ... | Development Team |
| ... | ... | Development Team |
