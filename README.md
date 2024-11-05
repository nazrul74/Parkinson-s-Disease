# Parkinson-s-Disease
# Laporan Proyek Machine Learning - Nazrul Effendy

## Domain Proyek - Parkinson's Disease

{Pada bagian ini, kamu perlu menuliskan latar belakang yang relevan dengan proyek yang diangkat.}
Penyakit Parkinson merupakan penyakit gangguan otak yang menyebabkan gerakan yang tidak diinginkan atau tidak terkendali, seperti gemetar, kaku, dan kesulitan menjaga keseimbangan dan koordinasi. Gejala ini biasanya muncul secara bertahap dan memburuk seiring waktu. Seiring perkembangan penyakit, penderita dapat mengalami kesulitan berjalan dan berbicara. Mereka juga mungkin mengalami perubahan mental dan perilaku, masalah tidur, depresi, kesulitan mengingat, dan kelelahan. Deteksi penyakit ini secara dini diperlukan sehingga pasien dapat diterapi sedini mungkin. [Parkinson’s Disease: Causes, Symptoms, and Treatments](https://www.nia.nih.gov/health/parkinsons-disease/parkinsons-disease-causes-symptoms-and-treatments) 

## Business Understanding

### Problem Statements
- Bagaimana merancang sistem deteksi penyakit Parkinson secara dini ?

### Goals
- Merancang sistem deteksi penyakit Parkinson secara dini

### Solution statements
    - Pada proyek ini dirancang model machine learning dengan ANN yg memiliki lapisan tersembunyi lebih sedikit dan deep learning dengan optimizer.
    - Metrik evaluasi kedua model machine learning akan dibandingkan.

## Data Understanding
Dataset yang digunakan: [Parkinson's Disease](https://www.kaggle.com/datasets/shreyadutta1116/parkinsons-disease/data).

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

Berikut informasi mengenai jumlah data ,tipe data dan informasi data hilang (***missing value***) yang terdapat pada dataset ini:
<p align="center">
  <img src="https://github.com/adiputrasinaga-cmd/Predictive-Analytics/blob/main/img/collegeGPA-rev.png?raw=true"/>
</p>

**Rubrik/Kriteria Tambahan (Opsional)**:
Untuk memahami data, dilakukan exploratory data analysis, antara lain:
- Membaca file dataset
- Menampilkan 5 baris pertama dari dataset

## Data Preparation
Teknik data preparation yang dilakukan:
1. Dropping kolom pertama dari dataset yang bernama "name"
2. Menghitung nilai cross-correlasi
3. 
4. 
5. . Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

