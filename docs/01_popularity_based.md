# Popularity-Based Movie Recommendation

## 📌 Overview

Popularity-Based Recommendation merupakan pendekatan awal yang digunakan sebagai **baseline** dalam proyek Movie Recommendation System ini.

Pendekatan ini merekomendasikan film berdasarkan nilai **popularity** tertinggi. Film dengan nilai popularity yang lebih tinggi akan memiliki prioritas lebih tinggi dalam daftar rekomendasi.

Pendekatan ini bersifat **rule-based**, sehingga belum menggunakan Machine Learning maupun Deep Learning.

Tujuan utamanya adalah membangun baseline sederhana yang dapat digunakan sebagai pembanding terhadap pendekatan recommendation system yang lebih kompleks pada tahap berikutnya.

---

## 📊 Dataset

Dataset yang digunakan merupakan dataset metadata film dengan sekitar **45.000 data film**.

Beberapa fitur yang digunakan dalam sistem rekomendasi:

| Feature        | Fungsi                                |
| -------------- | ------------------------------------- |
| `title`        | Identitas dan output film             |
| `genres`       | Informasi genre film                  |
| `popularity`   | Sinyal utama untuk menentukan ranking |
| `vote_average` | Informasi rating film                 |
| `overview`     | Informasi/deskripsi film              |

Pada pendekatan ini, hanya `popularity` yang digunakan untuk menentukan urutan rekomendasi.

Fitur seperti `genres`, `vote_average`, dan `overview` ditampilkan sebagai informasi tambahan kepada pengguna.

---

## ⚙️ Recommendation Logic

Logika rekomendasi sangat sederhana:

```text
Movie Catalog
     │
     ▼
Select movie data
     │
     ▼
Sort by popularity
     │
     ▼
Select Top-N movies
     │
     ▼
Display recommendations
```

Secara konseptual, skor rekomendasi dapat ditulis sebagai:

```text
score(movie) = popularity(movie)
```

Kemudian seluruh film diurutkan berdasarkan skor tersebut secara descending.

---

## 💻 Implementation

Fungsi utama yang digunakan:

```python
def popularity_recommender(data, top_n=10):
    recommendations = (
        data[
            ["title", "genres", "popularity", "vote_average", "overview"]
        ]
        .sort_values(
            by="popularity",
            ascending=False
        )
        .head(top_n)
    )

    return recommendations.reset_index(drop=True)
```

Contoh penggunaan:

```python
recommendations = popularity_recommender(
    recommendation_df,
    top_n=10
)
```

Hasilnya berupa daftar film dengan nilai `popularity` tertinggi.

---

## 📈 Output

Sistem menghasilkan **Top-N Popular Movies**.

Setiap rekomendasi menampilkan:

* Judul film
* Genre
* Rating
* Popularity
* Overview

Contoh struktur output:

```text
1. Movie Title
   Genre      : Action Adventure
   Rating     : 7.8
   Popularity : 250.45
   Overview   : ...

2. Movie Title
   Genre      : Drama
   Rating     : 7.5
   Popularity : 230.12
   Overview   : ...
```

Nilai `top_n` dapat diubah sesuai kebutuhan, misalnya:

```python
top_n=5
```

atau:

```python
top_n=20
```

---

## 🔎 Key Insight

Hasil Exploratory Data Analysis menunjukkan bahwa **popularitas tidak selalu berbanding lurus dengan rating film**.

Film dengan popularity tinggi tidak selalu memiliki `vote_average` yang tinggi. Hal ini menunjukkan bahwa popularitas dan kualitas yang dipersepsikan melalui rating merupakan dua aspek yang berbeda.

Insight ini menjadi salah satu alasan untuk mengeksplorasi pendekatan recommendation system yang lebih kompleks pada tahap berikutnya.

---

## ✅ Advantages

### 1. Simple

Algoritmanya sangat sederhana dan mudah dipahami.

### 2. Fast

Tidak membutuhkan proses training sehingga proses rekomendasi dapat dilakukan dengan cepat.

### 3. Tidak Membutuhkan User Interaction

Pendekatan ini tidak membutuhkan data seperti:

* user ID
* movie ID yang ditonton
* rating pengguna
* riwayat interaksi pengguna

### 4. Cocok Sebagai Baseline

Hasil dari popularity-based recommendation dapat digunakan sebagai baseline untuk membandingkan pendekatan recommendation system lainnya.

---

## ⚠️ Limitations

Meskipun sederhana, pendekatan ini memiliki beberapa keterbatasan.

### Tidak Personalized

Semua pengguna akan mendapatkan rekomendasi yang sama.

```text
User A ──┐
User B ──┼──> Top Popular Movies
User C ──┘
```

Sistem tidak mengetahui preferensi individual setiap pengguna.

### Popularity Bias

Film yang sudah populer akan terus mendapatkan posisi tinggi, sementara film yang kurang populer memiliki kemungkinan lebih kecil untuk direkomendasikan.

### Tidak Memahami Content

Algoritma tidak memahami hubungan antara film berdasarkan:

* genre
* overview
* storyline
* karakteristik konten lainnya

### Tidak Memanfaatkan User Behavior

Tidak terdapat informasi mengenai film yang pernah ditonton, disukai, atau diberi rating oleh pengguna.

---

## 🧪 Evaluation

Pada tahap ini, evaluasi seperti **Precision@K, Recall@K, atau NDCG@K** belum diterapkan.

Alasannya, dataset metadata yang digunakan belum menyediakan **ground truth berupa user-item interaction** yang dapat digunakan untuk mengetahui apakah sebuah rekomendasi benar-benar relevan bagi pengguna tertentu.

Oleh karena itu, pendekatan ini diposisikan sebagai **baseline ranking**, bukan sebagai model yang dievaluasi berdasarkan personalized recommendation metrics.

Evaluasi yang lebih formal akan dipertimbangkan pada pendekatan berikutnya ketika tersedia data interaksi yang sesuai.

---

## 📌 Role in the Overall System

Popularity-Based Recommendation berfungsi sebagai tahap awal dalam perkembangan sistem:

```text
Rule-Based Baseline
        │
        ▼
Content-Based
        │
        ▼
Collaborative Filtering
        │
        ▼
Neural Recommendation
        │
        ▼
Candidate Retrieval
        │
        ▼
Learning-to-Rank
```

Baseline ini memberikan titik awal yang sederhana sebelum sistem dikembangkan menuju pendekatan yang lebih personalized dan scalable.

---

## 🚀 Next Step

Tahap berikutnya adalah **Content-Based Recommendation menggunakan TF-IDF dan Cosine Similarity**.

Pendekatan tersebut akan mulai mempertimbangkan karakteristik konten film sehingga rekomendasi dapat dibuat berdasarkan **kemiripan antarfilm**, bukan hanya berdasarkan popularitas.
