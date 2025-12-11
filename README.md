# 📘 Judul Proyek
*ANALISIS PENGARUH PENGANGGURAN DAN PENDIDIKAN PADA TINGKAT KRIMINALITAS MENGGUNAKAN BASELINE MODEL, MACHINE LEARNING, DAN DEEP LEARNING*

## 👤 Informasi
- **Nama:** Salva Mahardhika Pratama  
- **Repo:** https://github.com/SalvaMahardhika/234311026_UAS_DataScience  
- **Video:** https://youtu.be/ISKQuym34i4  

---

# 1. 🎯 Ringkasan Proyek
- Memprediksi tingkat kriminalitas berdasarkan fitur pengangguran dan pendidikan  
- Melakukan data preparation (cleaning, scaling, splitting).  
- Membangun 3 pendekatan model:
(1) Baseline – Linear Regression
(2) Advanced ML – Gradient Boosting
(3) Deep Learning – MLP Neural Network 
- Melakukan evaluasi menggunakan MSE, MAE, dan R².
- Menentukan model terbaik dan memberikan insight dari hasil pemodelan.  

---

# 2. 📄 Problem & Goals
**Problem Statements:**  
- Diperlukan model yang bisa memprediksi tingkat kriminalitas (ViolentCrimesPerPop) dengan akurasi tinggi berdasarkan variabel pendidikan, pengangguran, dan kondisi ekonomi.
- Hubungan antara faktor pendidikan, tingkat pengangguran, dan kriminalitas bersifat non-linear sehingga digunakan Machine Learning dan Deep Learning untuk mempelajari pola-pola kompleks tersebut.
- Dataset memiliki banyak fitur sosial-ekonomi sehingga diperlukan proses seleksi fitur dan preprocessing agar model tidak terdampak noise dan multikolinearitas.
- Belum ada analisis yang bisa mengevaluasi kinerja dari model baseline, Machine Learning, dan Deep Learning dalam memprediksi tingkat kriminalitas, sehingga perlu pengujian model untuk menentukan pendekatan yang paling optimal.

**Goals:**  
- Membangun model untuk memprediksi tingkat kriminalitas (ViolentCrimesPerPop) menggunakan baseline, Machine Learning, dan Deep Learning.
- Dapat mencapai performa prediksi yang optimal dengan memanfaatkan fitur pendidikan, pengangguran.
- Membandingkan performa tiga pendekatan model—baseline (mean/linear), Machine Learning (Random Forest/dll), dan Deep Learning (Neural Network).
- Memberikan output berupa pipeline analisa yang reproducible, mencakup preprocessing, seleksi fitur, pelatihan model, dan evaluasi.
- Memberikan wawasan tentang seberapa besar pengaruh pendidikan dan pengangguran pada tingkat kriminalitas.

---
## 📁 Struktur Folder
```
project/
│
├── data/                   # Dataset (tidak di-commit, download manual)
│
├── notebooks/              # Jupyter notebooks
│   └── ML_Project.ipynb
│
├── src/                    # Source code
│   
├── models/                 # Saved models
│   ├── model_baseline.pkl
│   ├── model_rf.pkl
│   └── model_cnn.h5
│
├── images/                 # Visualizations
│   └── r
│
├── requirements.txt        # Dependencies
├── .gitignore
└── README.md
```
---

# 3. 📊 Dataset
- **Sumber:** UCI Machine Learning Repository  
- **Jumlah Data:**  1.994 baris, 127 fitur dan 1 target 
- **Tipe:** tabular

### Fitur Utama
Dataset asli memiliki **127 fitur**, namun proyek ini hanya menggunakan **10 fitur utama** yang relevan dengan pendidikan, ekonomi, dan pengangguran.  
Berikut tabel fitur yang digunakan:

| **Nama Fitur**        | **Deskripsi** |
|-----------------------|--------------------------------------------------------------------------------------------------------------------------------|
| **PctLess9thGrade**   | Persentase penduduk dengan pendidikan kurang dari kelas 9 (indikator rendahnya pendidikan dasar).                              |
| **PctNotHSGrad**      | Persentase penduduk yang tidak lulus SMA, menggambarkan kualitas pendidikan menengah.                                         |
| **PctBSorMore**       | Persentase penduduk dengan gelar sarjana atau lebih (pendidikan tinggi).                                                      |
| **PctOccupMgmtProf**  | Penduduk yang bekerja di bidang manajemen & profesional (indikator ekonomi & kualitas pendidikan).                            |
| **PctOccupManu**      | Persentase penduduk bekerja di sektor manufaktur (indikator ekonomi & pekerjaan).                                             |
| **PctEmploy**         | Persentase penduduk yang bekerja.                                                                                             |
| **PctUnemployed**     | Tingkat pengangguran dalam populasi.                                                                                          |
| **medIncome**         | Median pendapatan rumah tangga (indikator ekonomi).                                                                           |
| **perCapInc**         | Pendapatan per kapita.                                                                                                        |
| **medFamInc**         | Median pendapatan keluarga.                                                                                                   |
| **ViolentCrimesPerPop** | **Target** – tingkat kriminalitas & kekerasan per populasi yang diprediksi oleh model.                                      |

---

# 4. 🔧 Data Preparation
- **Cleaning**: Pemeriksaan missing values, duplikasi, outliers, noise, dan range nilai. Dataset sudah bersih dan tidak memerlukan cleaning tambahan.
- **Feature Selection**: Memilih 10 fitur pendidikan & ekonomi yang paling relevan serta 1 target (`ViolentCrimesPerPop`).
- **Scaling**: Menerapkan MinMaxScaler untuk memastikan konsistensi preprocessing meskipun dataset sudah berada pada skala 0–1.
- **Splitting**: Pembagian dataset menjadi 70% train, 15% validation, dan 15% test menggunakan `train_test_split` dengan `random_state = 42`.
- **Balancing**: Tidak diperlukan karena dataset bersifat regresi (tidak memiliki kelas yang harus diseimbangkan).  

---

# 5. 🤖 Modeling
- **Model 1 – Baseline:** [linear Regression]  
- **Model 2 – Advanced ML:** [Gradient Boosting]  
- **Model 3 – Deep Learning:** [MultiLayer Perceptron]  

---

# 6. 🧪 Evaluation
**Metrik:** MSE, MAE, R2

| Model                         | MSE      | MAE      | R²       | Training Time |
|------------------------------|----------|----------|----------|----------------|
| Baseline (Linear Regression) | 0.02914  | 0.12650  | 0.39127  | ~2 detik       |
| Advanced (Gradient Boosting) | 0.02846  | 0.12311  | 0.40197  | ~2 detik       |
| Deep Learning (MLP)          | 0.02758  | 0.11699  | 0.42044  | 9 detik        |

---

# 7. 🏁 Kesimpulan

- **Model terbaik:** MLP (Deep Learning)  
- **Alasan:**  
  - Mampu mempelajari pola non-linear yang tidak ditangkap linear regression  
  - Arsitektur multilayer memungkinkan representasi fitur lebih dalam  
  - Dropout & early stopping membuat training lebih stabil dan mencegah overfitting  
  - Memberikan akurasi dan kedekatan prediksi terbaik terhadap nilai asli  

- **Insight penting:**  
  - Pendidikan rendah dan pengangguran tinggi berkorelasi kuat dengan tingginya kriminalitas  
  - Faktor sosial ekonomi menjadi fitur paling berpengaruh dalam model  
  - MLP unggul karena mampu menangkap hubungan kompleks antar fitur  
  - Gradient Boosting lebih baik daripada Linear Regression karena dapat mempelajari pola non-linear  


---

# 8. 🔮 Future Work

## 📌 Data Improvements
- [x] Mengumpulkan lebih banyak data  
- [x] Menambah variasi data  
- [x] Melakukan feature engineering lebih lanjut  

## 🤖 Model Enhancements
- [x] Mencoba arsitektur deep learning yang lebih kompleks  
- [x] Hyperparameter tuning lebih ekstensif  
- [x] Mencoba ensemble methods  
- [ ] Transfer learning dengan model yang lebih besar  

## 🚀 Deployment & System
- [x] Membuat API (Flask / FastAPI)  
- [x] Membuat web app (Streamlit / Gradio)  
- [ ] Containerization dengan Docker  
- [ ] Deploy ke cloud (Heroku / GCP / AWS)  

## ⚙️ Optimization
- [ ] Model compression (pruning / quantization)  
- [x] Improving inference speed  
- [x] Reducing model size  
t  

---

# 9. 🔁 Reproducibility
Gunakan environment:
Python Version:
- Python 3.12

Main Libraries & Versions:
- numpy==1.26.4
- pandas==2.2.2
- scikit-learn==1.5.1
- matplotlib==3.7.1
- seaborn==0.13.2

Deep Learning Framework:
- tensorflow==2.15.0
- keras (termaasuk di tensorflow)

