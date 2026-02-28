Saya akan buatkan **Enterprise Architecture Landscape dalam format Mermaid** yang bisa langsung Anda gunakan di presentasi (Markdown, Notion, atau tools yang support Mermaid).

---

# ENTERPRISE ARCHITECTURE LANDSCAPE - KAI PLATFORM
## Format Mermaid

---

## 1. STRATEGIC LAYER

```mermaid
graph TB
    subgraph STRATEGIC_LAYER[STRATEGIC LAYER]
        V[VISI PERUSAHAAN<br/>'Menjadi solusi mobilitas dan logistik terintegrasi<br/>berbasis rail yang unggul di Asia Tenggara']
        
        subgraph TUJUAN[TUJUAN STRATEGIS]
            T1[Peningkatan Pendapatan<br/>• Cross-selling<br/>• Utilisasi +20%]
            T2[Efisiensi Operasional<br/>• BBM -15%<br/>• Waktu tunggu -25%]
            T3[Optimasi Aset<br/>• Okupansi +25%<br/>• Utilisasi armada +20%]
            T4[Data-Driven Decision<br/>• Real-time dashboard<br/>• Predictive analytics]
        end
        
        V --> TUJUAN
    end
```

---

## 2. BUSINESS LAYER

```mermaid
graph TB
    subgraph BUSINESS_LAYER[BUSINESS LAYER]
        B[TIGA PILAR BISNIS UTAMA + SATU PENDUKUNG]
        
        subgraph M1[Modul 1: PENUMPANG]
            P1[Pemesanan Tiket]
            P2[Boarding & Layanan]
            P3[Komplain/CRM]
            P4[Loyalty Program]
        end
        
        subgraph M2[Modul 2: KARGO]
            K1[Booking Kargo]
            subgraph WMS[WMS - Warehouse]
                W1[Receiving]
                W2[Put Away]
                W3[Picking]
                W4[Packing]
                W5[Dispatching]
            end
            subgraph TMS[TMS - Transport]
                T1[Route Optimization]
                T2[Load Planning]
                T3[Carrier Management]
                T4[Real-time Tracking]
            end
        end
        
        subgraph M3[Modul 3: PERSEWAAN]
            S1[Katalog Aset Digital]
            S2[Booking Online]
            S3[Kontrak Digital]
            S4[Tagihan Otomatis]
            S5[Monitoring Utilisasi]
            S6[Energy Management]
        end
        
        subgraph M4[Modul 4: SARANA]
            R1[Perawatan Preventif]
            R2[Predictive Maintenance]
            R3[IoT Sensor Monitoring]
            R4[Spare Parts Inventory]
        end
        
        B --> M1
        B --> M2
        B --> M3
        B --> M4
        
        M2 --> WMS
        M2 --> TMS
        
        subgraph LINTAS[PROSES LINTAS MODUL]
            L1[Manajemen Pelanggan - Customer 360]
            L2[Manajemen Armada - Modul 4 ↔ Modul 2]
            L3[Manajemen Aset - Modul 3 ↔ Seluruh Modul]
            L4[Manajemen SDM - Integrasi HCM]
        end
    end
```

---

## 3. APPLICATION LAYER

```mermaid
graph TB
    subgraph APPLICATION_LAYER[APPLICATION LAYER]
        subgraph CHANNELS[CHANNELS / FRONTEND]
            C1[Mobile App Penumpang<br/>Flutter]
            C2[Web Portal Kargo<br/>Next.js]
            C3[Web Portal Persewaan<br/>Next.js]
            C4[Internal Dashboard<br/>React/Grafana]
            C5[Mitra API<br/>REST/GraphQL]
        end
        
        subgraph APPS[BUSINESS APPLICATIONS]
            subgraph A1[Modul 1: PENUMPANG]
                A1_1[Tiket Service]
                A1_2[CRM Integrator]
                A1_3[Loyalty Engine]
                A1_4[Tracking Service]
                A1_5[AI Recommender]
                A1_6[Notifikasi Service]
            end
            
            subgraph A2[Modul 2: KARGO]
                A2_1[Cargo Booking]
                subgraph A2_WMS[WMS Core]
                    WMS1[Receiving]
                    WMS2[Put Away]
                    WMS3[Picking]
                    WMS4[Packing]
                    WMS5[Dispatching]
                    WMS6[Inventory]
                end
                subgraph A2_TMS[TMS Core]
                    TMS1[Route Optimization]
                    TMS2[Load Planning]
                    TMS3[Carrier Management]
                    TMS4[Tracking]
                    TMS5[Dokumen Transportasi]
                end
            end
            
            subgraph A3[Modul 3: PERSEWAAN]
                A3_1[Katalog Aset]
                A3_2[Booking Engine]
                A3_3[Contract Management]
                A3_4[Billing System]
                A3_5[IoT Gateway - Energi]
            end
            
            subgraph A4[Modul 4: ROLLINGSTOCK]
                A4_1[Maintenance Scheduling]
                A4_2[Predictive Maintenance AI]
                A4_3[Fleet Dashboard]
                A4_4[IoT Sensor Hub]
                A4_5[Spare Parts Inventory]
            end
            
            subgraph INTEGRATION[INTEGRATION SERVICES]
                I1[API Gateway - Kong/APISIX]
                I2[Message Queue - Kafka]
                I3[ESB - MuleSoft]
                I4[SSO - Keycloak]
            end
            
            subgraph DATA_PLATFORM[DATA PLATFORM]
                D1[Data Warehouse - BigQuery]
                D2[Data Virtualization - Dremio]
                D3[BI Reporting - Tableau]
                D4[Master Data Management]
            end
        end
        
        CHANNELS --> APPS
        APPS --> INTEGRATION
        INTEGRATION --> DATA_PLATFORM
    end
```

---

## 4. DATA LAYER

```mermaid
graph TB
    subgraph DATA_LAYER[DATA LAYER]
        subgraph SOURCES[SUMBER DATA - Data Sources]
            DB1[(Modul 1 DB<br/>PostgreSQL)]
            DB2[(Modul 2 DB<br/>PostgreSQL/TimescaleDB)]
            DB3[(Modul 3 DB<br/>PostgreSQL)]
            DB4[(Modul 4 DB<br/>InfluxDB/PostgreSQL)]
        end
        
        subgraph WAREHOUSE[DATA WAREHOUSE]
            DW[BigQuery<br/>• Data pelanggan terintegrasi<br/>• Data operasional historis<br/>• Data logistik & transportasi<br/>• Data perawatan sarana<br/>• Data aset & persewaan<br/>• Data IoT sensor]
        end
        
        subgraph VIRTUAL[DATA VIRTUALIZATION]
            DV[Dremio/Denodo<br/>• Menyatukan data berbagai sumber<br/>• API data untuk aplikasi & analitik]
        end
        
        subgraph EXTERNAL[SISTEM EKSTERNAL - Integrasi]
            EXT1[(CRM KAI 121<br/>Customer data)]
            EXT2[(SCM Divisi Logistik<br/>Supply chain)]
            EXT3[(HCM SAP/Raileo<br/>Pegawai data)]
            EXT4[(Sistem Vendor<br/>Outsourcing data)]
        end
        
        SOURCES --> WAREHOUSE
        EXTERNAL --> WAREHOUSE
        WAREHOUSE --> VIRTUAL
        
        DB1 <--> DW
        DB2 <--> DW
        DB3 <--> DW
        DB4 <--> DW
        EXT1 <--> DW
        EXT2 <--> DW
        EXT3 <--> DW
        EXT4 <--> DW
    end
```

---

## 5. TECHNOLOGY LAYER

```mermaid
graph TB
    subgraph TECHNOLOGY_LAYER[TECHNOLOGY LAYER]
        subgraph CLOUD[CLOUD INFRASTRUCTURE - GCP/AWS]
            direction TB
            
            subgraph COMPUTE[COMPUTE]
                Comp1[Kubernetes - GKE/EKS]
                Comp2[Compute Engine/EC2]
                Comp3[Cloud Functions]
                Comp4[App Engine]
            end
            
            subgraph STORAGE[STORAGE]
                S1[Cloud SQL - PostgreSQL]
                S2[BigQuery]
                S3[Cloud Storage]
                S4[Cloud Filestore]
            end
            
            subgraph NETWORKING[NETWORKING]
                N1[VPC]
                N2[Cloud Load Balancing]
                N3[Cloud CDN]
                N4[Cloud DNS]
            end
            
            subgraph SECURITY[SECURITY & IDENTITY]
                Sec1[IAM]
                Sec2[Cloud KMS]
                Sec3[Cloud Armor]
                Sec4[Secret Manager]
            end
            
            subgraph IOT[IoT & INTEGRATION]
                IoT1[IoT Core]
                IoT2[Pub/Sub]
                IoT3[Dataflow]
                IoT4[Cloud Functions]
            end
            
            subgraph AI[ANALYTICS & AI]
                AI1[Vertex AI]
                AI2[TensorFlow]
                AI3[Looker/Tableau]
                AI4[Data Studio]
            end
        end
        
        subgraph DEVOPS[DEVOPS & MONITORING]
            DevOps1[CI/CD<br/>GitLab CI/Cloud Build]
            DevOps2[Monitoring<br/>Grafana/Prometheus]
            DevOps3[Logging<br/>Cloud Logging/Elasticsearch]
            DevOps4[Alerting<br/>Cloud Alerting/PagerDuty]
        end
        
        CLOUD --> DEVOPS
    end
```

---

## 6. INTEGRATION LAYER

```mermaid
graph TB
    subgraph INTEGRATION_LAYER[INTEGRATION LAYER]
        subgraph MATRIX[INTEGRATION MATRIX - Data Flow]
            direction LR
            
            M1[Modul 1<br/>PENUMPANG]
            M2[Modul 2<br/>KARGO]
            M3[Modul 3<br/>PERSEWAAN]
            M4[Modul 4<br/>ROLLINGSTOCK]
            
            M1 -- "Data Pelanggan" --> M2
            M2 -- "Data Okupansi" --> M3
            M3 -- "Data Aset" --> M1
            
            M1 -- "Tracking Kereta" --> M4
            M2 -- "Status Armada" --> M4
            M4 -- "Ketersediaan Armada" --> M2
            M4 -- "Posisi Kereta" --> M1
        end
        
        subgraph EXTERNAL_INT[INTEGRASI EKSTERNAL]
            E1[CRM KAI 121<br/>Data pelanggan, komplain<br/>Read & Write]
            E2[SCM Divisi Logistik<br/>Suku cadang, pengadaan<br/>Read & Write]
            E3[HCM SAP/Raileo<br/>Data pegawai, jadwal<br/>Read Only]
            E4[Sistem Vendor<br/>Outsourcing data<br/>Read Only]
        end
        
        subgraph TECH_INT[INTEGRATION TECHNOLOGIES]
            T1[API Gateway<br/>Kong/APISIX]
            T2[Message Queue<br/>Kafka]
            T3[ESB<br/>MuleSoft]
            T4[SSO<br/>Keycloak]
            T5[WebSocket<br/>Real-time]
        end
        
        MATRIX --> TECH_INT
        EXTERNAL_INT --> TECH_INT
    end
```

---

## 7. SECURITY & GOVERNANCE LAYER

```mermaid
graph TB
    subgraph SECURITY_LAYER[SECURITY & GOVERNANCE LAYER]
        subgraph L1[LAYER 1: IDENTITY & ACCESS MANAGEMENT]
            I1[SSO - Keycloak]
            I2[Multi-Factor Authentication]
            I3[Role-Based Access Control]
            I4[Integrasi Active Directory KAI]
        end
        
        subgraph L2[LAYER 2: DATA SECURITY]
            D1[Enkripsi at rest - AES-256]
            D2[Enkripsi in transit - TLS 1.3]
            D3[Data Masking]
            D4[Tokenization - Payment]
        end
        
        subgraph L3[LAYER 3: API & NETWORK SECURITY]
            N1[API Gateway - Rate Limiting]
            N2[Web Application Firewall]
            N3[DDoS Protection]
            N4[VPC & Private Network]
        end
        
        subgraph L4[LAYER 4: MONITORING & AUDIT]
            A1[Audit Log Semua Akses]
            A2[Real-time Threat Detection]
            A3[Vulnerability Scanning]
            A4[Penetration Testing Berkala]
        end
        
        subgraph GOV[TATA KELOLA - GOVERNANCE]
            G1[Manajemen Proyek - Agile/Scrum]
            G2[Change Management Process]
            G3[Data Governance Committee]
            G4[Compliance - UU PDP, dll]
            G5[SLA Management]
        end
        
        L1 --> L2 --> L3 --> L4
        GOV -.-> L1
        GOV -.-> L2
        GOV -.-> L3
        GOV -.-> L4
    end
```

---

## 8. DEPLOYMENT & OPERATIONS LAYER

```mermaid
graph TB
    subgraph DEPLOYMENT_LAYER[DEPLOYMENT & OPERATIONS LAYER]
        subgraph ENV[ENVIRONMENT STRATEGY]
            direction LR
            DEV[DEV<br/>Developer Sandbox] --> SIT[SIT<br/>System Testing]
            SIT --> UAT[UAT<br/>User Acceptance]
            UAT --> PROD[PROD<br/>Live Production]
        end
        
        subgraph CIPIPELINE[CI/CD PIPELINE]
            C1[Commit] --> C2[Build]
            C2 --> C3[Test]
            C3 --> C4[Deploy to SIT]
            C4 --> C5[Test SIT]
            C5 --> C6[Deploy to UAT]
            C6 --> C7[Test UAT]
            C7 --> C8[Deploy to PROD<br/>Blue-Green/Canary]
        end
        
        subgraph HA[HIGH AVAILABILITY & DISASTER RECOVERY]
            direction LR
            PRIMARY[Region Primary<br/>Jakarta<br/>Active-Active<br/>Real-time sync]
            DR[Region DR<br/>Surabaya<br/>Standby<br/>Failover <1 jam]
            PRIMARY <-->|Replikasi Data| DR
        end
        
        subgraph METRICS[Target Metrics]
            M1[RTO - Recovery Time Objective<br/>< 4 jam]
            M2[RPO - Recovery Point Objective<br/>< 15 menit]
            M3[Availability Target<br/>99.9%]
        end
        
        subgraph SUPPORT[OPERATIONAL SUPPORT]
            O1[24/7 Monitoring - L1/L2/L3]
            O2[Incident Management - SLA Response]
            O3[Problem Management - RCA]
            O4[Capacity Planning]
            O5[Backup & Restore - Daily/Weekly/Monthly]
        end
        
        ENV --> CIPIPELINE
        HA --> METRICS
        CIPIPELINE --> SUPPORT
    end
```

---

## 9. COMPLETE ENTERPRISE ARCHITECTURE LANDSCAPE

```mermaid
graph TB
    subgraph EA[ENTERPRISE ARCHITECTURE LANDSCAPE - KAI PLATFORM]
        
        subgraph S1[STRATEGIC LAYER]
            V[VISI: Solusi Mobilitas & Logistik Terintegrasi]
            T1[Pendapatan] --- T2[Efisiensi] --- T3[Optimasi Aset] --- T4[Data-Driven]
        end
        
        subgraph B1[BUSINESS LAYER]
            B[3 Pilar Bisnis + Sarana]
            B --> M1[Penumpang]
            B --> M2[Kargo]
            B --> M3[Persewaan]
            B --> M4[Sarana]
        end
        
        subgraph A1[APPLICATION LAYER]
            C[Channels: Mobile/Web/API]
            APP[4 Modul Aplikasi]
            INT[Integration Services]
            DP[Data Platform]
        end
        
        subgraph D1[DATA LAYER]
            DS[(Databases)]
            DW[BigQuery Warehouse]
            DV[Dremio Virtualization]
            EXT[(Sistem Eksternal)]
        end
        
        subgraph T1[TECHNOLOGY LAYER]
            CL[Cloud - GCP/AWS]
            COMP[Compute]
            STOR[Storage]
            NET[Network]
            IOT[IoT]
            AI[AI/ML]
        end
        
        subgraph I1[INTEGRATION LAYER]
            API[API Gateway]
            MQ[Message Queue]
            ESB[ESB]
            SSO[SSO]
        end
        
        subgraph SEC[SECURITY LAYER]
            IAM[IAM]
            ENC[Encryption]
            WAF[WAF]
            AUDIT[Audit]
        end
        
        subgraph OPS[OPERATIONS LAYER]
            CICD[CI/CD]
            HA[HA/DR]
            MON[Monitoring]
            SUP[Support]
        end
        
        S1 --> B1
        B1 --> A1
        A1 --> D1
        D1 --> T1
        A1 --> I1
        I1 --> SEC
        T1 --> OPS
        SEC --> OPS
        
        style S1 fill:#e1f5fe
        style B1 fill:#fff3e0
        style A1 fill:#e8f5e8
        style D1 fill:#f3e5f5
        style T1 fill:#ffebee
        style I1 fill:#fff9c4
        style SEC fill:#ffcdd2
        style OPS fill:#d1c4e9
    end
```

---

## 10. RINGKASAN LANDSCAPE (TABEL)

```mermaid
graph LR
    subgraph LEGEND[LEGENDA ARSITEKTUR]
        L1[STRATEGIC<br/>Visión & Tujuan] --> L2[BUSINESS<br/>Proses & Lini Bisnis]
        L2 --> L3[APPLICATION<br/>Aplikasi & Modul]
        L3 --> L4[DATA<br/>Database & Warehouse]
        L4 --> L5[TECHNOLOGY<br/>Infrastruktur & Cloud]
        
        L3 -.-> L6[INTEGRATION<br/>API & Message Queue]
        L6 -.-> L7[SECURITY<br/>Keamanan & Governance]
        L7 -.-> L8[OPERATIONS<br/>Deployment & Support]
    end
    
    style L1 fill:#e1f5fe
    style L2 fill:#fff3e0
    style L3 fill:#e8f5e8
    style L4 fill:#f3e5f5
    style L5 fill:#ffebee
    style L6 fill:#fff9c4
    style L7 fill:#ffcdd2
    style L8 fill:#d1c4e9
```

---

## 📋 CARA MENGGUNAKAN

1. **Salin kode Mermaid** ke dalam file dengan ekstensi `.mmd` atau langsung ke platform yang mendukung Mermaid:
   - GitHub Markdown
   - Notion (dengan plugin Mermaid)
   - Obsidian
   - Mermaid Live Editor (https://mermaid.live)
   - Presentasi tools yang support Mermaid

2. **Untuk presentasi**, Anda bisa mengekspor setiap diagram sebagai PNG/SVG dari Mermaid Live Editor

3. **Urutan presentasi** yang disarankan:
   - Slide 1: Strategic Layer (visi & tujuan)
   - Slide 2: Business Layer (3 pilar bisnis)
   - Slide 3: Application Layer (modul & aplikasi)
   - Slide 4: Data Layer (sumber data)
   - Slide 5: Technology Layer (infrastruktur)
   - Slide 6: Integration Layer (hubungan antar sistem)
   - Slide 7: Security Layer (keamanan)
   - Slide 8: Operations Layer (deployment)
   - Slide 9: Complete Landscape (gabungan)
   - Slide 10: Ringkasan

---

Semoga diagram Mermaid ini membantu presentasi Anda! Ada yang ingin disesuaikan atau ditambahkan?
