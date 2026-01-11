# 🕵️‍♂️ Fraud Detection in Financial Transactions

## 📌 Project Overview

This project focuses on building a **machine learning model to proactively detect fraudulent financial transactions** using a large-scale transactional dataset.
The solution combines **exploratory data analysis, feature engineering, imbalance handling, and ensemble learning** to achieve high fraud detection performance with strong interpretability.

---

## 📊 Dataset Description

* **Total Records:** 6,362,620
* **Features:** 11 original + engineered features
* **Target Variable:** `isFraud`
* **Time Span:** 30 days (1 step = 1 hour)
* 
## 📂 Dataset
Due to GitHub file size limits, the full dataset is not included in this repository.

- Sample dataset: `fraud_sample.csv`
- Full dataset source: [https://www.kaggle.com/datasets/chitwanmanchanda/fraudulent-transactions-data/data]

### Key Columns

* `step` – Time unit (hour)
* `type` – Transaction type (CASH_OUT, TRANSFER, etc.)
* `amount` – Transaction amount
* `oldbalanceOrg`, `newbalanceOrig` – Sender balances
* `oldbalanceDest`, `newbalanceDest` – Receiver balances
* `isFraud` – Fraud label
* `isFlaggedFraud` – Rule-based fraud flag

---

## 🧹 Data Preprocessing

* Verified **no missing values**
* Preserved outliers as fraud often occurs in extreme values
* Removed identifier columns (`nameOrig`, `nameDest`)
* One-hot encoded transaction types
* Handled **severe class imbalance (0.13% fraud)** using **SMOTE**

---

## 🛠 Feature Engineering

Custom features were created to capture fraud behavior:

* `errorBalanceOrig` – Sender balance inconsistency
* `errorBalanceDest` – Receiver balance inconsistency
* `isOrigEmpty` – Sender account drained
* `isDestEmpty` – New or inactive destination account

These features significantly improved model performance and interpretability.

---

## 🤖 Model Used

### **Random Forest Classifier**

Chosen for:

* Strong performance on non-linear data
* Robustness to outliers
* Built-in feature importance
* Suitability for imbalanced classification

**Training Strategy**

* Stratified train-test split (70/30)
* SMOTE applied **only on training data** to avoid data leakage

---

## 📈 Model Performance

| Metric    | Fraud Class |
| --------- | ----------- |
| Precision | 0.99        |
| Recall    | 1.00        |
| F1-score  | 0.99        |
| ROC-AUC   | 0.9995      |

**Confusion Matrix Summary**

* Missed frauds: **9**
* False positives: **30**

---

## 🔍 Key Fraud Indicators

Top predictors identified by the model:

1. `errorBalanceOrig`
2. `oldbalanceOrg`
3. `amount`
4. `isOrigEmpty`
5. `type_TRANSFER`

These features align strongly with real-world fraud patterns such as account draining and large fund transfers.

---

## 🛡 Fraud Prevention Recommendations

* Real-time transaction monitoring
* Dynamic transaction limits
* Multi-factor authentication for high-value transfers
* Behavioral profiling
* Velocity checks for rapid transactions

---

## 📁 Project Structure

```
fraud-detection/
│
├── fraud_detection.ipynb
├── README.md
├── requirements.txt
└── fraud_sample.csv
```

---

## 🚀 How to Run

```bash
pip install -r requirements.txt
jupyter notebook
```

---

## 📌 Conclusion

This project demonstrates an **end-to-end fraud detection pipeline** combining strong ML performance with actionable business insights.
The model is both **accurate and interpretable**, making it suitable for real-world deployment.

---

## 👤 Author

**Arvind Kumar**
B.Tech CSE (AI & ML)
Aspiring Machine Learning Engineer



