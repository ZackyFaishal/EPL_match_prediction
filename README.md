# ⚽️ EPL Match Prediction Project  

## 📄 Deskripsi Proyek  
Proyek **Match Prediction** ini bertujuan untuk memprediksi **hasil pertandingan sepak bola Liga Inggris (2020–2025)** menggunakan **Machine Learning**.  
Langkah-langkah yang dilakukan meliputi:  
- Menggabungkan dataset pertandingan dari tahun 2020–2025  
- Melakukan **data cleansing** dan **feature engineering**  
- Melakukan **EDA (Exploratory Data Analysis)** untuk memahami pola data  
- Menerapkan **4 algoritma Machine Learning**:  
  - 🌲 **Random Forest**  
  - 📈 **Logistic Regression**  
  - 🌀 **Support Vector Machine (SVM)**  
  - ⚡ **XGBoost**  
- Melakukan **GridSearchCV + Cross Validation** untuk tuning hyperparameter  
- Mengevaluasi model dengan metrik akurasi, presisi, recall, dan F1-score  

Proyek ini membantu menganalisis faktor-faktor yang memengaruhi hasil pertandingan dan memberikan insight statistik serta prediksi hasil pertandingan ke depannya.

---

## 📊 Tahapan Proyek  

### 1. **Data Understanding**
- Dataset pertandingan Liga Inggris 2020–2025 dari [Football-data.co.uk](https://www.football-data.co.uk/englandm.php)
- Menggabungkan 5 file CSV menjadi satu dataset

### 2. **Data Cleaning & Feature Engineering**
- Menghapus kolom odds yang tidak relevan
- Ekstraksi fitur waktu (`Year`, `Month`, `Day`, `Weekday`, `Hour`)
- Label encoding untuk `HomeTeam`, `AwayTeam`, `Referee`
- Konversi target `FTR` dan `HTR` (H=0, D=1, A=2)

### 3. **Exploratory Data Analysis (EDA)**
- Distribusi hasil pertandingan (Home Win, Draw, Away Win)
- Rata-rata gol, kartu kuning, tembakan, dan statistik lainnya
- Korelasi antar variabel numerik menggunakan heatmap
- Deteksi outlier dengan boxplot & IQR

### 4. **Modeling**
Menggunakan empat algoritma utama:
- 🌲 **Random Forest**
- 📈 **Logistic Regression**
- 🌀 **Support Vector Machine (SVM)**
- ⚡ **XGBoost**

Langkah-langkah modeling:
- Split data **80:20** train-test
- Standarisasi fitur dengan `StandardScaler`
- Hyperparameter tuning dengan **GridSearchCV + Stratified K-Fold Cross Validation**
- Evaluasi model berdasarkan akurasi, presisi, recall, F1-score

### 5. **Model Terbaik**
Model dengan skor validasi tertinggi akan dipilih untuk prediksi akhir hasil pertandingan.

---

## 📈 Visualisasi  
Notebook ini menampilkan:
- Distribusi hasil pertandingan per bulan, jam, dan hari
- Boxplot dan histogram statistik pertandingan
- Heatmap korelasi antar fitur
- Pairplot kombinasi fitur numerik
- Bar chart perbandingan statistik berdasarkan hasil pertandingan

---
