# Perbedaan multiprogramming dan multitasking

## 1. Multi Programming
Multiprogramming menjalankan beberapa program sekaligus tetapi CPU hanya beralih saat program aktif menunggu I/O.

**ciri-ciri**
- Digunakan di sistem komputer lama
- Program disimpan semua di memori
- CPU hanya beralih saat program menunggu I/O

**contoh**
- Sistem bank yang memproses banyak transaksi sekaligus
- Server mencetak dokumen dari banyak user
  
## 2. Multi Tasking
multitasking dengan cepat bergantian menjalankan program berdasarkan pembagian waktu agar terlihat berjalan bersamaan.

**ciri-ciri**
- digunakan sistem operasi modern (Windows, Linux, macOS)
- CPU berpindah task sangat cepat
- User bisa interaksi dengan banyak aplikasi bersamaan

**contoh**
- coba buka browser + Word + Spotify bersamaan
- Edit foto sambil mendengarkan musik dan download file

## 3. Perbandingan dalam bentuk tabel
| Aspek            | Multiprogramming               | Multitasking                           |
|------------------|--------------------------------|----------------------------------------|
| Alokasi CPU      | Beralih hanya saat I/O wait    | Beralih berdasarkan waktu (time slice) |
| Responsif        | Tidak (non-interaktif)         | Ya (interaktif)                        |
| Manajemen Memori | Semua program dimuat sekaligus | Program bisa di-swap ke disk           |
| Contoh Sistem    | IBM OS/360 (1960-an)           | Windows 10, Linux, macOS               |
| Keuntungan       | Efisiensi CPU tinggi           | User experience lebih baik             |
| Kekurangan       | Tidak bisa interaksi real-time | Butuh resource lebih besar             |

## Kesimpulan
jadi Komputer punya dua cara menjalankan banyak tugas: multiprogramming dan multitasking. Sistem lama pakai multiprogramming, sistem modern pakai multitasking supaya lebih lancar. Sekarang komputer pake kedua cara ini - multitasking untuk aplikasi yang kita lihat, multiprogramming untuk kerja di belakang layar.
