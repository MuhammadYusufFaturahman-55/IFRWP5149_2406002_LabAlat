# LAPORAN SINGKAT PRAKTIKUM

**PERTEMUAN 04: USE CASE DIAGRAM LANJUTAN — GENERALIZATION DAN COLLABORATION**

**Mata Kuliah:** Praktikum Analisis & Desain Berorientasi Objek (IFRWP5149)

**Program Studi:** S1 Teknik Informatika — Institut Teknologi Garut

---

## 📌 1. Identitas Mahasiswa

| Field | Detail Informasi |
| :--- | :--- |
| **Nama Lengkap** | Muhammad Yusuf Faturahman |
| **NIM** | `2406002` |
| **Kelas** | Informatika A |
| **Program Studi** | S1 Teknik Informatika |
| **Mata Kuliah** | Praktikum Analisis & Desain Berorientasi Objek |
| **Kakas Pemodelan** | Draw.io / VS Code |
| **Nama Berkas Dokumen** | `P04_2406002_laporan_singkat_v01.md` |

---

## 🎯 2. Tujuan Pembelajaran

Setelah mengikuti praktikum Pertemuan 04, mahasiswa mampu:

1. Mengidentifikasi satu aktor umum dan minimal dua aktor khusus, lalu menyusun hierarki **Generalization Aktor** dengan arah panah yang benar (aktor khusus menuju aktor umum) tanpa menggambar ulang asosiasi yang diwarisi.
2. Menyusun **Generalization Use Case** yang memuat satu use case umum dan minimal dua use case khusus, serta menjelaskan perilaku yang diwarisi dan perilaku pembeda.
3. Menempatkan **Collaboration** (elips garis putus-putus) yang namanya sama persis dengan use case yang direalisasikan, dan menghubungkannya dengan relasi **Realization** (garis putus-putus berujung segitiga kosong) dari collaboration menuju use case.
4. Membuat **Use Case Diagram Kumulatif** Pertemuan 4 pada kasus laboratorium, yang mempertahankan utuh elemen Pertemuan 3 (`LAB-UC01` s.d. `LAB-UC07`, relasi `<<include>>`, relasi `<<extend>>`, beserta kondisi & extension point) lalu menambahkan elemen baru Pertemuan 4.
5. Menyusun satu **Use Case Description** baru (`LAB-UC11 Catat Pengembalian Peralatan`) yang memuat pemicu, prasyarat, alur utama, alur alternatif, pascakondisi berhasil, dan pascakondisi gagal yang konsisten dengan diagram.
6. Menunjukkan keterlacakan setiap elemen baru (`LAB-R07` s.d. `LAB-R11` dan `SIA-R07` s.d. `SIA-R12`) ke kebutuhan yang mendasarinya.

---

## 📖 3. Dasar Teori Ringkas

### **A. Generalization Aktor**
Generalization aktor menyatakan bahwa satu aktor bersifat umum (*parent*) dan aktor lain bersifat khusus (*specialized*). Aktor khusus mewarisi seluruh asosiasi aktor umum terhadap use case, serta dapat memiliki asosiasi khusus tambahan.
* **Aturan Notasi:** Panah garis utuh dengan ujung segitiga kosong menunjuk aktor umum (`Aktor Khusus → Aktor Umum`).
* **Penerapan Studi Kasus:** Aktor `Peminjam` (umum) diwarisi oleh `Mahasiswa` dan `Dosen` (khusus). Asosiasi ke `Lihat Ketersediaan` dan `Ajukan Peminjaman` ditarik satu kali dari `Peminjam`.

### **B. Generalization Use Case**
Generalization use case menyatakan bahwa satu use case bersifat umum (*parent*) dan use case lain merupakan bentuk khususnya (*child*). Use case khusus mewarisi tujuan dan perilaku dasar use case umum, lalu menambahkan atau menyesuaikan perilaku pembeda.
* **Aturan Notasi:** Panah garis utuh dengan ujung segitiga kosong menunjuk use case umum (`Use Case Khusus → Use Case Umum`).
* **Penerapan Studi Kasus:** `Kelola Data Peralatan` (`LAB-UC02`) diwarisi oleh `Tambah Data Peralatan` (`LAB-UC08`), `Ubah Data Peralatan` (`LAB-UC09`), dan `Hapus Data Peralatan` (`LAB-UC10`).

### **C. Collaboration & Realization**
Collaboration menyatakan struktur elemen/peran di dalam sistem yang bekerja sama untuk menyediakan perilaku sebuah use case. 
* **Notasi Collaboration:** Elips dengan garis putus-putus tanpa ID use case tersendiri (menggunakan ID `LAB-CO` / `SIA-CO`).
* **Notasi Realization:** Garis putus-putus dengan panah segitiga kosong dari Collaboration menuju Use Case (`Collaboration ⤍ Use Case`).
* **Catatan Penting:** Aktor **tidak pernah** dihubungkan langsung ke collaboration.

### **D. Perbandingan Praktis Empat Relasi UML**

| Relasi | Makna / Arti | Jenis Garis & Panah | Arah Panah |
| :--- | :--- | :--- | :--- |
| `<<include>>` | Perilaku penyerta selalu dieksekusi | Garis putus-putus, panah terbuka + label `<<include>>` | Base Use Case → Included Use Case |
| `<<extend>>` | Perilaku tambahan muncul jika kondisi terpenuhi | Garis putus-putus, panah terbuka + label `<<extend>>` | Extending Use Case → Base Use Case |
| **Generalization** | Elemen khusus mewarisi elemen umum | Garis utuh, panah segitiga kosong, tanpa label | Khusus → Umum (Child → Parent) |
| **Realization** | Collaboration mewujudkan use case | Garis putus-putus, panah segitiga kosong, tanpa label | Collaboration ⤍ Use Case |

---

## 📄 4. Matriks & Spesifikasi Diagram Kumulatif

### **A. Spesifikasi 17 Hubungan Diagram Kumulatif LAB**

| No | Elemen Asal (Source) | Jenis Relasi | Elemen Tujuan (Target) | Keterangan / Sumber Kebutuhan |
| :---: | :--- | :---: | :--- | :--- |
| 1 | `Peminjam` | Association | `LAB-UC01 Lihat Ketersediaan Peralatan` | Diwarisi Mahasiswa & Dosen (`LAB-R07`) |
| 2 | `Peminjam` | Association | `LAB-UC03 Ajukan Peminjaman` | Diwarisi Mahasiswa & Dosen (`LAB-R07`) |
| 3 | `Mahasiswa` | Association | `LAB-UC05 Cetak Bukti Pengajuan` | Asosiasi khusus milik Mahasiswa (`LAB-R04`) |
| 4 | `Mahasiswa` | Generalization | `Peminjam` | Ujung segitiga menunjuk `Peminjam` |
| 5 | `Dosen` | Generalization | `Peminjam` | Ujung segitiga menunjuk `Peminjam` |
| 6 | `Petugas Laboratorium` | Association | `LAB-UC02 Kelola Data Peralatan` | Fungsi pengelolaan bersama (`LAB-R08`) |
| 7 | `Petugas Laboratorium` | Association | `LAB-UC06 Proses Keputusan Peminjaman` | Keputusan persetujuan (`LAB-R05`) |
| 8 | `Petugas Laboratorium` | Association | `LAB-UC11 Catat Pengembalian Peralatan` | Fungsi pengembalian baru (`LAB-R09`) |
| 9 | `Kepala Laboratorium` | Association | `LAB-UC07 Lihat Laporan Peminjaman` | Satu-satunya asosiasi Kepala Lab (`LAB-R06`) |
| 10 | `LAB-UC03 Ajukan Peminjaman` | `<<include>>` | `LAB-UC04 Periksa Ketersediaan` | Relasi include tetap (`LAB-R03`) |
| 11 | `LAB-UC05 Cetak Bukti Pengajuan` | `<<extend>>` | `LAB-UC03 Ajukan Peminjaman` | Relasi extend tetap (`LAB-R04`) |
| 12 | `LAB-UC08 Tambah Data Peralatan` | Generalization | `LAB-UC02 Kelola Data Peralatan` | Form khusus Tambah (`LAB-R08`) |
| 13 | `LAB-UC09 Ubah Data Peralatan` | Generalization | `LAB-UC02 Kelola Data Peralatan` | Form khusus Ubah (`LAB-R08`) |
| 14 | `LAB-UC10 Hapus Data Peralatan` | Generalization | `LAB-UC02 Kelola Data Peralatan` | Form khusus Hapus (`LAB-R08`) |
| 15 | `LAB-UC11 Catat Pengembalian` | `<<include>>` | `LAB-UC12 Periksa Kondisi Peralatan` | Relasi include baru (`LAB-R10`) |
| 16 | `LAB-CO01` *(Collaboration)* | Realization | `LAB-UC03 Ajukan Peminjaman` | Realisasi Ajukan Peminjaman (`LAB-R11`) |
| 17 | `LAB-CO02` *(Collaboration)* | Realization | `LAB-UC11 Catat Pengembalian` | Realisasi Pengembalian (`LAB-R11`) |

---

### **B. Katalog Use Case Tugas Sistem Informasi Akademik (`SIA`)**

| ID Use Case | Nama Use Case | Aktor Terkait | Status / Jenis Pemetaan | Sumber Kebutuhan |
| :--- | :--- | :--- | :--- | :--- |
| **SIA-UC01** | Lihat Jadwal Kuliah | Mahasiswa, Dosen | Tetap dari P02 | `SIA-R01` |
| **SIA-UC02** | Kelola Jadwal Kuliah | Admin Akademik | Tetap dari P02 | `SIA-R02` |
| **SIA-UC03** | Ajukan KRS | Mahasiswa | Tetap dari P03 | `SIA-R03` |
| **SIA-UC04** | Validasi KRS | Dosen Wali | Tetap dari P03 | `SIA-R04` |
| **SIA-UC05** | Unduh Bukti Pengajuan KRS | Mahasiswa | Tetap dari P03 | `SIA-R05` |
| **SIA-UC06** | Proses Keputusan KRS | Dosen Wali | Tetap dari P03 | `SIA-R06` |
| **SIA-UC07** | Lihat Kalender Akademik | Civitas Akademika | Baru (Generalization Aktor) | `SIA-R07` |
| **SIA-UC08** | Input Nilai Mata Kuliah | Dosen | Baru (Realisasi `SIA-CO01`) | `SIA-R08`, `SIA-R12` |
| **SIA-UC09** | Lihat KHS | Mahasiswa | Baru (Realisasi `SIA-CO02`) | `SIA-R09`, `SIA-R12` |
| **SIA-UC10** | Kelola Data Mahasiswa | Admin Akademik | Baru (Generalization Parent) | `SIA-R10` |
| **SIA-UC11** | Tambah Data Mahasiswa | Admin Akademik | Baru (Generalization Child) | `SIA-R11` |
| **SIA-UC12** | Ubah Data Mahasiswa | Admin Akademik | Baru (Generalization Child) | `SIA-R11` |
| **SIA-UC13** | Hapus Data Mahasiswa | Admin Akademik | Baru (Generalization Child) | `SIA-R11` |

---

## 📝 5. Use Case Description Lanjutan (`LAB-UC11`)

| Elemen Deskripsi | Spesifikasi Deskripsi Use Case |
| :--- | :--- |
| **ID & Nama Use Case** | **LAB-UC11: Catat Pengembalian Peralatan** |
| **Sumber Kebutuhan** | `LAB-R09` dan `LAB-R10` |
| **Tujuan** | Pengembalian tercatat dan status peminjaman serta kondisi peralatan terbarui |
| **Aktor Utama** | Petugas Laboratorium |
| **Pemicu** | Petugas memilih fungsi pencatatan pengembalian dan menentukan peminjaman yang dikembalikan |
| **Prasyarat** | Petugas telah terautentikasi; peminjaman terpilih berstatus **Dipinjam** |
| **Pascakondisi Berhasil** | Pengembalian tercatat dengan tanggal kembali dan kondisi peralatan; status peminjaman menjadi **Selesai** |
| **Pascakondisi Gagal** | Tidak ada pengembalian baru yang tercatat; status peminjaman tidak berubah |
| **Include** | `LAB-UC12: Periksa Kondisi Peralatan` |
| **Collaboration** | `LAB-CO02: Catat Pengembalian Peralatan` |

### **Alur Utama (Main Flow):**

| Langkah | Tindakan Aktor (Petugas) | Respon Sistem |
| :---: | :--- | :--- |
| **1** | Memilih peminjaman yang akan dikembalikan | Menampilkan data peminjaman terpilih dan statusnya |
| **2** | Mengonfirmasi alat yang kembali dan jumlahnya | Menampung konfirmasi petugas |
| **3** | *(Tidak ada)* | Memeriksa status peminjaman harus **Dipinjam** |
| **4** | *(Tidak ada)* | Menjalankan `LAB-UC12: Periksa Kondisi Peralatan` |
| **5** | Menyimpan pencatatan pengembalian | Menyimpan tanggal kembali dan kondisi; mengubah status peminjaman menjadi **Selesai** |
| **6** | Melihat konfirmasi pengembalian | Menampilkan ringkasan pencatatan pengembalian |

### **Alur Alternatif / Pengecualian (Alternative Flows):**
* **A1: Status bukan Dipinjam (pada langkah 3):** Sistem menolak pencatatan dan menampilkan status peminjaman saat ini. Pascakondisi gagal berlaku; tidak ada data yang disimpan.
* **A2: Kondisi Rusak Ringan / Rusak Berat (pada langkah 4):** Sistem tetap menyimpan pencatatan, menandai kondisi pada data peralatan, dan pengembalian tetap tercatat tanpa denda.
* **A3: Jumlah alat yang kembali tidak sesuai (pada langkah 2):** Sistem meminta petugas memeriksa kembali isian sebelum penyimpanan.

---

## 📁 6. Struktur Workspace Pertemuan 04

```text
IFRWP5149_2406002_LabAlat/
├── 01_skenario/
│   ├── P04_2406002_LAB_kebutuhan_v01.md
│   ├── P04_2406002_LAB_skenario_v01.md
│   ├── P04_2406002_SIA_kebutuhan_v01.md
│   └── P04_2406002_SIA_skenario_v01.md
└── 04_model_analisis/
    ├── P03/                                   (Tetap, arsip P03 tidak diubah)
    └── P04/
        ├── LAB/
        │   ├── P04_2406002_LAB_usecase_v01.drawio
        │   └── P04_2406002_LAB_usecase_v01.png
        └── SIA/
            ├── P04_2406002_SIA_usecase_v01.drawio
            └── P04_2406002_SIA_usecase_v01.png
```

---

## 🔍 7. Checklist Quality Control Pertemuan 04

- [x] **Kumulatif:** Seluruh elemen Pertemuan 3 dipertahankan utuh (`LAB-UC01` s.d. `LAB-UC07`, `Kepala Laboratorium`, `<<include>>`, `<<extend>>`).
- [x] **Generalization Aktor:** Aktor `Peminjam` menerima asosiasi umum; panah generalization ditarik dari `Mahasiswa` dan `Dosen` dengan segitiga kosong menunjuk `Peminjam`.
- [x] **Generalization Use Case:** Panah generalization ditarik dari `UC08`, `UC09`, `UC10` ke `UC02` dengan segitiga kosong menunjuk `Kelola Data Peralatan`.
- [x] **Collaboration & Realization:** Collaboration digambar sebagai elips garis putus-putus (`LAB-CO01` & `LAB-CO02`), berada di dalam batas sistem, tidak terhubung langsung ke aktor, dan terhubung melalui garis realization berujung segitiga kosong menuju use case-nya.
- [x] **Batas Sistem:** Seluruh Aktor berada di luar batas sistem; seluruh Use Case dan Collaboration berada di dalam batas sistem.
- [x] **Integritas Versi:** Berkas P03 tidak ditimpa/diubah. Berkas sumber `.drawio` dan ekspor `.png` P04 konsisten menggunakan nama dan nomor versi `v01`.
```

Dokumen **Laporan Singkat Pertemuan 04** dalam bentuk berkas Markdown (`P04_2406002_laporan_singkat_v01.md`) sudah selesai dibuat dan dapat digunakan langsung di workspace Anda.