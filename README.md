# 🔤 EMNIST Letter Classification — HOG + SVM Pipeline

**Midterm Project — Computer Vision**  

---

## 📌 Project Overview

Proyek ini mengimplementasikan pipeline klasifikasi gambar untuk mengenali **26 huruf (A-Z)** menggunakan dataset **EMNIST Letters**. Pipeline terdiri dari:

1. **Dataset Preparation** — sampling seimbang, shuffle, train/test split
2. **HOG Feature Extraction** — ekstraksi fitur histogram of oriented gradients
3. **SVM Classification** — klasifikasi dengan support vector machine + grid search
4. **Evaluation** — accuracy, precision, recall, F1-score

---

## 📂 Repository Structure

```
├── emnist_classification.ipynb   # Main Jupyter Notebook
├── emnist-letters-train.csv      # Training data (download dari Kaggle)
├── emnist-letters-test.csv       # Testing data (download dari Kaggle)
├── README.md
└── outputs/
    ├── sample_images.png
    ├── hog_visualization.png
    ├── confusion_matrix.png
    ├── performance_comparison.png
    └── predictions_sample.png
```

> ⚠️ File CSV tidak di-upload ke repo karena ukurannya besar. Download sendiri dari Kaggle (link di bawah).

---

## 📊 Dataset

- **Source:** [EMNIST Dataset — Kaggle](https://www.kaggle.com/datasets/crawford/emnist/data)
- **Subset yang digunakan:** EMNIST Letters
- **Total samples:** 2.600 (100 sampel per kelas × 26 kelas)
- **Format:** CSV — kolom pertama = label, 784 kolom berikutnya = pixel value (28×28)
- **Kelas:** 26 huruf A–Z (uppercase & lowercase digabung)

---

## ⚙️ Pipeline Detail

### 1. Dataset Preparation
- Load dari CSV (`emnist-letters-train.csv` + `emnist-letters-test.csv`)
- Sampling seimbang: 100 sampel per kelas
- Shuffle dengan `random_state=42`
- Split: **80% training / 20% testing** (stratified)

### 2. HOG Feature Extraction

| Parameter | Default | Used |
|---|---|---|
| `orientations` | 9 | **12** |
| `pixels_per_cell` | (8, 8) | **(7, 7)** |
| `cells_per_block` | (3, 3) | **(2, 2)** |
| `block_norm` | L2-Hys | L2-Hys |
| `transform_sqrt` | False | **True** |

### 3. SVM + Grid Search

Parameter yang dicari dengan Grid Search (5-fold CV):

| Parameter | Values Tried |
|---|---|
| `kernel` | rbf, poly |
| `C` | 1, 10, 100 |
| `gamma` | scale, auto |

---

## 🚀 How to Run

### 1. Clone repo

```bash
git clone https://github.com/<username>/<repo-name>.git
cd <repo-name>
```

### 2. Install dependencies

```bash
pip install numpy pandas matplotlib seaborn scikit-learn scikit-image jupyter
```

### 3. Download dataset

Download dari [Kaggle EMNIST](https://www.kaggle.com/datasets/crawford/emnist/data) dan letakkan file berikut di folder yang sama dengan notebook:

```
emnist-letters-train.csv
emnist-letters-test.csv
```

### 4. Jalankan notebook

```bash
jupyter notebook emnist_classification.ipynb
```

Pilih **Cell → Run All**.

---

## 📈 Results

| Metric | Train | Test |
|---|---|---|
| Accuracy | - | - |
| Precision | - | - |
| Recall | - | - |
| F1-Score | - | - |

> Isi tabel ini setelah menjalankan notebook.

**Best SVM Parameters:** *(isi setelah grid search selesai)*

---

## 🛠️ Tech Stack

- Python 3.x
- NumPy, Pandas
- scikit-learn
- scikit-image
- Matplotlib, Seaborn
- Jupyter Notebook

---

## 📄 License

This project is for academic purposes only.
