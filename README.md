# 📊 Réalisation d’un Dashboard de Scoring Crédit & Veille Technique NLP

## 🧩 Description du projet
Ce projet combine deux volets complémentaires :

1. **Développement d’un Dashboard interactif** de scoring crédit permettant une analyse explicable et dynamique des clients via **Streamlit** et une **API Flask** déployée sur **Heroku**.
2. **Veille technique en NLP**, comparant les modèles **BERT-base-uncased** et **all-MiniLM-L6-v2** pour la classification de produits e-commerce à partir de descriptions textuelles.

---

## 🏗️ Structure du dépôt
```text
realisation_dashboard_veille_technique/
│
├── Martineau_Alexandre_3_note_méthodologique_022025.pdf    # Note méthodologique - MiniLM vs BERT
├── Martineau_Alexandre_4_presentation_022025.pdf           # Présentation PowerPoint du projet
│
├── Martineau_Alexandre_1_dashboard_022025.py               # Script principal Streamlit
├── Martineau_Alexandre_2_notebook_veille_022025.ipynb      # Notebook de veille technique NLP
└── README.md
```

## 🖥️ 1️⃣ Dashboard de Scoring Crédit

### ⚙️ Objectif
Concevoir une interface interactive et explicable pour visualiser le **score de crédit**, la **probabilité de remboursement**, et les **caractéristiques influentes** d’un client.

### 🧰 Technologies
- **Frontend / Dashboard** : Streamlit, Plotly, Seaborn, Matplotlib  
- **Backend / API** : Flask (API déployée sur Heroku : [my-scoring-app](https://my-scoring-app-546acd78d8fa.herokuapp.com/))  
- **ML Explainability** : SHAP (global + local), Feature Engineering dynamique  
- **CI/CD & Hébergement** : Heroku + GitHub Actions  

---

### 💡 Fonctionnalités principales
- Sélection d’un client et affichage de son score de crédit.  
- Modification des informations via une **barre latérale interactive**.  
- Recalcul instantané du score et des valeurs SHAP.  
- Visualisation :
  - **Jauge dynamique** du score et du seuil d’acceptabilité (52 %).  
  - **Importance globale et locale** des variables explicatives.  
  - **Analyses croisées** et **bi-variées** des variables.  

---

### 🧠 Interprétabilité
- **SHAP Global** : pondération moyenne des features expliquant les décisions du modèle.  
- **SHAP Local** : explication d’une prédiction individuelle.  
- **Visualisation dynamique** : beeswarm plots, waterfall plots, histograms et scatter plots interactifs.  

---

### 🔗 API utilisée
| Endpoint | Description |
|-----------|-------------|
| `/predict_proba` | Prédiction du score de crédit |
| `/best_threshold` | Renvoie le seuil de décision optimal |
| `/download_model` | Téléchargement du modèle entraîné |
| `/data` | Préparation et transformation des données d’entrée |

---

## 🧬 2️⃣ Veille Technique : NLP & Classification de Produits

### 🎯 Objectif
Comparer les performances de deux modèles NLP :
- **BERT-base-uncased** (modèle classique Hugging Face)
- **all-MiniLM-L6-v2** (modèle distillé, 3× plus rapide et 3× plus léger)

sur un **jeu de données Flipkart e-commerce**, afin d’évaluer leur efficacité pour la **classification de produits** selon leur description textuelle.

---

### 🧩 Méthodologie
1. **Prétraitement des données** : extraction des catégories principales, nettoyage des textes.  
2. **Encodage des descriptions** :
   - BERT via `TFAutoModel` (Hugging Face)  
   - MiniLM via `SentenceTransformer("all-MiniLM-L6-v2")`  
3. **Classification** :
   - Modèle : Régression Logistique  
   - Évaluation : Accuracy + Classification Report  
4. **Visualisation** :
   - Réduction de dimension via **t-SNE**  
   - Clustering via **KMeans**  
   - Calcul de l’**ARI (Adjusted Rand Index)**  

---

### 📈 Résultats

| Modèle | Accuracy | ARI | Commentaire |
|---------|:--------:|:----:|-------------|
| **BERT-base-uncased** | 0.93 | 0.31 | Bonne séparation, clusters mélangés |
| **all-MiniLM-L6-v2** | **0.95** | **0.71** | Excellente séparation, embeddings plus cohérents |

Les résultats démontrent que **MiniLM** offre une **précision équivalente à BERT** tout en étant **plus léger et plus rapide**, ce qui le rend particulièrement adapté à des contextes de production et de veille technique.

---

### 🛠️ Technologies utilisées
- **Machine Learning** : scikit-learn, numpy, pandas  
- **NLP** : Hugging Face Transformers, Sentence-Transformers, TensorFlow  
- **Visualisation** : matplotlib, seaborn, Plotly  
- **Dashboard & API** : Streamlit, Flask, Heroku  
- **Explainability & Monitoring** : SHAP  

---

### 🔍 Résumé global du projet
Ce dépôt illustre :
- L’intégration **MLOps + DataViz** via un dashboard explicable et déployé.  
- Une **veille NLP** approfondie comparant deux modèles de génération d’embeddings modernes.  
- Une approche **complète du cycle IA**, de la collecte de données à l’explicabilité en production.  

### 📦 Dépôt & Ressources

🔗 Dépôt GitHub : realisation_dashboard_veille_technique
🔗 API Scoring : https://my-scoring-app-546acd78d8fa.herokuapp.com/

## ✅ Conclusion

Ce projet associe data science appliquée et veille technologique autour de deux axes :
- un dashboard explicable en production pour la prise de décision en crédit,
- une analyse comparative de modèles NLP pour la classification de produits e-commerce.

Il démontre une maîtrise du cycle complet de la donnée à la visualisation, intégrant transparence, performance et innovation.
