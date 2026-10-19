# Skenario dan Keputusan Pemodelan SIA (Pertemuan 4)

**Versi:** v01  
**Kasus:** Sistem Informasi Akademik (SIA)  

---

## 1. Skenario Tugas
Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, *Input Nilai Mata Kuliah* dan *Lihat KHS*, ditunjukkan realisasinya oleh *collaboration* yang bersesuaian.

---

## 2. Identifikasi Aktor
| Aktor | Kedudukan | Tujuan terhadap Sistem |
| :--- | :--- | :--- |
| **Civitas Akademika** | Aktor Umum (*General*), Baru P04 | Peran umum bagi mahasiswa dan dosen. Mewariskan fungsi melihat kalender akademik. |
| **Mahasiswa** | Khusus dari Civitas Akademika, Tetap | Melihat kalender akademik (diwarisi), melihat jadwal kuliah, mengajukan KRS, mengunduh bukti KRS, dan melihat KHS. |
| **Dosen** | Khusus dari Civitas Akademika, Baru/Tetap | Melihat kalender akademik (diwarisi) dan menginput nilai mata kuliah yang diampu. |
| **Dosen Wali** | Aktor Tetap dari P03 | Memvalidasi dan memproses keputusan KRS mahasiswa bimbingan. |
| **Admin Akademik** | Aktor Tetap | Mengelola jadwal kuliah, mengelola data mahasiswa, dan memproses administrasi. |

---

## 3. Katalog Use Case Kumulatif SIA
| ID | Nama Use Case | Peran dalam Model | Sumber Kebutuhan |
| :--- | :--- | :--- | :--- |
| **SIA-UC01** | Lihat Jadwal Kuliah | Tetap P02 | SIA-R01 |
| **SIA-UC02** | Kelola Jadwal Kuliah | Tetap P02 | SIA-R02 |
| **SIA-UC03** | Ajukan KRS | Tetap P03; direalisasikan SIA-CO (P03) | SIA-R03 |
| **SIA-UC04** | Validasi KRS | Tetap P03; disertakan `<<include>>` oleh Ajukan KRS | SIA-R03 |
| **SIA-UC05** | Unduh Bukti Pengajuan KRS | Tetap P03; perluasan `<<extend>>` Ajukan KRS | SIA-R04 |
| **SIA-UC06** | Proses Keputusan KRS | Tetap P03 | SIA-R05, SIA-R06 |
| **SIA-UC07** | Lihat Kalender Akademik | Baru P04; fungsi aktor umum Civitas Akademika | SIA-R07 |
| **SIA-UC08** | Input Nilai Mata Kuliah | Baru P04; fungsi Dosen; direalisasikan SIA-CO01 | SIA-R08, SIA-R12 |
| **SIA-UC09** | Lihat KHS | Baru P04; fungsi Mahasiswa; direalisasikan SIA-CO02 | SIA-R09, SIA-R12 |
| **SIA-UC10** | Kelola Data Mahasiswa | Baru P04; use case UMUM bagi SIA-UC11 s.d. SIA-UC13 | SIA-R10, SIA-R11 |
| **SIA-UC11** | Tambah Data Mahasiswa | Baru P04; use case KHUSUS dari SIA-UC10 | SIA-R11 |
| **SIA-UC12** | Ubah Data Mahasiswa | Baru P04; use case KHUSUS dari SIA-UC10 | SIA-R11 |
| **SIA-UC13** | Hapus Data Mahasiswa | Baru P04; use case KHUSUS dari SIA-UC10 | SIA-R11 |

---

## 4. Keputusan Pemodelan SIA

### 4.1. Generalization Aktor
* **Keputusan:** `Mahasiswa` dan `Dosen` dispesifikasikan sebagai aktor khusus dari `Civitas Akademika`.
* **Alasan:** Keduanya berbagi fungsi yang sama, yaitu `Lihat Kalender Akademik` (`SIA-UC07`).
* **Aturan Diagram:** Asosiasi ke `SIA-UC07` digambar satu kali dari `Civitas Akademika`. Panah generalization segitiga kosong menunjuk ke `Civitas Akademika`.

### 4.2. Generalization Use Case
* **Keputusan:** `SIA-UC11` (Tambah), `SIA-UC12` (Ubah), dan `SIA-UC13` (Hapus) adalah bentuk khusus dari `SIA-UC10: Kelola Data Mahasiswa`.
* **Perilaku Pembeda:**
  * **Tambah Data Mahasiswa:** Menghasilkan data induk mahasiswa baru di sistem.
  * **Ubah Data Mahasiswa:** Menghasilkan pembaruan informasi profil/data mahasiswa.
  * **Hapus Data Mahasiswa:** Menghasilkan penghapusan data mahasiswa yang tidak lagi aktif.

### 4.3. Collaboration dan Realization
* **SIA-CO01 (Input Nilai Mata Kuliah):** Merealisasikan `SIA-UC08: Input Nilai Mata Kuliah`.
* **SIA-CO02 (Lihat KHS):** Merealisasikan `SIA-UC09: Lihat KHS`.