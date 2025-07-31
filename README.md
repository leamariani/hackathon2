Testez avec le subsampled.csv !!!

Climate Analyzer Pro est une plate-forme tout-en-un d’analyse, de classification et de question-réponse sur le changement climatique.
Elle combine :

    ✅ Fine-tuning LLM (LoRA) pour la classification de textes climatiques
    🧠 Système Q&A optimisé (FAISS + Sentence-BERT) avec base de connaissances extensible
    📰 Mise à jour automatique via flux RSS (Carbon Brief, NASA, UNFCCC)
    📊 Dashboard Streamlit ultra-rapide et 100 % cloud-ready (Colab, ngrok, Docker)
    🔍 Évaluation complète : accuracy, F1, BLEU, ROUGE, matrices de confusion…

1) Fonctionnalités

Fonctionnalité	Description
🚀 Pipeline Complet	Upload CSV → entraînement LoRA → sauvegarde & déploiement en 1 clic
❓ Q&A Avancée	Recherche sémantique, par mots-clés, par catégorie ou hybride avec fallback
📰 RSS Auto-Update	Ajoute quotidiennement les derniers articles climatiques à la base de connaissances
📈 Visualisations	Courbes d’entraînement, matrices de confusion, distributions, BLEU/ROUGE
📚 Gestion des Connaissances	Ajout / suppression / catégorisation via interface cliquable
⚡ Optimisations	Caching LRU, index FAISS, tokenisation batch, GPU/CPU auto
🛠️ Installation rapide

2) Structure du projet

climate-analyzer-pro/
├── streamlit_app.py           # Interface principale Streamlit
├── core_modules.py            # Configuration centrale (LoRA, hyper-paramètres)
├── data_modules.py            # Chargement, nettoyage et split des données CSV
├── model_modules.py           # Modèle LoRA + Trainer Hugging Face
├── visualization_modules.py   # Graphiques et rapports (Streamlit + matplotlib/seaborn)
├── qa_modules.py              # Moteur Q&A sémantique (FAISS + Sentence-BERT)
├── knowledge_modules.py       # Base de connaissances statique (fallback)
├── update_kb_rss.py           # Mise à jour automatique via flux RSS
├── setup_pipeline.py          # Script d'installation des dépendances
├── requirements.txt           # Liste complète des packages
├── README.md                  # Documentation du projet
└── outputs/                   # ✅ Sauvegardes du modèle et logs
    ├── final_model/
    │   ├── config.json
    │   ├── pytorch_model.bin
    │   └── trainer_state.json
    └── logs/

3) Structure des modules

| Fichier                    | Rôle                                               |
| -------------------------- | -------------------------------------------------- |
| `core_modules.py`          | Configuration centralisée (LoRA, hyper-paramètres) |
| `data_modules.py`          | Nettoyage CSV, split train/val/test                |
| `model_modules.py`         | Modèle LoRA, tokenizer, Trainer Hugging Face       |
| `qa_modules.py`            | Moteur Q\&A (FAISS + Sentence-BERT) avec cache     |
| `visualization_modules.py` | Graphiques Streamlit + BLEU/ROUGE                  |
| `knowledge_modules.py`     | Base de connaissances statique (fallback)          |
| `update_kb_rss.py`         | Tâche planifiée RSS → base de connaissances        |
| `streamlit_app.py`         | Interface principale (multi-onglets)               |
| `setup_pipeline.py`        | Script d’installation des dépendances              |

4) requirements.txt
# Core ML & NLP
torch>=2.1.0
transformers>=4.36.0
datasets>=2.16.0
tokenizers>=0.15.0
peft>=0.7.0
accelerate>=0.25.0

# Embedding & Search
sentence-transformers>=2.2.0
faiss-cpu>=1.7.0
langchain>=0.1.0
langchain-community>=0.0.10

# Web Framework
streamlit>=1.29.0
streamlit-authenticator>=0.2.0

# Data Processing
pandas>=1.5.0
numpy>=1.24.0
scikit-learn>=1.3.0
matplotlib>=3.7.0
seaborn>=0.12.0
plotly>=5.17.0

# Evaluation & Metrics
rouge-score>=0.1.2
nltk>=3.8
evaluate>=0.4.0

# Utilities
feedparser>=6.0.0
schedule>=1.2.0
pyngrok>=7.0.0
python-dotenv>=1.0.0
tqdm>=4.65.0
colorama>=0.4.6

5) System Requirements

    Python: 3.9+
    RAM: 4GB minimum (8GB recommended)
    Storage: 2GB free space
    OS: Linux / macOS / Windows
    Optional: CUDA 11.8+ for GPU acceleration
   
6) Automatisation RSS

    Planifiée tous les jours à 09h00
    Sources configurées :
        https://www.carbonbrief.org/feed/
        https://climate.nasa.gov/news/rss.xml
        https://unfccc.int/news/rss.xml
    Ajoute automatiquement les nouveaux articles (chunk 400 caractères) avec catégorie rss_news.

7) Métriques & évaluation

| Métrique          | Outil                                  |
| ----------------- | -------------------------------------- |
| **Accuracy / F1** | Scikit-learn (`classification_report`) |
| **BLEU**          | `nltk.translate.bleu_score`            |
| **ROUGE**         | `rouge_score`                          |
| **Similarité**    | Cosine FAISS (normalisée)              |


8) Q&A :
Exemples de questions

| Question                                                            | Type de réponse              |
| ------------------------------------------------------------------- | ---------------------------- |
| *Quelles sont les principales causes du réchauffement climatique ?* | Base de connaissances        |
| *Comment réduire mes émissions de CO2 ?*                            | Solutions + corpus           |
| *Impact de la déforestation ?*                                      | Chiffré (15 % des émissions) |
| *Derniers articles sur le GIEC ?*                                   | RSS + filtrage date          |


9) Paramètres avancés

| Paramètre              | Défaut | Description           |
| ---------------------- | ------ | --------------------- |
| `lora_r`               | 8      | Rang LoRA             |
| `max_length`           | 128    | Tokens maximum        |
| `similarity_threshold` | 0.3    | Seil FAISS            |
| `top_k`                | 5      | Nombre de réponses    |
| `batch_size`           | 16     | Taille batch training |

10) Dépannage
11) 
| Problème                  | Solution                                        |
| ------------------------- | ----------------------------------------------- |
| `CUDA out of memory`      | Réduire `batch_size` ou `max_length`            |
| `No module named 'faiss'` | Relancer `setup_pipeline.py`                    |
| Trop lent sur CPU         | Passer à `device='cuda'` dans `qa_modules.py`   |
| RSS ne se met pas à jour  | Vérifier la connectivité ou lancer manuellement |

Licence
MIT – voir LICENSE

Contribution
Les PR et issues sont les bienvenus !
Ajoutez simplement +1 sur une issue ou proposez une amélioration via une Pull Request.
Made with ❤️ by the Climate AI Community
