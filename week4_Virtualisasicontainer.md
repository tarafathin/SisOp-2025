# Virtualisasi Container

## 1. Pengertian Virtualisasi Container
Virtualisasi adalah cara menjalankan banyak sistem atau aplikasi terpisah dalam satu komputer.

## 2. jenis Virtualisasi Container di linux
- **Virtualisasi Lengkap**=Menggunakan platform seperti KVM/QEMU untuk membuat mesin virtual yang komplit.
- **Virtualisasi Ringan**=Teknologi seperti LXD menyediakan lingkungan sistem operasi yang terisolasi.
- **Isolasi Proses**=Solusi berbasis container seperti Podman dan Docker.
- **Subsistem Kompatibilitas**=WSL2 yang menggabungkan keunggulan dari container dan virtualisasi.

## 3. implementasi Praktis
### a. VirtualBox (bagi Pemula)
Dapat mengeksekusi berbagai sistem operasi, perangkat virtual yang fleksibel, Snapshot untuk pengembalian sistem.

**Kelebihan**
- mendukung berbagai sistem operasi
- fitur jaringan yang komprehensif

**Kekurangan**
- overhead yang signifikan
- konsumsi memo yang cukup tinggi
  
### b. Mesin Virtual Dedicated
Solusi seperti VMware ESXi dan Microsoft Hyper-V seperti isolasi perangkat yang penuh,menejemen resource yang spesifik,mendapat dukungan untuk live migration.

**Kelebihan**
- Keamanan yang tingkat tinggi
- Kompatibilitas perangkat keras lebih luas
- Kemampuan clustering

**Kekurangan**
- Persyaratan resource yang cukup besar
- Kompleksitas manajemen
  
### c. WSL (Linux di Windows)
mendapatkan kernel linux asli pada windows, Integrasi filesystem yang mulus, terdaapt Dukungan GPU dan container.

**Kelebihan**
- Performa mendekati native
- Akses langsung ke perangkat Windows
- Update sistem yang otomatis

**Kekurangan**
- Dukungan GUI yang terbatas
- Isolasi jaringan yang kurang ketat

## 4. Analisis Perbandingan Teknologi

| Aspek          | Container Modern | Virtual Klasik | Subsistem Hibrida |
|----------------|------------------|----------------|-------------------|
| Overhead       | Minimal          | Signifikan     | Sedang            |
| Densitas       | Tinggi           | Rendah         | Menengah          |
| Portabilitas   | Sangat Baik      | Terbatas       | Baik              |
| Kompatibilitas | Terbatas         | Luas           | Spesifik          |
| Keamanan       | Cukup            | Sangat Kuat    | Menengah          |

## Kesimpulannya
setiap pilihan mempunyai kelebihan dan kekurannya masing-masing, sekain kuat isolasinyas amka semakin banyak resource yang dibutuhkan.
- jika RAM terbatas maka gunakan container/WSL.
- jika butuh keamanan ynag tinggi maka gunakna VM.
- jika untuk kebutuhan development modern maka gunakan docker.
