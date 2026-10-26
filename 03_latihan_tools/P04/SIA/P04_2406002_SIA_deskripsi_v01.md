1. SIA-UC03: Ajukan KRS

| Bagian                    | Isi |
| ID dan Nama               | SIA-UC03 Ajukan KRS |
| Sumber Kebutuhan          | SIA-R03, SIA-R04, SIA-R05 |
| Tujuan                    | Mengirimkan draft pengajuan KRS yang valid untuk disetujui Dosen Wali |
| Aktor Utama               | Mahasiswa |
| Aktor Pendukung           | - |
| Pemicu                    | Mahasiswa memilih menu pengajuan KRS |
| Prasyarat                 | Mahasiswa telah terautentikasi dan periode pengisian KRS sedang aktif |
| Pascakondisi Berhasil     | Pengajuan KRS tersimpan dengan status "Menunggu persetujuan dosen wali" |
| Pascakondisi Gagal        | Pengajuan KRS tidak tersimpan di dalam sistem |
| Include                   | SIA-UC04 Validasi KRS |
| Extension Point           | Bukti KRS tersedia, pada langkah 6 |
| Extend                    | SIA-UC05 Unduh bukti pengajuan KRS jika [mahasiswa memilih unduh] |
| Aturan Bisnis/Asumsi      | Pengajuan yang tersimpan belum otomatis disetujui; batas SKS dan modul pembayaran di luar cakupan ini |

Alur Utama (SIA-UC03)
| Langkah | Tindakan Mahasiswa                    | Respons Sistem |
| 1       | Membuka menu pengajuan KRS            | Menampilkan daftar mata kuliah yang dapat dipilih |
| 2       | Memilih mata kuliah yang akan diambil | Menampung daftar pilihan mata kuliah |
| 3       | Mengirim pengajuan KRS                | Memeriksa kelengkapan pengisian |
| 4       | -                                     | Menjalankan **SIA-UC04 (Validasi KRS)** |
| 5       | -                                     | Jika validasi berhasil, menyimpan KRS dengan status "Menunggu persetujuan dosen wali" |
| 6       | Melihat konfirmasi penyimpanan        | Menampilkan status dan nomor pengajuan; mencapai *extension point* |
| 7       | Mengakhiri proses pengajuan           | Menutup halaman pengajuan KRS |

Alur Alternatif / Pengecualian (SIA-UC03)
4a. Validasi KRS Gagal (SIA-UC04 mengembalikan hasil tidak valid)**
  1. Sistem membatalkan proses penyimpanan pengajuan KRS.
  2. Sistem menampilkan pesan kesalahan detail (seperti benturan jadwal atau prasyarat mata kuliah belum terpenuhi).
  3. Mahasiswa kembali ke langkah 2 untuk menyesuaikan pilihan mata kuliah.


2. SIA-UC04: Validasi KRS

| Bagian                   | Isi |
| ID dan Nama              | SIA-UC04 Validasi KRS |
| Sumber Kebutuhan         | SIA-R04 |
| Tujuan                   | Memastikan pilihan mata kuliah memenuhi aturan prasyarat, kelengkapan, dan tidak bentrok jadwal |
| Aktor Utama              | Sistem (Perilaku Ter-include) |
| Aktor Pendukung          | Mahasiswa (Pemicu pemanggilan secara tidak langsung via SIA-UC03) |
| Pemicu                   | Dipanggil oleh use case SIA-UC03 (Ajukan KRS) pada langkah 4 |
| Prasyarat                | Data mata kuliah, prasyarat, dan jadwal kuliah sudah tersedia di sistem |
| Pascakondisi Berhasil    | Hasil validasi dinyatakan Valid/Berhasil |
| Pascakondisi Gagal       | Hasil validasi dinyatakan Tidak Valid/Gagal disertai daftar penyebab kegagalan |
| Aturan Bisnis/Asumsi     | Validasi memeriksa 3 kriteria: kelengkapan data, pemenuhan prasyarat mata kuliah, dan ketiadaan benturan jadwal |

Alur Utama (SIA-UC04)
| Langkah | Tindakan Aktor            | Respons Sistem |
| 1       | (Dipanggil dari SIA-UC03) | Membaca daftar mata kuliah yang dipilih mahasiswa |
| 2       | -                         | Memeriksa prasyarat dari setiap mata kuliah yang dipilih |
| 3       | -                         | Memeriksa potensi benturan jadwal antar mata kuliah yang dipilih |
| 4       | -                         | Mengembalikan status "Valid" ke use case pemanggil (SIA-UC03) |

Alur Alternatif / Pengecualian (SIA-UC04)
2a / 3a. Prasyarat Tidak Terpenuhi atau Jadwal Bentrok**
  1. Sistem mencatat jenis kesalahan (prasyarat belum lulus atau jam kuliah berbenturan).
  2. Sistem mengembalikan status "Tidak Valid" beserta rincian kesalahannya ke use case pemanggil (SIA-UC03).


3. SIA-UC05: Unduh Bukti Pengajuan KRS

| Bagian                     | Isi |
| ID dan Nama                | SIA-UC05 Unduh bukti pengajuan KRS |
| Sumber Kebutuhan           | SIA-R05 |
| Tujuan                     | Menghasilkan dan memberikan berkas bukti pengajuan KRS yang dapat diunduh mahasiswa |
| Aktor Utama                | Mahasiswa |
| Aktor Pendukung            | - |
| Pemicu                     | Mahasiswa memilih tombol/opsi unduh bukti pada tampilan konfirmasi |
| Prasyarat                  | Pengajuan KRS telah berhasil tersimpan dan mencapai *extension point* di SIA-UC03 |
| Pascakondisi Berhasil      | Berkas bukti pengajuan KRS berhasil diunduh oleh mahasiswa |
| Pascakondisi Gagal         | Berkas bukti pengajuan KRS gagal diunduh; data pengajuan KRS di sistem tetap tersimpan |
| Aturan Bisnis/Asumsi       | Pengunduhan bukti bersifat opsional dan tidak memengaruhi keberhasilan pengajuan KRS |

Alur Utama (SIA-UC05)
| Langkah | Tindakan Mahasiswa                         | Respons Sistem |
| 1       | Memilih opsi "Unduh Bukti" pada konfirmasi | Memproses pembuatan dokumen bukti pengajuan KRS |
| 2       | -                                          | Mengunduh berkas bukti pengajuan KRS ke perangkat mahasiswa |

Alur Alternatif / Pengecualian (SIA-UC05)
1a. Gagal Mengunduh / Gangguan Generasi Berkas**
  1. Sistem menampilkan pesan peringatan bahwa berkas bukti gagal dibuat/diunduh.
  2. Mahasiswa dapat mencoba mengunduh kembali tanpa membatalkan pengajuan KRS yang sudah tersimpan.

4. SIA-UC06: Proses Keputusan KRS

| Bagian                 | Isi |
| ID dan Nama            | SIA-UC06 Proses keputusan KRS |
| Sumber Kebutuhan       | SIA-R06 |
| Tujuan                 | Menetapkan status persetujuan atau penolakan pada draf pengajuan KRS mahasiswa bimbingan |
| Aktor Utama            | Dosen Wali |
| Aktor Pendukung        | - |
| Pemicu                 | Dosen Wali memilih daftar pengajuan KRS mahasiswa bimbingan |
| Prasyarat              | Dosen Wali telah terautentikasi dan terdapat pengajuan KRS berstatus "Menunggu persetujuan dosen wali" |
| Pascakondisi Berhasil  | Status KRS berubah menjadi "Disetujui" atau "Ditolak" beserta catatan keputusan yang tersimpan |
| Pascakondisi Gagal     | Status pengajuan KRS tidak mengalami perubahan |
| Aturan Bisnis/Asumsi   | Dosen Wali wajib memberikan catatan keputusan, terutama jika melakukan penolakan |

Alur Utama (SIA-UC06)
| Langkah | Tindakan Dosen Wali                               | Respons Sistem |
| 1       | Membuka menu persetujuan KRS                      | Menampilkan daftar mahasiswa bimbingan yang mengajukan KRS |
| 2       | Memilih salah satu pengajuan KRS                  | Menampilkan rincian mata kuliah yang diajukan mahasiswa |
| 3       | Menyetujui pengajuan KRS dan mengisikan catatan   | Menampung status persetujuan dan catatan Dosen Wali |
| 4       | Menyimpan keputusan                               | Memperbarui status KRS menjadi "Disetujui" dan menyimpan catatan keputusan |
| 5       | -                                                 | Menampilkan konfirmasi bahwa keputusan berhasil disimpan |

Alur Alternatif / Pengecualian (SIA-UC06)
3a. Dosen Wali Menolak Pengajuan KRS**
  1. Dosen Wali memilih opsi "Tolak" dan wajib mengisikan alasan/catatan penolakan.
  2. Dosen Wali menyimpan keputusan.
  3. Sistem memperbarui status KRS menjadi "Ditolak" beserta catatan alasannya.
  4. Sistem menampilkan konfirmasi bahwa keputusan penolakan berhasil disimpan.