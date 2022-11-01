# Airline_Customer_Segmentation
**Customer segmentation using K-Means clustering (unsupervised ML)**

## Background
**Dataset Introduction & Problem Statement:** <br>
<div align='justify'>

Manajemen hubungan dengan pelanggan adalah inti bisnis perusahaan. Kunci manajemen pelanggan adalah segmentasi pelanggan. 
Berdasarkan segmentasi pelanggan perusahaan dapat membedakan antara pelanggan yang tidak bernilai dengan pelanggan yang 
bernilai tinggi. Dengan mengetahui hal tersebut perusahaan kemudian dapat merumuskan rencana pelayanan yang dipersonalisasi
untuk masing-masing pelanggan, melakukan strategi pemasaran yang berbeda dan memfokuskan sumber daya perusahaan yang terbatas
pada pelanggan yang bernilai tinggi sehingga dapat memaksimalkan keuntungan perusahaan.

Segmentasi traditional biasa dilakukan dengan melihat nilai rata-rata dari suatu variabel kemudian membagi pelanggan menjadi
pelanggan yang memiliki nilai lebih dari rata-rata dan di bawah rata-rata, pembagian tersebut kurang efektif dan terkadang 
menyebabkan terlalu banyak kelompok pelanggan yang terbagi sehingga meningkatkan biaya pemasaran yang ditargetkan. Oleh karena itu,
metode clustering K-Means digunakan untuk mengidentifikasi nilai pelanggan sehingga pelanggan yang paling berharga dapat diidentifikasi.

Di sini, saya menggunakan dataset perusahaan penerbangan untuk membuat segmentasi pelanggan, menganalisis profil pelanggan untuk setiap
cluster yang diperoleh dan memberikan rekomendasi bisnis yang sesuai.

## Files
Repository ini berisi README, sebuah notebook python bernama Airline_Customer_Segmentation.ipynb dan dataset itu sendiri.

## Data Dictionary
|Variable|Description|
|--|--|
|MEMBER_NO| ID MEMBER|
|FFP_DATE| Tanggal bergabung ke dalam Frequent Flyier Program|
|FIRST_FLIGHT_DATE| Tanggal Penerbangan Pertama|
|GENDER| Jenis Kelamin|
|FFP_TIER| Tier dari Frequent Flyier Program|
|WORK_CITY| Kota asal|
|WORK_PROVINCE| Provinsi asal|
|WORK_COUNTRY| Negara asal|
|AGE| Umur customer|
|LOAD_TIME| Tanggal data diambil|
|FLIGHT_COUNT| Jumlah penerbangan customer|
|BP_SUM| Total basic integral|
|SUM_YR_1| Fare revenue|
|SUM_YR_2| Votes prices|
|SEG_KM_SUM| Total jarak penerbangan yang dilakukan (km)|
|LAST_FLIGHT_DATE| Tanggal penerbangan terakhir|
|LAST_TO_END| Waktu dari penerbangan terakhir hingga waktu data diperoleh|
|AVG_INTERVAL| Interval waktu penerbangan rata-rata|
|MAX_INTERVAL| Interval penerbangan maksimum|
|avg_discount| Rata-rata discount yang diperoleh customer|
|EXCHANGE_COUNT| Jumlah penukaran poin|
|Points_Sum| Total poin yang diperoleh customer|
|Point_NotFlight| Poin yang tidak digunakan customer|

## Methods
Proses yang kami lakukan secara garis besar adalah:
### **1. EDA**
 - Descriptive Statistics
 - Univariate Analysis
 - Multivariate Analysis
### **2. Preprocessing**
 - Handle Missing Values
 - Feature Engineering
   * Feature Extraction
   * Feature Selection:
      Pada project ini saya menggunakan model LRFMC untuk membuat segmentasi khusus untuk pelanggan perusahaan penerbangan,
      model ini merupakan pengembangan dari model umum RFM.
 - Feature transformation: BoxCox
 - Standardization
### **3. Modeling** 
Algoritma K-means digunakan untuk mengelompokkan pelanggan, sementara untuk menentukan jumlah cluster (nilai-k) yang optimal
saya menggunakan elbow method dan silhouette score. Setelah clustering selesai dilakukan kemudian setiap cluster dianalisis dari nilai LRFMC
untuk dilihat karakteristiknya.

Project ini membutuhkan paket standar pandas, numpy, matplotlib, seaborn, sklearn, dan yellowbrick untuk memvisualisasikan skor siluet. 
Jika ingin melakukan pengujian yang sama maka perlu menginstal paket ini terlebih dahulu.

## Result
Berdasarkan elbow method dan silhouette score jumlah cluster terbaik adalah 2. 
Kedua cluster yang diperoleh memiliki nilai LRFMC yang berbeda. Segmentasi pelanggan untuk metrik LRFMC menunjukkan cluster 1 
merupakan customer yang lebih bernilai dibandingkan dengan cluster 0 untuk perusahaan. Apabila dibandingkan dengan
segmentasi yang dimiliki perusahaan sebelumnya yaitu pada feature FFP_TIER, segmentasi tersebut masih belum 
ideal dalam memisahkan anggota cluster sehingga hasil clustering menggunakan KMeans dapat menggantikannya.
