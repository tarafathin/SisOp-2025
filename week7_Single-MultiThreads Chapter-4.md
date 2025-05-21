# Single Thread vs Multi Thread

## Apa Pengertian dari Single Thread?

Single thread artinya program hanya menjalankan **satu tugas dalam satu waktu**. Jadi, jika ada banyak tugas, semuanya dikerjakan **satu per satu secara berurutan**.

**Kelebihan:**
- Lebih mudah dibuat dan dipahami.
- Cocok untuk aplikasi sederhana.

**Kekurangan:**
- Lambat jika ada banyak tugas.
- Tidak cocok untuk aplikasi yang butuh banyak proses bersamaan.

---

## Apa Pengertian dari Multi Thread?

Multi thread artinya program bisa menjalankan **beberapa tugas sekaligus** dalam waktu bersamaan.

**Kelebihan:**
- Lebih cepat dan efisien, apalagi di komputer dengan banyak inti prosesor (multi-core).
- Cocok untuk aplikasi berat seperti game, server, dan aplikasi real-time.

**Kekurangan:**
- Lebih rumit, harus mengatur agar thread tidak saling ganggu (misalnya mengakses data yang sama).
- Bisa muncul masalah seperti *race condition* kalau tidak hati-hati.

---

## Perbandingan Sederhana

| Fitur            | Single Thread                   | Multi Thread                             |
|------------------|----------------------------------|-------------------------------------------|
| Eksekusi         | Satu tugas dalam satu waktu      | Banyak tugas secara bersamaan             |
| Kecepatan        | Lebih lambat                    | Lebih cepat pada tugas kompleks           |
| Implementasi     | Lebih mudah                     | Lebih rumit (perlu pengelolaan sinkronisasi) |
| Cocok untuk      | Aplikasi sederhana              | Aplikasi berat, multitasking, real-time   |

---


<img align="center" src="img/Single-MultiThread.png" alt="Perbandingan Single Thread dan Multi Thread" />

---

Dengan memahami perbedaan ini, kamu bisa memilih pendekatan yang sesuai saat membuat program: apakah cukup dengan satu alur kerja, atau butuh banyak jalur agar lebih cepat dan efisien.
