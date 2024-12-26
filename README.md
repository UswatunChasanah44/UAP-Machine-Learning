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


**Gambar pertama menunjukkan grafik "Loss Over Epochs**," di mana loss pada data training (garis biru) menurun secara konsisten, dan loss pada data validasi (garis oranye) juga menurun, meskipun sedikit fluktuatif, menunjukkan model semakin baik dalam meminimalkan kesalahan. **Gambar kedua adalah grafik "Accuracy Over Epochs,"** di mana akurasi training (garis biru) dan validasi (garis oranye) meningkat seiring bertambahnya epoch, hingga mencapai nilai yang stabil mendekati 90%. Hasil ini menunjukkan bahwa model memiliki performa yang baik tanpa indikasi overfitting yang signifikan.


![image](https://github.com/user-attachments/assets/99a95c17-2847-44d4-bc33-283b17f7429e)


Dari matriks, terlihat bahwa model memiliki performa tinggi pada kelas rendang, bakso, sate, dan gado dengan prediksi yang sangat akurat (207, 200, 200 dan 201 benar prediksi). Namun, model menunjukkan kesulitan dalam mengklasifikasikan kelas gudeg, hanya menghasilkan 22 prediksi benar dan beberapa kesalahan klasifikasi ke kelas gado dan rendang. 

![image](https://github.com/user-attachments/assets/7e42b5f8-0e6c-4208-b5fb-c5f573aa2938)


Model memiliki akurasi keseluruhan sebesar 91%, dengan performa terbaik pada kelas **rendang** (precision, recall, dan f1-score sekitar 0.90-0.93) dan performa terburuk pada kelas **gudeg** (precision 0.96, recall 0.47, dan f1-score 0.63), menunjukkan kesulitan model dalam mengenali kelas minoritas.

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


Grafik pertama menunjukkan "Loss Over Epochs," di mana loss pada data training (garis biru) tetap rendah dan stabil setelah beberapa epoch, sedangkan loss pada data validasi (garis oranye) lebih fluktuatif meskipun berada pada tingkat rendah. Grafik kedua menggambarkan "Accuracy Over Epochs," di mana akurasi training (garis biru) dengan cepat mencapai nilai tinggi mendekati 100% dan stabil, sedangkan akurasi validasi (garis oranye) fluktuatif tetapi secara keseluruhan tinggi dan konsisten. Performa ini menunjukkan bahwa model bekerja dengan baik pada data training dan validasi tanpa tanda-tanda overfitting yang jelas, meskipun fluktuasi pada data validasi dapat mengindikasikan ketidakkonsistenan kecil dalam generalisasi.


![image](https://github.com/user-attachments/assets/4d62ef48-c91e-42c9-9c9f-4113ffa3697f)


Confusion matrix ini menunjukkan performa model klasifikasi dalam mengklasifikasikan 5 kelas makanan tradisional Indonesia: bakso, gado, gudeg, rendang, dan sate. Dari matriks, terlihat bahwa model memiliki performa tinggi pada kelas dengan prediksi yang sangat akurat 217 benar prediksi. Namun, model menunjukkan kesulitan dalam mengklasifikasikan kelas gudeg, hanya menghasilkan 45 prediksi benar dan beberapa kesalahan klasifikasi ke kelas gado dan rendang. Kesalahan lain tampak minimal, menunjukkan bahwa model bekerja cukup baik secara keseluruhan, tetapi perlu perbaikan pada kelas gudeg untuk meningkatkan kinerja.


![image](https://github.com/user-attachments/assets/a6d43cfd-0080-41e0-9aa5-5f5f5be50ae2)

Hasil evaluasi model menunjukkan performa yang sangat baik dengan akurasi keseluruhan sebesar **96%**. Setiap kelas memiliki f1-score yang tinggi, berkisar antara **0.96 hingga 0.97**, menunjukkan kemampuan model dalam mengenali semua kelas dengan akurat. Precision dan recall juga seimbang di hampir semua kelas, meskipun ada sedikit fluktuasi, terutama pada kelas dengan jumlah data lebih sedikit seperti **gudeg**. Secara keseluruhan, model berhasil mengklasifikasikan data secara konsisten dan efektif.


Link Collab dapat diakses di [MobileNet Collab](https://colab.research.google.com/drive/1dY7v2-vXL54LdlhmzbCIz8si30xKHfrU?usp=sharing) 


**Link model CNN dan MobileNet dapat dilihat disini** 👉 [Model h5](https://drive.google.com/drive/folders/112A0kvZ0j0RmSm08IwHgTVgzbI2Wam8j?usp=sharing)

## Tampilan Web Klasifikasi 🌻

![image](https://github.com/user-attachments/assets/188e2324-341c-41ec-8335-11273bbbf41e)


![image](https://github.com/user-attachments/assets/e2362f48-ac41-409e-9c04-753ea932081b)

[Live Demo](http://localhost:8501/)


## Author 🧑‍💻
**Uswatun Chasanah**

**202110370311274**
















 



