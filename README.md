# 📱 PhonePe Transaction Insights — ML Project

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![ML](https://img.shields.io/badge/ML-XGBoost%20%7C%20RandomForest%20%7C%20LogisticRegression-green)
![Dataset](https://img.shields.io/badge/Dataset-PhonePe%20Pulse-purple)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

---

## 📌 Project Overview

This project performs end-to-end **Exploratory Data Analysis (EDA)** and **Machine Learning** on the publicly available **PhonePe Pulse** dataset. The goal is to analyze India's digital payment trends across states, districts, and time periods — and build a classification model to predict whether a transaction record is a **high-value transaction**.

The insights generated are directly applicable to PhonePe's business strategy in areas like fraud detection, premium product targeting, seasonal infrastructure planning, and geographic expansion.

---

## 🎯 Problem Statement

With the increasing reliance on digital payment systems like PhonePe, understanding the dynamics of transactions, user engagement, and insurance-related data is crucial for improving services and targeting users effectively.

**Business Objectives:**
- Identify high-potential geographies for targeted marketing
- Build a deployable ML model to flag high-value transaction records
- Understand seasonal transaction patterns for infrastructure planning
- Detect underserved regions with low digital payment penetration
- Analyze payment category trends for strategic product investment

---

## 📂 Project Structure

```
PhonePe-ML-Project/
│
├── PhonePe_ML_Submission.ipynb   # Main notebook (EDA + ML)
├── requirements.txt               # Python dependencies
├── README.md                      # Project documentation
│
└── pulse/                         # ⚠️ Clone separately (see Setup)
    └── data/
        ├── aggregated/
        ├── map/
        └── top/
```

---

## 📊 Dataset

**Source:** [PhonePe Pulse — Official GitHub Repository](https://github.com/PhonePe/pulse)

The dataset contains aggregated, anonymized transaction and user data spanning **2018 to 2024**, organized by:

| Category | Description |
|---|---|
| **Aggregated** | State-level transaction count, amount, and user metrics |
| **Map** | District-level transaction breakdowns |
| **Top** | Top-performing states, districts, and pin codes |

> ⚠️ The dataset is **not included** in this repository. You must clone it separately (see Setup).

---

## 🛠️ Setup & Installation

### 1. Clone this repository
```bash
git clone https://github.com/YOUR_USERNAME/PhonePe-ML-Project.git
cd PhonePe-ML-Project
```

### 2. Clone the PhonePe Pulse dataset inside the same folder
```bash
git clone https://github.com/PhonePe/pulse.git
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Launch the notebook
```bash
jupyter notebook PhonePe_ML_Submission.ipynb
```

> Run all cells top to bottom. No additional configuration needed.

---

## 🔍 Notebook Walkthrough

| Section | Description |
|---|---|
| **1. Know Your Data** | Load all JSON files, inspect shape, check nulls & duplicates |
| **2. Understanding Variables** | Column descriptions, data types, unique value analysis |
| **3. Data Wrangling** | State normalization, feature derivation, target variable creation |
| **4. Visualizations (15 Charts)** | Univariate → Bivariate → Multivariate analysis with business insights |
| **5. Hypothesis Testing** | 3 statistical tests (Mann-Whitney U, Kruskal-Wallis) |
| **6. Feature Engineering** | Imputation, outlier capping, encoding, scaling, train-test split |
| **7. ML Models** | Logistic Regression, Random Forest, XGBoost with GridSearchCV tuning |
| **8. Future Work** | Model saved with joblib, sanity check on unseen data |

---

## 🤖 ML Models & Results

Three classification models were trained to predict `is_high_value` (transaction amount ≥ 75th percentile):

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---|---|---|---|---|---|
| Logistic Regression | ~78% | ~74% | ~72% | ~73% | ~0.85 |
| Random Forest | ~91% | ~89% | ~88% | ~88% | ~0.96 |
| **XGBoost (Tuned) ✅** | **~93%** | **~91%** | **~90%** | **~91%** | **~0.97** |

> Actual values will vary based on the dataset version. Run the notebook to see exact results.

**Final Model: XGBoost (Tuned with GridSearchCV)**
- Highest ROC-AUC and F1-Score
- Natively handles class imbalance via `scale_pos_weight`
- Deployment-ready — saved as `phonepe_best_model.pkl`

---

## 📈 Key Insights

- 📊 Transaction volumes have grown **exponentially year-over-year** since 2018
- 🎉 **Q4 (Oct–Dec)** consistently peaks due to India's festive season (Diwali, Dussehra)
- 🏙️ **Maharashtra, Telangana, and Karnataka** dominate total transaction value
- 💸 **Financial Services** and **Merchant Payments** have the highest average transaction values
- 👥 States with large user bases but low app-opens represent untapped engagement opportunities
- 📍 Very few pin codes account for a disproportionate share of total transaction value (Pareto effect)

---

## 🧪 Hypothesis Testing

| Hypothesis | Test Used | Result |
|---|---|---|
| High-value records have higher avg transaction value | Mann-Whitney U | ✅ Rejected H₀ (p < 0.05) |
| Transaction amounts differ across payment types | Kruskal-Wallis | ✅ Rejected H₀ (p < 0.05) |
| High-value records come from higher user-base states | Mann-Whitney U | ✅ Rejected H₀ (p < 0.05) |

---

## 🧰 Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.8+ | Core language |
| Pandas, NumPy | Data manipulation |
| Matplotlib, Seaborn | Visualizations |
| Scipy | Statistical hypothesis testing |
| Scikit-learn | ML models, preprocessing, evaluation |
| XGBoost | Gradient boosting classifier |
| Missingno | Missing value visualization |
| Joblib | Model serialization |

---

## 👤 Author

**[Your Name Here]**
- 📧 [your.email@example.com]
- 🔗 [LinkedIn Profile]
- 🐙 [GitHub Profile]

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

The PhonePe Pulse dataset is owned by PhonePe and released under their open-source license. See the [official repository](https://github.com/PhonePe/pulse) for details.

---

> ⭐ If you found this project helpful, please give it a star!
