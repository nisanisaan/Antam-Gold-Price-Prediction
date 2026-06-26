# Prediksi Harga Emas Antam

## Deskripsi Masalah
Proyek ini bertujuan untuk memprediksi harga emas menggunakan Machine Learning. Harga emas merupakan data *time-series* yang fluktuatif, sehingga diperlukan model yang mampu menangkap pola tren kenaikan harga dari waktu ke waktu.

## Sumber Dataset
Dataset diperoleh dari Kaggle (https://www.kaggle.com/datasets/garethharrison/antam-historical-gold-price/data) 
Data terdiri dari kolom `Time (ms)` dan `Gold Price`.

## Tahapan Preprocessing
1. Konversi format waktu (`Time (ms)` ke `datetime`).
2. Pembersihan data (menghapus kolom tidak relevan).
3. Pengurutan data secara kronologis.
4. *Feature Engineering*: Membuat kolom `hari_ke` sebagai input numerik agar dapat diproses oleh model regresi.
5. *Data Splitting*: Membagi data menjadi 80% data latih dan 20% data uji (dengan `shuffle=False` karena ini data *time-series*).

## Metode (Model yang Digunakan)
Kami membandingkan empat model untuk melihat performa terbaik:
1. **Regresi Linear**: Dasar untuk melihat tren linear.
2. **Regresi Polinomial (Degree 2)**: Menangkap pola non-linear.
3. **Random Forest Regressor**: Model berbasis ensemble untuk pola yang lebih kompleks.
4. **Decision Tree Regressor**: Model berbasis pohon untuk perbandingan dasar.

## Hasil Evaluasi (Skor R2)
*Skor R2 yang diperoleh:*
- Regresi Linear: -4.3369
- Regresi Polinomial: -0.5706
- Random Forest: -1.7303
- Decision Tree: -1.6841

## Analisis & Kesimpulan
[cite_start]Berdasarkan hasil visualisasi dan skor evaluasi, model berbasis pohon (*Random Forest* & *Decision Tree*) memiliki keterbatasan dalam melakukan ekstrapolasi tren kenaikan harga emas yang terus naik karena model ini hanya memprediksi berdasarkan nilai yang pernah dipelajari di data latih[cite: 381, 388]. [cite_start]Sebaliknya, model regresi polinomial lebih mampu merepresentasikan tren kenaikan harga jangka panjang, meskipun akurasi model tetap terbatas mengingat volatilitas harga emas yang dipengaruhi faktor eksternal[cite: 389, 390]. [cite_start]Proyek ini menunjukkan pentingnya pemilihan algoritma yang tepat untuk data *time-series*[cite: 390].

## Cara Menjalankan
1. Pastikan library `pandas`, `scikit-learn`, `joblib`, dan `matplotlib` terinstal.
2. Jalankan notebook `1_EDA_dan_Preprocessing.ipynb`.
3. Jalankan notebook `2_Pemodelan_dan_Evaluasi.ipynb` untuk melatih model dan melihat hasilnya.