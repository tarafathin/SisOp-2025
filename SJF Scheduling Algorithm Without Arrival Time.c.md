# Analisis Hasil Eksekusi Program Penjadwalan SJF (Shortest Job First) Non-Preemptive

## Deskripsi Umum
Program pada gambar merupakan implementasi algoritma **Shortest Job First (SJF) Non-Preemptive** tanpa waktu kedatangan (arrival time). Dalam algoritma ini, proses yang memiliki **burst time** (waktu eksekusi) paling kecil akan dieksekusi terlebih dahulu. Karena bersifat non-preemptive, proses yang sedang berjalan tidak dapat dihentikan sampai selesai.

## Data Input
Jumlah proses: 4

Burst Time masing-masing proses:
- Process 1: 7
- Process 2: 4
- Process 3: 1
- Process 4: 4

## Proses Penjadwalan
Algoritma SJF mengurutkan proses berdasarkan burst time dari yang terkecil. Dengan burst time seperti di atas, urutan eksekusi proses berdasarkan burst time adalah:
1. P3 (1)
2. P2 (4)
3. P4 (4)
4. P1 (7)

Jika tidak ada arrival time, maka semua proses dianggap tersedia pada waktu 0. Maka proses dengan burst time terkecil dieksekusi lebih dahulu.

## Tabel Hasil
| ProcessNo | BT | CT | TAT | WT | RT |
|-----------|----|----|-----|----|----|
| P3        |  1 |  1 |   1 |  0 |  0 |
| P2        |  4 |  5 |   5 |  1 |  1 |
| P4        |  4 |  9 |   9 |  5 |  5 |
| P1        |  7 | 16 |  16 |  9 |  9 |

Keterangan:
- **BT (Burst Time)**: Waktu yang dibutuhkan proses untuk menyelesaikan eksekusi.
- **CT (Completion Time)**: Waktu saat proses selesai dieksekusi.
- **TAT (Turnaround Time)**: CT - waktu kedatangan (karena arrival time = 0, maka TAT = CT).
- **WT (Waiting Time)**: TAT - BT.
- **RT (Response Time)**: Sama dengan WT untuk algoritma non-preemptive.

## Perhitungan Rata-Rata
- **Average Turnaround Time** = (1 + 5 + 9 + 16) / 4 = 7.75
- **Average Waiting Time** = (0 + 1 + 5 + 9) / 4 = 3.75

## Analisis
1. **Efisiensi**: Dengan mengurutkan proses berdasarkan burst time, algoritma ini meminimalkan average waiting time dan average turnaround time dibanding algoritma seperti FCFS.

2. **Kelebihan**:
   - Cocok untuk sistem dengan proses yang tidak memiliki prioritas.
   - Meningkatkan efisiensi dengan memprioritaskan proses yang pendek.

3. **Kekurangan**:
   - Tidak adil bagi proses dengan burst time besar (seperti P1 dalam contoh ini), karena harus menunggu lebih lama.
   - Tidak cocok jika proses datang pada waktu yang berbeda.
