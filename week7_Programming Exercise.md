# Programming Exercises: Belajar Threading

## a. Contoh Thread di Java: `SumTask.java`

### Apa itu `SumTask.java`?

File `SumTask.java` adalah contoh program di Java yang menggunakan **thread** untuk menghitung jumlah elemen dalam array besar dengan cara **membagi tugas ke beberapa thread**.

### Bagaimana Cara Kerja `SumTask.java`?

1. Data (array) dibagi ke beberapa bagian kecil.
2. Tiap bagian dihitung oleh thread berbeda.
3. Semua hasil digabung untuk mendapatkan total akhir.

### Mengapa Memakai Thread?

Jika kamu harus menghitung 10.000 angka. Kalau pakai satu orang (single thread), butuh waktu yang lama. Tapi jika kamu bagi ke 4 orang (4 thread), pekerjaan jadi lebih cepat.

Program ini menggunakan **interface `Runnable`**, artinya objeknya bisa dijalankan oleh thread.

### Keuntungan:
- Lebih cepat, apalagi di komputer dengan banyak core (multi-core).
- Bisa digunakan untuk tugas berat seperti perhitungan besar.

### Tantangan:
- Harus hati-hati supaya hasil tidak kacau.
- Misalnya, dua thread tidak boleh menghitung bagian yang sama.

## b. Contoh Thread di Linux dan Windows

### `thrd-posix.c` (Linux / Unix)

Di sistem operasi Linux, program ini menggunakan **POSIX Threads (pthreads)** untuk membuat thread. Cara kerjanya:

1. Thread dibuat pakai `pthread_create`.
2. Masing-masing thread menjalankan fungsi tertentu.
3. Untuk **menghindari bentrok saat akses data**, digunakan **mutex (pengunci)**.

Kesimpualnnya: Setiap thread kerja sendiri-sendiri, tapi tetap koordinasi agar tidak tabrakan.

---

### `thrd-win32.c` (Windows)

Di sistem operasi Windows, program ini membuat thread menggunakan **Windows API**, khususnya fungsi `CreateThread`.

Cara kerjanya hampir sama seperti di Linux, tapi sintaks dan caranya berbeda karena Windows punya gaya sendiri.

## Perbandingan Sederhana

| Aspek               | Linux (`thrd-posix.c`)         | Windows (`thrd-win32.c`)        |
|---------------------|---------------------------------|----------------------------------|
| API Threading       | POSIX Threads (pthreads)        | Windows API (`CreateThread`)     |
| Sinkronisasi        | Mutex (POSIX)                   | Juga menggunakan mekanisme sinkronisasi (Windows Mutex, Semaphore, dll.) |
| Gaya Pemrograman    | Lebih terbuka/standar Unix      | Tertutup/khusus sistem Windows   |
| Prinsip Kerja       | Sama: jalankan beberapa tugas sekaligus |

---

## Kesimpulan

- **Threading** membuat program lebih cepat dan efisien dengan menjalankan tugas secara paralel.
- Walaupun caranya beda di setiap bahasa atau sistem operasi, **tujuan utamanya tetap sama**: membagi pekerjaan agar bisa selesai lebih cepat.
- Tapi, makin banyak thread, makin kompleks juga pengaturannya. Harus hati-hati agar tidak bentrok saat akses data bersama.

