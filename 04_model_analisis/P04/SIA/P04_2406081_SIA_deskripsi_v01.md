<!-- SIA-UC08: Input Nilai Mata Kuliah (Deskripsi Lengkap) -->
<!-- =============================================================== -->
| Elemen | Isi |
|--------|-----|
| ID dan nama | SIA-UC08: Input Nilai Mata Kuliah |
| Sumber kebutuhan | SIA-R08 dan SIA-R12 |
| Tujuan | Nilai mata kuliah yang diampu dosen tersimpan di sistem dengan status belum dipublikasikan |
| Aktor utama | Dosen |
| Pemicu | Dosen memilih fungsi input nilai dan menentukan mata kuliah beserta mahasiswa yang akan dinilai setelah masa perkuliahan berakhir |
| Prasyarat | Dosen telah terautentikasi; dosen adalah pengampu mata kuliah yang dipilih; masa perkuliahan mata kuliah telah berakhir |
| Pascakondisi berhasil | Nilai tersimpan untuk mata kuliah dan mahasiswa terpilih dengan status belum dipublikasikan, sehingga belum tampil pada KHS |
| Pascakondisi gagal | Tidak ada nilai baru yang tersimpan; data nilai yang sudah ada tidak berubah |
| Collaboration | SIA-CO01: Input Nilai Mata Kuliah |
| Aturan bisnis | Hanya dosen pengampu yang dapat menginput nilai; nilai harus berada dalam rentang yang sah; nilai yang diinput belum terpublikasi |

<!-- Alur Utama SIA-UC08 -->
| Langkah | Tindakan dosen | Respons sistem |
|---------|----------------|----------------|
| 1 | Memilih mata kuliah yang diampu | Memeriksa bahwa dosen adalah pengampu; menampilkan daftar mahasiswa mata kuliah tersebut |
| 2 | Mengisi nilai tiap mahasiswa | Menampung isian nilai |
| 3 | Tidak ada | Memeriksa bahwa setiap nilai berada dalam rentang yang sah |
| 4 | Menyimpan nilai | Menyimpan nilai dengan status belum dipublikasikan |
| 5 | Melihat konfirmasi | Menampilkan ringkasan nilai yang tersimpan |

<!-- Alur Alternatif SIA-UC08 -->
- **A1: Dosen bukan pengampu (pada langkah 1):** sistem menolak akses input nilai untuk mata kuliah itu dan menampilkan pesan bahwa dosen bukan pengampu. Pascakondisi gagal berlaku; tidak ada nilai yang disimpan.
- **A2: Nilai di luar rentang yang sah (pada langkah 3):** sistem menolak nilai tersebut, menandai isian yang salah, dan meminta koreksi. Penyimpanan tidak dilakukan sampai semua nilai sah; bila dosen membatalkan, pascakondisi gagal berlaku.

<!-- =============================================================== -->
<!-- SIA-UC09: Lihat KHS (Deskripsi Ringkas) -->
<!-- =============================================================== -->
| Elemen | Isi |
|--------|-----|
| ID dan nama | SIA-UC09: Lihat KHS |
| Sumber kebutuhan | SIA-R09 dan SIA-R12 |
| Tujuan | Mahasiswa melihat hasil studi per semester |
| Aktor utama | Mahasiswa |
| Pemicu | Mahasiswa memilih fungsi lihat KHS dan menentukan semester |
| Prasyarat | Mahasiswa telah terautentikasi |
| Perilaku inti | Hanya nilai yang sudah dipublikasikan yang ditampilkan. Semester yang nilainya belum dipublikasikan tidak menampilkan nilai tersebut |
| Pascakondisi berhasil | KHS semester terpilih tampil dengan nilai terpublikasi |
| Pascakondisi gagal | KHS tidak tampil; tidak ada data yang berubah |
| Collaboration | SIA-CO02: Lihat KHS |

<!-- =============================================================== -->
<!-- Baris tambahan untuk hierarki SIA-UC10 (Generalization) -->
<!-- =============================================================== -->
| Use case | Baris Generalization |
|----------|----------------------|
| SIA-UC10 Kelola Data Mahasiswa | Umum bagi SIA-UC11, SIA-UC12, SIA-UC13 |
| SIA-UC11 / UC12 / UC13 | Khusus dari SIA-UC10 Kelola Data Mahasiswa |