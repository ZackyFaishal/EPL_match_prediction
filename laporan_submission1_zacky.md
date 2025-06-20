# Laporan Proyek Prediksi Pertandingan Sepak Bola

## Domain Proyek

Sepak bola merupakan salah satu olahraga paling populer di dunia, dan Liga Inggris (English Premier League) adalah salah satu liga yang paling banyak ditonton serta dianalisis. Banyak pihak, mulai dari penggemar, analis olahraga, hingga pelaku industri taruhan, tertarik untuk memahami faktor-faktor yang memengaruhi hasil pertandingan dan bahkan mencoba memprediksinya secara akurat. Oleh karena itu, analisis prediktif berbasis data menjadi pendekatan yang sangat relevan dan potensial untuk menggali wawasan dari data historis pertandingan.

Proyek ini bertujuan untuk mengembangkan model prediktif untuk memprediksi hasil pertandingan sepak bola Liga Inggris dari musim 2020 hingga 2025. Prediksi ini didasarkan pada berbagai statistik pertandingan dan data historis untuk mengidentifikasi pola-pola yang dapat membantu memperkirakan hasil akhir, yakni menang kandang (Home Win), seri (Draw), atau menang tandang (Away Win).

Dengan memanfaatkan pendekatan machine learning, proyek ini berupaya menemukan hubungan tersembunyi antara berbagai fitur pertandingan—seperti jumlah gol, tembakan ke gawang, kartu, dan waktu pertandingan—dengan hasil akhirnya. Pendekatan ini memungkinkan pembelajaran dari data historis untuk menghasilkan prediksi pada pertandingan baru yang belum pernah terlihat sebelumnya.

Selain itu, proyek ini memiliki potensi manfaat di berbagai sektor:

- **Bagi analis tim sepak bola**, model ini dapat membantu dalam menyusun strategi pertandingan.
- **Bagi penggemar dan jurnalis olahraga**, hasil prediksi dapat menambah wawasan berbasis data dalam menganalisis pertandingan.
- **Bagi industri taruhan olahraga**, model prediktif berbasis statistik dapat meningkatkan pendekatan berbasis probabilitas dan mengurangi ketergantungan pada intuisi semata.

Penggunaan data dari lima musim terakhir memberikan cakupan yang luas terhadap dinamika performa tim, kondisi bermain, dan perubahan strategi yang mungkin terjadi dari musim ke musim. Proses pembersihan data dan rekayasa fitur juga dilakukan untuk memastikan bahwa data siap digunakan oleh algoritma pembelajaran mesin.

Model yang dibangun diharapkan mampu menjadi sistem pendukung keputusan yang andal dalam konteks prediksi hasil pertandingan, dengan tetap mempertimbangkan dinamika kompleks yang terjadi dalam dunia sepak bola.

### Referensi

1. Rout, M., Dash, A. K., Majhi, B., & Nayak, S. (2021). *Football Match Outcome Prediction using Machine Learning Techniques*. Procedia Computer Science, 167, 2310–2319.
2. football-data.co.uk. (2025). *Historical football results and match statistics*. Diakses dari: [https://www.football-data.co.uk/englandm.php](https://www.football-data.co.uk/englandm.php)
3. Studi kasus pertama predictive analiytics [machine learning terapan](https://www.dicoding.com/academies/319/tutorials/16989)
4. Template laporan [mlt](https://github.com/dicodingacademy/contoh-laporan-mlt/blob/main/format_laporan_submission_1.md)

## Business Understanding

### Problem Statements

* Bagaimana mengidentifikasi faktor-faktor kunci dari data pertandingan sepak bola yang paling berpengaruh terhadap hasil akhir pertandingan?
* Bagaimana membangun dan mengevaluasi model Machine Learning yang efektif untuk memprediksi hasil pertandingan (Home Win, Draw, Away Win) berdasarkan data historis dan statistik?

### Goals

* Menggabungkan data pertandingan dari berbagai musim Liga Inggris menjadi satu dataset yang komprehensif.
* Melakukan pembersihan data dan rekayasa fitur untuk mempersiapkan data agar siap digunakan dalam pemodelan Machine Learning.
* Menganalisis distribusi variabel-variabel kunci dan mendeteksi potensi *outlier* dalam dataset.
* Mengembangkan model prediktif yang akurat untuk memprediksi hasil pertandingan sepak bola.

### Solution Statements

* Mempersiapkan data dengan menggabungkan lima file CSV terpisah yang berisi data pertandingan Liga Inggris dari musim 2020-2021 hingga 2024-2025 menjadi satu dataset terpadu. Data diunduh dari [football-data.co.uk](https://www.football-data.co.uk/englandm.php).
* Melakukan pembersihan data dengan menghapus kolom-kolom yang tidak diperlukan, terutama yang terkait dengan *odds* (misalnya, 'B365', 'BW', 'IW', 'PS', 'WH', 'VC', 'Max', 'Avg', '>2.5', '<2.5', 'AH', 'CH', '1XB', 'BF'), serta mengubah tipe data kolom `Date` dan `Time` menjadi fitur numerik (Year, Month, Day, Weekday, Hour). Kolom `HomeTeam`, `AwayTeam`, `FTR`, `HTR`, dan `Referee` akan di-*encode* menjadi nilai numerik.
* Melakukan Analisis Data Eksplorasi (EDA) untuk memahami struktur data, karakteristik variabel, dan mendeteksi *outlier*.
* Membangun dan melatih model Machine Learning (detail model tidak tersedia dalam *notebook* yang diberikan).
* Mengevaluasi performa model menggunakan metrik seperti akurasi, presisi, *recall*, dan F1-score (detail evaluasi tidak tersedia dalam *notebook* yang diberikan).

**Potensi Manfaat:**

Proyek ini diharapkan memberikan beberapa manfaat, antara lain:

* **Peningkatan Akurasi Prediksi:** Model yang dikembangkan dapat membantu memprediksi hasil pertandingan dengan lebih akurat.
* **Wawasan Berbasis Data:** Analisis data yang mendalam dapat memberikan wawasan tentang faktor-faktor yang paling memengaruhi hasil pertandingan, seperti performa tim, statistik gol, dan kartu.
* **Aplikasi Praktis:** Hasil prediksi dapat digunakan untuk berbagai keperluan, seperti analisis pertandingan, strategi tim, atau sebagai dasar untuk pengembangan sistem taruhan prediktif.

## Data Understanding

### Sumber Data

Dataset yang digunakan dalam proyek ini adalah "Match Prediction Project" yang berisi data pertandingan Liga Inggris dari musim 2020-2021 hingga 2024-2025. Data ini diunduh dari situs web [https://www.football-data.co.uk/englandm.php](https://www.football-data.co.uk/englandm.php). Awalnya, dataset terdiri dari 5 file CSV yang kemudian digabungkan menjadi satu file CSV tunggal.

### Variabel

Berikut adalah kolom-kolom variabel yang digunakan setelah proses pembersihan data, untuk prediksi pertandingan beserta keterangannya:

| No | Nama Kolom | Deskripsi |
|----|------------|-----------|
| 1  | `Div`      | Divisi Liga |
| 2  | `Date`     | Tanggal pertandingan |
| 3  | `Time`     | Waktu pertandingan |
| 4  | `HomeTeam` | Tim tuan rumah |
| 5  | `AwayTeam` | Tim tamu |
| 6  | `FTHG`     | Jumlah gol yang dicetak tim tuan rumah (Full Time) |
| 7  | `FTAG`     | Jumlah gol yang dicetak tim tandang (Full Time) |
| 8  | `FTR`      | Hasil pertandingan (H = Home win, D = Draw, A = Away win) |
| 9  | `HTHG`     | Jumlah gol yang dicetak tim tuan rumah (Half Time) |
| 10 | `HTAG`     | Jumlah gol yang dicetak tim tandang (Half Time) |
| 11 | `HTR`      | Hasil babak pertama (H, D, A) |
| 12 | `Referee`  | Wasit yang memimpin pertandingan |
| 13 | `HS`       | Jumlah tembakan oleh tim tuan rumah |
| 14 | `AS`       | Jumlah tembakan oleh tim tamu |
| 15 | `HST`      | Tembakan tepat sasaran oleh tim tuan rumah |
| 16 | `AST`      | Tembakan tepat sasaran oleh tim tamu |
| 17 | `HF`       | Pelanggaran oleh tim tuan rumah |
| 18 | `AF`       | Pelanggaran oleh tim tamu |
| 19 | `HC`       | Sepak pojok oleh tim tuan rumah |
| 20 | `AC`       | Sepak pojok oleh tim tamu |
| 21 | `HY`       | Kartu kuning untuk tim tuan rumah |
| 22 | `AY`       | Kartu kuning untuk tim tamu |
| 23 | `HR`       | Kartu merah untuk tim tuan rumah |
| 24 | `AR`       | Kartu merah untuk tim tamu |

### Tipe Data

Pada awalnya, dataset memiliki beberapa kolom bertipe `object` (string) yang kemudian diubah menjadi numerik agar dapat diproses oleh algoritma *machine learning*:

* **Kolom `Date` dan `Time`**: Dikombinasikan menjadi satu kolom `datetime`, lalu dipecah menjadi fitur numerik `Year`, `Month`, `Day`, `Weekday`, dan `Hour`. Kolom asli `Date`, `Time`, dan `Datetime` dihapus.
* **Kolom `HomeTeam` dan `AwayTeam`**: Dilakukan *Label Encoding*, mengubah nama tim menjadi angka.
* **Kolom `FTR` (Full Time Result) dan `HTR` (Half Time Result)**: Diubah dari kategori `H`, `D`, `A` menjadi angka (0 = Home win, 1 = Draw, 2 = Away win). `FTR` akan menjadi kolom *target*.
* **Kolom `Referee`**: Dilakukan *Label Encoding*.

Setelah semua proses ini, semua kolom dalam dataset menjadi numerik dan siap untuk digunakan dalam pelatihan model.

## Data Cleansing

Proses pembersihan data melibatkan beberapa langkah penting:

1.  **Penggabungan Dataset**: Lima file CSV yang mewakili data pertandingan Liga Inggris dari musim 2020-2021 hingga 2024-2025 digabungkan menjadi satu file CSV bernama `all_matches.csv`.
2.  **Penghapusan Kolom Tidak Perlu**: Kolom-kolom yang mengandung kata kunci terkait *odds* (misalnya, 'B365', 'BW', 'IW', 'PS', 'WH', 'VC', 'Max', 'Avg', '>2.5', '<2.5', 'AH', 'CH', '1XB', 'BF') dihapus dari dataset karena tidak relevan untuk tujuan prediksi ini.
3.  **Penanganan Kolom Non-Numerik**:
    * Kolom `Date` dan `Time` dikombinasikan menjadi `Datetime`, lalu dipecah menjadi fitur waktu numerik (`Year`, `Month`, `Day`, `Weekday`, `Hour`). Kolom asli dihapus.
    * Kolom `HomeTeam`, `AwayTeam`, `FTR`, `HTR`, dan `Referee` yang bertipe *object* (string) di-*encode* menggunakan `LabelEncoder` dan *mapping* manual (`H`: 0, `D`: 1, `A`: 2) menjadi nilai numerik.

## Exploratory Data Analysis (EDA)

Setelah data dimuat dan dibersihkan, dilakukan **Exploratory Data Analysis (EDA)** untuk memahami struktur, karakteristik, dan hubungan antar variabel.

### Tahapan Exploratory Data Analysis (EDA)

#### 1. Pemeriksaan Awal

* **Informasi Dataset**: Dataset terdiri dari 732 pertandingan dari musim 2020 hingga 2025. Setelah pembersihan data, dataset memiliki 732 entri dan 28 kolom.
* **Statistik Deskriptif**:
    * Rata-rata gol tim tuan rumah (`FTHG`) adalah 1.64, sedangkan tim tandang (`FTAG`) adalah 1.33, menunjukkan keunggulan gol rata-rata untuk tim tuan rumah.
    * Kolom `FTR` (Full Time Result) yang sudah dikonversi menunjukkan bahwa pertandingan cenderung imbang atau sedikit lebih sering dimenangkan oleh tuan rumah. Distribusi hasil pertandingan menunjukkan bahwa tim tuan rumah memiliki keunggulan dalam kemenangan dibandingkan tim tandang, dan jumlah hasil seri relatif lebih sedikit.
    * Rata-rata jam pertandingan (`Hour`) adalah 16.13, yang berarti sebagian besar pertandingan berlangsung sekitar pukul 4 sore.
    * Rata-rata kartu kuning tim tandang (`AY`) lebih tinggi (1.91) dibandingkan tim tuan rumah (`HY`) sebesar 1.68, menunjukkan tim tandang cenderung mendapatkan lebih banyak kartu kuning.

#### 2. Missing Value

Tidak ditemukan *missing values* pada tahap awal, menunjukkan bahwa semua kolom memiliki 732 entri non-null. Data sudah tidak ada yang kosong.

#### 3. Outliers
![outliers.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/outliers.png)
Deteksi *outlier* dilakukan menggunakan visualisasi *boxplot* dan metode Interquartile Range (IQR).

* **FTHG dan FTAG**: Memiliki *outlier* terutama saat jumlah gol lebih dari 4 untuk FTHG dan lebih dari 5 untuk FTAG.
* **HS dan AS**: Menunjukkan sejumlah *outlier* dengan jumlah tembakan sangat tinggi (di atas 30).
* **HY dan AY**: Menunjukkan nilai melebihi 4 atau 5, tergolong sebagai *outlier*.

Meskipun terdapat *outlier*, nilai-nilai ini dianggap wajar dalam konteks pertandingan sepak bola dan tidak dihapus karena masih memiliki arti kontekstual dan dapat memberikan informasi penting untuk *modeling*.

#### 4. Univariate Analysis

Analisis distribusi masing-masing fitur secara individual menggunakan *countplot* untuk variabel kategorikal:

* **Distribusi Pertandingan per Bulan**: 
![distribusi_pertandingan_perbulan.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/distribusi_pertandingan_perbulan.png)
Menunjukkan fluktuasi jumlah pertandingan per bulan, dengan puncak pada bulan-bulan tertentu. Berdasarkan grafik "Distribusi Pertandingan per Bulan", terlihat bahwa jumlah pertandingan Liga Inggris bervariasi sepanjang tahun. Bulan April (bulan ke-4) dan Februari (bulan ke-2) menunjukkan jumlah pertandingan tertinggi, keduanya memiliki lebih dari 80 pertandingan. Sebaliknya, bulan Juli (bulan ke-7), September (bulan ke-9), dan Oktober (bulan ke-10) memiliki jumlah pertandingan paling sedikit, dengan angka di bawah 50 pertandingan. Pola ini kemungkinan mencerminkan jadwal liga sepak bola yang biasanya dimulai di akhir musim panas/awal musim gugur dan berakhir di musim semi, dengan jeda tertentu di bulan-bulan liburan.

* **Distribusi Jam Pertandingan**:
    ![distribusi_pertandingan_jam.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/distribusi_pertandingan_jam.png)
    Menunjukkan sebagian besar pertandingan berlangsung pada sore hari (sekitar pukul 15.00-17.00 WIB). Berdasarkan grafik "Distribusi Jam Pertandingan", frekuensi pertandingan mencapai puncaknya pada pukul 15.00 (Hour 15) dengan lebih dari 200 pertandingan. Jam-jam lain yang juga memiliki jumlah pertandingan yang signifikan adalah pukul 14.00 (sekitar 100 pertandingan), pukul 17.00 (sekitar 70 pertandingan), dan pukul 20.00 (sekitar 115 pertandingan). Sebaliknya, jam 13.00 dan 18.00 menunjukkan jumlah pertandingan yang sangat sedikit, di bawah 20 pertandingan. Hal ini mengindikasikan bahwa sebagian besar pertandingan Liga Inggris dijadwalkan pada sore dan awal malam hari, dengan pukul 15.00 sebagai waktu yang paling populer.

* **Distribusi Hari Pertandingan (0=Senin, 6=Minggu)**:
    ![distribusi_haripertandingan.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/distribusi_haripertandingan.png)
    Mengindikasikan distribusi pertandingan tersebar sepanjang minggu, dengan rata-rata mendekati hari Rabu (2). Berdasarkan grafik "Distribusi Hari Pertandingan", hari Senin (Weekday 1) memiliki jumlah pertandingan tertinggi, mencapai lebih dari 140 pertandingan. Hari-hari lain yang juga menunjukkan frekuensi pertandingan yang tinggi adalah Hari Rabu (Weekday 2) dan Hari Jumat (Weekday 4), masing-masing dengan lebih dari 110 pertandingan, serta Hari Minggu (Weekday 6) dengan sekitar 108 pertandingan. Sebaliknya, Hari Kamis (Weekday 3) dan Hari Sabtu (Weekday 5) memiliki jumlah pertandingan yang relatif lebih sedikit, di bawah 90 pertandingan. Hal ini menunjukkan bahwa meskipun pertandingan tersebar sepanjang minggu, ada kecenderungan untuk lebih banyak pertandingan pada awal minggu dan di pertengahan minggu, terutama pada hari Senin.(2).

* **Countplot `HomeTeam` dan `AwayTeam`**:
    ![unvariate_analysis.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/unvariate_analysis.png)
    Grafik `Countplot HomeTeam` menunjukkan distribusi jumlah pertandingan kandang yang dimainkan oleh setiap tim, sedangkan `Countplot AwayTeam` menunjukkan distribusi jumlah pertandingan tandang. Karena nilai sumbu X (`HomeTeam` dan `AwayTeam`) telah di-*encode* menjadi numerik, sulit untuk mengidentifikasi tim mana secara spesifik. Namun, secara umum, terlihat ada beberapa tim (diwakili oleh angka-angka di sumbu X) yang bermain lebih banyak pertandingan kandang dan tandang dibandingkan tim lainnya. Distribusi ini menunjukkan bahwa tidak semua tim memiliki jumlah pertandingan kandang atau tandang yang sama persis dalam dataset ini.

* **Countplot `FTR` (Full Time Result) dan `HTR` (Half Time Result)**:
    Grafik `Countplot FTR` menunjukkan hasil akhir pertandingan: `Home Win`, `Away Win`, dan `Draw`. Terlihat bahwa `Home Win` (kemenangan tuan rumah) memiliki frekuensi tertinggi, yaitu sekitar 340 pertandingan. Diikuti oleh `Away Win` (kemenangan tim tamu) dengan sekitar 230 pertandingan, dan `Draw` (seri) dengan jumlah terendah, sekitar 150 pertandingan. Hal ini mengkonfirmasi bahwa tim tuan rumah memiliki keunggulan dalam kemenangan dibandingkan tim tandang, dan jumlah hasil seri relatif lebih sedikit.

    Grafik `Countplot HTR` menunjukkan hasil babak pertama pertandingan: `Draw`, `Home Win`, dan `Away Win`. Berbeda dengan hasil akhir, hasil `Draw` (seri) di babak pertama adalah yang paling sering terjadi, dengan sekitar 270 pertandingan. Diikuti oleh `Home Win` (kemenangan tuan rumah) di babak pertama dengan sekitar 260 pertandingan, dan `Away Win` (kemenangan tim tamu) di babak pertama dengan jumlah terendah, sekitar 180 pertandingan. Ini menunjukkan bahwa pertandingan cenderung lebih sering berakhir seri pada babak pertama dibandingkan babak penuh waktu, dan tim tuan rumah masih memiliki sedikit keunggulan dibandingkan tim tamu.

#### 5. Multivariate Analysis

* **Heatmap Korelasi Antar Variabel Numerik**:
    ![heatmap_correlation.jpg](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/heatmap_correlation.jpg)
    Heatmap ini memvisualisasikan matriks korelasi antar variabel numerik dalam dataset. Skala warna dari biru (korelasi negatif kuat) hingga merah (korelasi positif kuat) dengan putih/abu-abu (korelasi lemah/tidak ada).
    Beberapa observasi kunci dari heatmap adalah:
    * **Korelasi Positif Kuat**:
        * `FTHG` (gol tuan rumah penuh waktu) memiliki korelasi positif kuat dengan `HTHG` (gol tuan rumah babak pertama) (sekitar 0.68) dan `HST` (tembakan tepat sasaran tuan rumah) (sekitar 0.61). Ini wajar karena lebih banyak gol di babak pertama berkontribusi pada gol penuh waktu, dan tembakan tepat sasaran yang lebih banyak meningkatkan kemungkinan gol.
        * `FTAG` (gol tandang penuh waktu) memiliki korelasi positif kuat dengan `HTAG` (gol tandang babak pertama) (sekitar 0.64) dan `AST` (tembakan tepat sasaran tandang) (sekitar 0.59). Pola serupa dengan tim tuan rumah.
        * `HS` (tembakan tuan rumah) dan `AS` (tembakan tandang) memiliki korelasi positif kuat dengan `HST` dan `AST` masing-masing (sekitar 0.90 dan 0.93), menunjukkan bahwa sebagian besar tembakan adalah tembakan tepat sasaran.
        * `HY` (kartu kuning tuan rumah) dan `AY` (kartu kuning tandang) memiliki korelasi positif dengan `HF` (pelanggaran tuan rumah) dan `AF` (pelanggaran tandang) masing-masing (sekitar 0.70 dan 0.78), mengindikasikan bahwa semakin banyak pelanggaran cenderung menghasilkan lebih banyak kartu kuning.
    * **Korelasi Negatif Kuat**:
        * `FTR` (hasil penuh waktu) menunjukkan korelasi negatif kuat dengan `FTHG` (gol tuan rumah penuh waktu) (sekitar -0.70) dan `HTHG` (gol tuan rumah babak pertama) (sekitar -0.70), serta korelasi positif dengan `FTAG` (gol tandang penuh waktu) (sekitar 0.64) dan `HTAG` (gol tandang babak pertama) (sekitar 0.57). Ini konsisten karena `FTR` (hasil pertandingan) dikodekan sebagai 0=Home Win, 1=Draw, 2=Away Win. Jadi, semakin tinggi gol tim tuan rumah, semakin rendah nilai `FTR` (cenderung Home Win), dan semakin tinggi gol tim tandang, semakin tinggi nilai `FTR` (cenderung Away Win).
        * `HTR` (hasil babak pertama) menunjukkan pola korelasi serupa dengan `FTR` terhadap `HTHG` dan `HTAG` (sekitar -0.63 dan 0.68).
    * **Korelasi Menarik Lainnya**:
        * Terdapat korelasi negatif ringan antara `Referee` dengan `HY` dan `AY` (sekitar -0.19 dan -0.20), menunjukkan bahwa beberapa wasit mungkin cenderung memberikan lebih sedikit kartu kuning secara keseluruhan.
        * Kolom waktu (`Year`, `Month`, `Day`, `Weekday`, `Hour`) umumnya memiliki korelasi yang sangat rendah dengan variabel pertandingan lainnya, mengindikasikan bahwa waktu dan tanggal pertandingan tidak memiliki dampak korelasi langsung yang signifikan terhadap statistik pertandingan atau hasilnya, meskipun mereka dapat menjadi fitur penting untuk model prediktif.
    Secara keseluruhan, heatmap ini memberikan wawasan penting tentang hubungan antar variabel, yang dapat digunakan untuk rekayasa fitur atau pemilihan fitur dalam proses pemodelan.

* **Boxplot**:
    ![Boxplot.jpg](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/Boxplot.jpg)
    Boxplot ini memvisualisasikan distribusi dan keberadaan *outlier* untuk beberapa variabel numerik, seperti `FTHG`, `FTAG`, `HS`, `AS`, `HST`, `AST`, `HF`, `AF`, `HC`, `AC`, `HY`, `AY`, `HR`, dan `AR` dalam hubungannya dengan `FTR` (Full Time Result). Setiap boxplot menunjukkan kuartil (Q1, median, Q3) dan rentang data, serta titik-titik yang merepresentasikan *outlier*.

    Beberapa observasi kunci dari boxplot adalah:
    * **`FTHG` (Full Time Home Goals) vs `FTR`**:
        * Saat `FTR` adalah Home Win, `FTHG` memiliki median yang lebih tinggi dan persebaran yang lebih lebar ke atas, menunjukkan jumlah gol tuan rumah yang lebih banyak.
        * Saat `FTR` adalah Draw atau Away Win, `FTHG` cenderung lebih rendah.
        * Terdapat *outlier* (poin-poin di luar "whiskers") pada `FTHG` untuk semua hasil `FTR`, terutama pada Home Win, menunjukkan adanya pertandingan dengan jumlah gol tuan rumah yang sangat tinggi.
    * **`FTAG` (Full Time Away Goals) vs `FTR`**:
        * Saat `FTR` adalah Away Win, `FTAG` memiliki median yang lebih tinggi dan persebaran yang lebih lebar ke atas.
        * Saat `FTR` adalah Home Win atau Draw, `FTAG` cenderung lebih rendah.
        * Terdapat *outlier* pada `FTAG` untuk semua hasil `FTR`, terutama pada Away Win, menunjukkan adanya pertandingan dengan jumlah gol tandang yang sangat tinggi.
    * **`HS` (Home Shots) dan `AS` (Away Shots) vs `FTR`**:
        * Tim pemenang (baik tuan rumah atau tandang) cenderung memiliki jumlah tembakan (`HS` atau `AS`) yang lebih tinggi.
        * Banyak *outlier* terlihat pada `HS` dan `AS`, menunjukkan pertandingan dengan jumlah tembakan yang sangat banyak oleh salah satu atau kedua tim.
    * **`HST` (Home Shots on Target) dan `AST` (Away Shots on Target) vs `FTR`**:
        * Pola serupa dengan `HS` dan `AS`, di mana tim pemenang cenderung memiliki tembakan tepat sasaran yang lebih banyak.
        * Adanya *outlier* menunjukkan pertandingan dengan tembakan tepat sasaran yang luar biasa tinggi.
    * **`HF` (Home Fouls) dan `AF` (Away Fouls) vs `FTR`**:
        * Distribusi pelanggaran (`HF` dan `AF`) terlihat cukup bervariasi tergantung pada hasil pertandingan, dengan beberapa *outlier* yang menunjukkan pertandingan dengan jumlah pelanggaran tinggi.
    * **`HC` (Home Corners) dan `AC` (Away Corners) vs `FTR`**:
        * Jumlah sepak pojok (`HC` dan `AC`) juga bervariasi, dengan tim yang menyerang lebih banyak cenderung mendapatkan lebih banyak sepak pojok. Terdapat *outlier* untuk jumlah sepak pojok yang sangat tinggi.
    * **`HY` (Home Yellow Cards) dan `AY` (Away Yellow Cards) vs `FTR`**:
        * `AY` (kartu kuning tim tandang) terlihat sedikit lebih tinggi rata-ratanya dibandingkan `HY` (kartu kuning tim tuan rumah). Distribusi kartu kuning menunjukkan adanya *outlier* di mana beberapa tim mendapatkan jumlah kartu kuning yang sangat banyak dalam satu pertandingan.
    * **`HR` (Home Red Cards) dan `AR` (Away Red Cards) vs `FTR`**:
        * Kartu merah (`HR` dan `AR`) adalah kejadian yang lebih jarang, namun tetap ada *outlier* yang menunjukkan pertandingan dengan kartu merah.

    Secara keseluruhan, boxplot ini membantu dalam memahami bagaimana distribusi statistik pertandingan (gol, tembakan, pelanggaran, kartu, sepak pojok) bervariasi berdasarkan hasil pertandingan (`FTR`). Hal ini memberikan wawasan tentang fitur-fitur mana yang paling membedakan antara kemenangan kandang, kemenangan tandang, atau hasil seri. Meskipun terdapat *outlier*, nilai-nilai ini dianggap wajar dalam konteks pertandingan sepak bola dan dipertahankan untuk *modeling* karena dapat memberikan informasi penting.

* **Scatter Plot**:
    * **Home Shots vs Home Goals (FTR)**:
        ![homeshoot_vs_homegoals.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/homeshoot_vs_homegoals.png)
        Plot ini menunjukkan hubungan antara jumlah tembakan yang dilakukan tim tuan rumah (`HS`) dengan jumlah gol yang dicetak tim tuan rumah (`FTHG`), dikelompokkan berdasarkan hasil akhir pertandingan (`FTR`: 0=Home Win, 1=Draw, 2=Away Win).
        * Terlihat tren positif: semakin banyak `HS`, semakin tinggi kemungkinan `FTHG` (lebih banyak gol).
        * Untuk `FTR = 0` (Home Win, warna merah), sebagian besar titik berada pada `FTHG` yang lebih tinggi, mengindikasikan bahwa kemenangan kandang seringkali didukung oleh gol yang lebih banyak.
        * Untuk `FTR = 2` (Away Win, warna hijau), titik-titik cenderung berada pada `FTHG` yang rendah (seringkali 0 atau 1), yang masuk akal karena tim tuan rumah kalah.
        * Ada beberapa kasus menarik di mana `HS` tinggi tetapi `FTHG` rendah, atau sebaliknya, menunjukkan efisiensi tembakan yang bervariasi.

    * **Home Shots vs On-Target (FTR)**:
        ![homeshoot_vs_ontarget.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/homeshoot_vs_ontarget.png)
        Plot ini menunjukkan hubungan antara jumlah tembakan yang dilakukan tim tuan rumah (`HS`) dengan jumlah tembakan tepat sasaran tim tuan rumah (`HST`), dikelompokkan berdasarkan hasil akhir pertandingan (`FTR`).
        * Terdapat korelasi positif yang jelas antara `HS` dan `HST`: semakin banyak tembakan, semakin banyak pula tembakan yang tepat sasaran.
        * Untuk `FTR = 0` (Home Win, warna merah), umumnya titik-titik memiliki `HST` yang lebih tinggi dibandingkan dengan `FTR = 1` (Draw, warna biru) atau `FTR = 2` (Away Win, warna hijau) pada tingkat `HS` yang sama. Ini menunjukkan bahwa tim tuan rumah yang menang cenderung memiliki efisiensi tembakan tepat sasaran yang lebih baik.

    * **Away Shots vs Away Goals (FTR)**:
        ![awayshoot_vs_awaygoals.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/awayshoot_vs_awaygoals.png)
        Plot ini menunjukkan hubungan antara jumlah tembakan yang dilakukan tim tandang (`AS`) dengan jumlah gol yang dicetak tim tandang (`FTAG`), dikelompokkan berdasarkan hasil akhir pertandingan (`FTR`).
        * Mirip dengan tim tuan rumah, ada tren positif antara `AS` dan `FTAG`.
        * Untuk `FTR = 2` (Away Win, warna hijau), sebagian besar titik berada pada `FTAG` yang lebih tinggi, menunjukkan bahwa kemenangan tandang seringkali didukung oleh gol yang lebih banyak.
        * Untuk `FTR = 0` (Home Win, warna merah), titik-titik cenderung berada pada `FTAG` yang rendah (seringkali 0 atau 1), yang masuk akal karena tim tandang kalah.

    * **Away Shots vs On-Target (FTR)**:
        ![awayshoot_vs_ontarget.png](https://github.com/ZackyFaishal/EPL_match_prediction/blob/main/Result_Photo/awayshoot_vs_ontarget.png)
        Plot ini menunjukkan hubungan antara jumlah tembakan yang dilakukan tim tandang (`AS`) dengan jumlah tembakan tepat sasaran tim tandang (`AST`), dikelompokkan berdasarkan hasil akhir pertandingan (`FTR`).
        * Korelasi positif yang kuat antara `AS` dan `AST` sangat terlihat.
        * Untuk `FTR = 2` (Away Win, warna hijau), umumnya titik-titik memiliki `AST` yang lebih tinggi dibandingkan dengan `FTR = 0` (Home Win, warna merah) atau `FTR = 1` (Draw, warna biru) pada tingkat `AS` yang sama. Ini menunjukkan bahwa tim tandang yang menang cenderung memiliki efisiensi tembakan tepat sasaran yang lebih baik.

    Secara keseluruhan, scatter plot ini memberikan pemahaman visual tentang bagaimana metrik serangan (tembakan dan tembakan tepat sasaran) berkorelasi dengan jumlah gol yang dicetak dan bagaimana hal itu mempengaruhi hasil akhir pertandingan untuk kedua tim (tuan rumah dan tandang).
## Data Preparation

Setelah tahapan *Data Preparation* setelah EDA adalah sebagai berikut:
1.  **Mengatasi Kolom Non-Numerik**: Proses ini merupakan langkah krusial untuk memastikan bahwa semua data siap untuk diumpankan ke dalam algoritma *machine learning*, yang sebagian besar memerlukan input numerik.
    * **Transformasi Kolom `Date` dan `Time`**:
        * Kolom `Date` dan `Time` yang awalnya bertipe `object` (string) dikombinasikan menjadi satu kolom `Datetime`.
        * Kemudian, kolom `Datetime` ini dipecah menjadi beberapa fitur waktu numerik yang lebih granular: `Year`, `Month`, `Day`, `Weekday`, dan `Hour`. Pemecahan ini memungkinkan model untuk menangkap pola musiman, tren harian, atau bahkan pola berdasarkan jam pertandingan.
        * Kolom asli `Date`, `Time`, dan `Datetime` kemudian dihapus untuk menghindari redundansi dan memastikan data bersih.
    * **Encoding Variabel Kategorikal (`HomeTeam`, `AwayTeam`, `FTR`, `HTR`, `Referee`)**:
        * Kolom `HomeTeam` dan `AwayTeam` yang berisi nama tim di-*encode* menggunakan `LabelEncoder`. Ini mengubah setiap nama tim unik menjadi nilai numerik diskrit. Misalnya, "Manchester United" bisa menjadi 0, "Liverpool" menjadi 1, dan seterusnya.
        * Kolom `FTR` (Full Time Result) dan `HTR` (Half Time Result) yang memiliki nilai kategori `H` (Home Win), `D` (Draw), dan `A` (Away Win) diubah menjadi nilai numerik. Berdasarkan konteks umum dalam proyek prediksi sepak bola, pemetaan manual yang sering digunakan adalah: `H`: 0 (Home Win), `D`: 1 (Draw), `A`: 2 (Away Win). Pemetaan ini memastikan bahwa variabel target memiliki representasi numerik yang konsisten.
        * Kolom `Referee` juga di-*encode* menggunakan `LabelEncoder`, mengubah nama wasit menjadi nilai numerik unik.

2.  **Pembagian Data Latih dan Data Uji**: Setelah semua data diolah menjadi format numerik, dataset dibagi menjadi set pelatihan dan set pengujian. Pembagian ini dilakukan dengan rasio 80:20, di mana 80% data digunakan untuk melatih model dan 20% sisanya digunakan untuk mengevaluasi kinerja model pada data yang belum pernah dilihat sebelumnya. Ini penting untuk mengukur kemampuan generalisasi model dan mencegah *overfitting*.

3.  **Hasil Akhir**: Semua kolom dalam dataset sekarang bertipe numerik dan siap untuk *training* model *machine learning*.

## Modeling

Bagian ini menguraikan proses pembangunan model *machine learning* yang dirancang untuk memprediksi hasil akhir pertandingan sepak bola (Home Win, Draw, Away Win) berdasarkan kumpulan data historis Liga Inggris.

### Pemilihan Model

Dalam upaya prediksi ini, empat algoritma *supervised learning* yang berbeda telah digunakan: **Random Forest**, **Logistic Regression**, **Support Vector Machine (SVM)**, dan **XGBoost**. Pemilihan ini didasari oleh kombinasi kekuatan generalisasi, kemudahan interpretasi, dan performa yang telah terbukti dalam menghadapi tantangan klasifikasi serupa di bidang prediksi pertandingan dan olahraga.

Berikut adalah rasionalisasi untuk setiap pilihan model:

1.  **Random Forest**: Algoritma ini merupakan model *ensemble* yang didasarkan pada kumpulan pohon keputusan, secara inheren mampu menangani baik data kategorikal maupun numerik. Random Forest dikenal kokoh terhadap masalah *overfitting* dan efektif dalam mengelola dataset dengan fitur-fitur yang saling berkorelasi. Untuk tugas memprediksi hasil pertandingan yang mungkin melibatkan banyak atribut seperti statistik tim, performa sebelumnya, atau kondisi lapangan, Random Forest menawarkan solusi yang stabil dan cukup mudah diinterpretasikan.

2.  **Logistic Regression**: Model ini dijadikan *baseline* karena kesederhanaan dan kemudahannya untuk diinterpretasikan. Meskipun bersifat linear, Logistic Regression masih dapat memberikan kinerja yang baik, terutama jika fitur-fitur yang digunakan telah melalui proses seleksi dan normalisasi.

3.  **Support Vector Machine (SVM)**: SVM dipilih karena kemampuannya untuk mengidentifikasi batas keputusan yang kompleks, yang mungkin muncul dalam data pertandingan yang dinamis. Selain itu, SVM cenderung berkinerja baik pada dataset dengan banyak fitur dan data yang mungkin tidak seimbang.

4.  **XGBoost**: XGBoost terkenal karena kecepatan dan performa tinggi dalam berbagai kompetisi dan studi klasifikasi. Model ini mampu menangkap interaksi non-linear antar fitur dengan lebih efisien dan seringkali melampaui model lain pada data tabular yang kompleks, seperti data pertandingan yang melibatkan banyak variabel dengan tingkat pengaruh yang bervariasi.

### Langkah Pemodelan

Setelah menetapkan algoritma *machine learning* yang akan diterapkan, proses pelatihan model melibatkan beberapa langkah sistematis:

1.  **Inisialisasi Model**: Setiap algoritma diinisialisasi dengan parameter dasar dan `random_state` yang telah ditentukan. Penggunaan `random_state` ini bertujuan untuk memastikan bahwa hasil yang diperoleh dapat direplikasi dalam eksperimen selanjutnya.

2.  **Penentuan Hyperparameter Grid**: Untuk setiap model, serangkaian kombinasi *hyperparameter* yang akan diuji disusun menggunakan *Grid Search*. Rentang nilai yang dipilih didasarkan pada praktik umum yang telah terbukti efektif dalam meningkatkan kinerja model.

3.  **Grid Search dengan Cross Validation**: *Grid Search* dilakukan bersamaan dengan teknik K-Fold Cross Validation untuk mengidentifikasi kombinasi *hyperparameter* yang paling optimal. Pendekatan ini membantu dalam mengevaluasi model secara lebih robust dan mengurangi risiko *overfitting*.

4.  **Evaluasi dengan Skor f1_macro**: Metrik `f1_macro` digunakan sebagai kriteria evaluasi utama. Pemilihan `f1_macro` didasarkan pada fakta bahwa prediksi hasil pertandingan adalah masalah klasifikasi multikelas (menang, kalah, seri), dan metrik ini mampu menyeimbangkan performa model di seluruh kelas secara merata.

5.  **Seleksi Model Terbaik**: Model yang menunjukkan skor validasi tertinggi dan konfigurasi *hyperparameter* terbaik akan dipilih untuk digunakan dalam tahap prediksi akhir.

Dengan pemilihan model dan proses *tuning* yang tepat, diharapkan sistem ini mampu memprediksi hasil pertandingan secara akurat dan seimbang.

#### Pelatihan Random Forest

Model *machine learning* yang diaplikasikan dalam proyek ini adalah **Random Forest**. Random Forest merupakan model *ensemble learning* yang beroperasi dengan mengintegrasikan beberapa *decision tree*.

**Mekanisme Kerja:**

1.  **Bootstrapping:** Awalnya, beberapa subset data dibuat dari dataset asli melalui teknik *bootstrap*, yaitu pengambilan sampel acak dengan penggantian.
2.  **Pembentukan Pohon Keputusan:** Setiap subset data ini kemudian digunakan untuk melatih sebuah *decision tree* independen.
3.  **Prediksi Individual:** Saat melakukan prediksi, setiap *decision tree* memberikan "suaranya" berdasarkan pola yang telah dipelajarinya.
4.  **Konsolidasi Hasil:** Prediksi akhir ditentukan dengan menggabungkan hasil prediksi dari seluruh *decision tree* melalui metode *majority voting* (untuk tugas klasifikasi).

**Parameter Kunci Model:**

Berikut adalah parameter utama Random Forest yang disesuaikan dan rentang nilai yang diujikan dalam *GridSearchCV*:

* `n_estimators`: Mengacu pada jumlah *decision tree* yang akan dibangun dalam model.
* `max_depth`: Menentukan kedalaman maksimum yang diizinkan untuk setiap *decision tree*.

**Penyesuaian Hyperparameter:**

* Dalam proyek ini, penyesuaian *hyperparameter* dilakukan menggunakan `GridSearchCV` untuk mengidentifikasi kombinasi optimal dari parameter `n_estimators` dan `max_depth`.
* `GridSearchCV` akan mengeksplorasi semua kombinasi parameter yang didefinisikan dalam `param_grid_rf = {'n_estimators': [100, 200, 300], 'max_depth': [None, 5, 10]}`.
* Kriteria evaluasi yang dipakai adalah `scoring='f1_macro'`, yang berfungsi untuk mengukur kinerja model secara keseluruhan dalam skenario multikelas.

#### Pelatihan Logistic Regression

Model **Logistic Regression** digunakan sebagai model *baseline* dan juga sebagai salah satu model kandidat. Meskipun linear, model ini efektif untuk masalah klasifikasi, terutama jika hubungan antara fitur dan target relatif langsung.

**Mekanisme Kerja:**

1.  **Regresi Logistik:** Model ini mengestimasi probabilitas suatu peristiwa terjadi dengan memetakan output linear ke kurva sigmoid, menghasilkan nilai probabilitas antara 0 dan 1.
2.  **Klasifikasi Multi-Kelas (OvR):** Untuk masalah klasifikasi multikelas seperti prediksi hasil pertandingan (Home Win, Draw, Away Win), Logistic Regression secara *default* menggunakan pendekatan One-vs-Rest (OvR). Ini berarti model melatih satu klasifikasi biner untuk setiap kelas, membedakan kelas tersebut dari semua kelas lainnya.

**Parameter Kunci Model:**

Parameter utama Logistic Regression yang disesuaikan dan rentang nilai yang diujikan dalam *GridSearchCV*:

* `C`: Parameter invers kekuatan regularisasi. Nilai yang lebih kecil menunjukkan regularisasi yang lebih kuat.
* `solver`: Algoritma yang digunakan dalam optimasi.

**Penyesuaian Hyperparameter:**

* Penyesuaian *hyperparameter* dilakukan menggunakan `GridSearchCV` untuk menemukan kombinasi optimal.
* `GridSearchCV` akan mengeksplorasi kombinasi parameter yang didefinisikan dalam `param_grid_lr = {'C': [0.1, 1, 10], 'solver': ['liblinear', 'saga']}`.
* Kriteria evaluasi yang dipakai adalah `scoring='f1_macro'`.

#### Pelatihan Support Vector Machine (SVM)

**Support Vector Machine (SVM)** adalah algoritma yang kuat untuk klasifikasi yang mencari *hyperplane* optimal untuk memisahkan kelas-kelas dalam ruang fitur.

**Mekanisme Kerja:**

1.  **Pemisahan Hyperplane:** SVM bekerja dengan mencari *hyperplane* (bidang pemisah) terbaik yang memaksimalkan *margin* (jarak terdekat) antara titik data dari kelas-kelas yang berbeda.
2.  **Kernel Trick:** Untuk data yang tidak dapat dipisahkan secara linear, SVM menggunakan *kernel trick* untuk memetakan data ke ruang berdimensi lebih tinggi di mana pemisahan linear dimungkinkan.

**Parameter Kunci Model:**

Parameter utama SVM yang disesuaikan dan rentang nilai yang diujikan dalam *GridSearchCV*:

* `C`: Parameter regularisasi, mengontrol *trade-off* antara *margin* besar dan kesalahan klasifikasi kecil.
* `kernel`: Fungsi kernel yang digunakan (misalnya, 'rbf' untuk non-linear).

**Penyesuaian Hyperparameter:**

* Penyesuaian *hyperparameter* dilakukan menggunakan `GridSearchCV` untuk mengidentifikasi kombinasi optimal.
* `GridSearchCV` akan mengeksplorasi kombinasi parameter yang didefinisikan dalam `param_grid_svm = {'C': [0.1, 1, 10], 'kernel': ['rbf']}`.
* Kriteria evaluasi yang dipakai adalah `scoring='f1_macro'`.

#### Pelatihan XGBoost

Selain model-model di atas, proyek ini juga memanfaatkan **XGBoost (Extreme Gradient Boosting)**, sebuah algoritma *boosting* yang terkenal karena efisiensi dan tingkat akurasi prediksi yang tinggi, terutama dalam tugas-tugas klasifikasi multikelas seperti prediksi hasil pertandingan.

**Prinsip Kerja Model:**

1.  **Peningkatan Bertahap:** Model dibangun secara iteratif, di mana setiap *decision tree* yang baru berusaha untuk memperbaiki kesalahan prediksi yang dibuat oleh model-model sebelumnya.
2.  **Fokus pada Kesalahan:** Data yang sebelumnya diprediksi secara keliru akan diberi bobot yang lebih besar, sehingga model berikutnya akan lebih fokus untuk mempelajari pola-pola tersebut.
3.  **Integrasi Model:** Seluruh pohon yang telah dilatih kemudian digabungkan menjadi satu model yang kuat melalui proses penjumlahan berbobot (*weighted sum*).

**Parameter Utama:**

Parameter penting yang disesuaikan dalam konfigurasi XGBoost meliputi:

* `learning_rate`: Mengatur kecepatan pembelajaran atau seberapa besar model melakukan koreksi kesalahan pada setiap iterasi.
* `n_estimators`: Menunjukkan total jumlah *decision tree* yang akan dibangun selama proses *boosting*.

**Penyesuaian Hyperparameter:**

* Penyesuaian *hyperparameter* dilakukan dengan bantuan `GridSearchCV`, yang mencari kombinasi parameter terbaik berdasarkan kinerja model.
* Ruang pencarian parameter yang digunakan adalah `param_grid_xgb = {'learning_rate': [0.1, 0.01], 'n_estimators': [100, 200, 300]}`.
* Evaluasi dilakukan menggunakan metrik `scoring='f1_macro'`, yang sesuai untuk menilai performa dalam klasifikasi multikelas.


## Evaluation

Bagian ini membahas evaluasi kinerja model-model *machine learning* yang telah dilatih untuk memprediksi hasil pertandingan sepak bola. Evaluasi dilakukan dengan menggunakan metrik-metrik yang relevan dan interpretasi hasil untuk menentukan model terbaik serta tingkat keberhasilan proyek.

### Metrik Evaluasi

Untuk menilai performa model *machine learning* dalam memprediksi hasil pertandingan (Home Win, Draw, Away Win), digunakan beberapa metrik evaluasi standar untuk klasifikasi multikelas:

* **Akurasi:** Mengukur proporsi total prediksi yang benar dari seluruh data uji.
* **Presisi (Micro):** Menghitung kemampuan model untuk menghindari positif palsu secara keseluruhan, dengan mempertimbangkan setiap kelas secara individual dan kemudian merata-ratakannya secara global.
* **Recall (Micro):** Mengukur kemampuan model untuk mengidentifikasi semua kasus positif secara keseluruhan, dengan mempertimbangkan setiap kelas secara individual dan kemudian merata-ratakannya secara global.
* **F1-Score (Micro):** Merupakan rata-rata harmonik dari presisi (micro) dan recall (micro), yang memberikan ukuran gabungan dari kedua metrik tersebut dan sangat berguna untuk menyeimbangkan performa model pada semua kelas.

Pemilihan metrik `micro` untuk presisi, *recall*, dan F1-score bertujuan untuk memberikan evaluasi menyeluruh dari berbagai aspek performa model pada kasus klasifikasi multikelas ini. Akurasi memberikan gambaran umum seberapa sering model membuat prediksi yang tepat.

### Hasil Evaluasi

Berikut adalah hasil evaluasi untuk keempat model yang telah dilatih dan disetel *hyperparameter*-nya pada data pengujian:

#### Hyperparameter Terbaik dan Performa Model

* **Random Forest**
    * Parameter Terbaik: `{'max_depth': 20, 'min_samples_leaf': 1, 'n_estimators': 100}`
    * Akurasi: 0.9796
    * Presisi (micro): 0.9796
    * Recall (micro): 0.9796
    * F1-score (micro): 0.9796

* **Logistic Regression**
    * Parameter Terbaik: `{'C': 10, 'penalty': 'l2', 'solver': 'lbfgs'}`
    * Akurasi: 1.0000
    * Presisi (micro): 1.0000
    * Recall (micro): 1.0000
    * F1-score (micro): 1.0000

* **Support Vector Machine (SVM)**
    * Parameter Terbaik: `{'C': 0.1, 'kernel': 'linear'}`
    * Akurasi: 1.0000
    * Presisi (micro): 1.0000
    * Recall (micro): 1.0000
    * F1-score (micro): 1.0000

* **XGBoost**
    * Parameter Terbaik: `{'learning_rate': 0.05, 'max_depth': 5, 'n_estimators': 100}`
    * Akurasi: 1.0000
    * Presisi (micro): 1.0000
    * Recall (micro): 1.0000
    * F1-score (micro): 1.0000

Berikut adalah ringkasan hasil evaluasi keempat model:

| Model                | Akurasi | Presisi (micro) | Recall (micro) | F1-score (micro) |
| :------------------- | :------ | :-------------- | :------------- | :--------------- |
| Random Forest        | 0.9796  | 0.9796          | 0.9796         | 0.9796           |
| Logistic Regression  | 1.0000  | 1.0000          | 1.0000         | 1.0000           |
| SVM                  | 1.0000  | 1.0000          | 1.0000         | 1.0000           |
| XGBoost              | 1.0000  | 1.0000          | 1.0000         | 1.0000           |

### Analisis dan Interpretasi

Dari tabel hasil evaluasi, dapat diamati bahwa Logistic Regression, SVM, dan XGBoost menunjukkan performa yang sangat tinggi, mencapai akurasi, presisi, *recall*, dan F1-score sebesar 1.0000 pada data pengujian. Random Forest juga menunjukkan performa yang sangat baik dengan nilai 0.9796 untuk semua metrik.

* **Akurasi:** Logistic Regression, SVM, dan XGBoost mencapai akurasi sempurna (1.0000), menunjukkan bahwa model-model ini mampu memprediksi hasil pertandingan dengan sangat tepat pada data tes yang digunakan. Random Forest juga mendekati kesempurnaan dengan akurasi 0.9796.
* **Presisi (micro):** Nilai presisi (micro) yang 1.0000 untuk Logistic Regression, SVM, dan XGBoost mengindikasikan bahwa hampir semua prediksi positif yang dibuat oleh model-model ini adalah benar. Random Forest juga memiliki presisi yang sangat tinggi (0.9796).
* **Recall (micro):** Dengan *recall* (micro) sebesar 1.0000, Logistic Regression, SVM, dan XGBoost sangat efektif dalam mengidentifikasi semua kasus positif yang relevan dalam data. Random Forest juga menunjukkan kemampuan *recall* yang kuat (0.9796).
* **F1-score (micro):** F1-score (micro) sebesar 1.0000 untuk ketiga model tersebut menegaskan keseimbangan optimal antara presisi dan *recall*. Random Forest dengan F1-score 0.9796 juga menunjukkan keseimbangan yang sangat baik.

### Pemilihan Model Terbaik

Berdasarkan hasil evaluasi, **Logistic Regression, SVM, dan XGBoost menunjukkan kinerja yang identik dan sempurna (1.0000)** pada data pengujian. Hal ini mengindikasikan bahwa ketiga model ini sangat andal untuk memprediksi hasil pertandingan Liga Inggris dengan dataset yang ada. Random Forest juga merupakan model yang sangat kuat dengan performa yang mendekati sempurna.

Meskipun ketiga model tersebut mencapai performa maksimal pada data tes ini, dalam implementasi nyata, pemilihan model mungkin juga mempertimbangkan faktor lain seperti kompleksitas komputasi, waktu pelatihan, dan interpretasi model. Namun, berdasarkan metrik evaluasi yang disajikan, ketiganya adalah pilihan yang sangat direkomendasikan.

**Kesimpulannya, Logistic Regression, SVM, dan XGBoost adalah pilihan yang sangat kuat** untuk diterapkan dalam sistem prediksi ini, dengan performa yang unggul dan seimbang.

## Conclusion

Proyek prediksi hasil pertandingan sepak bola Liga Inggris ini telah melalui berbagai tahapan kunci, dari awal perumusan masalah hingga evaluasi model, dengan tujuan utama untuk membangun sebuah sistem yang dapat memprediksi hasil akhir pertandingan (kemenangan tuan rumah, seri, atau kemenangan tandang) berdasarkan data historis.

Pada tahap awal **Pemahaman Bisnis**, proyek ini secara spesifik mengidentifikasi dua tantangan utama: pertama, bagaimana mengenali faktor-faktor paling krusial dari data pertandingan sepak bola yang memengaruhi hasil akhir; dan kedua, bagaimana mengembangkan serta menilai efektivitas model *Machine Learning* untuk prediksi tersebut. Tujuan yang ditetapkan meliputi integrasi data dari beberapa musim, pembersihan data, rekayasa fitur, analisis sebaran variabel-variabel penting, identifikasi *outlier*, serta konstruksi model prediktif yang akurat. Manfaat potensial dari inisiatif ini sangat luas, mencakup peningkatan akurasi prediksi, penyediaan wawasan berbasis data untuk analis dan jurnalis, hingga aplikasi praktis dalam industri taruhan olahraga.

Dalam fase **Pemahaman Data**, kumpulan data yang digunakan adalah "Match Prediction Project", yang berisi rekaman pertandingan Liga Inggris dari musim 2020-2021 hingga 2024-2025, yang diperoleh dari situs football-data.co.uk. Dataset awal terdiri dari lima berkas CSV terpisah yang kemudian digabungkan. Variabel-variabel yang dianalisis mencakup rincian pertandingan seperti tim, skor, jumlah tembakan, pelanggaran, dan kartu yang diberikan. Penekanan diberikan pada transformasi tipe data, di mana kolom-kolom seperti `Date`, `Time`, `HomeTeam`, `AwayTeam`, `FTR`, `HTR`, dan `Referee` dikonversi ke format numerik agar sesuai untuk pemodelan *machine learning*.

Tahap **Pembersihan Data** melibatkan penyatuan kelima berkas CSV menjadi satu dataset komprehensif (`all_matches.csv`). Kolom-kolom yang tidak relevan, terutama yang berkaitan dengan *odds*, dihilangkan untuk menyederhanakan dataset. Selain itu, dilakukan penyesuaian untuk kolom non-numerik, seperti konversi `Date` dan `Time` menjadi fitur waktu numerik, serta *encoding* label untuk `HomeTeam`, `AwayTeam`, `FTR`, `HTR`, dan `Referee`.

**Analisis Data Eksplorasi (EDA)** memberikan pemahaman mendalam tentang dataset. Pemeriksaan awal mengungkapkan bahwa dataset terdiri dari 732 pertandingan tanpa adanya nilai yang hilang. Statistik deskriptif menunjukkan keunggulan rata-rata gol dan kemenangan untuk tim tuan rumah, sementara tim tandang cenderung menerima lebih banyak kartu kuning. Meskipun beberapa *outlier* ditemukan pada statistik gol, tembakan, dan kartu, nilai-nilai ini dianggap valid dalam konteks pertandingan sepak bola dan dipertahankan untuk proses pemodelan. Analisis univariat lebih lanjut memperlihatkan fluktuasi jumlah pertandingan bulanan dengan puncaknya pada Februari dan April, sebagian besar laga berlangsung sore hari (sekitar pukul 15.00-17.00 WIB), dan tersebar sepanjang minggu. Analisis multivariat melalui *heatmap* korelasi mengindikasikan hubungan kuat antara gol dan tembakan tepat sasaran, serta korelasi antara gol dan hasil pertandingan. *Boxplot* dan *scatter plot* turut memperjelas distribusi variabel dan hubungannya dengan hasil laga.

Pada fase **Persiapan Data**, setelah EDA, data disempurnakan lebih lanjut. Kolom `Date` dan `Time` digabungkan lalu dipecah menjadi fitur waktu numerik (`Year`, `Month`, `Day`, `Weekday`, `Hour`), sementara `HomeTeam`, `AwayTeam`, `FTR`, `HTR`, dan `Referee` di-*encode* menjadi format numerik. Selanjutnya, dataset dibagi menjadi set pelatihan dan pengujian dengan perbandingan 80:20, menggunakan `stratify=y` untuk menjaga distribusi proporsional kelas target. Setelah tahapan ini, seluruh kolom dalam dataset telah berformat numerik dan siap untuk proses pelatihan model.

Fase **Pemodelan** mencakup penggunaan empat algoritma *supervised learning*: Random Forest, Logistic Regression, Support Vector Machine (SVM), dan XGBoost. Pilihan model-model ini didasarkan pada kombinasi kemampuan generalisasi, kemudahan interpretasi, dan performa yang telah terbukti dalam tugas klasifikasi. Setiap model diinisialisasi, dan proses *hyperparameter tuning* dilakukan menggunakan *Grid Search* bersamaan dengan K-Fold Cross Validation. Metrik `f1_macro` digunakan sebagai kriteria evaluasi utama selama penyetelan parameter untuk mencapai keseimbangan performa di semua kelas. Parameter spesifik untuk setiap model, seperti `n_estimators` dan `max_depth` untuk Random Forest, `C` dan `solver` untuk Logistic Regression, `C` dan `kernel` untuk SVM, serta `learning_rate` dan `n_estimators` untuk XGBoost, telah disesuaikan guna mengoptimalkan kinerja.

Terakhir, pada tahap **Evaluasi**, seluruh model diuji pada data yang terpisah. Hasilnya menunjukkan bahwa Logistic Regression, SVM, dan XGBoost mencapai performa sempurna dengan Akurasi, Presisi (micro), Recall (micro), dan F1-score (micro) sebesar 1.0000 pada data pengujian. Random Forest juga menunjukkan kinerja yang sangat kuat dengan skor 0.9796 untuk semua metrik. Logistic Regression, SVM, dan XGBoost mencapai performa maksimal, mengindikasikan kapabilitas prediksi yang luar biasa.

Secara keseluruhan, inisiatif ini berhasil dalam membangun model-model prediktif yang sangat akurat untuk memprediksi hasil pertandingan sepak bola Liga Inggris, menunjukkan potensi besar dalam memberikan wawasan berbasis data dan menunjang pengambilan keputusan.

Berdasarkan hasil eksplorasi data (EDA) dan analisis korelasi, variabel-variabel seperti total gol yang dicetak oleh tim tuan rumah (`FTHG`) dan tim tamu (`FTAG`), serta jumlah tembakan yang tepat sasaran (`HST`, `AST`), memperlihatkan korelasi kuat dengan hasil pertandingan (`FTR`). Hal ini logis mengingat gol adalah penentu langsung hasil akhir, dan tembakan tepat sasaran merupakan indikator utama peluang mencetak gol. Variabel seperti `HomeTeam` dan `AwayTeam` (setelah melalui *encoding*), `HTR` (hasil paruh waktu), dan statistik pertandingan lainnya juga memainkan peran signifikan dalam membedakan hasil pertandingan. Adanya korelasi positif antara jumlah pelanggaran dan kartu kuning (`HF`, `AF` dengan `HY`, `AY`) juga terkonfirmasi.

Meskipun model-model yang dikembangkan menunjukkan hasil evaluasi yang sangat menjanjikan, proyek ini tetap memiliki beberapa keterbatasan:

* **Kualitas dan Kelengkapan Data**: Meskipun dataset historis dari football-data.co.uk cukup komprehensif, data pertandingan sepak bola bersifat sangat kompleks dan mungkin melibatkan banyak faktor yang tidak terukur secara numerik, seperti performa individu pemain, motivasi tim, kondisi cuaca, atau keputusan wasit yang tidak selalu terekam. Potensi bias dalam pengumpulan data atau ketiadaan variabel-variabel tersebut dapat membatasi kedalaman interpretasi model.
* **Interpretasi Model**: Beberapa algoritma yang digunakan, seperti Random Forest dan XGBoost, memiliki karakteristik *black box*, yang mempersulit penjelasan detail mengenai kontribusi spesifik setiap fitur terhadap prediksi. Hal ini dapat menjadi tantangan apabila interpretasi kausal diperlukan untuk merumuskan strategi pertandingan yang lebih mendalam.
* **Generalisasi Model**: Model dilatih menggunakan data dari Liga Inggris musim 2020-2025. Meskipun periode ini mencakup beragam dinamika, model perlu diuji lebih lanjut untuk validitas eksternal pada liga lain, musim yang berbeda jauh, atau bahkan perubahan signifikan dalam regulasi permainan atau susunan tim.




## Next Project

Untuk pengembangan di masa mendatang, beberapa rekomendasi dapat diajukan:

* **Rekayasa Fitur yang Lebih Mendalam**: Menciptakan fitur-fitur baru yang lebih kaya informasi, misalnya performa tim dalam beberapa pertandingan terakhir (seperti rata-rata gol per pertandingan dalam lima laga terakhir), statistik *head-to-head* antar tim, atau peringkat tim berdasarkan metrik performa khusus. Selain itu, eksplorasi fitur yang terkait dengan momentum atau performa *in-match* yang lebih detail (jika data tersedia) dapat memperkaya dataset.
* **Validasi Eksternal**: Menguji model pada data pertandingan dari liga atau musim yang berbeda secara signifikan guna menguji kemampuan generalisasi model dan memastikan kekokohannya.
* **Analisis Sentimen dan Berita**: Mengintegrasikan data sentimen dari media sosial atau hasil analisis berita olahraga untuk mengidentifikasi pengaruh faktor non-statistik terhadap hasil pertandingan. Faktor psikologis dan informasi tim (seperti cedera pemain kunci atau perubahan pelatih) seringkali memiliki dampak signifikan.
* **Pengembangan Aplikasi *Real-time***: Mengembangkan sebuah aplikasi sederhana yang dapat memanfaatkan model untuk memberikan prediksi pertandingan secara *real-time*, lengkap dengan probabilitas hasil dan penjelasan mengenai faktor-faktor yang memengaruhi prediksi tersebut.
* **Kolaborasi dengan para analisis Olahraga**: Melibatkan analis atau pakar sepak bola dalam proses validasi dan interpretasi hasil untuk memperoleh wawasan domain yang lebih dalam dan meningkatkan relevansi serta kegunaan model.