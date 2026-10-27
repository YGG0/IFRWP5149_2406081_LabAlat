<!-- Tabel Aktor dan Generalization Aktor -->
| Aktor | Kedudukan | Tujuan terhadap sistem |
|-------|-----------|------------------------|
| Civitas Akademika | Umum, baru | Peran umum warga akademik; mewariskan Lihat Kalender Akademik |
| Mahasiswa | Khusus dari Civitas Akademika, tetap dari P3 | Melihat kalender (diwarisi), lalu melihat KHS dan fungsi lama P2/P3 sebagai asosiasi sendiri |
| Dosen | Khusus dari Civitas Akademika, baru | Melihat kalender (diwarisi), lalu menginput nilai |
| Admin Akademik | Tetap dari P2/P3 | Mengelola jadwal kuliah dan mengelola data mahasiswa |
| Dosen Wali | Tetap dari P3 | Memproses keputusan KRS |

<!-- Keputusan Pemodelan Generalization Aktor -->
1. Mahasiswa dan Dosen adalah bentuk khusus dari Civitas Akademika. Alasan: keduanya memakai fungsi yang sama persis (melihat kalender akademik), kesamaan itu berlaku selama sistem dikembangkan karena kalender adalah agenda institusi, dan nama peran umum membuat diagram lebih jelas. Ketiga pertanyaan keputusan terjawab ya.
2. Asosiasi ke SIA-UC07 digambar satu kali, dari Civitas Akademika. Tidak ada garis yang sama dari Mahasiswa maupun Dosen.
3. Fungsi yang bukan milik bersama tetap menjadi asosiasi langsung aktor khusus: Mahasiswa ke SIA-UC09, Dosen ke SIA-UC08, dan asosiasi lama Mahasiswa dari P3 tidak dipindahkan atau dihapus.
4. Segitiga kosong menempel pada Civitas Akademika. Karena Civitas Akademika digambar di tengah, panah Mahasiswa mengarah ke bawah dan panah Dosen mengarah ke atas, keduanya berakhir pada Civitas Akademika.
5. Dosen Wali tidak dijadikan bentuk khusus dari Dosen, karena skenario tidak menyatakan hubungan itu dan jobsheet menyebutnya tetap dari pertemuan sebelumnya.

<!-- Katalog Use Case Gabungan -->
| ID | Nama use case | Aktor terkait | Sumber kebutuhan | Status |
|----|---------------|---------------|------------------|--------|
| SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa (cek P03) | SIA-R01 (P2) | Tetap |
| SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik (cek P03) | SIA-R02 (P2) | Tetap |
| SIA-UC03 | Ajukan KRS | Mahasiswa; menyertakan SIA-UC04 | SIA-R03 (P3) | Tetap |
| SIA-UC04 | Validasi KRS | (dimasukkan oleh SIA-UC03) | SIA-R03 (P3) | Tetap |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa; «extend» SIA-UC03 | SIA-R04 (P3) | Tetap |
| SIA-UC06 | Proses Keputusan KRS | Dosen Wali | SIA-R05/R06 (P3) | Tetap |
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika (diwarisi Mahasiswa dan Dosen) | SIA-R07 | Baru |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen; direalisasikan SIA-CO01 | SIA-R08, SIA-R12 | Baru |
| SIA-UC09 | Lihat KHS | Mahasiswa; direalisasikan SIA-CO02 | SIA-R09, SIA-R12 | Baru |
| SIA-UC10 | Kelola Data Mahasiswa (umum) | Admin Akademik | SIA-R10, SIA-R11 | Baru |
| SIA-UC11 | Tambah Data Mahasiswa | Admin Akademik (via SIA-UC10); khusus SIA-UC10 | SIA-R11 | Baru |
| SIA-UC12 | Ubah Data Mahasiswa | Admin Akademik (via SIA-UC10); khusus SIA-UC10 | SIA-R11 | Baru |
| SIA-UC13 | Hapus Data Mahasiswa | Admin Akademik (via SIA-UC10); khusus SIA-UC10 | SIA-R11 | Baru |

<!-- Generalization Use Case -->
| Use case khusus | Perilaku pembeda (satu kalimat) |
|-----------------|---------------------------------|
| SIA-UC11 Tambah Data Mahasiswa | Menghasilkan data mahasiswa baru yang tersimpan. |
| SIA-UC12 Ubah Data Mahasiswa | Menghasilkan data mahasiswa yang berubah. |
| SIA-UC13 Hapus Data Mahasiswa | Menghasilkan data mahasiswa yang terhapus, hanya untuk mahasiswa yang tidak memiliki data akademik aktif. |

<!-- Alasan Generalization Use Case -->
Use case umum: SIA-UC10 Kelola Data Mahasiswa (konsep pengelolaan data mahasiswa).
Alasan: ketiganya sama-sama menghasilkan data mahasiswa yang terkelola, sehingga sah sebagai bentuk khusus SIA-UC10. Admin Akademik cukup dihubungkan ke SIA-UC10, bukan ke ketiga use case khusus. Hubungan ini hanya generalization, tidak digabung dengan include atau extend. Panah segitiga kosong menunjuk SIA-UC10.

<!-- Collaboration -->
| ID | Nama collaboration | Use case yang direalisasikan |
|----|--------------------|------------------------------|
| SIA-CO01 | Input Nilai Mata Kuliah | SIA-UC08 Input Nilai Mata Kuliah |
| SIA-CO02 | Lihat KHS | SIA-UC09 Lihat KHS |

<!-- Spesifikasi Hubungan Diagram Kumulatif -->
| Sumber | Hubungan | Tujuan | Status |
|--------|----------|--------|--------|
| Civitas Akademika | Association | SIA-UC07 Lihat Kalender Akademik | baru (digambar satu kali) |
| Mahasiswa | Generalization → | Civitas Akademika | baru |
| Dosen | Generalization → | Civitas Akademika | baru |
| Mahasiswa | Association | SIA-UC09 Lihat KHS | baru |
| Dosen | Association | SIA-UC08 Input Nilai Mata Kuliah | baru |
| Admin Akademik | Association | SIA-UC10 Kelola Data Mahasiswa | baru |
| SIA-UC11 | Generalization → | SIA-UC10 | baru |
| SIA-UC12 | Generalization → | SIA-UC10 | baru |
| SIA-UC13 | Generalization → | SIA-UC10 | baru |
| SIA-CO01 (collaboration) | Realization → | SIA-UC08 | baru |
| SIA-CO02 (collaboration) | Realization → | SIA-UC09 | baru |
| Mahasiswa | Association | SIA-UC01, SIA-UC03, SIA-UC05 | tetap (cek P03) |
| Admin Akademik | Association | SIA-UC02 | tetap (cek P03) |
| Dosen Wali | Association | SIA-UC06 | tetap (cek P03) |
| SIA-UC03 | «include» | SIA-UC04 | tetap |
| SIA-UC05 | «extend» | SIA-UC03 (beserta condition dan extension point dari P03) | tetap |