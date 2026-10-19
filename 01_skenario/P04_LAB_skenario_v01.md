# Skenario & Keputusan Pemodelan Laboratorium

## Identifikasi Aktor
| Aktor | Kedudukan | Tujuan Terhadap Sistem |
| :--- | :--- | :--- |
| Peminjam | Umum (General), Baru | Peran umum bagi peminjam peralatan. Mewariskan fungsi ke Mahasiswa dan Dosen. |
| Mahasiswa | Khusus dari Peminjam, Tetap | Melihat ketersediaan dan mengajukan peminjaman (warisan), serta mencetak bukti pengajuan (asosiasi khusus). |
| Dosen | Khusus dari Peminjam, Baru | Melihat ketersediaan dan mengajukan peminjaman (diwarisi dari Peminjam). |
| Petugas Laboratorium | Tetap P03 | Mengelola data peralatan, memproses keputusan peminjaman, dan mencatat pengembalian. |
| Kepala Laboratorium | Tetap P03 | Melihat laporan peminjaman. |

## Katalog Use Case Kumulatif
| ID | Nama Use Case | Peran dalam Model | Sumber Kebutuhan |
| :--- | :--- | :--- | :--- |
| LAB-UC01 | Lihat Ketersediaan Peralatan | Tetap P03; Fungsi aktor umum Peminjam | LAB-R01, LAB-R07 |
| LAB-UC02 | Kelola Data Peralatan | Tetap P03; Use case UMUM bagi LAB-UC08 s.d. LAB-UC10 | LAB-R02, LAB-R08 |
| LAB-UC03 | Ajukan Peminjaman | Tetap P03; Fungsi Peminjam; Direalisasikan LAB-CO01 | LAB-R03, LAB-R07, LAB-R11 |
| LAB-UC04 | Periksa Ketersediaan | Tetap P03; Perilaku disertakan (`<<include>>`) LAB-UC03 | LAB-R03 |
| LAB-UC05 | Cetak Bukti Pengajuan | Tetap P03; Perilaku tambahan (`<<extend>>`) ke LAB-UC03 | LAB-R04 |
| LAB-UC06 | Proses Keputusan Peminjaman | Tetap P03; Fungsi utama Petugas | LAB-R05 |
| LAB-UC07 | Lihat Laporan Peminjaman | Tetap P03; Fungsi utama Kepala Lab | LAB-R06 |
| LAB-UC08 | Tambah Data Peralatan | Baru P04; Use case KHUSUS dari LAB-UC02 | LAB-R08 |
| LAB-UC09 | Ubah Data Peralatan | Baru P04; Use case KHUSUS dari LAB-UC02 | LAB-R08 |
| LAB-UC10 | Hapus Data Peralatan | Baru P04; Use case KHUSUS dari LAB-UC02 | LAB-R08 |
| LAB-UC11 | Catat Pengembalian Peralatan | Baru P04; Fungsi Petugas; Direalisasikan LAB-CO02 | LAB-R09, LAB-R11 |
| LAB-UC12 | Periksa Kondisi Peralatan | Baru P04; Perilaku disertakan (`<<include>>`) LAB-UC11 | LAB-R10 |

## Alasan Pemodelan (Rational Decision)
1. Generalization Aktor: Mahasiswa dan Dosen adalah bentuk khusus dari Peminjam karena berbagi fungsi bersama. Asosiasi digambar 1 kali dari Peminjam.
2. Generalization Use Case: Tambah Data Peralatan, Ubah Data Peralatan, dan Hapus Data Peralatan adalah bentuk khusus dari Kelola Data Peralatan.
3. Collaboration & Realization: LAB-CO01 merealisasikan LAB-UC03 dan LAB-CO02 merealisasikan LAB-UC11.

## Use Case Description: LAB-UC11 Catat Pengembalian Peralatan
* ID dan Nama: LAB-UC11: Catat Pengembalian Peralatan
* Sumber Kebutuhan: LAB-R09 dan LAB-R10
* Tujuan: Pengembalian tercatat dan status peminjaman serta kondisi peralatan terbarui.
* Aktor Utama: Petugas Laboratorium
* Pemicu: Petugas memilih fungsi pencatatan pengembalian dan menentukan peminjaman yang akan dikembalikan.
* Prasyarat: Petugas telah terautentikasi; peminjaman terpilih berstatus Dipinjam.
* Pascakondisi Berhasil: Pengembalian tercatat dengan tanggal kembali dan kondisi peralatan; status peminjaman menjadi Selesai.
* Pascakondisi Gagal: Tidak ada pengembalian baru yang tercatat; status peminjaman tidak berubah.
* Include: LAB-UC12: Periksa Kondisi Peralatan
* Collaboration: LAB-CO02: Catat Pengembalian Peralatan

### Alur Utama
1. Petugas memilih peminjaman yang akan dikembalikan -> Sistem menampilkan data peminjaman terpilih dan statusnya.
2. Petugas mengonfirmasi alat yang kembali dan jumlahnya -> Sistem menampung konfirmasi petugas.
3. Sistem memeriksa status peminjaman harus Dipinjam.
4. Sistem menjalankan LAB-UC12: memeriksa dan mencatat kondisi peralatan.
5. Petugas menyimpan pencatatan pengembalian -> Menyimpan tanggal kembali dan kondisi; mengubah status peminjaman menjadi Selesai.
6. Petugas melihat konfirmasi -> Sistem menampilkan ringkasan pengembalian.

### Alur Alternatif
* A1: Status bukan Dipinjam (pada langkah 3): Sistem menolak pencatatan dan menampilkan status peminjaman saat ini. Pascakondisi gagal berlaku.
* A2: Kondisi Rusak Ringan atau Rusak Berat (pada langkah 4): Sistem tetap menyimpan pencatatan, menandai kondisi tersebut pada data peralatan, dan pengembalian tetap tercatat.
* A3: Jumlah alat yang kembali tidak sesuai (pada langkah 2): Sistem meminta petugas memeriksa kembali isian sebelum penyimpanan.