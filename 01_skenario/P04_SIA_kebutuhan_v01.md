<!-- Skenario -->
Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah, mengubah, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration.

<!-- Tabel Kebutuhan -->
| ID | Kebutuhan |
|----|-----------|
| SIA-R01, SIA-R02 | Kebutuhan Pertemuan 2 (jadwal kuliah), tetap berlaku |
| SIA-R03 s.d. SIA-R06 | Kebutuhan Pertemuan 3 (pengajuan KRS), tetap berlaku |
| SIA-R07 | Mahasiswa dan Dosen, sebagai Civitas Akademika, dapat melihat kalender akademik. |
| SIA-R08 | Dosen dapat menginput nilai mata kuliah yang diampunya. |
| SIA-R09 | Mahasiswa dapat melihat KHS untuk semester yang nilainya sudah dipublikasikan. |
| SIA-R10 | Admin Akademik dapat mengelola data mahasiswa. |
| SIA-R11 | Pengelolaan data mahasiswa terdiri dari tiga bentuk khusus: tambah, ubah, dan hapus data mahasiswa. |
| SIA-R12 | Model menunjukkan collaboration yang merealisasikan Input Nilai Mata Kuliah dan Lihat KHS. |

<!-- Batas dan Asumsi -->
- Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01/R02 (P2) dan SIA-R03 s.d. SIA-R06 (P3) tetap berbeda identitas.
- Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
- Kalender akademik adalah agenda resmi institusi (awal semester, batas KRS, masa ujian, dan sejenisnya), bukan jadwal kuliah P2.
- Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data akademik aktif (ketentuan fiktif untuk latihan).
- Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif P3. Pembayaran dan perancangan basis data di luar tugas ini.