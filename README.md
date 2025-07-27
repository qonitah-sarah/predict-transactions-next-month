# Berapa Banyak Transaksi yang Akan Terjadi dalam Satu Bulan ke Depan? 

## Latar Belakang Proyek
Tribe Growth merupakan sebuah perusahaan yang memiliki platform e-commerce dengan tiga kategori produk utama: perlengkapan kantor, furnitur, dan teknologi. Selama empat tahun terakhir, penjualan berlangsung di wilayah Amerika Serikat, mencakup 502 kota.

Tim bisnis Tribe Growth meminta bantuan tim data untuk melakukan analisis terhadap transaksi harian yang terjadi pada platform, serta membangun model forecasting untuk memprediksi jumlah transaksi satu bulan ke depan. Hasil prediksi ini akan digunakan sebagai dasar dalam menyusun strategi bisnis yang lebih akurat dan berbasis data.

## Struktur Data dan Pemeriksaan Awal
Dataset historis penjualan berisi 8.000 baris data dengan 21 kolom, yang secara garis besar mencakup informasi mengenai:
- Identitas pelanggan
- Detail produk yang dibeli
- Informasi transaksi

Tidak ditemukan missing values di seluruh kolom. Struktur data telah sesuai kecuali pada kolom Order Date dan Ship Date yang masih berupa object dan perlu dikonversi ke format datetime.

##  Metode
Langkah-langkah yang dilakukan dalam proyek ini meliputi:
### 1. Data Cleaning
- Tidak ditemukan nilai duplikat maupun missing value.
- Kolom `Sales`, `Quantity`, `Discount`, dan `Profit` mengandung outlier berdasarkan visualisasi boxplot.

### 2. Exploratory Data Analysis (EDA)
- Menghitung total revenue, jumlah order, dan jumlah barang yang terjual sepanjang tahun 2017.
- Menghitung rata-rata jumlah barang yang dibeli per transaksi serta rata-rata spending per transaksi.
- Menghitung jumlah order dan GMV dalam rentang waktu harian, mingguan, dan bulanan.
- Mengidentifikasi produk yang paling sering dibeli dalam 1 tahun terakhir.
- Menentukan Top 10 produk dengan revenue terbesar untuk keperluan bundling.
- Mengidentifikasi 5 kota dengan jumlah order terbanyak.
- Mengidentifikasi 5 kota dengan total dan rata-rata spending terbesar.

### 3. Pemilihan Model
- Menyusun dataset penjualan yang digunakan untuk pemodelan.
- Menganalisis pola transaksi (harian, mingguan, bulanan, dan tahunan), termasuk seasonal decomposition.
- Menguji model baseline seperti **Naïve Forecaster** dan model utama **Prophet**.

### 4. Pemodelan Menggunakan Prophet
- Membangun model Prophet untuk memprediksi jumlah transaksi harian.
- Mengevaluasi performa model menggunakan metrik **MAPE (Mean Absolute Percentage Error)**.

### 5. Eksplorasi Hasil Prediksi
- Mengidentifikasi periode waktu hasil prediksi (1 bulan ke depan).
- Menganalisis statistik prediksi: nilai rata-rata, median, total transaksi, serta nilai maksimum dan minimum harian.

## Executive Summary
### Ikhtisar Temuan
Rata-rata pola harian menunjukkan bahwa transaksi tertinggi terjadi pada hari Senin dengan total 4 transaksi, kemudian mengalami penurunan signifikan dalam dua hari berikutnya. Untuk memprediksi jumlah transaksi harian selama 1 bulan ke depan (31 Desember 2017 hingga 29 Januari 2018), digunakan model Prophet yang menunjukkan performa lebih baik dibandingkan Naïve Forecaster, dengan nilai MAPE sebesar 28,17%. Diperkirakan akan terjadi total 82 transaksi, dengan rata-rata 3 transaksi per hari. Tren menunjukkan pola mingguan yang konsisten dan fluktuatif.

### Pola Rata-Rata Harian
<img width="975" height="261" alt="image" src="https://github.com/user-attachments/assets/5aab78f5-e239-4515-8684-37a5e62f5ffb" />

Rata-rata transaksi harian tertinggi tercatat pada hari Senin sebanyak 4 transaksi. Setelahnya terjadi penurunan tajam dalam dua hari berikutnya. Tren kembali meningkat pada hari Kamis dan menunjukkan fluktuasi yang cenderung stabil setelahnya.

### Prediksi dengan Model Prophet: Bagaimana Transaksi dalam 1 bulan ke depan?
<img width="975" height="261" alt="image" src="https://github.com/user-attachments/assets/977c089e-5391-48f8-853e-28182bae93ac" />

Periode prediksi dilakukan dari tanggal 31 Desember 2017 hingga 29 Januari 2018 yaitu berdurasi 1 bulan. Hasil prediksi menunjukkan total 82 transaksi dalam periode tersebut, dengan rata-rata 3 transaksi per hari. Transaksi tertinggi diprediksi terjadi pada tanggal 1 Januari (4 transaksi), sedangkan transaksi terendah pada tanggal 17 Januari (2 transaksi). Pola mingguan cenderung berulang, di mana dalam dua hari awal minggu (Rabu–Kamis) terjadi penurunan signifikan, kemudian kembali meningkat, diikuti oleh fluktuasi yang stabil di hari-hari berikutnya.

### Rekomendasi
- Meningkatkan aktivitas promosi dan pengiriman notifikasi di pertengahan minggu (midweek) saat terjadi penurunan transaksi
- Meningkatkan engagement dan memastikan operasional e-commerce bekerja optimal di dua hari awal dan di akhir pekan
- Menyesuaikan jumlah staf berdasarkan tren harian, yaitu menambah staf di akhir pekan dan mengurangi pada hari ketiga dan keempat
- Menjadwalkan kegiatan operasional seperti maintenance pada hari-hari dengan volume transaksi rendah
