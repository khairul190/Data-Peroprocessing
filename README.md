# TIPS Data-Preprocessing
Seringkali pada saat terjun ke lapangan, data yang kita dapat tidak datang dalam keadaan rapi dan bersih, bahkan seringkali data yang kita peroleh sangat berantakan, diperlukan usaha ekstra untuk mempersiapkan data tersebut untuk siap dilakukan analisis

# Preprocessing
Kunci utama dalam mendapatkan model Data Science yang valid & reliable.
Preprocessing yang berbeda akan menghasilkan kesimpulan/insight yang berbeda.

# Beberapa Proses Dasar
- Seleksi variable dan "Join"
- Data Cleaning : Duplikasi, Noise dan Outliers
- Transformasi Data
- Dimensional Reduction

# Mengapa perlu preprocessing?
- Data di dunia nyata biasanya tidak sebersih/indah data di buku akademik.
  - Noise: Misal gaji bernilai negatif
  - Ouliers: Misal seseorang dengan penghasilan >500 juta/bulan.
  - Duplikasi: Banyak di media sosial
  - Encodings, dsb: Banyak di Big Data, karena masalah bagaimana data disimpan/join.
- Tidak lengkap: hanya agregat, kurang variabel penting, dsb.
- Analisa pada data yang tidak di preprocess biasanya menghasilkan insight yang tidak/kurang tepat.

# Beberapa langkah utama:
1. Data Gathering:
    - Data warehouse, database, web crawling/scrapping/streaming.
    - Identifikasi, ekstraksi, dan integrasi data
2. Data Cleaning:
3. Transformasi data (misal encoding var kategorik)
4. Normalisasi/standarisasi
5. Data reduction:
    - variable selection (domain knowledge/automatic)
    - Feature Engineering
    - Variable reduction

# Removing Duplicate Data
- Banyak di temukan di sistem Big Data.
- mempengaruhi model dan analisa yang berdasarkan frekuensi.
- Terkadang kita sengaja membuat duplikasi (misal pada kasus imbalanced learning).

# Noisy Data
Noise dapat terjadi karena:
- Kesalahan instrumen pengukuran: Misal di alat IoT pada saat cuaca buruk/baterai yang lemah.
- Kesalahan input/entry
- Transmisi yang tidak sempurna
- inkonsistensi penamaan

# Outliers
- Data yang memiliki karakteristik secara signifikan berbeda dengan kebanyakan data lainnya menurut suatu kriteria tertentu yang ditetapkan.
- Datanya valid (bukan Noise)
di Big Data sangat umum terjadi.
Apa yang sebaiknya dilakukan ke outliers?


# Univariate Outliers
- Quartiles (Boxplot)
- Asumsi Normal
- Asumsi distribusi lain

# Multivariate Outliers
- Clustering (DBSCAN)
- Isolation Forest

## Perbandingan beberapa metode pendeteksian outliers (multivariate):

- http://scikit-learn.org/stable/auto_examples/applications/plot_outlier_detection_housing.html#sphx-glr-auto-examples-applications-plot-outlier-detection-housing-py&nbsp;
- http://scikit-learn.org/stable/auto_examples/covariance/plot_outlier_detection.html#sphx-glr-auto-examples-covariance-plot-outlier-detection-py
- http://scikit-learn.org/stable/auto_examples/neighbors/plot_lof.html#sphx-glr-auto-examples-neighbors-plot-lof-py
- http://scikit-learn.org/stable/auto_examples/preprocessing/plot_all_scaling.html#sphx-glr-auto-examples-preprocessing-plot-all-scaling-py
- https://blog.dominodatalab.com/topology-and-density-based-clustering/

# Missing Values
Salah satu proses dalam ‘membersihkan data’ itu adalah mengidentifikasi dan menghandle missing value, apa itu missing value? Missing value adalah istilah untuk data yang hilang

# Penyebab Missing Value
Data yang hilang ini bisa disebabkan oleh beberapa hal, salah satu contohnya adalah
- Error pada data entry, baik itu human error ataupun kesalahan pada sistem
- Pada data survey, bisa disebabkan oleh responden yang lupa mengisi pertanyaan, pertanyaan yang sulit dimengerti, ataupun pertanyaan enggan diisi karena merupakan pertanyaan yang sensitif

# Bagaimana cara mendeteksi Missing Value?
Biasanya untuk menandakan bahwa suatu data hilang, cell tersebut dibiarkan kosong

Nah, permasalahan yang dihadapi pada data di lapangan adalah, penandaan untuk mengatakan bahwa data tersebut missing sangat beragam, bisa ditulis ‘?’ (tanda tanya), bisa ditulis ‘-‘ (strip), bisa suatu bilangan yang sangat besar atau sangat kecil (misal 99 atau -999)

Sebagai ilustrasi, perhatikan berikut ini:

Perhatikan bahwa data ini memiliki berbagai macam cara untuk mengatakan bahwa data pada cell tertentu adalah missing, misalnya:
- cellnya dikosongkan
- ditulis dengan n/a, NA, na, ataupun NaN
- ditulis dengan symbol –
- ataupun mempunyai nilai yang cukup aneh seperti nilai 12 pada kolom OWN_OCCUPIED, ataupun HURLEY pada kolom NUM_BATH

Ketika kita meng-load data ini ke python menggunakan pandas, beberapa notasi missing yang umum otomatis dikategorikan sebagai NaN (notasi missing value pada python)

# Tipe Missing Value
- Missing completely at random (MCAR)
Data hilang secara acak, dan tidak berkaitan dengan variabel tertentu


- Missing at random (MAR)
Data di suatu variabel hilang hanya berkaitan dengan variabel respon/pengamatan. Sebagai contoh, orang yang memiliki rasa was-was tinggi (x) cenderung tidak melaporkan pendapatan (y) mereka, walaupun missing value bergantung pada berapa nilai x, tapi seberapa besar nilai y yang missing tersebut masih tetap acak

- Missing not at random (MNAR)
Data di suatu variabel y berkaitan dengan variabel itu sendiri, tidak terdistribusi secara acak. Sebagai contoh, orang yang pendapatannya rendah cenderung tidak melaporkan pendapatannya. Tipe missing value ini yang relatif paling sulit untuk di handle

- Pada MCAR dan MAR, kita boleh menghilangkan data dengan missing value ataupun mengimputasinya. Namun pada kasus MNAR, menghilangkan data dengan missing value akan menghasilkan bias pada data. mengimputasinya pun tidak selalu memberikan hasil yang baik

# Menangani Missing Value
Setelah kita mengenali apa itu missing value, bagaimana biasanya missing value itu ditulis, dan juga apa saja tipe missing value. Sekarang akan dijelaskan bagaimana cara menghandle missing value


### Perlu dicatat bahwa, tidak ada metode yang benar benar terbaik dalam menghandle missing value, metode yang dapat digunakan akan bergantung pada tipe data dan masalah yang ditelaah

## Menghindari data dengan missing value
yaitu drop data / menghapus data yang mengandung missing value ataupun menghapus variabel yang memiliki banyak sekali missing value

Cara menghapus data inipun ada beberapa macam
- Listwise Deletion, yaitu menghapus row yang mempunyai satu atau lebih missing
- Pairwise Deletion, yaitu hanya menghapus missing value pada variabel variabel yang ingin digunakan, misal kita ingin mencari korelasi antara glucose_conc dan diastolic_bp, kita hanya perlu menghapus row berikut ini
- Menghapus variabel, yaitu membuang variabel jika data pada kolom tersebut banyak sekali yang missing, misalkan hampir 50%.

## Mengabaikan missing value
Beberapa algoritma machine learning atau metode analisis lainnya dapat dengan sendirinya menghandle missing value, contohnya adalah decision tree, k-Nearest Neighbors (kNN), Gradient Boosting Method (GBM) yang dapat mengabaikan missing value, ataupun XGBoost yang dapat mengimputasi sendiri missing value pada data

Ataupun jika ada beberapa kolom yang tidak memberikan informasi apa apa, kita dapat membiarkan missing value ada di kolom tersebut karena kolom tersebut pun tidak memberikan informasi yang signifikan, contohnya adalah nomor tiket pada data penerbangan, kita tidak perlu sulit-sulit memikirkan bagaimana cara mengimputasi kolom tersebut.

## Mengimputasinya
Kita dapat menggantikan missing value tersebut dengan suatu nilai, ada beberapa metode dalam mengimputasi missing value
- Univariate Imputation
Imputasi dengan median / mean / modus
Imputasi dengan median / mean digunakan pada data numerik, idenya kita mengganti missing value pada kolom dengan median / mean dari data yang tidak missing, sedangkan imputasi dengan modus digunakan pada data kategorik.

  (catatan : Jika distribusi data cukup skewed (menceng kanan atau kiri), atau terdapat nilai nilai ekstrim, median lebih di sarankan daripada mean)

  Alternatifnya, kita pun dapat membedakan imputasi berdasarkan variabel kategorik tertentu, misalnya untuk yang penderita diabetes, akan diimputasi dengan rata rata dari penderita diabetes, dan sebaliknya

- Multivariate Imputation

  Single Imputation
  
  Metode metode yang dapat digunakan adalah memprediksi nilai missing dengan menggunakan metode metode supervised learning seperti kNN, regresi linear, regresi logistik (untuk data kategorik)

Kasus Lainnya
Salah satu cara menangani missing value pada data kategorik dapat dijadikan level tersendiri

missing value pada data Time Series, imputasi dapat dilakukan dengan:

mengisi nilai yang missing dengan nilai sebelumnya yang tidak missing, sering disebut juga dengan Last Observation Carried Forward (LOCF) ataupun dengan nilai selanjutnya yang tidak missing, sering disebut juga Next Observation Carried Backward (NOCB)

Menggunakan Interpolasi Linear

Menggunakan Interpolasi Linear dengan memperhitungkan tren seasonal
