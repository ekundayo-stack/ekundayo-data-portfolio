🍷 Wine Quality Classification Using Machine Learning

This project applies supervised machine learning techniques to classify wines into three quality categories based on their physicochemical properties. It explores end-to-end model development — from exploratory data analysis to hyperparameter tuning, feature importance evaluation, and overfitting mitigation.

The dataset is a small Kaggle dataset (178 samples), making this a strong demonstration of careful model validation and the challenges of training on limited data.

🎯 Project Motivation

I undertook this project to strengthen my skills in:

Supervised classification modelling

Data preprocessing, EDA, and outlier analysis

Comparing multiple algorithms (LightGBM, XGBoost)

Hyperparameter tuning with GridSearchCV + StratifiedKFold

Model interpretability through feature importance

Detecting and mitigating overfitting

This project adds a clean, structured classification example to my GitHub portfolio.

📂 Repository Structure
wine-quality-classification/
│── dataset/
│── notebook/
│── visuals/
│── models/ (optional)
│── README.md

📊 Dataset Overview

Rows: 178

Features: 13 physicochemical properties

Target: 3 wine classes (0, 1, 2)

Most common class: Class 1 (39.89%)

All columns contain valid, non-missing values. Outliers were examined using IQR and visualized through boxplots.

Example features:

Alcohol

Malic Acid

Proline

Color Intensity

Flavanoids

Hue

OD280/OD315 of diluted wines

🔎 Exploratory Data Analysis (EDA)

The notebook includes:

Summary statistics (df.describe())

Class distribution

Distribution plots (histograms + KDE)

Outlier detection using IQR

Boxplots to highlight skewness

Correlation insights

These analyses revealed that variables like color_intensity, proline, and flavanoids show strong separation patterns across the target classes.

🧠 Modelling Approach
Train-Test Split

80/20 split

Stratified to preserve class balance

Models Trained

XGBoost (XGBClassifier)

LightGBM (LGBMClassifier)

Performance (Before Tuning)
Model	Accuracy
XGBoost	97.22%
LightGBM	100%

The perfect accuracy suggested likely overfitting, motivating further investigation.

⚙️ Hyperparameter Tuning (LightGBM)

Performed using:

GridSearchCV

5-fold StratifiedKFold

729 hyperparameter combinations

Best Parameters Identified:

learning_rate: 0.05
max_depth: 5
n_estimators: 100
num_leaves: 20
reg_alpha: 0
reg_lambda: 0


Best CV Accuracy: 97.91%
Test Accuracy after tuning: 100%

Despite tuning, 100% test accuracy still indicates likely overfitting due to the very small dataset size.

🔍 Feature Importance Analysis
LightGBM – Top Features
Feature	Importance
color_intensity	306
proline	235
flavanoids	198
alcohol	182
od280/od315_of_diluted_wines	126
XGBoost – Top Features
Feature	Importance
flavanoids	0.2118
color_intensity	0.1809
proline	0.1747
od280/od315_of_diluted_wines	0.1651
magnesium	0.1109

Consistent predictors across both models:

Color Intensity

Proline

Flavanoids

These features are reliable indicators of wine class.

📈 Visuals Included

Place these in your /visuals folder:

Distribution histograms

Boxplots

Correlation heatmap

Confusion matrices (LightGBM + XGBoost)

Feature importance bar charts

Example placeholders to reference in README:

![Confusion Matrix – LightGBM](./visuals/lgbm_confusion_matrix.png)
![Feature Importances – XGBoost](./visuals/xgb_feature_importance.png)

⚠️ Overfitting Analysis & Mitigation Strategies

The small dataset size (178 samples) makes perfect accuracy suspicious.
Overfitting is likely even with stratification and tuning.

Strategies Used

5-fold Stratified Cross-Validation

Regularization (L1/L2)

Model complexity limits (max_depth, num_leaves)

Hyperparameter tuning grid search

Further Strategies Recommended

Nested cross-validation for more reliable evaluation

Stronger regularization for XGBoost & LightGBM

Simpler model architectures

Feature selection guided by importance scores

Increasing training data, which is the most reliable fix

📝 Summary of Key Findings
🔹 Critical Features

Both models identified color_intensity, proline, and flavanoids as robust, high-signal predictors.

🔹 Model Performance

LightGBM achieved 100% accuracy after tuning

XGBoost reached 97.22%

Perfect results on small datasets require caution — high risk of overfitting

🔹 Next Steps

Implement nested CV

Explore simpler models

Engineer additional features

Collect or augment data

📘 Notebook & Files

Full notebook: notebook/winedataset.ipynb

All plots in: visuals/

Dataset in: dataset/wine_dataset.csv
