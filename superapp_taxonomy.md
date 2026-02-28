Saya akan buatkan **struktur project folder Superapps KAI** yang lengkap dengan teknologi yang Anda sebutkan. Struktur ini dirancang untuk mendukung **monorepo dengan Turborepo**, **microfrontend**, dan **arsitektur modular/plugin-based**.

---

# STRUKTUR PROJECT FOLDER SUPERAPPS KAI
## Teknologi: TypeScript, Next.js 16, Tailwind CSS, ShadCN/Radix, Turborepo, Microfrontend, Modular, Plugin Architecture

---

```
📦 superapps-kai
├── 📂 apps                                   # Aplikasi-aplikasi utama (Microfrontend)
│   ├── 📂 host                               # Host/Container App (Next.js 16)
│   │   ├── 📂 src
│   │   │   ├── 📂 app                          # App Router Next.js 16
│   │   │   │   ├── 📂 (auth)                   # Authentication routes group
│   │   │   │   │   ├── 📂 login
│   │   │   │   │   │   └── 📄 page.tsx
│   │   │   │   │   └── 📂 register
│   │   │   │   │       └── 📄 page.tsx
│   │   │   │   ├── 📂 (dashboard)               # Dashboard routes group (protected)
│   │   │   │   │   ├── 📄 layout.tsx
│   │   │   │   │   ├── 📄 page.tsx              # Dashboard utama
│   │   │   │   │   ├── 📂 penumpang             # Lazy load microfrontend
│   │   │   │   │   │   └── 📄 page.tsx
│   │   │   │   │   ├── 📂 kargo
│   │   │   │   │   │   └── 📄 page.tsx
│   │   │   │   │   ├── 📂 persewaan
│   │   │   │   │   │   └── 📄 page.tsx
│   │   │   │   │   ├── 📂 rollingstock
│   │   │   │   │   │   └── 📄 page.tsx
│   │   │   │   │   ├── 📂 superadmin
│   │   │   │   │   │   ├── 📄 layout.tsx
│   │   │   │   │   │   └── 📂 [menu]            # Dynamic routing untuk menu superadmin
│   │   │   │   │   │       └── 📄 page.tsx
│   │   │   │   │   └── 📂 settings
│   │   │   │   │       └── 📄 page.tsx
│   │   │   │   └── 📂 api                        # API Routes
│   │   │   │       ├── 📂 auth
│   │   │   │       │   └── 📂 [...nextauth]
│   │   │   │       │       └── 📄 route.ts
│   │   │   │       ├── 📂 modules
│   │   │   │       │   └── 📂 [moduleId]
│   │   │   │       │       └── 📂 [...path]
│   │   │   │       │           └── 📄 route.ts  # Proxy ke microfrontend API
│   │   │   │       └── 📂 webhook
│   │   │   │           └── 📂 payment
│   │   │   │               └── 📄 route.ts
│   │   │   ├── 📂 components                      # Shared components untuk host
│   │   │   │   ├── 📂 layout
│   │   │   │   │   ├── 📄 Sidebar.tsx
│   │   │   │   │   ├── 📄 Header.tsx
│   │   │   │   │   └── 📄 Footer.tsx
│   │   │   │   ├── 📂 navigation
│   │   │   │   │   ├── 📄 MenuItem.tsx
│   │   │   │   │   └── 📄 Breadcrumb.tsx
│   │   │   │   └── 📂 ui                          # Wrapper untuk ShadCN/Radix
│   │   │   │       ├── 📄 Button.tsx
│   │   │   │       ├── 📄 Card.tsx
│   │   │   │       ├── 📄 Modal.tsx
│   │   │   │       └── 📄 Table.tsx
│   │   │   ├── 📂 hooks                           # Custom hooks host
│   │   │   │   ├── 📄 useAuth.ts
│   │   │   │   ├── 📄 usePermissions.ts
│   │   │   │   ├── 📄 useModuleLoader.ts          # Hook untuk load microfrontend
│   │   │   │   └── 📄 useMenu.ts
│   │   │   ├── 📂 lib                             # Utilities
│   │   │   │   ├── 📂 auth
│   │   │   │   │   └── 📄 auth.ts
│   │   │   │   ├── 📂 module-federation
│   │   │   │   │   └── 📄 registry.ts              # Module Federation registry
│   │   │   │   └── 📂 utils
│   │   │   │       ├── 📄 cn.ts                    # Tailwind class merger
│   │   │   │       └── 📄 constants.ts
│   │   │   ├── 📂 types                            # Type definitions global
│   │   │   │   ├── 📄 user.ts
│   │   │   │   ├── 📄 module.ts                     # Module interface
│   │   │   │   └── 📄 menu.ts                       # Menu structure types
│   │   │   └── 📂 styles
│   │   │       └── 📄 globals.css
│   │   ├── 📂 public
│   │   │   ├── 📂 images
│   │   │   └── 📂 icons
│   │   ├── 📄 next.config.js                         # Module Federation config
│   │   ├── 📄 tailwind.config.js
│   │   ├── 📄 tsconfig.json
│   │   ├── 📄 package.json
│   │   └── 📄 .env.local
│   │
│   ├── 📂 modul-penumpang                           # Microfrontend - Modul 1
│   │   ├── 📂 src
│   │   │   ├── 📂 app
│   │   │   │   ├── 📄 page.tsx                      # Halaman utama modul
│   │   │   │   ├── 📂 pemesanan
│   │   │   │   │   └── 📄 page.tsx
│   │   │   │   ├── 📂 jadwal
│   │   │   │   │   └── 📄 page.tsx
│   │   │   │   ├── 📂 tiket
│   │   │   │   │   └── 📄 page.tsx
│   │   │   │   ├── 📂 komplain
│   │   │   │   │   └── 📄 page.tsx
│   │   │   │   └── 📂 api
│   │   │   │       └── 📂 [...route]
│   │   │   │           └── 📄 route.ts
│   │   │   ├── 📂 components
│   │   │   │   ├── 📂 features
│   │   │   │   │   ├── 📄 PemesananForm.tsx
│   │   │   │   │   ├── 📄 JadwalTable.tsx
│   │   │   │   │   └── 📄 TiketCard.tsx
│   │   │   │   └── 📂 shared
│   │   │   ├── 📂 hooks
│   │   │   ├── 📂 lib
│   │   │   ├── 📂 types
│   │   │   └── 📂 styles
│   │   ├── 📂 public
│   │   ├── 📄 module.json                            # Module manifest
│   │   ├── 📄 next.config.js                         # Module Federation config
│   │   ├── 📄 package.json
│   │   └── 📄 tsconfig.json
│   │
│   ├── 📂 modul-kargo                                # Microfrontend - Modul 2
│   │   └── 📂 src (struktur serupa modul-penumpang)
│   │       ├── 📂 app
│   │       │   ├── 📂 order
│   │       │   ├── 📂 wms
│   │       │   │   ├── 📂 gudang
│   │       │   │   ├── 📂 inventory
│   │       │   │   └── 📂 operasi
│   │       │   └── 📂 tms
│   │       │       ├── 📂 armada
│   │       │       ├── 📂 rute
│   │       │       └── 📂 tracking
│   │       ├── 📂 components
│   │       │   ├── 📂 wms
│   │       │   └── 📂 tms
│   │       └── ... (dll)
│   │
│   ├── 📂 modul-persewaan                            # Microfrontend - Modul 3
│   │   └── 📂 src
│   │       ├── 📂 app
│   │       │   ├── 📂 aset
│   │       │   ├── 📂 booking
│   │       │   ├── 📂 kontrak
│   │       │   └── 📂 iot
│   │       └── ... (dll)
│   │
│   ├── 📂 modul-rollingstock                         # Microfrontend - Modul 4
│   │   └── 📂 src
│   │       ├── 📂 app
│   │       │   ├── 📂 armada
│   │       │   ├── 📂 perawatan
│   │       │   ├── 📂 predictive
│   │       │   └── 📂 sensor
│   │       └── ... (dll)
│   │
│   └── 📂 modul-superadmin                           # Microfrontend - Superadmin
│       └── 📂 src
│           ├── 📂 app
│           │   ├── 📂 master-data
│           │   ├── 📂 user-management
│           │   ├── 📂 keuangan
│           │   ├── 📂 laporan
│           │   ├── 📂 pengaturan
│           │   └── 📂 integrasi
│           ├── 📂 components
│           │   ├── 📂 data-table                      # Advanced table components
│           │   ├── 📂 form-builder                    # Dynamic form builder
│           │   ├── 📂 menu-builder                    # Visual menu builder
│           │   └── 📂 role-permission                 # Role & permission UI
│           └── ... (dll)
│
├── 📂 packages                                       # Shared packages (monorepo)
│   ├── 📂 ui                                          # Shared UI Components (ShadCN/Radix)
│   │   ├── 📂 src
│   │   │   ├── 📂 components
│   │   │   │   ├── 📂 button
│   │   │   │   │   ├── 📄 Button.tsx
│   │   │   │   │   └── 📄 index.ts
│   │   │   │   ├── 📂 card
│   │   │   │   │   ├── 📄 Card.tsx
│   │   │   │   │   └── 📄 index.ts
│   │   │   │   ├── 📂 dialog
│   │   │   │   │   ├── 📄 Dialog.tsx
│   │   │   │   │   └── 📄 index.ts
│   │   │   │   ├── 📂 form
│   │   │   │   │   ├── 📄 Input.tsx
│   │   │   │   │   ├── 📄 Select.tsx
│   │   │   │   │   ├── 📄 Checkbox.tsx
│   │   │   │   │   └── 📄 index.ts
│   │   │   │   ├── 📂 table
│   │   │   │   │   ├── 📄 Table.tsx
│   │   │   │   │   └── 📄 index.ts
│   │   │   │   ├── 📂 layout
│   │   │   │   │   ├── 📄 Container.tsx
│   │   │   │   │   ├── 📄 Grid.tsx
│   │   │   │   │   └── 📄 index.ts
│   │   │   │   └── 📂 navigation
│   │   │   │       ├── 📄 Tabs.tsx
│   │   │   │       ├── 📄 Menu.tsx
│   │   │   │       └── 📄 index.ts
│   │   │   ├── 📂 hooks
│   │   │   │   ├── 📄 useTheme.ts
│   │   │   │   ├── 📄 useMediaQuery.ts
│   │   │   │   └── 📄 useToast.ts
│   │   │   ├── 📂 utils
│   │   │   │   └── 📄 cn.ts
│   │   │   └── 📄 index.ts                             # Public API
│   │   ├── 📄 package.json
│   │   ├── 📄 tsconfig.json
│   │   └── 📄 tailwind.config.js
│   │
│   ├── 📂 config                                       # Shared configuration
│   │   ├── 📂 eslint
│   │   │   └── 📄 base.js
│   │   ├── 📂 typescript
│   │   │   └── 📄 base.json
│   │   └── 📄 tailwind.config.ts
│   │
│   ├── 📂 types                                        # Shared TypeScript types
│   │   ├── 📂 api
│   │   │   ├── 📄 common.ts
│   │   │   └── 📄 responses.ts
│   │   ├── 📂 models
│   │   │   ├── 📄 user.ts
│   │   │   ├── 📄 penumpang.ts
│   │   │   ├── 📄 kargo.ts
│   │   │   ├── 📄 aset.ts
│   │   │   └── 📄 armada.ts
│   │   ├── 📂 enums
│   │   │   ├── 📄 role.ts
│   │   │   ├── 📄 status.ts
│   │   │   └── 📄 modul.ts
│   │   └── 📄 index.ts
│   │
│   ├── 📂 utils                                        # Shared utilities
│   │   ├── 📂 format
│   │   │   ├── 📄 currency.ts
│   │   │   ├── 📄 date.ts
│   │   │   └── 📄 number.ts
│   │   ├── 📂 validation
│   │   │   ├── 📄 schema.ts
│   │   │   └── 📄 rules.ts
│   │   ├── 📂 helpers
│   │   │   ├── 📄 array.ts
│   │   │   └── 📄 object.ts
│   │   └── 📄 index.ts
│   │
│   ├── 📂 hooks                                        # Shared React hooks
│   │   ├── 📄 useDebounce.ts
│   │   ├── 📄 useLocalStorage.ts
│   │   ├── 📄 usePagination.ts
│   │   ├── 📄 useSort.ts
│   │   └── 📄 useFilter.ts
│   │
│   ├── 📂 api-client                                   # Shared API client
│   │   ├── 📂 core
│   │   │   ├── 📄 client.ts
│   │   │   ├── 📄 interceptors.ts
│   │   │   └── 📄 errors.ts
│   │   ├── 📂 endpoints
│   │   │   ├── 📄 auth.ts
│   │   │   ├── 📄 penumpang.ts
│   │   │   ├── 📄 kargo.ts
│   │   │   ├── 📄 persewaan.ts
│   │   │   └── 📄 rollingstock.ts
│   │   └── 📄 index.ts
│   │
│   ├── 📂 database                                     # Shared database layer
│   │   ├── 📂 prisma
│   │   │   ├── 📄 schema.prisma                        # Prisma schema utama
│   │   │   └── 📄 migrations
│   │   ├── 📂 repositories
│   │   │   ├── 📄 user.repository.ts
│   │   │   ├── 📄 penumpang.repository.ts
│   │   │   └── ... (dll)
│   │   └── 📄 index.ts
│   │
│   └── 📂 module-loader                                # Module loader system
│       ├── 📂 core
│       │   ├── 📄 registry.ts                           # Module registry
│       │   ├── 📄 loader.ts                             # Dynamic module loader
│       │   └── 📄 resolver.ts                           # Module dependency resolver
│       ├── 📂 plugins
│       │   ├── 📄 plugin.interface.ts                    # Plugin interface
│       │   ├── 📄 plugin-manager.ts                       # Plugin manager
│       │   └── 📂 built-in
│       │       ├── 📄 auth.plugin.ts
│       │       └── 📄 menu.plugin.ts
│       └── 📄 index.ts
│
├── 📂 plugins                                           # Plugin system
│   ├── 📂 plugin-analytics                              # Plugin - Analytics
│   │   ├── 📂 src
│   │   │   ├── 📄 index.ts
│   │   │   ├── 📄 plugin.ts
│   │   │   └── 📂 components
│   │   │       ├── 📄 ChartWidget.tsx
│   │   │       └── 📄 DashboardWidget.tsx
│   │   ├── 📄 plugin.json                               # Plugin manifest
│   │   └── 📄 package.json
│   │
│   ├── 📂 plugin-reporting                              # Plugin - Advanced Reporting
│   │   └── 📂 src
│   │       ├── 📄 index.ts
│   │       ├── 📄 plugin.ts
│   │       └── 📂 components
│   │           ├── 📄 ReportBuilder.tsx
│   │           └── 📄 ExportButton.tsx
│   │
│   ├── 📂 plugin-export                                 # Plugin - Data Export
│   │   └── 📂 src
│   │       ├── 📄 index.ts
│   │       ├── 📄 plugin.ts
│   │       └── 📂 services
│   │           ├── 📄 excel.service.ts
│   │           ├── 📄 pdf.service.ts
│   │           └── 📄 csv.service.ts
│   │
│   ├── 📂 plugin-notification                           # Plugin - Notification
│   │   └── 📂 src
│   │       ├── 📄 index.ts
│   │       ├── 📄 plugin.ts
│   │       └── 📂 channels
│   │           ├── 📄 email.channel.ts
│   │           ├── 📄 whatsapp.channel.ts
│   │           └── 📄 push.channel.ts
│   │
│   ├── 📂 plugin-payment                                # Plugin - Payment Gateway
│   │   └── 📂 src
│   │       ├── 📄 index.ts
│   │       ├── 📄 plugin.ts
│   │       └── 📂 gateways
│   │           ├── 📄 midtrans.gateway.ts
│   │           ├── 📄 xendit.gateway.ts
│   │           └── 📄 dummy.gateway.ts
│   │
│   └── 📂 plugin-custom-module                          # Template untuk custom module
│       ├── 📂 src
│       │   ├── 📄 index.ts
│       │   ├── 📄 plugin.ts
│       │   └── 📂 components
│       └── 📄 plugin.json
│
├── 📂 tooling                                           # Development tools
│   ├── 📂 eslint
│   │   ├── 📄 index.js
│   │   └── 📄 package.json
│   ├── 📂 prettier
│   │   ├── 📄 index.js
│   │   └── 📄 package.json
│   └── 📂 typescript
│       └── 📄 base.json
│
├── 📂 documentation                                     # Documentation
│   ├── 📂 api
│   │   └── 📄 openapi.yaml
│   ├── 📂 architecture
│   │   ├── 📄 microfrontend.md
│   │   ├── 📄 plugin-system.md
│   │   └── 📄 module-federation.md
│   └── 📂 development
│       ├── 📄 getting-started.md
│       └── 📄 contributing.md
│
├── 📄 turbo.json                                         # Turborepo configuration
├── 📄 package.json                                       # Root package.json
├── 📄 pnpm-workspace.yaml                               # PNPM workspace (recommended)
├── 📄 .gitignore
├── 📄 .env.example
├── 📄 README.md
└── 📄 docker-compose.yml                                # Development environment
```

---

## 📋 PENJELASAN STRUKTUR

### 1. **Apps Layer (Microfrontend)**

| Folder | Deskripsi |
| :--- | :--- |
| **host** | Aplikasi utama/container yang menampung semua microfrontend. Bertanggung jawab untuk autentikasi, layout utama, dan dynamic module loading. |
| **modul-penumpang** | Microfrontend untuk Modul 1 - Penumpang. Dapat di-deploy secara independen. |
| **modul-kargo** | Microfrontend untuk Modul 2 - Kargo + WMS + TMS. |
| **modul-persewaan** | Microfrontend untuk Modul 3 - Persewaan Aset. |
| **modul-rollingstock** | Microfrontend untuk Modul 4 - Rollingstock Management. |
| **modul-superadmin** | Microfrontend khusus untuk Superadmin dengan menu lengkap. |

### 2. **Packages Layer (Shared)**

| Folder | Deskripsi |
| :--- | :--- |
| **ui** | Shared UI components berbasis ShadCN/Radix yang digunakan di semua modul. |
| **config** | Shared configuration (ESLint, TypeScript, Tailwind). |
| **types** | Shared TypeScript types dan interfaces. |
| **utils** | Shared utility functions. |
| **hooks** | Shared React hooks. |
| **api-client** | Shared API client untuk komunikasi dengan backend. |
| **database** | Shared database layer dengan Prisma ORM. |
| **module-loader** | Core system untuk dynamic module loading dan plugin management. |

### 3. **Plugins Layer**

Folder **plugins** berisi plugin-plugin yang dapat diaktifkan/dinonaktifkan secara dinamis:

- **plugin-analytics**: Menambahkan fitur analytics dan tracking.
- **plugin-reporting**: Menambahkan advanced report builder.
- **plugin-export**: Menambahkan fitur export ke Excel/PDF/CSV.
- **plugin-notification**: Menambahkan multi-channel notification.
- **plugin-payment**: Menambahkan integrasi payment gateway.
- **plugin-custom-module**: Template untuk membuat plugin/module custom.

### 4. **Struktur per Modul/Plugin (Standar)**

Setiap modul/plugin mengikuti struktur standar:

```
📂 modul-nama
├── 📂 src
│   ├── 📂 app                          # Next.js App Router
│   │   ├── 📄 page.tsx                  # Halaman utama modul
│   │   └── 📂 [feature]                 # Fitur-fitur dalam modul
│   ├── 📂 components                     # Komponen spesifik modul
│   │   ├── 📂 features
│   │   └── 📂 shared
│   ├── 📂 hooks                          # Custom hooks modul
│   ├── 📂 lib                            # Utilities modul
│   ├── 📂 types                           # Type definitions modul
│   └── 📂 styles                          # CSS Modules / Tailwind
├── 📄 module.json                         # Module manifest
├── 📄 next.config.js                      # Module Federation config
├── 📄 package.json
└── 📄 tsconfig.json
```

---

## 📄 FILE KONFIGURASI PENTING

### 1. **Root `turbo.json`**

```json
{
  "$schema": "https://turbo.build/schema.json",
  "globalDependencies": ["**/.env.*local"],
  "pipeline": {
    "build": {
      "dependsOn": ["^build"],
      "outputs": [".next/**", "dist/**"]
    },
    "dev": {
      "cache": false,
      "persistent": true
    },
    "lint": {
      "dependsOn": ["^lint"]
    },
    "test": {
      "dependsOn": ["build"],
      "outputs": []
    }
  }
}
```

### 2. **Root `pnpm-workspace.yaml`**

```yaml
packages:
  - "apps/*"
  - "packages/*"
  - "plugins/*"
  - "tooling/*"
```

### 3. **Host `next.config.js` (Module Federation)**

```javascript
const NextFederationPlugin = require("@module-federation/nextjs-mf");

module.exports = {
  webpack(config, options) {
    const { isServer } = options;
    config.plugins.push(
      new NextFederationPlugin({
        name: "host",
        filename: "static/chunks/remoteEntry.js",
        exposes: {
          "./layout": "./src/components/layout/Sidebar.tsx",
          "./auth": "./src/lib/auth/auth.ts",
        },
        remotes: {
          penumpang: `penumpang@http://localhost:3001/_next/static/${
            isServer ? "ssr" : "chunks"
          }/remoteEntry.js`,
          kargo: `kargo@http://localhost:3002/_next/static/${
            isServer ? "ssr" : "chunks"
          }/remoteEntry.js`,
          persewaan: `persewaan@http://localhost:3003/_next/static/${
            isServer ? "ssr" : "chunks"
          }/remoteEntry.js`,
          rollingstock: `rollingstock@http://localhost:3004/_next/static/${
            isServer ? "ssr" : "chunks"
          }/remoteEntry.js`,
          superadmin: `superadmin@http://localhost:3005/_next/static/${
            isServer ? "ssr" : "chunks"
          }/remoteEntry.js`,
        },
        shared: {
          react: {
            singleton: true,
            requiredVersion: false,
          },
          "react-dom": {
            singleton: true,
            requiredVersion: false,
          },
          "next/link": {
            singleton: true,
          },
          "next/router": {
            singleton: true,
          },
        },
      })
    );
    return config;
  },
};
```

### 4. **Modul `module.json` (Manifest)**

```json
{
  "id": "modul-penumpang",
  "name": "Modul Penumpang",
  "version": "1.0.0",
  "description": "Manajemen tiket, jadwal, dan layanan penumpang",
  "author": "KAI",
  "license": "MIT",
  "entry": "./src/index.ts",
  "dependencies": {
    "ui": "^1.0.0",
    "api-client": "^1.0.0"
  },
  "permissions": [
    "view:tiket",
    "create:tiket",
    "edit:tiket",
    "delete:tiket"
  ],
  "menu": [
    {
      "key": "penumpang.dashboard",
      "label": "Dashboard",
      "icon": "LayoutDashboard",
      "path": "/penumpang"
    },
    {
      "key": "penumpang.pemesanan",
      "label": "Pemesanan Tiket",
      "icon": "Ticket",
      "path": "/penumpang/pemesanan"
    },
    {
      "key": "penumpang.jadwal",
      "label": "Jadwal Kereta",
      "icon": "Calendar",
      "path": "/penumpang/jadwal"
    },
    {
      "key": "penumpang.komplain",
      "label": "Manajemen Komplain",
      "icon": "MessageCircle",
      "path": "/penumpang/komplain"
    }
  ],
  "settings": [
    {
      "key": "penumpang.kapasitas",
      "label": "Kapasitas Maksimal",
      "type": "number",
      "default": 100
    }
  ]
}
```

### 5. **Plugin Interface (`plugin.interface.ts`)**

```typescript
export interface Plugin {
  /** Unique plugin ID */
  id: string;
  
  /** Plugin name */
  name: string;
  
  /** Plugin version */
  version: string;
  
  /** Plugin description */
  description?: string;
  
  /** Initialize plugin */
  init: (context: PluginContext) => Promise<void>;
  
  /** Cleanup plugin */
  cleanup?: () => Promise<void>;
  
  /** Plugin components to register */
  components?: Record<string, React.ComponentType<any>>;
  
  /** Plugin routes to add */
  routes?: PluginRoute[];
  
  /** Plugin menu items to add */
  menuItems?: PluginMenuItem[];
  
  /** Plugin hooks/events */
  hooks?: PluginHooks;
}

export interface PluginContext {
  /** API client */
  api: ApiClient;
  
  /** Router */
  router: any;
  
  /** Current user */
  user: User;
  
  /** Permission checker */
  can: (permission: string) => boolean;
  
  /** Register component */
  registerComponent: (name: string, component: React.ComponentType) => void;
  
  /** Add menu item */
  addMenuItem: (menuItem: PluginMenuItem) => void;
  
  /** Add route */
  addRoute: (route: PluginRoute) => void;
}

export interface PluginMenuItem {
  key: string;
  label: string;
  icon?: string;
  path: string;
  parent?: string;
  permissions?: string[];
  order?: number;
}

export interface PluginRoute {
  path: string;
  component: React.ComponentType;
  exact?: boolean;
  permissions?: string[];
  layout?: "default" | "blank" | "none";
}

export interface PluginHooks {
  onBeforeRender?: () => Promise<void>;
  onAfterRender?: () => void;
  onDataLoad?: (data: any) => any;
  onError?: (error: Error) => void;
}
```

### 6. **Module Loader (`loader.ts`)**

```typescript
import { Plugin, PluginContext, PluginMenuItem, PluginRoute } from "./plugin.interface";

class ModuleLoader {
  private plugins: Map<string, Plugin> = new Map();
  private components: Map<string, React.ComponentType> = new Map();
  private menuItems: PluginMenuItem[] = [];
  private routes: PluginRoute[] = [];

  async loadModule(moduleId: string, manifestUrl: string): Promise<void> {
    try {
      // Load manifest
      const manifest = await fetch(manifestUrl).then(res => res.json());
      
      // Load plugin entry
      const module = await import(/* webpackIgnore: true */ manifest.entry);
      const plugin = module.default as Plugin;
      
      // Validate plugin
      if (!plugin.id || !plugin.name || !plugin.init) {
        throw new Error(`Invalid plugin: ${moduleId}`);
      }
      
      // Register plugin
      this.plugins.set(plugin.id, plugin);
      
      console.log(`Module loaded: ${plugin.name} v${plugin.version}`);
    } catch (error) {
      console.error(`Failed to load module ${moduleId}:`, error);
    }
  }

  async initializePlugins(context: PluginContext): Promise<void> {
    for (const plugin of this.plugins.values()) {
      try {
        await plugin.init(context);
        
        // Register components
        if (plugin.components) {
          Object.entries(plugin.components).forEach(([name, component]) => {
            this.components.set(`${plugin.id}.${name}`, component);
          });
        }
        
        // Add menu items
        if (plugin.menuItems) {
          this.menuItems.push(...plugin.menuItems);
        }
        
        // Add routes
        if (plugin.routes) {
          this.routes.push(...plugin.routes);
        }
        
        console.log(`Plugin initialized: ${plugin.name}`);
      } catch (error) {
        console.error(`Failed to initialize plugin ${plugin.id}:`, error);
      }
    }
    
    // Sort menu items by order
    this.menuItems.sort((a, b) => (a.order || 999) - (b.order || 999));
  }

  getComponent(componentId: string): React.ComponentType | undefined {
    return this.components.get(componentId);
  }

  getMenuItems(parent?: string): PluginMenuItem[] {
    if (parent) {
      return this.menuItems.filter(item => item.parent === parent);
    }
    return this.menuItems.filter(item => !item.parent);
  }

  getRoutes(): PluginRoute[] {
    return this.routes;
  }
}

export const moduleLoader = new ModuleLoader();
```

---

## 🚀 COMMANDS YANG DIDUKUNG

```bash
# Install dependencies
pnpm install

# Development (jalankan semua apps)
pnpm dev

# Development (app tertentu)
pnpm dev --filter=host
pnpm dev --filter=modul-penumpang

# Build semua
pnpm build

# Build app tertentu
pnpm build --filter=host

# Lint semua
pnpm lint

# Test semua
pnpm test

# Add dependency ke package tertentu
pnpm add lodash --filter=@kai/ui

# Clean cache
pnpm clean
```

---

## 🔧 ENVIRONMENT VARIABLES

```env
# Database
DATABASE_URL="postgresql://..."

# Authentication
NEXTAUTH_SECRET="..."
NEXTAUTH_URL="http://localhost:3000"

# API
API_BASE_URL="http://localhost:4000"

# Payment Gateway
MIDTRANS_SERVER_KEY="..."
MIDTRANS_CLIENT_KEY="..."

# External Services
GOOGLE_MAPS_API_KEY="..."
CRM_API_URL="..."
SCM_API_URL="..."

# Module Federation
NEXT_PUBLIC_HOST_URL="http://localhost:3000"
NEXT_PUBLIC_MODUL_PENUMPANG_URL="http://localhost:3001"
NEXT_PUBLIC_MODUL_KARGO_URL="http://localhost:3002"
NEXT_PUBLIC_MODUL_PERSEWAAN_URL="http://localhost:3003"
NEXT_PUBLIC_MODUL_ROLLINGSTOCK_URL="http://localhost:3004"
NEXT_PUBLIC_MODUL_SUPERADMIN_URL
