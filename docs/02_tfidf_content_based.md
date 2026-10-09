# 02 — Content-Based Movie Recommender: TF-IDF

## 1. Overview

Notebook ini mengimplementasikan sistem rekomendasi film berbasis konten menggunakan TF-IDF dan cosine similarity.

Sistem membandingkan metadata film untuk menghasilkan rekomendasi berdasarkan kemiripan karakteristik konten.

Pendekatan ini menjadi tahap kedua dalam proyek Movie Recommendation System setelah Popularity-Based Recommendation.

## 2. Objectives

* Mengubah metadata tekstual film menjadi representasi numerik.
* Menghitung kemiripan antarfilm menggunakan cosine similarity.
* Menggabungkan kemiripan beberapa fitur menggunakan weighted scoring.
* Menghasilkan daftar rekomendasi berdasarkan skor tertinggi.
* Mengamati relevansi hasil melalui pengujian beberapa judul film.

## 3. Dataset and Features

Dataset berisi sekitar 45.428 baris metadata film.

Fitur yang digunakan:

| Feature                 | Fungsi                                                 |
| ----------------------- | ------------------------------------------------------ |
| `title`                 | Identitas film masukan dan label hasil rekomendasi     |
| `genres`                | Merepresentasikan kategori film                        |
| `overview`              | Merepresentasikan ringkasan cerita                     |
| `tagline`               | Merepresentasikan teks promosi                         |
| `belongs_to_collection` | Merepresentasikan informasi koleksi atau waralaba film |

Kolom `title` digunakan untuk menemukan film masukan dan menampilkan hasil. Empat fitur lainnya digunakan untuk menghitung kemiripan konten.

## 4. Methodology

### 4.1 TF-IDF Vectorization

Setiap fitur teks diproses menjadi matriks TF-IDF menggunakan `TfidfVectorizer` dari Scikit-learn.

Konfigurasi utama meliputi:

* `stop_words="english"`
* `max_features=5000` untuk membatasi ukuran vocabulary pada fitur yang sesuai
* `dtype=np.float32` untuk representasi numerik float32

Setiap fitur memiliki matriks tersendiri. Matriks disimpan dalam dictionary `tfidf_matrices`.

### 4.2 Cosine Similarity

Cosine similarity digunakan untuk menghitung kemiripan antara film masukan dan seluruh film lain pada masing-masing matriks fitur.

Perhitungan dilakukan saat dibutuhkan untuk film yang dipilih, bukan dengan membentuk seluruh matriks kemiripan pasangan film sekaligus.

### 4.3 Weighted Similarity

Skor kemiripan dari masing-masing fitur digabungkan menggunakan bobot awal berikut:

| Feature               | Weight |
| --------------------- | -----: |
| Genres                |   0.30 |
| Overview              |   0.45 |
| Tagline               |   0.10 |
| Belongs to Collection |   0.15 |

Rumus skor akhir:

$$
S(i,j)=\sum_{k=1}^{m}w_kS_k(i,j)
$$

Bobot ini merupakan konfigurasi awal eksperimen dan belum dioptimalkan secara sistematis.

### 4.4 Ranking

Film diurutkan berdasarkan skor gabungan dari yang tertinggi ke terendah. Film masukan dikecualikan dari daftar rekomendasi, lalu sistem mengembalikan sejumlah film teratas sesuai nilai `top_n`.

## 5. Experimental Results

Sistem diuji menggunakan sepuluh judul film.

| Input Movie              | Top Recommendation             | Similarity Score |
| ------------------------ | ------------------------------ | ---------------: |
| The Dark Knight          | The Dark Knight Rises          |         0.576426 |
| Finding Nemo             | Back To The Sea                |         0.402791 |
| The Godfather            | The Godfather: Part II         |         0.526293 |
| Titanic                  | Fida                           |         0.360214 |
| Toy Story                | Toy Story 3                    |         0.665822 |
| The Conjuring            | The Conjuring 2                |         0.555488 |
| Home Alone               | Home Alone 2: Lost in New York |         0.475209 |
| The Matrix               | The Matrix Reloaded            |         0.400092 |
| Minions                  | Despicable Me 2                |         0.571038 |
| The Shawshank Redemption | Brute Force                    |         0.418596 |

Hasil di atas merupakan skor kemiripan dari implementasi saat ini. Skor bukan probabilitas bahwa pengguna akan menyukai rekomendasi tersebut.

### Observations

* Beberapa film sekuel muncul di posisi teratas, misalnya The Dark Knight Rises, Toy Story 3, dan The Matrix Reloaded.
* Informasi genre dan koleksi dapat membantu menghasilkan rekomendasi yang relevan secara intuitif.
* Kemiripan genre belum tentu berarti kesamaan alur cerita atau tema secara mendalam.
* Pengujian masih bersifat kualitatif dan belum menjadi pengukuran performa kuantitatif.

## 6. Debugging and Implementation Notes

Pada pengujian awal, ditemukan ketidaksesuaian antara film masukan dan rekomendasi yang dihasilkan.

Penyebabnya adalah penggunaan label indeks DataFrame sebagai posisi baris pada matriks TF-IDF.

Implementasi kemudian diperbaiki menggunakan `np.flatnonzero()` untuk menemukan posisi film, dan `DataFrame.iloc` untuk mengambil baris berdasarkan posisi.

Perbaikan ini mengasumsikan bahwa urutan baris DataFrame tetap sama dengan urutan baris matriks TF-IDF.

## 7. Limitations

* Hasil bergantung pada ketersediaan dan kualitas metadata.
* TF-IDF menangkap pola kata, bukan pemahaman semantik mendalam.
* Bobot fitur masih berupa konfigurasi awal.
* Skor kemiripan tidak sama dengan probabilitas preferensi pengguna.
* Evaluasi belum menggunakan ground truth atau label relevansi.
* Sistem belum memanfaatkan riwayat interaksi atau preferensi individual pengguna.

## 8. Future Improvements

* Menguji variasi bobot fitur secara sistematis.
* Menyiapkan label relevansi untuk evaluasi.
* Menggunakan metrik seperti Precision@K, Recall@K, atau NDCG@K apabila data relevansi tersedia.
* Membandingkan pendekatan ini dengan Collaborative Filtering.
* Mempelajari metode rekomendasi berbasis neural network pada notebook berikutnya.

## 9. Learning Notes

Untuk penjelasan lebih mendalam tentang sintaks, konsep TF-IDF, sparse matrix, cosine similarity, weighted scoring, fungsi rekomendasi, dan debugging, lihat:

[`docs/02_content_based_deep_dive.md`](02_content_based_deep_dive.md)

## 10. Notebook

[`notebooks/02_Content_Based_Movie_Recommender_TFIDF.ipynb`](../notebooks/02_Content_Based_Movie_Recommender_TFIDF.ipynb)

## References

* [Scikit-learn — TfidfVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html)
* [Scikit-learn — cosine_similarity](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.pairwise.cosine_similarity.html)
* [NumPy — argsort](https://numpy.org/doc/stable/reference/generated/numpy.argsort.html)
* [Pandas — DataFrame.iloc](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iloc.html)
