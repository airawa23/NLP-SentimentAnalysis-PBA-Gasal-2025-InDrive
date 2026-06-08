# 💡 NLP-SentimentAnalysis-PBA-Gasal-2025-InDrive

- **Author**: Airlangga Bayu Taqwa (NRP: 5026221204)
- **Kelas**: PBA A Gasal 2025
- **Dosen Pengampu**: Irmasari Hafidz, S.Kom., M.Sc.

## *`Overview`*
Proyek ini bertujuan untuk membangun dan mengevaluasi model **klasifikasi sentimen** guna mengidentifikasi pandangan (**positif**, **negatif**, atau **netral**) pengguna terhadap layanan dan fitur yang disediakan oleh **Aplikasi Transportasi InDrive**, berdasarkan ulasan yang dikumpulkan dari platform Google Play Store.

---

## 🎯 Tujuan

Tujuan utama dari proyek ini adalah:
1.  **Mengumpulkan Data:** Melakukan *web scraping* ulasan pengguna aplikasi InDrive dari Google Play Store.
2.  **Pra-pemrosesan Data (NLP):** Menerapkan teknik pembersihan, normalisasi kata tidak baku, *tokenisasi*, *stopword removal*, dan *stemming* pada teks ulasan berbahasa Indonesia untuk mempersiapkan data.
3.  **Analisis Data Eksploratif (EDA):** Menganalisis distribusi *rating* dan visualisasi *Word Cloud* untuk memahami sentimen secara umum.
4.  **Pembangun dan Evaluasi Model:** Membangun dan membandingkan beberapa model *Machine Learning* untuk klasifikasi sentimen (*Positif* vs *Negatif*).

---

## 📊 Exploratory Data Analysis (EDA) & Dataset

Sebelum masuk ke tahap pemodelan, ulasan yang telah dikumpulkan dianalisis terlebih dahulu untuk melihat karakteristik kata dan distribusi sentimennya.

### 1. Sampel Dataset (Setelah NLP Preprocessing)
Berikut adalah cuplikan perbandingan data ulasan sebelum dan sesudah melewati proses pembersihan (*cleaning*, normalisasi, dan *stemming*):

| Ulasan Asli | Teks Hasil Preprocessing | Label Sentimen |
| :--- | :--- | :---: |
| apk yg sangat baguss dan bisa pilih indrive | apk yang sangat bagus dan bisa pilih indrive | Positif |
| saldo driver msh ada tau2 suruh daftar ulang | saldo driver masih ada tau suruh daftar ulang | Negatif |

### 2. Top 20 Most Common Words
Grafik di bawah ini menunjukkan 20 kata baku yang paling sering muncul di seluruh ulasan pengguna InDrive setelah proses *Stopword Removal*:

<img width="1189" height="590" alt="top 20 the most common words in a text column" src="https://github.com/user-attachments/assets/3c6170d0-cab0-46af-8d0b-8d743b0c426a" />

### 3. Word Cloud Sentimen Positif vs Negatif
Visualisasi kata yang paling dominan muncul berdasarkan pembagian kategori sentimen pengguna:

<table table-layout="fixed" width="100%">
  <tr>
    <td align="center" width="50%"><b>🟢 Word Cloud Sentimen Positif</b></td>
    <td align="center" width="50%"><b>🔴 Word Cloud Sentimen Negatif</b></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/c281e499-a4b0-47da-83f4-9f2474406af6"<img width="794" height="429" alt="negative_reviews" alt="Positive Reviews" width="100%"></td>
    <td><img src="https://github.com/user-attachments/assets/53b58db4-2f2a-426e-9eeb-e27d4e389919" alt="Negative Reviews" width="100%"></td>
  </tr>
</table>

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
| **Extra Trees** | 0.81 | **0.8463** | Kinerja paling seimbang (F1-Score tertinggi). |
| Random Forest | 0.79 | 0.8411 | |
| SVM (Linear) | 0.78 | 0.8310 | |
| Logistic Regression | 0.78 | 0.8331 | |
| Naive Bayes | 0.78 | 0.8368 | |
| K-Nearest Neighbor | 0.61 | 0.7616 | |

**Kesimpulan:** Model **Extra Trees Classifier** menunjukkan kinerja paling seimbang dan stabil.

---
