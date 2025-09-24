# 🛡️ Fraud Detection - Machine Learning Project

A machine learning system to detect fraudulent banking transactions using unsupervised clustering (HDBSCAN) and semi-supervised learning (pseudo-label augmentation), validated with a supervised XGBoost baseline. The goal is to identify suspicious transactions to help banks reduce financial losses and strengthen security.

🚀 Live Demo: https://fraudulent-bank-transaction.streamlit.app/

---

## 📖 Project Overview

Cybercrime banking fraud is a growing threat targeting customers and financial institutions through skimming, phishing, and malware attacks. Traditional fraud detection systems often struggle with imbalanced datasets where fraudulent transactions are very rare.

To address this, we developed a semi-supervised fraud detection pipeline:

- **Unsupervised clustering** with **HDBSCAN** to discover hidden patterns
- **Pseudo-label generation** to classify suspicious vs. normal transactions
- **Supervised XGBoost baseline** to validate performance

---

## 📊 Dataset

We used the Kaggle dataset: Bank Transaction Fraud Detection by LOL Bank Pvt. Ltd.

- Kaggle: https://www.kaggle.com/datasets/marusagar/bank-transaction-fraud-detection
- Size: ~200,000 rows × 24 features
- Key features:
  - `Customer_ID`, `Transaction_ID`
  - `Transaction_Amount`, `Transaction_Type`, `Merchant_Category`
  - `Device_Type`, `Transaction_Location`
  - `Is_Fraud` (1 = Fraud, 0 = Normal)

---

## 🔎 Exploratory Data Analysis (EDA)

- Fraud cases are rare (<1%), making the dataset imbalanced
- Transaction amounts are fairly evenly distributed without extreme outliers
- No missing values detected
- Encoding applied:
  - Label Encoding: `Gender`
  - One-Hot Encoding: `Account_Type`, `Transaction_Type`, `Merchant_Category`, `Device_Type`

---

## ⚙️ Methodology

### 1) Feature Selection

- Used XGBoost feature importance
- Kept only features with contribution ≥ 2%

### 2) Experiments

- Tested clustering models: KMeans, DBSCAN, Gaussian Mixture (GMM)
- Best performance from **HDBSCAN** (Silhouette score: 0.34)

### 3) Semi-Supervised Learning (Main Approach)

1. Apply HDBSCAN to generate pseudo-labels
2. Train XGBoost on pseudo-labeled data
3. Validate performance with limited ground-truth labels

---

## ✅ Results

- HDBSCAN alone struggled to form clear fraud clusters
- Pseudo-label augmentation + XGBoost significantly improved detection
- Final model achieved strong recall for fraud detection, suitable for real-time monitoring systems

---

## 💻 Installation & Usage

### Requirements

Install dependencies:

```bash
pip install -r requirements.txt
```

Key libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `xgboost`, `hdbscan`, `streamlit`

### Running the Notebook

```bash
jupyter notebook main.ipynb
```

### Running the Streamlit App

```bash
streamlit run streamlit_app.py
```

---

## 🌐 Application

Prototype deployed on Streamlit: https://fraudulent-bank-transaction.streamlit.app/

Users can input transaction details and instantly check if a transaction is fraudulent or normal.

---

## 🗂️ Project Structure

```
Code/
├─ Bank_Transaction_Fraud_Detection.csv    # Dataset (sample)
├─ encoder.pkl                             # Trained categorical encoder
├─ scaler.pkl                              # Trained feature scaler
├─ selected_features.json                  # Selected features metadata
├─ fraud_detection_model_pseudolabel.json  # Trained XGBoost model (pseudo-labeled)
├─ main.ipynb                              # End-to-end analysis & training notebook
├─ streamlit_app.py                        # Streamlit UI for inference
├─ requirements.txt                        # Project dependencies
├─ README.md                               # This file
├─ Final Report.pdf                        # Detailed report
└─ Project Presentation.pdf                # Slide deck
```

---

## 📌 Key Takeaways

- Fraudulent transactions are rare and scattered across clusters
- Pure clustering methods are not enough — semi-supervised approaches are more effective
- The system can be integrated as a real-time fraud detection tool in banking applications

---

## 🔧 Reproducibility Notes

- Ensure consistent Python environment using the provided `requirements.txt`
- If running Streamlit locally, keep `encoder.pkl`, `scaler.pkl`, `selected_features.json`, and `fraud_detection_model_pseudolabel.json` in the same directory as `streamlit_app.py`
- If you change feature engineering, regenerate artifacts to match the app’s expectations

---

## 📝 License

This project is for academic purposes. Please cite the dataset owner and this repository when using or extending the work.
