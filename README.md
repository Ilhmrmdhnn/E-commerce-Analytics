# 20240827_Perqara_Assessment_Data Scientist

# E-commerce Analytics Project

## Deskripsi

Proyek ini melibatkan analisis komprehensif dataset (e-commerce), mencakup berbagai aspek seperti perilaku pelanggan, kinerja produk, dan pola pemesanan. Analisis meliputi persiapan data, analitik dasar dan lanjutan, serta pemodelan prediktif untuk nilai pemesanan dan status pesanan.

### Fitur Utama
- Integrasi data dari sumber yang diberikan
- Peramalan time series volume pesanan
- Analisis geospasial distribusi pelanggan
- Segmentasi pelanggan RFM (Recency, Frequency, Monetary)
- Deteksi outlier pada nilai pembayaran
- Pemodelan prediktif untuk nilai pesanan dan status pesanan

### Tujuan
- Mendapatkan wawasan yang dapat ditindaklanjuti dari dataset e-commerce
- Mengembangkan model prediktif untuk memperkirakan nilai pesanan dan status pesanan
- Melakukan segmentasi pelanggan berdasarkan perilaku pembelian mereka (RFM)
- Mengidentifikasi tren dan pola dalam data pesanan

## Persiapan Data

### ERD

![Assasment Data Science](https://github.com/user-attachments/assets/9e18e52a-07aa-44db-9aad-62046b1a4698)

Proses persiapan data melibatkan penggabungan beberapa dataset:
- Customers Dataset
- Geolocation Dataset
- Order Items Dataset
- Order Payments Dataset
- Order Reviews Dataset
- Orders Dataset
- Product Category Name Translation
- Product Dataset
- Sellers Dataset

### Langkah-langkah Kunci dalam Persiapan Data:
- Pembersihaan setiap datasets
	- Size
	- Duplicate
	- Missing Value
- Penggabungan dataset yang relevan menjadi 1 kesatuan
- Penanganan nilai yang hilang menggunakan imputasi mean
- Konversi kolom tanggal ke format datetime
- Rekayasa fitur (misalnya, menghitung hari pengiriman)
- Normalisasi fitur numerik
- Features Engineering

# Analisis Dasar
Fase analisis dasar mengungkapkan beberapa wawasan:

## Describe Stats:

![Describe](https://github.com/user-attachments/assets/2a328c11-6698-4d3e-9be8-0d11a2860416)

Data ini menunjukkan data deskriptif untuk berbagai fitur yang terkait dengan pesanan online. Berikut adalah deskripsi dan interpretasi untuk setiap fitur:
### Fitur dan Interpretasi
- **order_purchase_timestamp**: Tanggal dan waktu ketika pesanan dibuat.  
  Rentang tanggal: Oktober 2016 - Agustus 2018  
  Rata-rata tanggal pembelian: Desember 2017
- **order_delivered_customer_date**: Tanggal dan waktu ketika pesanan dikirimkan ke pelanggan.  
  Rentang tanggal: Oktober 2016 - Oktober 2018  
  Rata-rata tanggal pengiriman: Januari 2018
- **order_estimated_delivery_date**: Tanggal dan waktu yang diperkirakan untuk pengiriman pesanan.  
  Rentang tanggal: Oktober 2016 - Oktober 2018  
  Rata-rata tanggal pengiriman yang diperkirakan: Januari 2018
- **customer_zip_code_prefix**: Kode pos pelanggan yang dipotong.  
  Rentang kode pos: 1003 - 99980  
  Rata-rata kode pos: 34320
- **order_item_id**: ID unik untuk setiap item dalam pesanan.  
  Rentang ID item: 1 - 21  
  Rata-rata ID item: 1
- **price**: Harga item dalam pesanan.  
  Rentang harga: 0.85 - 6735  
  Rata-rata harga: 122
- **freight_value**: Biaya pengiriman untuk pesanan.  
  Rentang biaya pengiriman: 0 - 375.28  
  Rata-rata biaya pengiriman: 20
- **payment_sequential**: Nomor urut pembayaran untuk pesanan.  
  Rentang nomor urut pembayaran: 1 - 13  
  Rata-rata nomor urut pembayaran: 1
- **payment_installments**: Jumlah cicilan pembayaran untuk pesanan.  
  Rentang jumlah cicilan: 1 - 24  
  Rata-rata jumlah cicilan: 3
- **payment_value**: Nilai total pembayaran untuk pesanan.  
  Rentang nilai pembayaran: 0 - 13664.08  
  Rata-rata nilai pembayaran: 185
- **review_score**: Skor ulasan pelanggan untuk pesanan.  
  Rentang skor ulasan: 1 - 5  
  Rata-rata skor ulasan: 3.6
- **product_name_length**: Panjang nama produk dalam karakter.  
  Rentang panjang nama produk: 5 - 720  
  Rata-rata panjang nama produk: 48
- **product_description_length**: Panjang deskripsi produk dalam karakter.  
  Rentang panjang deskripsi produk: 4 - 3992  
  Rata-rata panjang deskripsi produk: 769
- **product_photos_qty**: Jumlah foto produk dalam pesanan.  
  Rentang jumlah foto: 1 - 19  
  Rata-rata jumlah foto: 2
- **product_weight_g**: Berat produk dalam gram.  
  Rentang berat produk: 0 - 30000  
  Rata-rata berat produk: 2274
- **product_length_cm**: Panjang produk dalam sentimeter.  
  Rentang panjang produk: 7 - 105  
  Rata-rata panjang produk: 30
- **product_height_cm**: Tinggi produk dalam sentimeter.  
  Rentang tinggi produk: 2 - 105  
  Rata-rata tinggi produk: 17
- **product_width_cm**: Lebar produk dalam sentimeter.  
  Rentang lebar produk: 6 - 118  
  Rata-rata lebar produk: 23
- **seller_zip_code_prefix**: Kode pos penjual yang dipotong.  
  Rentang kode pos: 1001 - 99730  
  Rata-rata kode pos: 24343
- **geolocation_zip_code_prefix**: Kode pos lokasi geografis yang dipotong.  
  Rentang kode pos: 1003 - 99980  
  Rata-rata kode pos: 34320
- **geolocation_lat**: Lintang lokasi geografis.  
  Rentang lintang: -36.605374 - 42.428884  
  Rata-rata lintang: -21.669125
- **geolocation_lng**: Bujur lokasi geografis.  
  Rentang bujur: -101.466766 - -4.947823  
  Rata-rata bujur: -46.00489
- **order_delivery_days**: Jumlah hari yang dibutuhkan untuk mengirimkan pesanan.  
  Rentang jumlah hari: 0 - 195  
  Rata-rata jumlah hari: 12
- **estimated_delivery_days**: Jumlah hari yang diperkirakan untuk mengirimkan pesanan.  
  Rentang jumlah hari: 2 - 155  
  Rata-rata jumlah hari: 24

### Interpretasi

Data ini dapat digunakan untuk memahami pola pembelian, perilaku pengiriman, dan preferensi pelanggan:
- **Waktu Pengiriman**: Rata-rata waktu pengiriman sekitar 12 hari, sementara waktu pengiriman yang diperkirakan sekitar 24 hari, menunjukkan bahwa pengiriman seringkali lebih cepat dari yang diperkirakan.
- **Biaya Pengiriman**: Rata-rata biaya pengiriman sekitar 20, menunjukkan bahwa pengiriman merupakan bagian penting dari biaya pesanan.
- **Peningkatan Area**: Data ini dapat digunakan untuk mengidentifikasi area yang perlu ditingkatkan, seperti waktu pengiriman yang tidak akurat atau biaya pengiriman yang tinggi.

### Distribusi Status Pesanan:

![Order Status](https://github.com/user-attachments/assets/dc7ee13e-10f9-4851-8d93-9003460dbb53)

- **Delivered**: 4759405
- **Canceled**: 612

**Insight**: Mayoritas pesanan berhasil dikirimkan, dengan tingkat pembatalan yang relatif rendah.

### 10 Kategori Produk Teratas berdasarkan Nilai Pesanan Rata-rata:

![Top 10](https://github.com/user-attachments/assets/583fe5c6-4209-4481-abfe-2bf357802b4c)

- **Computers**
- **Fixed Telephony** 
- **Signaling and Security**
- **Furniture Living Room**
- **Home Appliances 2**
- **Small Appliances Home Oven and Coffee**
- ** Agro Industry and Commerce**
- **Office Furniture**
- **Musical Instrument**
- **Air Conditioning**

**Insight**: Kategori Computers dan Fixed Telephony memiliki nilai pesanan rata-rata tertinggi, diikuti oleh Signaling and Security dan Furniture Living Room.

### Analisis Korelasi:

![Correlation Heatmap](https://github.com/user-attachments/assets/6c3c470d-b0d4-4af0-b1a3-19ef32f08a3e)

- Korelasi positif tinggi antara 'customer_zip_code_prefix' dan 'geolocation_zip_code_prefix' (1.00)
- Korelasi positif lainnya antara 'price' dan 'payment_value' (0.72)

**Insight**: Harga produk sangat mempengaruhi nilai pembayaran, serta customer prefix sangat mempengaruhi geolocation prefix

### Boxplot

![Boxplot Price](https://github.com/user-attachments/assets/7387d582-bc7d-4beb-9fa4-9e50ed98514f)

- pada kolom 'price' memiliki outliers akan tetapi tidak dilakukan pendropan data dikarenakan akan ilang banyak informasi penting nantinya.

### Tren Volume Pesanan Harian:

![Daily Order Volume](https://github.com/user-attachments/assets/2493f990-18a2-42f8-8573-a8f001bfc014)

- Tren menunjukkan pergerakan yang fluktuatif volume pesanan dari waktu ke waktu.
- Fluktuasi mingguan terlihat jelas, dengan penurunan pada akhir pekan

### Tren Volume Pesanan Bulanan:

![Monthly Order Volume](https://github.com/user-attachments/assets/fa25a99d-3d7f-4c94-897d-69e074a609dc)

- Tren  menunjukkan peningkatan volume pesanan dari bulan ke bulan

**Insight**: Bisnis e-commerce ini menunjukkan pertumbuhan, dengan pola permintaan yang konsisten.

## Analisis Lanjutan

### Peramalan Time Series
- **Metodologi**: Model ARIMA
- **Horizon Peramalan**: 365 hari dan 12 bulan
- **Daily** dan **Monhtly**

![Order Volume Forecast 1 Year (Daily)](https://github.com/user-attachments/assets/ab145fb2-1bca-4426-af0e-62398b156cdc)
![Order Volume Forecast 1 Year (Monthly)](https://github.com/user-attachments/assets/7fdb2056-c1e2-4e5b-b868-f8c8d0c75a6a)

#### Temuan Utama:
- **Daily** Model memprediksi tren peningkatan volume pesanan untuk 365 hari ke depan akan tetapi akan menjadi flat pada waktu yang cukup panjang dikarenkan kurang fluktuatif data historicalnya
- **Monthly** Model memprediksi tren peningkatan volumen pesanan untuk 12 bulan kedepan yang mengalami peningkatan setiap bulannya.

### Analisis Geo
- **Distribusi Geografis Pelanggan**:
![Cust Geo Distribution](https://github.com/user-attachments/assets/c4142a4d-54aa-48e3-8b02-c88f3220ee6e)

#### Wawasan:
- Konsentrasi pelanggan tinggi di wilayah sao paulo, guarulhos dan sao bernardo do campo

### Deteksi Outlier
- **Metode**: Elliptic Envelope

![Payment Value Outliers](https://github.com/user-attachments/assets/cffbe4ed-3f03-41a5-80cd-07fd62ec53ed)

#### Temuan:
- Sekitar 10% dari nilai pembayaran teridentifikasi sebagai outlier
- Outlier umumnya merupakan transaksi dengan nilai sangat tinggi

### Analisis RFM
- **Segmentasi**: 4 cluster pelanggan teridentifikasi
![Elbow Method](https://github.com/user-attachments/assets/5a4647d2-a03b-44e8-8d25-a2bb4a18cf0e)
![Visual RFM](https://github.com/user-attachments/assets/9abc1847-cabf-4bc6-a6bb-06610fe036a6)
![Visual RFM 3D](https://github.com/user-attachments/assets/c456aaab-8463-416b-8d1a-31356a4c28a3)
![Cluster Stat RFM](https://github.com/user-attachments/assets/f395149a-52f0-4bc4-a72f-b5be7be8ac77)
![RFM Summary](https://github.com/user-attachments/assets/29e6d86b-5fb1-41dc-969f-f8680dc9f2cb)

### Segmentasi Pelanggan
### 1. Pelanggan Utama
- **Frekuensi pembelian**: Sangat tinggi
- **Nilai moneter**: Sangat tinggi
- **Karakteristik**: Pelanggan paling berharga dan loyal

### 2. Pelanggan Potensial
- **Frekuensi dan nilai moneter**: Menengah
- **Recency**: Cukup baik
- **Karakteristik**: Berpotensi ditingkatkan menjadi pelanggan utama

### 3. Pelanggan Baru
- **Recency**: Rendah (baru-baru ini melakukan transaksi)
- **Frekuensi dan nilai moneter**: Masih rendah
- **Karakteristik**: Perlu strategi untuk meningkatkan loyalitas

### 4. Pelanggan Pasif
- **Recency**: Tinggi (lama tidak bertransaksi)
- **Frekuensi dan nilai moneter**: Rendah
- **Karakteristik**: Perlu strategi reaktivasi


## Pemodelan Prediktif

### Model Prediksi Status Pesanan
- **Model**: Random Forest Classifier
- **Variabel Target**: Status Pesanan

#### Performa Model:
![Classification Report (Order Status)](https://github.com/user-attachments/assets/0c5898f6-db36-4f57-ab1d-c9b07b8bfb39)

- **Accuracy**: 1
- **F1-score (weighted average)**: 1

#### Confusion Matrix
![CM (Order Status)](https://github.com/user-attachments/assets/e28b2329-6212-46b8-82e4-0553e39e22a2)

#### Kepentingan Fitur Teratas:
![Features Importan (Order Status)](https://github.com/user-attachments/assets/3cd05ed7-ae41-488e-b8d8-18bdcdf62ba4)

- **estimated_delivery_days**
- **freight_value**
- **order_delivery_days**
- **product_weight_g**
- **product_name_length**

**Insight**: Model memiliki akurasi tinggi dalam memprediksi status pesanan, dengan variale diatas yang menjadi predictor utama

### Model Prediksi Nilai Pesanan
- **Model**: Random Forest Regressor
- **Variabel Target**: Nilai Pembayaran

#### Performa Model:

![evaluasi (Payment Value)](https://github.com/user-attachments/assets/3511b2ad-0d4a-48c6-92cc-b6ccbc64dd89)

- **Mean Squared Error**: 575.9692311025973
- **R-squared Score**: 0.992264227932851

#### Kepentingan Fitur Teratas:

![Features Importan (Payment Value)](https://github.com/user-attachments/assets/dedb39e9-c11f-47ea-8161-44eb68799e17)

- **price**
- **freight_value**
- **product_description_length**
- **product_name_length**
- **review_score**

**Insight**: Model menunjukkan performa yang baik dalam memprediksi nilai pesanan, dengan harga produk sebagai prediktor paling signifikan.



## Wawasan Utama
- Mayoritas pesanan (99.99%) berhasil dikirimkan, menunjukkan efisiensi operasional yang tinggi.
- Kategori produk seperti Computers, aksesori komputer, dan Fixed Telephony menghasilkan nilai pesanan tertinggi, menjadi target potensial untuk promosi.
- Terdapat pola tren yang jelas dalam volume pesanan, dengan penurunan pada akhir pekan, yang dapat dimanfaatkan untuk strategi pemasaran.
- Konsentrasi pelanggan tinggi di wilayah sao paulo, menunjukkan potensi untuk ekspansi pasar di wilayah lain.
- Segmentasi pelanggan mengungkapkan empat kelompok utama, memungkinkan strategi pemasaran yang lebih terpersonalisasi.

## Rekomendasi
- Fokuskan upaya pemasaran pada kategori produk bernilai tinggi seperti komputer dan Fixed Telephony.
- Implementasikan strategi retensi untuk pelanggan di Cluster 0 (Pelanggan Pasif) untuk meningkatkan frekuensi pembelian mereka.
- Optimalkan inventaris dan sumber daya pengiriman berdasarkan pola permintaan yang teridentifikasi.
- Pertimbangkan kampanye pemasaran khusus untuk meningkatkan penjualan di setiap pekan.
- Eksplorasi peluang ekspansi ke wilayah dengan konsentrasi pelanggan yang lebih rendah.

## Cara Menggunakan Repositori Ini
1. Clone repositori
2. Instal dependensi yang diperlukan: `pip install -r requirements.txt`
3. Jalankan script dalam urutan berikut:
   - `assesment.py`
4. Lihat visualisasi yang dihasilkan di folder `visualizations`
5. Periksa folder `models` untuk model prediktif yang disimpan

## Kontributor
Ilham Ramadhan Nur Ahmad
