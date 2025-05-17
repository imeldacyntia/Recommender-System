# Laporan Proyek Machine Learning - Imelda Cyntia

## 📌Project Overview

Di era digital saat ini, sistem rekomendasi memiliki peran penting dalam membantu pengguna memilah informasi dari banjir konten yang tersedia. Dalam industri hiburan Jepang, khususnya anime, ribuan judul tersedia di berbagai platform digital seperti MyAnimeList, Crunchyroll, dan Netflix. Jumlah konten yang masif ini sering kali membuat pengguna kewalahan dalam memilih anime yang sesuai preferensi, sehingga dibutuhkan sistem cerdas yang dapat memberikan rekomendasi personal.

Permintaan global terhadap anime terus meningkat. Menurut laporan Content Japan oleh Japan External Trade Organization (JETRO), nilai ekspor konten Jepang (termasuk anime) melalui layanan digital meningkat tajam, mencapai rekor baru pasca-2020 akibat percepatan digitalisasi selama pandemi COVID-19 (JETRO, 2021). Tren ini menunjukkan betapa pentingnya optimalisasi pengalaman pengguna dalam mengakses konten melalui sistem rekomendasi yang relevan.

Studi terbaru dalam bidang sistem rekomendasi juga menunjukkan bahwa pendekatan seperti Content-based Filtering dan Collaborative Filtering secara signifikan dapat meningkatkan kepuasan dan keterlibatan pengguna. Dalam kajian oleh Zhang et al. (2021), sistem rekomendasi yang menggabungkan informasi konten dengan perilaku pengguna terbukti memberikan performa lebih baik dalam domain hiburan seperti musik dan video-on-demand, termasuk anime.

Berdasarkan hal tersebut, proyek ini bertujuan membangun sistem rekomendasi anime menggunakan pendekatan Content-based Filtering dan Collaborative Filtering. Sistem ini memanfaatkan dataset publik dari Kaggle untuk menganalisis informasi genre, sinopsis, studio, serta rating pengguna. Hasilnya diharapkan dapat membantu pengguna menemukan anime yang relevan dengan minat mereka, serta memberikan insight bagaimana machine learning diterapkan dalam sektor hiburan digital.

## 📚 Daftar Referensi
JETRO. (2021). Content Japan Report: Export and Market Trends of Japanese Content. Japan External Trade Organization. https://www.jetro.go.jp/en/reports/statistics.html

Zhang, S., Yao, L., Sun, A., & Tay, Y. (2021). Deep Learning Based Recommender System: A Survey and New Perspectives. ACM Computing Surveys (CSUR), 52(1), 1–38. https://doi.org/10.1145/3285029

Adomavicius, G., & Tuzhilin, A. (2020). Context-Aware Recommender Systems. AI Magazine, 40(4), 67–80. https://doi.org/10.1609/aimag.v40i4.5319

## Business Understanding

Pada bagian ini, Anda perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan proyek yang menjawab pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Approach” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution approach (algoritma atau pendekatan sistem rekomendasi).

## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai jumlah data, kondisi data, dan informasi mengenai data yang digunakan. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya, uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

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
