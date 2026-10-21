<!--SIA-UC01 — Lihat jadwal kuliah-->

| Elemen                | Isi                                                     |
| --------------------- | ------------------------------------------------------- |
| ID dan Nama           | SIA-UC01 — Lihat jadwal kuliah                          |
| Sumber kebutuhan      | SIA-R01                                                 |
| Tujuan                | Menampilkan jadwal kuliah kepada mahasiswa              |
| Aktor utama           | Mahasiswa                                               |
| Aktor pendukung       | —                                                       |
| Pemicu                | Mahasiswa memilih menu jadwal kuliah                    |
| Prasyarat             | Mahasiswa telah terautentikasi; data jadwal tersedia    |
| Pascakondisi berhasil | Jadwal kuliah tampil di layar mahasiswa                 |
| Pascakondisi gagal    | Jadwal tidak tampil; sistem menampilkan pesan kesalahan |
| Aturan bisnis/asumsi  | Jadwal hanya menampilkan mata kuliah yang relevan       |

Alur utama:
| Langkah | Tindakan mahasiswa  | Respons sistem                               |
| ------- | ------------------- | -------------------------------------------- |
| 1       | Membuka menu jadwal | Menampilkan pilihan semester / periode       |
| 2       | Memilih periode     | Menampilkan daftar jadwal kuliah             |
| 3       | Melihat jadwal      | Menampilkan detail jadwal (hari, jam, ruang) |

Alur alternatif/pengecualian:
| Kode | Kondisi                    | Langkah | Penanganan                              |
| ---- | -------------------------- | ------- | --------------------------------------- |
| A1   | Data jadwal belum tersedia | 2       | Tampilkan pesan "jadwal belum tersedia" |
| A2   | Koneksi data gagal         | 2       | Tampilkan pesan kegagalan sistem        |


<!--SIA-UC02 — Kelola jadwal kuliah-->
| Elemen                | Isi                                                          |
| --------------------- | ------------------------------------------------------------ |
| ID dan Nama           | SIA-UC02 — Kelola jadwal kuliah                              |
| Sumber kebutuhan      | SIA-R02                                                      |
| Tujuan                | Menambah, mengubah, atau menghapus data jadwal kuliah        |
| Aktor utama           | Admin Akademik                                               |
| Aktor pendukung       | —                                                            |
| Pemicu                | Admin akademik membuka menu kelola jadwal                    |
| Prasyarat             | Admin akademik terautentikasi dengan hak akses kelola jadwal |
| Pascakondisi berhasil | Data jadwal tersimpan dan konsisten                          |
| Pascakondisi gagal    | Data jadwal tidak berubah                                    |
| Aturan bisnis/asumsi  | Jadwal tidak boleh bentrok untuk kelas, ruang, dan waktu     |

Alur utama:
| Langkah | Tindakan admin                   | Respons sistem                             |
| ------- | -------------------------------- | ------------------------------------------ |
| 1       | Membuka menu kelola              | Menampilkan daftar jadwal kuliah           |
| 2       | Memilih aksi (tambah/ubah/hapus) | Menampilkan formulir sesuai aksi           |
| 3       | Mengisi data jadwal              | Memvalidasi kelengkapan dan benturan       |
| 4       | Mengirim perubahan               | Menyimpan perubahan dan menampilkan status |

Alur alternatif/pengecualian:
| Kode | Kondisi            | Langkah | Penanganan                           |
| ---- | ------------------ | ------- | ------------------------------------ |
| A1   | Data tidak lengkap | 3       | Tampilkan pesan kelengkapan          |
| A2   | Jadwal bentrok     | 3       | Tolak penyimpanan; tampilkan konflik |
| A3   | Admin membatalkan  | 3       | Kembali ke daftar tanpa perubahan    |

<!--SIA-UC03 — Ajukan KRS-->
| Elemen                | Isi                                                                                     |
| --------------------- | --------------------------------------------------------------------------------------- |
| ID dan Nama           | SIA-UC03 — Ajukan KRS                                                                   |
| Sumber kebutuhan      | SIA-R03, SIA-R04, SIA-R05                                                               |
| Tujuan                | Menghasilkan pengajuan KRS yang tersimpan dengan status Menunggu persetujuan dosen wali |
| Aktor utama           | Mahasiswa                                                                               |
| Aktor pendukung       | —                                                                                       |
| Pemicu                | Mahasiswa memilih fungsi pengajuan KRS                                                  |
| Prasyarat             | Mahasiswa telah terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia        |
| Include               | SIA-UC04 — Validasi KRS                                                                 |
| Extension point       | Bukti pengajuan tersedia, pada langkah 6                                                |
| Extend                | SIA-UC05 jika [mahasiswa memilih unduh]                                                 |
| Pascakondisi berhasil | Pengajuan KRS tersimpan dengan nomor dan status Menunggu persetujuan dosen wali         |
| Pascakondisi gagal    | Tidak ada pengajuan KRS baru yang berhasil tersimpan                                    |
| Aturan bisnis/asumsi  | KRS tersimpan ≠ disetujui; unduh bukti tidak menjadi syarat keberhasilan pengajuan      |

Alur utama:
| Langkah | Tindakan mahasiswa    | Respons sistem                                         |
| ------- | --------------------- | ------------------------------------------------------ |
| 1       | Membuka pengajuan KRS | Menampilkan formulir pengajuan                         |
| 2       | Memilih mata kuliah   | Menampung isian                                        |
| 3       | Mengirim pengajuan    | Memeriksa kelengkapan data                             |
| 4       | —                     | Menjalankan SIA-UC04                                   |
| 5       | —                     | Jika valid, menyimpan pengajuan dan memberikan nomor   |
| 6       | Melihat konfirmasi    | Menampilkan nomor dan status; mencapai extension point |
| 7       | Mengakhiri pengajuan  | Menutup proses pengajuan                               |

Alur alternatif/pengecualian:
| Kode | Kondisi                                       | Langkah | Penanganan                                            |
| ---- | --------------------------------------------- | ------- | ----------------------------------------------------- |
| A1   | Data pengajuan tidak lengkap                  | 3       | Tampilkan pesan kelengkapan; pengajuan tidak disimpan |
| A2   | Validasi KRS gagal                            | 4       | Tampilkan alasan kegagalan; pengajuan tidak disimpan  |
| A3   | Mahasiswa memilih unduh bukti pada konfirmasi | 6       | Jalankan SIA-UC05; kembali ke langkah 7               |


<!--SIA-UC04 — Validasi KRS-->
| Elemen                | Isi                                                                                   |
| --------------------- | ------------------------------------------------------------------------------------- |
| ID dan Nama           | SIA-UC04 — Validasi KRS                                                               |
| Sumber kebutuhan      | SIA-R04                                                                               |
| Tujuan                | Memastikan KRS memenuhi kelengkapan, prasyarat mata kuliah, dan tidak benturan jadwal |
| Aktor utama           | — (dijalankan sebagai bagian SIA-UC03)                                                |
| Aktor pendukung       | —                                                                                     |
| Pemicu                | Dipanggil dari SIA-UC03 langkah 4                                                     |
| Prasyarat             | Data pengajuan KRS diterima; data mata kuliah, prasyarat, dan jadwal tersedia         |
| Pascakondisi berhasil | Status validasi = valid; sistem melanjutkan penyimpanan                               |
| Pascakondisi gagal    | Status validasi = tidak valid; masalah dikembalikan ke UC03                           |
| Aturan bisnis/asumsi  | Validasi bersifat wajib (include), bukan opsional                                     |

Alur utama:
| Langkah | Tindakan | Respons sistem                              |
| ------- | -------- | ------------------------------------------- |
| 1       | —        | Menerima data pengajuan KRS dari SIA-UC03   |
| 2       | —        | Memeriksa kelengkapan data pengajuan        |
| 3       | —        | Memeriksa prasyarat setiap mata kuliah      |
| 4       | —        | Memeriksa benturan jadwal antar mata kuliah |
| 5       | —        | Mengembalikan status valid kepada SIA-UC03  |

Alur alternatif/pengecualian:
| Kode | Kondisi                   | Langkah | Penanganan                                             |
| ---- | ------------------------- | ------- | ------------------------------------------------------ |
| A1   | Data tidak lengkap        | 2       | Kembalikan tidak valid + daftar field kosong           |
| A2   | Prasyarat tidak terpenuhi | 3       | Kembalikan tidak valid + daftar mata kuliah bermasalah |
| A3   | Benturan jadwal           | 4       | Kembalikan tidak valid + pasangan jadwal bentrok       |


<!--SIA-UC05 — Unduh bukti pengajuan KRS-->

| Elemen                | Isi                                                          |
| --------------------- | ------------------------------------------------------------ |
| ID dan Nama           | SIA-UC05 — Unduh bukti pengajuan KRS                         |
| Sumber kebutuhan      | SIA-R05                                                      |
| Tujuan                | Menyediakan berkas bukti pengajuan KRS yang dapat diunduh    |
| Aktor utama           | Mahasiswa                                                    |
| Aktor pendukung       | —                                                            |
| Pemicu                | Mahasiswa memilih opsi unduh pada konfirmasi (extension pt.) |
| Prasyarat             | Pengajuan KRS berhasil tersimpan (SIA-UC03 langkah 6)        |
| Extension point       | Bukti pengajuan tersedia                                     |
| Kondisi extend        | [mahasiswa memilih unduh]                                    |
| Pascakondisi berhasil | Berkas bukti pengajuan KRS berhasil diunduh mahasiswa        |
| Pascakondisi gagal    | Berkas tidak terunduh; pengajuan KRS tetap tersimpan         |
| Aturan bisnis/asumsi  | Unduh tidak menjadi syarat keberhasilan pengajuan            |

Alur utama:
| Langkah | Tindakan mahasiswa         | Respons sistem                            |
| ------- | -------------------------- | ----------------------------------------- |
| 1       | Memilih opsi "Unduh bukti" | Menyiapkan berkas bukti pengajuan KRS     |
| 2       | Menyimpan berkas           | Mengirimkan berkas ke perangkat mahasiswa |

Alur alternatif/pengecualian:
| Kode | Kondisi                 | Langkah | Penanganan                                       |
| ---- | ----------------------- | ------- | ------------------------------------------------ |
| A1   | Gagal menyiapkan berkas | 1       | Tampilkan pesan gagal unduh; KRS tetap tersimpan |
| A2   | Mahasiswa membatalkan   | 1       | Kembali ke SIA-UC03 langkah 7                    |


<!--SIA-UC06 — Proses keputusan KRS-->
| Elemen                | Isi                                                                         |
| --------------------- | --------------------------------------------------------------------------- |
| ID dan Nama           | SIA-UC06 — Proses keputusan KRS                                             |
| Sumber kebutuhan      | SIA-R06                                                                     |
| Tujuan                | Menetapkan persetujuan atau penolakan KRS beserta catatan                   |
| Aktor utama           | Dosen Wali                                                                  |
| Aktor pendukung       | —                                                                           |
| Pemicu                | Dosen wali membuka daftar pengajuan KRS mahasiswa bimbingan                 |
| Prasyarat             | Dosen wali terautentikasi; ada pengajuan KRS berstatus Menunggu persetujuan |
| Pascakondisi berhasil | KRS berstatus Disetujui atau Ditolak; catatan tersimpan                     |
| Pascakondisi gagal    | Status KRS tidak berubah                                                    |
| Aturan bisnis/asumsi  | Keputusan memerlukan catatan; KRS tersimpan ≠ disetujui                     |

Alur utama:
| Langkah | Tindakan dosen wali          | Respons sistem                                    |
| ------- | ---------------------------- | ------------------------------------------------- |
| 1       | Membuka daftar pengajuan KRS | Menampilkan daftar KRS Menunggu persetujuan       |
| 2       | Memilih satu pengajuan       | Menampilkan detail KRS dan data mahasiswa         |
| 3       | Menetapkan keputusan         | Menampung pilihan keputusan                       |
| 4       | Menuliskan catatan keputusan | Menampung catatan                                 |
| 5       | Mengirim keputusan           | Menyimpan keputusan & catatan; memperbarui status |

Alur alternatif/pengecualian:
| Kode | Kondisi                  | Langkah | Penanganan                                      |
| ---- | ------------------------ | ------- | ----------------------------------------------- |
| A1   | Catatan keputusan kosong | 4       | Tampilkan pesan wajib isi catatan               |
| A2   | KRS sudah diputuskan     | 2       | Tampilkan status terkini; keputusan tidak ulang |
| A3   | Dosen menyetujui         | 5       | Status = Disetujui; catatan tersimpan           |
| A4   | Dosen menolak            | 5       | Status = Ditolak; catatan tersimpan             |