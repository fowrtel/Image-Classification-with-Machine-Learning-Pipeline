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
├── source
    └── emnist_classification.ipynb   # Main Jupyter Notebook
├── emnist-letters-train.csv        # Training data (download dari Kaggle)
├── emnist-letters-test.csv       # Testing data (download dari Kaggle)
├── README.md
└── outputs/
    ├── sample_images.jpeg
    ├── hog_visualization.jpeg
    ├── confusion_matrix.jpeg
    ├── performance_comparison.jpeg
    └── predictions_sample.jpeg
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
git clone https://github.com/fowrtel/Image-Classification-with-Machine-Learning-Pipeline.git
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
| Accuracy |  0.995673 | 0.840385 |
| Precision | 0.995678 | 0.844490 |
| Recall | 0.995673 | 0.840385 |
| F1-Score | 0.995673 | 0.839171 |


**Best SVM Parameters:**
Top 10 kombinasi parameter:

| param_kernel | param_C | param_gamma | mean_test_score | std_test_score | rank_test_score |
| :--- | ---: | :--- | ---: | ---: | ---: |
| poly | 1 | scale | 0.812019 | 0.014849 | 1 |
| rbf | 10 | scale | 0.807212 | 0.015385 | 2 |
| rbf | 100 | scale | 0.806731 | 0.015020 | 3 |
| poly | 10 | scale | 0.805288 | 0.016304 | 4 |
| poly | 100 | scale | 0.805288 | 0.016304 | 4 |
| rbf | 1 | scale | 0.800481 | 0.016930 | 6 |
| rbf | 100 | auto | 0.787981 | 0.020476 | 7 |
| rbf | 10 | auto | 0.724519 | 0.021747 | 8 |
| poly | 1 | auto | 0.657212 | 0.027559 | 9 |
| poly | 10 | auto | 0.657212 | 0.027559 | 9 |

Model terbaik: `SVC(C=1, kernel='poly', probability=True, random_state=42)`

---

## 🛠️ Tech Stack

- Python 3.x
- NumPy, Pandas
- scikit-learn
- scikit-image
- Matplotlib, Seaborn
- Jupyter Notebook

---

preview : [![Open in nbviewer](https://img.shields.io/badge/Open-NBViewer-orange)](https://nbviewer.org/github/fowrtel/Image-Classification-with-Machine-Learning-Pipeline/blob/main/source/emnist_classification.ipynb)

## 📄 License

This project is for academic purposes only.
