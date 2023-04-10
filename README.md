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
