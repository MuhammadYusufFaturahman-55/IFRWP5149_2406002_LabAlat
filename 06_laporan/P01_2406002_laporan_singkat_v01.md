# LAPORAN SINGKAT PRAKTIKUM

**PERTEMUAN 01: PENGENALAN LINGKUNGAN PRAKTIKUM DAN KAKAS PEMODELAN UML**

**Mata Kuliah:** Praktikum Analisis & Desain Berorientasi Objek (IFRWP5149)

**Program Studi:** S1 Teknik Informatika — Institut Teknologi Garut

## 📌 1. Identitas Mahasiswa

| Field | Detail Informasi | 
| ----- | ----- | 
| **Nama Lengkap** | Muhammad Yusuf Faturahman | 
| **NIM** | `2406002` | 
| **Kelas** | Informatika A | 
| **Program Studi** | S1 Teknik Informatika | 
| **Mata Kuliah** | Praktikum Analisis & Desain Berorientasi Objek | 
| **Kakas Pemodelan** | Draw.io (Desktop / Web) | 
| **Nama Berkas Dokumen** | `P01_2406002_laporan_singkat_v01.md` | 

## 🎯 2. Tujuan Pembelajaran & Bobot RPS

Setelah mengikuti praktikum Pertemuan 01, mahasiswa mampu:

1. Membuat *workspace* proyek praktikum sesuai struktur folder SOP yang ditetapkan (`IFRWP5149_2406002_LabAlat`).
2. Mengoperasikan fitur dasar kakas pemodelan UML (membuat kanvas, memilih pustaka notasi, menghubungkan elemen, menuliskan label, menyimpan berkas sumber, serta mengekspor diagram).
3. Membuktikan keterbukaan kembali berkas sumber (`.drawio`) agar dapat disunting ulang (*re-editable*).
4. Menyiapkan template metadata artefak dan logbook praktikum individu.

**Bobot Penilaian RPS:** 1% dari total nilai akhir mata kuliah.

## 📖 3. Dasar Teori & Orientasi Kasus

### **A. Pengenalan Kakas Pemodelan UML**

UML (Unified Modeling Language) adalah bahasa pemodelan standar untuk visualisasi, spesifikasi, konstruksi, dan dokumentasi sistem berorientasi objek. Kakas pemodelan seperti **Draw.io**, **Visual Paradigm**, dan **StarUML** berfungsi sebagai alat bantu grafis. 

Pada praktikum ini, format berkas sumber `.drawio` diwajibkan untuk disimpan secara lokal sebagai bukti autentik pemodelan yang dapat disunting kembali, sedangkan gambar ekspor (`.png`/`.svg`) digunakan untuk peninjauan visual.

### **B. Orientasi Skenario Latihan (`S-ORI-01`)**

* **Domain Kasus Semester:** *Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus*.
* **Skenario Latihan Alat (`S-ORI-01`):** Mahasiswa membuka daftar peralatan laboratorium dan melihat informasi ketersediaan peralatan.
* **Batas Pemodelan P01:** Pemodelan uji operasional kakas menggunakan diagram aktivitas sederhana 4 elemen (tanpa aturan keputusan persetujuan, denda, atau arsitektur basis data).

## 📄 4. Hasil Uji Operasional Kakas (Activity Diagram Sederhana `S-ORI-01`)

Diagram aktivitas uji kanvas dibangun menggunakan 4 elemen terurut sebagai berikut:

$$\text{Initial Node (Start)} \longrightarrow \text{Aktivitas: "Buka daftar peralatan"} \longrightarrow \text{Aktivitas: "Lihat informasi ketersediaan"} \longrightarrow \text{Activity Final Node (End)}$$

### **Spesifikasi Berkas & Pengujian Kakas:**

* **Judul Kanvas:** Latihan kakas S-ORI-01
* **Status Model:** *Latihan — Belum divalidasi sebagai model proses*
* **Uji Buka Ulang (Re-editability Test):** Berkas `P01_2406002_latihan_activity_v01.drawio` telah ditutup dan dibuka kembali, posisi node digeser untuk membuktikan integritas struktur data XML draw.io, kemudian diekspor ulang menjadi `P01_2406002_latihan_activity_v01.png`.

## 📝 5. Template Metadata Artefak Standar P01

```markdown
ID Artefak       : LAB-P01-ACT
Judul            : Uji Operasional Kakas Diagram Aktivitas S-ORI-01
Pertemuan        : 01
Sumber Skenario  : S-ORI-01 (Orientasi Kasus Laboratorium)
Jenis/Status     : Activity Diagram / Latihan — Belum divalidasi
Kakas Pembuat    : Draw.io Desktop v22.x / Web
Pembuat          : Muhammad Yusuf Faturahman (NIM: 2406002)
Versi & Tanggal  : v01 / 2026-09-14
Asumsi           : Autentikasi dan mekanisme filter ketersediaan di luar cakupan P01
Pemeriksaan      : Berkas sumber (.drawio) dapat dibuka dan disunting ulang
Riwayat Revisi   : v01 - Inisialisasi awal berkas latihan
```

## 📁 6. Struktur Workspace SOP Praktikum (`IFRWP5149_2406002_LabAlat`)

```
IFRWP5149_2406002_LabAlat/
├── 00_administrasi/
│   └── P01_2406002_logbook_v01.md
├── 01_skenario/
│   └── S-ORI-01_orientasi_kasus_v01.md
├── 02_template/
│   └── template_metadata_artefak_v01.md
├── 03_latihan_tools/
│   ├── P01_2406002_latihan_activity_v01.drawio
│   └── P01_2406002_latihan_activity_v01.png
├── 04_model_analisis/                         (Sengaja kosong pada P01)
├── 05_model_desain/                           (Sengaja kosong pada P01)
├── 06_laporan/
│   └── P01_2406002_laporan_singkat_v01.md
└── README.md
```

## 🔍 7. Checklist Quality Control Penyerahan P01

* [x] **Folder Induk:** Menggunakan penamaan baku `IFRWP5149_2406002_LabAlat`.
* [x] **README.md:** Memuat identitas mahasiswa (`Muhammad Yusuf Faturahman` - `2406002`), deskripsi kasus, dan status P01.
* [x] **Elemen Diagram:** Memuat 4 elemen terurut (*Start*, 2 *Action*, *End*) dengan garis konektor berarah yang terhubung sempurna.
* [x] **Status Model:** Dicantumkan catatan "*Belum divalidasi sebagai model proses*" untuk membedakannya dari model analisis final.
* [x] **Bukti Sumber & Ekspor:** Berkas sumber `.drawio` dan gambar ekspor `.png` tersimpan di subfolder `03_latihan_tools/` dengan nomor versi yang identik (`v01`).
* [x] **Uji Buka Ulang:** Berkas sumber berhasil ditutup, dibuka kembali, dan disunting tanpa *corrupt*.