# LAPORAN SINGKAT PRAKTIKUM

**PERTEMUAN 03: USE CASE DIAGRAM DAN USE CASE DESCRIPTION**

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
| **Nama Berkas Dokumen** | `P03_2406002_laporan_singkat_v01.md` |

---

## 🎯 2. Tujuan Pembelajaran

Setelah mengikuti praktikum Pertemuan 03, mahasiswa mampu:

1. Menuliskan batas sistem (*system boundary*), aktor, kebutuhan, aturan bisnis, dan asumsi dari skenario yang diberikan.
2. Menentukan *use case* berdasarkan tujuan aktor, bukan berdasarkan nama tombol, tabel, atau langkah teknis antarmuka.
3. Membuat Use Case Diagram yang konsisten dengan daftar kebutuhan dan hubungan aktor-fungsi.
4. Menyusun Use Case Description lengkap yang memuat pemicu, prasyarat, alur utama (*main flow*), alur alternatif/pengecualian (*alternative flow*), serta pascakondisi berhasil dan gagal.
5. Menunjukkan keterlacakan (*traceability*) setiap *use case* ke kebutuhan yang mendasarinya.
6. Memperbaiki model berdasarkan hasil *review* dan mendokumentasikan perubahan pada versi berikutnya (`v01` ke `v02`).

---

## 📖 3. Dasar Teori Ringkas

### **A. Pengertian Use Case Diagram**

Use Case Diagram menggambarkan fungsionalitas yang disediakan oleh sistem dari sudut pandang eksternal (aktor). Diagram ini berfokus pada **apa** (*what*) yang dilakukan sistem, bukan **bagaimana** (*how*) sistem mengimplementasikannya secara teknis.

### **B. Simbol Utamanya (OMG UML 2.5.1)**

* **Aktor (Actor):** Menggambarkan peran orang, sistem lain, atau proses yang berinteraksi langsung dengan sistem. Digambar di **luar** batas sistem.
* **Use Case:** Fungsionalitas atau aksi utama yang bernilai bagi aktor. Dinamai dengan kata kerja + objek (contoh: *Ajukan Peminjaman*). Digambar di **dalam** batas sistem.
* **Batas Sistem (System Boundary):** Kotak pembatas yang memisahkan antara bagian internal sistem dengan lingkungan luar (aktor).
* **Asosiasi (Association):** Garis utuh tanpa panah yang menghubungkan Aktor dengan Use Case.
* **Relasi `<<include>>`:** Relasi garis putus-putus berpanah terbuka dari Use Case dasar menuju Use Case penyerta. Perilaku penyerta ini **selalu dieksekusi** sebagai bagian dari Use Case dasar.
* **Relasi `<<extend>>`:** Relasi garis putus-putus berpanah terbuka dari Use Case tambahan menuju Use Case dasar. Perilaku ini bersifat **opsional / bersyarat** dan dieksekusi hanya pada titik *Extension Point* jika syarat (*condition*) terpenuhi.

### **C. Perbandingan Relasi `<<include>>` vs `<<extend>>`**

| Aspek | Relasi `<<include>>` | Relasi `<<extend>>` |
| :--- | :--- | :--- |
| **Tujuan** | Menyertakan fungsi wajib/kritis | Menambahkan fungsi opsional/bersyarat |
| **Arah Panah** | Base Use Case $\rightarrow$ Included Use Case | Extending Use Case $\rightarrow$ Base Use Case |
| **Sifat Eksekusi** | Selalu dijalankan | Dijalankan jika *condition* terpenuhi |
| **Kemandirian Use Case Dasar** | Membutuhkan *included use case* | Tetap utuh dan bermakna tanpa *extend* |
| **Kelengkapan Notasi** | Panah + Label `<<include>>` | Panah + Label `<<extend>>` + *Condition* & *Extension Point* |

---

## 📄 4. Studi Kasus Laboratorium (`LAB`)

### **A. Daftar Kebutuhan Sistem (`LAB-R01` s.d. `LAB-R06`)**

| ID Kebutuhan | Spesifikasi Kebutuhan | Use Case Terkait |
| :---: | :--- | :--- |
| **LAB-R01** | Mahasiswa dapat melihat ketersediaan peralatan laboratorium. | `LAB-UC01 Lihat Ketersediaan Peralatan` |
| **LAB-R02** | Petugas laboratorium dapat mengelola data peralatan. | `LAB-UC02 Kelola Data Peralatan` |
| **LAB-R03** | Mahasiswa dapat mengajukan peminjaman; sistem memeriksa ketersediaan sebelum menyimpan pengajuan. | `LAB-UC03 Ajukan Peminjaman` (`<<include>>` `LAB-UC04`) |
| **LAB-R04** | Mahasiswa dapat mencetak bukti pada konfirmasi pengajuan jika memilihnya. | `LAB-UC05 Cetak Bukti Pengajuan` (`<<extend>>` `LAB-UC03`) |
| **LAB-R05** | Petugas laboratorium dapat menetapkan persetujuan atau penolakan pengajuan peminjaman. | `LAB-UC06 Proses Keputusan Peminjaman` |
| **LAB-R06** | Kepala laboratorium dapat melihat laporan peminjaman peralatan. | `LAB-UC07 Lihat Laporan Peminjaman` |

### **B. Katalog Use Case Laboratorium**

| ID Use Case | Nama Use Case | Aktor Utama | Tipe Relasi / Peran |
| :---: | :--- | :--- | :--- |
| **LAB-UC01** | Lihat Ketersediaan Peralatan | Mahasiswa | Utama (Asosiasi) |
| **LAB-UC02** | Kelola Data Peralatan | Petugas Laboratorium | Utama (Asosiasi) |
| **LAB-UC03** | Ajukan Peminjaman | Mahasiswa | Utama (Base Use Case `include` & `extend`) |
| **LAB-UC04** | Periksa Ketersediaan | *(Internal System)* | Included Use Case dari `LAB-UC03` |
| **LAB-UC05** | Cetak Bukti Pengajuan | Mahasiswa | Extending Use Case ke `LAB-UC03` |
| **LAB-UC06** | Proses Keputusan Peminjaman | Petugas Laboratorium | Utama (Asosiasi) |
| **LAB-UC07** | Lihat Laporan Peminjaman | Kepala Laboratorium | Utama (Asosiasi) |

---

## 📝 5. Use Case Description Utama (`LAB-UC03`)

| Bagian Deskripsi | Spesifikasi Dokumentasi |
| :--- | :--- |
| **ID & Nama Use Case** | **LAB-UC03: Ajukan Peminjaman** |
| **Sumber Kebutuhan** | `LAB-R03` dan `LAB-R04` |
| **Tujuan** | Menghasilkan pengajuan peminjaman peralatan yang berhasil tersimpan di sistem. |
| **Aktor Utama** | Mahasiswa |
| **Aktor Pendukung** | *(Tidak ada)* |
| **Pemicu** | Mahasiswa memilih fungsi pengajuan peminjaman peralatan. |
| **Prasyarat** | Mahasiswa telah terautentikasi; data peralatan tersedia dalam sistem. |
| **Pascakondisi Berhasil** | Pengajuan tersimpan dengan nomor pengajuan dan berstatus **Menunggu Keputusan**. |
| **Pascakondisi Gagal** | Tidak ada pengajuan baru yang berhasil tersimpan di sistem. |
| **Include** | `LAB-UC04: Periksa Ketersediaan` |
| **Extension Point** | *Bukti pengajuan tersedia* (pada langkah 6) |
| **Extend** | `LAB-UC05: Cetak Bukti Pengajuan` jika `[mahasiswa memilih cetak]` |

### **Alur Utama (Main Flow):**

| Langkah | Tindakan Aktor (Mahasiswa) | Respon Sistem |
| :---: | :--- | :--- |
| **1** | Membuka fungsi pengajuan peminjaman | Menampilkan formulir pengajuan peminjaman |
| **2** | Memilih peralatan, jumlah, rentang waktu pinjam, dan tujuan | Menampung isian formulir |
| **3** | Mengirim pengajuan peminjaman | Memeriksa kelengkapan isian data |
| **4** | *(Tidak ada)* | Menjalankan `LAB-UC04: Periksa Ketersediaan` |
| **5** | *(Tidak ada)* | Jika peralatan tersedia, menyimpan pengajuan dan menerbitkan nomor pengajuan berstatus **Menunggu Keputusan** |
| **6** | Melihat konfirmasi penyimpanan pengajuan | Menampilkan nomor dan status pengajuan; mencapai *Extension Point* (*Bukti pengajuan tersedia*) |
| **7** | Mengakhiri alur pengajuan | Menutup proses pengajuan peminjaman |

---

## 📄 6. Tugas Praktik Sistem Informasi Akademik (`SIA`)

### **A. Daftar Kebutuhan Tugas (`SIA-R01` s.d. `SIA-R06`)**

| ID Kebutuhan | Spesifikasi Kebutuhan Tugas | Use Case Terkait |
| :---: | :--- | :--- |
| **SIA-R01** | Mahasiswa dapat melihat jadwal kuliah. *(Bawaan P02)* | `SIA-UC01 Lihat Jadwal Kuliah` |
| **SIA-R02** | Admin akademik dapat mengelola jadwal kuliah. *(Bawaan P02)* | `SIA-UC02 Kelola Jadwal Kuliah` |
| **SIA-R03** | Mahasiswa dapat mengajukan Kartu Rencana Studi (KRS). | `SIA-UC03 Ajukan KRS` |
| **SIA-R04** | Sistem memvalidasi KRS (prasyarat & benturan) sebagai bagian dari pengajuan. | `SIA-UC04 Validasi KRS` (`<<include>>` dari `SIA-UC03`) |
| **SIA-R05** | Mahasiswa dapat mengunduh bukti KRS jika memilihnya pada konfirmasi pengajuan. | `SIA-UC05 Unduh Bukti Pengajuan KRS` (`<<extend>>` ke `SIA-UC03`) |
| **SIA-R06** | Dosen wali dapat memproses persetujuan atau penolakan pengajuan KRS. | `SIA-UC06 Proses Keputusan KRS` |

### **B. Katalog Use Case SIA**

| ID Use Case | Nama Use Case | Aktor Terkait | Keterangan Relasi |
| :---: | :--- | :--- | :--- |
| **SIA-UC01** | Lihat Jadwal Kuliah | Mahasiswa | Asosiasi (Fungsi P02) |
| **SIA-UC02** | Kelola Jadwal Kuliah | Admin Akademik | Asosiasi (Fungsi P02) |
| **SIA-UC03** | Ajukan KRS | Mahasiswa | Base Use Case (`include` & `extend`) |
| **SIA-UC04** | Validasi KRS | *(Internal System)* | `<<include>>` dari `SIA-UC03` |
| **SIA-UC05** | Unduh Bukti Pengajuan KRS | Mahasiswa | `<<extend>>` ke `SIA-UC03` (`[mahasiswa memilih unduh]`) |
| **SIA-UC06** | Proses Keputusan KRS | Dosen Wali | Asosiasi Utama Dosen Wali |

---

## 📁 7. Struktur Workspace Pertemuan 03

```text
IFRWP5149_2406002_LabAlat/
├── 00_administrasi/
│   └── P03_2406002_logbook_v01.md
├── 01_skenario/
│   ├── P03_2406002_LAB_kebutuhan_v01.md
│   ├── P03_2406002_LAB_skenario_v01.md
│   ├── P03_2406002_SIA_kebutuhan_v01.md
│   └── P03_2406002_SIA_skenario_v01.md
└── 04_model_analisis/
    └── P03/
        ├── LAB/
        │   ├── P03_2406002_LAB_deskripsi_v01.md
        │   ├── P03_2406002_LAB_usecase_v01.drawio
        │   └── P03_2406002_LAB_usecase_v01.png
        └── SIA/
            ├── P03_2406002_SIA_deskripsi_v01.md
            ├── P03_2406002_SIA_usecase_v01.drawio
            └── P03_2406002_SIA_usecase_v01.png
```

---

## 🔍 8. Checklist Quality Control Pertemuan 03

- [x] **Aktor & Batas Sistem:** Seluruh Aktor berada di luar *System Boundary*; Use Case berada di dalam *System Boundary*.
- [x] **Penamaan Use Case:** Seluruh Use Case dinamai dengan kata kerja + objek yang mencerminkan fungsi bernilai bagi aktor.
- [x] **Arah Panah Include:** Panah `<<include>>` mengarah dari Base Use Case ke Included Use Case (`LAB-UC03` $\rightarrow$ `LAB-UC04` / `SIA-UC03` $\rightarrow$ `SIA-UC04`).
- [x] **Arah Panah Extend:** Panah `<<extend>>` mengarah dari Extending Use Case ke Base Use Case (`LAB-UC05` $\rightarrow$ `LAB-UC03` / `SIA-UC05` $\rightarrow$ `SIA-UC03`).
- [x] **Notasi Lengkap Extend:** Menjelaskan *Condition* (`[mahasiswa memilih cetak/unduh]`) dan *Extension Point* (*Bukti tersedia*).
- [x] **Integritas Versi:** Berkas sumber `.drawio` dan ekspor `.png` menggunakan penamaan dan versi yang identik (`v01`).