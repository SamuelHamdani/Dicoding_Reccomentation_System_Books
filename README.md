# Laporan Proyek Machine Learning - Samuel Christian Hamdani

## Domain Proyek


---

### Latar Belakang

Perkembangan teknologi informasi yang pesat telah mendorong transformasi digital di berbagai bidang, termasuk dalam penyediaan layanan informasi dan hiburan. Salah satu bentuk transformasi tersebut adalah pemanfaatan sistem rekomendasi (recommender system) dalam membantu pengguna menemukan konten yang sesuai dengan minat atau kebutuhan mereka. Dalam konteks literasi dan pembelajaran, sistem rekomendasi buku menjadi salah satu solusi yang sangat relevan untuk mengatasi tantangan dalam memilih buku yang tepat di tengah melimpahnya pilihan yang tersedia.

Sistem rekomendasi buku adalah sistem yang dirancang untuk memberikan saran bacaan kepada pengguna berdasarkan sejumlah faktor, seperti interaksi sebelumnya, preferensi pribadi, atau karakteristik konten dari buku itu sendiri. Salah satu pendekatan populer yang digunakan dalam pengembangan sistem rekomendasi adalah content-based filtering menawarkan solusi yang lebih personal dengan menganalisis karakteristik atau fitur dari buku, seperti judul dan penuli. Sistem ini akan merekomendasikan buku yang memiliki kemiripan konten dengan buku yang pernah dibaca atau disukai oleh pengguna. Dengan demikian, meskipun pengguna baru dan belum memiliki banyak interaksi, sistem tetap dapat memberikan rekomendasi berdasarkan deskripsi atau atribut buku yang pernah mereka baca.

Melalui latar belakang ini, pengembangan model machine learning untuk sistem rekomendasi buku berdasarkan buku yang pernah dibaca menjadi topik yang penting dan relevan untuk diteliti. Dengan memanfaatkan data historis interaksi pengguna, diharapkan sistem yang dikembangkan mampu memberikan rekomendasi yang bersifat personal, adaptif, dan dapat meningkatkan kepuasan pengguna dalam menjelajahi dunia literasi.

## Business Understanding

---

### Problem Statement
1. Pengguna kesulitan menemukan buku yang sesuai dengan minat mereka karena terlalu banyak pilihan yang tersedia.

2. Rekomendasi yang bersifat umum atau acak sering kali tidak relevan dan mengurangi kepuasan pengguna.

3. Kurangnya pemanfaatan teknologi machine learning dalam sistem rekomendasi buku yang ada saat ini.

### Goals
1. Mengembangkan sistem rekomendasi buku berbasis machine learning.

2. Menganalisis dan memahami preferensi pengguna berdasarkan data buku yang pernah dibaca.

3. Meningkatkan relevansi dan akurasi rekomendasi buku untuk setiap pengguna.

### Solution Statement
1. Mengembangkan sistem rekomendasi buku berbasis machine learning dengan pendekatan content-based filtering, yaitu merekomendasikan buku yang memiliki kemiripan fitur (seperti judul, penulis) dengan buku yang pernah dibaca atau disukai oleh pengguna.

2. Menggunakan algoritma machine learning untuk mempelajari pola kesukaan pengguna dan menghasilkan rekomendasi yang bersifat personal.

3. Menerapkan teknik pemrosesan teks (seperti TF-IDF atau cosine similarity) untuk mengukur kemiripan antar buku berdasarkan kontennya.

## Data Understanding

---

Pada tahap ini dilakukan eksplorasi awal isi dataset untuk mengenalu beberapa fitur penting yang memengaruhi pengembangan sistem rekomendasi buku.

### Sumber Data
Sumber Dataset : https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset?select=Ratings.csv

Dataset yang diambil berasal dari sumber open source yaitu Kaggle yang menyimpan 3 dataset seperti macam-macam buku yang tersedia, rating pengguna, dan jumlah pengguna.

### Jumlah Data

1. Dataset Buku (books.csv)
  
    Jumlah Kolom : Pada dataset terdapat jumlah kolom sebanyak 8 kolom yang menyimpan data buku seperti:

    *   ISBN
    *   Book-TItle
    *   Book-Author
    *   Year-Of-Publication
    *   Publisher
    *   Image-URL-S
    *   Image-URL-M
    *   Image-URL-L

    Jumlah Baris : Sebanyak 271360 baris yang menyimpan data buku pada dataset ini.

2. Dataset Pengguna (users.csv)
  
    Jumlah Kolom : Pada dataset terdapat jumlah kolom sebanyak 3 kolom yang menyimpan data rating pengguna kepada buku yang pernah dibaca seperti:

    *   User-ID
    *   Location
    *   Age

    Jumlah Baris : Sebanyak 278858 baris yang menyimpan data buku pada dataset ini.

3. Dataset Rating (rating.csv)
  
    Jumlah Kolom : Pada dataset terdapat jumlah kolom sebanyak 3 kolom yang menyimpan data pengguna seperti:

    *   User-ID
    *   ISBN
    *   Book-Rating

    Jumlah Baris : Sebanyak 1149780 baris yang menyimpan data buku pada dataset ini.

### Kondisi Data:

1. Nilai Missing Value : Pada setiap dataset setelah dilakukan pemeriksaan nilai missing value didapatkan hasil bahwa dataset buku (books.csv) memiliki 3 baris yang menyimpan data kosong, pada dataset pengguna (users.csv) terdapat cukup banyak nilai kosong untuk usia pengguna, dan dataset rating (rating.csv) tidak memiliki data kosong. Dataset yang menyimpan nilai kosong akan dilakukan proses pembersihan.

2. Nilai Duplikat : Pada ketiga dataset, tidak terdapat data yang terduplikat, sehingga bisa disimpulkan bahwa ketiga dataset aman dari datad uplikat.

### Deskripsi Fitur
Berikut adalah penjelasan masing-masing fitur dalam masing-masing dataset:
1. Dataset Buku (books.csv)

    *   ISBN : Kode unik identifikasi untuk setiap buku (International Standard Book Number). Digunakan untuk menghubungkan data buku dengan data rating.
    *   Book-TItle : Judul lengkap dari buku. Berguna untuk menampilkan informasi buku pada antarmuka pengguna
    *   Book-Author : Nama penulis buku
    *   Year-Of-Publication : Tahun terbit buku.
    *   Publisher : Nama penerbit buku.
    *   Image-URL-S : URL gambar sampul buku dalam ukuran kecil (S)
    *   Image-URL-M : URL gambar sampul buku dalam ukuran sedang (M)
    *   Image-URL-L : URL gambar sampul buku dalam ukuran besar (L)

2. Dataset Pengguna (users.csv)
    *   User-ID : ID unik untuk masing-masing pengguna. Digunakan untuk menghubungkan data pengguna dengan data rating.
    *   Location : Lokasi pengguna
    *   Age : Usia pengguna

3. Dataset Rating (ratings.csv)
    *   User-ID : ID unik untuk masing-masing pengguna. Digunakan untuk menghubungkan data pengguna dengan data pengguna.
    *   ISBN : Kode unik identifikasi untuk setiap buku (International Standard Book Number). Digunakan untuk menghubungkan data buku dengan data rating.
    *   Book-Rating : Nilai rating yang diberikan pengguna terhadap buku yang pernah dibaca, dinilai dalam skala 0–10.

### Proses Eksplorasi Awal
Pada bagian ini, dilakukan beberapa tahapan awal yang dilakukan sebelum pengembangan model, diantaranya:
1. Load Dataset

    Dataset diupload dari google drive yang dimana sudah didownload dari sumber (Kaggle) agar dapat digunakan untuk identifikasi macam-macam buku yang tersimpan beserta keterangannya, rating pengguna, dan jumlah pengguna.

2. Pemeriksaan Nilai Kosong

    Dataset diperiksa untuk mengetahui apakah terdapat nilai yang hilang atau tidak valid. Jika ditemukan, dilakukan penanganan seperti imputasi atau penghapusan baris.

3. Pemeriksaan Nilai Duplikat

    Dataset diperiksa untuk mengetahui apakah terdapat nilai yang Duplikat. Jika ditemukan, dilakukan penanganan seperti penghapusan baris.

## Data Preparation

---

Pada tahap ini dilakukan proses persiapan data sebelum data digunakan untuk pengembangan model sistem rekomendasi dengan melakukan pembersihan dan transformasi. 

### Proses Persiapan Data
Dikarenakan model yang dikembangkan menggunakan pendekatan Content-Based Filtering, model akan dipakai untuk memberikan rekomendasi buku berdasarkan buku yang telah dibaca oleh pengguna berdasarkan penulis yang sama. Oleh karena itu, dilakukan proses persiapan data hanya pada dataset 'books.csv' karena menyimpan data buku dan penulis. Tahapan yang dilakukan dalam persiapan data diantaranya:

1. Perubahan Nama Kolom
  
    Nama-nama kolom yang ada pada dataset diubah menjadi bentuk yang dapat dibaca oleh sistem agar membantu proses eksplorasi menjadi lebih mudah.

2. Pembersihan Data dan Perubahan Tipe Data
  
    Dataset yang menyimpan data yang tidak sesuai akan dilakukan pembersihan agar dan Kolom-kolom yang tipe datanya tidak sesuai dengan data yang disimpan akan dilakukan pembersihan untuk memudahkan proses eksplorasi selanjutnya.
  
3. Penyaringan Data

    Penyaringan data buku berdasarkan rentang tahun terbit dilakukan untuk memastikan validitas dan relevansi data yang digunakan dalam analisis Penyaringan ini membantu meningkatkan kualitas data dan menghasilkan analisis yang lebih valid serta dapat diandalkan.

4. Distribusi Data

    Dibuatkan sebuah visualisasi untuk menghitung jumlah banyak buku yang ada dari tahun ke tahun, jumlah buku yang diterbit dari masing-masing penerbit, jumlah buku yang dibuat oleh penulis.

5. Penanganan Nilai Kosong (Missing Value)

    Dataset diperiksa untuk mengetahui apakah terdapat nilai yang hilang atau tidak valid. Jika ditemukan, dilakukan penanganan seperti imputasi atau penghapusan baris.

6. Pengurangan Data
  
  Karena data yang tersimpan pada dataset berjumlah cukup banyak (+- 20000 data) sistem membutuhkan memori yang cukup banyak untuk memproses seluruh data tersebut. Oleh karena itu dilakukan pengurangan data agar sistem dapat menggunakan data buku untuk pembuatan sistem rekomendasi.

7. Transformasi Data
  
  Setelah dataset telah bersih, selanjutnya mengtransformasi data menjadi bentuk dictionary agar bisa dipakai dalam pengembangan model sistem rekomendasi.

8. Vektorisasi Data

  Dilakukan proses vektorisasi data menggunakan library TfIdVectorizer untuk menyaring dan mengubah teks menjadi representasi angka yang mencerminkan pentingnya setiap kata, agar bisa diproses oleh model machine learning dengan lebih efektif.

## Model Development

---

Setelah data yang digunakan telah selesai untuk dibersihkan dan bisa dipakai, selanjutnya adalah pengembangan model machine learning dengan pendekatan Content-Based Filtering untuk membuat sistem rekomendasi buku berdasarkan buku dengan penulis (author) yang sama menggunakan kelas Cosine Similarity.

Penjelasan pendekatan Content-Based Filtering:

**Cara kerja:**

1. Ekstraksi Fitur: Sistem mengekstrak fitur dari item, seperti penulis, genre, kata kunci, deskripsi, dll.

2. Representasi Vektor: Fitur-fitur tersebut dikonversi menjadi bentuk numerik, biasanya menggunakan metode seperti TF-IDF atau word embeddings.

3. Perhitungan Kemiripan: Sistem menghitung kemiripan antara item menggunakan metrik seperti cosine similarity.

4. Rekomendasi: Sistem merekomendasikan item lain yang paling mirip dengan item yang pernah disukai oleh pengguna.

**Kelebihan :**

1. Tidak tergantung data pengguna lain: Sistem dapat bekerja dengan baik meskipun hanya ada sedikit pengguna (cocok untuk cold-start user).

2. Personalized: Rekomendasi sangat sesuai dengan preferensi individu karena berdasarkan riwayat pengguna itu sendiri.

3. Transparansi: Lebih mudah menjelaskan alasan rekomendasi ("buku ini direkomendasikan karena mirip dengan buku X yang Anda sukai").

**Kekurangan:**

1. Kurang mampu memberikan keberagaman: Sistem cenderung merekomendasikan item yang sangat mirip, sehingga bisa membatasi eksplorasi.

2. Terbatas pada fitur item: Jika fitur kurang informatif atau tidak lengkap, kualitas rekomendasi akan menurun.

3. Cold-start item: Tidak dapat merekomendasikan item baru jika belum memiliki informasi kontennya.

## Evaluation

---

Setelah model telah selesai dikembangkan, selanjutnya melakukan tes validasi guna mencari tahu apakah model yang dikembangkan untuk memberikan rekomendasi 5 buku berdasarkan penulis yang sama dengan metrik evaluasi Precision@K dan NDCG@K

**Precision@K**

Mengukur proporsi item yang relevan di antara k item teratas yang direkomendasikan.

Rumus :

Precision@k=  (Jumlah item relevan dalam top-k) /k

**NDCG@k**

Mengukur kualitas peringkat dari rekomendasi, dengan memberi bobot lebih tinggi pada item relevan yang muncul di posisi atas.

Rumus:

**DCG@k**

DCG@k = rel₁ + (rel₂ / log₂(3)) + (rel₃ / log₂(4)) + ... + (rel_k / log₂(k + 1))

Keterangan:
- relᵢ adalah skor relevansi item pada posisi ke-i (biasanya 1 untuk relevan, 0 untuk tidak relevan)
- log₂ adalah logaritma basis 2
- Posisi dihitung mulai dari 1, sehingga rumus menggunakan log₂(i + 1)

**NDCG@k**

NDCG@k = DCG@k / IDCG@k

Keterangan:
- IDCG@k adalah nilai DCG ideal, yaitu ketika semua item relevan berada di urutan teratas
- Nilai NDCG berada antara 0 (sangat buruk) hingga 1 (sangat baik)

---

### Hasil Evaluasi

| Metrik Evaluasi | Skor | Persentase |
| -------------------- | ---------- | ----|
| Precision@k               | 0.80   | 80% |
| Recall@k               | 1.00   | 100% |

Hasil evaluasi menunjukkan bahwa sistem mampu merekomendasikan buku dengan Precision@5 sebesar 0.80 atau 80% dan NDCG@5 sebesar 1.00 100% , yang berarti 4 dari 5 rekomendasi benar-benar relevan dan semuanya berada dalam urutan peringkat yang ideal—menandakan bahwa sistem rekomendasi bekerja sangat baik dalam konteks buku ini.

### Hubungan Business Understanding
| **Aspek**                                                                                                       | **Evaluasi**                                                                                                                                                                                                |
| --------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Problem 1: Pengguna kesulitan menemukan buku yang sesuai dengan minat mereka karena terlalu banyak pilihan**  | Model mampu menyaring dan merekomendasikan buku yang relevan berdasarkan kemiripan dengan buku yang pernah dibaca atau disukai, sehingga membantu pengguna menemukan buku yang sesuai dengan preferensinya. |
| **Problem 2: Rekomendasi yang bersifat umum atau acak sering kali tidak relevan**                               | Dengan pendekatan content-based filtering dan perhitungan kemiripan menggunakan cosine similarity, sistem dapat memberikan rekomendasi yang lebih personal dan tepat sasaran.                               |
| **Problem 3: Kurangnya pemanfaatan teknologi machine learning dalam sistem rekomendasi buku yang ada saat ini** | Sistem yang dibangun telah mengimplementasikan teknik TF-IDF dan cosine similarity secara efektif untuk memahami kemiripan antar buku, memanfaatkan teknologi machine learning secara langsung.             |
| **Goal 1: Mengembangkan sistem rekomendasi buku berbasis machine learning**                                     | Sistem berhasil dibangun dengan pendekatan content-based filtering menggunakan data buku, penulis, dan tingkat kesamaan antar konten.                                                                       |
| **Goal 2: Menganalisis dan memahami preferensi pengguna berdasarkan data buku yang pernah dibaca**              | Sistem dapat mengidentifikasi dan menyarankan buku lain berdasarkan kemiripan penulis dengan yang pernah dibaca oleh pengguna.                                                                              |
| **Goal 3: Meningkatkan relevansi dan akurasi rekomendasi buku untuk setiap pengguna**                           | Output sistem memberikan hasil dengan skor kemiripan yang tinggi, menunjukkan bahwa sistem menghasilkan rekomendasi yang relevan dan akurat.                                                                |

### Solusi
Solusi yang dikembangkan berupa sistem rekomendasi buku berbasis content-based filtering terbukti mampu menyajikan daftar rekomendasi buku yang sesuai berdasarkan konten buku yang telah dibaca, khususnya melalui analisis penulis. Dengan menggunakan pendekatan TF-IDF Vectorizer dan cosine similarity, sistem ini memberikan hasil yang akurat dan relevan tanpa memerlukan data eksplisit dari pengguna. Hasilnya, pengguna dapat dengan mudah menemukan buku yang sesuai dengan minatnya, menghemat waktu dalam pencarian, serta meningkatkan kepuasan terhadap pengalaman membaca.

Dengan demikian, tahap evaluasi menunjukkan bahwa model rekomendasi yang dibangun tidak hanya menjawab permasalahan utama pengguna, tetapi juga memberikan nilai tambah nyata dalam konteks personalisasi dan efisiensi dalam menemukan referensi bacaan yang relevan.
