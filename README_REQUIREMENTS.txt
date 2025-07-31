
CLIMATE LLM FINE-TUNING – HACKATHON PROJECT
===========================================


OBJECTIFS
---------
Ce projet a pour but d'exploiter la puissance des modèles de langage (LLM) pour analyser les discussions publiques sur le climat à partir de données issues de Reddit.

Les étapes principales :
- Extraction et nettoyage de discussions Reddit sur le thème du climat
- Préparation des données pour l'entraînement
- Fine-tuning léger d’un modèle de langage (type DistilBERT)
- Évaluation des performances
- Visualisation des tendances et des sentiments exprimés

STRUCTURE DU PROJET
-------------------
📁 hackathon2_karim_lea_llm_finetuned_climate_final.ipynb : 
    Notebook principal contenant l’ensemble du code du projet

📁 data/ : 
    Répertoire à créer pour stocker les données (non incluses ici)

📁 modules internes :
    - core_modules
    - data_modules
    - model_modules
    - qa_modules
    - visualization_modules
    Ces fichiers Python doivent être présents localement (non installables via pip)

📄 README_REQUIREMENTS.txt : 
    Ce fichier (documentation + dépendances)

TECHNOLOGIES UTILISÉES
-----------------------
- Python (3.8+)
- NLP / IA : Hugging Face Transformers, PEFT, Sentence Transformers
- Analyse de données : Pandas, NumPy, Scikit-learn
- Visualisation : Matplotlib, Seaborn
- Divers : LangChain, Streamlit, Faiss, Pyngrok

INSTALLATION & UTILISATION
---------------------------
1. Cloner le dépôt GitHub :
   git clone https://github.com/ton-repo/climate-llm-hackathon.git
   cd climate-llm-hackathon

2. Installer les dépendances :
   pip install -r requirements.txt

3. Lancer le notebook :
   jupyter notebook hackathon2_karim_lea_llm_finetuned_climate_final.ipynb

4. (Facultatif) Lancer une interface Streamlit :
   streamlit run app.py

AUTEURS
-------
👥 Karim & Léa  
📅 Hackathon Juillet 2025

---

📦 REQUIREMENTS (Dépendances Python)
------------------------------------

datasets
faiss-cpu
feedparser
langchain
matplotlib
nltk
numpy
pandas
peft
pyngrok
rouge-score
schedule
seaborn
sentence-transformers
scikit-learn
streamlit
torch
transformers
