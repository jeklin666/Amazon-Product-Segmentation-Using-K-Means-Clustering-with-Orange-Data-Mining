# Amazon-Product-Segmentation-Using-K-Means-Clustering-with-Orange-Data-Mining

## Deskripsi Proyek
Proyek ini mengimplementasikan algoritma K-Means Clustering untuk melakukan segmentasi produk e-commerce berdasarkan data historis Amazon. Analisis ini bertujuan untuk mengekstraksi wawasan bisnis strategis guna mendukung pengambilan keputusan dalam manajemen portofolio produk, penetapan harga, dan kontrol inventaris. Pemrosesan data dan pemodelan machine learning divisualisasikan secara end-to-end menggunakan Orange Data Mining.

## Tautan Presentasi Bisnis
* **Dokumentasi Lengkap (Notion)**:[ https://app.notion.com/p/PORTOFOLIO-DATA-ANALYST-ZAKII-RAMADHAN-3770d45be53980c4b15cf0451a6cafd5?source=copy_link]
## Struktur Repositori
* `dataset/`: Berisi dataset mentah `amazon.csv` (1.465 baris data).
* `workspace/`: Berisi file alur kerja utama `k_means_amazon.ows` yang dapat dijalankan di Orange Data Mining.
* `assets/`: Berisi tangkapan layar alur kerja, visualisasi scatter plot, dan hasil evaluasi Silhouette Score.
* `docs/`: Berisi dokumen referensi jurnal pendukung.

## Teknologi dan Metodologi
* **Perangkat Lunak**: Orange Data Mining
* **Bahasa Pendukung**: Python (di balik layar Orange)
* **Algoritma**: K-Means Clustering (dengan inisialisasi KMeans++)
* **Evaluasi Model**: Silhouette Score
* **Metodologi Pendekatan**: CRISP-DM Framework

## Alur Prapemrosesan Data (Data Pipeline)
Proses Extract, Transform, Load (ETL) dikerjakan secara modular menggunakan komponen (widget) Orange:
1. **Feature Constructor (Formula)**: Membersihkan string non-numerik (simbol mata uang, koma, persen) dan melakukan casting tipe data float pada fitur harga dan diskon.
2. **Feature Selection (Select Columns)**: Mengisolasi atribut fungsional numerik untuk model dan menetapkan data string sebagai meta-atribut agar tidak membiaskan perhitungan jarak[cite: 2].
3. **Missing Value Handling (Impute)**: Mengisi data kosong pada kolom interaksi (rating) menggunakan nilai rata-rata (Average/Most-frequent) untuk mempertahankan 1.465 baris sampel data[cite: 2].
4. **Standardization (Preprocess)**: Menerapkan z-score normalization untuk menyetarakan metrik dengan rentang skala yang timpang (seperti harga dan rating bintang)[cite: 2].

## Hasil Segmentasi Utama
Evaluasi Silhouette Score merekomendasikan pembentukan dua klaster optimal (k=2) dengan skor 0.556 (Moderate Structure)[cite: 2]. 
* **Cluster 1 (Premium Products)**: Produk dengan harga asli tinggi, tingkat diskon rendah-sedang, dan rating stabil[cite: 2]. Fokus strategi bisnis: Optimasi margin dan kampanye retensi pelanggan[cite: 2].
* **Cluster 2 (Mass Market Products)**: Produk harga murah dengan persentase diskon masif dan volume ulasan sangat tinggi[cite: 2]. Fokus strategi bisnis: Penetrasi pasar dan kontrol inventaris untuk menjaga kelancaran arus kas[cite: 2].

## Cara Menjalankan Proyek
1. Unduh dan instal [Orange Data Mining](https://orangedatamining.com/).
2. Kloning repositori ini ke komputer lokal Anda.
3. Buka Orange, pilih menu `File` -> `Open`, lalu navigasikan ke folder `workspace/` dan buka file `.ows`.
4. Pastikan path dataset di widget `File` sudah diarahkan ke file `amazon.csv` di folder `dataset/`.
