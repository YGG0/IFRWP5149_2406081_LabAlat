
<!--LAB-UC11 — Catat Pengembalian Peralatan-->
| Elemen                | Isi                                                                                                   |
| :-------------------- | :---------------------------------------------------------------------------------------------------- |
| ID dan nama           | LAB-UC11: Catat Pengembalian Peralatan                                                                |
| Sumber kebutuhan      | LAB-R09 dan LAB-R10                                                                                   |
| Tujuan                | Pengembalian tercatat dan status peminjaman serta kondisi peralatan terbarui                          |
| Aktor utama           | Petugas Laboratorium                                                                                  |
| Pemicu                | Petugas memilih fungsi pencatatan pengembalian dan menentukan peminjaman yang akan dikembalikan       |
| Prasyarat             | Petugas telah terautentikasi; peminjaman terpilih berstatus Dipinjam                                  |
| Pascakondisi berhasil | Pengembalian tercatat dengan tanggal kembali dan kondisi peralatan; status peminjaman menjadi Selesai |
| Pascakondisi gagal    | Tidak ada pengembalian baru yang tercatat; status peminjaman tidak berubah                            |
| Include               | LAB-UC12: Periksa Kondisi Peralatan                                                                   |
| Collaboration         | LAB-CO02: Catat Pengembalian Peralatan                                                                |

Alur Utama:
| Langkah | Tindakan Petugas                              | Respons Sistem                                                                    |
| ------- | --------------------------------------------- | --------------------------------------------------------------------------------- |
| 1       | Memilih peminjaman yang akan dikembalikan     | Menampilkan data peminjaman terpilih dan statusnya                                |
| 2       | Mengonfirmasi alat yang kembali dan jumlahnya | Menampung konfirmasi petugas                                                      |
| 3       | —                                             | Memeriksa status peminjaman harus Dipinjam                                        |
| 4       | —                                             | Menjalankan LAB-UC12: memeriksa dan mencatat kondisi peralatan                    |
| 5       | Menyimpan pencatatan pengembalian             | Menyimpan tanggal kembali dan kondisi; mengubah status peminjaman menjadi Selesai |
| 6       | Melihat konfirmasi                            | Menampilkan ringkasan pengembalian                                                |

Alur Alternatif / Pengecualian:
| Kode | Kondisi                          | Langkah | Penanganan                                                                                            |
| ---- | -------------------------------- | ------- | ----------------------------------------------------------------------------------------------------- |
| A1   | Status bukan Dipinjam            | 3       | Sistem menolak pencatatan dan menampilkan status peminjaman saat ini. Pascakondisi gagal berlaku.     |
| A2   | Kondisi Rusak Ringan atau Berat  | 4       | Sistem tetap menyimpan pencatatan, menandai kondisi tersebut pada data peralatan. Tidak memicu denda. |
| A3   | Jumlah alat kembali tidak sesuai | 2       | Sistem meminta petugas memeriksa kembali isian. Pencatatan tidak disimpan sampai jumlah dikoreksi.    |