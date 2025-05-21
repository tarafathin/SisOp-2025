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
