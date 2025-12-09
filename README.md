# 🎯 Analyse en Composantes Principales (ACP) & Clustering K-Means  
### Projet de segmentation des clients — Dataset Mall_Customers

Ce projet a pour objectif d’analyser le comportement des clients d’un centre commercial en utilisant  
**deux techniques d’apprentissage non supervisé :**

- **Analyse en Composantes Principales (ACP / PCA)**  
- **Clustering K-Means** avec initialisations *random* et *k-means++*

Le dataset contient des informations démographiques et comportementales, et l’objectif final est de  
**segmenter les clients en groupes homogènes** afin d’aider le service marketing à cibler leurs actions.

---

## 📌 **1. Contenu du dataset**
Le fichier `Mall_Customers.csv` contient :

| Variable | Description |
|---------|-------------|
| `CustomerID` | Identifiant du client |
| `Genre` | Sexe |
| `Age` | Âge |
| `Annual Income (k$)` | Revenu annuel |
| `Spending Score (1-100)` | Score de dépenses |

---

## 📌 **2. Prétraitement des données**
- Sélection des variables numériques :  
  `Age`, `Annual Income (k$)`, `Spending Score (1-100)`
- Normalisation des données via **MinMaxScaler**
- Vérification des valeurs manquantes

---

## 📌 **3. ACP — Analyse en Composantes Principales**

Deux ACP ont été réalisées :

### ✔ ACP personnalisée
- Calcul de la matrice de corrélation  
- Valeurs propres & vecteurs propres  
- Pourcentage d'information expliqué  
- Projection sur deux axes principaux  

### ✔ ACP sklearn
Méthode standard utilisant `sklearn.decomposition.PCA`.

### 🔎 **Résultat**
Les deux méthodes donnent :
- Des variances expliquées très proches  
- Une représentation similaire (à un signe près)  
- Environ **80% de la variance expliquée** par les deux premiers axes

---

## 📌 **4. Clustering K-Means**

Deux initialisations testées :
- `init='random'`
- `init='k-means++'`

Pour chaque valeur de **k (2 → 8)**, nous avons calculé :  
➡️ **Indice de Calinski-Harabasz** afin de mesurer la qualité des clusters.

### 🔎 **Meilleure solution trouvée**
- **k = 5 clusters**
- Initialisation **k-means++**
- Meilleur score Calinski-Harabasz

---

## 📌 **5. Interprétation des segments**

| Cluster | Profil client | Interprétation marketing |
|--------|---------------|--------------------------|
| 1 | Jeunes – Score élevé – Faible revenu | Dépenseurs impulsifs |
| 2 | Revenu élevé – Score faible | Clients riches mais peu acheteurs |
| 3 | Revenu élevé – Score élevé | Clients VIP à fidéliser |
| 4 | Revenu moyen – Dépenses moyennes | Clients réguliers |
| 5 | Âgés – Faibles dépenses | Peu sensibles au marketing |

---

## 📌 **6. Visualisations**
Le rapport inclut :
- Projection ACP (PC1 vs PC2)
- Score Calinski-Harabasz en fonction de k
- Clusters projetés sur l’ACP

---

## 📌 **7. Technologies utilisées**
- Python  
- Pandas  
- NumPy  
- Matplotlib / Seaborn  
- Scikit-learn  

---

## 📌 **8. Comment exécuter le projet (Google Colab)**

### Étapes :
1. Importer le Notebook dans Google Colab  
2. Exécuter la cellule pour uploader le CSV :

```python
from google.colab import files
uploaded = files.upload()
data = pd.read_csv(list(uploaded.keys())[0], sep=';')

-----------------------------------------
  Abdellah Lambaraa
  Data & Cloud Computing Engineer  
  Full Stack Developer — Laravel | React
  Analyse, Sécurité, Performance & IA
-----------------------------------------
