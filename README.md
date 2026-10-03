# Housing Price Prediction

Projet de prédiction du prix médian des logements en Californie à partir de variables socio‑économiques et géographiques, avec un pipeline en deux notebooks : nettoyage des données puis régression linéaire.

## 1) Objectif

Prédire `median_house_value` (valeur médiane des maisons) avec un modèle de régression linéaire entraîné sur des données nettoyées.

## 2) Données

### Fichiers CSV
- `housing.csv` : jeu de données brut (`20640` lignes, `10` colonnes)
- `housing_cleaned.csv` : jeu nettoyé produit par `Cleaning.ipynb` (`16683` lignes, `10` colonnes)

### Variables présentes
- Numériques : `longitude`, `latitude`, `housing_median_age`, `total_rooms`, `total_bedrooms`, `population`, `households`, `median_income`, `median_house_value`
- Catégorielle : `ocean_proximity`

Variable cible : `median_house_value`.

## 3) Nettoyage des données (`Cleaning.ipynb`)

Étapes effectivement réalisées dans le notebook :
1. Chargement et inspection (`head`, `tail`, `info`, types).
2. Valeurs manquantes : `207` valeurs manquantes dans `total_bedrooms` (jeu brut), remplacées par la médiane de la colonne.
3. Doublons : vérification (`0` doublon détecté).
4. Détection visuelle des outliers via boxplots.
5. Traitement des outliers par règle IQR, appliquée successivement sur les colonnes numériques.
6. Normalisation de `ocean_proximity` : passage en minuscules, suppression des espaces, corrections de libellés.
7. Export du fichier nettoyé vers `housing_cleaned.csv`.

Répartition finale de `ocean_proximity` (nettoyé) :
- `<1h ocean` : 7151
- `inland` : 5647
- `near ocean` : 2095
- `near bay` : 1785
- `island` : 5

## 4) EDA (exploration)

L’exploration visible dans les notebooks couvre principalement :
- structure et statistiques descriptives du dataset,
- contrôle des valeurs manquantes et des doublons,
- visualisation des distributions/outliers (boxplots),
- distribution des catégories de `ocean_proximity`.

## 5) Modélisation (`linear_regression.ipynb`)

Pipeline observé dans le notebook :
1. Chargement de `housing_cleaned.csv`.
2. Séparation cible/features (`y = median_house_value`, `X = autres colonnes`).
3. Encodage de `ocean_proximity` avec `pd.get_dummies(drop_first=True)`.
4. Split des données :
   - train : `(11678, 12)`
   - validation : `(2502, 12)`
   - test : `(2503, 12)`
5. Standardisation des features (`StandardScaler`).
6. Implémentation pas à pas d’une régression linéaire (prédiction, MSE, gradients, descente de gradient).
7. Évaluation avec MSE, RMSE, MAE, R² + validation croisée 5-fold.

## 6) Métriques et résultats (valeurs affichées dans le notebook)

### Performances du modèle
- **Train**: MSE `3215697397.14` | RMSE `56707.12` | MAE `42152.67` | R² `0.6119`
- **Validation**: MSE `3285213724.71` | RMSE `57316.78` | MAE `42585.39` | R² `0.6122`
- **Test**: MSE `3180215067.59` | RMSE `56393.40` | MAE `42587.86` | R² `0.6226`

### Validation croisée (5 folds)
- Folds (MSE) : `3301316291.97`, `3069116827.93`, `3267185374.69`, `3395567530.62`, `3110019269.75`
- Mean MSE : `3228641058.99`
- Std MSE : `121779234.58`
- Mean RMSE : `56821.13`

### Interprétation affichée
Le notebook met en avant :
- plus forte influence positive : `median_income`
- plus forte influence négative : `population`

## 7) Rôle de l’auteur dans ce projet

D’après les notebooks présents, l’auteur a construit un workflow complet de bout en bout :
- nettoyage/préparation des données,
- exploration et contrôles qualité,
- entraînement d’un modèle de régression linéaire (implémentation pédagogique par gradient descent),
- évaluation et interprétation des résultats.

## 8) Structure du repository

```text
.
├── Cleaning.ipynb
├── linear_regression.ipynb
├── housing.csv
├── housing_cleaned.csv
└── README.md
```

## 9) Reproduire le projet

1. Ouvrir `Cleaning.ipynb`.
2. Exécuter toutes les cellules pour produire/mettre à jour `housing_cleaned.csv`.
3. Ouvrir `linear_regression.ipynb`.
4. Exécuter toutes les cellules dans l’ordre pour entraîner le modèle et retrouver les métriques ci-dessus.

Bibliothèques utilisées dans les notebooks : `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`.

## 10) Limites et pistes d’amélioration

### Limites
- Modèle linéaire : capacité limitée pour des relations non linéaires.
- Traitement IQR appliqué séquentiellement : réduction importante du volume de données (20640 → 16683).
- Peu de feature engineering avancé (interactions, transformations non linéaires, etc.).

### Pistes d’amélioration
- Comparer avec des modèles non linéaires (Random Forest, Gradient Boosting, XGBoost).
- Ajouter un pipeline reproductible (`Pipeline` sklearn) avec validation croisée systématique.
- Tester des stratégies alternatives de gestion des outliers et d’ingénierie de variables.
- Ajouter un suivi d’expériences et une séparation claire des scripts/notebooks de production.
