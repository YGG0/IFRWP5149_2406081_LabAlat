| No. | Temuan | Perbaikan yang Diperlukan | Alasan |
|:---:|:---|:---|:---|
| 1 | Aktor Mahasiswa diletakkan di dalam batas sistem (*System Boundary*). | Pindahkan aktor Mahasiswa ke luar batas sistem di sebelah kiri. | Aktor adalah entitas eksternal di luar sistem. Batas sistem hanya melingkupi fungsi-fungsi internal (*Use Case*). |
| 2 | Fungsi "Lihat jadwal kuliah" digambar dengan bentuk kotak (*rectangle*). | Ubah bentuk notasi menjadi elips horizontal (*ellipse*). | Standar UML mensyaratkan Use Case digambarkan dengan bentuk elips, sedangkan kotak digunakan untuk notasi lain (Class/Package). |
| 3 | Aktor Mahasiswa terhubung ke "Kelola jadwal kuliah". | Putuskan garis asosiasi tersebut, lalu hubungkan Mahasiswa ke "Lihat jadwal kuliah" dan Admin Akademik ke "Kelola jadwal kuliah". | Sesuai batasan skenario SIA-R01 & SIA-R02, Mahasiswa hanya berhak melihat jadwal, sedangkan pengelolaan jadwal adalah wewenang Admin Akademik. |
| 4 | Judul batas sistem tertulis sistem laboratorium. | Ubah judul *boundary* menjadi "Sistem Informasi Akademik". | Menjaga konsistensi identitas sistem agar ruang lingkup yang dimodelkan sesuai kasus SIA dan tidak tertukar. |
