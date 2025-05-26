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
  
## 2. SJF Scheduling Algorithm.c

###code program
```c
#include<stdio.h>
struct proc
{
    int no,at,bt,it,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Arrival Time: ");
    scanf("%d",&p.at);
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    return p;
}
int main()
{
    int  n,j,min=0;
    float avgtat=0,avgwt=0;
    struct proc p[10],temp;
    printf("<--SJF Scheduling Algorithm (Non-Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(j=0;j<n-i-1;j++)    
            if(p[j].at>p[j+1].at)
            {
            temp=p[j];
            p[j]=p[j+1];
            p[j+1]=temp;
            }
    for(j=1;j<n&&p[j].at==p[0].at;j++)
        if(p[j].bt<p[min].bt)
            min=j;
    temp=p[0];
    p[0]=p[min];
    p[min]=temp;
    p[0].it=p[0].at;
    p[0].ct=p[0].it+p[0].bt;
    for(int i=1;i<n;i++)
    {
        for(j=i+1,min=i;j<n&&p[j].at<=p[i-1].ct;j++)
            if(p[j].bt<p[min].bt)
                min=j;
        temp=p[i];
        p[i]=p[min];
        p[min]=temp;
        if(p[i].at<=p[i-1].ct)
            p[i].it=p[i-1].ct;
        else
            p[i].it=p[i].at;
        p[i].ct=p[i].it+p[i].bt;
    }
    printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\tRT\n");
    for(int i=0;i<n;i++)
    {
        p[i].tat=p[i].ct-p[i].at;
        avgtat+=p[i].tat;
        p[i].wt=p[i].tat-p[i].bt;
        avgwt+=p[i].wt;
        printf("P%d\t\t%d\t%d\t%d\t%d\t%d\t%d\n",p[i].no,p[i].at,p[i].bt,p[i].ct,p[i].tat,p[i].wt,p[i].wt);
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}
```

### Analisa 

 Shortest Job First (SJF), kode ini memiliki waktu eksekusi terpendek (Burst Time), tetapi (Non-Preemtive) jika prosesnya dijalankan, maka prosesnya tidak bisa di ganggu. 

### Cara Kerja Code

**Struktur Data**
```c
struct proc {
    int no, at, bt, it, ct, tat, wt;
};
```
- `no`: Nomor Proses(urutan proses)
- `at`: Arrival Time (Waktu Kedatangan proses masuk ke sistem) 
- `bt`: Burst Time (Waktu Eksekusi)
- `it`: Idle Time (Waktu kosong sebelum mulai eksekusi proses)
- `ct`: Completion Time (Waktu Selesainya)
- `tat`: Turnaround Time (Waktu Total yang dibutuhkan dari awal sampai selesai)
- `wt`: Waiting Time (Waktu menunggu proses sebelum dikerjakan)

**Fungsi read()**
```c
struct proc read(int i) {
    struct proc p;
    p.no = i;
    printf("Enter Arrival Time: ");
    scanf("%d", &p.at);
    printf("Enter Burst Time: ");
    scanf("%d", &p.bt);
    return p;
}
```
-Fungsi untuk membaca data proses dari input user kemudian mengembalikannya sebagai sebuah struct proc

**Fungsi main()**

**Input Jumlah Proses**
```c
printf("Enter Number of Processes: ");
scanf("%d", &n);
for(int i=0; i<n; i++)
    p[i] = read(i+1);
```
-Fungsi untuk mengambil input data semua proses dan menyimpannya ke dalam array


**Sorting Berdasarkan Arrival Time**
```c
for(int i=0; i<n-1; i++)
    for(int j=0; j<n-i-1; j++)    
        if(p[j].at > p[j+1].at) {
            temp = p[j];
            p[j] = p[j+1];
            p[j+1] = temp;
        }
```
-Fungsinya untuk mengurutkan array agar proses awal berada didepan, proses ini penting untuk mengurutkan proses yang benar.

**Pemilihan Proses Pertama**
```c
for(j=1; j<n && p[j].at == p[0].at; j++)
    if(p[j].bt < p[min].bt)
        min=j;
temp = p[0];
p[0] = p[min];
p[min] = temp;
```
 -Fungsinya untuk mengoptimalkan waktu tunggu dan efisiensi, jadi code memilih proses pertama dan memprioritaskan proses yang paling cepat selesai(burst time paling kecil) 
**Penjadwalan SJF Non-Preemptive**
```c
p[0].it = p[0].at;  // Waktu proses pertama: arrival time
p[0].ct = p[0].it + p[0].bt;

for(int i=1; i<n; i++) {
    // Memulai proses dengan menentukan berdasarkan burst time terkecilnya.
    for(j=i+1, min=i; j<n && p[j].at <= p[i-1].ct; j++)
        if(p[j].bt < p[min].bt)
            min = j;

    // Untuk menukar posisi proses
    temp = p[i];
    p[i] = p[min];
    p[min] = temp;

    // Untuk Menghitung waktu mulai (idle time dan Completion Time)
    if(p[i].at <= p[i-1].ct)
        p[i].it = p[i-1].ct;  // Lanjut ke proses selanjutnya
    else
        p[i].it = p[i].at;    // proses mulai 
    p[i].ct = p[i].it + p[i].bt;  // Waktu selesai mengihitung
}
```
-Code ini memilih proses yang tercepat diantara yang datang.

###Output program




**Langkah-Langkah Penjadwalan**

1. **Waktu 0–5**: P1 dieksekusi karena merupakan proses yang datang pada saat waktu 0.
2. **Waktu 5–8**: P2 dipilih berikutnya karena sudah datang (AT=1) dan memiliki burst time terkecil (BT=3).
3. **Waktu 8–16**: P3 dijalankan terakhir karena burst timenya paling besar dan baru datang setelah P2 selesai.

**Perhitungan TAT, WT, dan Output**

- **CT (Completion Time)**: Waktu proses selesai dijalankan.
- **TAT (Turnaround Time)**: Total waktu dari awal datang hingga selesai.
- **WT (Waiting Time)**: Waktu menunggu antrian (TAT - BT).
- **RT (Response Time)**: Sama dengan WT pada SJF Non-Preemptive.

**Rata-Rata**

- **Average Turnaround Time** = (5 + 7 + 14) / 3 = **8.6667**
- **Average Waiting Time**   = (0 + 4 + 6) / 3 = **3.3333**

###Kesimpulan

- **Urutan Eksekusi**: `P1 → P2 → P3`
- **Algoritmanya berjalan sesuai dengan aturan SJF Non-Preemptive**:
  - Proses dengan burst time terkecil dan sudah tiba selalu diprioritaskan.
- **Response Time = Waiting Time**, karena proses langsung dijalankan tanpa preemption.
- **Tidak ada idle time**, CPU selalu digunakan tanpa jeda selama semua proses tersedia sesuai dengan waktunya.


## 3. SRTF Scheduling Algorithm (Preemptive)

###Code Program
```c
#include<stdio.h>
#define MAX 9999
struct proc
{
    int no,at,bt,rt,ct,tat,wt;
};
struct proc read(int i)
{
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no=i;
    printf("Enter Arrival Time: ");
    scanf("%d",&p.at);
    printf("Enter Burst Time: ");
    scanf("%d",&p.bt);
    p.rt=p.bt;
    return p;
}
int main()
{
    struct proc p[10],temp;
    float avgtat=0,avgwt=0;
    int n,s,remain=0,time;
    printf("<--SRTF Scheduling Algorithm (Preemptive)-->\n");
    printf("Enter Number of Processes: ");
    scanf("%d",&n);
    for(int i=0;i<n;i++)
        p[i]=read(i+1);
    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)    
            if(p[j].at>p[j+1].at)
            {
                temp=p[j];
                p[j]=p[j+1];
                p[j+1]=temp;
            }
    printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\n");
    p[9].rt=MAX;
    for(time=0;remain!=n;time++)
    {
        s=9;
        for(int i=0;i<n;i++)
            if(p[i].at<=time&&p[i].rt<p[s].rt&&p[i].rt>0)
                s=i;
        p[s].rt--;
        if(p[s].rt==0)
        {
            remain++;
            p[s].ct=time+1;
            p[s].tat=p[s].ct-p[s].at;
            avgtat+=p[s].tat;
            p[s].wt=p[s].tat-p[s].bt;
            avgwt+=p[s].wt;
            printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n",p[s].no,p[s].at,p[s].bt,p[s].ct,p[s].tat,p[s].wt);
        }
    }
    avgtat/=n,avgwt/=n;
    printf("\nAverage TurnAroundTime=%f\nAverage WaitingTime=%f",avgtat,avgwt);
}
```

###Analisa

**Struktur Data**
```c
struct proc {
    int no, at, bt, rt, ct, tat, wt;
};
```
- `no` = Nomor urut  proses (misal: P1, P2, dst)
- `at` = Arrival Time (waktu datang)
- `bt` = Burst Time (lama eksekusi proses)
- `rt` = Remaining Time (waktu sisa eksekusi)
- `ct` = Completion Time (waktu selesai)
- `tat` = Turnaround Time (waktu penyelesaian total : ct - at)
- `wt` = Waiting Time (waktu tunggu: tat - bt)

**Fungsi read(int i)**
```c
struct proc read(int i) {
    struct proc p;
    printf("\nProcess No: %d\n",i);
    p.no = i;
    printf("Enter Arrival Time: ");
    scanf("%d", &p.at);
    printf("Enter Burst Time: ");
    scanf("%d", &p.bt);
    p.rt = p.bt;  // Initialize remaining time with burst time
    return p;
}
```
-sebagai nomer proses
-waktu kedatangan(AT)
-Lamanya proses

**Fungsi main()**
```c
int main() {
```

**Deklarasi dan Input Awal**
```c
struct proc p[10], temp;
float avgtat = 0, avgwt = 0;
int n, s, remain = 0, time;
```
-`p[10]`: array maksimum 10 proses
-`temp`: variabel bantu untuk sorting
-`avgtat, avgwt`: akumulator rata-rata TAT dan W
-`n`: jumlah proses
-`remain`: menghitung jumlah proses yang telah selesai
-`time`: waktu simulasi berjalan

** Input Jumlah Proses**
```c
printf("Enter Number of Processes: ");
scanf("%d", &n);
for(int i=0; i<n; i++)
    p[i] = read(i+1);

```
-Input awal yang berupa jumlah proses

**Sorting Berdasarkan Arrival Time**
```c
for(int i=0; i<n-1; i++)
    for(int j=0; j<n-i-1; j++)
        if(p[j].at > p[j+1].at) {
            temp = p[j];
            p[j] = p[j+1];
            p[j+1] = temp;
        }

```
-Proses diurutkan sesuai dengan waktu kedatangan.

**Header Tabel Output**
```c
printf("\nProcess\t\tAT\tBT\tCT\tTAT\tWT\n");

```
-Menampilkan judul kolom untuk hasil akhirnya

** Inisialisasi Proses Dummy**
```c
p[9].rt = MAX;

```
-Sebagai sentinel dalam pencarian proses

**Loop Eksekusi Algoritma SRTF**
```c
for(time = 0; remain != n; time++) {
    s = 9;
    for(int i = 0; i < n; i++)
        if(p[i].at <= time && p[i].rt < p[s].rt && p[i].rt > 0)
            s = i;


```
-Proses dengan sisa waktu terkecil yang telah datang akan dieksekusi.
**Eksekusi Proses Terpilih**
```c
p[s].rt--;

```
**Proses Selesai**
```c
if(p[s].rt == 0) {
    remain++;
    p[s].ct = time + 1;
    p[s].tat = p[s].ct - p[s].at;
    avgtat += p[s].tat;
    p[s].wt = p[s].tat - p[s].bt;
    avgwt += p[s].wt;
    printf("P%d\t\t%d\t%d\t%d\t%d\t%d\n", p[s].no, p[s].at, p[s].bt, p[s].ct, p[s].tat, p[s].wt);
}

```
-Jika proses selesai( rt == 0 ), maka dihitung:Completion Time (CT), Turnaround Time (TAT), Waiting Time (WT).

**Perhitungan Rata-Rata**
```c
avgtat /= n;
avgwt /= n;
printf("\nAverage TurnAroundTime = %f\nAverage WaitingTime = %f", avgtat, avgwt);

```
-Menghitung dan mencetak rata-rata TAT dan WT.

###output proses


**Input Proses**
- P1: at=0, bt=7  
- P2: at=2, bt=4  
- P3: at=4, bt=1  
- P4: at=5, bt=4 

**Jalannya Proses**

Waktu 0-2: P1 berjalan (RT dari 7 → 5)
Waktu 2: P2 masuk dan punya RT lebih kecil (4), alihkan ke P2
Waktu 4: P3 masuk (RT=1) lebih kecil dari P2, alihkan ke P3
Waktu 5: P3 selesai → CT=5, TAT=1, WT=0
Waktu 5-7: P2 lanjut → CT=7, TAT=5, WT=1
Waktu 7-11: P4 masuk → CT=11, TAT=6, WT=2
Waktu 11-16: P1 lanjut hingga selesai → CT=16, TAT=16, WT=9
**Rata-rata**
-Turnaround Time: (1 + 5 + 6 + 16) / 4 = 7.0
-Waiting Time: (0 + 1 + 2 + 9) / 4 = 3.0
## Kesimpulan
## Kesimpulan
1. **SRTF** adalah cara penjadwalan proses di mana proses yang sisa waktunya paling sedikit akan dijalankan lebih dulu.
2. Proses yang cepat selesai akan langsung dikerjakan lebih awal, meskipun datang belakangan.
3. Proses yang lama bisa tertunda kalau ada proses lain yang lebih cepat.
4. Hasil dari program:
   - Rata-rata waktu proses selesai: **7.0**
   - Rata-rata waktu menunggu: **3.0**
5. Ini menunjukkan bahwa algoritma SRTF cukup bagus karena bisa menyelesaikan proses-proses cepat lebih dulu.
6. Tapi, proses yang lama bisa menunggu terlalu lama jika terus-menerus ada proses baru yang lebih cepat.

