# Testez avec le subsampled.csv !!!

Climate Analyzer Pro est une plate-forme tout-en-un d’analyse, de classification et de question-réponse sur le changement climatique.
Elle combine :

    ✅ Fine-tuning LLM (LoRA) pour la classification de textes climatiques
    🧠 Système Q&A optimisé (FAISS + Sentence-BERT) avec base de connaissances extensible
    📰 Mise à jour automatique via flux RSS (Carbon Brief, NASA, UNFCCC)
    📊 Dashboard Streamlit ultra-rapide et 100 % cloud-ready (Colab, ngrok, Docker)
    🔍 Évaluation complète : accuracy, F1, BLEU, ROUGE, matrices de confusion…

## 1) Fonctionnalités

| Emoji | Fonctionnalité | Description |
|-------|----------------|-------------|
| 🚀 | **Pipeline complet** | Upload CSV → entraînement LoRA → sauvegarde & déploiement en 1 clic |
| ❓ | **Q&A avancée** | Recherche sémantique, mots-clés, catégorie ou hybride + fallback |
| 📰 | **RSS auto-update** | Articles climatiques ajoutés quotidiennement à la base de connaissances |
| 📈 | **Visualisations** | Courbes d’entraînement, matrices de confusion, BLEU/ROUGE… |
| 📚 | **Gestion connaissances** | Ajout / suppression / catégorisation via interface cliquable |
| ⚡ | **Optimisations** | LRU cache, FAISS, batch tokenisation, GPU/CPU auto |
| 🛠️ | **Installation rapide** | `pip install -r requirements.txt && streamlit run streamlit_app.py` |

## 2) 📁 Structure du projet

```
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
```

# 3) Structure des modules

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


   
# 4) Automatisation RSS

    Planifiée tous les jours à 09h00
    Sources configurées :
        https://www.carbonbrief.org/feed/
        https://climate.nasa.gov/news/rss.xml
        https://unfccc.int/news/rss.xml
    Ajoute automatiquement les nouveaux articles (chunk 400 caractères) avec catégorie rss_news.

# 5) Métriques & évaluation

| Métrique          | Outil                                  |
| ----------------- | -------------------------------------- |
| **Accuracy / F1** | Scikit-learn (`classification_report`) |
| **BLEU**          | `nltk.translate.bleu_score`            |
| **ROUGE**         | `rouge_score`                          |
| **Similarité**    | Cosine FAISS (normalisée)              |


# 6) Q&A :
Exemples de questions

| Question                                                            | Type de réponse              |
| ------------------------------------------------------------------- | ---------------------------- |
| *Quelles sont les principales causes du réchauffement climatique ?* | Base de connaissances        |
| *Comment réduire mes émissions de CO2 ?*                            | Solutions + corpus           |
| *Impact de la déforestation ?*                                      | Chiffré (15 % des émissions) |
| *Derniers articles sur le GIEC ?*                                   | RSS + filtrage date          |


# 7) Paramètres avancés

| Paramètre              | Défaut | Description           |
| ---------------------- | ------ | --------------------- |
| `lora_r`               | 8      | Rang LoRA             |
| `max_length`           | 128    | Tokens maximum        |
| `similarity_threshold` | 0.3    | Seil FAISS            |
| `top_k`                | 5      | Nombre de réponses    |
| `batch_size`           | 16     | Taille batch training |

# 8) Dépannage

| Problème                  | Solution                                        |
| ------------------------- | ----------------------------------------------- |
| `CUDA out of memory`      | Réduire `batch_size` ou `max_length`            |
| `No module named 'faiss'` | Relancer `setup_pipeline.py`                    |
| Trop lent sur CPU         | Passer à `device='cuda'` dans `qa_modules.py`   |
| RSS ne se met pas à jour  | Vérifier la connectivité ou lancer manuellement |

# Licence
MIT – voir LICENSE

# Contribution
Les PR et issues sont les bienvenus !
Ajoutez simplement +1 sur une issue ou proposez une amélioration via une Pull Request.
Made with ❤️ by the Climate AI Community
