# Laporan Proyek Machine Learning - Nazrul Effendy

> ## Domain Proyek

Penyakit Parkinson merupakan penyakit gangguan otak yang menyebabkan gerakan yang tidak diinginkan atau tidak terkendali, seperti gemetar, kaku, dan kesulitan menjaga keseimbangan dan koordinasi. Gejala ini biasanya muncul secara bertahap dan memburuk seiring waktu. Seiring perkembangan penyakit, penderita dapat mengalami kesulitan berjalan dan berbicara. Mereka juga mungkin mengalami perubahan mental dan perilaku, masalah tidur, depresi, kesulitan mengingat, dan kelelahan. Deteksi penyakit ini secara dini diperlukan sehingga pasien dapat diterapi sedini mungkin. [Parkinson’s Disease: Causes, Symptoms, and Treatments](https://www.nia.nih.gov/health/parkinsons-disease/parkinsons-disease-causes-symptoms-and-treatments);[Fan dkk, 2024](https://www.sciencedirect.com/science/article/pii/S1353802024011945); [Jeong dkk, 2024](https://www.sciencedirect.com/science/article/pii/S0010482524011636);[Dennis and Strafella, 2024](https://www.sciencedirect.com/science/article/pii/S1353802024009982)

> ## Business Understanding

### Problem Statements
Permasalahan pada proyek ini adalah bagaimana merancang sistem deteksi penyakit Parkinson secara dini.

### Goals
Berdasarkan pernyataan permasalahan di atas, pada proyek ini akan dirancang sistem deteksi penyakit Parkinson secara dini menggunakan machine learning.

### Solution statements
Pada proyek ini dirancang model machine learning menggunakan linear regression, K-Nearest Neighbor dan Deep Learning.
Metrik evaluasi ketiga model machine learning akan dibandingkan.

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

Informasi mengenai jumlah data dan tipe data yang terdapat pada dataset ini ditampilkan pada gambar berikut:
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/df-info.JPG?raw=true"/>
</p>

Gambar tersebut menunjukkan bahwa tidak ada data hilang di dataset yang digunakan. Sedangkan pairplot masing-masing variabel ditampilkan pada gambar berikut:
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/pairplot.png?raw=true"/>
</p>

Hasil cross correlation masing-masing variabel ditampilkan pada gambar berikut:
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/corr.png?raw=true"/>
</p>

> ## Data Preparation
Teknik data preparation yang dilakukan:
1. Variabel status diedit sehingga jika nilainya lebih besar dari 0,7 diubah menjadi 1. Jika kurang atau sama dengan 0,7 diubah menjadi 0.
2. Menghitung jumlah data hilang. Jumlah data hilang ini perlu diketahui untuk kemudian dapat dilakukan preparation tertentu pada data tersebut, misalkan menghapus baris data tersebut.
3. Dropping kolom pertama dari dataset yang bernama "name"
4. Variabel input machine learning distandarisasi


Informasi data hilang (***missing value***) yang terdapat pada dataset ini ditampilkan pada gambar berikut.
<p align="center">
  <img src="https://github.com/nazrul74/Parkinson-s-Disease/blob/main/img/df-isnull.JPG?raw=true"/>
</p>

> ## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

> ## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.



