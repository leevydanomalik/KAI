Saya akan buatkan **Enterprise Architecture Landscape** dalam format yang bisa digunakan untuk presentasi dan dokumentasi. Karena Anda meminta format "memaid", saya asumsikan Anda meminta diagram yang jelas dan terstruktur seperti arsitektur enterprise pada umumnya.

---

# ENTERPRISE ARCHITECTURE LANDSCAPE
## Platform Digital Terintegrasi KAI

---

## 1. STRATEGIC LAYER (Visión & Strategi)

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           STRATEGIC LAYER                                            │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                      VISI PERUSAHAAN                                           │   │
│  │         "Menjadi solusi mobilitas dan logistik terintegrasi berbasis rail     │   │
│  │                yang unggul di Asia Tenggara melalui transformasi digital"      │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                    TUJUAN STRATEGIS PLATFORM                                  │   │
│  ├─────────────────┬─────────────────┬─────────────────┬───────────────────────┤   │
│  │   Peningkatan   │   Efisiensi     │   Optimasi      │   Data-Driven         │   │
│  │   Pendapatan    │   Operasional   │   Aset          │   Decision Making     │   │
│  │   • Cross-selling│ • BBM -15%     │ • Okupansi +25% │ • Real-time dashboard │   │
│  │   • Utilisasi +20%│ • Waktu tunggu│ • Utilisasi     │ • Predictive analytics│   │
│  │   • Okupansi +25%│   -25%         │   armada +20%   │ • AI recommendations  │   │
│  └─────────────────┴─────────────────┴─────────────────┴───────────────────────┘   │
│                                                                                       │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 2. BUSINESS LAYER (Lini Bisnis & Proses)

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                            BUSINESS LAYER                                            │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                     3 PILAR BISNIS UTAMA + 1 PENDUKUNG                        │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────┐│
│  │   PENUMPANG      │  │     KARGO        │  │   PERSEWAAN      │  │   SARANA     ││
│  │   (Modul 1)      │  │   (Modul 2)      │  │   (Modul 3)      │  │  (Modul 4)   ││
│  ├──────────────────┤  ├──────────────────┤  ├──────────────────┤  ├──────────────┤│
│  │ Proses:          │  │ Proses:          │  │ Proses:          │  │ Proses:      ││
│  │ • Pemesanan tiket│  │ • Booking kargo  │  │ • Katalog aset   │  │ • Perawatan  ││
│  │ • Boarding       │  │ • WMS: receiving │  │ • Booking online │  │   preventif  ││
│  │ • Layanan onboard│  │   put away,pick  │  │ • Kontrak digital│  │ • Predictive ││
│  │ • Komplain/CRM   │  │   pack,dispatch  │  │ • Tagihan otomatis│  │   maintenance││
│  │ • Loyalty program│  │ • TMS: route opt │  │ • Monitoring     │  │ • IoT sensor ││
│  │                  │  │   load planning, │  │   utilisasi      │  │   monitoring ││
│  │                  │  │   tracking       │  │ • Energy mgmt    │  │ • Spare parts││
│  └──────────────────┘  └──────────────────┘  └──────────────────┘  └──────────────┘│
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                    PROSES BISNIS LINTAS MODUL                                 │   │
│  │  ┌─────────────────────────────────────────────────────────────────────┐    │   │
│  │  │ • Manajemen Pelanggan (Customer 360 dari CRM)                       │    │   │
│  │  │ • Manajemen Armada (Modul 4 → Modul 2 untuk ketersediaan gerbong)   │    │   │
│  │  │ • Manajemen Aset (Modul 3 → utilisasi properti)                      │    │   │
│  │  │ • Manajemen SDM (integrasi read-only dengan HCM)                    │    │   │
│  │  └─────────────────────────────────────────────────────────────────────┘    │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. APPLICATION LAYER (Aplikasi & Modul)

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           APPLICATION LAYER                                          │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                      CHANNELS / FRONTEND                                      │   │
│  ├──────────────┬──────────────┬──────────────┬──────────────┬───────────────┤   │
│  │ Mobile App   │ Web Portal   │ Web Portal   │ Internal     │ Mitra API     │   │
│  │ Penumpang    │ Kargo        │ Persewaan    │ Dashboard    │ Eksternal     │   │
│  │ (Flutter)    │ (Next.js)    │ (Next.js)    │ (React/Grafana)│ (REST/GraphQL)│   │
│  └──────────────┴──────────────┴──────────────┴──────────────┴───────────────┘   │
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                         BUSINESS APPLICATIONS                                 │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────────┐│
│  │                                                                                   ││
│  │  ┌────────────────────┐    ┌────────────────────┐    ┌────────────────────┐   ││
│  │  │   MODUL 1          │    │   MODUL 2          │    │   MODUL 3          │   ││
│  │  │   PENUMPANG        │    │   KARGO            │    │   PERSEWAAN        │   ││
│  │  ├────────────────────┤    ├────────────────────┤    ├────────────────────┤   ││
│  │  │ • Tiket Service    │    │ • Cargo Booking    │    │ • Katalog Aset     │   ││
│  │  │ • CRM Integrator   │    │ • WMS Core         │    │ • Booking Engine   │   ││
│  │  │ • Loyalty Engine   │    │   - Receiving      │    │ • Contract Mgmt    │   ││
│  │  │ • Tracking Service │    │   - Put Away       │    │ • Billing System   │   ││
│  │  │ • AI Recommender   │    │   - Picking        │    │ • IoT Gateway      │   ││
│  │  │ • Notifikasi       │    │   - Packing        │    │   (Energi)         │   ││
│  │  │                    │    │   - Dispatching    │    │                    │   ││
│  │  │                    │    │   - Inventory      │    │                    │   ││
│  │  │                    │    │ • TMS Core         │    │                    │   ││
│  │  │                    │    │   - Route Opt      │    │                    │   ││
│  │  │                    │    │   - Load Planning  │    │                    │   ││
│  │  │                    │    │   - Carrier Mgmt   │    │                    │   ││
│  │  │                    │    │   - Tracking       │    │                    │   ││
│  │  │                    │    │   - Dokumen Trans  │    │                    │   ││
│  │  └────────────────────┘    └────────────────────┘    └────────────────────┘   ││
│  │                                                                                   ││
│  │  ┌────────────────────┐    ┌────────────────────┐    ┌────────────────────┐   ││
│  │  │   MODUL 4          │    │   INTEGRATION      │    │   DATA PLATFORM    │   ││
│  │  │   ROLLINGSTOCK     │    │   SERVICES         │    │                    │   ││
│  │  ├────────────────────┤    ├────────────────────┤    ├────────────────────┤   ││
│  │  │ • Maintenance      │    │ • API Gateway      │    │ • Data Warehouse   │   ││
│  │  │   Scheduling       │    │   (Kong/APISIX)    │    │   (BigQuery)       │   ││
│  │  │ • Predictive       │    │ • Message Queue    │    │ • Data Virtualization│   │
│  │  │   Maintenance (AI) │    │   (Kafka)          │    │   (Dremio)         │   ││
│  │  │ • Fleet Dashboard  │    │ • ESB              │    │ • BI Reporting     │   ││
│  │  │ • IoT Sensor Hub   │    │   (MuleSoft)       │    │   (Tableau)        │   ││
│  │  │ • Spare Parts      │    │ • SSO (Keycloak)   │    │ • Master Data Mgmt │   ││
│  │  │   Inventory        │    │                    │    │                    │   ││
│  │  └────────────────────┘    └────────────────────┘    └────────────────────┘   ││
│  │                                                                                   ││
│  └─────────────────────────────────────────────────────────────────────────────────┘│
│                                                                                       │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 4. DATA LAYER (Sumber Data & Aliran)

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              DATA LAYER                                              │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                      SUMBER DATA (Data Sources)                              │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────────┐│
│  │                                                                                   ││
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐       ││
│  │  │   Modul 1    │  │   Modul 2    │  │   Modul 3    │  │   Modul 4    │       ││
│  │  │   Database   │  │   Database   │  │   Database   │  │   Database   │       ││
│  │  │ (PostgreSQL) │  │ (PostgreSQL/ │  │ (PostgreSQL) │  │ (InfluxDB/   │       ││
│  │  │              │  │ TimescaleDB) │  │              │  │  PostgreSQL) │       ││
│  │  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘       ││
│  │         │                 │                  │                 │                ││
│  │         └─────────────────┼──────────────────┼─────────────────┘                ││
│  │                           │                  │                                  ││
│  │  ┌────────────────────────▼──────────────────▼─────────────────────────────┐  ││
│  │  │                      DATA WAREHOUSE (BigQuery)                           │  ││
│  │  │  • Data pelanggan terintegrasi  • Data operasional historis              │  ││
│  │  │  • Data logistik & transportasi • Data perawatan sarana                  │  ││
│  │  │  • Data aset & persewaan        • Data IoT sensor                        │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │              DATA VIRTUALIZATION LAYER (Dremio/Denodo)                   │  ││
│  │  │  • Menyatukan data dari berbagai sumber tanpa memindahkan                │  ││
│  │  │  • Menyediakan API data untuk aplikasi dan analitik                      │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │                    SISTEM EKSTERNAL (Integrasi)                          │  ││
│  │  │  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐        │  ││
│  │  │  │ CRM KAI 121│  │ SCM Divisi │  │ HCM (SAP/  │  │ Sistem     │        │  ││
│  │  │  │ (Customer │  │ Logistik   │  │   Raileo)  │  │ Vendor     │        │  ││
│  │  │  │   data)   │  │ (Supply    │  │ (Pegawai   │  │ Outsourcing│        │  ││
│  │  │  │           │  │   chain)   │  │   data)    │  │            │        │  ││
│  │  │  └────────────┘  └────────────┘  └────────────┘  └────────────┘        │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  └─────────────────────────────────────────────────────────────────────────────────┘│
│                                                                                       │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 5. TECHNOLOGY LAYER (Infrastruktur & Platform)

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           TECHNOLOGY LAYER                                           │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                    CLOUD INFRASTRUCTURE (GCP/AWS)                            │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────────┐│
│  │                                                                                   ││
│  │  ┌─────────────────────────┐    ┌─────────────────────────┐                    ││
│  │  │   COMPUTE               │    │   STORAGE                │                    ││
│  │  │  • Kubernetes (GKE/EKS) │    │  • Cloud SQL (PostgreSQL)│                    ││
│  │  │  • Compute Engine/EC2   │    │  • BigQuery              │                    ││
│  │  │  • Cloud Functions      │    │  • Cloud Storage         │                    ││
│  │  │  • App Engine           │    │  • Cloud Filestore       │                    ││
│  │  └─────────────────────────┘    └─────────────────────────┘                    ││
│  │                                                                                   ││
│  │  ┌─────────────────────────┐    ┌─────────────────────────┐                    ││
│  │  │   NETWORKING            │    │   SECURITY & IDENTITY    │                    ││
│  │  │  • VPC                  │    │  • IAM                   │                    ││
│  │  │  • Cloud Load Balancing │    │  • Cloud KMS             │                    ││
│  │  │  • Cloud CDN            │    │  • Cloud Armor           │                    ││
│  │  │  • Cloud DNS            │    │  • Secret Manager        │                    ││
│  │  └─────────────────────────┘    └─────────────────────────┘                    ││
│  │                                                                                   ││
│  │  ┌─────────────────────────┐    ┌─────────────────────────┐                    ││
│  │  │   IOT & INTEGRATION     │    │   ANALYTICS & AI        │                    ││
│  │  │  • IoT Core             │    │  • Vertex AI            │                    ││
│  │  │  • Pub/Sub              │    │  • TensorFlow           │                    ││
│  │  │  • Dataflow             │    │  • Looker/Tableau       │                    ││
│  │  │  • Cloud Functions      │    │  • Data Studio          │                    ││
│  │  └─────────────────────────┘    └─────────────────────────┘                    ││
│  │                                                                                   ││
│  └─────────────────────────────────────────────────────────────────────────────────┘│
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                   DEVOPS & MONITORING                                         │   │
│  ├──────────────────┬──────────────────┬──────────────────┬──────────────────┤   │
│  │   CI/CD          │   MONITORING     │   LOGGING        │   ALERTING       │   │
│  │ • GitLab CI      │ • Cloud Monitor  │ • Cloud Logging  │ • Cloud Alerting │   │
│  │ • Cloud Build    │ • Grafana        │ • Elasticsearch  │ • PagerDuty      │   │
│  │ • Jenkins        │ • Prometheus     │ • Kibana         │ • Opsgenie       │   │
│  └──────────────────┴──────────────────┴──────────────────┴──────────────────┘   │
│                                                                                       │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 6. INTEGRATION LAYER (Hubungan Antar Sistem)

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           INTEGRATION LAYER                                          │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                   INTEGRATION MATRIX (Data Flow)                             │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────────┐│
│  │                                                                                   ││
│  │  ┌──────────────┐         ┌──────────────┐         ┌──────────────┐            ││
│  │  │   MODUL 1    │◄───────►│   MODUL 2    │◄───────►│   MODUL 3    │            ││
│  │  │  PENUMPANG   │  Data   │    KARGO     │  Data   │  PERSEWAAN   │            ││
│  │  │              │ Pelang- │              │ Okupansi│              │            ││
│  │  │              │  gan    │              │   Aset  │              │            ││
│  │  └──────┬───────┘         └──────┬───────┘         └──────────────┘            ││
│  │         │                        │                                              ││
│  │         │ Tracking           Status│                                            ││
│  │         │ Kereta              Armada│                                            ││
│  │         │                        │                                              ││
│  │  ┌──────▼────────────────────────▼───────┐                                    ││
│  │  │              MODUL 4                    │                                    ││
│  │  │         ROLLINGSTOCK MANAGEMENT         │                                    ││
│  │  │  • Menyediakan data armada ke Modul 2  │                                    ││
│  │  │  • Menyediakan tracking ke Modul 1     │                                    ││
│  │  │  • Menerima jadwal utilisasi dari TMS  │                                    ││
│  │  └────────────────────────────────────────┘                                    ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │                    INTEGRASI EKSTERNAL                                    │  ││
│  │  ├────────────────────┬─────────────────────┬──────────────────────────────┤  ││
│  │  │   CRM KAI 121      │   SCM Divisi        │   HCM (SAP/Raileo)           │  ││
│  │  │   • Data pelanggan │   Logistik          │   • Data pegawai             │  ││
│  │  │   • Riwayat komplain│   • Suku cadang    │   • Jadwal tugas             │  ││
│  │  │   • Feedback       │   • Pengadaan       │   • Sertifikasi              │  ││
│  │  │   (Read & Write)   │   (Read & Write)    │   (Read Only)                │  ││
│  │  └────────────────────┴─────────────────────┴──────────────────────────────┘  ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │                    INTEGRATION TECHNOLOGIES                               │  ││
│  │  │                                                                           │  ││
│  │  │   ┌───────────────────────────────────────────────────────────────┐    │  ││
│  │  │   │  API GATEWAY (Kong/APISIX)  •  MESSAGE QUEUE (Kafka)          │    │  ││
│  │  │   │  ESB (MuleSoft)             •  SSO (Keycloak)                 │    │  ││
│  │  │   │  REST/GraphQL APIs          •  WebSocket (real-time)          │    │  ││
│  │  │   └───────────────────────────────────────────────────────────────┘    │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  └─────────────────────────────────────────────────────────────────────────────────┘│
│                                                                                       │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 7. SECURITY & GOVERNANCE LAYER

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                      SECURITY & GOVERNANCE LAYER                                     │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                      KEAMANAN BERTINGKAT                                     │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────────┐│
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │   LAYER 1: IDENTITY & ACCESS MANAGEMENT                                  │  ││
│  │  │  • Single Sign-On (SSO) dengan Keycloak                                  │  ││
│  │  │  • Multi-Factor Authentication (MFA)                                     │  ││
│  │  │  • Role-Based Access Control (RBAC)                                      │  ││
│  │  │  • Integrasi dengan Active Directory KAI                                │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │   LAYER 2: DATA SECURITY                                                 │  ││
│  │  │  • Enkripsi data at rest (AES-256)                                       │  ││
│  │  │  • Enkripsi data in transit (TLS 1.3)                                    │  ││
│  │  │  • Data masking untuk data sensitif                                      │  ││
│  │  │  • Tokenization untuk payment data                                       │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │   LAYER 3: API & NETWORK SECURITY                                        │  ││
│  │  │  • API Gateway dengan rate limiting                                      │  ││
│  │  │  • Web Application Firewall (WAF)                                        │  ││
│  │  │  • DDoS Protection                                                       │  ││
│  │  │  • VPC & Private Network                                                 │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │   LAYER 4: MONITORING & AUDIT                                            │  ││
│  │  │  • Audit log semua akses data                                            │  ││
│  │  │  • Real-time threat detection                                            │  ││
│  │  │  • Vulnerability scanning                                                │  ││
│  │  │  • Penetration testing berkala                                           │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  └─────────────────────────────────────────────────────────────────────────────────┘│
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                    TATA KELOLA (GOVERNANCE)                                  │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │  • Manajemen Proyek (Agile/Scrum)                                           │   │
│  │  • Change Management Process                                                │   │
│  │  • Data Governance Committee                                                │   │
│  │  • Compliance dengan regulasi (UU PDP, dll)                                 │   │
│  │  • SLA Management dengan vendor                                             │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 8. DEPLOYMENT & OPERATIONS LAYER

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                      DEPLOYMENT & OPERATIONS LAYER                                   │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                    DEPLOYMENT ARCHITECTURE                                    │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────────┐│
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │   ENVIRONMENT STRATEGY                                                    │  ││
│  │  │                                                                           │  ││
│  │  │   ┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐      │  ││
│  │  │   │ DEV      │────►│ SIT      │────►│ UAT      │────►│ PROD     │      │  ││
│  │  │   │(Developer│     │(System   │     │(User     │     │(Live)    │      │  ││
│  │  │   │ sandbox) │     │ Testing) │     │Acceptance)│     │          │      │  ││
│  │  │   └──────────┘     └──────────┘     └──────────┘     └──────────┘      │  ││
│  │  │                                                                           │  ││
│  │  │   • Setiap environment terisolasi                                        │  ││
│  │  │   • Data production tidak pernah ke non-prod                            │  ││
│  │  │   • Automated deployment dengan CI/CD                                   │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │   CI/CD PIPELINE                                                         │  ││
│  │  │                                                                           │  ││
│  │  │   Commit → Build → Test → Deploy to SIT → Test → Deploy to UAT → Test →  │  ││
│  │  │   → Deploy to PROD (Blue-Green atau Canary)                              │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  │  ┌──────────────────────────────────────────────────────────────────────────┐  ││
│  │  │   HIGH AVAILABILITY & DISASTER RECOVERY                                 │  ││
│  │  │                                                                           │  ││
│  │  │   ┌────────────────────┐          ┌────────────────────┐               │  ││
│  │  │   │   Region Primary   │          │   Region DR        │               │  ││
│  │  │   │   (Jakarta)        │◄────────►│   (Surabaya)       │               │  ││
│  │  │   │   • Active-Active  │  Replikasi│   • Standby        │               │  ││
│  │  │   │   • Real-time sync │  data    │   • Failover <1 jam│               │  ││
│  │  │   └────────────────────┘          └────────────────────┘               │  ││
│  │  │                                                                           │  ││
│  │  │   • RTO (Recovery Time Objective): < 4 jam                               │  ││
│  │  │   • RPO (Recovery Point Objective): < 15 menit                          │  ││
│  │  └──────────────────────────────────────────────────────────────────────────┘  ││
│  │                                                                                   ││
│  └─────────────────────────────────────────────────────────────────────────────────┘│
│                                                                                       │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                    OPERATIONAL SUPPORT                                       │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │  • 24/7 Monitoring (L1, L2, L3 Support)                                     │   │
│  │  • Incident Management (SLA response time)                                  │   │
│  │  • Problem Management (root cause analysis)                                 │   │
│  │  • Capacity Planning                                                         │   │
│  │  • Backup & Restore (daily, weekly, monthly)                                │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                       │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 RINGKASAN LANDSCAPE ARSITEKTUR

| Layer | Komponen Utama | Teknologi Kunci |
| :--- | :--- | :--- |
| **Strategic** | Visi, Tujuan Strategis | - |
| **Business** | 3 Pilar Bisnis + Sarana | Proses bisnis terintegrasi |
| **Application** | 4 Modul Utama + Channels | Flutter, React, Next.js, Grafana |
| **Data** | Database, Warehouse, Virtualisasi | PostgreSQL, BigQuery, Dremio |
| **Technology** | Cloud Infra, Compute, Storage | GCP/AWS, Kubernetes, Cloud SQL |
| **Integration** | API Gateway, Message Queue, ESB | Kong, Kafka, MuleSoft |
| **Security** | IAM, Enkripsi, WAF, Audit | Keycloak, TLS, Cloud Armor |
| **Operations** | CI/CD, HA/DR, Monitoring | GitLab CI, Grafana, Prometheus |

---

Semoga diagram Enterprise Architecture Landscape ini membantu presentasi Anda! Ada yang ingin ditambahkan atau disesuaikan?
