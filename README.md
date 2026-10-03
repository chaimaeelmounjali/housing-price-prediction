# 🏡 California Housing Price Prediction (Linear Regression & EDA)

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB.svg?logo=python)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626.svg?logo=jupyter)](https://jupyter.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-F7931E.svg?logo=scikit-learn)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458.svg?logo=pandas)](https://pandas.pydata.org/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

*Bilingual README: [Français](#-version-française) | [English](#-english-version)*

---

## 🇫🇷 Version Française

### 🎯 Objectif
Le projet **California Housing Price Prediction** a pour objectif de concevoir un pipeline complet d'analyse exploratoire des données (EDA), de prétraitement rigoureux et de modélisation statistique par régression linéaire pour estimer la valeur médiane des logements en Californie (`median_house_value`). Le projet sert de référence méthodologique pour comprendre l'impact des facteurs géographiques, démographiques et économiques sur le marché immobilier.

### 🛠️ Stack Technologique
- **Langage & Environnement** : Python 3, Jupyter Notebook.
- **Manipulation & Prétraitement de Données** : Pandas, NumPy.
- **Machine Learning & Évaluation** : Scikit-Learn (`LinearRegression`, `train_test_split`, `KFold`, `cross_val_score`, `mean_squared_error`, `r2_score`, `mean_absolute_error`).
- **Visualisation & Analyse Statistique** : Matplotlib, Seaborn (distributions, matrices de corrélation, scatter plots géographiques, résidus).

### 👩‍💻 Mon Rôle & Contributions
- **Nettoyage & Préparation des Données (`Cleaning.ipynb`)** :
  - Audit approfondi du jeu de données brut (`housing.csv` avec 20 640 enregistrements).
  - Traitement des valeurs manquantes (imputation ciblée sur `total_bedrooms`).
  - Détection et gestion des valeurs aberrantes / seuils plafonds (`median_house_value` et `housing_median_age`).
  - Encodage des variables catégorielles (`ocean_proximity` via One-Hot Encoding).
  - Export d'un jeu de données nettoyé et standardisé (`housing_cleaned.csv`).
- **Modélisation & Validation Statistique (`linear_regression.ipynb`)** :
  - Découpage rigoureux Train / Validation / Test.
  - Implémentation du modèle de Régression Linéaire pas à pas avec interprétabilité des coefficients.
  - Validation croisée (*K-Fold Cross-Validation*) pour évaluer la stabilité du modèle et éviter le surapprentissage.
  - Analyse des résidus et des hypothèses statistiques de linéarité et d'homoscédasticité.
- **Documentation & Pédagogie** :
  - Rédaction d'un dictionnaire de variables explicatif et vulgarisé pour chaque attribut géographique et économique.

### 📊 Résultats & Métriques Clés
- **Évaluation multi-métriques complète** :
  - **RMSE** & **MSE** : Mesure précise de l'erreur quadratique moyenne par rapport aux prix réels.
  - **MAE** : Écart absolu moyen fournissant une interprétation monétaire directe en dollars.
  - **Score R²** : Capacité explicative significative de la variance des prix immobiliers grâce aux prédicteurs majeurs (revenu médian `median_income` et localisation géographique).
- **Reproductibilité totale** : Pipeline séquentiel propre et documenté exécutable de bout en bout.

---

## 🇬🇧 English Version

### 🎯 Objective
The **California Housing Price Prediction** project delivers an end-to-end Machine Learning and Exploratory Data Analysis (EDA) pipeline designed to predict median house prices (`median_house_value`) across California census blocks. It investigates the statistical correlation between geographical coordinates, socioeconomic variables, and housing values using rigorous preprocessing and linear regression modeling.

### 🛠️ Tech Stack
- **Language & Runtime**: Python 3, Jupyter Notebooks.
- **Data Engineering & Wrangling**: Pandas, NumPy.
- **Machine Learning & Modeling**: Scikit-Learn (`LinearRegression`, `train_test_split`, `cross_val_score`, `KFold`, evaluation metrics: MSE, RMSE, MAE, R²).
- **Visualization**: Matplotlib, Seaborn (correlation heatmaps, geographical price mapping, residual distribution plots).

### 👩‍💻 My Role & Key Contributions
- **Data Preprocessing & Cleansing (`Cleaning.ipynb`)**:
  - Conducted extensive exploratory data analysis across 20,640 records.
  - Handled missing values systematically on skewed distributions (`total_bedrooms`).
  - Addressed dataset-specific caps and outliers on target features.
  - Encoded categorical attributes (`ocean_proximity`) using One-Hot Encoding.
  - Created a reproducible clean baseline dataset (`housing_cleaned.csv`).
- **Modeling & Experimental Validation (`linear_regression.ipynb`)**:
  - Implemented train/validation/test split strategies.
  - Trained and tuned Linear Regression models, extracting feature importance weights.
  - Performed K-Fold cross-validation to guarantee generalization capacity.
  - Conducted in-depth residual diagnostics to validate regression assumptions.
- **Data Dictionary**:
  - Authored a descriptive breakdown of each variable (geospatial coordinates, population density, room ratios).

### 📊 Key Results & Impact
- **Comprehensive Benchmark**: Clear performance baseline evaluated across MAE, RMSE, and R² metrics.
- **Strongest Predictive Drivers**: Identified `median_income` and spatial proximity to high-value coastal areas as the primary factors governing valuation.
- **Turnkey Reproducibility**: Self-contained notebooks ready for experimentation and pedagogical reuse.

---

### 📂 Repository Structure / Structure du Projet
```text
├── Cleaning.ipynb           # Data cleaning, outlier handling & encoding
├── linear_regression.ipynb  # Step-by-step linear regression & validation
├── housing.csv              # Raw California housing dataset
├── housing_cleaned.csv      # Cleansed & transformed dataset
└── README.md                # Project documentation
```

### 🚀 Usage / Exécution
```bash
# Clone the repository
git clone git@github.com:chaimaeelmounjali/housing-price-prediction.git
cd housing-price-prediction

# Launch Jupyter
jupyter notebook
# Open Cleaning.ipynb, then linear_regression.ipynb
```
