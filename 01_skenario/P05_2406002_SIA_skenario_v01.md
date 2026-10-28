# TABEL SKENARIO USE CASE SIA (LAYANAN HASIL STUDI)
**Mata Kuliah:** Praktikum Analisis dan Desain Berorientasi Objek[cite: 1]  
**Pertemuan:** 5 (Skenario Use Case: Dari Diagram ke Langkah Kegiatan)[cite: 1]  
**Nama Mahasiswa:** <NAMA_MAHASISWA>  
**NIM:** <NIM>  
**Nama Berkas:** P05_<NIM>_SIA_skenario_v01.md[cite: 7, 20]  

---

## Tabel 5.15 Skenario Use Case SIA-UC07 Lihat Kalender Akademik

| Field | Isi |
|---|---|
| **Nama use case** | SIA-UC07 Lihat Kalender Akademik[cite: 17] |
| **Aktor** | Civitas Akademika (berlaku untuk Mahasiswa dan Dosen)[cite: 17, 18] |
| **Tujuan** | Civitas Akademika dapat melihat jadwal kegiatan akademik pada semester aktif[cite: 17] |
| **Deskripsi** | Civitas Akademika membuka fungsi kalender akademik dan sistem menampilkan daftar kegiatan akademik beserta tanggal pelaksanaannya[cite: 17] |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Civitas Akademika membuka fungsi Lihat Kalender Akademik | 2. Sistem menampilkan daftar kegiatan akademik beserta tanggal pelaksanaannya untuk semester aktif |
| **Skenario Alternative** | |
| 3. Kalender akademik semester aktif belum dipublikasikan (cabang dari langkah 2) | 4. Sistem menampilkan pesan bahwa kalender akademik belum tersedia |
| **Skenario Akhir** | Use case selesai jika daftar kegiatan kalender akademik ditampilkan; jika belum dipublikasikan, use case selesai dengan pesan tersebut. |

*Keterangan: Ditulis satu kali atas nama Civitas Akademika sebagai aktor umum; Mahasiswa dan Dosen mewarisi use case ini[cite: 17, 18].*

---

## Tabel 5.16 Skenario Use Case SIA-UC08 Input Nilai Mata Kuliah

| Field | Isi |
|---|---|
| **Nama use case** | SIA-UC08 Input Nilai Mata Kuliah[cite: 17] |
| **Aktor** | Dosen[cite: 17] |
| **Tujuan** | Dosen dapat memasukkan dan menyimpan nilai mata kuliah yang diampunya ke dalam sistem[cite: 17] |
| **Deskripsi** | Dosen memilih mata kuliah yang diampu, mengisi nilai mahasiswa, dan menyimpan data nilai. Prasyarat: dosen merupakan pengampu mata kuliah tersebut[cite: 17, 18] |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Dosen memilih mata kuliah yang diampu dan membuka daftar mahasiswa | 2. Sistem memeriksa hak akses dosen pengampu dan menampilkan daftar mahasiswa peserta mata kuliah |
| 3. Dosen mengisi nilai untuk masing-masing mahasiswa | 4. Sistem memeriksa format dan rentang nilai yang dimasukkan (0-100 atau A-E) |
| 5. Dosen menyimpan data nilai | 6. Sistem menyimpan data nilai mahasiswa dan menampilkan konfirmasi keberhasilan penyimpanan |
| **Skenario Alternative** | |
| 7. Dosen bukan pengampu mata kuliah tersebut (cabang dari langkah 2) | 8. Sistem menolak akses dan menampilkan pesan bahwa dosen tidak berhak menginput nilai mata kuliah tersebut |
| 9. Nilai yang dimasukkan di luar rentang yang sah atau format tidak valid (cabang dari langkah 4) | 10. Sistem menolak penyimpanan dan meminta dosen memperbaiki isian nilai[cite: 17] |
| **Skenario Akhir** | Use case selesai jika data nilai tersimpan; jika dosen bukan pengampu atau nilai tidak sah, data nilai tidak tersimpan[cite: 17]. |

*Keterangan: Use case ini direalisasikan oleh collaboration SIA-CO01 Input Nilai[cite: 17, 18]. Collaboration tersebut tidak mempunyai langkah kegiatan pada tabel ini[cite: 5, 18, 19].*

---

## Tabel 5.17 Skenario Use Case SIA-UC09 Lihat KHS

| Field | Isi |
|---|---|
| **Nama use case** | SIA-UC09 Lihat KHS[cite: 17] |
| **Aktor** | Mahasiswa[cite: 17] |
| **Tujuan** | Mahasiswa dapat melihat Kartu Hasil Studi (KHS) untuk semester yang dipilih[cite: 17] |
| **Deskripsi** | Mahasiswa memilih semester dan melihat daftar nilai mata kuliah yang telah dipublikasikan[cite: 17, 18] |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Mahasiswa membuka fungsi Lihat KHS dan memilih semester | 2. Sistem menampilkan daftar nilai mata kuliah yang sudah dipublikasikan pada semester tersebut[cite: 17, 18] |
| **Skenario Alternative** | |
| 3. Belum ada nilai yang dipublikasikan pada semester yang dipilih (cabang dari langkah 2) | 4. Sistem menampilkan pesan bahwa nilai KHS untuk semester tersebut belum dipublikasikan[cite: 17, 18] |
| **Skenario Akhir** | Use case selesai jika KHS semester terpilih ditampilkan; jika belum dipublikasikan, use case selesai dengan pesan tersebut. |

*Keterangan: Use case ini direalisasikan oleh collaboration SIA-CO02 Lihat KHS[cite: 17, 18]. Collaboration tersebut tidak mempunyai langkah kegiatan pada tabel ini[cite: 5, 18, 19].*

---

## Tabel 5.18 Skenario Use Case SIA-UC10 Kelola Data Mahasiswa

| Field | Isi |
|---|---|
| **Nama use case** | SIA-UC10 Kelola Data Mahasiswa[cite: 17] |
| **Aktor** | Admin Akademik[cite: 17] |
| **Tujuan** | Data mahasiswa terkelola melalui satu fungsi pengelolaan bersama[cite: 17] |
| **Deskripsi** | Admin membuka fungsi pengelolaan data mahasiswa, memilih bentuk pengelolaan, dan menyimpan perubahan. Bentuk tambah, ubah, dan hapus dijabarkan pada tabel khususnya masing-masing[cite: 17, 18] |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Kelola Data Mahasiswa | 2. Sistem menampilkan daftar data mahasiswa |
| 3. Admin Akademik memilih bentuk pengelolaan, yaitu tambah, ubah, atau hapus | 4. Sistem menampilkan formulir sesuai bentuk pengelolaan yang dipilih |
| 5. Admin Akademik mengisi atau mengonfirmasi data | 6. Sistem memeriksa kelengkapan dan keabsahan data mahasiswa |
| 7. Admin Akademik menyimpan perubahan | 8. Sistem menyimpan perubahan dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 9. Data mahasiswa tidak lengkap atau tidak sah (cabang dari langkah 6) | 10. Sistem menolak penyimpanan dan menampilkan pesan kesalahan data |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa tersimpan; jika data tidak lengkap atau tidak sah, perubahan tidak tersimpan. |

*Keterangan: Use case umum (parent) untuk SIA-UC11, SIA-UC12, dan SIA-UC13[cite: 5, 17, 18].*

---

## Tabel 5.19 Skenario Use Case SIA-UC11 Tambah Data Mahasiswa

| Field | Isi |
|---|---|
| **Nama use case** | SIA-UC11 Tambah Data Mahasiswa[cite: 17] |
| **Aktor** | Admin Akademik[cite: 17] |
| **Tujuan** | Data mahasiswa baru tersimpan sebagai bentuk khusus dari pengelolaan data mahasiswa[cite: 17] |
| **Deskripsi** | Admin mengisi data mahasiswa baru dan menyimpan data tersebut; langkah bersama mengikuti Tabel skenario SIA-UC10[cite: 17, 18] |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Admin Akademik membuka fungsi Tambah Data Mahasiswa | 2. Sistem menampilkan formulir data mahasiswa baru |
| 3. Admin Akademik mengisi data mahasiswa baru (NIM, Nama, Prodi, Angkatan) | 4. Sistem memeriksa kelengkapan data dan keunikan NIM |
| 5. Admin Akademik menyimpan data | 6. Sistem menyimpan data mahasiswa baru dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 7. NIM sudah terdaftar atau data tidak lengkap (cabang dari langkah 4) | 8. Sistem menolak penyimpanan dan menampilkan pesan kesalahan |
| **Skenario Akhir** | Use case selesai jika data mahasiswa baru tersimpan; jika NIM ganda atau data tidak lengkap, data tidak tersimpan[cite: 17]. |

*Keterangan: Use case khusus dari SIA-UC10 Kelola Data Mahasiswa[cite: 17, 18]. Perilaku pembeda: data mahasiswa baru tersimpan[cite: 17, 18]. Langkah bersama mengikuti Tabel skenario SIA-UC10[cite: 5, 17, 18].*

---

## Tabel 5.20 Skenario Use Case SIA-UC12 Ubah Data Mahasiswa

| Field | Isi |
|---|---|
| **Nama use case** | SIA-UC12 Ubah Data Mahasiswa[cite: 17] |
| **Aktor** | Admin Akademik[cite: 17] |
| **Tujuan** | Data mahasiswa berubah sebagai bentuk khusus dari pengelolaan data mahasiswa[cite: 17] |
| **Deskripsi** | Admin memilih data mahasiswa, mengubah datanya, dan menyimpan perubahan; langkah bersama mengikuti Tabel skenario SIA-UC10[cite: 17, 18] |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Admin Akademik memilih data mahasiswa yang akan diubah | 2. Sistem menampilkan data mahasiswa saat ini |
| 3. Admin Akademik mengubah data mahasiswa | 4. Sistem memeriksa perubahan data |
| 5. Admin Akademik menyimpan perubahan | 6. Sistem menyimpan data yang diubah dan menampilkan konfirmasi |
| **Skenario Alternative** | |
| 7. Data mahasiswa tidak ditemukan (cabang dari langkah 2) | 8. Sistem menampilkan pesan data mahasiswa tidak ditemukan |
| **Skenario Akhir** | Use case selesai jika perubahan data mahasiswa tersimpan; jika data tidak ditemukan, perubahan tidak tersimpan[cite: 17]. |

*Keterangan: Use case khusus dari SIA-UC10 Kelola Data Mahasiswa[cite: 17, 18]. Perilaku pembeda: data mahasiswa berubah[cite: 17, 18]. Langkah bersama mengikuti Tabel skenario SIA-UC10[cite: 5, 17, 18].*

---

## Tabel 5.21 Skenario Use Case SIA-UC13 Hapus Data Mahasiswa

| Field | Isi |
|---|---|
| **Nama use case** | SIA-UC13 Hapus Data Mahasiswa[cite: 17] |
| **Aktor** | Admin Akademik[cite: 17] |
| **Tujuan** | Data mahasiswa terhapus sebagai bentuk khusus dari pengelolaan data mahasiswa[cite: 17] |
| **Deskripsi** | Admin memilih data mahasiswa, mengonfirmasi penghapusan, dan sistem menghapus data tersebut; langkah bersama mengikuti Tabel skenario SIA-UC10[cite: 17, 18] |

| Kegiatan | Respon sistem |
|---|---|
| **Skenario Normal** | |
| 1. Admin Akademik memilih data mahasiswa yang akan dihapus | 2. Sistem memeriksa mahasiswa tidak memiliki data akademik aktif (KRS/KHS/Nilai aktif)[cite: 17, 18] |
| 3. Admin Akademik mengonfirmasi penghapusan | 4. Sistem menghapus data mahasiswa dan menampilkan konfirmasi penghapusan |
| **Skenario Alternative** | |
| 5. Mahasiswa masih memiliki data akademik aktif (cabang dari langkah 2) | 6. Sistem menolak penghapusan dan menampilkan pesan bahwa data mahasiswa masih aktif[cite: 17, 18] |
| **Skenario Akhir** | Use case selesai jika data mahasiswa terhapus; jika mahasiswa memiliki data akademik aktif, data tidak terhapus[cite: 17, 18]. |

*Keterangan: Use case khusus dari SIA-UC10 Kelola Data Mahasiswa[cite: 17, 18]. Perilaku pembeda: data mahasiswa terhapus, dengan syarat tidak ada data akademik aktif[cite: 17, 18]. Langkah bersama mengikuti Tabel skenario SIA-UC10[cite: 5, 17, 18].*