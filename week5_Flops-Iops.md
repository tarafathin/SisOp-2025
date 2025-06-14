# Pengujian FLOPS dan IOPS di WSL

## Tujuan
- Mengerti apa itu FLOPS dan IOPS.
- Mengetahui performa CPU dalam operasi angka floating-point dan integer.
- Belajar cara menjalankan benchmark FLOPS dan IOPS di WSL.

## Penjelasan Singkat

### FLOPS (Floating Point Operations Per Second)
Mengukur berapa banyak operasi angka desimal (floating point) yang bisa CPU lakukan per detik. Biasanya dipakai untuk menghitung performa komputer dalam bidang ilmiah atau grafik.

### IOPS (Integer Operations Per Second)
Mengukur berapa banyak operasi bilangan bulat (integer) yang bisa CPU lakukan per detik. Penting untuk aplikasi yang banyak mengolah data atau enkripsi.

### WSL (Windows Subsystem for Linux)
Fitur Windows yang memungkinkan kita menjalankan Linux langsung di Windows tanpa perlu dual boot.

## Langkah-Langkah Pengujian

1. **Pasang WSL** (jika belum ada)  
   Buka PowerShell, jalankan:  
   ```powershell
   wsl --install
   
2. **Buka Terminal WSL**
   Buka terminal WSL melalui menu Start atau aplikasi terminal pilihan Anda.

3. **Perbarui Paket dan Instal Dependensi**
   ```bash
   sudo apt update && sudo apt install -y build-essential
   ```
   
4. **Clone Repository FLOPS-IOPS**
   ```bash
   git clone https://github.com/ferryastika/flops-iops.git
   cd flops-iops
   ```
   
5. **Build Program Benchmark**
   ```bash
   make
   ```
   
6. **Jalankan Pengujian FLOPS dan IOPS**
   Jalankan benchmark dengan jumlah thread sesuai dengan jumlah core CPU       Anda:
   ```bash
   ./iops32 $(nproc)
   ./iops64 $(nproc)
   ./flops32 $(nproc)
   ./flops64 $(nproc)
   ```

   ---

## Analisa
- **IOPS Benchmark**: Mengukur jumlah operasi integer yang dapat diproses CPU dalam satu detik.
- **FLOPS Benchmark**: Mengukur jumlah operasi floating point yang dapat dilakukan CPU dalam satu detik.
- **Hasil Pengujian** dapat digunakan untuk membandingkan performa CPU dengan spesifikasi yang berbeda.
- **Semakin tinggi nilai FLOPS dan IOPS**, semakin cepat CPU dalam menangani operasi aritmetika dan komputasi ilmiah.

## Kesimpulan
- FLOPS dan IOPS adalah metrik penting dalam mengevaluasi performa CPU.
- WSL memungkinkan pengguna menjalankan benchmark sistem Linux langsung di Windows.
- Pengujian ini memberikan wawasan tentang kemampuan komputasi numerik CPU untuk berbagai kebutuhan aplikasi.
- Hasil yang diperoleh dapat digunakan sebagai bahan analisis untuk memilih prosesor yang sesuai dengan kebutuhan spesifik.
