# 💳 Financial Fraud Analysis

This project presents a complete machine learning pipeline to detect fraudulent transactions in a large-scale financial dataset (6M+ records). It includes exploratory data analysis (EDA), data cleaning, feature engineering, and model training using Logistic Regression, Decision Tree, and Random Forest.
 

---

## 📂 Dataset

- 📦 Size: ~6.3 million rows, 11 columns  
- 📥 Source: [Google Drive Link](https://drive.google.com/uc?id=1VNpyNkGxHdskfdTNRSjjyNa5qC9u0JyV) (via `gdown`)
- Columns include:
  - `step`, `type`, `amount`, `oldbalanceOrg`, `newbalanceOrig`, `oldbalanceDest`, `newbalanceDest`, `isFraud`, etc.

---

## 🎯 Objectives

- Identify patterns in transaction data that indicate fraud.
- Handle class imbalance and outliers.
- Build robust models to predict fraudulent behavior.
- Evaluate models using F1-score, ROC AUC, and feature importance.

---

## 📊 Exploratory Data Analysis

- Visualized transaction types and their fraud distribution.
- Identified imbalances: ~0.13% transactions are fraudulent.
- Detected that most frauds occur in `TRANSFER` and `CASH_OUT` types.
- Uncovered balance anomalies and transaction amount outliers.

---

## 🧠 Feature Engineering

- Dropped non-informative features
- One-hot encoded `type`
- Engineered features:
  - `balanceDiffOrig`: sender balance change
  - `isOutlier_amount`: creat new feature
  - `amountMismatch`: balance mismatch flag

---

## 🤖 Modeling

### ✅ Logistic Regression
- Very high recall (~99%) but low precision due to imbalance.
- Good baseline, poor precision (many false positives).

### 🌲 Decision Tree
- Slightly improved performance with `max_depth=6`.

### 🏆 Random Forest
- Best performance:
  - **Precision:** 85.4%
  - **Recall:** 54.3%
  - **F1 Score:** ~0.66
  - **ROC AUC:** 0.9477
- Cross-validation confirmed consistency.

---

## 📈 Results

| Model              | Precision | Recall | F1 Score | ROC AUC |
|-------------------|-----------|--------|----------|---------|
| Logistic Regression | 0.0527   | 0.9955 | 0.1000   | ~0.86   |
| Decision Tree       | 0.0528   | 0.9963 | 0.1003   | ~0.88   |
| **Random Forest**   | **0.8543** | **0.5426** | **0.6637** | **0.9477** |

---

## 🧾 Conclusion

- Random Forest is most effective in balancing precision and recall.
- Fraud detection is heavily imbalanced careful feature engineering, anomaly detection, and class weighting are essential.
- This pipeline provides a solid baseline for real-time fraud alert systems.
 
