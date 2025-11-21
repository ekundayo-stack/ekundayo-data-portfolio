# 🍷 Wine Quality Classification with Machine Learning

This project uses XGBoost and LightGBM machine learning to predict winary location based on quality and physicochemical properties (e.g. acidity, ash, magnesium). It was built using a Kaggle dataset and focuses on model comparison, interpretability, and practical recommendations for application of models on classification tasks.

---

## 🎯 Project Motivation

I undertook this project to:

- Practice end-to-end **classification modelling** on a real dataset.
- Strengthen my skills in **EDA, feature engineering, and model evaluation**.
- Build a clear, portfolio-ready example of how I turn raw data into **relevant insights**.

---

## 📊 Dataset

- **Source:** Kaggle – Wine Quality dataset  
- **Observations:** ~ 179 samples and 14 columns 
- **Features:** physicochemical measurements such as:
  - malic_acid, ash, alcalinity_of_ash
  - magnesium, total_phenols, flavanoids
  - nonflavanoid_phenols, proanthocyanins, color_intensity
  - hue, od280/od315_of_diluted_wines, proline

- **Target:** Winery Location (converted into a classification problem: e.g. *0*, *1*, *2* locations).

Any preprocessing steps:
- Handled missing values (if any)
- Removed/treated outliers
- Scaled numerical features (e.g. StandardScaler / MinMaxScaler)
- Encoded target classes

---

## 🧠 Methods & Models

Key steps:

1. **Exploratory Data Analysis (EDA)**
   - Distribution plots, correlations, class balance
   - Relationship between alcohol, acidity and quality

2. **Feature Engineering**
   - Optional: created combined features (e.g. acidity ratios)
   - Dealt with class imbalance (e.g. class weighting / resampling)

3. **Models Tested**
   - Tree-based: XGBoost / Gradient Boosting, Light_GBM

4. **Evaluation Metrics**
   - Accuracy, Precision, Recall, F1-score
   - Confusion matrix
   - Cross-validation scores

---

## 🏆 Results

- Best model: **[XGBoost]**
- Test Accuracy: **97.2%**
- Macro F1-score: **0.97**
- Key insights:
  - [Example] Higher alcohol and balanced acidity are strong indicators of higher-quality wine.
  - [Example] Model performance improved after handling class imbalance and tuning hyperparameters.

You can find the detailed implementation and analysis in the notebook:

👉 `notebook/wine_quality_classification.ipynb`

Important visuals are saved in:

👉 `visuals/` (confusion matrices, feature importance, EDA plots)

---

