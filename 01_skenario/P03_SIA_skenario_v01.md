<!--tabel kebutuhan-->
Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap
pengajuan menjalankan validasi KRS yang memeriksa kelengkapan,
prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil,
sistem menyimpan pengajuan berstatus menunggu persetujuan dosen
wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih
mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS
dan memberikan catatan keputusan.

<!--tabel kebutuhan-->
| ID      | Kebutuhan                                                       |
|---------|-----------------------------------------------------------------|
| SIA-R03 | Mahasiswa dapat mengajukan KRS                                  |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan                 |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS       |

<!--Batas sistem dan aturan-->
Batas dan asumsi:
• Pengguna telah terautentikasi.
• Data mata kuliah, prasyarat, dan jadwal tersedia.
• Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
• Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
• KRS tersimpan belum berarti disetujui.
• Pembayaran, pengisian nilai, dan implementasi basis data berada di luar
tugas.

<!--tabel identifikasi aktor-->
| Aktor      | Tujuan terhadap Sistem                                       |
|------------|--------------------------------------------------------------|
| Mahasiswa  | Mengajukan KRS dan mengunduh bukti jika memilihnya pada      |
|            | konfirmasi pengajuan                                         |
| Dosen Wali | Memproses persetujuan atau penolakan KRS beserta catatan     |
|            | keputusan                                                    |

<!--Katalog usecase-->
|   ID    |   Nama use case           |          Peran dalam model           |
|---------|---------------------------|--------------------------------------|
| SIA-UC01| Ajukan KRS                | Fungsi utama mahasiswa               |
| SIA-UC02| Validasi KRS              | Perilaku yang disertakan UC01        |
| SIA-UC03| Unduh bukti pengajuan KRS | Tambahan bersyarat pada UC01         |
| SIA-UC04| Proses keputusan KRS      | Fungsi utama dosen wali              |

<!--Relasi Include-->
SIA-UC03 «include» SIA-UC04
Alasan: validasi kelengkapan, prasyarat, dan benturan jadwal selalu menjadi bagian dari setiap pengajuan KRS.

<!--Relasi Extend-->
SIA-UC05 «extend» SIA-UC03
Extension point: Bukti pengajuan tersedia
Kondisi: [mahasiswa memilih unduh]
Alasan: pengajuan tetap berhasil tanpa pengunduhan bukti.

