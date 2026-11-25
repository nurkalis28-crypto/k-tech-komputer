# Spesifikasi Sistem — Pesona Explore Aceh

**Versi Dokumen:** 1.0 (MVP Prototype Specification)  
**Peran Penyusun:** System Analyst & Software Engineer  
**Jenis Aplikasi:** Aplikasi Web Pariwisata Halal (*Halal Tourism Editorial & Trip Planner*)  
**Target Stack Implementasi:** Vite + Vanilla JavaScript (ES6+), HTML5, CSS3, Inline SVG, `localStorage` (tanpa backend dan tanpa autentikasi/login palsu)

---

## 1. Tujuan (Objectives)

**Pesona Explore Aceh** adalah aplikasi web pariwisata halal yang dirancang untuk memudahkan wisatawan menemukan destinasi wisata, kuliner halal dan produk UMKM lokal, akomodasi ramah Muslim, serta menyusun rencana perjalanan (*itinerary*) di wilayah Provinsi Aceh secara transparan dan terstruktur.

Tujuan utama pengembangan MVP ini meliputi:
1. **Sentralisasi Informasi Pariwisata Halal Aceh**: Menyajikan katalog terkurasi untuk wilayah Banda Aceh, Sabang, Aceh Besar, Aceh Tengah, dan Bener Meriah dalam satu antarmuka editorial yang mudah diakses di desktop maupun smartphone.
2. **Transparansi Informasi Ibadah & Status Halal**: Menyediakan rincian fasilitas ibadah pada setiap destinasi, memisahkan secara tegas antara **Fasilitas Ramah Muslim** (kesiapan layanan hospitality) dengan **Status Sertifikasi Halal Resmi** (klaim sertifikat dengan sumber verifikasi), serta memberi penanda jelas untuk informasi nyata yang belum terverifikasi lapangan.
3. **Perencanaan Perjalanan Mandiri**: Membantu wisatawan menyusun *itinerary* 1–5 hari, menghitung simulasi estimasi anggaran perjalanan secara *real-time*, dan mendapatkan rekomendasi paket wisata berbasis aturan (*rule-based filtering*).
4. **Pemberdayaan UMKM & Pengelola Informasi**: Menyediakan fitur kontak WhatsApp mode demo untuk pelaku UMKM/akomodasi serta dashboard demo CRUD agar pengelola informasi dapat mensimulasikan pengelolaan data destinasi, kuliner, akomodasi, dan paket wisata secara langsung di browser menggunakan `localStorage`.

---

## 2. Pengguna (Target Users & Personas)

| Segmen Pengguna | Kebutuhan Utama | Fitur Kunci yang Digunakan |
| :--- | :--- | :--- |
| **Wisatawan Domestik** | Mencari referensi wisata religi, bahari, dataran tinggi, kuliner halal terpercaya, dan estimasi biaya liburan keluarga. | Katalog destinasi, filter wilayah/kategori, kalkulator anggaran, itinerary planner 1–5 hari, tautan WhatsApp demo. |
| **Wisatawan Mancanegara (Muslim & Umum)** | Memahami konteks budaya Aceh dalam bahasa Inggris, lokasi fasilitas shalat/wudhu, serta akomodasi ramah Muslim. | Toggle bahasa `ID / EN`, peta ilustratif SVG & tautan Google Maps, detail fasilitas ibadah & ramah Muslim. |
| **Pelaku UMKM Pariwisata & Kuliner** | Menampilkan produk kuliner/oleh-oleh lokal beserta status verifikasi halal dan kanal kontak simulasi bagi wisatawan. | Katalog kuliner & UMKM, badge/label status sertifikasi halal & sumber verifikasi, tombol kontak WhatsApp demo. |
| **Pengelola Informasi Destinasi Wisata** | Mengelola pembaruan data destinasi, kuliner, akomodasi, dan paket wisata secara cepat dalam sesi demonstrasi. | Dashboard demo CRUD (Tambah, Ubah, Hapus, Reset Data Awal) yang tersimpan pada `localStorage`. |

---

## 3. Daftar Fitur (MVP Features)

### A. Eksplorasi & Katalog
1. **Landing Page Editorial**: Ringkasan nilai pariwisata halal Aceh, sorotan destinasi unggulan, pengenalan cakupan 5 wilayah, dan navigasi cepat ke seluruh modul.
2. **Katalog Minimal 12 Destinasi Wisata Contoh**: Dilengkapi 15 data contoh representatif mencakup wilayah **Banda Aceh, Sabang, Aceh Besar, Aceh Tengah, dan Bener Meriah** serta kategori **Religi, Alam, Bahari, Sejarah, Budaya, dan Kuliner**.
3. **Detail Destinasi Lengkap**: Menampilkan foto/ilustrasi, deskripsi (dwibahasa), alamat, tautan Google Maps tanpa API key, estimasi biaya (simulasi), fasilitas umum, **fasilitas ibadah** (masjid/mushalla, tempat wudhu, arah kiblat, perlengkapan shalat), dan status verifikasi data.
4. **Katalog Kuliner Halal & Produk UMKM Lokal**: Informasi harga simulasi, kategori produk, wilayah, **status sertifikasi halal**, **sumber verifikasi**, dan kontak WhatsApp simulasi.
5. **Katalog Akomodasi Ramah Muslim**: Informasi harga per malam (simulasi), fasilitas umum, rincian **fasilitas ramah Muslim** (kiblat, sajadah, dapur/sarapan halal, lingkungan kondusif keluarga), dan kontak WhatsApp simulasi.
6. **Pencarian, Filter & Sorting**: Pencarian kata kunci secara *real-time*, filter wilayah, filter kategori, filter status halal (untuk kuliner), serta pengurutan (*Unggulan, Biaya Terendah, Biaya Tertinggi, Nama A–Z*).

### B. Peta, Personalisasi & Perencanaan
7. **Peta Ilustratif SVG & Tautan Google Maps**: Peta vektor interaktif wilayah Aceh utara–tengah (Sabang, Banda Aceh, Aceh Besar, Aceh Tengah, Bener Meriah) dengan pin destinasi interaktif dan tautan eksternal ke Google Maps tanpa memerlukan API key.
8. **Fitur Favorit**: Menyimpan dan mengelola item favorit (destinasi, kuliner, akomodasi) secara persisten di `localStorage` dengan panel/drawer khusus.
9. **Travel Itinerary Planner (1–5 Hari)**: Menyusun jadwal perjalanan multi-hari (Hari 1 s.d. Hari 5), memilih waktu aktivitas (Pagi/Siang/Sore/Malam), menambahkan item langsung dari katalog atau aktivitas kustom, serta menyimpan beberapa rencana perjalanan di `localStorage`.
10. **Kalkulator Estimasi Anggaran Perjalanan**: Menghitung otomatis estimasi biaya berdasarkan aktivitas terpilih, jumlah wisatawan, estimasi konsumsi harian, estimasi akomodasi per malam, dan transportasi lokal (seluruh nilai ditandai sebagai *estimasi simulasi*).
11. **Rekomendasi Paket Wisata (Rule-Based Filtering)**: Menyaring dan memberi skor kecocokan paket wisata berdasarkan preferensi minat/kategori, durasi (1–5 hari), dan rentang anggaran per wisatawan. Paket yang cocok dapat langsung diterapkan ke Itinerary Planner.

### C. Interaksi, Lokalisasi & Pengelolaan Data
12. **Tombol Kontak WhatsApp (Mode Demo)**: Menghasilkan pratinjau pesan WhatsApp terformat untuk pelaku UMKM, akomodasi, atau paket wisata menggunakan nomor simulasi nonpribadi.
13. **Pilihan Bahasa Indonesia & Inggris (`ID | EN`)**: Pergantian bahasa antarmuka dan konten katalog secara instan dan persisten di `localStorage`.
14. **Dashboard Demo CRUD**: Pengelolaan penuh (*Create, Read, Update, Delete*) untuk entitas Destinasi, Kuliner, Akomodasi, dan Paket Wisata, disertai fitur reset ke data awal contoh.
15. **Persistensi Lokal (`localStorage`)**: Menyimpan data favorit, daftar itinerary, konfigurasi bahasa, dan perubahan CRUD secara lokal di browser.

---

## 4. Data Model

Seluruh entitas disimpan sebagai struktur objek JSON di memori dan disinkronkan ke `localStorage` dengan namespace `pesona_aceh_*`.

### 4.1. `Destinasi`
| Field | Tipe Data | Deskripsi & Batasan |
| :--- | :--- | :--- |
| `id` | `string` | Identifier unik (contoh: `"dest-baiturrahman"`). |
| `nama` | `string` / `{ id: string, en: string }` | Nama destinasi wisata. |
| `kategori` | `enum` | Salah satu dari: `"Religi"`, `"Alam"`, `"Bahari"`, `"Sejarah"`, `"Budaya"`, `"Kuliner"`. |
| `wilayah` | `enum` | Salah satu dari: `"Banda Aceh"`, `"Sabang"`, `"Aceh Besar"`, `"Aceh Tengah"`, `"Bener Meriah"`. |
| `deskripsi` | `{ id: string, en: string }` | Deskripsi ringkas dan informatif destinasi. |
| `imageUrl` | `string` | Path gambar lokal atau fallback SVG editorial. |
| `alamat` | `string` | Alamat atau lokasi geografis ringkas. |
| `mapsUrl` | `string` | Tautan URL Google Maps (`https://www.google.com/maps/search/?api=1&query=...`) tanpa API key. |
| `estimasiBiaya` | `number` | Estimasi biaya tiket/masuk per orang dalam Rupiah (simulasi). |
| `fasilitas` | `string[]` | Daftar fasilitas umum (parkir, pemandu lokal, area istirahat, dll.). |
| `fasilitasIbadah` | `string[]` | Rincian fasilitas ibadah (masjid/mushalla, tempat wudhu terpisah, arah kiblat, mukena/sarung). |
| `unggulan` | `boolean` | Penanda destinasi unggulan untuk tampilan beranda dan pengurutan default. |
| `statusVerifikasiInfo` | `string` | Penanda apakah informasi destinasi bersifat `"Terverifikasi Dasar"` atau `"Belum Diverifikasi Lapangan"`. |
| `mapCoords` | `{ x: number, y: number }` | Koordinat relatif untuk penempatan pin pada peta ilustratif SVG. |

### 4.2. `Kuliner`
| Field | Tipe Data | Deskripsi & Batasan |
| :--- | :--- | :--- |
| `id` | `string` | Identifier unik kuliner/produk UMKM. |
| `nama` | `string` | Nama hidangan atau produk UMKM lokal. |
| `kategori` | `string` | Subkategori (contoh: `"Hidangan Utama"`, `"Kopi & Minuman"`, `"Kue & Oleh-Oleh UMKM"`). |
| `wilayah` | `enum` | `"Banda Aceh"`, `"Sabang"`, `"Aceh Besar"`, `"Aceh Tengah"`, `"Bener Meriah"`. |
| `harga` | `number` | Estimasi harga satuan/porsi dalam Rupiah (simulasi). |
| `imageUrl` | `string` | Path gambar lokal atau fallback SVG. |
| `statusSertifikasiHalal` | `enum` | `"Tersertifikasi Halal Resmi (Contoh Data)"`, `"Klaim Mandiri / Dalam Verifikasi"`, atau `"Belum Tersertifikasi Resmi"`. |
| `sumberVerifikasi` | `string` | Keterangan sumber verifikasi resmi (atau catatan bahwa produk belum memiliki verifikasi sertifikat resmi). |
| `kontak` | `string` | Nomor kontak simulasi nonpribadi (format demo). |

### 4.3. `Akomodasi`
| Field | Tipe Data | Deskripsi & Batasan |
| :--- | :--- | :--- |
| `id` | `string` | Identifier unik akomodasi. |
| `nama` | `string` | Nama penginapan/hotel/homestay contoh. |
| `wilayah` | `enum` | `"Banda Aceh"`, `"Sabang"`, `"Aceh Besar"`, `"Aceh Tengah"`, `"Bener Meriah"`. |
| `hargaPerMalam` | `number` | Estimasi tarif per malam dalam Rupiah (simulasi). |
| `fasilitas` | `string[]` | Fasilitas umum (Wi-Fi, AC/penghangat, sarapan, parkir). |
| `fasilitasRamahMuslim` | `string[]` | Fasilitas khusus ramah Muslim (arah kiblat, sajadah, Al-Qur'an, dapur bebas non-halal, kebijakan keluarga). *Catatan: Bukan pengganti sertifikat halal BPJPH/MPU.* |
| `imageUrl` | `string` | Path gambar lokal atau fallback SVG. |
| `kontak` | `string` | Nomor kontak simulasi nonpribadi (format demo). |

### 4.4. `PaketWisata`
| Field | Tipe Data | Deskripsi & Batasan |
| :--- | :--- | :--- |
| `id` | `string` | Identifier unik paket wisata. |
| `nama` | `{ id: string, en: string }` | Nama paket wisata tematik. |
| `durasi` | `number` | Durasi dalam hari (`1` s.d. `5`). |
| `daftarDestinasi` | `string[]` | Array `id` destinasi yang termasuk dalam paket. |
| `estimasiBiaya` | `number` | Estimasi biaya paket per wisatawan dalam Rupiah (simulasi). |
| `deskripsi` | `{ id: string, en: string }` | Ringkasan pengalaman dan fokus paket. |
| `minatKategori` | `string[]` | Tag kategori untuk pencocokan *rule-based filtering*. |
| `wilayahCakupan` | `string[]` | Wilayah yang dikunjungi dalam paket. |

### 4.5. `Itinerary`
| Field | Tipe Data | Deskripsi & Batasan |
| :--- | :--- | :--- |
| `id` | `string` | Identifier unik rencana perjalanan. |
| `namaPerjalanan` | `string` | Judul rencana perjalanan pengguna. |
| `tanggalMulai` | `string` | Tanggal mulai format ISO (`YYYY-MM-DD`). |
| `jumlahHari` | `number` | Durasi perjalanan (`1` s.d. `5`). |
| `jumlahWisatawan` | `number` | Jumlah peserta perjalanan (`>= 1`). |
| `daftarAktivitas` | `AktivitasItem[]` | Daftar aktivitas berisi `{ id, hariKe, waktu, judul, tipe, itemId, wilayah, estimasiBiaya }`. |
| `biayaAkomodasiPerMalam` | `number` | Input simulasi biaya penginapan per malam. |
| `biayaMakanPerHari` | `number` | Input simulasi biaya makan per orang per hari. |
| `biayaTransportPerHari` | `number` | Input simulasi biaya transportasi lokal per hari. |
| `totalAnggaran` | `number` | Hasil kalkulasi total seluruh komponen anggaran (simulasi). |

### 4.6. `Favorit`
| Field | Tipe Data | Deskripsi & Batasan |
| :--- | :--- | :--- |
| `id` | `string` | Identifier unik entri favorit. |
| `itemId` | `string` | Referensi ID item (`Destinasi`, `Kuliner`, atau `Akomodasi`). |
| `tipeItem` | `enum` | `"destinasi"` \| `"kuliner"` \| `"akomodasi"`. |
| `tanggalDitambahkan` | `string` | Timestamp ISO saat item disimpan ke favorit. |

---

## 5. Nonfunctional Requirements (NFR)

1. **Portabilitas & Tanpa Instalasi Tambahan**: Prototipe *single HTML* dapat dijalankan langsung melalui browser modern (`Chrome`, `Edge`, `Firefox`, `Safari`) baik via server Vite maupun langsung dibuka sebagai berkas lokal, tanpa instalasi database atau server backend.
2. **Keamanan & Privasi Data**:
   - Tidak menyimpan API key atau kredensial rahasia apa pun di kode sumber.
   - Tidak menggunakan form login atau autentikasi palsu.
   - Seluruh nomor telepon/kontak dan harga menggunakan data contoh nonpribadi yang ditandai secara eksplisit sebagai **data simulasi**.
   - Semua input pengguna pada CRUD dan Itinerary disanitasi (menghindari injeksi HTML mentah via `textContent` / escaping).
3. **Kepatuhan Klaim Halal & Verifikasi Informasi**:
   - Aplikasi tidak boleh menampilkan label "Halal Resmi" pada produk yang belum memiliki sumber verifikasi.
   - Aplikasi wajib membedakan informasi **Fasilitas Ramah Muslim** dari **Status Sertifikasi Halal Resmi**.
   - Aplikasi tidak boleh mengarang ulasan atau rating bintang wisatawan fiktif.
4. **Kinerja & Responsivitas**:
   - Interaksi pencarian, filter, kalkulasi anggaran, dan perpindahan tab merespons di bawah `100ms` di sisi klien.
   - Tata letak responsif untuk layar desktop (`>= 1280px`), tablet (`768px–1023px`), dan smartphone (`360px–767px`).
5. **Aksesibilitas & Keterbacaan (WCAG AA)**:
   - Rasio kontras teks minimal `4.5:1` pada latar belakang terang maupun gelap.
   - Navigasi keyboard yang jelas (`focus-visible`) dan ukuran target sentuh memadai di perangkat mobile.

---

## 6. Risiko & Mitigasi (Risks & Mitigations)

| No | Risiko | Dampak | Mitigasi |
| :--- | :--- | :--- | :--- |
| 1 | **Klaim Halal Tidak Akurat** | Menyesatkan wisatawan Muslim terkait status kehalalan produk UMKM/kuliner. | Memisahkan kategori status sertifikasi (`Tersertifikasi Halal Resmi (Contoh)`, `Klaim Mandiri`, `Belum Tersertifikasi`), menampilkan `sumberVerifikasi`, dan menyertakan disclaimer simulasi. |
| 2 | **Kebingungan Antara Ramah Muslim dan Sertifikat Halal** | Pengguna menganggap akomodasi ramah Muslim otomatis memiliki sertifikat halal dapur resmi. | Menampilkan label eksplisit bahwa fasilitas ramah Muslim (kiblat, sajadah, bebas alkohol) bersifat kesiapan layanan, terpisah dari sertifikasi halal produk BPJPH/MPU. |
| 3 | **Data Destinasi Nyata Belum Terverifikasi Lapangan** | Perubahan jam buka, biaya masuk, atau fasilitas ibadah aktual di lokasi. | Menambahkan field `statusVerifikasiInfo` beserta catatan verifikasi pada detail destinasi dan menandai seluruh tarif sebagai estimasi simulasi. |
| 4 | **Keterbatasan `localStorage`** | Data CRUD, favorit, atau itinerary hilang jika cache browser dibersihkan atau kapasitas terlampaui. | Menyediakan tombol ekspor ringkasan itinerary (JSON/cetak) dan tombol "Reset Data Contoh" yang aman serta penanganan `try/catch` saat baca/tulis `localStorage`. |
| 5 | **Ketergantungan Aset Gambar Eksternal** | Gambar rusak apabila dibuka tanpa internet atau di lingkungan terisolasi. | Menggunakan aset lokal atau fallback ilustrasi SVG terintegrasi langsung pada setiap kartu agar tampilan tetap utuh dalam mode offline. |

---

## 7. Out-of-Scope (Di Luar Cakupan MVP)

Fitur-fitur berikut secara sadar **tidak** disertakan pada fase MVP:
- Backend server, database relasional/NoSQL cloud, dan sinkronisasi lintas perangkat secara real-time.
- Sistem registrasi, login akun, atau otorisasi berbasis peran (*RBAC*) produksi.
- Integrasi pembayaran online (*payment gateway*), pemesanan hotel/tiket langsung (*OTA booking engine*), atau transaksi e-commerce.
- Integrasi Google Maps JavaScript SDK berbayar, pelacakan GPS real-time, atau perhitungan rute lalu lintas langsung.
- Sistem ulasan/rating publik dari pengguna (*user-generated reviews*) atau chatbot berbasis LLM.
- Integrasi API langsung ke database sertifikasi halal BPJPH/LPPOM secara live.

---

## 8. Acceptance Criteria (Kriteria Penerimaan Manual)

Setiap skenario berikut dapat diuji secara manual langsung di browser:

| ID | Skenario Uji | Langkah Pengujian | Hasil yang Diharapkan |
| :--- | :--- | :--- | :--- |
| **AC-01** | **Katalog & Pencarian** | Ketik kata kunci (mis. `"Sabang"` atau `"Kopi"`) pada kolom pencarian destinasi. | Daftar destinasi tersaring seketika menampilkan item yang cocok tanpa reload halaman; jumlah hasil diperbarui. |
| **AC-02** | **Filter Wilayah & Kategori** | Pilih filter wilayah `"Aceh Tengah"` lalu pilih kategori `"Alam"`, kemudian ubah sorting ke `"Biaya Terendah"`. | Hanya destinasi Aceh Tengah berkategori Alam yang tampil, terurut naik berdasarkan `estimasiBiaya`. |
| **AC-03** | **Detail Destinasi & Ibadah** | Klik salah satu kartu destinasi. | Modal detail terbuka menampilkan foto/ilustrasi, deskripsi, fasilitas umum, **fasilitas ibadah**, status verifikasi info, estimasi biaya simulasi, dan tautan eksternal Google Maps yang valid. |
| **AC-04** | **Status Halal Kuliner & Akomodasi** | Buka tab/seksi Kuliner & Akomodasi, periksa produk dengan status berbeda. | Terlihat jelas perbedaan antara produk tersertifikasi contoh, klaim mandiri, dan belum terverifikasi pada Kuliner, serta fasilitas ramah Muslim pada Akomodasi. |
| **AC-05** | **Favorit & Persistensi** | Klik tombol Favorit pada 2 destinasi dan 1 kuliner, lalu muat ulang (*refresh*) halaman browser. | Jumlah favorit di tombol/drawer tetap 3 setelah reload dan daftar item tersimpan muncul di panel Favorit. |
| **AC-06** | **Itinerary Planner (1–5 Hari)** | Buat rencana perjalanan 3 hari, tambahkan aktivitas dari katalog atau form kustom ke Hari 1 dan Hari 2, lalu refresh browser. | Aktivitas tersusun per hari, dapat dihapus/dipindahkan, dan tetap tersimpan di `localStorage` setelah reload. |
| **AC-07** | **Kalkulator Anggaran** | Ubah jumlah wisatawan dari `2` menjadi `4` dan ubah estimasi biaya penginapan/makan. | Total anggaran grup dan estimasi per orang langsung terhitung ulang dengan format Rupiah yang akurat. |
| **AC-08** | **Rekomendasi Paket (Rule-Based)** | Pilih minat `"Bahari"`, durasi `3` hari, dan anggaran `<= Rp 3.000.000`, lalu klik `"Terapkan ke Itinerary"`. | Paket yang sesuai muncul dengan alasan kecocokan; menekan terapkan langsung mengisi rencana perjalanan di Itinerary Planner. |
| **AC-09** | **Tombol WhatsApp Demo** | Klik `"Hubungi via WhatsApp (Demo)"` pada item UMKM atau akomodasi. | Modal pratinjau pesan WhatsApp muncul menampilkan nomor simulasi, draf pesan otomatis, dan tautan `wa.me` demo. |
| **AC-10** | **Pergantian Bahasa (`ID / EN`)** | Klik tombol bahasa `EN` lalu kembali ke `ID`, kemudian refresh halaman. | Seluruh label navigasi, filter, deskripsi, dan form berubah bahasa sesuai pilihan dan preferensi tetap tersimpan. |
| **AC-11** | **Dashboard Demo CRUD** | Buka tab Dashboard CRUD, tambah 1 destinasi baru, edit namanya, periksa di katalog utama, lalu hapus atau reset data contoh. | Data baru langsung muncul di katalog dan peta, pembaruan tersimpan ke `localStorage`, penghapusan menghapus item, dan reset mengembalikan data awal. |

---

## 9. Implementation Plan per Iterasi

### Iterasi 1 — Fondasi Editorial, Data Model & Katalog Utama
- Perancangan sistem desain Aceh Halal Tourism (palet *Emerald Green, Turquoise, Gold, Ivory White*, ornamen geometris *Pinto Aceh*, tipografi editorial serif + sans-serif).
- Penyusunan dataset contoh terverifikasi/simulasi (15 Destinasi di 5 wilayah & 6 kategori, 8 Kuliner/UMKM, 6 Akomodasi, 5 Paket Wisata).
- Implementasi katalog interaktif dengan pencarian, filter wilayah, filter kategori, pengurutan, modal detail, serta fasilitas ibadah & status halal.

### Iterasi 2 — Peta Ilustratif SVG, Favorit & Lokalisasi ID/EN
- Pembangunan peta ilustratif SVG Provinsi Aceh (Sabang, Banda Aceh, Aceh Besar, Aceh Tengah, Bener Meriah) dengan pin interaktif dan tautan Google Maps tanpa API key.
- Implementasi manajemen Favorit lintas entitas (`localStorage`) dan panel/drawer Favorit.
- Implementasi sistem translasi dwibahasa (`ID | EN`) menyeluruh beserta persistensi konfigurasi.

### Iterasi 3 — Travel Itinerary Planner, Kalkulator Anggaran & Rekomendasi Rule-Based
- Pembangunan Itinerary Planner 1–5 hari dengan penambahan aktivitas dari katalog maupun input kustom.
- Implementasi Kalkulator Estimasi Anggaran Perjalanan *real-time* (tiket/aktivitas, makan, akomodasi, transportasi).
- Implementasi mesin rekomendasi paket wisata berbasis *rule-based filtering* dengan aksi satu klik terapkan ke itinerary dan pratinjau kontak WhatsApp mode demo.

### Iterasi 4 — Dashboard Demo CRUD, Pengujian Manual & Finalisasi Single-HTML
- Pembangunan Dashboard Demo CRUD (Create, Read, Update, Delete, Reset Data Awal) untuk 4 entitas utama yang langsung tersinkronisasi dengan katalog dan peta.
- Audit kepatuhan batasan (penandaan data simulasi, pemisahan fasilitas ramah Muslim vs sertifikasi halal, tanpa API key/login palsu/rating palsu).
- Pengemasan prototipe *single HTML* mandiri serta verifikasi manual terhadap seluruh Acceptance Criteria (`AC-01` s.d. `AC-11`).
