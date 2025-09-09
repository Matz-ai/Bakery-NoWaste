# 🍞 Prédiction des ventes et réduction des invendus en boulangerie

## 📌 Problème
Les boulangeries font face à un dilemme quotidien : produire assez pour satisfaire la demande, sans générer trop d’invendus.
Les pertes liées au gaspillage alimentaire représentent un coût important, qui pourrait être réduit grâce à une meilleure prévision des ventes.

Ce projet vise à construire un modèle de **prévision de la demande** pour une boulangerie française, afin de limiter les invendus et d’optimiser la production.

---

## 📊 Données utilisées
- **Ventes historiques (`sales.csv`)**
  Données provenant d’une boulangerie française (dataset Kaggle).

- **Météo (API [Open-Meteo](https://open-meteo.com/))**
  Température, précipitations et autres variables météo impactant la fréquentation d’une boulangerie.

- **Vacances scolaires**
  Utilisation du package Python [`vacances-scolaires-france`](https://pypi.org/project/vacances-scolaires-france/) (v0.10.0) pour enrichir le dataset avec les périodes de vacances selon les zones.

---

## ⚙️ Méthodologie
1. **Exploration et préparation des données**
   - Nettoyage et agrégation des ventes journalières.
   - Enrichissement avec la météo et les vacances scolaires.

2. **Modélisation**
   - Baseline naïve (moyenne glissante).
   - Tests de plusieurs modèles de machine learning.
   - **LightGBM** s’est révélé le plus performant.

3. **Analyse des résultats**
   - Le modèle prédit correctement les tendances, mais sous-évalue les ventes en août (probablement un événement local non capturé dans les données).
   - Limite : le dataset ne couvre qu’**une seule année**, ce qui réduit la significativité statistique.

---

## 💰 Impact économique estimé
Le modèle permet de réduire les invendus et d’optimiser la production.
Voici les économies annuelles estimées par produit :

| Produit              | Gain unités/jour | Économie/jour (€) | Économie/an (€) |
|----------------------|------------------|-------------------|-----------------|
| Traditional Baguette | 27.48            | 8.24              | 2,761.74        |
| Croissant            | 19.21            | 5.76              | 1,930.37        |
| Pain au chocolat     | 11.27            | 3.38              | 1,133.02        |
| Baguette             | 3.44             | 0.77              | 259.54          |
| Special Bread        | 0.51             | 0.31              | 102.33          |
| **TOTAL**            | -                | -                 | **6,186.99**    |

➡️ Soit plus de **6 000 € d’économies par an** pour cette boulangerie.

---

## 📈 Contexte économique
- **Chiffre d’affaires observé :** 507,564 €
- **Chiffre d’affaires annualisé :** 279,160 €
- La boulangerie se situe plutôt dans la moyenne du secteur.

Ainsi, les économies estimées représenteraient **~2% du chiffre d’affaires annuel**.

---

## 🖼️ Exemple de résultats
![Graphique performance du modèle](./assets/model_performance.png)

---

## 🚀 Améliorations possibles
- Collecter des données sur plusieurs années pour mieux capter la saisonnalité.
- Ajouter des features locales (événements, jours de marché, fêtes).
- Tester des architectures de type **RNN/LSTM** ou **transformers temporels** pour améliorer la capture des tendances complexes.

---

## 🛠️ Stack technique
- **Python** (pandas, numpy, scikit-learn, lightgbm, matplotlib, seaborn)
- **API Open-Meteo**
- **vacances-scolaires-france 0.10.0**

---

## 📂 Organisation du repo
├── data/ # Données brutes
├── assets/ # Graphiques et visuels
├── notebook # Notebook Jupyter (exploration + modèle)
├── requirements.txt # Dépendances Python
└── README.md # Présentation du projet


---

## ✨ Auteur
Projet réalisé par **Mathieu Zinzen** (2025).
