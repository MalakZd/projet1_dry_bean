# 🫘 Projet 1 — Classification Morphologique de Grains de Haricots Secs

> **Projet Data Mining — Bloc 1 réalisé par HAJAR**  
> Dataset : Dry Bean Dataset | Source : UCI Machine Learning Repository

---

## 📌 Présentation du projet

Ce projet applique une démarche complète de **Data Mining** sur le Dry Bean Dataset afin de prédire automatiquement la variété d'un grain de haricot sec à partir de ses **mesures morphologiques** extraites d'images numériques.

La classification manuelle des haricots secs est coûteuse et sujette aux erreurs humaines. Ce projet vise à automatiser ce processus grâce à des algorithmes de **classification supervisée multiclasses**.

---

## 🎯 Problématique

> **Comment prédire automatiquement la variété d'un grain de haricot sec à partir de ses caractéristiques morphologiques ?**

- **Type de tâche** : Classification supervisée multiclasses
- **Variable cible** : `Class` (7 variétés de haricots)
- **Variables explicatives** : 16 features numériques morphologiques

---

## 📂 Structure du projet

```
projet1_dry_bean/
│
├── DryBeanDataset/
│   ├── Dry_Bean_Dataset.xlsx       ← Dataset principal
│   ├── Dry_Bean_Dataset.arff       ← Format alternatif
│   └── Dry_Bean_Dataset.txt        ← Documentation
│
├── notebook_hajar.ipynb            ← Notebook Bloc 1 (sections 01–05)
├── requirements.txt                ← Dépendances Python
└── README.md                       ← Ce fichier
```

---

## 📊 Dataset

| Attribut | Valeur |
|----------|--------|
| **Source** | [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/602/dry+bean+dataset) |
| **Nombre de lignes** | 13 611 |
| **Nombre de colonnes** | 17 (16 features + 1 cible) |
| **Type de variables** | Numériques continues (sauf Class) |
| **Valeurs manquantes** | Aucune |

### 🌿 Les 7 variétés (classes)

| Variété | Nombre | Proportion |
|---------|--------|------------|
| DERMASON | 3 546 | 26.05 % |
| SIRA | 2 636 | 19.37 % |
| SEKER | 2 027 | 14.89 % |
| HOROZ | 1 928 | 14.16 % |
| CALI | 1 630 | 11.98 % |
| BARBUNYA | 1 322 | 9.71 % |
| BOMBAY | 522 | 3.84 % |

---

## 🔬 Description des variables

| Variable | Type | Description |
|----------|------|-------------|
| `Area` | int64 | Surface de la zone du grain (pixels) |
| `Perimeter` | float64 | Périmètre du contour du grain |
| `MajorAxisLength` | float64 | Longueur du grand axe de l'ellipse englobante |
| `MinorAxisLength` | float64 | Longueur du petit axe de l'ellipse englobante |
| `AspectRation` | float64 | Ratio grand axe / petit axe |
| `Eccentricity` | float64 | Excentricité de l'ellipse (0=cercle, 1=ligne) |
| `ConvexArea` | int64 | Surface de l'enveloppe convexe du grain |
| `EquivDiameter` | float64 | Diamètre d'un cercle de même surface |
| `Extent` | float64 | Ratio surface grain / surface boîte englobante |
| `Solidity` | float64 | Ratio surface grain / surface convexe |
| `roundness` | float64 | Circularité du grain (proche de 1 = rond) |
| `Compactness` | float64 | Compacité relative du grain |
| `ShapeFactor1` | float64 | Facteur de forme 1 |
| `ShapeFactor2` | float64 | Facteur de forme 2 |
| `ShapeFactor3` | float64 | Facteur de forme 3 |
| `ShapeFactor4` | float64 | Facteur de forme 4 |
| `Class` | str | ✅ **CIBLE** — Variété du haricot |

---

## 📓 Contenu du notebook — Bloc 1 (HAJAR)

### Section 01 — Import des bibliothèques
Importation de `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn` avec paramètres d'affichage configurés.

### Section 02 — Chargement du dataset
- Chargement via chemin relatif (`DryBeanDataset/Dry_Bean_Dataset.xlsx`)
- Vérification de la taille, des types et de la distribution des classes
- Preuve de la source UCI documentée

### Section 03 — Compréhension du problème
- Reformulation de la problématique
- Identification du type de tâche (classification multiclasses)
- Présentation des algorithmes envisagés

### Section 04 — Description du dataset
- Description détaillée des 16 variables morphologiques
- Identification de la variable cible `Class`
- Aperçu des premières lignes

### Section 05 — Analyse Exploratoire (EDA)
Cinq visualisations produites, toutes commentées en français :

| Figure | Contenu | Fichier |
|--------|---------|---------|
| Fig. 1 | Distribution des 7 classes | `fig_01_distribution_classes.png` |
| Fig. 2 | Histogrammes des 16 variables | `fig_02_histogrammes.png` |
| Fig. 3 | Boxplots par classe (8 variables) | `fig_03_boxplots_classe.png` |
| Fig. 4 | Matrice de corrélation | `fig_04_correlation.png` |
| Fig. 5 | Scatter plot MajorAxisLength vs Roundness | `fig_05_scatter.png` |

---

## 🔍 Principaux résultats EDA

- **Déséquilibre modéré** : DERMASON (26%) vs BOMBAY (3.8%) — géré par split stratifié
- **BOMBAY très distinct** : valeurs d'Area et Perimeter nettement supérieures aux autres
- **DERMASON et SIRA proches** : chevauchement morphologique, risque de confusion en classification
- **Fortes corrélations** entre Area, Perimeter, ConvexArea, MajorAxisLength (r > 0.95)
- **Corrélation négative** entre `roundness` et `Eccentricity` (r = -0.93)

---

## 🔄 Répartition des blocs

| Personne | Bloc | Sections | Statut |
|----------|------|----------|--------|
| **HAJAR** | Données & Exploration | 01 · 02 · 03 · 04 · 05 | ✅ Terminé |
| **MALAK** | Nettoyage & Modélisation | 06 · 07 · 08 | ⏳ En attente |
| **WISSAL** | Évaluation & Finalisation | 09 · 10 · PCA · vérif | ⏳ En attente |

---

## ⚙️ Installation

### Prérequis
- Python 3.13+
- VS Code avec extension Jupyter

### Installation des dépendances

```bash
pip install -r requirements.txt
```

### Contenu de `requirements.txt`

```
pandas>=2.0.0
numpy>=1.26.0
matplotlib>=3.7.0
seaborn>=0.12.0
scikit-learn>=1.3.0
openpyxl>=3.1.0
```

### Lancer le notebook

1. Ouvrir VS Code dans le dossier `projet1_dry_bean/`
2. Ouvrir `notebook_hajar.ipynb`
3. Sélectionner le kernel **base (Python 3.13)**
4. Cliquer sur **Run All**

---

## ✅ Checklist Bloc 1

- [x] Lien source du dataset dans le notebook
- [x] Dataset chargé via chemin relatif
- [x] Taille, types et distribution affichés
- [x] Problématique reformulée
- [x] 16 variables décrites
- [x] Distribution des classes visualisée
- [x] Histogrammes des variables produits
- [x] Boxplots par classe (8 variables)
- [x] Matrice de corrélation
- [x] Scatter plot de deux variables discriminantes
- [x] Tous les graphiques commentés en français
- [x] Notebook exécutable sans erreur jusqu'à la section 05

---

## 📝 Auteure

**HAJAR** — Bloc 1 : Données & Exploration  
Projet Data Mining | Classification morphologique de grains de haricots secs