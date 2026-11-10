# Sistem Informasi Pendeteksi dan Pencegahan Kebakaran Hutan di Perkebunan Raya Desa Kauditan Berbasis Web

Sistem informasi berbasis web untuk Perkebunan Raya Desa Kauditan II yang membantu masyarakat/petani, perangkat desa (Kepala Jaga), dan petugas lapangan memantau titik panas (hotspot), mengetahui status risiko kebakaran (Aman, Waspada, Siaga, Awas), melapor, serta berkoordinasi agar kebakaran terdeteksi lebih dini dan lokasinya presisi.

![Halaman utama](docs/screenshots/01_halaman_utama.png)

| | |
|---|---|
| **Mata kuliah** | System Analysis and Design — Fakultas Ilmu Komputer, Universitas Klabat |
| **Kelompok** | Korektor |
| **Objek / studi kasus** | Perkebunan Raya Desa Kauditan II, Minahasa Utara |
| **Model SDLC** | Waterfall |
| **Dokumen SRS** | [docs/SRS.pdf](docs/SRS.pdf) |
| **Prototipe UI** | [https://www.figma.com/proto/4iZq7M7G2g4CjL2WFVjUvg/UI-UX-Kauditan-siaga-versi-beta-1.0?node-id=0-1&t=RLLOmOddJhigZiRx-1](https://www.figma.com/proto/4iZq7M7G2g4CjL2WFVjUvg/UI-UX-Kauditan-siaga-versi-beta-1.0?node-id=0-1&t=RLLOmOddJhigZiRx-1) |

## Anggota Kelompok

| No | Nama | NIM | Peran | Kontribusi utama |
|----|------|-----|-------|------------------|
| 1 | Goni, Gabriel Richard | 105012510018 | Project Manager | Mengoordinasikan tim dan jadwal, mengelola repositori, menjaga alur kerja SDLC, draf SRS Bagian 1–2 |
| 2 | Rares, Josua Afriyan | 105022510105 | System Analyst | Elisitasi kebutuhan, penyusunan dokumen SRS, matriks keterlacakan, use case diagram dan description, activity diagram (Bagian 6) |
| 3 | Reo, Marchiando Stephen | 105022510086 | UI/UX Designer & System Designer | Prototipe antarmuka Figma, pemodelan UML (use case, activity, sequence, class diagram) |
| 4 | Sompie, Yehuda Miracle | 105022510032 | Database & Backend Specialist | ERD, kamus data, arsitektur basis data, API backend (Bagian 7–9) |
| 5 | Loing, Clifford Justine | 105012510113 | Lead Developer | Antarmuka front-end, integrasi logika bisnis, repositori kode, implementasi dan pengujian black-box (Bagian 10) |

## Latar Belakang

- **Masalah:** Deteksi kebakaran hutan/lahan terlambat dan lokasi kejadian sulit dipastikan secara presisi, sehingga api sering sudah membesar ketika diketahui. Petugas diharapkan tiba di lokasi kurang dari 15 menit, tetapi tidak ada notifikasi real-time.
- **Kondisi saat ini:** Pemantauan dilakukan lewat patroli langsung dan himbauan lisan. Pelaporan lewat telepon/WhatsApp tanpa koordinat presisi. Tidak ada basis data terpusat, riwayat kejadian hanya tersimpan di percakapan WhatsApp atau diingat secara lisan. Data satelit (NASA FIRMS) dan cuaca (BMKG) belum dimanfaatkan.
- **Tujuan sistem:**
  1. Pemantauan titik panas (hotspot) berbasis web dengan peta dan koordinat presisi.
  2. Pengkategorian status risiko kawasan (Aman, Waspada, Siaga, Awas) otomatis dari data satelit dan cuaca.
  3. Notifikasi peringatan dini (early warning) yang cepat kepada perangkat desa dan petugas lapangan.
  4. Kemudahan koordinasi penanganan darurat: pelaporan warga, verifikasi, dan ekspor data ke instansi terkait.
  5. Panduan tindakan pencegahan mandiri bagi warga dan petani (sekat pemisah lahan, persiapan air).
- **Pengguna (aktor):**
  - **Masyarakat / Petani:** warga dan pemilik lahan yang memantau risiko lahan dan melapor.
  - **Operator / Kepala Jaga:** perangkat desa yang memantau dashboard, memverifikasi laporan, dan mengelola status penanganan.
  - **Petugas Lapangan:** penjaga kebun yang menerima notifikasi dan mengonfirmasi titik api di lokasi.
  - **Admin Sistem:** personel teknis pengelola akun dan konfigurasi sistem.
  - **Instansi Terkait (BPBD/Damkar):** pihak eksternal penerima data rujukan hasil ekspor, tidak login langsung.
  - **Sistem (Penjadwal):** aktor non-manusia yang mengambil data NASA FIRMS dan BMKG secara berkala.

## Fitur Utama

| No | Fitur | Aktor | Use case | Kebutuhan |
|----|-------|-------|----------|-----------|
| 1 | Login / Autentikasi (RBAC) | Pengguna, Perangkat Desa | UC-11 | FR-08 |
| 2 | Memantau peta spasial dan hotspot | Pengguna, Perangkat Desa | UC-01 | FR-01 |
| 3 | Melihat status risiko (indikator warna) | Pengguna, Perangkat Desa | UC-02 | FR-02 |
| 4 | Panduan mitigasi mandiri | Pengguna | UC-03 | FR-04 |
| 5 | Mengirim laporan kejadian dan melampirkan foto lokasi | Pengguna | UC-04, UC-10 | FR-05 |
| 6 | Verifikasi laporan warga | Perangkat Desa | UC-05 | FR-06 |
| 7 | Ubah status bahaya | Perangkat Desa | UC-06 | FR-02, FR-06 |
| 8 | Notifikasi early warning | Sistem (dipicu UC-06) | UC-07 | FR-03 |
| 9 | Ekspor data rujukan (PDF/Excel) | Perangkat Desa | UC-08 | FR-07 |
| 10 | Kelola akun pengguna | Perangkat Desa (Administrator/Operator) | UC-09 | FR-08 |

## Screenshot

**[UC-01] Memantau Peta Spasial**

![UC-01](docs/screenshots/02_uc01.png)

**[UC-02] Melihat Status Risiko**

![UC-02](docs/screenshots/03_uc02.png)

**[UC-03] Baca Panduan Mitigasi**

![UC-03](docs/screenshots/04_uc03.png)

**[UC-04] Mengirim Laporan Kejadian (termasuk UC-10 Lampirkan Foto Lokasi)**

![UC-04](docs/screenshots/05_uc04.png)

**[UC-05] Verifikasi Laporan**

![UC-05](docs/screenshots/06_uc05.png)

**[UC-06] Ubah Status Bahaya**

![UC-06](docs/screenshots/07_uc06.png)

**[UC-07] Notifikasi Early Warning**

![UC-07](docs/screenshots/08_uc07.png)

**[UC-08] Mengekspor Data Rujukan**

![UC-08](docs/screenshots/09_uc08.png)

**[UC-09] Kelola Akun Pengguna**

![UC-09](docs/screenshots/10_uc09.png)

**[UC-11] Login / Autentikasi**

![UC-11](docs/screenshots/11_uc11.png)

**Validasi input**

![Pesan validasi](docs/screenshots/12_validasi.png)

## Teknologi

| Lapisan | Teknologi | Versi |
|---------|-----------|-------|
| Front-end | React.js, Tailwind CSS, Leaflet.js / Mapbox GL | — |
| Back-end | Node.js (Express.js), REST API, arsitektur Microservices (Auth, Hotspot, Weather, Notification, Incident) | — |
| Database | PostgreSQL + PostGIS, AWS S3 Bucket (object storage foto bukti) | — |
| Hosting / lingkungan uji | Docker, Nginx (reverse proxy / API Gateway), Cloudflare CDN & Load Balancer | — |
| Layanan eksternal | NASA FIRMS API (MODIS/VIIRS), API cuaca BMKG, OpenStreetMap | — |
| Tools pemodelan | Visual Paradigm / Draw.io | — |
| Prototipe UI | Figma | — |
| Pengujian dan CI/CD | Postman, GitHub Actions | — |

## Kebutuhan Sistem

- Node.js dan npm
- PostgreSQL dengan ekstensi PostGIS
- Docker dan Nginx (untuk deployment)
- Git
- Browser modern (sistem berupa web responsif untuk ponsel, tablet, dan PC) dengan koneksi internet minimal 2 Mbps

## Instalasi dan Menjalankan Aplikasi

> Nama repository, folder, port, dan nama database di bawah ini masih berupa placeholder karena belum tercantum di SRS (Bagian 10.2 masih `[https://github.com/...]`). Sesuaikan dengan repository sebenarnya.

1. Clone repository:

   ```bash
   git clone [https://github.com/akun/nama-repo.git]
   cd [nama-repo]
   ```

2. Pasang dependensi:

   ```bash
   npm install
   ```

3. Siapkan konfigurasi. Salin file contoh lalu sesuaikan isinya (koneksi database, API key NASA FIRMS, interval sinkronisasi, kredensial AWS S3, secret JWT):

   ```bash
   cp .env.example .env
   ```

4. Siapkan database (PostgreSQL + PostGIS):

   ```bash
   [buat database "nama_db", aktifkan ekstensi PostGIS, lalu jalankan migrasi dan seed]
   ```

5. Jalankan aplikasi:

   ```bash
   npm run dev
   ```

6. Buka [http://localhost:xxxx] di browser.

### Akun uji

| Aktor | Username / email | Password |
|-------|------------------|----------|
| [Masyarakat / Petani] | [email dari data seed] | [password uji] |
| [Operator / Perangkat Desa] | [email dari data seed] | [password uji] |
| [Admin Sistem] | [email dari data seed] | [password uji] |

## Struktur Folder

Struktur mengikuti class diagram (SRS 7.2), arsitektur microservices (SRS 10.1), dan matriks keterlacakan (SRS 10.3). Sesuaikan dengan struktur repository sebenarnya.

```text
[nama-repo]/
├── frontend/               # React.js + Tailwind CSS + Leaflet.js
│   └── src/                # tampilan sesuai prototipe UI L-01 s.d. L-08 (SRS Bagian 9)
├── backend/                # Node.js (Express.js), REST API
│   ├── models/             # kelas entity sesuai class diagram (SRS 7.2)
│   ├── controllers/        # MapController, MitigationGuideController, IncidentVerificationController, UserController
│   └── services/           # HotspotService, RiskEngineService, NotificationService, IncidentReportService, ExportReportService, AuthService
├── database/               # skema/migrasi dan data contoh sesuai model data (SRS Bagian 8)
├── docs/
│   ├── SRS.pdf
│   ├── diagrams/           # file sumber diagram UML (.drawio, dsb.)
│   └── screenshots/
├── [.env.example]
└── README.md
```

## Rancangan Sistem

Ringkasan rancangan; detail lengkap ada di dokumen SRS.

| Artefak | Lokasi |
|---------|--------|
| Kebutuhan fungsional dan non-fungsional | SRS Bagian 5 |
| Use case diagram dan description | SRS Bagian 6 · `docs/diagrams/[file]` |
| Activity dan sequence diagram | SRS Bagian 6.4 dan 7.1 |
| Class diagram | SRS Bagian 7.2 |
| Model data (ERD) dan kamus data | SRS Bagian 8 |
| Prototipe UI | [Figma](https://www.figma.com/proto/4iZq7M7G2g4CjL2WFVjUvg/UI-UX-Kauditan-siaga-versi-beta-1.0?node-id=0-1&t=RLLOmOddJhigZiRx-1) |

![Class diagram](docs/diagrams/class_diagram.png)

## Pengujian

Ringkasan: **10 kasus uji, 10 lulus**. Daftar lengkap ada di SRS 10.4.

| ID | Use case | Skenario | Hasil diharapkan | Status |
|----|----------|----------|------------------|--------|
| TC-01 | UC-11 | Login dengan data benar (email & password terdaftar) | Berhasil masuk ke dashboard utama | Lulus |
| TC-02 | UC-11 | Login dengan password salah (email benar, password salah) | Tampil pesan error "Password salah" | Lulus |
| TC-03 | UC-01 | Menampilkan peta spasial & titik hotspot (buka halaman dashboard peta) | Peta memuat batas kawasan & penanda hotspot | Lulus |
| TC-04 | UC-02 | Kalkulasi otomatis status risiko bahaya (data suhu & titik panas diperbarui) | Status kawasan berubah (Aman/Waspada/Siaga/Awas) | Lulus |
| TC-05 | UC-07 | Penerimaan notifikasi peringatan dini (pemicu status Awas terdeteksi) | Notifikasi alert terkirim real-time ke pengelola | Lulus |
| TC-06 | UC-03 | Akses modul panduan mitigasi mandiri (klik menu panduan mitigasi) | Tampil rekomendasi teknik sekat lahan/air | Lulus |
| TC-07 | UC-04, UC-10 | Pengiriman formulir laporan warga (input deskripsi, lokasi & foto bukti) | Laporan tersimpan & foto terunggah ke S3 | Lulus |
| TC-08 | UC-05 | Verifikasi laporan kejadian oleh Perangkat Desa (pilih laporan & ubah status ke "Proses") | Status insiden berhasil diperbarui di database | Lulus |
| TC-09 | UC-08 | Ekspor rekapitulasi data kejadian (klik tombol ekspor PDF/Excel) | File laporan terunduh sesuai format | Lulus |
| TC-10 | UC-11 | Pengujian hak akses pengguna / RBAC (akun Warga mencoba akses menu Verifikasi) | Akses ditolak & diarahkan kembali ke dashboard | Lulus |

Bug yang ditemukan dan sudah diperbaiki: keterlambatan notifikasi real-time saat sinyal lemah (diperbaiki dengan mengoptimalkan payload Webhook) dan format penulisan koordinat spasial pada layar peta.

## Keterbatasan dan Pengembangan Berikutnya

- Notifikasi WhatsApp/SMS Gateway berbayar tidak dipakai; notifikasi disimulasikan lewat pop-up/panel notifikasi di antarmuka web.
- Pengiriman laporan langsung ke sistem internal BPBD/Damkar tidak tersedia; hanya ekspor data PDF/Excel untuk dirujuk.
- Sistem hanya memakai data hotspot dari API pihak ketiga (NASA FIRMS); tidak memproses citra satelit mentah. Akurasi hotspot dibatasi resolusi dan jadwal lintasan satelit, serta ketersediaan API NASA FIRMS dan BMKG. Jika API tidak tersedia, sistem menampilkan data terakhir yang berhasil diambil beserta waktu pembaruannya.
- Tidak ada sensor IoT, perangkat pemantau fisik, atau otomatisasi alat pemadam di lapangan.
- Bukan aplikasi mobile native; sistem diakses lewat peramban web responsif.
- Status bahaya resmi hanya boleh ditetapkan oleh perangkat desa, dan sistem tidak menggantikan prosedur penanganan resmi.
- Operasional membutuhkan pelatihan singkat, SOP tertulis, serta penunjukan operator dan pemelihara sistem di desa setelah masa proyek berakhir.

## Penggunaan AI dan Referensi

| Alat AI | Dipakai untuk | Yang diperiksa atau diubah dari hasilnya |
|---------|---------------|------------------------------------------|
| [ChatGPT / Claude / Copilot / …] | [isi sesuai Lampiran B SRS] | [isi sesuai Lampiran B SRS] |

Referensi:

1. IEEE Std 830-1998, *IEEE Recommended Practice for Software Requirements Specifications*, IEEE Computer Society, 1998.
2. Badan Meteorologi, Klimatologi, dan Geofisika (BMKG). *Dokumentasi API Terbuka Data Cuaca Indonesia*.
3. National Aeronautics and Space Administration (NASA). *Fire Information for Resource Management System (FIRMS) API Documentation*.
4. Pressman, R. S., & Maxim, B. R. (2019). *Software Engineering: A Practitioner's Approach* (9th ed.). McGraw-Hill Education.
5. Pemerintah Desa Kauditan II. (2026). *Hasil Wawancara Pengumpulan Kebutuhan Sistem (Requirements Gathering) Pemantauan Kebakaran Perkebunan Raya Kauditan*. Minahasa Utara.
6. Leaflet API Reference. Open-Source JavaScript Library for Interactive Maps.
