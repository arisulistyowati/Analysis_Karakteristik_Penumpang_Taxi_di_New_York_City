# **Analysis Karakteristik Penumpang Taxi di New York City**

<br>

# **Latar Belakang**
<br>
Sebuah perusahaan baru yang bergerak dibidang pengelolaan transportasi umum yakni Green Taxi sedang giat dalam mengembangkan bisnisnya. Oleh karena itu, tim marketing meminta bantuan tim data analyst untuk mengeksplore informasi yang dapat membantu meningkatkan strategi pemasaran yang lebih efektif dan efisien.

<br>

# **Pernyataan Masalah**
<br>
Perusahaan ingin mengetahui bagaimana karakteristik dari penumpang taxi selama satu bulan terakhir. Informasi ini akan membantu perusahaan memahami profil pelanggan mereka secara lebih baik yang berguna untuk meningkatkan profit. 

<br>

# **Pertanyaan**
<br>
1. Daerah mana yang paling banyak pemesanan taksi baik pickup maupun dropoff?
2. Metode pembayaran apa yang paling sering digunakan penumpang?
3. Apakah ada pola aktivitas yang berbeda antara weekdays dan weekend?  
4. Bagaimanakah preferensi waktu penumpang?

<br>

# **Data Understanding**
<br>

**VendorID** = kode yang menunjukkan penyedia LPEP
- 1 = Creative Mobile Technologies, LLC.
- 2 = VeriFone Inc. 

**lpep_pickup_datetime** = Tanggal dan Waktu ketika meteran diaktifkan

**lpep_dropoff_datetime** = Tanggal dan Waktu ketika meteran dimatikan

**Passenger_count** = Jumlah penumpang di kendaran. Data ini di-inputkan oleh pengemudi

**Trip_distance** = Jarak perjalanan dalam (mil) dilaporkan oleh taksimeter

**PULocationID** = Zona taksi TLC dimana taksimeter digunakan

**DOLocationID** = Zona taksi TLC dimana taksimeter dilepaskan

**RateCodeID** = Kode tarif akhir berlaku pada akhir perjalanan
- 1 = Tarif standar
- 2 = JFK
- 3 = NewYork
- 4 = Nassau dan Westchester
- 5 = Tarif yang dinegoisasikan
- 6 = Perjalanan kelompok

**Store_and_fwd_flag** = bendera ini menunjukkan apakah catatan perjalanan disimpan dalam memori kendaraan sebelum dikirim ke vendor, alias, "simpan dan teruskan", karena kendaraan tidak memiliki koneksi ke server.
- Y = menyimpan dan meneruskan perjalanan
- N = bukan toko dan perjalanan lanjutan

**Payment_type** = Kode numerik yang menandakan cara penumpang membayar perjalanan
- 1 = Credit card
- 2 = Cash
- 3 = Tidak kembali
- 4 = Ada konfilik
- 5 = Unknown
- 6 = Perjalanan tidak valid dan tidak akan dihitung atau diperhitungkan dalam analisis atau perhitungan statistik

**Fare_amount** = Tarif waktu dan jarak dihitung berdasarkan argo. Biaya tambahan dan biaya tambahan lainnya. Saat ini, tarif ini hanya mencakup biaya jam sibuk dan biaya semalam sebesar $0.50 dan $1

**MTA_tax** = Pajak MTA sebesar $0.50 secara otomatis dipicu berdasarkan tarif meteran yang digunakan

**Improvement_surcharge** = Biaya tambahan perbaikan sebesar $0.30 dinilai pada perjalanan yang dielu-elukan di bendera turun. Biaya tambahan perbaikan mulai dikenakan pada tahun 2015

**Tip_amount** = Kolom ini secara otomatis terisi untuk tip kartu kredit. Tip tunai tidak termasuk

**Tolls_amount** = Jumlah total semua tol yang dibayarkan dalam perjalanan

**Total_amount** = Jumlah total yang dibebankan kepada penumpang. Tidak termasuk top tunai

**Trip_type** = Kode yang menunjukkan apakah perjanan tersebut merupakan perjalanan di jalanan atau pengiriman yang secara otomatis ditetapkan berdasarkan tarif meteran yang digunakan, namun dapat diubah oleh pengemudi.

- 1 = Hujan es jalanan
- 2 = Pengiriman

**Congestion Surcharge** = Biaya kemacetan
- $2.50 = untuk perjalanan *non-shared* dalam taksi
- $2.50 untuk perjalanan non-shared (tidak berbagi) dalam taksi
- $2.75 untuk perjalanan non-shared dalam For-Hire-Vehicles (termasuk limusin) dan Street-Hail Liveries **(Green Taxis)**
- $0.75 untuk perjalanan bersama (shared-rides) dalam jenis kendaraan apapun
- Tidak ada biaya tambahan untuk Access-A-Ride, atau perjalanan yang diatur oleh MTA lainnya.
- Biaya kemacetan tidak dapat dikurangi dari pendapatan pengemudi, dan harus dibebankan kepada penumpang.

<br>

# **Kesimpulan**
##### <font color='white'>Identifikasi tren berdasarkan *pick up* dan *drop off*</font>
**Manhattan** dengan zone paling populer untuk penumpang dengan perjalanan *pick up* dan *drop off* berada di zona **East Harlem North** dan **East Harlem South** dengan tipe perjalanan **Street-hail**. Hal ini dapat memberikan wawasan tentang pusat aktivitas atau tujuan yang populer bagi penumpang

##### <font color='white'>Identifikasi pembayaran berdasarkan *Borough*</font>
Hal yang menarik terjadi pada semua Borough, terutama di **Manhattan, Brooklyn, EWR, dan Staten Island** dimana metode pembayaran yang paling sering digunakan adalah **Credit Card**. Sedangkan di **Bronx dan Queens**, terdapat variasi dalam pemilihan metode pembayaran antara **Credit Card** dan **Cash**. Selain itu, baik untuk perjalanan *pickup* dan *dropoff* serta hari *weekdays* dan *weekends* metode pembayaran yang paling dominan masih menggunakan **Credit Card**

##### <font color='white'>Identifikasi pola aktivitas berdasarkan *weekdays* dan *weekends*</font>
Berdasarkan analisis, terdapat perbedaan jumlah pendapatan antara hari **weekdays** dan **weekends**. Jumlah Pendapatan pada hari **weekdays** sebesar 3.5 kali lebih tinggi daripada hari **weekends**. Hal ini dapat disebabkan oleh jumlah perjalanan yang lebih banyak pada hari **weekdays**. Perjalanan cenderung dilakukan oleh individu yang bepergian sendirian.  Selain itu, durasi perjalanan pada hari **weekdays** cenderung lebih lama daripada hari **weekends**, yang juga berkontribusi terhadap pendapatan yang lebih tinggi. Namun, pada hari **weekends** terdapat kecenderungan penumpang untuk melakukan perjalanan dengan jarak yang lebih jauh.

##### <font color='white'>Identifikasi pola aktivitas berdasarkan waktu</font>
Pola perjalanan taksi cenderung terkait dengan aktivitas sehari-hari, hal ini di buktikan dengan jumlah perjalanan *pick up* dan *drop off* meningkat dari pukul 5 pagi hingga 6 sore. Selain itu, perjalanan dengan tujuan **EWR** membutuhkan waktu tempuh yang lebih lama disebabkan oleh jarak yang lebih jauh, mengingat lokasi **EWR** berada di luar wilayah **New York**. Informasi ini dapat membantu perushaan pengelola taksi dalam mengatur dan mengoptimalkan pelayaan mereka, terutama dalam hal alokasi waktu tunggu.

<br>

# **Rekomendasi**
#### 1. Fokus pada daerah populer
- Perusahaan dapat mengalokasikan lebih banyak armada di daerah Manhattan dengan zona East Harlem North dan East Harlem South
#### 2. Peningkatan layanan *Street-hail*
- Tipe perjalanan ini dominan, diharapkan perushaan meningkatkan layanan dan ketersediaan taksi di jalan.
#### 3. Memberikan promosi pembayaran
- Perusahaan dapat bekerja sama dengan provider mitra credit card untuk memberikan penawaran diskon atau reward khusus bagi para penumpang.
#### 4. Strategi pemasaran yang berbeda untuk setiap **Borough**
- Untuk dihari weekdays, promosi lebih kepada individu yang melakukan perjalanan seorang diri seperti, mahasiswa, pekerja atau profesional, yang melakukan perjalanan rutin.
- Untuk weekends perusahan dapat menargetkan kelompok pelanggan yang condong untuk bepergian tujuan rekreasi.
#### 5. Penawaran paket tour wisata
- Seperti perjalanan wisata, perjalanan ke acara khusus, atau penjemputan dari tempat rekreasi populer. Diharapkan dapat meningkatkan minat pelanggan untuk menggunakan taksi.
#### 6. Pengaturan ketersediaan taksi
- Perusahaan dapat mengatur jumlah taksi yang tersedia dan waktu tunggu di area-area dengan tingkat peminat yang tinggi diantara pukul 5 pagi hingga 6 pagi.


































