# Proyek Analisis Sentimen Ulasan WhatsApp Google Play Store

---

## Pendahuluan

Proyek ini bertujuan untuk mengembangkan model analisis sentimen pada ulasan aplikasi WhatsApp yang diambil dari Google Play Store. Analisis sentimen ini akan mengklasifikasikan ulasan menjadi tiga kategori: **negatif**, **netral**, dan **positif**. Kami menggunakan pendekatan _Machine Learning_ klasik dengan berbagai teknik ekstraksi fitur dan algoritma pelatihan untuk mencapai akurasi model yang tinggi.

---

## Tujuan Proyek

* Mengumpulkan **10.000 data** ulasan aplikasi WhatsApp dari Google Play Store melalui proses _scraping_.
* Melakukan tahapan **ekstraksi fitur** dan **pelabelan data** untuk mempersiapkan data pelatihan.
* Menggunakan algoritma _Machine Learning_ untuk pelatihan model analisis sentimen.
* Mencapai **akurasi minimal 85%** pada _testing set_.
* Melakukan **3 percobaan skema pelatihan** yang berbeda untuk membandingkan performa.
* Menyediakan fungsi **inferensi/pengujian** untuk mengklasifikasikan sentimen ulasan baru.

---
## Struktur Proyek

.
├── whatsapp_scraper.py             # Script untuk mengambil data ulasan dari Google Play Store
├── whatsapp_reviews.csv            # Dataset mentah hasil scraping (akan dihasilkan)
├── label_data_from_score.py        # Script untuk melabeli data berdasarkan kolom 'score'
├── whatsapp_reviews_labeled.csv    # Dataset ulasan yang sudah dilabeli (akan dihasilkan)
├── sentiment_analysis.ipynb        # Notebook Jupyter untuk pra-pemrosesan, ekstraksi fitur,
|                                   # pelatihan model (3 skema), evaluasi, dan inferensi
├── requirements.txt                # Daftar dependensi Python yang dibutuhkan
├── README.md                       # File ini
├── best_rf_word2vec_model_optimized.pkl  # Contoh model terbaik yang disimpan (akan dihasilkan)
└── best_word2vec_embeddings_optimized.model # Contoh model Word2Vec yang disimpan (akan dihasilkan)
---

## Persyaratan Sistem

Pastikan Anda memiliki **Python (versi 3.8 atau lebih tinggi direkomendasikan)** terinstal di sistem Anda.

---

## Langkah-langkah Menjalankan Proyek

Ikuti langkah-langkah di bawah ini secara berurutan untuk menjalankan proyek.

### 1. Menginstal Dependensi

Buka terminal atau _command prompt_ Anda, navigasikan ke direktori proyek ini, lalu jalankan perintah berikut untuk menginstal semua pustaka Python yang diperlukan:

```bash
pip install -r requirements.txt
```
## Anda mungkin juga perlu mengunduh data NLTK (untuk stopwords, lemmatizer, dan VADER jika digunakan untuk pelabelan awal):
import nltk
nltk.download('stopwords')
nltk.download('punkt')
nltk.download('wordnet')
nltk.download('vader_lexicon') # Opsional, jika Anda masih ingin mencoba VADER

### 2. Mengambil Data Ulasan (Scraping)
Jalankan skrip whatsapp_scraper.py untuk mengumpulkan ulasan aplikasi WhatsApp. Skrip ini akan mengambil sekitar 10.000 ulasan dan menyimpannya dalam file CSV.
```bash
python whatsapp_scraper.py
```
### 3. Pelabelan Data
Setelah data mentah terkumpul, selanjutnya buat pelabelan data untuk menambahkan kolom sentimen berdasarkan kolom 'score' yang ada di data ulasan.
### 4. Pelatihan dan Evaluasi Model
Buka file.ipynb. Notebook ini berisi semua langkah mulai dari pra-pemrosesan data, ekstraksi fitur, hingga pelatihan dan evaluasi model untuk ketiga skema percobaan yang telah ditentukan.

Skema 1: Pelatihan: SVM, Ekstraksi Fitur: TF-IDF, Pembagian Data: 80/20
Skema 2: Pelatihan: Random Forest, Ekstraksi Fitur: Word2Vec, Pembagian Data: 80/20 (dengan optimasi untuk mencapai akurasi >85%)
Skema 3: Pelatihan: Random Forest, Ekstraksi Fitur: TF-IDF, Pembagian Data: 70/30
Jalankan setiap sel di notebook secara berurutan. Notebook ini juga akan menyimpan model terbaik dan vectorizer yang digunakan.

### 5. Melakukan Inferensi (Pengujian)
Bagian inferensi disertakan di akhir file.ipynb. Anda dapat menguji model yang sudah dilatih dengan memasukkan ulasan teks baru dan melihat hasil klasifikasi sentimennya. Pastikan Anda telah menjalankan semua sel sebelumnya di notebook agar model dan vectorizer yang disimpan dapat dimuat dan digunakan.

## Kontribusi
Jika Anda ingin berkontribusi pada proyek ini, silakan ajukan _pull request_ atau buka issue di repositori ini.

## Lisensi
Proyek ini dilisensikan di bawah [MIT License]. Lihat file LICENSE (jika ada) untuk detail lebih lanjut.

