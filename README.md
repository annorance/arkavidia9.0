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

## Leaderboard
Peringkat dalam kompetisi ini akan didasarkan pada Mean Absolute Persentage Error (MAPE), di mana skor yang lebih rendah akan mendapatkan peringkat lebih tinggi. Leaderboard akan terdiri dari dua fase:

**Public Leaderboard**
Dihitung berdasarkan sebagian dari data uji (30%) dan akan terlihat sepanjang kompetisi. Ini memberikan gambaran sementara tentang performa model peserta selama kompetisi berlangsung.

**Private Leaderboard**
Dihitung berdasarkan sisa data uji (70%) dan akan digunakan untuk menentukan peringkat akhir di akhir kompetisi.

**Pembobotan**
Peringkat akhir akan ditentukan berdasarkan Private Leaderboard dengan bobot sebagai berikut: Final Submission Score = 100% Private

---

## Submission
Untuk setiap ID dalam test set, peserta harus memprediksi untuk variabel price. File .csv dikirim dengan menyertakan header dan memiliki format sebagai berikut yang dapat dilihat pada Harga Bahan Pangan/sample_submission.csv
```
id,price
Bawang Merah/Aceh/2024-10-01,0
Bawang Merah/Aceh/2024-10-02,0
Bawang Merah/Aceh/2024-10-03,0
Bawang Merah/Aceh/2024-10-04,0
Bawang Merah/Aceh/2024-10-05,0
etc.
```

---

## Competition Link
https://www.kaggle.com/competitions/comodity-price-prediction-penyisihan-arkavidia-9

## Citation
Datavidia. Commodity Price Prediction, Penyisihan Datavidia 9. https://kaggle.com/competitions/comodity-price-prediction-penyisihan-arkavidia-9, 2025. Kaggle.
