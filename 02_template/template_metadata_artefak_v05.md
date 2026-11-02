# P05 - Metadata & Keterlacakan Skenario Use Case LAB & SIA

> Dokumen ini berisi metadata resmi, keterlacakan relasi UML ke skenario, dan lembar telaah untuk 12 tabel skenario Laboratorium (LAB) dan 7 tabel skenario Sistem Informasi Akademik (SIA) Pertemuan 05.

---

## 📌 1. Identitas Mahasiswa & Metadata Artefak

| Bidang Metadata | Isi Informasi |
|---|---|
| **Nama Mahasiswa** | Muhammad Yusuf Faturahman |
| **NIM** | `2406002` |
| **Kelas / Prodi** | Informatika A / S1 Teknik Informatika |
| **Mata Kuliah** | Praktikum Analisis dan Desain Berorientasi Objek (IFRWP5149) |
| **Pertemuan / Modul** | Pertemuan 05 — Skenario Use Case: Dari Diagram ke Langkah Kegiatan |
| **Tanggal Penyusunan** | 2 November 2026 |
| **Kakas Pembuat** | VS Code / Markdown Editor / Draw.io |
| **Status Artefak** | **v01** (Skenario Terverifikasi & Ditelaah) |

---

## 📁 2. Lokasi Penyimpanan Berkas & Workspace SOP

Seluruh dokumen skenario Pertemuan 05 disimpan di subfolder `01_skenario` pada folder induk `IFRWP5149_2406002_LabAlat`. Diagram acuan Pertemuan 04 di folder `04_model_analisis/P04` dipertahankan utuh dan **tidak diubah/ditimpa**.

```text
IFRWP5149_2406002_LabAlat/
├── 00_administrasi/
│   └── P05_2406002_logbook_v01.md
├── 01_skenario/
│   ├── P05_2406002_LAB_telaah_skenario_v01.md       (Lembar Telaah LAB)
│   ├── P05_2406002_SIA_skenario_v01.md              (Dokumen Skenario SIA)
│   └── P04_LAB_skenario_v01.md                      (Arsip Pertemuan 4)
├── 03_latihan_tools/
├── 04_model_analisis/
│   ├── P03/                                          (Tetap, arsip P03)
│   └── P04/                                          (Acuan utama, tidak diubah)
│       ├── LAB/ P04_2406002_LAB_usecase_v01.drawio (.png)
│       └── SIA/ P04_2406002_SIA_usecase_v01.drawio (.png)
└── 05_model_desain/                                  (Tetap kosong)
```

---

## 🎯 3. Prinsip Pemetaan Relasi Diagram ke Skenario (SOP P05)

1. **Relasi `<<include>>`:** Ditulis sebagai langkah pemanggilan **wajib** di dalam **Skenario Normal** (menyebut ID, Nama Use Case, dan nomor tabel skenario penyerta tanpa menyalin ulang langkahnya).
2. **Relasi `<<extend>>`:** Ditulis sebagai **cabang bersyarat** di **Skenario Alternative**, dilengkapi dengan `condition` dan `extension point`.
3. **Generalization Aktor:** Skenario ditulis **satu kali** atas nama Aktor Umum (misal: `Peminjam` atau `Civitas Akademika`), dengan catatan hak khusus aktor turunan (misal: `Mahasiswa`).
4. **Generalization Use Case:** Skenario Use Case Umum (misal: `LAB-UC02` / `SIA-UC10`) memuat alur bersama. Use Case Khusus hanya memuat **langkah pembeda** dan merujuk ke skenario umum.
5. **Collaboration & Realization:** Collaboration (`LAB-CO` / `SIA-CO`) **TIDAK** diberi langkah kegiatan tersendiri; cukup dicantumkan pada catatan/keterangan tabel Use Case yang direalisasikannya.
6. **Penomoran Berlanjut:** Penomoran langkah pada **Skenario Alternative** melanjutkan nomor terakhir dari **Skenario Normal** (tidak diulang dari nomor 1).

---

## 📋 4. Matriks Keterlacakan 12 Skenario Laboratorium (`LAB`)

| ID Use Case | Nama Use Case | Aktor Utama | Tipe Pemetaan Relasi UML | Rujukan Tabel Skenario P5 |
|---|---|---|---|---|
| **LAB-UC01** | Lihat Ketersediaan Peralatan | Peminjam | Generalization Aktor (`Mahasiswa`, `Dosen`) | Tabel 5.3 |
| **LAB-UC02** | Kelola Data Peralatan | Petugas Laboratorium | Generalization Use Case (Parent) | Tabel 5.6 |
| **LAB-UC03** | Ajukan Peminjaman | Peminjam | Base UC (`include` UC04, `extend` UC05) | Tabel 5.1 |
| **LAB-UC04** | Periksa Ketersediaan | Peminjam (Internal) | `<<include>>` dari `LAB-UC03` (Langkah 2) | Tabel 5.4 |
| **LAB-UC05** | Cetak Bukti Pengajuan | Mahasiswa | `<<extend>>` ke `LAB-UC03` (`[pilih cetak]`) | Tabel 5.5 |
| **LAB-UC06** | Proses Keputusan Peminjaman | Petugas Laboratorium | Asosiasi Utama (Disetujui / Ditolak) | Tabel 5.10 |
| **LAB-UC07** | Lihat Laporan Peminjaman | Kepala Laboratorium | Asosiasi Tunggal Mandiri | Tabel 5.11 |
| **LAB-UC08** | Tambah Data Peralatan | Petugas Laboratorium | Child UC dari `LAB-UC02` (Data Baru) | Tabel 5.7 |
| **LAB-UC09** | Ubah Data Peralatan | Petugas Laboratorium | Child UC dari `LAB-UC02` (Ubah Data) | Tabel 5.8 |
| **LAB-UC10** | Hapus Data Peralatan | Petugas Laboratorium | Child UC dari `LAB-UC02` (Syarat Bebas Pinjam) | Tabel 5.9 |
| **LAB-UC11** | Catat Pengembalian Peralatan | Petugas Laboratorium | Base UC (`include` UC12; Realisasi `LAB-CO02`)| Tabel 5.12 |
| **LAB-UC12** | Periksa Kondisi Peralatan | Petugas Laboratorium | `<<include>>` dari `LAB-UC11` (Langkah 6) | Tabel 5.13 |

---

## 🎓 5. Matriks Keterlacakan 7 Skenario Tugas Akademik (`SIA`)

| ID Use Case | Nama Use Case | Aktor Utama | Catatan & Pemetaan Relasi UML |
|---|---|---|---|
| **SIA-UC07** | Lihat Kalender Akademik | Civitas Akademika | Generalization Aktor (`Mahasiswa` & `Dosen`). Ditulis 1 kali. |
| **SIA-UC08** | Input Nilai Mata Kuliah | Dosen | Prasyarat: Dosen Pengampu; Realisasi `SIA-CO01`. |
| **SIA-UC09** | Lihat KHS | Mahasiswa | Menyajikan nilai terpublikasi; Realisasi `SIA-CO02`. |
| **SIA-UC10** | Kelola Data Mahasiswa | Admin Akademik | Generalization Use Case (Parent alur bersama). |
| **SIA-UC11** | Tambah Data Mahasiswa | Admin Akademik | Generalization Child (Data Mahasiswa Baru). |
| **SIA-UC12** | Ubah Data Mahasiswa | Admin Akademik | Generalization Child (Perubahan Data Mahasiswa). |
| **SIA-UC13** | Hapus Data Mahasiswa | Admin Akademik | Generalization Child (Syarat: Tidak ada data aktif). |

---

## 📝 6. Lembar Telaah Skenario Studi Kasus LAB

| No | Tabel yang Ditelaah | Relasi Diagram P04 yang Ditelusur | Hasil Pencocokan & Status Telaah |
|---|---|---|---|
| **1** | `LAB-UC01` | Asosiasi Peminjam (Generalization) | **Sesuai**. Berlaku untuk Mahasiswa dan Dosen tanpa duplikasi tabel. |
| **2** | `LAB-UC02` | Asosiasi Petugas Lab & Generalization Parent | **Sesuai**. Menyediakan struktur alur bersama untuk UC08, UC09, dan UC10. |
| **3** | `LAB-UC03` | Asosiasi Peminjam, Include UC04, Extend UC05, Realization `LAB-CO01` | **Sesuai**. Include di langkah 2, Extend di langkah 11-12, Collaboration pada catatan. |
| **4** | `LAB-UC04` | Include dari `LAB-UC03` | **Sesuai**. Berjalan internal di dalam alur pengajuan tanpa interaksi aktor langsung. |
| **5** | `LAB-UC05` | Extend ke `LAB-UC03` | **Sesuai**. Memuat `condition: [mahasiswa memilih cetak]` dan `extension point`. |
| **6** | `LAB-UC06` | Asosiasi Petugas Laboratorium | **Sesuai**. Memodelkan dua cabang keputusan (Disetujui / Ditolak). |
| **7** | `LAB-UC07` | Asosiasi Kepala Laboratorium | **Sesuai**. Berdiri sendiri, tanpa relasi include, extend, atau generalization. |
| **8** | `LAB-UC08` | Generalization Use Case ke `LAB-UC02` | **Sesuai**. Memuat langkah khusus tambah data dan merujuk alur bersama UC02. |
| **9** | `LAB-UC09` | Generalization Use Case ke `LAB-UC02` | **Sesuai**. Memuat langkah khusus ubah data dan merujuk alur bersama UC02. |
| **10** | `LAB-UC10` | Generalization Use Case ke `LAB-UC02` | **Sesuai**. Memuat syarat pemeriksaan data tidak sedang aktif dipinjam. |
| **11** | `LAB-UC11` | Asosiasi Petugas Lab, Include UC12, Realization `LAB-CO02` | **Sesuai**. Memeriksa prasyarat status Dipinjam dan memanggil UC12 pada langkah 6. |
| **12** | `LAB-UC12` | Include dari `LAB-UC11` | **Sesuai**. Mencatat nilai kondisi (Baik, Rusak Ringan, Rusak Berat) secara internal. |

---

## 🔍 7. Checklist Quality Control Pertemuan 05

- [x] **Kelengkapan Field:** Seluruh field tabel (Nama UC, Aktor, Tujuan, Deskripsi, Skenario Normal, Skenario Alternative, Skenario Akhir) terisi penuh.
- [x] **Pemisahan Kolom:** Kolom `Kegiatan` hanya berisi aksi aktor; kolom `Respon sistem` hanya berisi tanggapan sistem.
- [x] **Penomoran Berlanjut:** Penomoran Skenario Alternative melanjutkan nomor terakhir Skenario Normal tanpa pengulangan dari nomor 1.
- [x] **Pemetaan Include:** Relasi include dipanggil sebagai langkah rujukan wajib pada Skenario Normal.
- [x] **Pemetaan Extend:** Relasi extend dipanggil pada Skenario Alternative lengkap dengan *condition* dan *extension point*.
- [x] **Pemetaan Generalization:** Generalization aktor ditulis 1 kali atas nama Aktor Umum; Generalization UC dipisahkan antara alur bersama dan alur pembeda.
- [x] **Keterangan Collaboration:** Collaboration dicantumkan dalam catatan tabel UC yang direalisasikan tanpa membuat langkah tersendiri.
- [x] **Konsistensi Nama & ID:** Seluruh ID, nama use case, dan aktor persis sama dengan Diagram Kumulatif Pertemuan 04.