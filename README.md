# Analisis Kinerja Model CNN dan ResNet untuk Klasifikasi Citra Makanan Tradisional Nusantara

## Overview Project
Project *klasifikasi makanan tradisional Indonesia* bertujuan untuk melestarikan kekayaan kuliner sebagai bagian dari warisan budaya, sekaligus mendukung digitalisasi dan pengembangan teknologi di bidang kuliner. Model ini membantu mendokumentasikan dan mengenali ragam makanan tradisional secara akurat, mempermudah akses informasi, serta mendukung promosi kuliner lokal dalam sektor pariwisata dan ekonomi, termasuk pemberdayaan UMKM. Selain itu, teknologi ini dapat diaplikasikan dalam sistem rekomendasi makanan berbasis gambar, aplikasi pesan antar, dan platform wisata kuliner, memberikan pengalaman pengguna yang lebih baik. Di sisi penelitian, klasifikasi ini menyediakan data untuk analisis tren kuliner dan mendorong inovasi AI dalam mengenali dataset yang beragam. Dengan demikian, teknologi klasifikasi makanan tradisional Nusantara berperan penting dalam pelestarian budaya, promosi ekonomi, dan pengembangan layanan modern.

*Dataset* yang digunakan dalam penelitian ini diambil dari website Kaggle dengan data awal sebanyak 90.000 data. Berikut ini link datasetnya [Dataset Makanan Tradisional Indonesia](https://www.kaggle.com/datasets/theresalusiana/indonesian-food).

## Model yang Digunakan

Proyek ini menggunakan dua model deep learning utama untuk tugas klasifikasi gambar, yaitu:

1. **Convolutional Neural Network (CNN):**  
   CNN adalah model jaringan saraf yang dirancang khusus untuk pemrosesan data berbentuk gambar. CNN digunakan untuk mengekstraksi fitur penting dari gambar makanan tradisional Nusantara, seperti tekstur, warna, dan pola, sehingga model dapat mengenali dan membedakan kategori makanan secara akurat.

2. **Residual Network (ResNet):**  
   ResNet merupakan model jaringan saraf yang lebih dalam dibandingkan CNN standar, dengan fitur utama berupa residual connections. Fitur ini memungkinkan pelatihan jaringan yang lebih efisien dan mencegah masalah vanishing gradient pada jaringan yang dalam. Dalam proyek ini, ResNet digunakan untuk meningkatkan akurasi klasifikasi gambar dengan menangkap fitur visual yang lebih kompleks.

Penggunaan kedua model ini bertujuan untuk membandingkan performa antara CNN dan ResNet dalam mengklasifikasikan makanan tradisional Nusantara. Hasil perbandingan mencakup metrik seperti akurasi, loss, dan waktu pelatihan, yang akan dianalisis untuk menentukan model terbaik.
