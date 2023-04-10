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
