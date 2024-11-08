# Laporan Proyek Machine Learning - Nazrul Effendy

> ## Domain Proyek

Penyakit Parkinson merupakan penyakit gangguan otak yang menyebabkan gerakan yang tidak diinginkan atau tidak terkendali, seperti gemetar, kaku, dan kesulitan menjaga keseimbangan dan koordinasi. Gejala ini biasanya muncul secara bertahap dan memburuk seiring waktu. Seiring perkembangan penyakit, penderita dapat mengalami kesulitan berjalan dan berbicara. Mereka juga mungkin mengalami perubahan mental dan perilaku, masalah tidur, depresi, kesulitan mengingat, dan kelelahan. Deteksi penyakit ini secara dini diperlukan sehingga pasien dapat diterapi sedini mungkin. [Parkinson’s Disease: Causes, Symptoms, and Treatments](https://www.nia.nih.gov/health/parkinsons-disease/parkinsons-disease-causes-symptoms-and-treatments);[Fan dkk, 2024](https://www.sciencedirect.com/science/article/pii/S1353802024011945); [Jeong dkk, 2024](https://www.sciencedirect.com/science/article/pii/S0010482524011636);[Dennis and Strafella, 2024](https://www.sciencedirect.com/science/article/pii/S1353802024009982)

> ## Business Understanding

### Problem Statements
Permasalahan pada proyek ini adalah bagaimana merancang sistem prediksi penyakit Parkinson secara dini.

### Goals
Berdasarkan pernyataan permasalahan di atas, pada proyek ini akan dirancang sistem prediksi penyakit Parkinson secara dini menggunakan machine learning.

### Solution statements
Pada proyek ini dirancang model machine learning menggunakan logistic regression, K-Nearest Neighbor dan Deep Learning.
Akurasi ketiga model machine learning akan dibandingkan.

> ## Data Understanding
Dataset yang digunakan berasal dari kaggle di link [Parkinson's Disease](https://www.kaggle.com/datasets/shreyadutta1116/parkinsons-disease/data).

Berikut penjelasan mengenai variabel-variabel pada kolom dataset:
| Variabel | Deskripsi |
| --- | --- |
| name | Unique identifier for each patient |
| MDVP:Fo(Hz) | Average vocal fundamental frequency. |
| MDVP:Fhi(Hz) | Maximum vocal fundamental frequency. |
| MDVP:Flo(Hz) | Minimum vocal fundamental frequency. |
| MDVP:Jitter(%) | Various measures of variations in frequency (jitter) - % |
| MDVP:Jitter(Abs) | Various measures of variations in frequency (jitter) - abs |
| MDVP:RAP | MDVP - RAP |
| MDVP:PPQ | MDVP - PPQ |
| Jitter:DDP | Various measures of variations in frequency (jitter) - DDP |
| MDVP:Shimmer | Various measures of amplitude variation (shimmer) |
| MDVP:Shimmer(dB) | Various measures of amplitude variation (shimmer) - dB |
| Shimmer:APQ3 | Various measures of amplitude variation (shimmer) - APQ3 |
| Shimmer:APQ5 | Various measures of amplitude variation (shimmer) - APQ5 |
| MDVP:APQ | MDVP - APQ |
| Shimmer:DDA | Various measures of amplitude variation (shimmer) - DDA |
| NHR | (Noise-to-Harmonics Ratio): Measures the proportion of noise to tonal components in the voice |
| HNR |  (Harmonics-to-Noise Ratio): Quantifies the ratio of harmonic sound to noise in the voice |
| Status | Indicates whether the individual is diagnosed with Parkinson’s disease (1 for positive, 0 for negative). |
| RPDE | (Recurrence Period Density Entropy): A nonlinear dynamical analysis of voice |
| DFA | (Detrended Fluctuation Analysis): Measures the long-term signal correlation in the voice |
| spread1 | Measures of variation in voice frequency 1 |
| spread2 | Measures of variation in voice frequency 2 |
| D2 | Another nonlinear dynamical measure |
| PPE | (Pitch Period Entropy): Measures the regularity of the pitch period |

Variabel-variabel tersebut secara umum merupakan:
- ID dan status pasien (terdiagnosis atau tidak). 
- Fitur akustik seperti MDVP, jitter, shimmer, dan rasio noise.
- Metrik analisis suara dinamis nonlinier seperti RPDE dan DFA.

Informasi mengenai jumlah data dan tipe data yang terdapat pada dataset ini ditampilkan pada gambar berikut. Dari coding yang dijalankan, diperoleh bahwa **dataset** yang digunakan **terdiri dari 1195 baris** dan 24 kolom.
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/df-info.JPG?raw=true"/>
</p>

Menggunakan coding 'describe' diperoleh nilai statistik dari dataset tersebut, antara lain berupa jumlah data, rerata, standard deviasi, nilai minimal, 25%, 50%, 75% dan nilai maksimum masing-masing variabel. Gambar berikut memperlihatkan tampilan sebagian dari hasil coding tersebut.
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/df-describe.JPG?raw=true"/>
</p>

Sedangkan pairplot masing-masing variabel ditampilkan pada gambar berikut:
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/pairplot.png?raw=true"/>
</p>

Hasil cross correlation masing-masing variabel ditampilkan pada gambar berikut:
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/corr.png?raw=true"/>
</p>



> ## Data Preparation
Teknik data preparation yang dilakukan:
1. Dropping kolom pertama dari dataset yang bernama "name". Variabel name ini dianggap tidak diperlukan sebagai variabel input untuk memprediksi status penyakit Parkinson tersebut.
2. Variabel 'status" diedit sehingga jika nilainya lebih besar dari 0,7 diubah menjadi 1. Jika kurang atau sama dengan 0,7 diubah menjadi 0. Konversi angka ini untuk memastikan mana yang terindikasi memiliki penyakit Parkinson, dan mana yang tidak.
3. Menghitung jumlah data hilang. Jumlah data hilang ini perlu diketahui untuk kemudian dapat dilakukan preparation tertentu pada data tersebut, misalkan menghapus baris data tersebut.
4. Membuat data variabel input yang merupakan data asli dikurangin variabel 'status', sedangkan variabel 'status' menjadi variabel output. Hal ini dilakukan untuk memastikan mana variabel yang akan menjadi input maupun output baik untuk pelatihan maupun untuk evaluasi model machine learning.
5. Variabel input machine learning distandarisasi. Standarisasi ini dilakukan agar nilai maksimum dan minimum dari variabel-variabel yang digunakan tidak terlalu beda besarnya. 


Informasi data hilang (***missing value***) yang terdapat pada dataset ini ditampilkan pada gambar berikut. 
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/df-isnull.JPG?raw=true"/>
</p>

Gambar tersebut menunjukkan bahwa tidak ada data hilang di dataset yang digunakan. 

> ## Modeling
Pada proyek ini digunakan tiga jenis machine learning, yaitu logistic regression, K-Nearest Neighbor dan Deep Learning.

- Pemisahan data training dan data pengujian:

```
X_train,X_test,y_train,y_test = train_test_split(X_scalled,y,test_size=0.3,random_state=1)
```

- Model prediksi dengan algoritma logistic regression:

```
from sklearn.linear_model import LogisticRegression
lr = LogisticRegression(penalty = 'l2')
lr.fit(X_train,y_train)
y_pred = lr.predict(X_test)
```

- Model prediksi dengan algoritma KNN:

```
from sklearn.neighbors import KNeighborsClassifier
model2 = KNeighborsClassifier(n_neighbors=3)
model2.fit(X_train,y_train)
y_pred = model2.predict(X_test)
```

- Model prediksi dengan algoritma Deep Learning:

```
import tensorflow
from tensorflow import keras
from keras.models import Sequential
from keras.layers import Dense,Dropout
from keras.callbacks import EarlyStopping

model3 = Sequential()
model3.add(Dense(128,activation = 'relu',input_dim =(22) ))
model3.add(Dropout(0.2))
model3.add(Dense(64,activation='relu'))
model3.add(Dropout(0.2))
model3.add(Dense(1,activation='sigmoid'))
model3.summary()

model3.compile(loss='binary_crossentropy',optimizer='adam',metrics=['accuracy'])
early_stopping = EarlyStopping(monitor='val_loss',
                               patience=5,
                               restore_best_weights=True)
history = model3.fit(X_train,y_train,validation_data=(X_test,y_test),batch_size=32,epochs=100,verbose=True,callbacks=[early_stopping])
y_pred = model3.predict(X_test)
```

> ## Evaluation
Pada proyek ini, digunakan nilai akurasi untuk membandingkan unjuk kerja ketiga model machine learning yang digunakan. Pada proyek ini, ditampilkan juga nilai loss training maupun validasi dari model deep learning seperti pada gambar berikut. Gambar tersebut memperlihatkan bahwa training model deep learning telah berjalan dengan baik.

<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/loss-dl.png?raw=true"/>
</p>

Dari hasil experiment pada proyek ini, diperoleh bahwa deep learning berhasil mencapat nilai akurasi tertinggi yaitu sebesar 93,59%, diikuti oleh KNN dan logistic regression, masing-masing sebesar 92,20% dan 91,36% seperti yang ditunjukkan pada tabel berikut.

| No | Model | Akurasi (%) |
| --- | --- | --- |
| 1 | logistic regression | 91,36 |
| 2 | KNN | 92,20 |
| 3 | deep learning | 93,59 |


