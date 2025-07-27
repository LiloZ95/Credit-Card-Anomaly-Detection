# 💳 Credit Card Anomaly Detection  
**Zaka & BLACKBOX Technical Challenge**  
**Author:** Khalil Kurdi

---

## 🧠 Overview

This project tackles the detection of fraudulent credit card transactions using unsupervised machine learning models, built with the realities of highly imbalanced data in mind.

We explored and compared two models:

- 🟡 **Isolation Forest**: A fast, tree-based approach ideal for quick anomaly detection.  
- 🟢 **Autoencoder (Bonus)**: A neural network trained to reconstruct normal transactions, flagging outliers based on reconstruction error.

---

## 📁 Dataset

- **Source:** [Kaggle - Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)  
- **Transactions:** 284,807  
- **Fraudulent Cases:** 492 (≈0.17%)

---

## 🧭 Project Approach

Given the lack of labeled fraud data in most real-world scenarios, we focused on unsupervised anomaly detection:

- **Baseline:** Isolation Forest was used to define a lightweight, tunable baseline.  
- **Deep Dive:** We then trained an Autoencoder on only non-fraudulent transactions, leveraging reconstruction error to identify anomalies.  
- **Evaluation:** Models were assessed using precision, recall, F1-score, and ROC AUC to reflect both detection quality and class imbalance challenges.  
- **Visualization:** PCA was used to reduce dimensionality and interpret anomaly predictions visually.

---

## 🧪 Methods in Detail

### 1. Isolation Forest
- Trained on the full dataset  
- Tested using `contamination=0.005`  
- Evaluated via confusion matrix, precision, recall, F1-score, and ROC AUC  

### 2. Autoencoder (Bonus Model)
- Trained on 50,000 non-fraudulent transactions  
- Tested against a mixed dataset (50k normal + all frauds)  
- Anomalies detected using reconstruction error  
- Threshold set at the 95th percentile of Mean Squared Error (MSE)  

---

## 📊 Results Summary

| Model           | Precision | Recall | ROC AUC | Notes                                 |
|----------------|-----------|--------|---------|----------------------------------------|
| Isolation Forest | 0.15      | 0.45   | 0.72    | Simple and fast, but limited recall     |
| Autoencoder      | 0.16      | 0.84   | 0.94    | Strong recall and ROC AUC; best performer |

✅ **Takeaway:** The Autoencoder significantly outperformed Isolation Forest, especially in recall—making it more suitable for fraud detection where missing fraud is costly.

---

## 📈 Visualizations

- **ROC Curves:** Plotted for both models with side-by-side comparison  
- **Anomaly Map:** 2D PCA projection of 30,000 transactions with anomaly predictions overlaid  

📍 See notebook sections: `"ROC Curve - Model Comparison"` and `"PCA Projection of Transactions"` for visuals

---

## 🚧 Key Challenges

- **Extreme class imbalance:** Less than 0.2% of transactions are fraud, making accuracy a poor metric  
- **Model tuning:** Isolation Forest required fine-tuning of contamination to balance false positives and missed frauds  
- **Training scale:** Autoencoder performance improved notably with more training data (from 5k to 50k samples)  
- **Visualizing high-dimensional data:** Required careful use of PCA for effective anomaly interpretation

---

## 📦 Requirements

1. Install dependencies:
   ```bash
   pip install pandas scikit-learn matplotlib seaborn plotly tensorflow

2. Download dataset via Kaggle API (`kaggle.json` required in notebook)

---

## 🧠 Relevance to BLACKBOX AI

This project demonstrates how unsupervised learning can uncover hidden anomalies and improve decision-making — directly aligning with BLACKBOX AI’s mission.

### 🔑 Key Takeaways

- Unsupervised modeling scales well in environments with minimal labeled data  
- Autoencoders effectively detect rare behaviors and outliers  
- Visual analytics help interpret black-box predictions for stakeholders  

### 🚀 Potential Extensions

- Monitoring API usage patterns  
- Detecting abnormal developer activity  
- Securing systems with unsupervised log analysis
   
