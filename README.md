# 💳 AI-Driven Financial Fraud & Anomaly Detection Platform

![Python](https://img.shields.io/badge/Python-3.9-blue?style=flat&logo=python)
![Flask](https://img.shields.io/badge/Flask-Web_App-black?style=flat&logo=flask)
![XGBoost](https://img.shields.io/badge/XGBoost-Ensemble-orange?style=flat)
![Accuracy](https://img.shields.io/badge/Accuracy-99.51%25-brightgreen?style=flat)
![ROC--AUC](https://img.shields.io/badge/ROC--AUC-0.983-blue?style=flat)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)

> A production-grade ML web application that detects fraudulent credit card transactions using a **weighted ensemble of 3 models** — Logistic Regression, Random Forest, and XGBoost — deployed on Render with secure user authentication.

---

## 🌐 Live Demo

🔗 **[Try it live →]((https://fraud-lc6b.onrender.com/))** *(replace with your actual Render URL)*

---

## ✨ Features

- 🔐 Secure multi-user authentication (signup / login / logout)
- 📤 Upload any CSV of transactions for bulk real-time prediction
- 🤖 Weighted ensemble: **LR (20%) + RF (20%) + XGBoost (60%)**
- 🟢 3-tier probabilistic risk classification:
  - **LEGIT** — Fraud probability < 0.30
  - **UNDER REVIEW** — 0.30 to 0.65
  - **FRAUD** — > 0.65
- 📊 Live analytics dashboard with transaction summary cards
- ☁️ Cloud-deployed on Render with SQLite user management

---

## 📊 Model Performance

| Metric | Score |
|--------|-------|
| Testing Accuracy | **99.51%** |
| ROC-AUC Score | **0.983** |
| Recall | 81.0% |
| Precision | 94.19% |

> Dataset: [Kaggle Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) — 284,807 real-world transactions, 492 fraud cases.

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Backend | Python, Flask, Flask-Login, SQLAlchemy |
| ML Models | Logistic Regression, Random Forest, XGBoost |
| Data Processing | pandas, scikit-learn, NumPy |
| Frontend | HTML5, Bootstrap 5 |
| Database | SQLite (via SQLAlchemy) |
| Deployment | Render (cloud) |

---

## 🚀 Getting Started

### Prerequisites
```
Python 3.9+
pip
```

### Installation
```bash
# Clone the repo
git clone https://github.com/NikhilDunnala/fraud.git
cd fraud

# Install dependencies
pip install -r requirements.txt

# Run the app
python app.py
```

App will be running at `http://localhost:5000`

---

## 📂 Project Structure

```
fraud/
├── app.py                  # Main Flask application (routes, auth, prediction)
├── templates/
│   ├── login.html          # Login page
│   ├── signup.html         # Registration page
│   ├── index.html          # Dashboard / CSV upload
│   └── result.html         # Prediction results dashboard
├── lr_model.pkl            # Trained Logistic Regression model
├── rf_model.pkl            # Trained Random Forest model
├── xgb_model.pkl           # Trained XGBoost model
├── scaler.pkl              # Feature scaler (Time + Amount)
├── requirements.txt        # Python dependencies
└── runtime.txt             # Python version for Render
```

---

## 🧠 How It Works

1. **User uploads** a CSV file with columns: `Time, V1–V28, Amount`
2. `Time` and `Amount` are scaled using the pre-trained scaler
3. All 3 models run inference; probabilities are **weighted averaged**
4. Each transaction is classified into one of 3 risk tiers
5. Results are displayed in an interactive dashboard table

### Ensemble Formula
```
Final Probability = (0.2 × LR_prob) + (0.2 × RF_prob) + (0.6 × XGB_prob)
```

---

## 🔬 ML Details

- **Class imbalance** handled via random under-sampling (492 fraud vs 5,000 legitimate)
- **Hyperparameter tuning** via GridSearchCV
- **Features**: Time, V1–V28 (PCA-transformed), Amount
- All 3 models trained with stratified splits for fair evaluation

---


## 👨‍💻 Author

**Nikhil Dunnala** — [GitHub](https://github.com/NikhilDunnala) · [LinkedIn](https://linkedin.com/in/nikhildunnala)

*B.Tech CSE @ VIT-AP University, 2026*
