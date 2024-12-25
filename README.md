# Analisis Kinerja Model CNN dan MobileNet untuk Klasifikasi Citra Makanan Tradisional Nusantara

## Overview Project
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

## Overview Dataset
Dataset yang digunakan dalam klasifikasi terdiri dari 9.098 image dan telah terbagi ke dalam file train, validation, dan test. Terdapat 5 label yaitu '_Bakso_','_Gudeg_', '_Rendang_', '_Gado-Gado_',dan '_Sate_'.

## Pre Processing & Modelling 



