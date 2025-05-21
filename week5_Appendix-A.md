# Operating System Concepts (Silberschatz, 2018)

## 1. Apa Itu Sistem Operasi?

Sistem operasi (OS) adalah program utama yang mengatur cara kerja komputer. OS menghubungkan pengguna dengan perangkat keras komputer.

### Fungsi Utama OS:
- **Proses**: Menjalankan dan mengatur program yang aktif.
- **Memori**: Mengatur penggunaan RAM.
- **Penyimpanan**: Mengelola file dan folder di hard disk.
- **Perangkat I/O**: Mengontrol keyboard, mouse, printer, dll.
- **Keamanan**: Melindungi data dari akses yang tidak sah.

*Contoh OS: Windows, Linux, macOS, Android.*

## 2. Bagaimana OS Mengelola Proses?

**Proses** = program yang sedang dijalankan.

### Komponen Proses:
- **PCB**: Tempat menyimpan informasi proses.
- **Context Switch**: OS berganti dari satu proses ke proses lain.
- **Scheduler**: Memilih proses mana yang akan dijalankan duluan.

### Jenis Penjadwalan:
| Jenis | Penjelasan Singkat |
|------|---------------------|
| FCFS | Siapa cepat dia dapat |
| SJF  | Proses tercepat dijalankan dulu |
| Round Robin | Giliran waktu jalan tiap proses |

*IPC (Interprocess Communication)* digunakan untuk komunikasi antar proses: bisa lewat memori bersama atau pesan.

## 3. Bagaimana OS Mengatur Memori?

**Memori** dipakai oleh program saat berjalan. OS bertugas mengalokasikan memori agar efisien.

### Teknik Alokasi:
- **Statis**: Ukuran tetap (bisa boros).
- **Dinamis**: Ukuran fleksibel.
- **Paging**: Dibagi jadi bagian kecil (page).
- **Segmentation**: Dibagi berdasarkan jenis data (kode, stack, data).

### Memori Virtual:
Membantu program seolah punya memori besar meskipun RAM kecil.

- **Demand Paging**: Hanya memuat yang dibutuhkan.
- **Penggantian Halaman**: FIFO, LRU, Optimal.

## 4. Bagaimana File & Disk Dikelola?

OS bertugas menyimpan dan membaca file di penyimpanan.

### Struktur Direktori:
- **Single-Level**: Semua file di satu tempat.
- **Two-Level**: Tiap user punya direktori sendiri.
- **Tree**: Seperti folder dan subfolder.
- **Acyclic Graph**: Bisa shortcut antar file.
- **General Graph**: Bebas, tapi rawan loop.

### Penjadwalan Disk:
| Algoritma | Penjelasan |
|-----------|------------|
| FCFS | Berdasarkan urutan permintaan |
| SSTF | Yang paling dekat diakses dulu |
| SCAN | Kepala disk bergerak maju-mundur |

## 5. Bagaimana OS Menjaga Keamanan?

OS harus mencegah akses tak sah dan menjaga data tetap aman.

### Ancaman:
- **Malware**: Virus, worm, trojan, ransomware.
- **DoS**: Membuat sistem sibuk terus.
- **Phishing**: Tipu daya untuk ambil data.

### Solusi:
- **Autentikasi**: Login dengan password, biometrik, atau OTP.
- **Enkripsi**: Data diacak agar tidak bisa dibaca sembarangan.
- **ACL (Access Control List)**: Siapa boleh akses apa.

**Kesimpulan**: Sistem operasi adalah otak dari komputer modern. Ia mengatur segala hal mulai dari jalannya program, penggunaan memori, penyimpanan data, hingga keamanan pengguna. Tanpa OS, komputer hanyalah kumpulan perangkat keras yang tidak bisa digunakan secara praktis.

