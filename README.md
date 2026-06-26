# Antam Gold Price Prediction

## Anggota Kelompok
1. **Nisa** (103132400044)
2. **Gendis Pambayun** (103132400031)
3. **Nanda Mayla Adiasti** (103132400003)

## Deskripsi Masalah
Proyek ini bertujuan untuk memprediksi harga emas menggunakan *Machine Learning*. Harga emas merupakan data *time-series* yang fluktuatif, sehingga diperlukan model yang mampu menangkap pola tren kenaikan harga dari waktu ke waktu untuk membantu analisis pergerakan harga di masa depan.

## Sumber Dataset
Dataset diperoleh dari Kaggle: [Antam Historical Gold Price](https://www.kaggle.com/datasets/garethharrison/antam-historical-gold-price/data). Data terdiri dari kolom `Time (ms)`, `Gold Price` dan `Date`

## Tahapan Preprocessing
1. **Konversi Waktu**: Mengubah format `Time (ms)` menjadi format *datetime*.
2. **Pembersihan Data**: Menghapus kolom yang tidak relevan serta memfilter data sehingga hanya mencakup periode 2020–2025.
3. **Pengurutan**: Mengurutkan data secara kronologis berdasarkan waktu.
4. **Feature Engineering**: Membuat kolom `hari_ke` sebagai input numerik untuk model regresi.
5. **Data Splitting**: Membagi data menjadi 80% data latih dan 20% data uji (*shuffle=False*).

## Metode (Model yang Digunakan)
Kami membandingkan empat model untuk menentukan performa terbaik:
1. **Regresi Linear**: Dasar untuk melihat tren linear.
2. **Regresi Polinomial (Degree 2)**: Menangkap pola non-linear.
3. **Random Forest Regressor**: Model *ensemble* untuk pola yang kompleks.
4. **Decision Tree Regressor**: Model berbasis pohon untuk perbandingan dasar.

## Hasil Evaluasi
Berikut adalah perbandingan metrik performa keempat model:

| Model | MAE | RMSE | R² |
| :--- | :--- | :--- | :--- |
| **Regresi Linear** | 558,310.35 | 604,648.00 | -4.3369 |
| **Regresi Polinomial** | 286,138.87 | 328,010.13 | -0.5706 |
| **Random Forest** | 347,966.86 | 432,477.26 | -1.7303 |
| **Decision Tree** | 344,339.67 | 428,800.58 | -1.6841 |

*Berdasarkan hasil di atas, **Regresi Polinomial** menjadi model terbaik karena memiliki kesalahan (MAE/RMSE) paling rendah.*

## Analisis & Kesimpulan
Berdasarkan visualisasi dan skor evaluasi, model berbasis pohon (*Random Forest* & *Decision Tree*) memiliki keterbatasan dalam melakukan ekstrapolasi tren kenaikan harga emas yang terus naik karena model ini hanya memprediksi berdasarkan nilai yang pernah dipelajari di data latih. Sebaliknya, model regresi polinomial lebih mampu merepresentasikan tren kenaikan harga jangka panjang, meskipun akurasi model tetap terbatas mengingat volatilitas harga emas yang dipengaruhi faktor eksternal. Proyek ini menunjukkan pentingnya pemilihan algoritma yang tepat untuk data *time-series*.

## Cara Menjalankan
1. Pastikan library `pandas`, `scikit-learn`, `joblib`, dan `matplotlib` terinstal.
2. Jalankan notebook `1_EDA_dan_Preprocessing.ipynb`.
3. Jalankan notebook `2_Pemodelan_dan_Evaluasi.ipynb` untuk melatih model dan melihat hasilnya.

---
*Proyek ini diselesaikan sebagai Tugas Besar Mata Kuliah Machine Learning.*
