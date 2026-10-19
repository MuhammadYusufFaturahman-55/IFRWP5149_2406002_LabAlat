# Dokumentasi Kebutuhan Sistem Informasi Akademik (Pertemuan 4)

## Kebutuhan Kumulatif
* SIA-R01 s.d. SIA-R02: Mengacu pada Jobsheet Pertemuan 2 (Jadwal Kuliah).
* SIA-R03 s.d. SIA-R06: Mengacu pada Jobsheet Pertemuan 3 (Pengajuan KRS).
* SIA-R07: Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik.
* SIA-R08: Dosen dapat menginput nilai mata kuliah yang diampunya.
* SIA-R09: Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan.
* SIA-R10: Admin Akademik dapat mengelola data mahasiswa.
* SIA-R11: Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa.
* SIA-R12: Model menunjukkan collaboration yang merealisasikan Input Nilai Mata Kuliah dan Lihat KHS.

## Batas dan Asumsi
1. Kalender akademik adalah agenda resmi institusi (awal semester, ujian, dll.), bukan jadwal perkuliahan harian.
2. Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut.
3. KHS hanya menampilkan nilai yang statusnya telah dipublikasikan secara resmi.
4. Hapus Data Mahasiswa hanya diizinkan untuk data mahasiswa yang tidak memiliki rekam akademik aktif.

## Hasil Pengujian Konsistensi Situasi Khusus
* Situasi A (Mahasiswa melihat kalender akademik tanpa asosiasi langsung): Tetap valid menurut UML karena Mahasiswa mewarisi seluruh asosiasi milik aktor umum Civitas Akademika.
* Situasi B (Dosen bukan pengampu mencoba menginput nilai): Sistem menolak akses input nilai pada tahap verifikasi prasyarat otoritas dosen pengampu.
* Situasi C (Admin menghapus data mahasiswa aktif): Sistem membatalkan proses hapus data dan menampilkan pesan kesalahan aturan bisnis.