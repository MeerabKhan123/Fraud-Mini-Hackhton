# 🛡️ Fraud Detection using Machine Learning

This project is a **fraud detection system** for financial transactions, developed as part of a hackathon. Multiple machine learning models were trained and evaluated on a synthetic dataset to identify fraudulent transactions. The goal is to build a classifier that can effectively detect fraud despite severe class imbalance.

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8%2B-blue" alt="Python Version">
  <img src="https://img.shields.io/badge/License-MIT-green" alt="License">
</p>

---

## 📊 Dataset

The dataset used is **Synthetic Financial Datasets For Fraud Detection**, available on Kaggle:

🔗 [Kaggle Dataset – Synthetic Financial Datasets For Fraud Detection](https://www.kaggle.com/datasets/sriharshaeedala/financial-fraud-detection-dataset)

- **File used:** `Synthetic_Financial_datasets_log.csv`
- **Size:** 179,014 transactions
- **Features:** step, type, amount, nameOrig, oldbalanceOrg, newbalanceOrig, nameDest, oldbalanceDest, newbalanceDest, isFraud, isFlaggedFraud
- **Target variable:** `isFraud` (1 = fraudulent, 0 = legitimate)

### Class distribution (highly imbalanced):
- Non-fraud: ~99.92%
- Fraud: ~0.08%

---

## 🧠 Methodology

### 1. Exploratory Data Analysis (EDA)
- Distribution of transaction amounts
- Fraud vs Non‑Fraud counts
- Transaction types vs amounts (pie chart)
- Boxplots and histograms to understand feature behavior

### 2. Data Preprocessing
- Handling missing values (NaNs filled with 0)
- One‑hot encoding of categorical variable `type`
- Train‑test split (70% train, 30% test)

### 3. Models Evaluated
- **Logistic Regression**
- **Decision Tree** (with and without pruning)
- **Random Forest** (n_estimators=100)

> Note: SMOTE was explored but not finally applied; the final comparison used original imbalanced data.

### 4. Evaluation Metrics
Given the class imbalance, the following metrics were prioritized:
- **ROC‑AUC score**
- **Precision, Recall, F1‑score** (for minority class)
- Confusion matrix
- Accuracy (less informative)

---

## 📈 Results

| Model                    | Accuracy | Precision (fraud) | Recall (fraud) | ROC‑AUC |
|--------------------------|----------|------------------|----------------|---------|
| Logistic Regression      | 0.9994   | 0.00              | 0.00            | -       |
| Decision Tree (no prune) | 0.9985   | 0.05              | 0.10            | 0.548   |
| Random Forest            | 0.9985   | 0.05              | 0.10            | **0.691** |

- **Logistic Regression** failed to detect any fraud due to extreme class imbalance.
- **Decision Tree** detected a few fraud cases but had a low ROC‑AUC.
- **Random Forest** achieved the **highest ROC‑AUC (0.691)** and identified the most fraudulent transactions among the three.
  - ***Conclusion:*** Random Forest is the best performing model for this imbalanced fraud detection task.
