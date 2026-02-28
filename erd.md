Saya akan buatkan **Entity Relationship Diagram (ERD)** untuk Landscape Arsitektur Utama platform KAI. ERD ini akan mencakup semua entitas utama dari 4 modul dan hubungan antar entitas.

---

# ENTITY RELATIONSHIP DIAGRAM (ERD)
## Landscape Arsitektur Utama - Platform KAI

---

## 1. ERD MASTER - SEMUA MODUL

```mermaid
erDiagram
    %% MODUL 1: PENUMPANG
    PENUMPANG ||--o{ PEMESANAN_TIKET : melakukan
    PENUMPANG ||--o{ KOMPLAIN : mengajukan
    PENUMPANG ||--o{ LOYALTY_POIN : memiliki
    
    PEMESANAN_TIKET ||--|| TIKET : menghasilkan
    PEMESANAN_TIKET ||--|| PEMBAYARAN : memiliki
    TIKET }o--|| JADWAL_KERETA : untuk
    
    %% MODUL 2: KARGO
    PELANGGAN_KARGO ||--o{ ORDER_KARGO : membuat
    ORDER_KARGO ||--o{ DETAIL_ORDER_KARGO : memiliki
    ORDER_KARGO ||--|| PEMBAYARAN : memiliki
    
    GUDANG ||--o{ INVENTORY_GUDANG : memiliki
    PRODUK ||--o{ INVENTORY_GUDANG : disimpan_di
    
    ORDER_KARGO ||--o{ PICKING_LIST : menghasilkan
    PICKING_LIST ||--o{ DETAIL_PICKING : memiliki
    
    ORDER_KARGO ||--|| SHIPMENT : menjadi
    SHIPMENT ||--|| RUTE_PENGIRIMAN : menggunakan
    SHIPMENT }o--|| ARMADA_KARGO : diangkut_oleh
    
    %% MODUL 3: PERSEWAAN
    PENYEWA ||--o{ BOOKING_ASET : melakukan
    ASET ||--o{ BOOKING_ASET : dipesan_di
    ASET ||--o{ KONTRAK_SEWA : memiliki
    ASET ||--o{ SENSOR_ASET : dipasangi
    
    BOOKING_ASET ||--|| KONTRAK_SEWA : menghasilkan
    KONTRAK_SEWA ||--o{ TAGIHAN_SEWA : memiliki
    TAGIHAN_SEWA ||--|| PEMBAYARAN : dibayar_dengan
    
    %% MODUL 4: ROLLINGSTOCK
    ARMADA ||--o{ PERAWATAN : menjalani
    ARMADA ||--o{ SENSOR_ARMADA : memiliki
    ARMADA {
        string id_armada PK
        string tipe "Lokomotif/Kereta/Gerbong"
        string nomor_seri
        date tahun_pembuatan
        string status "Operasi/Perawatan/Rusak"
        float kilometer_tempuh
    }
    
    PERAWATAN ||--o{ DETAIL_PERAWATAN : memiliki
    PERAWATAN }o--|| TEKNISI : dilakukan_oleh
    
    SUKU_CADANG ||--o{ PEMAKAIAN_SUKU_CADANG : digunakan_di
    PEMAKAIAN_SUKU_CADANG }o--|| PERAWATAN : untuk_perawatan
    
    %% ENTITAS LINTAS MODUL
    PENUMPANG {
        int id_penumpang PK
        string nama
        string email UK
        string no_hp
        date tanggal_lahir
        string alamat
        datetime created_at
    }
    
    PELANGGAN_KARGO {
        int id_pelanggan_kargo PK
        string nama_perusahaan
        string npwp
        string email_perusahaan
        string no_telp
        string alamat
        string pic_nama
        string pic_no_hp
    }
    
    PENYEWA {
        int id_penyewa PK
        string nama
        string email UK
        string no_hp
        string tipe_identitas "KTP/PASPOR"
        string no_identitas
    }
    
    USER_UNIFIED {
        int id_user PK
        string username UK
        string email UK
        string password_hash
        string role
        datetime last_login
        boolean is_active
        int id_penumpang FK "nullable"
        int id_pelanggan_kargo FK "nullable"
        int id_penyewa FK "nullable"
    }
    
    PEMBAYARAN {
        int id_pembayaran PK
        string invoice_number UK
        decimal amount
        string payment_method "Transfer/EWallet/CC"
        string status "PENDING/SUCCESS/FAILED/REFUND"
        datetime payment_date
        string gateway_response
        int id_user FK
        string sumber_modul "Penumpang/Kargo/Sewa"
        int sumber_id "ID di modul asal"
    }
    
    %% RELASI LINTAS MODUL
    PEMBAYARAN }o--|| USER_UNIFIED : dilakukan_oleh
    
    %% RELASI KE MODUL LAIN
    ARMADA ||--o{ SHIPMENT : digunakan_untuk_kargo
    JADWAL_KERETA ||--|| ARMADA : menggunakan_armada
```

---

## 2. ERD MODUL 1 - PENUMPANG (DETAIL)

```mermaid
erDiagram
    PENUMPANG ||--o{ PEMESANAN_TIKET : melakukan
    PENUMPANG ||--o{ KOMPLAIN : mengajukan
    PENUMPANG ||--o{ LOYALTY_POIN : memiliki
    PENUMPANG ||--o{ PREFERENSI_PENUMPANG : memiliki
    
    PEMESANAN_TIKET ||--|| TIKET : menghasilkan
    PEMESANAN_TIKET ||--|| PEMBAYARAN : memiliki
    PEMESANAN_TIKET ||--o{ PENUMPANG_TIKET : berisi_penumpang
    
    TIKET }o--|| JADWAL_KERETA : untuk
    TIKET }o--|| KELAS_LAYANAN : memiliki_kelas
    
    JADWAL_KERETA ||--o{ DETAIL_JADWAL : memiliki
    JADWAL_KERETA }o--|| RUTE : melalui
    JADWAL_KERETA }o--|| ARMADA : menggunakan_armada
    
    RUTE ||--o{ STASIUN_RUTE : memiliki_stasiun
    STASIUN ||--o{ STASIUN_RUTE : berada_di
    
    KOMPLAIN ||--o{ FOLLOW_UP_KOMPLAIN : memiliki
    KOMPLAIN }o--|| PETUGAS_CS : ditangani_oleh
    
    LOYALTY_POIN ||--o{ RIWAYAT_POIN : memiliki
    LOYALTY_POIN }o--|| TIER_MEMBER : masuk_tier
    
    PENUMPANG {
        int id_penumpang PK
        string nama
        string email UK
        string no_hp
        date tanggal_lahir
        string alamat
        string kota
        string kode_pos
        string no_ktp
        datetime created_at
        datetime updated_at
    }
    
    PEMESANAN_TIKET {
        int id_pemesanan PK
        int id_penumpang FK
        string kode_booking UK
        datetime tanggal_pesan
        int jumlah_penumpang
        decimal total_harga
        string status "NEW/PAID/CANCELLED/EXPIRED"
        datetime expired_at
    }
    
    TIKET {
        int id_tiket PK
        int id_pemesanan FK
        int id_jadwal FK
        string kode_tiket UK
        string nama_penumpang
        string no_identitas
        int nomor_kursi
        decimal harga
        string status "ACTIVE/USED/CANCELLED"
        string qr_code
    }
    
    JADWAL_KERETA {
        int id_jadwal PK
        int id_rute FK
        int id_armada FK
        datetime waktu_berangkat
        datetime waktu_tiba
        int durasi_menit
        string status "ON_TIME/DELAYED/CANCELLED"
        int keterlambatan_menit
    }
    
    RUTE {
        int id_rute PK
        string kode_rute UK
        string nama_rute
        int jarak_km
        int stasiun_asal FK
        int stasiun_tujuan FK
    }
    
    STASIUN {
        int id_stasiun PK
        string kode_stasiun UK
        string nama_stasiun
        string kota
        string provinsi
        float latitude
        float longitude
    }
    
    KOMPLAIN {
        int id_komplain PK
        int id_penumpang FK
        string tiket_number
        datetime tanggal_kejadian
        string kategori "Keterlambatan/Pelayanan/Fasilitas/Lainnya"
        string deskripsi
        string status "OPEN/IN_PROGRESS/RESOLVED/CLOSED"
        datetime created_at
        int id_petugas FK
    }
    
    LOYALTY_POIN {
        int id_loyalty PK
        int id_penumpang FK
        int total_poin
        int tier_id FK
        datetime last_update
    }
```

---

## 3. ERD MODUL 2 - KARGO + WMS + TMS (DETAIL)

```mermaid
erDiagram
    PELANGGAN_KARGO ||--o{ ORDER_KARGO : membuat
    ORDER_KARGO ||--o{ DETAIL_ORDER_KARGO : memiliki
    ORDER_KARGO ||--|| PEMBAYARAN : memiliki
    ORDER_KARGO ||--o{ DOKUMEN_KARGO : menghasilkan
    
    GUDANG ||--o{ ZONA_GUDANG : memiliki
    ZONA_GUDANG ||--o{ LOKASI_RAK : memiliki
    LOKASI_RAK ||--o{ INVENTORY_GUDANG : menyimpan
    
    PRODUK ||--o{ INVENTORY_GUDANG : disimpan_di
    PRODUK }o--|| KATEGORI_PRODUK : masuk_kategori
    
    ORDER_KARGO ||--o{ PICKING_LIST : menghasilkan
    PICKING_LIST ||--o{ DETAIL_PICKING : memiliki
    DETAIL_PICKING }o--|| LOKASI_RAK : diambil_dari
    
    ORDER_KARGO ||--|| SHIPMENT : menjadi
    SHIPMENT ||--|| RUTE_PENGIRIMAN : menggunakan
    SHIPMENT }o--|| ARMADA_KARGO : diangkut_oleh
    SHIPMENT ||--o{ TRACKING_HISTORY : memiliki
    
    ARMADA_KARGO }o--|| MODUL4_ARMADA : referensi_dari
    ARMADA_KARGO ||--o{ JADWAL_PENGIRIMAN : memiliki
    
    RUTE_PENGIRIMAN ||--o{ TITIK_RUTE : memiliki
    TITIK_RUTE }o--|| STASIUN_BONGKAR_MUAT : melalui
    
    PELANGGAN_KARGO {
        int id_pelanggan PK
        string nama_perusahaan
        string npwp
        string email
        string no_telp
        string alamat
        string pic_nama
        string pic_no_hp
        string pic_email
        datetime created_at
    }
    
    ORDER_KARGO {
        int id_order PK
        int id_pelanggan FK
        string no_order UK
        datetime tanggal_order
        string tipe_pengiriman "Domestik/Internasional"
        string status_order "DRAFT/BOOKED/PROCESSING/SHIPPED/DELIVERED/CANCELLED"
        datetime requested_pickup_date
        datetime requested_delivery_date
        decimal total_volume
        decimal total_berat
        decimal total_harga
        string catatan
    }
    
    DETAIL_ORDER_KARGO {
        int id_detail PK
        int id_order FK
        int id_produk FK
        string deskripsi_barang
        int quantity
        decimal volume
        decimal berat
        decimal harga_per_unit
        decimal subtotal
    }
    
    GUDANG {
        int id_gudang PK
        string kode_gudang UK
        string nama_gudang
        string lokasi
        float luas_total
        int kapasitas_maks
        string jenis_gudang "Covered/Open/Cold Storage"
    }
    
    PRODUK {
        int id_produk PK
        string sku UK
        string nama_produk
        int id_kategori FK
        string deskripsi
        decimal panjang
        decimal lebar
        decimal tinggi
        decimal berat
        string satuan "KG/TON/M3"
    }
    
    INVENTORY_GUDANG {
        int id_inventory PK
        int id_gudang FK
        int id_produk FK
        int id_lokasi_rak FK
        int quantity
        datetime expired_date "nullable"
        string batch_number
        datetime last_count_date
    }
    
    SHIPMENT {
        int id_shipment PK
        int id_order FK
        string no_shipment UK
        datetime tanggal_kirim
        datetime estimasi_tiba
        int id_armada_kargo FK
        int id_rute FK
        string status "PENDING/IN_TRANSIT/DELIVERED"
    }
    
    ARMADA_KARGO {
        int id_armada_kargo PK
        int id_armada_modul4 FK "referensi ke Modul 4"
        string nomor_gerbong
        int kapasitas_kg
        string tipe_gerbong
        string status_ketersediaan "TERSEDIA/DIPAKAI/PERAWATAN"
    }
    
    TRACKING_HISTORY {
        int id_tracking PK
        int id_shipment FK
        datetime timestamp
        string lokasi
        string status
        float latitude
        float longitude
        string keterangan
    }
```

---

## 4. ERD MODUL 3 - PERSEWAAN ASET (DETAIL)

```mermaid
erDiagram
    PENYEWA ||--o{ BOOKING_ASET : melakukan
    PENYEWA ||--o{ KONTRAK_SEWA : memiliki
    PENYEWA {
        int id_penyewa PK
        string nama
        string email UK
        string no_hp
        string tipe_identitas
        string no_identitas
        string alamat
        string perusahaan "nullable"
        string npwp "nullable"
        datetime created_at
    }
    
    ASET ||--o{ BOOKING_ASET : dipesan_di
    ASET ||--o{ KONTRAK_SEWA : memiliki
    ASET ||--o{ SENSOR_ASET : dipasangi
    ASET ||--o{ DOKUMEN_ASET : memiliki
    ASET }o--|| KATEGORI_ASET : masuk_kategori
    ASET }o--|| STATUS_ASET : memiliki_status
    
    BOOKING_ASET ||--|| KONTRAK_SEWA : menghasilkan
    BOOKING_ASET ||--o{ PEMBAYARAN_DEPOSIT : memiliki
    
    KONTRAK_SEWA ||--o{ TAGIHAN_SEWA : memiliki
    KONTRAK_SEWA ||--o{ AMENDEMEN_KONTRAK : memiliki
    TAGIHAN_SEWA ||--|| PEMBAYARAN : dibayar_dengan
    
    SENSOR_ASET ||--o{ DATA_SENSOR : menghasilkan
    DATA_SENSOR {
        int id_data PK
        int id_sensor FK
        datetime timestamp
        float nilai
        string satuan
    }
    
    ASET {
        int id_aset PK
        string kode_aset UK
        string nama_aset
        int id_kategori FK
        string deskripsi
        string alamat
        float luas_m2
        float latitude
        float longitude
        decimal harga_sewa_per_bulan
        decimal deposit
        int id_status FK
        datetime available_from
        datetime available_to
        string fasilitas
        boolean has_panel_surya
        float kapasitas_panel_surya "kWp"
    }
    
    KATEGORI_ASET {
        int id_kategori PK
        string nama_kategori
        string deskripsi
    }
    
    STATUS_ASET {
        int id_status PK
        string nama_status "TERSEDIA/DISEWA/PERBAIKAN/TIDAK_TERSEDIA"
    }
    
    BOOKING_ASET {
        int id_booking PK
        int id_penyewa FK
        int id_aset FK
        datetime tanggal_booking
        datetime start_date
        datetime end_date
        string tujuan_penyewaan
        string status_booking "PENDING/APPROVED/REJECTED/CANCELLED"
    }
    
    KONTRAK_SEWA {
        int id_kontrak PK
        int id_booking FK
        string no_kontrak UK
        datetime tanggal_mulai
        datetime tanggal_selesai
        decimal nilai_sewa
        decimal deposit
        string file_kontrak_url
        string status_kontrak "AKTIF/SELESAI/TERMINASI"
    }
    
    TAGIHAN_SEWA {
        int id_tagihan PK
        int id_kontrak FK
        string no_tagihan UK
        datetime periode_tagihan
        datetime jatuh_tempo
        decimal jumlah
        string status "UNPAID/PAID/OVERDUE"
        datetime paid_date
    }
    
    SENSOR_ASET {
        int id_sensor PK
        int id_aset FK
        string kode_sensor UK
        string tipe_sensor "SUHU/HUNIAN/ENERGI/KEAMANAN"
        string lokasi_pasang
        date tanggal_pasang
        boolean is_active
    }
```

---

## 5. ERD MODUL 4 - ROLLINGSTOCK MANAGEMENT (DETAIL)

```mermaid
erDiagram
    ARMADA ||--o{ PERAWATAN : menjalani
    ARMADA ||--o{ SENSOR_ARMADA : memiliki
    ARMADA ||--o{ RIWAYAT_OPERASI : memiliki
    ARMADA }o--|| TIPE_ARMADA : memiliki_tipe
    ARMADA {
        int id_armada PK
        string nomor_seri UK
        int id_tipe FK
        string nama_armada
        date tahun_pembuatan
        date tanggal_operasi
        float kilometer_tempuh
        string status "OPERASI/PERAWATAN/RUSAK/APKIR"
        int pemilik_id
        string depo_lokasi
    }
    
    TIPE_ARMADA {
        int id_tipe PK
        string nama_tipe "Lokomotif/Kereta Penumpang/Gerbong Barang"
        string sub_tipe
        string spesifikasi
        int kapasitas
        int daya_mesin
        int jumlah_roda
    }
    
    PERAWATAN ||--o{ DETAIL_PERAWATAN : memiliki
    PERAWATAN }o--|| TEKNISI : dilakukan_oleh
    PERAWATAN ||--o{ PEMAKAIAN_SUKU_CADANG : menggunakan
    PERAWATAN {
        int id_perawatan PK
        int id_armada FK
        int id_teknisi FK
        datetime tanggal_mulai
        datetime tanggal_selesai
        string tipe_perawatan "PREVENTIF/KOREKTIF/PREDIKTIF"
        string deskripsi
        float kilometer_saat_ini
        string hasil_perawatan
        string rekomendasi
    }
    
    SENSOR_ARMADA ||--o{ DATA_SENSOR_ARMADA : menghasilkan
    SENSOR_ARMADA {
        int id_sensor PK
        int id_armada FK
        string kode_sensor UK
        string tipe_sensor "GETARAN/SUHU/TEKANAN/GPS"
        string lokasi_pasang
        date tanggal_pasang
        int frekuensi_pembacaan
    }
    
    DATA_SENSOR_ARMADA {
        int id_data PK
        int id_sensor FK
        datetime timestamp
        float nilai
        string satuan
        boolean is_anomaly
    }
    
    SUKU_CADANG ||--o{ PEMAKAIAN_SUKU_CADANG : digunakan_di
    SUKU_CADANG ||--o{ STOK_SUKU_CADANG : memiliki_stok
    SUKU_CADANG {
        int id_suku_cadang PK
        string kode_part UK
        string nama_part
        string spesifikasi
        string merk
        int harga
        int minimum_stok
        string lokasi_penyimpanan
    }
    
    TEKNISI {
        int id_teknisi PK
        string nama
        string nip
        string spesialisasi
        string level_sertifikasi
        string no_hp
        string email
    }
    
    PREDICTIVE_MODEL {
        int id_model PK
        string nama_model
        string tipe_armada
        string parameter_input
        float akurasi_model
        date tanggal_train
        string file_path
    }
    
    ALERT_PREDICTIVE {
        int id_alert PK
        int id_armada FK
        datetime timestamp
        string tipe_alert
        float confidence_level
        string rekomendasi_tindakan
        string status "NEW/IN_PROGRESS/RESOLVED"
    }
```

---

## 6. ERD INTEGRASI LINTAS MODUL

```mermaid
erDiagram
    %% USER UNIFIED - Single Identity
    USER_UNIFIED ||--o| PENUMPANG : bisa_menjadi
    USER_UNIFIED ||--o| PELANGGAN_KARGO : bisa_menjadi
    USER_UNIFIED ||--o| PENYEWA : bisa_menjadi
    USER_UNIFIED ||--o{ PEMBAYARAN : melakukan
    
    USER_UNIFIED {
        int id_user PK
        string username UK
        string email UK
        string password_hash
        string full_name
        string no_hp
        string role "CUSTOMER/INTERNAL/ADMIN"
        datetime last_login
        boolean is_active
        int id_penumpang FK "nullable"
        int id_pelanggan_kargo FK "nullable"
        int id_penyewa FK "nullable"
        datetime created_at
    }
    
    %% PEMBAYARAN TERPUSAT
    PEMBAYARAN ||--o{ DETAIL_PEMBAYARAN : memiliki
    PEMBAYARAN {
        int id_pembayaran PK
        int id_user FK
        string invoice_number UK
        decimal total_amount
        string payment_method
        string status
        datetime transaction_date
        string payment_gateway
        string gateway_reference
        string callback_data
    }
    
    DETAIL_PEMBAYARAN {
        int id_detail PK
        int id_pembayaran FK
        string sumber_modul "PENUMPANG/KARGO/PERSEWAAN"
        int sumber_id
        decimal amount
        string deskripsi
    }
    
    %% ARMADA - shared resource
    ARMADA_UNIFIED {
        int id_armada PK
        string nomor_armada UK
        string tipe_armada
        string sub_tipe
        string status_operasional
        string lokasi_terkini
        float kilometer_terkini
        int kapasitas_penumpang "untuk Modul 1"
        int kapasitas_kargo_kg "untuk Modul 2"
    }
    
    ARMADA_UNIFIED ||--o{ JADWAL_KERETA : digunakan_Modul1
    ARMADA_UNIFIED ||--o{ ARMADA_KARGO : digunakan_Modul2
    
    %% NOTIFICATION - centralized
    NOTIFICATION ||--o{ NOTIFICATION_RECIPIENT : dikirim_ke
    NOTIFICATION {
        int id_notif PK
        string title
        string body
        string tipe "INFO/PROMO/ALERT/REMINDER"
        string target_role "ALL/PENUMPANG/KARGO/PERSEWAAN"
        datetime send_time
        boolean is_push
        boolean is_email
        boolean is_whatsapp
    }
    
    NOTIFICATION_RECIPIENT {
        int id_recipient PK
        int id_notif FK
        int id_user FK
        datetime read_at
        string status "SENT/DELIVERED/READ"
    }
    
    %% AUDIT LOG - cross-module
    AUDIT_LOG {
        int id_log PK
        datetime timestamp
        int id_user FK
        string action
        string modul
        string entity_type
        int entity_id
        string old_value
        string new_value
        string ip_address
        string user_agent
    }
```

---

## 7. ERD MASTER - HUBUNGAN ANTAR MODUL

```mermaid
erDiagram
    %% HUBUNGAN MODUL 1 DENGAN MODUL 4
    JADWAL_KERETA }o--|| ARMADA_UNIFIED : menggunakan
    
    %% HUBUNGAN MODUL 2 DENGAN MODUL 4
    ARMADA_KARGO ||--|| ARMADA_UNIFIED : referensi_ke
    
    %% HUBUNGAN SEMUA MODUL DENGAN PEMBAYARAN
    PEMESANAN_TIKET ||--|| PEMBAYARAN : memiliki
    ORDER_KARGO ||--|| PEMBAYARAN : memiliki
    TAGIHAN_SEWA ||--|| PEMBAYARAN : memiliki
    
    %% HUBUNGAN SEMUA MODUL DENGAN USER
    PENUMPANG ||--|| USER_UNIFIED : satu_akun
    PELANGGAN_KARGO ||--|| USER_UNIFIED : satu_akun
    PENYEWA ||--|| USER_UNIFIED : satu_akun
    
    %% HUBUNGAN MODUL 2 DENGAN MODUL 3
    ASET }o--|| GUDANG : bisa_jadi_gudang_kargo
    
    %% HUBUNGAN NOTIFIKASI
    USER_UNIFIED ||--o{ NOTIFICATION_RECIPIENT : menerima
    
    ARMADA_UNIFIED {
        int id_armada PK
        string nomor_armada
        string tipe
        string status
    }
    
    JADWAL_KERETA {
        int id_jadwal FK
        int id_armada FK
    }
    
    ARMADA_KARGO {
        int id_armada_kargo PK
        int id_armada FK
    }
    
    PEMBAYARAN {
        int id_pembayaran PK
        int id_user FK
        decimal amount
        string sumber_modul
        int sumber_id
    }
    
    USER_UNIFIED {
        int id_user PK
        string username
        string email
    }
```

---

## 8. ENTITY SUMMARY - DAFTAR ENTITAS UTAMA

| Modul | Entitas | Deskripsi |
| :--- | :--- | :--- |
| **Semua** | USER_UNIFIED | Single identity untuk semua pengguna |
| **Semua** | PEMBAYARAN | Transaksi pembayaran terpusat |
| **Semua** | NOTIFICATION | Notifikasi lintas modul |
| **Semua** | AUDIT_LOG | Log audit untuk semua aktivitas |
| **Modul 1** | PENUMPANG | Data penumpang |
| **Modul 1** | PEMESANAN_TIKET | Pemesanan tiket |
| **Modul 1** | TIKET | Tiket kereta |
| **Modul 1** | JADWAL_KERETA | Jadwal perjalanan |
| **Modul 1** | RUTE | Rute perjalanan |
| **Modul 1** | STASIUN | Data stasiun |
| **Modul 1** | KOMPLAIN | Komplain pelanggan |
| **Modul 1** | LOYALTY_POIN | Poin loyalitas |
| **Modul 2** | PELANGGAN_KARGO | Pelanggan kargo |
| **Modul 2** | ORDER_KARGO | Order kargo |
| **Modul 2** | GUDANG | Data gudang |
| **Modul 2** | PRODUK | Master produk |
| **Modul 2** | INVENTORY_GUDANG | Stok di gudang |
| **Modul 2** | SHIPMENT | Pengiriman |
| **Modul 2** | ARMADA_KARGO | Armada kargo |
| **Modul 2** | TRACKING_HISTORY | Riwayat tracking |
| **Modul 3** | PENYEWA | Penyewa aset |
| **Modul 3** | ASET | Data aset |
| **Modul 3** | BOOKING_ASET | Booking aset |
| **Modul 3** | KONTRAK_SEWA | Kontrak sewa |
| **Modul 3** | TAGIHAN_SEWA | Tagihan sewa |
| **Modul 3** | SENSOR_ASET | Sensor IoT di aset |
| **Modul 4** | ARMADA | Data armada |
| **Modul 4** | TIPE_ARMADA | Tipe armada |
| **Modul 4** | PERAWATAN | Perawatan armada |
| **Modul 4** | SENSOR_ARMADA | Sensor di armada |
| **Modul 4** | SUKU_CADANG | Master suku cadang |
| **Modul 4** | TEKNISI | Data teknisi |
| **Modul 4** | PREDICTIVE_ALERT | Alert prediktif |

---

## 9. RELATIONSHIP CARDINALITY SUMMARY

| Relationship | Type | Deskripsi |
| :--- | :--- | :--- |
| PENUMPANG : PEMESANAN_TIKET | 1 : N | Satu penumpang bisa banyak pemesanan |
| PEMESANAN_TIKET : TIKET | 1 : N | Satu pemesanan bisa banyak tiket |
| JADWAL_KERETA : ARMADA_UNIFIED | N : 1 | Banyak jadwal bisa pakai satu armada |
| PELANGGAN_KARGO : ORDER_KARGO | 1 : N | Satu pelanggan banyak order |
| ORDER_KARGO : DETAIL_ORDER | 1 : N | Satu order banyak detail |
| ORDER_KARGO : SHIPMENT | 1 : 1 | Satu order jadi satu shipment |
| SHIPMENT : TRACKING_HISTORY | 1 : N | Satu shipment banyak tracking |
| GUDANG : INVENTORY | 1 : N | Satu gudang banyak inventory |
| ASET : KONTRAK_SEWA | 1 : N | Satu aset bisa banyak kontrak |
| PENYEWA : KONTRAK_SEWA | 1 : N | Satu penyewa banyak kontrak |
| ARMADA : PERAWATAN | 1 : N | Satu armada banyak perawatan |
| USER_UNIFIED : PEMBAYARAN | 1 : N | Satu user banyak pembayaran |
| PEMBAYARAN : DETAIL_PEMBAYARAN | 1 : N | Satu pembayaran bisa untuk banyak modul |

---

## 10. DATA WAREHOUSE - STAR SCHEMA

```mermaid
erDiagram
    %% FACT TABLES
    FACT_PENJUALAN_TIKET ||--o{ DIM_WAKTU : memiliki
    FACT_PENJUALAN_TIKET ||--o{ DIM_PENUMPANG : memiliki
    FACT_PENJUALAN_TIKET ||--o{ DIM_RUTE : memiliki
    FACT_PENJUALAN_TIKET ||--o{ DIM_LAYANAN : memiliki
    
    FACT_PENGIRIMAN_KARGO ||--o{ DIM_WAKTU : memiliki
    FACT_PENGIRIMAN_KARGO ||--o{ DIM_PELANGGAN_KARGO : memiliki
    FACT_PENGIRIMAN_KARGO ||--o{ DIM_RUTE : memiliki
    FACT_PENGIRIMAN_KARGO ||--o{ DIM_PRODUK : memiliki
    
    FACT_PERSEWAAN_ASET ||--o{ DIM_WAKTU : memiliki
    FACT_PERSEWAAN_ASET ||--o{ DIM_PENYEWA : memiliki
    FACT_PERSEWAAN_ASET ||--o{ DIM_ASET : memiliki
    
    FACT_PERAWATAN_ARMADA ||--o{ DIM_WAKTU : memiliki
    FACT_PERAWATAN_ARMADA ||--o{ DIM_ARMADA : memiliki
    FACT_PERAWATAN_ARMADA ||--o{ DIM_TEKNISI : memiliki
    
    %% DIMENSION TABLES
    DIM_WAKTU {
        int id_waktu PK
        date tanggal
        int tahun
        int bulan
        int minggu
        int hari
        string hari_nama
        string kuartal
        boolean is_weekend
        boolean is_holiday
    }
    
    DIM_PENUMPANG {
        int id_penumpang PK
        string nama
        string kota
        string provinsi
        int usia
        string gender
        int tier_loyalty
    }
    
    DIM_RUTE {
        int id_rute PK
        string kode_rute
        string stasiun_asal
        string stasiun_tujuan
        string kota_asal
        string kota_tujuan
        int jarak_km
    }
    
    DIM_PELANGGAN_KARGO {
        int id_pelanggan PK
        string nama_perusahaan
        string kota
        string provinsi
        string sektor_industri
        int total_order_ytd
    }
    
    DIM_ASET {
        int id_aset PK
        string kode_aset
        string nama_aset
        string kota
        string tipe_aset
        float luas_m2
        string status
    }
    
    DIM_ARMADA {
        int id_armada PK
        string nomor_armada
        string tipe_armada
        int tahun_pembuatan
        int umur_tahun
        float kilometer_terkini
    }
```

---

## 📋 CARA MENGGUNAKAN ERD

| Kegunaan | Diagram yang Digunakan |
| :--- | :--- |
| **Gambaran Umum** | ERD Master - Semua Modul (1) |
| **Detail per Modul** | ERD Modul 1-4 (2,3,4,5) |
| **Integrasi Antar Modul** | ERD Integrasi Lintas Modul (6) |
| **Relasi Lengkap** | ERD Master - Hubungan (7) |
| **Daftar Entitas** | Entity Summary (8) |
| **Business Intelligence** | Data Warehouse Star Schema (10) |

---

Semoga ERD ini membantu dalam menjelaskan struktur data platform KAI! Ada yang ingin ditambahkan atau disesuaikan?
