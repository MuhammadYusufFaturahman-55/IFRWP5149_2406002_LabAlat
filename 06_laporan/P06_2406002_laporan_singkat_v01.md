# LAPORAN SINGKAT PRAKTIKUM
**PERTEMUAN 06: ACTIVITY DIAGRAM — DARI SKENARIO KE ALUR AKTIVITAS**

**Mata Kuliah:** Praktikum Analisis & Desain Berorientasi Objek (IFRWP5149)  
**Program Studi:** S1 Teknik Informatika — Institut Teknologi Garut  

---

## 📌 1. Identitas Mahasiswa

| Field | Detail Informasi |
| :--- | :--- |
| **Nama Lengkap** | Muhammad Yusuf Faturahman |
| **NIM** | `2406002` |
| **Kelas** | Informatika A |
| **Dosen / Instruktur** | Tim Dosen Analisis & Desain Berorientasi Objek |
| **Kakas Pemodelan** | Draw.io / VS Code / PlantUML |
| **Nama Berkas Dokumen** | `P06_2406002_laporan_singkat_v01.md` |

---

## 🎯 2. Tujuan Praktikum

Setelah menyelesaikan Praktikum Pertemuan 06, mahasiswa mampu:
1. Menyusun alur utama Activity Diagram dari Skenario Normal pada tabel skenario Pertemuan 05, dengan tepat satu *initial node*, urutan *action* berurutan, dan tepat satu *activity final node*.
2. Mengubah Skenario Alternative menjadi cabang *decision* dengan *guard* yang sah, lalu mengembalikannya melalui *merge* atau mengakhirinya pada jalur akhir yang jelas.
3. Menggunakan pasangan *fork* dan *join* untuk memodelkan dua atau lebih proses yang berjalan secara paralel.
4. Mengelompokkan setiap *action* ke dalam *swimlane* (partisi aktivitas) yang sesuai dengan aktor atau sistem pelakunya.
5. Menelusurkan setiap *action* pada Activity Diagram ke langkah tabel skenario Pertemuan 05.

---

## 📖 3. Dasar Teori Ringkas

Activity Diagram adalah diagram UML yang memodelkan alur kegiatan (*workflow*) sebuah proses bisnis atau use case. Unsur-unsur utama pemodelan menurut spesifikasi OMG UML 2.5.1 mencakup:

* **Initial Node:** Titik awal alur eksekusi (tepat 1 per diagram).
* **Action:** Langkah kegiatan tunggal yang ditulis menggunakan kata kerja dan objek.
* **Control Flow:** Panah penunjuk arah urutan eksekusi *action*.
* **Decision & Merge:** *Decision* membagi alur berdasarkan syarat (*guard* `[...]`), sedangkan *Merge* menggabungkan kembali cabang-cabang ke alur utama.
* **Fork & Join:** *Fork* membagi satu alur menjadi beberapa alur paralel, dan *Join* menyatukan kembali alur paralel setelah semua alur selesai.
* **Activity Final Node:** Titik akhir penutupan alur.
* **Swimlane (Partisi):** Mengelompokkan *action* berdasarkan penanggung jawabnya (Aktor / Sistem).

---

## 📄 4. Matriks Artefak Activity Diagram yang Dihasilkan

### A. Studi Kasus Laboratorium (`LAB`)

| No | ID Use Case | Nama Activity Diagram | Swimlane yang Digunakan | Unsur Khusus / Catatan Pemodelan | Nama Berkas Artefak (`v01`) |
| :---: | :---: | :--- | :--- | :--- | :--- |
| 1 | `LAB-UC01` | Activity Lihat Ketersediaan Peralatan | Peminjam, Sistem | Percabangan *decision* jika peralatan tidak tersedia. | `P06_2406002_LAB_activity_lihat_ketersediaan_v01.drawio` |
| 2 | `LAB-UC02` | Activity Kelola Data Peralatan | Petugas Laboratorium, Sistem | Memuat 3 varian: Tambah (`UC08`), Ubah (`UC09`), Hapus (`UC10`) beserta validasi syarat hapus. | `P06_2406002_LAB_activity_kelola_data_v01.drawio` |
| 3 | `LAB-UC03` | Activity Peminjaman | Mahasiswa, Sistem, Petugas Lab | Memuat *include* `LAB-UC04` (Periksa Ketersediaan) & *extend* `LAB-UC05` (Cetak Bukti). | `P06_2406002_LAB_activity_peminjaman_v01.drawio` |
| 4 | `LAB-UC05` | Activity Cetak Bukti Pengajuan | Mahasiswa, Sistem | Perilaku *extend* mandiri saat status pengajuan *Menunggu Keputusan*. | `P06_2406002_LAB_activity_cetak_bukti_v01.drawio` |
| 5 | `LAB-UC06` | Activity Proses Keputusan Peminjaman | Petugas Laboratorium, Sistem | Tugas Mandiri: Penetapan persetujuan/penolakan dan pembaruan status sistem. | `P06_2406002_LAB_activity_keputusan_v01.drawio` |
| 6 | `LAB-UC11` | Activity Pengembalian Peralatan | Mahasiswa, Petugas Lab, Sistem | Menggunakan **Fork & Join** untuk pemeriksaan fisik (`UC12`) & kelengkapan aksesori secara paralel. | `P06_2406002_LAB_activity_pengembalian_v01.drawio` |
| 7 | `LAB-UC07` | Activity Lihat Laporan Peminjaman | Kepala Laboratorium, Sistem | Menampilkan laporan berdasarkan periode yang dipilih tanpa fitur ekspor tambahan. | `P06_2406002_LAB_activity_laporan_v01.drawio` |

---

### B. Tugas Akademik Sistem Informasi Akademik (`SIA`)

| ID Use Case | Nama Activity Diagram | Swimlane yang Digunakan | Unsur Wajib yang Terpenuhi | Nama Berkas Artefak (`v01`) |
| :---: | :--- | :--- | :--- | :--- |
| `SIA-UC08` & `SIA-UC09` | Activity Input Nilai Sampai Lihat KHS | Dosen, Sistem, Admin Akademik, Mahasiswa | 1. 4 Swimlane Aktor lengkap.<br>2. *Decision* kelengkapan nilai oleh Dosen.<br>3. Pasangan **Fork & Join** penerbitan KHS & notifikasi. | `P06_2406002_SIA_activity_v01.drawio` |

---

## 📝 5. Catatan Evaluasi Tugas Mandiri (LAB-UC06)

Sesuai instruksi Langkah 10 pada Jobsheet, penyusunan `Activity Diagram Proses Keputusan Peminjaman` (`LAB-UC06`) dilakukan secara mandiri sebelum dibandingkan dengan berkas acuan.

### Log Perbandingan & Perbaikan:
1. **Pemeriksaan Awal:** Alur utama penetapan keputusan persetujuan dan penolakan sudah sesuai dengan skenario Pertemuan 05.
2. **Evaluasi Decision Pengajuan:** Ditambahkan titik percabangan *decision* pertama `Pengajuan dapat diproses?` dengan *guard* `[tidak dapat diproses]` untuk menangani kondisi pengajuan yang sudah tidak valid/berubah status.
3. **Penyelarasan Status:** Memastikan *action* perubahan status oleh *Sistem* menggunakan terminologi resmi yaitu `Disetujui` dan `Ditolak`.
4. **Verifikasi Swimlane:** Menghapus swimlane Mahasiswa dari diagram ini karena pada skenario `LAB-UC06` mahasiswa bersifat pasif dan tidak melakukan tindakan langsung.

---

## 📁 6. Struktur Repositori & Workspace Tugas

Seluruh berkas sumber pemodelan (`.drawio`) dan ekspor gambar (`.png`) disimpan pada struktur folder workspace sebagai berikut:

```text
IFRWP5149_2406002_LabAlat/
├── README.md
├── P06_2406002_laporan_singkat_v01.md
└── 04_model_analisis/
    └── P06/
        ├── LAB/
        │   ├── P06_2406002_LAB_activity_lihat_ketersediaan_v01.drawio (.png)
        │   ├── P06_2406002_LAB_activity_kelola_data_v01.drawio (.png)
        │   ├── P06_2406002_LAB_activity_peminjaman_v01.drawio (.png)
        │   ├── P06_2406002_LAB_activity_cetak_bukti_v01.drawio (.png)
        │   ├── P06_2406002_LAB_activity_keputusan_v01.drawio (.png)
        │   ├── P06_2406002_LAB_activity_pengembalian_v01.drawio (.png)
        │   └── P06_2406002_LAB_activity_laporan_v01.drawio (.png)
        └── SIA/
            └── P06_2406002_SIA_activity_v01.drawio (.png)
```

---

## ✅ 7. Checklist Quality Control (Penilaian Mandiri)

- [x] Tepat satu *initial node* dan minimal satu *activity final node* di setiap diagram.
- [x] Setiap *decision* memiliki *guard* dalam kurung siku `[...]` yang saling lepas pada seluruh alur keluar.
- [x] Setiap cabang percabangan disatukan kembali menggunakan *merge* atau bermuara ke *final node*.
- [x] Pasangan *fork* selalu disatukan kembali oleh *join* untuk proses paralel (bukan *merge*).
- [x] Setiap *action* berada pada *swimlane* yang tepat sesuai aktor/sistem pelakunya pada skenario P05.
- [x] Setiap *action* tertelusur ke tabel skenario P05 dengan penamaan kata kerja + objek.
- [x] Action *Periksa kelengkapan aksesori peralatan* pada `LAB-UC11` telah diberi label keterangan `(unsur proses baru)`.
- [x] Penamaan berkas sumber `.drawio` dan gambar ekspor `.png` konsisten menggunakan `v01`.
- [x] Berkas pertemuan sebelumnya (P03, P04, P05) tetap dipertahankan dan tidak ditimpa.

---
