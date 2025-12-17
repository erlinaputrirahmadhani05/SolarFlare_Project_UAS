# 📘 Prediksi Suar Matahari Menggunakan Model Klasifikasi Machine Learning dan Deep Learning

## 👤 Informasi

- **Nama:** Erlina Putri Rahmadhani
- **Repo:** https://github.com/erlinaputrirahmadhani05/UASPROJECT_SOLARFLARE
- **Video:** [...]

---

# 1. 🎯 Ringkasan Proyek

Fenomena Suar Matahari (Solar Flare) kuat (Kelas M dan X) merupakan salah satu kejadian paling signifikan dalam ranah Cuaca Angkasa (Space Weather). Proyek ini bertujuan untuk mengembangkan sistem prediksi dengan menggunakan Machine Learning untuk mengklasifikasikan kemungkinan terjadinya Strong Flare berdasarkan data bintik tinggi yang dilepaskan oleh flare. Pemodelan fenomena ini menghadapi tantangan utama, yaitu ketidakseimbangan Kelas (Class Imbalance). Masalah imbalance, hubungan antara fitur bintik matahari yang terukur dengan aktivitas flare bersifat sangat non-linear, yang sulit ditangkap oleh model statistik tradisional. Untuk mengatasi permasalaha tersebut, proyek ini menerapkan dan membandingkan algoritma klasifikasi yang canggih, meliputi model Baseline, model Advanced, dan Deep Learning

---

# 2. 📄 Problem & Goals

**Problem Statements:**

- Sulit memprediksi terjadinya solar flare berdasarkan parameter aktivitas matahari
- Dataset solar flare memiliki fitur kategorikal yang perlu preprocessing khusus
- Dibutuhkan model machine learning yang mampu menangkap pola non-linear
- Model deep learning diperlukan untuk mempelajari hubungan kompleks antar fitur

**Goals:**

- Membangun model klasifikasi solar flare dengan akurasi minimal 80%
- Membandingkan performa baseline, ML, dan deep learning
- Menentukan model terbaik berdasarkan metrik evaluasi
- Menghasilkan model yang dapat direproduksi

---

## 📁 Struktur Folder

```
project/
│
├── data/
│   └── flare.data1
│   └── flare.data2                  # Dataset (tidak di-commit, download manual)
│
├── notebooks/                       # Jupyter notebooks
│   └── UAS_DATASCIENCE_ERLINA_5B.ipynb
│
├── models/                          # Saved models
│   ├── rf_predictions_solar_flare.pkl
│   ├── model_solar_flare_logreg.pkl
│   └── dl_predictions_solar_flare.pkl
│   ├── hasil_uji_solar_logreg.csv
│
├── images/                 # Visualizations
│   └── Matrix_Logistic Regression.png
│   └── Matrix_Random Forest.png
│   └── Matrix_MLP.png
│   └── VisualisaiPerbandingan.png
│   └── Visualisasi1.png
│   └── Visualisasi2.png
│   └── Visualisasi3.png
│
├── LAPORAN PROYEK AKHIR.pdf
├── requirements.txt        # Dependencies
└── README.md
```

---

# 3. 📊 Dataset

- **Sumber:** UCI Machine Learning Repository
- **Jumlah Data:** 1389
- **Tipe:** categorical (nominal & ordinal), integer (numerik diskrit)

### Fitur Utama

| Fitur             | Deskripsi                             |
| ----------------- | ------------------------------------- |
| code              | Kode klasifikasi region matahari      |
| largest_spot_size | Ukuran terbesar sunspot pada region   |
| spot_distribution | Pola distribusi sunspot               |
| activity          | Tingkat aktivitas region matahari     |
| evolution         | Perkembangan region matahari          |
| previous_activity | Aktivitas flare sebelumnya            |
| complexity        | Kompleksitas magnetik region matahari |
| area              | Luas area sunspot                     |
| largest_spot      | Ukuran sunspot terbesar               |
| c_class_flare     | Jumlah flare kelas C dalam 24 jam     |
| m_class_flare     | Jumlah flare kelas M dalam 24 jam     |
| c_class_flare     | Jumlah flare kelas C dalam 24 jam     |

---

# 4. 🔧 Data Preparation

- Cleaning : missing/duplicate: tidak ditemukan, sedangkan outlier: ada beberpaa nilai tinggi pada jumlah frale ditemukan melalui boxplot, namun nilai tersebut dianggap relevan secara ilmiah dan tidak dihapus
- Transformasi (encoding/scaling):

1. target Engineering: dibuat fitur target baru berdasarkan jumlah c-class, m-class, x-class flare
2. Encoding Fitur Kategorikal: fitur kategorikal (ukuran bintk matahari dan distribusi) di-encode menjadi nilai numerik unik menggunakan Label Encoding
3. Scaling: Fitur numerik distandarisasi menggunkaan StandardScaler

- Splitting (train/val/test): data dibagi menjadi Training Set 80% dan Test Set 20%

---

# 5. 🤖 Modeling

- **Model 1 – Baseline:** Logistic Regression
- **Model 2 – Advanced ML:** Random Forest
- **Model 3 – Deep Learning:** Multilayer Perceptron (MLP)

---

# 6. 🧪 Evaluation

**Metrik:** F1-Score / Recall / ROC-AUC (dipilih karena data tidak seimbang)

### Hasil Singkat

| Model         | F1- Score | Recall | ROC-AUC | Catatan                                                                     |
| ------------- | --------- | ------ | ------- | --------------------------------------------------------------------------- |
| Baseline      | 0.2353    | 0.6667 | 0.8345  | Memiliki Recall terbaik, sensitif terhadap Strong Flare                     |
| Advanced      | 0.1765    | 0.2000 | 0.7435  | Akurasi overall tertinggi (0.8993), tetapi kinerja F1/Recall rendah         |
| Deep Learning | 0.1176    | 0.0667 | 0.7957  | Accuracy tertinggi (0.946), tetapi Recall terendah (gagal mendeteksi flare) |

---

# 7. 🏁 Kesimpulan

- Model terbaik: Multilayer Perceptron (MLP)
- Alasan: mampu mempelajari hubungan non-linear antar fitur aktivitas matahari yang bersifat kompleks, memiliki akurasi dan nilai evaluasi yang lebih stabil pada data uji
- Insight penting:
  o Dataset Solar Flare didominasi oleh kejadian flare kelas C, sedangkan flare kelas M dan X jumlahnya jauh lebih sedikit, sehingga data bersifat imbalanced
  o Fitur numerik seperti jumlah kelas C,M,X menunjukkan distribusi yang tidak merata dan cenderung bernilai rendah.
  o Beberapa fitur kategorikal seperti kompleksitas magnetik dan evolusi region matahari memiliki keterkaitan dengan tingkat kemunculan solar flare yang lebih tinggi

---

# 8. 🔮 Future Work

- Data: Feature engineering lebih lanjut, saran: mengumpulkan lebih banyak observasi.
- Model: hyperparameter tuning lebih ekstensif dan Ensemble methods, saran: mencoba arsitektur DL yang lebih kompleks
- Deployment: membuat API, membuat web application, Containerization dengan Docker, saran: Deploy ke cloud

---

# 9. 🔁 Reproducibility

 Python version: 3.13
 Main Libraries:

1. Numpy
2. Pandas
3. Scikit-learn
4. Matplotlib
5. Seaborn
6. Tensorflow
