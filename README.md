# 🔬 Breast Cancer Tumor Diagnostic — ML Classification Project

A machine learning project that classifies breast tumors as **Malignant** or **Benign** using 30 numerical features extracted from digitized cell nucleus images. Five different classification models are compared across multiple evaluation metrics, with a focus on **Recall** as the critical metric given the medical context of false negatives.

---

## 📌 Problem Statement

Early and accurate detection of malignant breast tumors is critical — a false negative (predicting Benign when actually Malignant) can delay treatment with life-threatening consequences. This project builds and evaluates multiple ML classifiers to maximize diagnostic accuracy, with particular emphasis on minimizing missed malignant cases.

---

## 📊 Dataset

- **Source:** [Breast Cancer Wisconsin (Diagnostic) Dataset — Kaggle](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data)
- **Samples:** 569
- **Features:** 30 numerical features (mean, standard error, and worst values of 10 cell nucleus measurements)
- **Target:** Binary — Malignant (1) / Benign (0)
- **Class Distribution:** 62.7% Benign, 37.3% Malignant (mild imbalance)

---

## ⚙️ Project Pipeline

```
Data Loading → EDA → Preprocessing → Model Building → Evaluation → Hyperparameter Tuning → Feature Importance → Conclusion
```

---

## 🤖 Models Used

| Model | Paradigm |
|---|---|
| Logistic Regression | Linear |
| K-Nearest Neighbors (KNN) | Distance-based |
| Support Vector Machine (SVM) | Margin-based |
| Random Forest | Ensemble — Bagging |
| XGBoost | Ensemble — Boosting |

---

## 📈 Results

| Model | Accuracy | Recall | Precision | F1 | ROC-AUC |
|---|---|---|---|---|---|
| Logistic Regression | 0.9649 | 0.9286 | 0.9750 | 0.9512 | 0.9960 |
| **SVM** | **0.9737** | **0.9286** | **1.0000** | **0.9630** | **0.9947** |
| XGBoost | 0.9737 | 0.9286 | 1.0000 | 0.9630 | 0.9940 |
| Random Forest | 0.9737 | 0.9286 | 1.0000 | 0.9630 | 0.9929 |
| KNN | 0.9561 | 0.9048 | 0.9744 | 0.9383 | 0.9823 |

**Best Model: SVM** — 97.37% Accuracy, 100% Precision, ROC-AUC of 0.9947

---

## 🔍 Key Findings

- **Recall was prioritized** over Accuracy as the key metric — in medical diagnosis, missing a malignant tumor is far more dangerous than a false alarm
- **SVM** achieved the best balance of Accuracy, Precision and F1; tuned via GridSearchCV with 5-fold cross validation (`C=10`, `kernel=rbf`, `gamma=scale`)
- **Logistic Regression** achieved the highest ROC-AUC (0.9960) despite being the simplest model — demonstrating that simpler models can produce superior probability estimates on clean, well-structured data
- **`_worst` features dominated predictions** — `area_worst` and `concave points_worst` were the top two predictors, indicating that the most extreme outlier cells are most diagnostically significant
- Cross-validated Recall of 0.9588 dropped marginally to 0.9286 on unseen test data — confirming the model is **not overfitting**
- 3 Malignant cases were misclassified as Benign — likely borderline tumors where even clinical diagnosis is uncertain

---

## 🛠️ Tech Stack

- **Language:** Python
- **Libraries:** Pandas, NumPy, Scikit-learn, XGBoost, Matplotlib, Seaborn
- **Environment:** Google Colab

---

## 🚀 How To Run

1. Clone this repo and open `Breast_Cancer_Tumor_Diagnostic.ipynb` in [Google Colab](https://colab.research.google.com/)
2. Upload `data.csv` when prompted and run all cells sequentially

---

## ⚠️ Disclaimer

This project is for educational purposes only. The model is **not intended for actual clinical or medical diagnosis** and should not be used as a substitute for professional medical evaluation.
