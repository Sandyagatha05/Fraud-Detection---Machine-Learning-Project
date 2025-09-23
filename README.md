# 🛡️Fraud-Detection---Machine-Learning-Project

This project aims to build a fraud detection system for banking transactions using a combination of unsupervised learning (clustering) and semi-supervised learning (pseudo-label augmentation). The system can automatically identify suspicious transactions, helping banks reduce financial losses and strengthen security.

**🚀 Live Demo**: [Fraudulent Bank Transaction App](https://fraudulent-bank-transaction.streamlit.app/)

**📖 Project Overview**

Cybercrime banking fraud is a growing threat targeting customers and financial institutions through skimming, phishing, and malware attacks. Traditional fraud detection systems often struggle with imbalanced datasets where fraudulent transactions are very rare.

To address this, we developed a semi-supervised fraud detection pipeline:

-Unsupervised clustering with HDBSCAN to discover hidden patterns.

-Pseudo-label generation to classify suspicious vs. normal transactions.

-Supervised XGBoost baseline to validate performance.

**📊 Dataset**

We used the Bank Transaction Fraud Detection Dataset
 from LOL Bank Pvt. Ltd.

Size: ~200,000 rows × 24 features

Key Features:

-Customer_ID, Transaction_ID

-Transaction_Amount, Transaction_Type, Merchant_Category

-Device_Type, Transaction_Location

-Is_Fraud (1 = Fraud, 0 = Normal)

**🔎 Exploratory Data Analysis (EDA)**

-Fraud cases are rare (<1%), making the dataset imbalanced.

-Transaction amounts are fairly evenly distributed without extreme outliers.

-No missing values detected.

**-Encoding applied:**

-Label Encoding: Gender

-One-Hot Encoding: Account type, transaction type, merchant category, device type

**⚙️ Methodology**
1. Feature Selection

-Used XGBoost feature importance

-Kept only features with contribution ≥ 2%

2. Experiments

-Tested clustering models: KMeans, DBSCAN, GMM

-Best performance from HDBSCAN (Silhouette score: 0.34)

3. Semi-Supervised Learning (Main Approach)

-Apply HDBSCAN to generate pseudo-labels.

-Train XGBoost on pseudo-labeled data.

-Validate performance with limited ground-truth labels.

**✅ Results**

-HDBSCAN alone struggled to form clear fraud clusters.

-Pseudo-label augmentation + XGBoost significantly improved detection.

-The final model achieved strong recall for fraud detection, making it suitable for real-time monitoring systems.

**💻 Installation & Usage**
**Requirements**

Make sure you have the following installed:

**pip install -r requirements.txt**


Key dependencies:

-numpy, pandas, matplotlib, seaborn

-scikit-learn

-xgboost

-hdbscan

-streamlit

Running the Notebook
jupyter notebook main.ipynb

Running the Streamlit App
streamlit run app.py

**🌐 Application**

We deployed a prototype on Streamlit:
👉 [Fraudulent Bank Transaction App](https://fraudulent-bank-transaction.streamlit.app/)

Users can input transaction details and instantly check if a transaction is fraudulent or normal.

**📌 Key Takeaways**

-Fraudulent transactions are rare and scattered across clusters.

-Pure clustering methods are not enough — semi-supervised approaches are more effective.

-The system can be integrated as a real-time fraud detection tool in banking applications.
