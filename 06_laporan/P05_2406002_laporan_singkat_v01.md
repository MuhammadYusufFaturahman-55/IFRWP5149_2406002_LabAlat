# LAPORAN SINGKAT PRAKTIKUM

**PERTEMUAN 05: SKENARIO USE CASE — DARI DIAGRAM KE LANGKAH KEGIATAN**

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
| **Nama Berkas Dokumen** | `P05_2406002_LAB_telaah_skenario_v01.md` / `P05_2406002_SIA_skenario_v01.md` |

---

## 🎯 2. Tujuan Pembelajaran

Setelah mengikuti praktikum Pertemuan 05, mahasiswa mampu:
1. Menyusun tabel skenario use case dengan struktur lengkap (*Nama use case, Aktor, Tujuan, Deskripsi, Kegiatan, Respon sistem, Skenario Normal, Skenario Alternative, Skenario Akhir*) tanpa ada *field* yang kosong.
2. Menulis langkah skenario secara berurutan dengan prinsip **satu aksi per langkah**, pemisahan aksi aktor (*Kegiatan*) dan tanggapan sistem (*Respon sistem*), serta **penomoran langkah berlanjut** dari Skenario Normal ke Skenario Alternative.
3. Memetakan relasi `<<include>>` menjadi langkah wajib rujukan di Skenario Normal dan relasi `<<extend>>` menjadi cabang bersyarat di Skenario Alternative (*dilengkapi condition & extension point*).
4. Menerapkan *generalization* aktor (ditulis satu kali atas nama aktor umum) dan *generalization* use case (skenario umum memuat perilaku bersama, skenario khusus memuat perilaku pembeda).
5. Menelaah 12 tabel skenario studi kasus Laboratorium (`LAB`) dari diagram kumulatif Pertemuan 4 serta menyusun 7 tabel skenario tugas akademis (`SIA`).

---

## 📖 3. Dasar Teori Ringkas

### **A. Pengertian Skenario Use Case**
Skenario Use Case adalah uraian langkah demi langkah interaksi antara aktor dan sistem untuk satu use case. Skenario menjawab *bagaimana* use case berjalan dari awal hingga selesai: aksi aktor, tanggapan sistem, titik alur bercabang, dan kondisi selesai. Skenario ditulis dalam format tabel dua kolom (*Kegiatan* dan *Respon sistem*).

### **B. Struktur Standar Tabel Skenario**
1. **Header Tabel:** Nama Use Case, Aktor, Tujuan, Deskripsi.
2. **Skenario Normal:** Rangkaian langkah utama saat alur berjalan ideal tanpa hambatan.
3. **Skenario Alternative:** Langkah cabang akibat ketidaksesuaian syarat, kesalahan isian, atau terpenuhinya kondisi *extend*. **Penomoran langkah MELANJUTKAN penomoran Skenario Normal** (tidak diulang dari angka 1).
4. **Skenario Akhir:** Kalimat penyataan kondisi selesai use case, mencakup jalur berhasil (*success state*) maupun jalur gagal (*failed state*).

### **C. Aturan Pemetaan Relasi Diagram ke Skenario**
| Relasi pada Diagram | Cara Penulisan dalam Tabel Skenario |
| :--- | :--- |
| `<<include>>` | Langkah rujukan wajib di Skenario Normal (menyebut nama & ID use case yang disertakan tanpa menyalin langkahnya). |
| `<<extend>>` | Cabang bersyarat pada Skenario Alternative yang dilengkapi `condition` dan `extension point` serta merujuk ke tabel use case tambahan. |
| **Generalization Aktor** | Skenario ditulis satu kali atas nama Aktor Umum (misal: *Peminjam* berlaku untuk *Mahasiswa* & *Dosen*). Catatan aktor khusus ditambahkan jika ada pembeda. |
| **Generalization Use Case** | Use case umum (*Kelola Data*) memuat perilaku bersama. Use case khusus (*Tambah*, *Ubah*, *Hapus*) hanya memuat perilaku pembeda dan merujuk ke use case umum. |
| **Collaboration** | **Tidak** dibuatkan langkah/tabel sendiri. Cukup dicantumkan pada catatan keterangan tabel use case yang direalisasikannya. |

---

## 📄 4. Matriks Artefak Skenario yang Dihasilkan

### **A. Lembar Telaah Studi Kasus Laboratorium (`LAB`) — 12 Use Case**

| ID Use Case | Nama Use Case | Aktor Utama | Relasi Pemetaan Utama | Keterangan Telaah Skenario |
| :---: | :--- | :--- | :--- | :--- |
| **LAB-UC01** | Lihat Ketersediaan Peralatan | Peminjam | Normal / Alternative | Menampilkan daftar peralatan; percabangan saat alat tidak tersedia. |
| **LAB-UC02** | Kelola Data Peralatan | Petugas Laboratorium | Generalization Parent | Skenario umum bersama untuk pengelolaan data peralatan. |
| **LAB-UC03** | Ajukan Peminjaman | Peminjam | Include UC04, Extend UC05, Collab LAB-CO01 | Acuan utama skenario; memuat include `LAB-UC04` dan extend `LAB-UC05`. |
| **LAB-UC04** | Periksa Ketersediaan | Peminjam | Include (by LAB-UC03) | Berjalan di dalam `LAB-UC03`; tidak ada interaksi langsung aktor. |
| **LAB-UC05** | Cetak Bukti Pengajuan | Mahasiswa | Extend (by LAB-UC03) | Extension point *Bukti pengajuan tersedia*, condition `[mahasiswa memilih cetak]`. |
| **LAB-UC06** | Proses Keputusan Peminjaman | Petugas Laboratorium | Normal / Alternative | Keputusan status pengajuan (*Disetujui* / *Ditolak*). |
| **LAB-UC07** | Lihat Laporan Peminjaman | Kepala Laboratorium | Berdiri Sendiri | Berdiri sendiri tanpa include/extend/generalization/collaboration. |
| **LAB-UC08** | Tambah Data Peralatan | Petugas Laboratorium | Generalization Child (UC02) | Perilaku khusus pembeda: Pengisian & penyimpanan data baru. |
| **LAB-UC09** | Ubah Data Peralatan | Petugas Laboratorium | Generalization Child (UC02) | Perilaku khusus pembeda: Perubahan data peralatan eksisting. |
| **LAB-UC10** | Hapus Data Peralatan | Petugas Laboratorium | Generalization Child (UC02) | Perilaku khusus pembeda: Penghapusan dengan syarat tidak ada pengajuan aktif. |
| **LAB-UC11** | Catat Pengembalian Peralatan | Petugas Laboratorium | Include UC12, Collab LAB-CO02 | Memuat include `LAB-UC12` (Periksa Kondisi Peralatan). |
| **LAB-UC12** | Periksa Kondisi Peralatan | Petugas Laboratorium | Include (by LAB-UC11) | Berjalan di dalam `LAB-UC11` untuk pencatatan kondisi fisik alat. |

---

### **B. Tugas Akademik Layanan Hasil Studi (`SIA`) — 7 Use Case**

| ID Use Case | Nama Use Case | Aktor Utama | Catatan Pemetaan & Ketentuan Skenario | Nama Berkas Artefak (`v01`) |
| :---: | :--- | :--- | :--- | :--- |
| **SIA-UC07** | Lihat Kalender Akademik | Civitas Akademika | Generalization Aktor: Ditulis 1x atas nama *Civitas Akademika* (Mahasiswa & Dosen). | `P05_2406002_SIA_skenario_v01.md` |
| **SIA-UC08** | Input Nilai Mata Kuliah | Dosen | Realisasi `SIA-CO01`. Prasyarat: Dosen pengampu; nilai di luar rentang ditolak. | `P05_2406002_SIA_skenario_v01.md` |
| **SIA-UC09** | Lihat KHS | Mahasiswa | Realisasi `SIA-CO02`. Menampilkan nilai yang telah dipublikasikan. | `P05_2406002_SIA_skenario_v01.md` |
| **SIA-UC10** | Kelola Data Mahasiswa | Admin Akademik | Generalization Parent: Skenario umum pengelolaan data mahasiswa. | `P05_2406002_SIA_skenario_v01.md` |
| **SIA-UC11** | Tambah Data Mahasiswa | Admin Akademik | Generalization Child (UC10): Perilaku pembeda penyimpanan mahasiswa baru. | `P05_2406002_SIA_skenario_v01.md` |
| **SIA-UC12** | Ubah Data Mahasiswa | Admin Akademik | Generalization Child (UC10): Perilaku pembeda pembaruan profil mahasiswa. | `P05_2406002_SIA_skenario_v01.md` |
| **SIA-UC13** | Hapus Data Mahasiswa | Admin Akademik | Generalization Child (UC10): Syarat hapus tidak memiliki data akademik aktif. | `P05_2406002_SIA_skenario_v01.md` |

---

## 📁 5. Struktur Workspace Pertemuan 05

```text
IFRWP5149_2406002_LabAlat/
├── 01_skenario/
│   ├── P05_2406002_LAB_telaah_skenario_v01.md   (Baru, Hasil Telaah LAB)
│   ├── P05_2406002_SIA_skenario_v01.md          (Baru, Tugas Skenario SIA)
│   ├── P04_LAB_skenario_v01.md                  (Arsip P04, tidak diubah)
│   └── P04_SIA_skenario_v01.md                  (Arsip P04, tidak diubah)
└── 04_model_analisis/
    └── P04/                                     (Diagram Acuan P04, tidak diubah)
        ├── LAB/P04_2406002_LAB_usecase_v01.drawio (.png)
        └── SIA/P04_2406002_SIA_usecase_v01.drawio (.png)
```

---

## 🔍 6. Checklist Quality Control Skenario

- [x] **Kelengkapan Field:** Seluruh baris (*Nama Use Case, Aktor, Tujuan, Deskripsi*) dan kolom (*Kegiatan, Respon sistem*) terisi lengkap.
- [x] **Prinsip Satu Aksi:** Setiap langkah memuat tepat satu aksi aktor atau satu respon sistem.
- [x] **Penomoran Berlanjut:** Penomoran Skenario Alternative melanjutkan nomor langkah Skenario Normal tanpa mengulang dari angka 1.
- [x] **Eksplisitas Data:** Menyebutkan nama field, nilai, dan status secara eksplisit (misal: status *Menunggu Keputusan*, tanggal pinjam).
- [x] **Pemetaan Include:** Ditulis sebagai langkah rujukan wajib di Skenario Normal.
- [x] **Pemetaan Extend:** Ditulis di Skenario Alternative dilengkapi `condition` dan `extension point`.
- [x] **Penerapan Generalization:** Aktor umum dikelompokkan; use case umum & khusus dipisahkan dengan jelas.
- [x] **Catatan Collaboration:** Collaboration dicantumkan di Keterangan Tabel tanpa membuat langkah sendiri.
- [x] **Skenario Akhir:** Menjelaskan kondisi selesai baik jalur sukses maupun jalur gagal.