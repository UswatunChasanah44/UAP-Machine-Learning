# Analisis Kinerja Model CNN dan MobileNet untuk Klasifikasi Citra Makanan Tradisional Nusantara 🥘🎉

## Overview Project 🌻
Project *klasifikasi makanan tradisional Indonesia* bertujuan untuk melestarikan kekayaan kuliner sebagai bagian dari warisan budaya, sekaligus mendukung digitalisasi dan pengembangan teknologi di bidang kuliner. Model ini membantu mendokumentasikan dan mengenali ragam makanan tradisional secara akurat, mempermudah akses informasi, serta mendukung promosi kuliner lokal dalam sektor pariwisata dan ekonomi, termasuk pemberdayaan UMKM. 

*Dataset* yang digunakan dalam penelitian ini diambil dari website Kaggle dengan data awal sebanyak 90.000 data. Berikut ini link datasetnya [Dataset Makanan Tradisional Indonesia](https://www.kaggle.com/datasets/theresalusiana/indonesian-food).

## Model yang Digunakan

Proyek ini menggunakan dua model klasifikasi gambar, yaitu:

1. **Convolutional Neural Network (CNN):**
   ![image](https://github.com/user-attachments/assets/47a74a46-3276-4654-83cf-8d01a579e236)
   CNN adalah model jaringan saraf yang dirancang khusus untuk pemrosesan data berbentuk gambar. CNN digunakan untuk mengekstraksi fitur penting dari gambar makanan tradisional Nusantara, seperti tekstur, warna, dan pola, sehingga model dapat mengenali dan membedakan kategori makanan secara akurat.

2. **MobileNet**
   
   ![image](https://github.com/user-attachments/assets/dab24000-35eb-469e-8849-eb063d9b50f7)
   Dalam konteks klasifikasi makanan tradisional, MobileNet dapat digunakan untuk mengekstraksi fitur penting dari gambar makanan dengan cepat dan efektif. Arsitektur ini dirancang untuk berjalan lebih cepat dan menggunakan lebih sedikit sumber daya (seperti memori dan daya komputasi), sehingga cocok untuk aplikasi pada perangkat bergerak atau sistem dengan kemampuan terbatas.

## Overview Dataset 🌻
Dataset yang digunakan dalam klasifikasi terdiri dari 9.098 image dan telah terbagi ke dalam file train, validation, dan test. Terdapat 5 label yaitu '_Bakso_','_Gudeg_', '_Rendang_', '_Gado-Gado_',dan '_Sate_'.

## Pre Processing & Modelling 
**A. CNN MODEL** 📌

**Preprocessing**
1. ImageDataGenerator
   
Berfungsi untuk menghasilkan batch gambar dengan preprocessing (normalisasi atau augmentasi) yang diterapkan secara langsung ke gambar selama pelatihan.

2. Rescale

Membagi setiap nilai piksel dengan 255, sehingga nilai piksel yang awalnya berada di rentang [0, 255] menjadi [0, 1]. Rescale penting karena model deep learning bekerja lebih baik dengan data yang ternormalisasi, mengurangi sensitivitas terhadap nilai besar.

**Augmentasi** 

- rotation_range=30      : Rotasi gambar secara acak dalam rentang 0 hingga 30 derajat.

- width_shift_range=0.2 dan height_shift_range=0.2: Perpindahan gambar secara horizontal atau vertikal sebesar 20% dari dimensi gambar.

- shear_range=0.2         : Transformasi shear pada gambar sebesar 20%.
Berguna untuk menambah variasi pada dataset.

- zoom_range=0.2            :Zoom in atau zoom out gambar hingga 20%.
Membantu model menangani objek dengan ukuran berbeda.

- horizontal_flip=True      : Membalik gambar secara horizontal.
Cocok untuk dataset di mana orientasi horizontal objek dapat bervariasi (misalnya, wajah menghadap kiri/kanan).

- fill_mode='nearest'         : Mengisi area kosong akibat transformasi (rotasi, shift) dengan nilai piksel terdekat.

 **Modelling**
 
 Hasil dari modelling CNN adalah sebagai berikut :
 
 ![image](https://github.com/user-attachments/assets/b357cc69-266f-42f9-a0a4-7468b97a3254)


**Model Evaluation**

Berikut adalah plot akurasi dan loss dengan jumlah 50 Epoch : 

![image](https://github.com/user-attachments/assets/4dc1baec-29c1-4cc8-a22a-bad7c95c9f3d)


Akurasi pelatihan meningkat secara konsisten dari sekitar 50% hingga mendekati 90% seiring bertambahnya epoch, menunjukkan bahwa model berhasil belajar dari data pelatihan, sementara akurasi validasi, meskipun fluktuatif, secara umum meningkat dari sekitar 70% hingga mendekati 89% dan tetap mengikuti tren akurasi pelatihan, tanpa tanda overfitting yang signifikan karena kedua garis akurasi berada dalam kisaran yang hampir sama sepanjang proses pelatihan.


![image](https://github.com/user-attachments/assets/99a95c17-2847-44d4-bc33-283b17f7429e)


Berdasarkan confusion matrik tersebut, terlihat bahwa sebanyak 62 kelas Gado diprediksi sebagai sate dan hanya 3 prediksi benar dari kelas gudeg yang diprediksi sebagai gudeg.

![image](https://github.com/user-attachments/assets/7e42b5f8-0e6c-4208-b5fb-c5f573aa2938)


Model memiliki akurasi keseluruhan sebesar 23%, dengan performa terbaik pada kelas **rendang** (precision, recall, dan f1-score sekitar 0.24-0.25) dan performa terburuk pada kelas **gudeg** (precision 0.08, recall 0.06, dan f1-score 0.07), menunjukkan kesulitan model dalam mengenali kelas minoritas. Rata-rata makro (0.20) dan rata-rata berbobot (0.22-0.23) mencerminkan performa buruk secara keseluruhan, terutama karena ketidakseimbangan data dan fitur model yang belum optimal. 

Source code dapat diakses di [CNN COLLAB](https://colab.research.google.com/drive/1RHOmJ603qH9bf3ur2-PoFTECrGSSrDYh?usp=sharing)


**B. MobileNet Model** 📌

**Preprocessing**

1. rescale=1./255:
   
Ini adalah langkah preprocessing untuk menormalkan nilai piksel gambar dari rentang [0, 255] menjadi [0, 1]. Hal ini membantu model konvergen lebih cepat selama pelatihan.

2. target_size=(224, 224):
   
Mengubah ukuran gambar menjadi resolusi tertentu (224x224) agar sesuai dengan input yang diharapkan oleh arsitektur MobileNet.

3. class_mode='categorical':
   
Menentukan format label sebagai kategori (one-hot encoding) agar sesuai dengan output model yang bekerja untuk klasifikasi multi-kelas.

**Augmentasi**

1. rotation_range=20:
Memutar gambar secara acak hingga 20 derajat.

2. width_shift_range=0.2:
Menggeser gambar secara horizontal hingga 20% dari lebar gambar.

4. height_shift_range=0.2:
Menggeser gambar secara vertikal hingga 20% dari tinggi gambar.

**Modelling**

 Hasil dari modelling MobileNet adalah sebagai berikut :

 ![image](https://github.com/user-attachments/assets/5c5fb7a6-4226-47c2-98a8-f1af1eb5fec9)


Berikut plot akurasi dan loss : 

![image](https://github.com/user-attachments/assets/b7b77cf9-0def-4be7-b967-80dc35ccf4e2)


Dari grafik ini, terlihat bahwa loss training menurun secara konsisten, sementara loss validasi lebih fluktuatif, menunjukkan kemungkinan overfitting, di mana model terlalu terfokus pada data training. Hal ini juga didukung oleh grafik akurasi, di mana akurasi training terus meningkat mendekati 100%, sedangkan akurasi validasi lebih bervariasi meskipun cenderung meningkat secara keseluruhan. Fluktuasi pada data validasi mencerminkan bahwa model mungkin kurang stabil dalam memgeneralisasi pola pada data yang belum pernah dilihat.


![image](https://github.com/user-attachments/assets/4d62ef48-c91e-42c9-9c9f-4113ffa3697f)


Confusion matrix ini menunjukkan performa model klasifikasi dalam mengklasifikasikan 5 kelas makanan tradisional Indonesia: bakso, gado, gudeg, rendang, dan sate. Dari matriks, terlihat bahwa model memiliki performa tinggi pada kelas bakso, rendang, dan sate dengan prediksi yang sangat akurat (213, 212, dan 211 benar prediksi). Namun, model menunjukkan kesulitan dalam mengklasifikasikan kelas gudeg, hanya menghasilkan 46 prediksi benar dan beberapa kesalahan klasifikasi ke kelas gado dan rendang. Kesalahan lain tampak minimal, menunjukkan bahwa model bekerja cukup baik secara keseluruhan, tetapi perlu perbaikan pada kelas gudeg untuk meningkatkan kinerja.


![image](https://github.com/user-attachments/assets/a6d43cfd-0080-41e0-9aa5-5f5f5be50ae2)

Hasil evaluasi model menunjukkan performa yang sangat baik dengan **akurasi keseluruhan sebesar 97%** pada 913 data uji. Setiap kelas memiliki nilai **precision**, **recall**, dan **f1-score** yang konsisten tinggi, berkisar antara 0.94 hingga 1.00. 

- **Bakso** memiliki recall tertinggi (1.00), menunjukkan semua data bakso terdeteksi dengan benar.  
- **Gudeg** memiliki jumlah data terkecil (47) tetapi tetap menunjukkan performa baik dengan f1-score 0.96.  
- Kelas **gado-gado** sedikit kurang optimal dengan recall 0.94.  
- Rata-rata makro dan berbobot menunjukkan bahwa model seimbang dalam menangani data, tanpa bias terhadap kelas tertentu.

Secara keseluruhan, model ini sangat andal untuk klasifikasi makanan tradisional.

Link Collab dapat diakses di [MobileNet Collab](https://colab.research.google.com/drive/1dY7v2-vXL54LdlhmzbCIz8si30xKHfrU?usp=sharing) 


**Link model CNN dan MobileNet dapat dilihat disini** 👉 [Model h5](https://drive.google.com/drive/folders/112A0kvZ0j0RmSm08IwHgTVgzbI2Wam8j?usp=sharing)

## Tampilan Web Klasifikasi 🌻

![image](https://github.com/user-attachments/assets/188e2324-341c-41ec-8335-11273bbbf41e)


![image](https://github.com/user-attachments/assets/e2362f48-ac41-409e-9c04-753ea932081b)


## Author 🧑‍💻
**Uswatun Chasanah**

**202110370311274**
















 



