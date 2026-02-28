Saya akan buatkan **Struktur Menu Superadmin (Taxonomy)** untuk Super Apps KAI yang komprehensif, mencakup semua modul yang telah kita rancang sebelumnya.

---

# STRUKTUR MENU SUPERADMIN - TAXONOMY
## Super Apps KAI - Platform Digital Terintegrasi

---

## 📊 LEGENDA STRUKTUR MENU

| Simbol | Arti |
| :--- | :--- |
| **📁** | Menu Utama (Parent Menu) |
| **📂** | Sub Menu (Child Menu) |
| **🔧** | Halaman Konfigurasi |
| **📋** | Halaman Daftar/List |
| **➕** | Halaman Tambah Data |
| **✏️** | Halaman Edit |
| **👁️** | Halaman View/Detail |
| **📊** | Halaman Dashboard/Report |
| **⚙️** | Menu Settings |

---

## 1. SIDEBAR UTAMA - NAVIGASI SUPERADMIN

```
🏠 DASHBOARD UTAMA
├── 📊 Overview Real-time
├── 📊 System Health
├── 📊 Quick Stats (4 Modul)
└── 📊 Recent Activities

📁 MASTER DATA
📁 MANAJEMEN USER
📁 MODUL 1 - PENUMPANG
📁 MODUL 2 - KARGO
📁 MODUL 3 - PERSEWAAN
📁 MODUL 4 - ROLLINGSTOCK
📁 INTEGRASI & EKSTERNAL
📁 KEUANGAN & PEMBAYARAN
📁 LAPORAN & ANALITIK
📁 PENGATURAN SISTEM
```

---

## 2. MASTER DATA (GLOBAL)

```
📁 MASTER DATA
│
├── 📋 Data Master Global
│   ├── 📋 Provinsi
│   ├── 📋 Kota/Kabupaten
│   ├── 📋 Kecamatan
│   └── 📋 Kelurahan
│
├── 📋 Master Wilayah Operasi KAI
│   ├── 📋 Divisi Regional (Divre)
│   ├── 📋 Daerah Operasi (Daop)
│   └── 📋 Unit Pelaksana Teknis (UPT)
│
├── 📋 Master Referensi
│   ├── 📋 Mata Uang
│   ├── 📋 Satuan (Kg, Ton, M3, dll)
│   ├── 📋 Kode Pos
│   └── 📋 Hari Libur Nasional
│
├── 📋 Master Kategori
│   ├── 📋 Kategori Aset
│   ├── 📋 Kategori Produk
│   ├── 📋 Kategori Komplain
│   └── 📋 Kategori Dokumen
│
└── 📋 Master Dokumen
    ├── 📋 Template Dokumen
    ├── 📋 Nomor Seri Dokumen
    └── 📋 Arsip Dokumen
```

---

## 3. MANAJEMEN USER & AKSES

```
📁 MANAJEMEN USER
│
├── 📋 Semua User (Unified)
│   ├── 🔧 Filter & Pencarian
│   ├── ➕ Tambah User Baru
│   ├── 📥 Import Bulk (Excel/CSV)
│   ├── 📤 Export Data
│   └── ✏️ Edit / 👁️ Detail per User
│
├── 📁 Manajemen Role & Permission
│   ├── 📋 Daftar Role
│   │   ├── Superadmin
│   │   ├── Admin Penumpang
│   │   ├── Admin Kargo
│   │   ├── Admin Persewaan
│   │   ├── Admin Rollingstock
│   │   ├── Operator Gudang
│   │   ├── Teknisi
│   │   ├── Customer Service
│   │   ├── Viewer (Read Only)
│   │   └── Custom Role (➕ Tambah)
│   │
│   ├── ⚙️ Permission per Role
│   │   ├── Module Access
│   │   ├── CRUD Permissions
│   │   ├── Data Scope (Semua/Divre/Daop)
│   │   └── Feature Toggles
│   │
│   └── 📋 Assignment Role ke User
│
├── 📁 Manajemen Grup
│   ├── 📋 Grup Pengguna
│   ├── 📋 Grup Perusahaan (B2B)
│   └── 🔧 Assign User ke Grup
│
├── 📁 Verifikasi & Approval
│   ├── 📋 Pending Registrasi
│   ├── 📋 Verifikasi Dokumen
│   └── 📋 Approval Change Request
│
└── 📁 Audit Trail
    ├── 📋 Log Aktivitas User
    ├── 📋 Log Login
    ├── 📋 Log Perubahan Data
    └── 🔍 Impersonation Log
```

---

## 4. MODUL 1 - PENUMPANG (SUPERADMIN VIEW)

```
📁 MODUL 1 - PENUMPANG
│
├── 📊 Dashboard Penumpang
│   ├── 📊 Grafik Penjualan Tiket
│   ├── 📊 Okupansi Kereta
│   ├── 📊 Rute Terpopuler
│   └── 📊 On-Time Performance
│
├── 📁 Manajemen Rute & Jadwal
│   ├── 📋 Daftar Stasiun
│   │   ├── ➕ Tambah Stasiun
│   │   ├── ✏️ Edit Stasiun
│   │   └── 🗺️ Atur Peta/Lokasi
│   │
│   ├── 📋 Daftar Rute
│   │   ├── ➕ Tambah Rute
│   │   ├── ✏️ Edit Rute
│   │   └── 🚉 Atur Stasiun dalam Rute
│   │
│   └── 📋 Jadwal Kereta
│       ├── ➕ Tambah Jadwal
│       ├── ✏️ Edit Jadwal
│       ├── 🔁 Atur Jadwal Berulang
│       ├── ⏰ Atur Waktu & Durasi
│       └── 🚆 Assign Armada (dari Modul 4)
│
├── 📁 Manajemen Tiket & Harga
│   ├── 📋 Kelas Layanan
│   │   ├── Eksekutif
│   │   ├── Bisnis
│   │   └── Ekonomi
│   │
│   ├── ⚙️ Struktur Harga
│   │   ├── Harga Dasar per KM
│   │   ├── Dynamic Pricing Rules
│   │   ├── Diskon & Promo
│   │   └── Biaya Tambahan (Asuransi, dll)
│   │
│   ├── 📋 Manajemen Promo
│   │   ├── ➕ Tambah Promo
│   │   ├── 📅 Atur Periode Promo
│   │   ├── 🔢 Kode Voucher
│   │   └── 📊 Report Penggunaan Promo
│   │
│   └── 📋 Manajemen Pembatalan
│       ├── ⚙️ Kebijakan Refund
│       └── 📋 Daftar Refund Request
│
├── 📁 Manajemen Pelanggan (CRM)
│   ├── 📋 Data Penumpang
│   ├── 📋 Tier Loyalty
│   ├── 📋 Poin & Reward
│   └── 🔧 Atur Konversi Poin
│
├── 📁 Manajemen Komplain
│   ├── 📋 Semua Komplain
│   ├── 📋 Komplain Open
│   ├── 📋 Komplain In Progress
│   ├── 📋 Komplain Resolved
│   ├── 🔧 Kategori Komplain
│   └── ⏱️ SLA Komplain
│
└── 📁 Konfigurasi Modul 1
    ├── ⚙️ Atur Kapasitas Maksimal Tiket
    ├── ⚙️ Atur Waktu Booking (H-90 s/d H-1)
    ├── ⚙️ Atur Batas Pembatalan
    └── ⚙️ Integrasi dengan Modul 4 (Armada)
```

---

## 5. MODUL 2 - KARGO + WMS + TMS (SUPERADMIN VIEW)

```
📁 MODUL 2 - KARGO
│
├── 📊 Dashboard Kargo
│   ├── 📊 Volume Pengiriman
│   ├── 📊 Revenue per Komoditas
│   ├── 📊 Utilisasi Gudang
│   ├── 📊 Utilisasi Armada Kargo
│   └── 📊 On-Time Delivery Rate
│
├── 📁 Manajemen Pelanggan Kargo (B2B)
│   ├── 📋 Daftar Perusahaan
│   ├── 📋 PIC Perusahaan
│   ├── 📋 Kontrak Kerjasama
│   ├── 🔧 Approval Kredit Limit
│   └── 📋 Tarif Khusus per Pelanggan
│
├── 📁 Manajemen Tarif Kargo
│   ├── ⚙️ Tarif Dasar per KG / per M3
│   ├── ⚙️ Tarif per KM
│   ├── ⚙️ Tarif Komoditas Khusus
│   ├── ⚙️ Tarif Layanan Tambahan
│   └── ⚙️ Tarif Door-to-Door
│
├── 📁 WMS - WAREHOUSE MANAGEMENT
│   ├── 📋 Manajemen Gudang
│   │   ├── ➕ Tambah Gudang
│   │   ├── ✏️ Edit Gudang
│   │   └── 🗺️ Atur Peta/Lokasi
│   │
│   ├── 📋 Zona & Rak
│   │   ├── ➕ Tambah Zona
│   │   ├── ➕ Tambah Rak
│   │   ├── 🔧 Atur Kapasitas Rak
│   │   └── 🔧 Atur Tipe Penyimpanan
│   │
│   ├── 📋 Manajemen Inventory
│   │   ├── 📋 Stok per Gudang
│   │   ├── 📋 Mutasi Stok
│   │   ├── 📋 Stok Opname
│   │   ├── ⚠️ Low Stock Alert
│   │   └── 📋 Expired/Batch Tracking
│   │
│   └── 📋 Operasional Gudang
│       ├── 📋 Penerimaan Barang (Receiving)
│       ├── 📋 Penyimpanan (Put Away)
│       ├── 📋 Pengambilan (Picking)
│       ├── 📋 Pengemasan (Packing)
│       └── 📋 Pengiriman (Dispatching)
│
├── 📁 TMS - TRANSPORTATION MANAGEMENT
│   ├── 📋 Manajemen Armada Kargo
│   │   ├── 📋 Data Gerbong (sync Modul 4)
│   │   ├── 📋 Kapasitas per Gerbong
│   │   ├── 📋 Ketersediaan Real-time
│   │   └── 🔧 Atur Tipe Gerbong
│   │
│   ├── 📋 Manajemen Rute Kargo
│   │   ├── 📋 Master Rute Kargo
│   │   ├── 📋 Stasiun Bongkar Muat
│   │   ├── 🗺️ Optimasi Rute (Algoritma)
│   │   └── 📋 Jarak & Estimasi Waktu
│   │
│   ├── 📋 Load Planning
│   │   ├── 🔧 Atur Kapasitas Maksimal
│   │   ├── 🔧 Atur Konsolidasi Kiriman
│   │   └── 📋 Schedule Pengiriman
│   │
│   └── 📋 Tracking & Monitoring
│       ├── 🗺️ Live Track Shipment
│       ├── 📋 Riwayat Tracking
│       ├── ⚠️ Exception Handling
│       └── 📋 Proof of Delivery
│
├── 📁 Manajemen Order Kargo
│   ├── 📋 Semua Order
│   ├── 📋 Order Pending
│   ├── 📋 Order Processing
│   ├── 📋 Order Shipped
│   ├── 📋 Order Delivered
│   └── 📋 Order Cancelled
│
└── 📁 Konfigurasi Modul 2
    ├── ⚙️ Atur ASN (Advance Shipping Notice)
    ├── ⚙️ Atur Integrasi WMS-TMS
    ├── ⚙️ Atur IoT Sensor untuk Gudang
    ├── ⚙️ Atur Kebijakan Klaim
    └── ⚙️ Integrasi Bea Cukai
```

---

## 6. MODUL 3 - PERSEWAAN ASET (SUPERADMIN VIEW)

```
📁 MODUL 3 - PERSEWAAN ASET
│
├── 📊 Dashboard Persewaan
│   ├── 📊 Okupansi Aset
│   ├── 📊 Revenue per Kategori Aset
│   ├── 📊 Top Performing Aset
│   ├── 📊 Grafik Penyewaan per Periode
│   └── 📊 Monitoring Energi (Panel Surya)
│
├── 📁 Manajemen Aset
│   ├── 📋 Kategori Aset
│   │   ├── Tanah
│   │   ├── Bangunan
│   │   ├── Ruko / Retail
│   │   ├── Billboard / Iklan
│   │   ├── Area Parkir
│   │   ├── Stasiun (Area Komersial)
│   │   └── Custom (➕ Tambah)
│   │
│   ├── 📋 Daftar Aset
│   │   ├── ➕ Tambah Aset Baru
│   │   ├── ✏️ Edit Aset
│   │   ├── 📸 Upload Foto/Dokumen
│   │   ├── 🗺️ Atur Peta/Lokasi (GIS)
│   │   ├── 🔧 Atur Spesifikasi
│   │   └── 📋 Riwayat Penyewaan
│   │
│   ├── 📋 Status Aset
│   │   ├── Tersedia
│   │   ├── Disewa
│   │   ├── Perbaikan
│   │   ├── Tidak Tersedia
│   │   └── 🔧 Atur Jadwal Ketersediaan
│   │
│   └── 📋 Dokumen Aset
│       ├── Sertifikat
│       ├── IMB
│       ├── Pajak
│       └── Kontrak Lama
│
├── 📁 Manajemen Harga Sewa
│   ├── ⚙️ Harga Dasar per m2
│   ├── ⚙️ Harga per Bulan/Tahun
│   ├── ⚙️ Harga Khusus Tenant Tertentu
│   ├── ⚙️ Deposit & Biaya Lain
│   └── ⚙️ Diskon Early Bird / Long Term
│
├── 📁 Manajemen Booking & Kontrak
│   ├── 📋 Booking Request
│   │   ├── ✅ Approve
│   │   ├── ❌ Reject
│   │   └── ⏳ Pending
│   │
│   ├── 📋 Kontrak Aktif
│   │   ├── 👁️ View Kontrak
│   │   ├── ✏️ Amendemen Kontrak
│   │   ├── 🔄 Perpanjangan
│   │   └── ⚠️ Akan Berakhir (30/14/7 hari)
│   │
│   ├── 📋 Riwayat Kontrak
│   └── 📋 Template Kontrak
│
├── 📁 Manajemen Tagihan
│   ├── 📋 Semua Tagihan
│   ├── 📋 Tagihan Bulanan
│   ├── 📋 Tagihan Overdue
│   ├── 📋 Riwayat Pembayaran
│   ├── 🔧 Atur Periode Tagihan
│   └── 🔧 Atur Denda Keterlambatan
│
├── 📁 IoT & Smart Building
│   ├── 📋 Sensor Terpasang
│   │   ├── Sensor Hunian
│   │   ├── Sensor Suhu
│   │   ├── Sensor Energi
│   │   └── Sensor Keamanan
│   │
│   ├── 📊 Dashboard Monitoring
│   │   ├── 🏢 Occupancy Real-time
│   │   ├── ⚡ Konsumsi Listrik
│   │   ├── ☀️ Produksi Panel Surya
│   │   └── 🔐 Keamanan
│   │
│   └── ⚙️ Konfigurasi Alert
│       ├── Ambang Batas Konsumsi
│       ├── Alert Keamanan
│       └── Notifikasi Perawatan
│
└── 📁 Konfigurasi Modul 3
    ├── ⚙️ Atur Syarat & Ketentuan Sewa
    ├── ⚙️ Atur Kebijakan Pembatalan
    ├── ⚙️ Atur Mekanisme Refund Deposit
    └── ⚙️ Integrasi dengan Modul 2 (Gudang sebagai Aset)
```

---

## 7. MODUL 4 - ROLLINGSTOCK MANAGEMENT (SUPERADMIN VIEW)

```
📁 MODUL 4 - ROLLINGSTOCK MANAGEMENT
│
├── 📊 Dashboard Sarana
│   ├── 📊 Fleet Readiness
│   ├── 📊 Armada Operasi vs Perawatan
│   ├── 📊 Downtime Analysis
│   ├── 📊 Biaya Perawatan per Armada
│   └── 📊 Predictive Maintenance Alerts
│
├── 📁 Manajemen Armada
│   ├── 📋 Tipe Armada
│   │   ├── Lokomotif
│   │   ├── Kereta Penumpang
│   │   ├── Gerbong Barang
│   │   ├── Kereta Inspeksi
│   │   └── Sarana Lainnya
│   │
│   ├── 📋 Daftar Armada
│   │   ├── ➕ Tambah Armada Baru
│   │   ├── ✏️ Edit Data Armada
│   │   ├── 📋 Spesifikasi Teknis
│   │   ├── 📋 Riwayat Operasi
│   │   └── 📋 Kilometer Tempuh
│   │
│   └── 📋 Status Armada
│       ├── Operasi
│       ├── Perawatan Preventif
│       ├── Perbaikan (Korektif)
│       ├── Rusak
│       ├── Apkir
│       └── 🔧 Atur Status Real-time
│
├── 📁 Manajemen Perawatan
│   ├── 📋 Jadwal Perawatan Preventif
│   │   ├── 🔧 Atur Interval (Hari/KM)
│   │   ├── 🔧 Atur Tipe Perawatan
│   │   └── 📋 Kalender Perawatan
│   │
│   ├── 📋 Predictive Maintenance
│   │   ├── 🤖 Model AI
│   │   ├── ⚠️ Alert Prediktif
│   │   ├── 📊 Confidence Level
│   │   └── ✅ Rekomendasi Tindakan
│   │
│   ├── 📋 Perawatan Berjalan
│   ├── 📋 Riwayat Perawatan
│   └── 📋 Dokumen Perawatan
│       ├── Manual Book
│       ├── Sertifikat Laik Jalan
│       └── Laporan Teknis
│
├── 📁 IoT & Sensor Armada
│   ├── 📋 Sensor Terpasang
│   │   ├── Sensor Getaran
│   │   ├── Sensor Suhu
│   │   ├── Sensor Tekanan
│   │   ├── Sensor GPS
│   │   └── Sensor Lainnya
│   │
│   ├── 📊 Data Sensor Real-time
│   │   ├── 📈 Grafik Getaran
│   │   ├── 📈 Grafik Suhu
│   │   ├── 📈 Grafik Tekanan
│   │   └── 🗺️ GPS Tracking
│   │
│   └── ⚙️ Konfigurasi Sensor
│       ├── Ambang Batas Normal
│       ├── Frekuensi Pembacaan
│       └── Kalibrasi Sensor
│
├── 📁 Manajemen Suku Cadang
│   ├── 📋 Master Suku Cadang
│   │   ├── ➕ Tambah Part Baru
│   │   ├── ✏️ Edit Data Part
│   │   └── 🔧 Atur Part Number
│   │
│   ├── 📋 Stok Suku Cadang
│   │   ├── 📦 Stok per Gudang (sync SCM)
│   │   ├── ⚠️ Minimum Stok Alert
│   │   ├── 📋 Reorder Point
│   │   └── 📋 Riwayat Pemakaian
│   │
│   └── 📋 Pengadaan (Integrasi SCM)
│       ├── 📋 Purchase Request
│       ├── 📋 Purchase Order
│       └── 📋 Receiving
│
├── 📁 Manajemen Teknisi
│   ├── 📋 Data Teknisi
│   │   ├── Data Pribadi
│   │   ├── Spesialisasi
│   │   ├── Sertifikasi
│   │   └── Jadwal Kerja
│   │
│   ├── 📋 Assignment Perawatan
│   └── 📋 Kinerja Teknisi
│
└── 📁 Konfigurasi Modul 4
    ├── ⚙️ Atur Parameter Predictive Maintenance
    ├── ⚙️ Atur Integrasi dengan Modul 1 & 2
    ├── ⚙️ Atur Sinkronisasi Data Armada
    └── ⚙️ Atur Digital Twin (3D Model)
```

---

## 8. INTEGRASI & EKSTERNAL

```
📁 INTEGRASI & EKSTERNAL
│
├── 📁 Integrasi CRM KAI 121
│   ├── 🔧 Konfigurasi API
│   ├── 📋 Mapping Data
│   ├── 🔄 Sinkronisasi Manual
│   ├── 📊 Status Sinkronisasi
│   └── 📋 Log Sinkronisasi
│
├── 📁 Integrasi SCM Divisi Logistik
│   ├── 🔧 Konfigurasi API
│   ├── 📋 Mapping Suku Cadang
│   ├── 🔄 Sinkronisasi Stok
│   ├── 📊 Status Sinkronisasi
│   └── 📋 Log Sinkronisasi
│
├── 📁 Integrasi HCM (SAP/Raileo)
│   ├── 🔧 Konfigurasi API (Read-only)
│   ├── 📋 Mapping Data Pegawai
│   ├── 📋 Data Teknisi
│   ├── 📋 Data Petugas
│   └── 📊 Status Koneksi
│
├── 📁 Integrasi Vendor Outsourcing
│   ├── 🔧 Konfigurasi API Vendor
│   ├── 📋 Daftar Vendor
│   ├── 📋 Data Tenaga Alih Daya
│   ├── 📋 Monitoring Kehadiran
│   └── 📋 Penilaian Kinerja
│
├── 📁 Payment Gateway
│   ├── 🔧 Konfigurasi Midtrans/Xendit
│   │   ├── 🔑 API Key
│   │   ├── 🔐 Merchant ID
│   │   ├── ⚙️ Sandbox / Production Mode
│   │   └── 🔄 Webhook Configuration
│   │
│   ├── 📋 Metode Pembayaran
│   │   ├── Bank Transfer (BCA/Mandiri/BNI/BRI)
│   │   ├── E-Wallet (GoPay/OVO/DANA)
│   │   ├── Credit Card
│   │   ├── Convenience Store
│   │   └── QRIS
│   │
│   ├── 📊 Status Transaksi
│   ├── 📋 Log Callback
│   └── 💰 Settlement Report
│
├── 📁 Integrasi Map & Geolocation
│   ├── 🔧 Google Maps API
│   ├── 🗺️ Mapbox Configuration
│   ├── 📋 Peta Stasiun
│   ├── 📋 Peta Gudang
│   ├── 📋 Peta Aset
│   └── 🛤️ Peta Jalur Kereta
│
├── 📁 Integrasi IoT Platform
│   ├── 🔧 AWS IoT Core / ThingsBoard
│   ├── 📋 Daftar Device
│   ├── 📊 Status Koneksi
│   └── 📋 Data Stream Configuration
│
├── 📁 Integrasi Bea Cukai (CEISA)
│   ├── 🔧 Konfigurasi API
│   ├── 📋 Dokumen Ekspor-Impor
│   └── 📊 Status Dokumen
│
└── 📁 Open API untuk Mitra
    ├── 🔧 API Key Management
    ├── 📋 Daftar Mitra Terdaftar
    ├── 📊 Usage Analytics
    └── ⚙️ Rate Limiting Configuration
```

---

## 9. KEUANGAN & PEMBAYARAN

```
📁 KEUANGAN & PEMBAYARAN
│
├── 📊 Dashboard Keuangan
│   ├── 💰 Total Revenue Hari Ini
│   ├── 💰 Total Revenue Bulan Ini
│   ├── 💰 Total Revenue Tahun Ini
│   ├── 📊 Revenue per Modul
│   ├── 📊 Revenue per Metode Bayar
│   └── 📈 Grafik Trend
│
├── 📁 Semua Transaksi
│   ├── 📋 Transaksi Penumpang
│   ├── 📋 Transaksi Kargo
│   ├── 📋 Transaksi Persewaan
│   └── 🔍 Filter & Pencarian
│
├── 📁 Manajemen Invoice
│   ├── 📋 Semua Invoice
│   ├── 📋 Invoice Pending
│   ├── 📋 Invoice Paid
│   ├── 📋 Invoice Overdue
│   ├── 📋 Invoice Cancelled
│   └── 📋 Template Invoice
│
├── 📁 Manajemen Refund
│   ├── 📋 Request Refund
│   ├── 📋 Approved Refund
│   ├── 📋 Processed Refund
│   └── ⚙️ Kebijakan Refund
│
├── 📁 Rekonsiliasi
│   ├── 📋 Rekonsiliasi Bank
│   ├── 📋 Settlement Payment Gateway
│   ├── 📋 Unmatched Transactions
│   └── 🔄 Manual Match
│
├── 📁 Laporan Keuangan
│   ├── 📊 Laporan Harian
│   ├── 📊 Laporan Bulanan
│   ├── 📊 Laporan Tahunan
│   ├── 📊 Laporan per Modul
│   ├── 📊 Laporan Pajak (PPN)
│   └── 📤 Export (Excel/PDF)
│
└── 📁 Konfigurasi Keuangan
    ├── ⚙️ Atur PPN
    ├── ⚙️ Atur Biaya Admin
    ├── ⚙️ Atur Mata Uang
    ├── ⚙️ Atur Rekening Perusahaan
    └── ⚙️ Atur Kebijakan Pembulatan
```

---

## 10. LAPORAN & ANALITIK

```
📁 LAPORAN & ANALITIK
│
├── 📊 Dashboard Analitik
│   ├── 📈 KPI Utama
│   ├── 📈 Trend & Forecasting
│   └── 📈 Insight Otomatis
│
├── 📁 Laporan Operasional
│   ├── 📊 Laporan Penumpang
│   │   ├── Penjualan Tiket per Rute
│   │   ├── Okupansi per Jadwal
│   │   ├── On-Time Performance
│   │   └── Top 10 Rute Terlaris
│   │
│   ├── 📊 Laporan Kargo
│   │   ├── Volume Pengiriman
│   │   ├── Utilisasi Gudang
│   │   ├── Utilisasi Armada
│   │   └── Top 10 Komoditas
│   │
│   ├── 📊 Laporan Persewaan
│   │   ├── Okupansi Aset
│   │   ├── Revenue per Aset
│   │   └── Top 10 Penyewa
│   │
│   └── 📊 Laporan Sarana
│       ├── Fleet Readiness
│       ├── Downtime Analysis
│       ├── Biaya Perawatan
│       └── Predictive Maintenance Effectiveness
│
├── 📁 Laporan Keuangan
│   ├── 📊 Revenue Report
│   ├── 📊 Aging Report (Piutang)
│   ├── 📊 Cash Flow
│   └── 📊 Pajak Report
│
├── 📁 Laporan Pelanggan
│   ├── 📊 Customer 360 Report
│   ├── 📊 Loyalty Program Report
│   ├── 📊 Komplain Analysis
│   └── 📊 Churn Analysis
│
├── 📁 Laporan Kinerja
│   ├── 📊 Kinerja Modul
│   ├── 📊 Kinerja Petugas
│   └── 📊 SLA Achievement
│
├── 📁 Custom Report Builder
│   ├── 🔧 Pilih Data Source
│   ├── 🔧 Pilih Fields
│   ├── 🔧 Pilih Filter
│   ├── 🔧 Pilih Grouping
│   └── 📤 Export & Schedule
│
└── 📁 Data Export
    ├── 📥 Export to Excel
    ├── 📥 Export to CSV
    ├── 📥 Export to PDF
    └── ⏰ Scheduled Export
```

---

## 11. PENGATURAN SISTEM

```
📁 PENGATURAN SISTEM
│
├── 📁 Profil Perusahaan
│   ├── ✏️ Informasi Umum
│   ├── 📋 Kontak Perusahaan
│   ├── 🖼️ Logo & Branding
│   └── 📋 Legal Information
│
├── 📁 Pengaturan Aplikasi
│   ├── ⚙️ Nama Aplikasi
│   ├── ⚙️ Versi Aplikasi
│   ├── ⚙️ Timezone
│   ├── ⚙️ Date Format
│   ├── ⚙️ Currency Format
│   └── ⚙️ Language (Bahasa Indonesia / English)
│
├── 📁 Pengaturan Mobile App
│   ├── 🖼️ Logo App
│   ├── 🎨 Warna Tema
│   ├── 📱 Splash Screen
│   ├── 🔧 Force Update Version
│   ├── 📝 Update Notes
│   └── 🔗 App Store & Play Store Links
│
├── 📁 Pengaturan Email & Notifikasi
│   ├── ✉️ SMTP Configuration
│   ├── 📧 Email Template
│   │   ├── Welcome Email
│   │   ├── Invoice Email
│   │   ├── Reminder Email
│   │   └── Promo Email
│   │
│   ├── 📱 Push Notification
│   │   ├── Firebase Configuration
│   │   ├── Template Notifikasi
│   │   └── Schedule Notifikasi
│   │
│   └── 📱 WhatsApp Gateway
│       ├── Konfigurasi API
│       └── Template Pesan
│
├── 📁 Pengaturan Security
│   ├── 🔐 Password Policy
│   │   ├── Minimal Length
│   │   ├── Karakter Khusus
│   │   ├── Masa Berlaku Password
│   │   └── History Password
│   │
│   ├── 🔑 Two-Factor Authentication
│   ├── ⏱️ Session Timeout
│   ├── 🚫 Login Attempt Limit
│   ├── 🌐 IP Whitelist
│   └── 📋 Audit Log Configuration
│
├── 📁 Pengaturan Cache & Performance
│   ├── 🔄 Clear Cache
│   ├── ⚙️ Cache Duration
│   ├── 📊 Performance Metrics
│   └── 🔧 CDN Configuration
│
├── 📁 Backup & Recovery
│   ├── ⏰ Schedule Backup
│   ├── 📋 Daftar Backup
│   ├── 🔄 Restore
│   └── ⚙️ Konfigurasi Storage Backup
│
├── 📁 Log & Monitoring
│   ├── 📋 System Log
│   ├── 📋 Error Log
│   ├── 📋 API Log
│   ├── 📋 Audit Trail
│   └── 📊 System Health
│
└── 📁 Maintenance Mode
    ├── 🚧 Aktifkan Maintenance Mode
    ├── 📝 Pesan Maintenance
    ├── 🌐 IP Whitelist saat Maintenance
    └── ⏱️ Jadwal Maintenance
```

---

## 12. TAXONOMY - QUICK REFERENCE CARD

```
┌─────────────────────────────────────────────────────────────┐
│              QUICK REFERENCE - SUPERADMIN MENU              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  🏠 DASHBOARD       │ Overview, Health, Quick Stats        │
│  📁 MASTER DATA     │ Provinsi, Kota, Wilayah, Referensi   │
│  👥 USER MANAGEMENT │ Users, Roles, Permissions, Audit     │
│  🚆 MODUL 1         │ Penumpang - Rute, Tiket, CRM         │
│  📦 MODUL 2         │ Kargo - WMS, TMS, Order              │
│  🏢 MODUL 3         │ Persewaan - Aset, Kontrak, IoT       │
│  🚂 MODUL 4         │ Rollingstock - Armada, Perawatan     │
│  🔌 INTEGRASI       │ CRM, SCM, HCM, Payment, IoT          │
│  💰 KEUANGAN        │ Transaksi, Invoice, Refund, Report   │
│  📊 LAPORAN         │ Operasional, Keuangan, Custom        │
│  ⚙️ PENGATURAN      │ Profil, App, Security, Backup        │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

---

## 📋 FITUR-FITUR KHUSUS SUPERADMIN

| Fitur | Deskripsi | Lokasi Menu |
| :--- | :--- | :--- |
| **Impersonation** | Login sebagai user lain untuk troubleshooting | User Management |
| **Bulk Operations** | Import/Export data massal | Semua Modul |
