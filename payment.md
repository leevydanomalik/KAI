Saya akan perbaiki **DFD Alur Pembayaran Terintegrasi** dengan format Mermaid yang benar. Error sebelumnya kemungkinan karena sintaks yang kurang tepat.

---

# DFD - ALUR PEMBAYARAN TERINTEGRASI (FIXED)
## Format Mermaid yang Benar

---

## 1. DFD LEVEL 2 - ALUR PEMBAYARAN (FLOWCHART STYLE)

```mermaid
flowchart TB
    subgraph PAYMENT[ALUR PEMBAYARAN TERINTEGRASI]
        
        User((User))
        
        subgraph PLATFORM[PLATFORM KAI]
            direction TB
            M1[Modul 1<br/>Penumpang]
            M2[Modul 2<br/>Kargo]
            M3[Modul 3<br/>Persewaan]
            
            PG[Payment Gateway<br/>Service]
            
            DB1[(DB Transaksi<br/>Penumpang)]
            DB2[(DB Transaksi<br/>Kargo)]
            DB3[(DB Transaksi<br/>Sewa)]
            DW[(Data Warehouse)]
        end
        
        subgraph EXTERNAL[EKSTERNAL]
            direction TB
            PGW[Payment Gateway<br/>Midtrans/Xendit]
            
            subgraph METHOD[Metode Pembayaran]
                Bank[Bank Transfer]
                EWallet[E-Wallet]
                CC[Credit Card]
            end
        end
        
        User -- Pilih Layanan --> M1
        User -- Pilih Layanan --> M2
        User -- Pilih Layanan --> M3
        
        M1 -- Request Payment --> PG
        M2 -- Request Payment --> PG
        M3 -- Request Payment --> PG
        
        PG -- Generate Invoice --> User
        
        User -- Pilih Metode Bayar --> PG
        PG -- Forward ke Payment Gateway --> PGW
        
        PGW -- Proses Pembayaran --> Bank
        PGW -- Proses Pembayaran --> EWallet
        PGW -- Proses Pembayaran --> CC
        
        Bank -- Konfirmasi Sukses/Gagal --> PGW
        EWallet -- Konfirmasi Sukses/Gagal --> PGW
        CC -- Konfirmasi Sukses/Gagal --> PGW
        
        PGW -- Status Pembayaran --> PG
        
        PG -- Update Status ke Modul --> M1
        PG -- Update Status ke Modul --> M2
        PG -- Update Status ke Modul --> M3
        
        M1 -- Simpan Transaksi --> DB1
        M2 -- Simpan Transaksi --> DB2
        M3 -- Simpan Transaksi --> DB3
        
        M1 -- Generate Tiket/Resi --> User
        M2 -- Generate Resi/Invoice --> User
        M3 -- Generate Invoice --> User
        
        DB1 -- Data ke Data Warehouse --> DW
        DB2 -- Data ke Data Warehouse --> DW
        DB3 -- Data ke Data Warehouse --> DW
        
    end
    
    style User fill:#f9f,stroke:#333,stroke-width:4px
    style PGW fill:#ffcdd2,stroke:#333,stroke-width:2px
    style Bank fill:#fff9c4,stroke:#333
    style EWallet fill:#fff9c4,stroke:#333
    style CC fill:#fff9c4,stroke:#333
    style DW fill:#d1c4e9,stroke:#333
```

---

## 2. ALUR PEMBAYARAN - SEQUENCE DIAGRAM

```mermaid
sequenceDiagram
    participant User as Pengguna
    participant Modul as Modul 1/2/3
    participant PG as Payment Gateway Service
    participant PGW as Payment Gateway Eksternal
    participant Bank as Bank/EWallet/CC
    participant DB as Database Transaksi
    
    User->>Modul: 1. Pilih Layanan (Tiket/Kargo/Sewa)
    Modul->>Modul: 2. Hitung Total
    Modul->>PG: 3. Request Pembayaran
    
    PG->>PG: 4. Generate Invoice ID
    PG-->>User: 5. Tampilkan Invoice & Metode Bayar
    
    User->>PG: 6. Pilih Metode Pembayaran
    
    PG->>PGW: 7. Forward Payment Request
    PGW->>Bank: 8. Proses Pembayaran
    
    alt Pembayaran Sukses
        Bank-->>PGW: 9a. Konfirmasi Sukses
        PGW-->>PG: 9b. Status SUCCESS
        
        PG->>Modul: 10. Update Status Sukses
        Modul->>DB: 11. Simpan Transaksi
        DB-->>Modul: 12. Konfirmasi Simpan
        
        Modul-->>User: 13. Tampilkan Tiket/Resi/Invoice
        User->>Modul: 14. Akses Layanan
        
    else Pembayaran Gagal
        Bank-->>PGW: 9a. Konfirmasi Gagal
        PGW-->>PG: 9b. Status FAILED
        
        PG-->>User: 10. Tampilkan Error
        User->>PG: 11. Coba Lagi / Ganti Metode
    end
```

---

## 3. ALUR PEMBAYARAN - STATE DIAGRAM

```mermaid
stateDiagram-v2
    [*] --> MenungguPembayaran
    
    state MenungguPembayaran {
        [*] --> InvoiceDibuat
        InvoiceDibuat --> MenungguKonfirmasi: User pilih metode
    }
    
    MenungguKonfirmasi --> Diproses: Forward ke PG Eksternal
    
    state Diproses {
        [*] --> CekBank
        [*] --> CekEWallet
        [*] --> CekCC
    }
    
    Diproses --> Sukses: Konfirmasi diterima
    Diproses --> Gagal: Ditolak/Timeout
    
    state Sukses {
        [*] --> UpdateStatusModul
        UpdateStatusModul --> SimpanTransaksi
        SimpanTransaksi --> GenerateTiket
    }
    
    state Gagal {
        [*] --> NotifikasiUser
        NotifikasiUser --> UlangPembayaran: User mau coba lagi
        NotifikasiUser --> Batal: User batalkan
    }
    
    Sukses --> [*]: Layanan diberikan
    
    UlangPembayaran --> MenungguPembayaran
    Batal --> [*]
```

---

## 4. ALUR PEMBAYARAN - DATA FLOW DETAIL

```mermaid
flowchart LR
    subgraph INPUT[INPUT DATA]
        A1[Data Order<br/>dari Modul]
        A2[Data User<br/>ID Pelanggan]
        A3[Metode Pembayaran<br/>yang Dipilih]
    end
    
    subgraph PROCESS[PROSES]
        B1[Generate Invoice<br/>ID Unik]
        B2[Hitung Total<br/>+ Biaya Admin]
        B3[Validasi Metode<br/>Pembayaran]
        B4[Komunikasi dengan<br/>PG Eksternal]
        B5[Update Status<br/>Transaksi]
    end
    
    subgraph OUTPUT[OUTPUT DATA]
        C1[Invoice & QR Code]
        C2[Status Transaksi<br/>Sukses/Gagal]
        C3[Tiket/Resi Digital]
        C4[Data Transaksi<br/>ke Database]
    end
    
    subgraph STORAGE[PENYIMPANAN]
        D1[(DB Transaksi<br/>Penumpang)]
        D2[(DB Transaksi<br/>Kargo)]
        D3[(DB Transaksi<br/>Sewa)]
        D4[(Data Warehouse<br/>BigQuery)]
    end
    
    INPUT --> PROCESS
    PROCESS --> OUTPUT
    OUTPUT --> STORAGE
    
    D1 --> D4
    D2 --> D4
    D3 --> D4
    
    style INPUT fill:#e1f5fe
    style PROCESS fill:#fff3e0
    style OUTPUT fill:#e8f5e8
    style STORAGE fill:#f3e5f5
```

---

## 5. INTEGRASI PAYMENT GATEWAY - ARSITEKTUR

```mermaid
graph TB
    subgraph ARCH[ARSITEKTUR PAYMENT GATEWAY]
        
        User((User))
        
        subgraph FRONTEND[FRONTEND]
            F1[Mobile App]
            F2[Web Portal]
        end
        
        subgraph BACKEND[BACKEND - PLATFORM KAI]
            B1[Payment Controller]
            B2[Invoice Generator]
            B3[Transaction Manager]
            B4[Notification Service]
            
            DB[(Database Transaksi)]
        end
        
        subgraph GATEWAY[PAYMENT GATEWAY LAYER]
            G1[API Connector<br/>Midtrans/Xendit]
            G2[Response Handler]
            G3[Webhook Receiver]
        end
        
        subgraph EXTERNAL[EKSTERNAL]
            E1[Bank BCA]
            E2[Bank Mandiri]
            E3[BNI]
            E4[GoPay]
            E5[OVO]
            E6[DANA]
            E7[Visa/Mastercard]
        end
        
        User --> FRONTEND
        FRONTEND --> BACKEND
        
        BACKEND --> GATEWAY
        GATEWAY --> EXTERNAL
        
        EXTERNAL -- "Webhook Callback" --> G3
        G3 -- "Update Status" --> B3
        B3 -- "Update" --> DB
        B3 -- "Trigger" --> B4
        B4 -- "Notifikasi" --> FRONTEND
        FRONTEND -- "Tampilkan Status" --> User
        
    end
    
    style User fill:#f9f
    style GATEWAY fill:#ffcdd2
    style EXTERNAL fill:#fff9c4
    style BACKEND fill:#e1f5fe
```

---

## 6. FLOW PEMBAYARAN LINTAS MODUL

```mermaid
flowchart TD
    Start([User Memilih Layanan]) --> Decision{Modul yang Dipilih}
    
    Decision -->|Tiket Kereta| M1[Modul 1 - Penumpang]
    Decision -->|Kirim Barang| M2[Modul 2 - Kargo]
    Decision -->|Sewa Aset| M3[Modul 3 - Persewaan]
    
    M1 --> C[Hitung Biaya<br/>Tiket + Asuransi]
    M2 --> D[Hitung Biaya<br/>Kargo + Handling]
    M3 --> E[Hitung Biaya<br/>Sewa + Deposit]
    
    C --> F[Generate Invoice]
    D --> F
    E --> F
    
    F --> G[Tampilkan Invoice ke User]
    G --> H[User Pilih Metode Bayar]
    
    H --> I{Metode Pembayaran}
    
    I -->|Bank Transfer| J1[Generate Virtual Account]
    I -->|E-Wallet| J2[Redirect ke E-Wallet App]
    I -->|Credit Card| J3[Form Input Kartu Kredit]
    
    J1 --> K[User Transfer via Bank]
    J2 --> L[User Bayar di E-Wallet]
    J3 --> M[User Input Detail Kartu]
    
    K --> N[Payment Gateway<br/>Terima Konfirmasi]
    L --> N
    M --> N
    
    N --> O{Status?}
    
    O -->|Sukses| P[Update Status Transaksi]
    O -->|Gagal| Q[Notifikasi Gagal ke User]
    
    Q --> H
    
    P --> R[Generate Tiket/Resi/Invoice Final]
    R --> S[Kirim ke User via App/Email]
    S --> T[User Dapat Layanan]
    
    T --> End([Selesai])
    
    style Start fill:#9f9,stroke:#333
    style End fill:#f99,stroke:#333
    style O fill:#ffeb3b,stroke:#333
    style P fill:#8bc34a,stroke:#333
    style Q fill:#ff7043,stroke:#333
```

---

## 7. DATA ENTITY - TRANSAKSI PEMBAYARAN

```mermaid
erDiagram
    TRANSAKSI ||--o{ DETAIL_TRANSAKSI : memiliki
    TRANSAKSI ||--|| INVOICE : menghasilkan
    TRANSAKSI }o--|| USER : dilakukan_oleh
    TRANSAKSI }o--|| MODUL : berasal_dari
    
    USER {
        int user_id PK
        string nama
        string email
        string no_hp
    }
    
    MODUL {
        int modul_id PK
        string nama_modul
        string deskripsi
    }
    
    TRANSAKSI {
        int transaksi_id PK
        int user_id FK
        int modul_id FK
        string invoice_id UK
        datetime tanggal
        decimal total_amount
        string status "PENDING/SUCCESS/FAILED"
        string payment_method
        datetime payment_time
    }
    
    DETAIL_TRANSAKSI {
        int detail_id PK
        int transaksi_id FK
        string item_type "tiket/kargo/sewa"
        int item_id
        string item_name
        int quantity
        decimal price
        decimal subtotal
    }
    
    INVOICE {
        int invoice_id PK
        int transaksi_id FK
        string invoice_number UK
        datetime issue_date
        datetime due_date
        string pdf_url
        string qr_code
    }
    
    PAYMENT_LOG {
        int log_id PK
        int transaksi_id FK
        datetime log_time
        string event "REQUEST/SUCCESS/FAILED/CALLBACK"
        string gateway_response
        string ip_address
    }
```

---

## 8. PAYMENT GATEWAY - INTEGRATION MATRIX

```mermaid
graph TB
    subgraph MATRIX[INTEGRATION MATRIX - PAYMENT GATEWAY]
        
        subgraph METHODS[METODE PEMBAYARAN]
            M1[Bank Transfer<br/>BCA/Mandiri/BNI/BRI]
            M2[E-Wallet<br/>GoPay/OVO/DANA/LinkAja]
            M3[Credit Card<br/>Visa/Mastercard/JCB]
            M4[Convenience Store<br/>Indomaret/Alfamart]
            M5[QRIS]
        end
        
        subgraph MODUL[MODUL YANG DILAYANI]
            MP[Modul 1 - Penumpang]
            MK[Modul 2 - Kargo]
            MS[Modul 3 - Persewaan]
        end
        
        subgraph FEATURES[FITUR PAYMENT GATEWAY]
            F1[One-Click Payment<br/>untuk repeat customer]
            F2[Split Payment<br/>antar beberapa metode]
            F3[Refund Automation]
            F4[Recurring Billing<br/>untuk sewa aset]
            F5[Invoice via Email/WA]
            F6[Multi-currency]
        end
        
        M1 --> MP
        M1 --> MK
        M1 --> MS
        
        M2 --> MP
        M2 --> MK
        
        M3 --> MP
        M3 --> MS
        
        M4 --> MP
        M5 --> MP
        M5 --> MK
        M5 --> MS
        
        MP --> F1
        MP --> F5
        
        MK --> F2
        MK --> F3
        
        MS --> F4
        MS --> F6
        
    end
```

---

## 9. SEQUENCE - PAYMENT CALLBACK HANDLER

```mermaid
sequenceDiagram
    participant PGW as Payment Gateway Eksternal
    participant WH as Webhook Handler
    participant VM as Validator
    participant TM as Transaction Manager
    participant DB as Database
    participant NOTIF as Notification Service
    participant USER as User
    
    PGW->>WH: POST /webhook (payment_data)
    
    WH->>WH: 1. Verifikasi Signature
    WH->>VM: 2. Data Transaksi
    
    VM->>DB: 3. Cek Invoice ID
    DB-->>VM: 4. Data Transaksi
    
    VM->>VM: 5. Validasi Amount
    
    alt Validasi Sukses
        VM-->>WH: 6. Valid OK
        WH->>TM: 7. Update Status
        
        TM->>DB: 8. Update Transaksi ke SUCCESS
        DB-->>TM: 9. Update Confirmed
        
        TM->>NOTIF: 10. Trigger Notifikasi
        NOTIF-->>USER: 11. Email/InApp Notif "Pembayaran Sukses"
        
        TM->>TM: 12. Generate Tiket/Resi
        
    else Validasi Gagal
        VM-->>WH: 6. Valid Failed
        WH->>TM: 7. Update Status Gagal
        TM->>DB: 8. Update Transaksi ke FAILED
        TM->>NOTIF: 9. Alert Admin
    end
    
    WH-->>PGW: 13. HTTP 200 OK
```

---

## 10. PAYMENT DASHBOARD - MONITORING

```mermaid
graph TB
    subgraph DASHBOARD[PAYMENT DASHBOARD - MONITORING REAL-TIME]
        
        subgraph METRICS[METRIK UTAMA]
            M1[Total Transaksi<br/>Hari Ini: Rp X]
            M2[Transaksi Sukses<br/>Hari Ini: X transaksi]
            M3[Transaksi Gagal<br/>Hari Ini: X transaksi]
            M4[Pending Payment<br/>X transaksi]
            M5[Total Revenue<br/>Bulan Ini: Rp X]
        end
        
        subgraph CHART[GRAFIK]
            C1[Grafik Transaksi per Jam]
            C2[Grafik Revenue per Modul]
            C3[Metode Pembayaran Favorit]
        end
        
        subgraph RECENT[TRANSAKSI TERKINI]
            R1[ID: INV001 - Sukses - 10:30]
            R2[ID: INV002 - Pending - 10:25]
            R3[ID: INV003 - Sukses - 10:20]
            R4[ID: INV004 - Failed - 10:15]
        end
        
        subgraph ALERT[ALERT & NOTIFIKASI]
            A1[⚠️ 3 transaksi gagal beruntun]
            A2[⚠️ Payment gateway lambat >5 detik]
        end
        
        METRICS --> CHART
        CHART --> RECENT
        RECENT --> ALERT
        
    end
    
    style METRICS fill:#e1f5fe
    style CHART fill:#fff3e0
    style RECENT fill:#e8f5e8
    style ALERT fill:#ffcdd2
```

---

## 🎯 FITUR-FITUR PAYMENT SYSTEM

| Fitur | Deskripsi | Modul |
| :--- | :--- | :--- |
| **One-Click Payment** | Simpan metode pembayaran untuk transaksi berikutnya | Penumpang |
| **Split Payment** | Bayar dengan 2 metode (contoh: GoPay + CC) | Kargo |
| **Recurring Billing** | Tagihan otomatis bulanan untuk sewa aset | Persewaan |
| **Refund Automation** | Refund otomatis ke sumber pembayaran awal | Semua Modul |
| **Invoice Digital** | Generate dan kirim invoice via email/WA | Semua Modul |
| **QRIS** | Bayar dengan scan QR code | Semua Modul |
| **Multi-currency** | Support mata uang asing untuk pelanggan internasional | Kargo |

---

Semoga diagram yang sudah diperbaiki ini bisa tampil dengan baik! Ada yang ingin ditambahkan?
