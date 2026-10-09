# 🎬 Movie Recommendation System

Proyek ini merupakan eksplorasi dan pengembangan **sistem rekomendasi film** menggunakan berbagai pendekatan, mulai dari metode berbasis aturan sederhana hingga machine learning dan deep learning.

Proyek dikembangkan secara bertahap untuk memahami bagaimana sistem rekomendasi berkembang dari pendekatan sederhana menjadi sistem retrieval dan ranking yang lebih terstruktur.

Setiap pendekatan diimplementasikan dan dianalisis secara terpisah agar karakteristik, kelebihan, keterbatasan, serta hasil eksperimennya dapat dipelajari dan dibandingkan.

## 🎯 Latar Belakang

Dengan katalog film yang terdiri dari puluhan ribu judul, pengguna dapat mengalami kesulitan menemukan film yang sesuai tanpa menelusuri katalog secara manual.

Sistem rekomendasi membantu mempersempit pilihan dengan menyarankan film berdasarkan kriteria tertentu.

Namun, setiap pendekatan memiliki karakteristik berbeda. Popularity-Based Recommendation menggunakan popularitas sebagai dasar rekomendasi, Content-Based Recommendation membandingkan karakteristik film, sedangkan Collaborative Filtering memanfaatkan pola interaksi pengguna.

Proyek ini mengeksplorasi berbagai pendekatan tersebut untuk memahami cara kerja, trade-off, dan kemungkinan pengembangannya.

## 🎯 Tujuan Proyek

* Memahami proses pengembangan sistem rekomendasi dari data hingga rekomendasi.
* Mengeksplorasi berbagai algoritma recommendation system.
* Memahami perbedaan Content-Based Filtering, Collaborative Filtering, Retrieval, dan Learning-to-Rank.
* Menerapkan pendekatan machine learning dan deep learning secara bertahap.
* Mengevaluasi hasil eksperimen berdasarkan karakteristik masing-masing metode.
* Mempelajari pertimbangan relevansi, personalisasi, kompleksitas, dan kebutuhan komputasi.

## 📊 Dataset

Proyek menggunakan dataset metadata film dengan sekitar **45.000 judul film**.

Informasi yang tersedia mencakup judul, genre, overview, popularitas, rating, informasi perilisan, dan metadata lainnya.

Fitur yang digunakan dapat berbeda pada setiap pendekatan. Dataset mentah tidak disertakan langsung dalam repository; lihat dokumentasi masing-masing notebook untuk informasi tentang data yang digunakan.

## 🧠 Pendekatan yang Dieksplorasi

| No. | Pendekatan                                 | Teknologi          | Status                                   |
| --- | ------------------------------------------ | ------------------ | ---------------------------------------- |
| 01  | Popularity-Based Recommendation            | Pandas             | ✅ Selesai                                |
| 02  | Content-Based — TF-IDF + Cosine Similarity | Scikit-learn       | ✅ Implementasi dan evaluasi awal selesai |
| 03  | Collaborative Filtering                    | TBD                | 🚧 Direncanakan                          |
| 04  | Neural Collaborative Filtering             | PyTorch            | 🚧 Direncanakan                          |
| 05  | Two-Tower / Dual Encoder                   | PyTorch            | 🚧 Direncanakan                          |
| 06  | Learning-to-Rank                           | PyTorch / LightGBM | 🚧 Direncanakan                          |

Status akan diperbarui berdasarkan perkembangan implementasi dan eksperimen aktual.

## 🔎 Perkembangan Pendekatan

```text
Popularity-Based Recommendation
              ↓
Content-Based Recommendation
              ↓
Collaborative Filtering
              ↓
Neural Recommendation
              ↓
Candidate Retrieval
              ↓
Learning-to-Rank
              ↓
Future Improvements
```

Urutan ini merupakan jalur eksplorasi pembelajaran, bukan pernyataan bahwa pendekatan yang lebih kompleks selalu lebih baik.

Fokus utama adalah memahami trade-off antara relevansi, personalisasi, kesederhanaan, kompleksitas model, dan kebutuhan komputasi.

## 📈 Evaluasi dan Perbandingan

Evaluasi dilakukan sesuai dengan tujuan dan karakteristik setiap pendekatan.

Metrik yang dapat dipertimbangkan meliputi:

* Precision@K
* Recall@K
* NDCG@K
* Hit Rate@K
* Mean Reciprocal Rank (MRR)
* Coverage
* Waktu inferensi
* Penggunaan sumber daya

Tidak semua metrik dapat diterapkan pada setiap metode. Metrik akan dipilih berdasarkan ketersediaan data relevansi dan tujuan evaluasi.

### Perbandingan Pendekatan

| Pendekatan                     | Hasil saat ini                    | Catatan                              |
| ------------------------------ | --------------------------------- | ------------------------------------ |
| Popularity-Based               | Implementasi selesai              | Baseline berbasis popularitas        |
| TF-IDF Content-Based           | Pengujian kualitatif awal selesai | Belum dievaluasi dengan ground truth |
| Collaborative Filtering        | Belum tersedia                    | Direncanakan                         |
| Neural Collaborative Filtering | Belum tersedia                    | Direncanakan                         |
| Two-Tower                      | Belum tersedia                    | Direncanakan                         |
| Learning-to-Rank               | Belum tersedia                    | Direncanakan                         |

Hasil kuantitatif akan dicantumkan setelah eksperimen dan evaluasi yang sesuai benar-benar dilakukan.

## 📁 Struktur Proyek

```text
movie-recommendation-system/
│
├── data/
│   └── movies_metadata.csv
│
├── notebooks/
│   ├── 01_Popularity_Based_Movie_Recommender.ipynb
│   ├── 02_Content_Based_Movie_Recommender_TFIDF.ipynb
│   ├── 03_Collaborative_Filtering_Recommender.ipynb
│   ├── 04_Neural_Collaborative_Filtering_PyTorch.ipynb
│   ├── 05_Two_Tower_Movie_Recommender_PyTorch.ipynb
│   └── 06_Learning_to_Rank_Movie_Recommender.ipynb
│
├── docs/
│   ├── 01_popularity_based.md
│   ├── 02_tfidf_content_based.md
│   ├── 02_content_based_deep_dive.md
│   ├── 03_collaborative_filtering.md
│   ├── 04_ncf_pytorch.md
│   ├── 05_two_tower_pytorch.md
│   └── 06_learning_to_rank.md
│
├── src/
│   ├── preprocessing.py
│   ├── recommender.py
│   └── evaluation.py
│
├── models/
├── .gitignore
└── README.md
```

Struktur di atas merupakan struktur yang direncanakan. Pastikan nama file dan folder disesuaikan dengan isi repository yang benar-benar sudah dibuat. Folder atau file yang belum ada tidak perlu dibuat hanya demi menyesuaikan diagram ini.

## 🛠️ Teknologi

Teknologi yang digunakan atau direncanakan untuk dieksplorasi:

* Python
* Pandas
* NumPy
* Scikit-learn
* SciPy
* PyTorch
* LightGBM
* Jupyter Notebook / Google Colab

Penggunaan library disesuaikan dengan kebutuhan masing-masing pendekatan.

## 📚 Dokumentasi Model

Setiap pendekatan memiliki dokumentasi tersendiri agar penjelasan teknis tidak menumpuk di README utama.

| Pendekatan                     | Dokumentasi                                                                |
| ------------------------------ | -------------------------------------------------------------------------- |
| Popularity-Based               | [`docs/01_popularity_based.md`](docs/01_popularity_based.md)               |
| TF-IDF Content-Based           | [`docs/02_tfidf_content_based.md`](docs/02_tfidf_content_based.md)         |
| Content-Based Deep Dive        | [`docs/02_content_based_deep_dive.md`](docs/02_content_based_deep_dive.md) |
| Collaborative Filtering        | [`docs/03_collaborative_filtering.md`](docs/03_collaborative_filtering.md) |
| Neural Collaborative Filtering | [`docs/04_ncf_pytorch.md`](docs/04_ncf_pytorch.md)                         |
| Two-Tower / Dual Encoder       | [`docs/05_two_tower_pytorch.md`](docs/05_two_tower_pytorch.md)             |
| Learning-to-Rank               | [`docs/06_learning_to_rank.md`](docs/06_learning_to_rank.md)               |

Dokumentasi pendekatan berikutnya akan dilengkapi seiring selesainya implementasi.

## 🚀 Pengembangan Selanjutnya

Rencana pengembangan meliputi:

* Mengimplementasikan Collaborative Filtering.
* Mengeksplorasi Neural Collaborative Filtering dan Two-Tower Recommendation.
* Mengembangkan pipeline candidate retrieval dan ranking.
* Mengevaluasi relevansi rekomendasi dengan metode yang sesuai.
* Membandingkan hasil antarpendekatan.
* Melakukan refactoring kode notebook menjadi modul yang dapat digunakan kembali.
* Mengeksplorasi recommendation API dan deployment apabila implementasi inti telah memadai.

## 📌 Status Proyek

**Status: Aktif dikembangkan.**

Popularity-Based Recommendation telah selesai diimplementasikan sebagai baseline. Content-Based Recommendation menggunakan TF-IDF dan cosine similarity juga telah diimplementasikan dan menjalani pengujian kualitatif awal.

Tahap berikutnya adalah memperkuat pemahaman dan dokumentasi hasil eksperimen, kemudian melanjutkan pengembangan Collaborative Filtering.

## 💡 Catatan

Proyek ini dikembangkan sebagai sarana pembelajaran dan eksplorasi recommendation system.

Fokusnya bukan hanya menghasilkan rekomendasi, tetapi juga memahami asumsi, proses, trade-off, keterbatasan, serta alasan pemilihan setiap pendekatan.

Tujuan akhirnya adalah membangun pemahaman bertahap mengenai sistem rekomendasi, machine learning, retrieval, dan ranking.
