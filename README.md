# 🌍 Climate Sentiment Analyzer

**Pipeline complet d’analyse de sentiments climatiques avec Transformers, LoRA et Streamlit.**

---

## 📦 Fonctionnalités

- ✅ **Chargement automatique de CSV** avec détection de colonnes
- ✅ **Entraînement de modèle** avec LoRA (efficient fine-tuning)
- ✅ **Visualisations complètes** : matrice de confusion, courbes d’entraînement, F1-score par classe, distribution des labels
- ✅ **Interface Q&A** avec recherche sémantique
- ✅ **Interface Streamlit** moderne et responsive

---

## 🚀 Installation rapide

### 1. Cloner le projet
```bash
git clone https://github.com/votre-utilisateur/climate-sentiment-analyzer.git
cd climate-sentiment-analyzer

2. Installer les dépendances
bash


pip install -r requirements.txt

3. Lancer l’interface
bash


streamlit run streamlit_app.py

📁 Structure du projet


climate-sentiment-analyzer/
├── streamlit_app.py           # Interface principale
├── core_modules.py            # Configuration centrale
├── data_modules.py            # Chargement et nettoyage CSV
├── model_modules.py           # Modèle + LoRA + Trainer
├── visualization_modules.py   # Graphiques et rapports
├── qa_modules.py              # Recherche sémantique
├── knowledge_modules.py       # Base de connaissances
├── requirements.txt           # Dépendances
├── README.md                  # Ce fichier
└── outputs/                   # Sauvegardes du modèle

🧪 Exemple d’utilisation

    Télécharger un CSV avec deux colonnes (texte + label)
    Cliquer sur "Lancer l’entraînement"
    Changer de mode → Q&A ou Visualisations → Tout fonctionne sans réentraîner

📊 Visualisations disponibles

Graphique	Description
Matrice de confusion	Erreurs par classe
Rapport de classification	Precision, Recall, F1-score
Distribution des classes	Histogramme des labels
F1-score par classe	Performance par catégorie
Courbes d’entraînement	Loss et accuracy au fil des epochs
📌 Remarques

    Compatible CPU et GPU
    Utilise LoRA pour un entraînement rapide et léger
    Pas de sauvegarde pickle → pas d’erreur de sérialisation

🤝 Contribution
Les PR et issues sont les bienvenues !



---

### ✅ `requirements.txt`

```txt
# === Core ===
torch>=2.1.0
transformers>=4.36.0
datasets>=2.16.0
peft>=0.7.0

# === Interface ===
streamlit>=1.29.0
plotly>=5.17.0

# === Visualisation ===
matplotlib>=3.7.0
seaborn>=0.12.0

# === ML ===
scikit-learn>=1.3.0
numpy>=1.24.0
pandas>=1.5.0

# === Q&A ===
sentence-transformers>=2.2.0

# === Utils ===
tqdm>=4.64.0

✅ Utilisation
bash


# 1. Installer les dépendances
pip install -r requirements.txt

# 2. Lancer l'interface
streamlit run streamlit_app.py

✅ Accès après entraînement

    Q&A : pose des questions sur le climat → réponses basées sur le dataset
    Visualisations : 5 types de graphiques disponibles

🎯 Résultat final
✅ Projet prêt à être partagé sur GitHub ou Colab
