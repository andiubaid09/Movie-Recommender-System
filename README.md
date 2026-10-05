# 🎬 Movie Recommendation System

Proyek ini merupakan eksplorasi dan pengembangan **sistem rekomendasi film** dengan menerapkan berbagai pendekatan, mulai dari metode berbasis aturan sederhana hingga *machine learning* dan *deep learning*.

Proyek dikembangkan secara bertahap untuk memahami bagaimana sebuah sistem rekomendasi dapat berkembang dari pendekatan sederhana menjadi sistem **retrieval dan ranking** yang lebih terstruktur.

Setiap pendekatan diimplementasikan dan dianalisis secara terpisah sehingga karakteristik, kelebihan, keterbatasan, dan hasilnya dapat dibandingkan dengan pendekatan lainnya.

---

## 🎯 Latar Belakang

Dengan katalog film yang terdiri dari puluhan ribu judul, pengguna dapat mengalami kesulitan dalam menemukan film yang sesuai tanpa harus menelusuri katalog secara manual.

Sistem rekomendasi dapat membantu mempersempit pilihan tersebut dengan memberikan sejumlah film yang dianggap paling relevan berdasarkan pendekatan tertentu.

Namun, tidak terdapat satu pendekatan yang selalu paling tepat untuk semua kondisi.

Pendekatan berbasis popularitas dapat memberikan rekomendasi secara sederhana, tetapi tidak mempertimbangkan preferensi individual. Pendekatan berbasis konten dapat mempertimbangkan karakteristik film, sedangkan *collaborative filtering* dapat memanfaatkan pola interaksi pengguna.

Oleh karena itu, proyek ini mengeksplorasi berbagai pendekatan untuk memahami bagaimana masing-masing metode menyelesaikan permasalahan rekomendasi.

---

## 📌 Tujuan Proyek

Proyek ini bertujuan untuk:

* Memahami proses pengembangan sistem rekomendasi dari tahap data hingga rekomendasi.
* Mengeksplorasi berbagai algoritma dan pendekatan recommendation system.
* Memahami perbedaan *content-based*, *collaborative filtering*, *retrieval*, dan *ranking*.
* Menerapkan pendekatan machine learning dan deep learning untuk recommendation.
* Membandingkan karakteristik dan hasil dari berbagai pendekatan.
* Mempelajari bagaimana sistem rekomendasi dapat dikembangkan menuju arsitektur yang lebih scalable dan berorientasi produksi.

---

## 📊 Dataset

Proyek menggunakan dataset metadata film dengan sekitar **45.000 judul film**.

Beberapa informasi yang tersedia meliputi:

* Judul film
* Genre
* Overview
* Popularitas
* Rating
* Informasi perilisan
* Metadata film lainnya

Fitur yang digunakan dapat berbeda pada setiap pendekatan, sesuai dengan kebutuhan algoritma yang digunakan.

Dataset mentah tidak disertakan secara langsung dalam repository. Informasi mengenai sumber dataset dan cara mempersiapkan data akan dijelaskan pada dokumentasi terkait.

---

# 🧠 Pendekatan yang Dieksplorasi

Proyek ini dikembangkan secara bertahap. Pendekatan yang telah dan akan dieksplorasi meliputi:

| No. | Pendekatan                                 | Teknologi          | Status         |
| --- | ------------------------------------------ | ------------------ | -------------- |
| 01  | Popularity-Based Recommendation            | Pandas             | ✅ Selesai      |
| 02  | Content-Based — TF-IDF + Cosine Similarity | Scikit-learn       | 🚧 Coming Soon |
| 03  | Collaborative Filtering                    | TBD                | 🚧 Coming Soon |
| 04  | Neural Collaborative Filtering             | PyTorch            | 🚧 Coming Soon |
| 05  | Two-Tower / Dual Encoder                   | PyTorch            | 🚧 Coming Soon |
| 06  | Learning-to-Rank                           | PyTorch / LightGBM | 🚧 Coming Soon |
| 07+ | Pendekatan lainnya                         | —                  | 🔮 Eksplorasi  |

> Daftar pendekatan dapat bertambah seiring eksplorasi dan pengembangan proyek.

---

## 🔎 Perkembangan Pendekatan

Secara umum, proyek berkembang dari pendekatan sederhana menuju sistem yang semakin kompleks:

```text
Rule-Based Ranking
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
Future Approaches
```

Urutan tersebut bukan berarti pendekatan yang lebih kompleks selalu lebih baik.

Tujuan utama proyek adalah memahami **trade-off antara kesederhanaan, relevansi, personalisasi, kompleksitas model, dan kebutuhan komputasi**.

---

# 📈 Evaluasi dan Perbandingan

Evaluasi merupakan bagian penting dalam pengembangan sistem rekomendasi.

Metode evaluasi akan disesuaikan dengan jenis data, tujuan rekomendasi, dan karakteristik masing-masing pendekatan.

Beberapa metrik yang dapat digunakan antara lain:

* Precision@K
* Recall@K
* NDCG@K
* Hit Rate@K
* Mean Reciprocal Rank (MRR)
* Coverage
* Retrieval performance
* Waktu inferensi
* Penggunaan sumber daya

Tidak semua metrik akan diterapkan pada setiap pendekatan. Pemilihan metrik akan disesuaikan dengan permasalahan dan data yang tersedia.

### 📊 Perbandingan Model

Bagian ini akan diperbarui setelah beberapa pendekatan selesai diimplementasikan.

| Pendekatan                     | Metrik Utama | Hasil | Catatan     |
| ------------------------------ | -----------: | ----: | ----------- |
| Popularity-Based               |            — |     — | Baseline    |
| TF-IDF                         |            — |     — | Coming Soon |
| Collaborative Filtering        |            — |     — | Coming Soon |
| Neural Collaborative Filtering |            — |     — | Coming Soon |
| Two-Tower                      |            — |     — | Coming Soon |
| Learning-to-Rank               |            — |     — | Coming Soon |

> Tabel evaluasi akan diperbarui berdasarkan hasil eksperimen aktual. Tidak ada hasil yang dicantumkan sebelum model benar-benar diuji.

---

# 📁 Struktur Proyek

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
│
├── .gitignore
└── README.md
```

Struktur dapat berkembang seiring bertambahnya algoritma, eksperimen, dan kebutuhan sistem.

---

## 🛠️ Teknologi

Teknologi yang digunakan atau akan dieksplorasi dalam proyek ini meliputi:

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **PyTorch**
* **LightGBM**
* **Jupyter Notebook**

Library tambahan dapat digunakan apabila diperlukan oleh pendekatan tertentu.

---

# 📚 Dokumentasi Model

Penjelasan teknis setiap pendekatan dipisahkan dari README utama agar dokumentasi proyek tetap ringkas.

Dokumentasi masing-masing model dapat ditemukan di:

| Pendekatan                     | Dokumentasi                                                                |
| ------------------------------ | -------------------------------------------------------------------------- |
| Popularity-Based               | [`docs/01_popularity_based.md`](docs/01_popularity_based.md)               |
| TF-IDF Content-Based           | [`docs/02_tfidf_content_based.md`](docs/02_tfidf_content_based.md)         |
| Collaborative Filtering        | [`docs/03_collaborative_filtering.md`](docs/03_collaborative_filtering.md) |
| Neural Collaborative Filtering | [`docs/04_ncf_pytorch.md`](docs/04_ncf_pytorch.md)                         |
| Two-Tower                      | [`docs/05_two_tower_pytorch.md`](docs/05_two_tower_pytorch.md)             |
| Learning-to-Rank               | [`docs/06_learning_to_rank.md`](docs/06_learning_to_rank.md)               |

Dokumentasi akan tersedia seiring pendekatan tersebut selesai diimplementasikan.

---

# 🚀 Pengembangan Selanjutnya

Proyek ini dirancang sebagai proyek yang berkembang secara bertahap.

Pengembangan selanjutnya dapat mencakup:

* Implementasi pendekatan rekomendasi tambahan.
* Eksperimen dengan berbagai representasi user dan item.
* Eksplorasi metode candidate generation dan retrieval.
* Pengembangan ranking pipeline.
* Optimasi performa model.
* Refactoring notebook menjadi kode yang lebih modular.
* Penyimpanan dan versioning model.
* Penyediaan recommendation API.
* Pengembangan antarmuka pengguna.
* Eksperimen deployment dan serving.
* Pengujian pada dataset atau skenario yang berbeda.

Pendekatan baru dapat ditambahkan ke proyek tanpa mengubah struktur utama.

---

# 📌 Status Proyek

**Status: 🚧 Aktif Dikembangkan**

Saat ini pendekatan pertama, **Popularity-Based Recommendation**, telah selesai sebagai baseline.

Pendekatan berikutnya akan dikembangkan secara bertahap dan setiap implementasi akan didokumentasikan serta dievaluasi berdasarkan karakteristiknya masing-masing.

---

## 💡 Catatan

Proyek ini dikembangkan sebagai sarana pembelajaran dan eksplorasi sistem rekomendasi dengan pendekatan yang semakin kompleks.

Fokus utama proyek bukan hanya mendapatkan hasil rekomendasi, tetapi memahami **proses, asumsi, trade-off, dan alasan pemilihan setiap pendekatan**.

Dengan demikian, proyek ini diharapkan dapat menjadi perjalanan dari **baseline sederhana menuju pemahaman yang lebih menyeluruh mengenai machine learning recommendation system, retrieval, dan ranking**.
