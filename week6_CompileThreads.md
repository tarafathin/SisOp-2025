# Pemahaman Program `print123thread.c` 
Program ini adalah contoh sederhana penggunaan thread di bahasa C untuk mencetak angka 1, 2, dan 3. Setiap angka dicetak oleh thread yang berbeda. Program ini membantu memahami bagaimana thread berjalan secara paralel dan bagaimana hasil bisa berbeda jika tidak disinkronkan.

## Tujuan Program
- Menunjukkan cara membuat beberapa thread.
- Melihat bagaimana thread berjalan bersamaan (tanpa urutan tetap).
- Memahami pentingnya sinkronisasi untuk menjaga urutan eksekusi.

## Isi Kode Program

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

void *print1(void *arg) {
    printf("1\\n");
    return NULL;
}

void *print2(void *arg) {
    printf("2\\n");
    return NULL;
}

void *print3(void *arg) {
    printf("3\\n");
    return NULL;
}

int main() {
    pthread_t t1, t2, t3;

    pthread_create(&t1, NULL, print1, NULL);
    pthread_create(&t2, NULL, print2, NULL);
    pthread_create(&t3, NULL, print3, NULL);

    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
    pthread_join(t3, NULL);

    return 0;
}

## Penjelasan Setiap Thread

### 1. Thread 1 (print1)
- Mencetak angka 1.
- Tidak ada urutan pasti kapan akan dijalankan karena tidak ada sinkronisasi.

### 2. Thread 2 (print2)
- Mencetak angka 2.
- Bisa dijalankan sebelum atau sesudah thread lainnya.

### 3. Thread 3 (print3)
- Mencetak angka 3.
- Sama seperti thread lainnya, tidak pasti urutan eksekusinya.

## contoh output:
3
1
2
atau
1
2
3
