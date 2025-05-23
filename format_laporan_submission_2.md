# Laporan Proyek Machine Learning - Imelda Cyntia

## Project Overview

Di era digital saat ini, sistem rekomendasi memiliki peran penting dalam membantu pengguna memilah informasi dari banjir konten yang tersedia. Dalam industri hiburan Jepang, khususnya anime, ribuan judul tersedia di berbagai platform digital seperti MyAnimeList, Crunchyroll, dan Netflix. Jumlah konten yang masif ini sering kali membuat pengguna kewalahan dalam memilih anime yang sesuai preferensi, sehingga dibutuhkan sistem cerdas yang dapat memberikan rekomendasi personal.

Permintaan global terhadap anime terus meningkat. Menurut laporan Content Japan oleh Japan External Trade Organization (JETRO), nilai ekspor konten Jepang (termasuk anime) melalui layanan digital meningkat tajam, mencapai rekor baru pasca-2020 akibat percepatan digitalisasi selama pandemi COVID-19 (JETRO, 2021). Tren ini menunjukkan betapa pentingnya optimalisasi pengalaman pengguna dalam mengakses konten melalui sistem rekomendasi yang relevan.

Studi terbaru dalam bidang sistem rekomendasi juga menunjukkan bahwa pendekatan seperti Content-based Filtering dan Collaborative Filtering secara signifikan dapat meningkatkan kepuasan dan keterlibatan pengguna. Dalam kajian oleh Zhang et al. (2021), sistem rekomendasi yang menggabungkan informasi konten dengan perilaku pengguna terbukti memberikan performa lebih baik dalam domain hiburan seperti musik dan video-on-demand, termasuk anime.

Berdasarkan hal tersebut, proyek ini bertujuan membangun sistem rekomendasi anime menggunakan pendekatan Content-based Filtering dan Collaborative Filtering. Sistem ini memanfaatkan dataset publik dari Kaggle untuk menganalisis informasi genre, sinopsis, studio, serta rating pengguna. Hasilnya diharapkan dapat membantu pengguna menemukan anime yang relevan dengan minat mereka, serta memberikan insight bagaimana machine learning diterapkan dalam sektor hiburan digital.

## Daftar Referensi
JETRO. (2021). Content Japan Report: Export and Market Trends of Japanese Content. Japan External Trade Organization. https://www.jetro.go.jp/en/reports/statistics.html

Zhang, S., Yao, L., Sun, A., & Tay, Y. (2021). Deep Learning Based Recommender System: A Survey and New Perspectives. ACM Computing Surveys (CSUR), 52(1), 1–38. https://doi.org/10.1145/3285029

Adomavicius, G., & Tuzhilin, A. (2020). Context-Aware Recommender Systems. AI Magazine, 40(4), 67–80. https://doi.org/10.1609/aimag.v40i4.5319

## Business Understanding

### Problem Statements

1. Bagaimana pengguna dapat menemukan anime yang sesuai dengan preferensi pribadi mereka di tengah ribuan pilihan judul yang tersedia di berbagai platform?

2. Mengapa sistem rekomendasi umum atau daftar trending saat ini kurang efektif bagi pengguna yang memiliki preferensi khusus terhadap genre dan tipe tayangan?

3. Bagaimana cara menciptakan sistem rekomendasi yang tidak hanya mempertimbangkan karakteristik konten anime, tetapi juga perilaku pengguna lain untuk memberikan saran yang lebih personal dan relevan?

### Goals

1. Membangun sistem rekomendasi anime berbasis Content-based Filtering yang mempertimbangkan genre dan tipe tayangan untuk membantu pengguna menemukan anime yang relevan dengan preferensi pribadi mereka.

2. Meningkatkan personalisasi rekomendasi dengan pendekatan Collaborative Filtering yang memanfaatkan data interaksi dan rating pengguna lain yang memiliki pola kesukaan serupa.

3. Mengembangkan sistem rekomendasi yang adaptif dengan menggabungkan pendekatan Content-based dan Collaborative Filtering, sehingga mampu memberikan saran yang lebih akurat dan sesuai dengan minat pengguna.

### Solution Approach

Untuk mencapai tujuan di atas, sistem akan dikembangkan dengan mengimplementasikan lebih dari satu pendekatan rekomendasi yang saling melengkapi:

#### Solution Statements:

Pengguna membutuhkan sistem rekomendasi yang mampu menyajikan saran anime yang **relevan secara kontekstual** dan **personal secara sosial**, dengan mempertimbangkan baik karakteristik konten maupun perilaku pengguna lain.

#### Pendekatan 1: **Content-Based Filtering**

* **Deskripsi**: Sistem akan merekomendasikan anime berdasarkan kemiripan karakteristik konten, seperti genre, jenis tayangan (TV, Movie, OVA), dan skor rating. Pendekatan ini memungkinkan pengguna mendapatkan rekomendasi anime yang mirip dengan yang pernah mereka sukai.
* **Teknik yang digunakan**:

  * Representasi teks pada fitur genre menggunakan teknik TF-IDF Vectorizer.
  * Encoding fitur-fitur konten (seperti genre dan tipe) ke bentuk numerik.
  * Perhitungan kemiripan antar anime menggunakan Cosine Similarity.
  * Rekomendasi diberikan berdasarkan anime yang memiliki kemiripan tertinggi terhadap anime pilihan pengguna.

#### Pendekatan 2: **Collaborative Filtering**

* **Deskripsi**: Sistem akan merekomendasikan anime berdasarkan interaksi atau rating dari pengguna lain yang memiliki pola kesukaan serupa. Pendekatan ini membantu menangkap aspek sosial dari preferensi pengguna.
* **Teknik yang digunakan**:

  * User-Based Collaborative Filtering dengan algoritma k-Nearest Neighbors (kNN) untuk menemukan pengguna yang memiliki preferensi serupa.
  * Alternatif: Item-Based Collaborative Filtering, yang mengukur kemiripan antar anime berdasarkan rating kolektif dari banyak pengguna.

## Data Understanding
Proyek ini menggunakan **Anime Recommendation Database 2020** yang tersedia secara publik melalui Kaggle. Dataset ini dapat diakses melalui tautan berikut:
[https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database)

Dataset terdiri dari dua bagian utama:

1. **anime.csv** yang berisi metadata dari berbagai judul anime seperti genre, jumlah episode, rating, dan jumlah anggota (members) yang menambahkan anime ke daftar mereka.
2. **rating.csv** yang berisi rating yang diberikan oleh pengguna terhadap berbagai judul anime.

Secara umum:

* **anime.csv** memiliki **12.294 baris** dan **7 kolom**.
* **rating.csv** memiliki lebih dari **20 juta baris** dan **3 kolom**.

Dari eksplorasi awal:

* Dataset relatif **bersih**, meskipun terdapat **nilai kosong** pada kolom `rating` dan `genre` di `anime.csv`, serta rating `-1` di `rating.csv` yang menandakan pengguna belum memberikan penilaian. Nilai-nilai ini akan diproses atau dihapus sesuai konteks penggunaan.
* Tidak ditemukan missing value pada kolom utama di `rating.csv`, namun **outlier** seperti entri dengan `episodes` tidak diketahui (misalnya "Unknown") juga akan dibersihkan.

### Variabel-variabel pada `anime.csv`:

* `anime_id` : ID unik dari judul anime.
* `name` : Nama judul anime.
* `genre` : Daftar genre anime, dipisahkan koma (contoh: Action, Comedy).
* `type` : Tipe media (TV, Movie, OVA, dll.).
* `episodes` : Jumlah episode anime.
* `rating` : Rata-rata skor pengguna (0–10).
* `members` : Jumlah pengguna yang menambahkan anime ke daftar mereka.

### Variabel-variabel pada `rating.csv`:

* `user_id` : ID unik dari pengguna.
* `anime_id` : ID anime yang diberi rating.
* `rating` : Rating dari pengguna (1–10), atau `-1` jika pengguna hanya menambahkan ke daftar tanpa memberi penilaian.

## Exploratory Data Analysis (EDA)

Untuk memahami karakteristik data, dilakukan beberapa eksplorasi visual dan statistik dasar, antara lain:

### 1. Distribusi Genre:

Visualisasi genre menunjukkan bahwa **Comedy**, **Action**, dan **Romance** adalah genre yang paling umum. Sebagian besar judul anime memiliki lebih dari satu genre, sehingga fitur ini akan di-*split* dan *multi-hot encoded* dalam preprocessing.

### 2. Distribusi Rating:

Distribusi skor `rating` pada `anime.csv` menunjukkan bentuk lonceng, dengan puncak sekitar 6.5–7.5. Rating dari `rating.csv` memiliki distribusi mirip, namun juga mengandung `-1` yang akan dihapus karena tidak mewakili preferensi nyata.

### 3. Tipe Anime:

Sebagian besar anime bertipe **TV series**, diikuti oleh **Movie** dan **OVA**. Ini memberi indikasi bahwa mayoritas rekomendasi akan berasal dari anime TV.

### 4. Jumlah Episode:

Terdapat outlier seperti episode = "Unknown" atau jumlah episode ekstrem (>1000) yang memerlukan penanganan. Distribusi jumlah episode menunjukkan bahwa sebagian besar anime memiliki 12–24 episode, konsisten dengan format musim tayang di Jepang.

### 5. Analisis Interaksi Pengguna:

* Banyak pengguna hanya memberi rating pada sedikit anime, sementara sebagian kecil pengguna sangat aktif (memberi rating ke ratusan judul).
* Ini berpengaruh pada pendekatan collaborative filtering, di mana pengguna aktif menjadi basis penting dalam menemukan kesamaan minat.

### 6. Deteksi Outliner:
Boxplot menunjukkan adanya outlier pada beberapa fitur:

* Rating Anime: Umumnya berada di 6–8, namun ada outlier di bawah 4 dan di atas 9.
* Rating Pengguna: Setelah menghapus nilai -1, rating tetap menunjukkan outlier pada nilai ekstrem (1 dan 10).
* Jumlah Episode: Sebagian besar anime memiliki <100 episode, tapi ada outlier hingga >1000 episode.
* Jumlah Rating per Pengguna: Mayoritas pengguna memberi sedikit rating, namun ada outlier dengan >3000 rating.

## Data Preparation
Dalam proses persiapan data, dilakukan delapan tahap utama sebagai berikut:

1. **Pre-cleaning Rating Kosong (Rating = -1)**

   * Menghapus semua entri rating dengan nilai -1 pada dataset rating untuk memastikan hanya data valid yang diproses.

2. **Menangani Nilai yang Hilang (Missing Values)**

   * Mengecek nilai yang hilang pada dataset asli.
   * Melakukan imputasi pada kolom kategorikal seperti `genre` dan `type` dengan nilai modus (nilai paling sering muncul).
   * Menghapus baris dengan nilai rating kosong (`NaN`) karena rating merupakan fitur penting untuk pemodelan.

3. **Menghapus / Menyesuaikan Outlier**

   * Menggunakan metode IQR (Interquartile Range) untuk mendeteksi dan menghapus outlier pada fitur numerik seperti `rating` dan `episodes`.
   * Menangani nilai `episodes` yang tidak diketahui dengan menghapus baris dengan nilai ‘Unknown’ dan mengkonversi tipe data ke numerik.
   * Menghapus outlier pada rating pengguna dan jumlah rating per pengguna untuk menghindari bias akibat data ekstrem.

4. **Normalisasi / Standarisasi Fitur Numerik**

   * Melakukan standarisasi (StandardScaler) pada fitur numerik seperti `rating` dan `episodes` agar memiliki skala yang sama dan mendukung algoritma machine learning.

5. **Encoding Fitur Kategorikal**

   * Mengubah fitur `genre` yang multi-label dari string menjadi list, kemudian menerapkan MultiLabelBinarizer untuk membuat fitur biner untuk setiap genre.
   * Melakukan one-hot encoding pada fitur `type` untuk mengubah kategori menjadi fitur numerik yang dapat diproses model.

6. **Feature Engineering**

   * Membuat fitur baru `rating_per_episode` yang merupakan hasil pembagian rating dengan jumlah episode, sebagai indikator kualitas per episode.
   * Menambahkan fitur `genre_count` yang menghitung jumlah genre yang melekat pada satu anime.
   * Membuat fitur biner `type_TV_or_not` untuk menandai apakah anime bertipe TV atau bukan.

7. **Pembentukan Dataset Final**

   * Menyimpan nama anime pada dataset terpisah untuk keperluan tampilan hasil rekomendasi.
   * Membuat salinan dataset final dengan menghapus kolom yang tidak relevan atau bersifat ID seperti `anime_id` dan `name`.
   * Memastikan seluruh fitur penting termasuk hasil encoding dan fitur rekayasa sudah tercakup dalam dataset final.
   * Menampilkan dimensi dataset dan beberapa contoh data sebagai verifikasi akhir.



############################################BATAS AM KERJOAKAN ########################################################

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
