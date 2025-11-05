# 💡 NLP-SentimentAnalysis-PBA-Gasal-2025-InDrive

Proyek ini bertujuan untuk membangun dan mengevaluasi model **klasifikasi sentimen** guna mengidentifikasi pandangan (**positif**, **negatif**, atau **netral**) pengguna terhadap layanan dan fitur yang disediakan oleh **Aplikasi Transportasi InDrive**, berdasarkan ulasan yang dikumpulkan dari platform Google Play Store.

---

## 🎯 Tujuan

Tujuan utama dari proyek ini adalah:
1.  **Mengumpulkan Data:** Melakukan *web scraping* ulasan pengguna aplikasi InDrive dari Google Play Store.
2.  **Pra-pemrosesan Data (NLP):** Menerapkan teknik pembersihan, normalisasi kata tidak baku, *tokenisasi*, *stopword removal*, dan *stemming* pada teks ulasan berbahasa Indonesia untuk mempersiapkan data.
3.  **Analisis Data Eksploratif (EDA):** Menganalisis distribusi *rating* dan visualisasi *Word Cloud* untuk memahami sentimen secara umum.
4.  **Pembangun dan Evaluasi Model:** Membangun dan membandingkan beberapa model *Machine Learning* untuk klasifikasi sentimen (*Positif* vs *Negatif*).

---

## ⚙️ Metodologi & Algoritma

Proyek ini menggunakan alur kerja Natural Language Processing (NLP) standar, yang mencakup:

### Pra-pemrosesan Data
* **Pembersihan Teks:** Penghapusan URL, *tag* HTML, simbol, dan angka.
* **Case Folding:** Mengubah semua teks menjadi huruf kecil.
* **Normalisasi Kata:** Mengubah kata-kata tidak baku (slang/singkatan) menjadi kata baku. **Tahap ini mengacu pada file input kamus kata baku (`kamuskatabaku.xlsx`) untuk memastikan konsistensi dan keakuratan data.**
* **Stopword Removal & Stemming:** Menghapus kata-kata umum yang tidak signifikan dan mengubah kata berimbuhan menjadi kata dasar.

### Ekstraksi Fitur
* **TF-IDF (Term Frequency-Inverse Document Frequency):** Digunakan untuk mengubah teks hasil *stemming* menjadi representasi numerik.

### Penentuan Label Sentimen

Untuk tujuan klasifikasi biner (*Positif* vs *Negatif*), rating numerik (1 hingga 5) dari Google Play Store dipetakan sebagai berikut:

* **Rating Positif**: Ulasan dengan **Rating 4 dan 5**.
* **Rating Negatif**: Ulasan dengan **Rating 1, 2, dan 3**.

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/297d5f8f-4e79-49ff-88e0-7e50b009a1ba" />


#### Pemodelan Klasifikasi
Beberapa algoritma *Machine Learning* dibandingkan:
* Multinomial Naive Bayes (MNB)
* Random Forest Classifier (RF)
* Support Vector Machine (SVM) - Linear Kernel
* K-Nearest Neighbor (KNN)
* Extra Trees Classifier (ET)

---

## 📊 Hasil Evaluasi Model

| Algoritma | Accuracy (Test Set) | F1-Score (Cross-Validation) | Keterangan |
| :--- | :---: | :---: | :--- |
| **Extra Trees** | 0.81 | **0.8216** | Kinerja paling seimbang (F1-Score tertinggi). |
| Random Forest | 0.80 | 0.8177 | |
| SVM (Linear) | 0.79 | 0.8277 | |
| Logistic Regression | 0.76 | 0.8177 | |
| Naive Bayes | 0.74 | 0.8323 | |
| K-Nearest Neighbor | 0.62 | 0.7625 | |

**Kesimpulan:** Model **Extra Trees Classifier** menunjukkan kinerja paling seimbang dan stabil.

---
