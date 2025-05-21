# Forking dan Analisis Kode print123thread.c

## Apa Itu pengertian dari Forking?

Forking adalah proses membuat salinan sebuah proses (parent) menjadi proses baru (child). Ini dilakukan menggunakan fungsi `fork()` di bahasa C.

- Setelah `fork()` dipanggil, ada dua proses yang berjalan:
  - Proses induk (parent) dengan PID asli.
  - Proses anak (child) dengan PID baru.
- Kedua proses mulai berjalan dari baris kode setelah pemanggilan `fork()`.

## Contoh Kode Forking di C

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid = fork();

    if (pid < 0) {
        perror("Fork gagal");
        return 1;
    } else if (pid == 0) {
        // Ini proses anak
        printf("Proses anak, PID: %d\n", getpid());
    } else {
        // Ini proses induk
        printf("Proses induk, PID: %d, anak PID: %d\n", getpid(), pid);
    }

    return 0;
}

# Analisis Kode `print123thread.c`

## Apa yang Dilakukan Kode Ini?

Kode ini membuat 3 thread yang mencetak angka 1, 2, dan 3 secara bergantian terus menerus.

## Cara Kerja Kode

- Ada 3 thread yang berjalan bersamaan.
- Setiap thread punya nomor (1, 2, atau 3).
- Hanya thread dengan nomor yang sama dengan variabel `done` yang boleh mencetak angkanya.
- Setelah mencetak, thread mengubah `done` ke nomor thread berikutnya.
- Thread lain yang bukan gilirannya akan menunggu sampai diberi sinyal.

## Bagaimana Cara Sinkronisasinya?

- Mutex dipakai supaya cuma satu thread yang aktif mencetak pada waktu tertentu.
- Condition variable dipakai supaya thread yang bukan giliran bisa menunggu dulu dengan tenang.
- Setelah thread selesai, dia memberi tahu thread berikutnya untuk mulai jalan.

## Kesimpulan

Kode ini contoh sederhana bagaimana membuat beberapa thread kerja bergantian tanpa tabrakan, pakai cara sinkronisasi yang aman dengan mutex dan condition variable.

