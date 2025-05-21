# Chapter 4 – Threads & Concurrency: 

## 1. Kapan Multithread Lebih Cepat?

Multithread berguna saat banyak hal perlu dikerjakan secara bersamaan. Contohnya:

- **Web Server**: Setiap permintaan dari pengguna dijalankan oleh thread berbeda, jadi tidak perlu menunggu satu per satu.
- **Pemrosesan Gambar**: Gambar besar bisa dibagi ke beberapa bagian lalu diproses paralel.
- **Game**: Grafik, logika, dan AI dijalankan di thread berbeda agar game berjalan mulus.

## 2. Hitung Kecepatan dengan Amdahl’s Law

Misalnya, 60% program bisa paralel (P = 0.6). Maka:

### a) 2 Core:
Speedup = 1 / (1 - 0.6 + 0.6 / 2)
= 1 / 0.7 ≈ 1.43

### b) 4 Core:
Speedup = 1 / (1 - 0.6 + 0.6 / 4)
= 1 /

**Kesimpulan**: Lebih banyak core = lebih cepat, tapi tetap terbatas jika sebagian program tidak bisa paralel.

## 3. Task atau Data Parallelism?

Web server yang multithread termasuk **task parallelism**, karena setiap thread menjalankan tugas yang berbeda (melayani request berbeda), bukan membagi data besar.

## 4. Perbedaan User Thread & Kernel Thread

| User Thread                   | Kernel Thread                      |
|------------------------------|------------------------------------|
| Dikelola oleh program        | Dikelola oleh sistem operasi       |
| Lebih ringan dan cepat       | Lebih kuat dan bisa paralel sesungguhnya |
| Tidak bisa manfaatkan multicore langsung | Bisa gunakan multicore CPU |

Mengunakan **user thread** untuk aplikasi ringan, dan **kernel thread** untuk aplikasi berat.

## 5. Apa yang Terjadi Saat Ganti Thread?

Saat sistem mengganti thread:
1. Menyimpan keadaan thread saat ini (data, posisi, dll).
2. Memilih thread baru.
3. Memuat kembali keadaan thread baru.
4. Melanjutkan dari posisi terakhir thread tersebut.

Multithreading membuat program lebih cepat dan responsif, tetapi tetap harus diatur dengan baik agar tidak terjadi konflik atau kesalahan data.


