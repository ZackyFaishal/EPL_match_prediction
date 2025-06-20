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
## Data Preparation

Berdasarkan *notebook* yang diberikan, tahapan *Data Preparation* setelah EDA adalah sebagai berikut:
1.  **Mengatasi Kolom Non-Numerik**: Kolom `Date` dan `Time` digabungkan menjadi `Datetime`, lalu dipecah menjadi `Year`, `Month`, `Day`, `Weekday`, `Hour`. Kolom `HomeTeam`, `AwayTeam`, `FTR`, `HTR`, dan `Referee` di-*encode* menjadi numerik menggunakan `LabelEncoder` dan *mapping*.
2.  **Hasil Akhir**: Semua kolom dalam dataset sekarang bertipe numerik dan siap untuk *training* model *machine learning*.

## Modeling

Informasi mengenai tahapan *Modeling* tidak tersedia secara lengkap dalam *notebook* `match_prediction.ipynb` yang diberikan. Namun, cuplikan kode menunjukkan adanya proses *tuning* model dan evaluasi beberapa model yang disimpan dalam `all_results`, yang menyiratkan penggunaan model *machine learning* untuk klasifikasi. Metrik evaluasi yang dihitung adalah Akurasi, Presisi (micro), Recall (micro), dan F1-score (micro).

## Evaluation

Informasi mengenai hasil *Evaluation* secara spesifik (nilai-nilai metrik) tidak tersedia dalam *notebook* `match_prediction.ipynb` yang diberikan. Namun, *notebook* menunjukkan bahwa model dievaluasi menggunakan:
* Akurasi (`accuracy_score`)
* Presisi mikro (`precision_score` dengan `average='micro'`)
* Recall mikro (`recall_score` dengan `average='micro'`)
* F1-score mikro (`f1_score` dengan `average='micro'`)

Ini mengindikasikan bahwa model klasifikasi digunakan untuk memprediksi hasil pertandingan (Home Win, Draw, Away Win) dan performanya diukur dengan metrik-metrik tersebut.

## Conclusion

Berdasarkan Analisis Data Eksplorasi (EDA), dapat disimpulkan bahwa dataset pertandingan sepak bola Liga Inggris dari musim 2020-2025 cukup komprehensif, dengan 732 pertandingan dan tidak ada *missing values*. Tim tuan rumah memiliki keunggulan gol dan kemenangan rata-rata, dan tim tandang cenderung mendapatkan lebih banyak kartu kuning. Meskipun terdapat *outlier* pada statistik gol, tembakan, dan kartu, nilai-nilai ini dianggap valid secara kontekstual dan dipertahankan untuk *modeling*. Fitur-fitur seperti `Date`, `Time`, `HomeTeam`, `AwayTeam`, `FTR`, `HTR`, dan `Referee` telah berhasil diubah menjadi format numerik, menjadikan data siap untuk pelatihan model *machine learning*.

Meskipun detail spesifik model dan hasil evaluasinya tidak disertakan dalam *notebook* yang diberikan, struktur kode menunjukkan adanya upaya untuk melatih dan mengevaluasi model klasifikasi untuk memprediksi hasil pertandingan menggunakan metrik standar seperti akurasi, presisi, *recall*, dan F1-score.

## Next Project

Informasi mengenai rencana *Next Project* tidak tersedia secara eksplisit dalam *notebook* `match_prediction.ipynb` yang diberikan. Namun, pengembangan lebih lanjut dapat meliputi:

* **Penerapan Model Lanjutan**: Mengeksplorasi model-model *machine learning* yang lebih kompleks atau *ensemble methods* untuk meningkatkan akurasi prediksi.
* **Rekayasa Fitur Lanjutan**: Membuat fitur-fitur baru seperti performa tim dalam beberapa pertandingan terakhir, rata-rata gol per pertandingan, *head-to-head* antar tim, atau *rankings* tim untuk memperkaya dataset.
* **Validasi Eksternal**: Menguji model pada data pertandingan dari liga atau musim yang berbeda untuk menguji generalisasi model.
* **Analisis Sentimen**: Menggabungkan data sentimen dari berita atau media sosial untuk melihat pengaruhnya terhadap hasil pertandingan.
* **Pengembangan Aplikasi**: Membuat aplikasi sederhana yang dapat menggunakan model untuk memberikan prediksi pertandingan secara *real-time*.