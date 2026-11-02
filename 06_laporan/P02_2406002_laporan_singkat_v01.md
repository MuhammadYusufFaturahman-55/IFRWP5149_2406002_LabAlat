# LAPORAN SINGKAT PRAKTIKUM

**PERTEMUAN 02: UNIFIED MODELING LANGUAGE (UML) — NOTASI DASAR DAN PERBAIKAN USE CASE**

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
| **Kakas Pemodelan** | Draw.io / VS Code | 
| **Nama Berkas Dokumen** | `P02_2406002_laporan_singkat_v01.md` | 

## 🎯 2. Tujuan Pembelajaran

Setelah mengikuti praktikum Pertemuan 02, mahasiswa mampu:

1. Menempatkan simbol aktor, use case, batas sistem (*system boundary*), dan asosiasi pada diagram sederhana sesuai skenario latihan.

2. Menggunakan nama aktor dan nama fungsi secara konsisten dengan skenario latihan.

3. Mengisi identitas artefak menggunakan template metadata yang telah disiapkan pada Pertemuan 01.

4. Menyimpan berkas sumber (`.drawio`) dan berkas ekspor (`.png`) dengan nama, lokasi, serta nomor versi yang konsisten.

5. Memperbaiki kesalahan notasi dan dokumentasi berdasarkan hasil *review*, kemudian mencatat perubahannya pada riwayat revisi.

## 📖 3. Dasar Teori Ringkas

### **A. Sejarah dan Perkembangan UML**

Unified Modeling Language (UML) dikembangkan pada pertengahan 1990-an oleh "Three Amigos" Rational Software: **Grady Booch** (Object-Oriented Design/OOD), **James Rumbaugh** (Object Modeling Technique/OMT), dan **Ivar Jacobson** (Object-Oriented Software Engineering/OOSE). 

* **1995:** Unified Method v0.8 diluncurkan.
* **1997:** Object Management Group (OMG) mengadopsi UML 1.1 sebagai standar industri.
* **2005 - Sekarang:** Pengenalan UML 2.0 dan 2.x dengan struktur diagram yang lebih ekspresif (13–14 jenis diagram).

### **B. Tiga Elemen Utama Building Blocks UML**

1. **Benda (Things):** Abstraksi utama dalam model (Structural: *Classes, Interfaces, Use Cases, Nodes*; Behavioral: *Interactions, State Machines*; Grouping: *Packages*; Annotational: *Notes*).

2. **Hubungan (Relationships):** Alat komunikasi antar benda (Structural: *Association, Generalization*; Semantic: *Dependency, Realization*).

3. **Diagram:** Kelompok grafis elemen visual UML.

### **C. Empat Notasi Dasar Use Case Diagram (Pertemuan 02)**

| Notasi | Simbol | Keterangan Pemodelan | 
| ----- | ----- | ----- | 
| **Aktor (Actor)** | `옷` *(Stick Figure)* | Orang, sistem luar, atau proses yang berinteraksi dengan use case. Diletakkan di **luar** batas sistem. | 
| **Use Case** | Oval / Elips Solid | Fungsionalitas atau aksi utama yang dijalankan sistem. Diberi nama kata kerja + objek. Diletakkan di **dalam** batas sistem. | 
| **Batas Sistem (System Boundary)** | Persegi Panjang | Kotak pembatas yang memisahkan bagian internal sistem dengan lingkungan luar (aktor). | 
| **Asosiasi (Association)** | Garis Utuh *(Solid Line)* | Menghubungkan Aktor dengan Use Case untuk menunjukkan partisipasi interaksi (bukan alur proses). | 

## 📄 4. Studi Kasus Laboratorium (`LAB`)

### **A. Kebutuhan Sistem (`LAB-R01` & `LAB-R02`)**

| ID Kebutuhan | Aktor Terkait | Nama Fungsi (Use Case) | Spesifikasi Fungsi | 
| ----- | ----- | ----- | ----- | 
| **LAB-R01** | Mahasiswa | `Lihat ketersediaan peralatan` | Mahasiswa melihat informasi ketersediaan peralatan laboratorium melalui sistem. | 
| **LAB-R02** | Petugas laboratorium | `Kelola data peralatan` | Petugas laboratorium mengelola data peralatan laboratorium. | 

### **B. Spesifikasi Asosiasi dan Komponen LAB**

* **Batas Sistem:** `Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium Kampus`
* **Aktor Kiri:** `Mahasiswa` (di luar batas sistem)
* **Aktor Kanan:** `Petugas laboratorium` (di luar batas sistem)
* **Garis Asosiasi:** 
  * `Mahasiswa` $\rightarrow$ `Lihat ketersediaan peralatan`
  * `Petugas laboratorium` $\rightarrow$ `Kelola data peralatan`

## 📝 5. Tugas Praktik SIA (Pemeriksaan & Perbaikan Notasi)

### **A. Kebutuhan Tugas SIA (`SIA-R01` & `SIA-R02`)**

* **SIA-R01:** Mahasiswa melihat jadwal kuliah melalui Sistem Informasi Akademik.
* **SIA-R02:** Admin akademik mengelola jadwal kuliah.

### **B. Tabel Matriks Temuan Kesalahan dan Koreksi Pemodelan**

| No | Temuan Kesalahan Diagram Awal | Perbaikan yang Dilakukan | Alasan Koreksi Berdasarkan Standar UML | 
| ----- | ----- | ----- | ----- | 
| **1** | Aktor `Mahasiswa` diletakkan di **dalam** batas sistem. | Memindahkan aktor `Mahasiswa` ke **luar** kotak batas sistem (sebelah kiri). | Aktor merepresentasikan entitas eksternal di luar perangkat lunak. | 
| **2** | Fungsi `Lihat jadwal kuliah` digambar menggunakan kotak persegi panjang. | Mengubah simbol fungsi dari kotak persegi panjang menjadi **elips / oval solid**. | Notasi resmi Use Case dalam UML wajib menggunakan simbol elips. | 
| **3** | Aktor `Mahasiswa` dihubungkan dengan `Kelola jadwal kuliah`. | Memutus asosiasi tersebut dan menghubungkan `Mahasiswa` hanya ke `Lihat jadwal kuliah`, serta `Admin akademik` ke `Kelola jadwal kuliah`. | Hubungan asosiasi harus mencerminkan pembagian hak akses aktor pada skenario. | 
| **4** | Judul batas sistem menggunakan nama sistem laboratorium. | Mengubah nama header batas sistem menjadi **`Sistem Informasi Akademik`**. | Judul batas sistem wajib mencerminkan nama domain aplikasi yang sedang dirancang. | 

## 📁 6. Struktur Workspace Pertemuan 02

```
IFRWP5149_2406002_LabAlat/
├── 00_administrasi/
│   └── P02_2406002_logbook_v01.md
├── 01_skenario/
│   ├── P02_LAB_skenario_v01.md
│   └── P02_SIA_skenario_v01.md
├── 03_latihan_tools/
│   └── P02/
│       ├── LAB/
│       │   ├── P02_2406002_LAB_notasi_usecase_v01.drawio
│       │   └── P02_2406002_LAB_notasi_usecase_v01.png
│       └── SIA/
│           ├── P02_2406002_SIA_perbaikan_notasi_v01.drawio  (Awal, Keliru)
│           ├── P02_2406002_SIA_notasi_v01.drawio            (Hasil Revisi)
│           └── P02_2406002_SIA_notasi_v01.png
└── 06_laporan/
    └── P02_2406002_jobsheet_review_v01.md

```

## 🔍 7. Checklist Quality Control Pertemuan 02

* \[x\] **Judul Sistem:** Judul pada batas sistem sesuai dengan domain kasus (`LAB` atau `SIA`).

* \[x\] **Letak Aktor:** Seluruh aktor berada di **luar** kotak batas sistem.

* \[x\] **Notasi Use Case:** Seluruh Use Case digambar menggunakan simbol **elips solid** dan berada di **dalam** kotak batas sistem.

* \[x\] **Penamaan Kata Kerja:** Nama use case memakai kata kerja + objek (*Lihat...*, *Kelola...*).

* \[x\] **Garis Asosiasi:** Garis asosiasi berupa garis utuh tanpa panah, menghubungkan aktor ke use case yang tepat.

* \[x\] **Tanpa Garis Urutan:** Tidak terdapat garis antar-elips use case (tidak memodelkan alur kerja pada Use Case Diagram).

* \[x\] **Integritas Versi:** Berkas `.drawio` dan ekspor `.png` menggunakan nomor versi yang sama (`v01`).