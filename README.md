# # Laporan Akhir Kecerdasan Buatan - Kelompok Kelas IK-2D

**Anggota Kelompok :**

1. Dewi Maharani - NIM. 3.34.21.3.07
2. Vannisa Ardiani - NIM. 3.34.21.3.24

## Domain Proyek

Seiring dengan perkembangan teknologi, penggunaan laptop semakin hari semakin populer dan memperlihatkan perkembangan yang cukup signifikan. Berbeda dengan komputer atau desktop yang dirancang agar dapat digunakan di mana pun pemiliknya berada. Karena itu, untuk seseorang yang dengan mobilitas tinggi, memiliki laptop lebih diminati dibanding  memiliki komputer desktop.  Salah satu segmentasi yang menjadi target produsen laptop adalah mahasiswa.  Bagi produsen, mahasiswa merupakan salah satu pasar yang potensial karena mahasiswa memiliki kegiatan yang membutuhkan bantuan laptop untuk menunjang kegiatannya.  Laptop dapat berfungsi sebagai sarana penunjang pendidikan dan dapat pula  sebagai sarana hiburan. 

Pada era digitalisasi saat ini, pemanfaatan teknologi sangat dibutuhkan untuk membantu meringankan pekerjaan manusia. Dahulu dibutuhkan banyak ruang dan waktu untuk melakukan suatu kegiatan administrasi. Seiring berkembangkan teknologi, berangkas di mana dokumen disimpan telah digantikan dengan memori yang berada pada PC (personal computer). Penggunaan PC berhasil memangkas ruang dan waktu yang sebelumnya memerlukan ruang yang lebih luas untuk menyimpan suatu data dan memangkas waktu dalam melakukan pencarian data. Selain itu, PC dapat digunakan untuk melakukan aktivitas lainnya, seperti menggambar,bermain gim, menulis, menyunting gambar atau video, dan masih banyak lagi.

## Business Understanding

Tujuan dari proyek ini adalah untuk membangun model machine learning yang dapat memprediksi harga laptop berdasarkan atribut-atribut seperti ukuran kamera, kapasitas RAM, memori internal, kecepatan prosesor, dan merek. Pertanyaan utama yang ingin dijawab adalah bagaimana atribut-atribut spesifik tersebut berhubungan dengan harga laptop, apakah terdapat tren kenaikan harga berdasarkan peningkatan fitur tertentu, dan bagaimana membangun model yang akurat dalam memprediksi harga laptop berdasarkan spesifikasi yang diberikan. Konteks bisnis yang perlu dipahami meliputi persaingan di pasar laptop, preferensi konsumen terkait spesifikasi laptop dan harga, serta pengaruh persaingan harga antara merek-merek laptop. Meskipun ada beberapa batasan seperti ketersediaan data yang lengkap dan keterbatasan sumber daya, proyek ini diharapkan dapat memberikan wawasan kepada calon konsumen dalam menentukan budget yang sesuai dengan spesifikasi laptop yang mereka inginkan.

#### Problem Statements

Berdasarkan permasalahan yang telah dijelaskan, *problem statements* dari proyek ini adalah sebagai berikut.

1. Fitur-fitur apa saja yang paling berpengaruh terhadap harga *laptop*?
2. Bagaimana proses *Pre-Processing* yang dilakukan agar menghasilkan model *machine learning* yang akurat ?
3. Bagaimana membuat atau memilih model *machine learning* yang memiliki akurasi terbaik dalam memprediksi harga *laptop* ?

#### Goals

Tujuan yang hendak dicapai dari proyek ini adalah sebagai berikut 

1. Mengetahui fitur yang paling berkorelasi dengan penentuan harga *laptop*.
2. Membuat model *machine learning* yang dapat memprediksi harga *laptop*.
3. Memilih model *machine learning* yang menghasilkan prediksi paling akurat berdasarkan proses *preprocessing* yang dilakukan

####  Solution Statements

Solusi yang diajukan untuk menyelesaikan masalah yang telah diuraikan adalah sebagai berikut.

1. Melakukan analisis deskriptif untuk mengetahui pola dan informasi yang tersimpan di data mengenai fitur atau spesifikasi yang mempengaruhi harga *laptop*.
2. Melakukan proses *Data Manipulation* untuk menggabungkan kolom-kolom yang berpengaruh terhadap akurasi predisi harga *laptop* 
3. Melakukan  Proses *Preprocessing* seperti :
   - Mengecek *missing value* dan duplikasi data. Kebetulan dataset yang digunakan tidak ada *missing value* dan duplikasi data.
   - Melakukan visualisasi data untuk melihat persebaran dan korelasi antar kolom
   - Membagi data menjadi *training* dan *test set*, dengan prosentase 85% banding 15%. Alasan menggunakan 15% karena jumlah data yang digunakan banyak, jadi hanya dengan 15% sudah didapatkan banyak data tes.
   - Melakukan *Encoding* terhadap kolom yang bertipe objek / kategorikal menggunakan fungsi `Map`.
4. Melakukan pemilihan model terbaik menggunakan LazyPredict
   - Memilih 4 algoritma yang menghasilkan model dengan performa terbaik
   - Perfoma model terbaik dilihat dari skor *Mean Square Error* (MSE), *Root Mean Square Error* (RMSE), dan *R Square* (R2).

## Data Understanding

Dataset yang digunakan pada proyek ini diperoleh dari Kaggle. Silahkan kunjungi tautan berikut [Laptop Specifications and Prices](https://www.kaggle.com/datasets/muhammetvarl/laptop-price) untuk mengakses dataset yang dipakai. Adapun variabel-variabel yang terdapat pada dataset adalah sebagai berikut :

1. **Company**: String, Nama perusahaan laptop
2. **Product**: String, Nama Brand
3. **TypeName**: String, Model *Smarphone*
4. **Inches**: Numeric, Ukuran layar laptop
5. **ScreenResolution**: String, Resolusi layar laptop
6. **Cpu**: String, Central Processing Unit
7. **Ram**: String, RAM Laptop
8. **Gpu**: String, Graphics Processing Units
9. **OpSys**: String, Operating System
10. **Weight**: String, Berat Laptop
11. **Price_euros**: Numeric, Harga laptop dalam euro

Pada dataset, terdapat 12 fitur numerikal dan 9 fitur kategorikal. Ringkasan statistik dari data-data numerikal dapat dilihat pada Tabel 1.

<div style="text-align:center">Tabel 1. Ringkasan Statistik Data-Data Numerikal Pada Dataset</div>

![image-20230712141540389](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230712141540389.png)

Pada tahap *Data Understanding* dilakukan analisis data eksploratif untuk mendapatkan wawasan tentang karakteristik data, memahami struktur data, dan mengidentifikasi potensi masalah atau kesalahan yang mungkin terjadi. Kegiatan Data Understanding yang dilakukan pada Proyek ini antara lain :

- Memberikan informasi seperti jumlah data, *missing value*, duplikasi data, korelasi antar kolom, dan sebaran data.

- Melakukan visualisasi data untuk mengetahui korelasi dan sebaran data. Berdasarkan diagaram heatmap Gambar 1 diketahui bahawa terdapat  kolom dan laptop_ID yang berkorelasi dengan kolom 'Price_euros'.  Semakin mendekati nilai 1 maka korelasi semakin tinggi. 

  ![image-20230712141626825](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230712141626825.png)

  <div style="text-align:center">Gambar 1. Visualisasi Korelasi Data dengan Heatmap</div>

  Sedangkan contoh visualisasi dari sebaran data ditunjukan pada Gambar 2. Visualisasi yang ditunjukan pada Gambar 2 menunjukan bahwa ada ketidakseimbangan data pada kolom Inches, ScreenResolution, Product, dan Weight.

  ![image-20230712141804168](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230712141804168.png)

<div style="text-align:center">Gambar 2. Visualisasi Data pada Dataset</div>

## Data Preparation

Teknik data preparation yang dilakukan pada proyek ini adalah sebagai berikut : 

1. Feature Selection : Melakukan seleksi fitur untuk menyeleksi kolom yang berperan sebagai data fitur dan kolom yang menjadi data label.

2. Data Splitting: Membagi dataset menjadi data latih dan data uji. Pada proyek ini perbandingan data latih dan data uji adalah 85 : 15.

   ![image-20230712223109816](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230712223109816.png)

   Men-drop colom seperti Inches, Company, OpSys, dan lainnya dan berfokus pada colom harga atau Price_euros.

3. Menampilkan informasi jumlah data latih dan data uji. Jumlah data latih adalah 1107, sedangkan data uji terdat 196 data. jumlah data fitur yang dipakai untuk pelatihan adalah 12.

   ![image-20230712222954439](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230712222954439.png)

   


## Modelling

Pada tahap ini dilakukan proses pelatihan untuk mendapatkan model dengan performa terbaik. Tahapan yang dilakukan pada proses Modelling adalah sebagai berikut.

1. Memprediksi algoritma dengan performa terbaik menggunakan Lazy Predict

   Lazy Predict adalah library Python yang membantu dalam membuat model *machine learning* dengan cepat dan mudah. Library ini dikembangkan untuk mempercepat proses eksplorasi data dan pemodelan awal. Hasil dari proses pelatihan yang dilakukan Lazy Predict ditunjukan pada Tabel 2.

   <div style="text-align:center">Tabel 2. Hasil Perbandingan model menggunakan Lazy Predict</div>

   ![image-20230712223525310](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230712223525310.png)

   Algoritma dengan performa terbaik dilihat dari nilai R-Square dan RMSE. Semakin besar nilai R-Square (mendekati 1) maka model semakin akurat. Sedangkan pada RMSE, apabila nilai semain kecil (mendekati 0), maka akurasi model akan semakin tinggi. Berdasarkan hasil R-Square dan RMSE menggunakan Lazy Predict pada Tabel 1, disimpulkan bahwa 3 algoritma terbaik yang akan digunakan untuk mempredikasi harga adalah **GradientBoostingRegressor**, **RandomForestRegressor**, dan **BaggingRegressor**.

2. Menggunakan `ColumnTransformer` untuk mengubah data kategorik menjadi numerik

   Pada proyek ini masih mempertahankan kolom kategorikal yaitu Brand dan OS. Sebab pada saat ingin mempredikasi harga smartphone, calon pembeli tentunya akan memilih Brand dan OS dalam bentuk kategori bukan numerik. Oleh karena itu kita ubah data kategorik menjadi numberik menggunkan teknik OneHotEncoding. Tapi sebelum dilakukan teknik `OneHotEncoding` dilakukan harus menampilkan indeks dari masing-masing kolom menggunakan fungsi `enumerate()`. Brand berada di indeks 0, dan OS berada di index 9. Selanjutkan dilakukan proses `ColumnTransformer`.

3. Membuat pipeline untuk menggabungkan data numerik dan kategorik

   Hasil penggunakan teknik `ColumnTransformer` disimpan dalam objek feature. Selanjutnya dilakukan proses pipeline untuk menggabungkan dan meng-optimasi kolom numerikal dan kategorikan agar dapat di proses oleh algoritma machine learning. 

4. Memilih 3 (tiga) algoritma dengan performa terbaik untuk di evaluasi

   Setelah dilakukan proses pelatihan oleh Lazy Predict, diperoleh 3 algoritma dengan performa terbaik yaitu :

   - **GradientBoostingRegressor**

     GradientBoostingRegressor adalah algoritma pemodelan yang digunakan dalam pembelajaran mesin untuk memprediksi variabel target berkelanjutan. Ini adalah metode ensambel yang menggabungkan beberapa pohon keputusan untuk membuat model yang lebih kuat. Algoritma GradientBoostingRegressor bekerja dengan menggabungkan banyak pohon keputusan sederhana. Setiap pohon yang ditambahkan ke model berusaha untuk memperbaiki kesalahan prediksi yang dihasilkan oleh pohon sebelumnya. Algoritma ini bekerja dengan cara mengoptimalkan gradien fungsi kerugian (misalnya, *Mean Squared Error*) menggunakan proses iteratif. Ilustrasi dari cara kerja GradienBoostingRegressor ditunjukan pada Gambar 2.

     ![](https://afandistudio.net/prak_ai/GradienRegression.png)

     <div style="text-align:center">Gambar 2. Ilustrasi GradienBoostingRegressor [5]</div>

   - **RandomForestRegressor**

     RandomForestRegressor adalah algoritma pemodelan yang digunakan dalam pembelajaran mesin untuk memprediksi variabel target berkelanjutan. Ini adalah metode ensambel yang menggabungkan beberapa pohon keputusan acak (*random decision trees*) untuk membuat model yang lebih kuat. Pada dasarnya, algoritma RandomForestRegressor bekerja dengan menggabungkan hasil dari banyak pohon keputusan acak yang diberi bobot yang sama. Setiap pohon keputusan acak dibangun dengan menggunakan subset acak dari data pelatihan dan subset acak dari fitur (variabel independen). Proses ini dikenal sebagai bootstrap aggregating atau biasa disebut juga sebagai "bagging". Ilustrasi dari cara kerja RandomForestRegressor ditunjukan pada Gambar 3.

     <img src="https://afandistudio.net/prak_ai/RFRegression.jpg" style="zoom: 25%;" />

     <div style="text-align:center">Gambar 3. Ilustrasi RandomForestRegressor [6]</div>

   - **BaggingRegressor**

     BaggingRegressor adalah algoritma pemodelan yang digunakan dalam pembelajaran mesin untuk memprediksi variabel target berkelanjutan. Ini adalah metode ensambel yang menggabungkan beberapa model regresi (misalnya, Regresi Linier, DecisionTreeRegressor) untuk membuat model yang lebih kuat. Pada dasarnya, algoritma BaggingRegressor bekerja dengan membuat beberapa model regresi yang berbeda menggunakan subset acak dari data pelatihan. Setiap model regresi dibangun secara independen dan tidak saling bergantung satu sama lain. Ketika melakukan prediksi, hasil dari semua model regresi digabungkan untuk menghasilkan prediksi akhir dengan menggunakan rata-rata atau mayoritas suara (tergantung pada jenis variabel target). Ilustrasi dari cara kerja BaggingRegressor ditunjukan pada Gambar 4.

     <img src="https://afandistudio.net/prak_ai/BaggingRegressor.png" style="zoom:50%;" />

     <div style="text-align:center">Gambar 4. Ilustrasi BaggingRegressor [7]</div>

     Namun, BaggingRegressor tidak memberikan interpretasi model yang langsung seperti Regresi Linier. Selain itu, dalam beberapa kasus, jika terdapat korelasi yang kuat antara fitur, BaggingRegressor mungkin tidak memberikan peningkatan yang signifikan dalam kinerja prediksi dibandingkan dengan model regresi tunggal.

5. Menambahkan parameter tunning untuk mengingkatkan performa model

   Penambahan parameter menggunakan **Teknik Grid Search**. Sehingga diperoleh hyperparameter dari masing-masing algoritma adalah sebagai berikut.

   - Parameter GradienBoostingRegressor

     ![image-20230712224049572](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230712224049572.png)

     - n_estimator = 70
     - max_depth = 5
     - min_samples_split = 40
     - min_samples_leaf = 3
     - max_features = 3

   - Parameter RandomForestRegressor

     ![image-20230712224153640](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20230712224153640.png)

     - n_estimator = 100
     - max_samples = 0.6

     - max_features = 0.7

   - Parameter BaggingRegressor

     - n_estimators = 70
     - max_features = 0.7
     - max_samples = 0.6

  - warm_start= False
    - oob_score = False
  - bootstrap = False


## Evaluation

- Metrik evaluasi yang digunakan adalah *Mean Square Error* (MSE), *Root Mean Square Error* (RMSE), dan *R Square* (R2 Score)

- MSE melakukan pengurangan nilai data aktual dengan data peramalan dan hasilnya dikuadratkan (*squared*) kemudian dijumlahkan secara keseluruhan dan membaginya dengan banyaknya data yang ada. Rumus dari MSE adalah sebagai berikut 
  $$
  MSE = \frac{1}{n} \Sigma_{i=1}^n({y}-\hat{y})^2
  $$
  Diketahui:

  - n = Jumlah Data
  - yi = *Actual Value* / Nilai Sebenarnya
  - ŷi = *Predicted Value* / Nilai Prediksi

- RMSE adalah jumlah dari kesalahan kuadrat atau selisih antara nilai sebenarnya dengan nilai prediksi yang telah ditentukan. Cara menghitungnya tinggal mengakar kan mse menggunakan fungsi *np.sqrt*. Rumus dari RMSE adalah sebagai berikut.
  $$
  RMSE = \sqrt{(\frac{1}{n})\sum_{i=1}^{n}(y_{i} - x_{i})^{2}}
  $$
  Diketahui:

  - n = Jumlah Data
  - yi = *Actual Value* / Nilai Sebenarnya
  - ŷi = *Predicted Value* / Nilai Prediksi

- R2 Score dijadikan sebagai pengukuran seberapa baik garis regresi mendekati nilai data asli yang dibuat melalui model. Rumus dari R2 Score adalah sebagai berikut.
  $$
  R^2 = 1 - {SS_R \over SS_T} =  1 - {\sum_{i} (y_i - ŷ_p) ^ 2 \over \sum_{i} (y_i - ȳ) ^ 2}
  $$

  - SSR : Kuadrat dari selisih nilai Y prediksi dengan nilai rata-rata Y = ∑ (Ypred – Yrata-rata)²
  - SST : Kuadrat dari selisih nilai Y aktual dengan nilai rata-rata Y = ∑ (Yaktual – Yrata-rata)²

- Setelah melalui tahap pelatihan dan evaluasi menggunakan MSE, RMSE, dan R Square, diperoleh hasil bahwa algoritma **GradienBoosterRegressor** memiliki performa yang paling baik seperti ditunjukan Tabel 3. Maksud performa yang paling baik adalah memiliki nilai MSE dan RMSE yang mendekati nilai 0, serta memiliki nilai R2 Score yang mendekati nilai 1.

  <div style="text-align:center">Tabel 3. Hasil Pengujian dari 3 Algoritma Teratas</div>

  | id   | Model_Name       | MSE       | R2 Score  | RMSE      |
  | ---- | ---------------- | --------- | --------- | --------- |
  | 0    | GradienBoosting  | 0.1588188 | 0.7238088 | 0.3985208 |
  | 1    | RandomForest     | 0.1639016 | 0.7149698 | 0.4048476 |
  | 2    | BaggingRegressor | 0.1595067 | 0.7226127 | 0.3993828 |

- Membandingkan data sebenarnya dengan hasil prediksi. Hasil perbandingan dapat dilihat pada Tabel 4.

  <div style="text-align:center">Tabel 4. Hasil Perbandingan Data Sebenarnya dengan Hasil Prediksi</div>

  | Id   | y_true     | prediksi_GB | prediksi_RF | prediksi_BG |
  | :--- | :--------- | :---------- | :---------- | :---------- |
  | 965  | 13.6112660 | 13.9000000  | 13.9000000  | 14.0000000  |
  | 657  | 13.4294333 | 13.6000000  | 13.6000000  | 13.7000000  |
  | 1002 | 13.7166489 | 13.5000000  | 13.4000000  | 13.4000000  |
  | 918  | 13.2056893 | 13.7000000  | 13.7000000  | 13.8000000  |
  | 798  | 14.3035242 | 13.9000000  | 14.0000000  | 14.0000000  |
  | ...  | ...        | ...         | ...         | ...         |
  | 53   | 15.1153689 | 14.9000000  | 15.0000000  | 15.0000000  |
  | 1027 | 13.5657933 | 13.8000000  | 13.8000000  | 14.0000000  |
  | 436  | 14.1867278 | 13.3000000  | 13.3000000  | 13.3000000  |
  | 161  | 14.9745150 | 15.9000000  | 15.9000000  | 15.8000000  |
  | 47   | 15.2850487 | 14.9000000  | 15.1000000  | 14.9000000  |

## Conclussion

1. Fitur-fitur seperti ukuran layar, kapasitas RAM, kapasitas memori internal, kecepatan prosesor, dan merek laptop memiliki pengaruh yang signifikan terhadap harga laptop. Semakin besar ukuran layar, kapasitas RAM, dan kapasitas memori internal, serta semakin tinggi kecepatan prosesor, cenderung meningkatkan harga laptop.

2. Berdasarkan evaluasi menggunakan metrik MSE, RMSE, dan R2 Score, algoritma GradientBoostingRegressor memiliki performa terbaik dalam memprediksi harga laptop berdasarkan spesifikasi yang diberikan. Algoritma ini mampu menghasilkan prediksi dengan tingkat akurasi yang tinggi, dengan nilai MSE dan RMSE yang rendah, serta nilai R2 Score yang mendekati 1.

3. Merek laptop dan spesifikasi seperti ukuran layar, kapasitas RAM, dan kapasitas memori internal berperan penting dalam menentukan harga laptop. Merek tertentu mungkin memiliki harga yang lebih tinggi karena faktor reputasi, kualitas, atau fitur-fitur khusus yang ditawarkan.

4. Rekomendasi bagi konsumen adalah mempertimbangkan merek, ukuran layar, kapasitas RAM, dan kapasitas memori internal sesuai dengan kebutuhan dan anggaran mereka. Dengan memahami hubungan antara fitur-fitur ini dengan harga laptop, konsumen dapat membuat keputusan yang lebih informasional dan sesuai dengan preferensi dan kebutuhan mereka.

5. Hasil proyek ini memberikan wawasan yang berharga dalam memahami faktor-faktor yang berpengaruh pada harga laptop dan membangun model machine learning untuk memprediksi harga. Namun, disarankan untuk melakukan analisis yang lebih mendalam dan mempertimbangkan konteks bisnis dan pasar yang relevan sebelum membuat keputusan pembelian laptop.

   

## Referensi

[1]   JUISI, Vol. 06, No. 02, Agustus 2020, “PENERAPAN DATA MINING REKOMENDASI LAPTOP MENGGUNAKAN ALGORITMA APRIORI” . [Online]. Available: [https://journal.uc.ac.id/index.php/JUISI/article/view/1703](https://journal.uc.ac.id/index.php/JUISI/article/view/1703).

[2]   Prof. Vaishali Surjuse et al, International Journal of Computer Science and Mobile Computing, Vol.11 Issue.1, January- 2022, pg. 164-168, “Laptop Price Prediction using Machine Learning,” 2020, doi: [laptop price prediction](https://d1wqtxts1xzle7.cloudfront.net/79627922/V11I1202229-libre.pdf?1643278606=&response-content-disposition=inline%3B+filename%3DLaptop_Price_Prediction_using_Machine_Le.pdf&Expires=1689170225&Signature=g2zkRVeZivgc2ZlnQfsfu~uSRwH2CpQsLZndmwzJE-0U347FgnBN8Zo2VNmndwN4MinqwfxQkkTXPMq0xie9iQEXhxkyW3d0Oo0~PEvRsDnwddOmlMx2UxThgIkJyCwvHPY-ndJ2~NeODSMoy9aIAHI8kKQEmODiCORrzS1A6GrMMnJU7GodCDK75RCxVfHqjV9khep8mYBw~ntLcQm084beFwMh8cvZbWUVy4nL523NlIwO8Hn7IZ95TbdWoK8AJO~INHZ~pfoJhyZgyY8f56Ou5vpXNlH9d4DhXtTLGIpm9hbPTG8e9JzGw8u~6WfRvfIFe7-93deR2o12AwMtHw__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA).

[3]   M. Çetın and Y. Koç, “Mobile Phone Price Class Prediction Using Different Classification Algorithms with Feature Selection and Parameter Optimization,” 2021, doi: [FORECASTING LAPTOP PRICES](https://deliverypdf.ssrn.com/delivery.php?ID=598084112068091077102107069119103026104005064017060018007085105124003125002101015011061119044127042010060112031007074071025096012016025042084125030028092114105021076070022064078102064030069102084024096071065123115106010127001097022028006100106102103071&EXT=pdf&INDEX=TRUE).

[4]   Laptop Price Prediction – Practical Understanding of Machine learning project lifecycle, [https://apjii.or.id/survei](https://apjii.or.id/survei). https://www.analyticsvidhya.com/blog/2021/11/laptop-price-prediction-practical-understanding-of-machine-learning-project-lifecycle/.

[5]  V. Aliyev, “A hands-on explanation of Gradient Boosting Regression,” *medium.com*, 2020. https://vagifaliyev.medium.com/a-hands-on-explanation-of-gradient-boosting-regression-4cfe7cfdf9e (accessed Jun. 03, 2023).

[6]   Forecasting Laptop Prices: A Comparative Study of Machine Learning Algorithms for Predictive Modeling, https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4413726

[7]   A. Biswal, “Bagging in machine learning: Step to Perform And Its Advantages,” *simplilearn.com*, 2023. https://www.simplilearn.com/tutorials/machine-learning-tutorial/bagging-in-machine-learning (accessed Jun. 03, 2023).

**---Ini adalah bagian akhir laporan---**
