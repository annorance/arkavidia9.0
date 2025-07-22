# Commodity Price Prediction, Penyisihan Datavidia 9
## Overview
Seiring dengan meningkatnya volatilitas pasar pangan global, memprediksi harga komoditas pangan dengan akurat menjadi tantangan penting bagi pembuat kebijakan, pelaku bisnis, dan peneliti. Kompetisi Prediksi Harga Komoditas Pangan ini memberikan kesempatan bagi peserta untuk menganalisis faktor-faktor yang mempengaruhi fluktuasi harga bahan pangan. Dataset yang digunakan mencakup tren harga historis, kondisi pasar, dan indikator ekonomi yang berperan dalam perubahan harga pangan di berbagai wilayah. Dengan menerapkan teknik data science, peserta dapat menggali wawasan mendalam tentang dinamika pasar yang mendasari pergerakan harga.
## Permasalahan
Fluktuasi harga komoditas pangan memiliki dampak ekonomi dan sosial yang signifikan, mulai dari anggaran rumah tangga hingga kebijakan perdagangan global. Dalam kompetisi ini, peserta ditantang untuk mengembangkan model prediktif yang dapat memperkirakan harga komoditas pangan berdasarkan data historis. Dataset yang diberikan mencakup berbagai fitur seperti harga sebelumnya, nilai tukar mata uang, tren pasokan global, serta indikator makroekonomi. Dengan menggunakan data tersebut, peserta diharapkan dapat membangun model yang mampu memprediksi harga setiap komoditas tiap tanggal pada rentang waktu tertentu dengan tingkat akurasi yang tinggi.
## Tujuan
Tujuan dari kompetisi ini adalah mendorong para data scientist untuk mengasah keterampilan mereka dalam membangun model prediksi yang akurat. Dengan berpartisipasi, peserta turut berkontribusi dalam pemahaman yang lebih mendalam mengenai pergerakan harga pangan dan dampaknya terhadap ketahanan pangan serta stabilitas ekonomi. Selain meningkatkan kemampuan teknis, kompetisi ini juga berfokus pada pentingnya pengambilan keputusan berbasis data dalam mengelola rantai pasokan pangan dan mengurangi risiko volatilitas harga.

---

## Evaluation
### Mean Absolute Percentage Error (MAPE)
Submisi dinilai berdasarkan Mean Absolute Percentage Error (Persentase Kesalahan Absolut Rata-rata). MAPE pada scikit-learn library didefinisikan sebagai:
![image](https://github.com/user-attachments/assets/62462714-0345-4022-b227-62dbbc2a18dd)
dalam hal ini, yi adalah nilai aktual (ground truth) dan yhati adalah nilai prediksi untuk setiap i
```
import numpy as np

def mape(y_true: np.ndarray, y_pred: np.ndarray) -> float:
    """
    Calculate the Mean Absolute Percentage Error (MAPE).

    Parameters:
    y_true (array-like): True values.
    y_pred (array-like): Predicted values.

    Returns:
    float: The calculated MAPE.
    """
    return np.mean(np.abs((y_true - y_pred) / y_true))

```

atau secara simpel menggunakan scikit-learn library

```
from sklearn.metrics import mean_absolute_percentage_error
mape = mean_absolute_percentage_error(y_true, y_pred)
```
### Mengapa MAPE?
MAPE dipilih karena menyediakan metrik kesalahan berbasis persentase yang intuitif sehingga sangat efektif untuk kompetisi ini, saat prediksi harga komoditas yang akurat sangat penting. Mengingat hubungan ekonomi dan pasar sebagai faktor dari fluktuasi harga komoditas, diharapkan peserta mengembangkan model yang secara konsisten menghasilkan persentase kesalahan yang lebih kecil.

---

## Hasil & Pembahasan 
Jenis analisis deret waktu yang dilakukan adalah analisis multivariate, yakni analisis menggunakan beberapa atribut sebagai prediktor untuk melakukan peramalan pada data deret waktu. Dari data-data yang disediakan, kami memilih untuk menggunakan harga keenam komoditas global (global commodity price) dan nilai tukar Rupiah ke US Dollar. Data harga komoditas global memiliki kolom price yang menunjukkan harga pasar pada akhir perdagangan, open yang menunjukkan harga pembukaan pasar saat mulai beroperasi, high yang menunjukkan harga tertinggi yang dicapai oleh suatu komoditas pada hari tersebut, low yang menunjukkan harga terendah yang dicapai oleh suatu komoditas pada hari tersebut, vol. yang menunjukkan jumlah kontrak suatu komoditas yang diperdagangkan pada hari itu, dan change % yang menunjukkan persentase perubahan harga (closing price) dibandingkan dengan harga penutupan hari sebelumnya. Kami memutuskan untuk hanya menggunakan nilai tukar Rupiah Indonesia ke US Dollar karena setelah melakukan eksplorasi menggunakan heatmap untuk mengetahui korelasi pearson dari harga komoditas bahan pangan dengan konversi mata uang, didapati bahwa hanya variabel konversi Rupiah Indonesia ke US Dollar lah yang memengaruhi harga komoditas bahan pangan, yakni beras medium, beras premium, dan gula konsumsi. Kolom yang terdapat pada dataset mata uang adalah open yang menunjukkan harga pertama pada hari tersebut, high yang menunjukkan harga tertinggi yang dicapai pada hari tersebut, low yang menunjukkan harga terendah yang dicapai pada hari tersebut, close yang menunjukkan harga terakhir  sebelum pasar ditutup, adj close yakni harga penutupan yang disesuaikan dan bernilai sama dengan close pada mata uang, dan volume yang menunjukkan jumlah unit yang diperdagangkan pada hari tersebut. Kami hanya memilih kolom close karena merupakan representasi yang paling akurat untuk mewakili kurs mata uang pada hari tersebut. Kami memutuskan untuk tidak menggunakan dataset Google Trend karena banyaknya data yang hilang (missing value) dan sulitnya mencari data kovariat lampau maupun kovariat masa depan dari data di internet. 

Hyperparameter n_estimators dalam Random Forest Regressor menentukan jumlah pohon keputusan (decision trees) yang akan digunakan. Berdasarkan eksperimen hyperparameter tuning yang dilakukan dengan pilihan nilai n_estimator = 50, 100, 200, diperoleh nilai n_estimator yang memberikan hasil prediksi paling baik adalah n_estimator = 100 dengan indikator nilai MAPE yang menunjukkan angka paling minimum untuk nilai n_estimator tersebut. MAPE yang diperoleh untuk gula pasir di daerah Aceh adalah sebesar 0.063. 

---

## Competition Link
https://www.kaggle.com/competitions/comodity-price-prediction-penyisihan-arkavidia-9

## Citation
Datavidia. Commodity Price Prediction, Penyisihan Datavidia 9. https://kaggle.com/competitions/comodity-price-prediction-penyisihan-arkavidia-9, 2025. Kaggle.
