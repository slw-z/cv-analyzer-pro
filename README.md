# 🎯 CV Analyzer Pro

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-active-success.svg)]()

> Outil d'analyse de compatibilité CV/Offre d'emploi utilisant le traitement du langage naturel (NLP) pour optimiser vos candidatures et contourner les filtres ATS (Applicant Tracking Systems).

![CV Analyzer Demo](examples/captures d'écran/demo.png)
*Screenshot de l'analyse en action*

---

## 📋 Table des matières

- [Problème](#-problème)
- [Solution](#-solution)
- [Fonctionnalités](#-fonctionnalités)
- [Résultats](#-résultats)
- [Installation](#-installation)
- [Utilisation](#-utilisation)
- [Architecture Technique](#-architecture-technique)
- [Exemples](#-exemples)
- [Roadmap](#-roadmap)
- [Contribution](#-contribution)
- [Auteur](#-auteur)
- [Licence](#-licence)

---

## 🚨 Problème

### Le recrutement moderne est cassé

- **75%** des CV sont rejetés par les ATS avant qu'un humain ne les voie
- Les candidats ne savent pas **pourquoi** leurs CV sont rejetés
- Difficulté à **adapter** son CV pour chaque offre (temps, expertise)
- Les juniors sont particulièrement impactés par ces filtres automatiques

### Impact concret

- Des profils qualifiés jamais vus par les recruteurs
- Temps perdu sur des candidatures inadaptées
- Frustration et perte de confiance des chercheurs d'emploi

---

## ✨ Solution

**CV Analyzer Pro** analyse automatiquement la compatibilité entre votre CV et une offre d'emploi, puis génère des **recommandations personnalisées** pour optimiser vos chances.

### Ce que l'outil fait

1. **Analyse** votre CV et l'offre d'emploi
2. **Calcule** un score de compatibilité
3. **Détecte** les compétences et mots-clés manquants
4. **Génère** des suggestions personnalisées d'amélioration
5. **Produit** un template de lettre de motivation adapté
6. **Interprète** les résultats selon votre niveau (junior/confirmé)

---

## 🚀 Fonctionnalités

### Analyse Complète

- ✅ **Support multi-formats** : PDF, DOCX, TXT
- ✅ **Extraction de texte** intelligente avec gestion des erreurs
- ✅ **Détection de 30+ compétences techniques** (Python, SQL, Power BI, AWS, etc.)
- ✅ **Analyse NLP** : tokenization, nettoyage, extraction de mots-clés

### Suggestions Intelligentes

- 💡 **Recommandations de compétences** avec guide d'ajout détaillé
- 💡 **Suggestions de mots-clés** contextualisées
- 💡 **Propositions de reformulations** pour optimiser le contenu
- 💡 **Template de lettre de motivation** personnalisé automatiquement

### Interprétation Contextuelle

- 📊 **Scores adaptés au profil** (junior vs confirmé)
- 📊 **Benchmarks réalistes** : 12-18% = bon score junior
- 📊 **Estimation d'impact** des modifications suggérées
- 📊 **Analyse comparative** (mode batch pour plusieurs offres)

### Interfaces Multiples

- 🖥️ **Interface Jupyter** avec widgets interactifs
- 🖥️ **Mode copier-coller** rapide
- 🖥️ **Mode batch** pour analyser 5-10 offres simultanément
- 🖥️ **Export des résultats** en fichier texte

---

## 📈 Résultats

### Cas d'usage réel

**Avant optimisation :**
- Score de compatibilité : **8.82%**
- Compétences détectées : **7/19**
- CV invisible pour les ATS

**Après optimisation avec CV Analyzer :**
- Score de compatibilité : **30.39%**
- Compétences détectées : **18/19**
- CV passe les filtres ATS

### Amélioration mesurée : **+244%**

### Impact

- ✅ Temps d'optimisation par candidature : **5 min** au lieu de 30 min
- ✅ Taux de réponse positive : **Amélioration significative**
- ✅ Confiance du candidat : **Augmentée** (compréhension claire des attentes)

---

## 🔧 Installation

### Prérequis

- Python 3.8 ou supérieur
- Jupyter Notebook (pour l'interface interactive)
- pip (gestionnaire de paquets Python)

### Installation rapide

```bash
# Cloner le repository
git clone https://github.com/slw-z/cv-analyzer-pro.git
cd cv-analyzer-pro

# Installer les dépendances
pip install -r requirements.txt

# Lancer Jupyter Notebook
jupyter notebook CV_Analyzer_Pro.ipynb
```

### Dépendances

```
PyPDF2>=3.0.0
python-docx>=0.8.11
ipywidgets>=8.0.0
```

---

## 💻 Utilisation

### Méthode 1 : Interface Interactive (Recommandé)

```python
# Exécutez les cellules dans l'ordre
# L'interface apparaît automatiquement avec :
# - Bouton d'upload pour le CV
# - Zone de texte pour l'offre
# - Bouton "Analyser"
```

![Interface Widget](examples/captures d'écran/interface.png)

### Méthode 2 : Mode Rapide (Copier-Coller)

```python
from cv_analyzer_pro import CVAnalyzerPro

analyzer = CVAnalyzerPro()

# Votre CV
cv_path = "mon_cv.pdf"

# L'offre d'emploi
job_description = """
Nous recherchons un Data Analyst junior...
Compétences : Python, SQL, Power BI...
"""

# Analyser
results = analyzer.analyze(
    cv_path, 
    job_description,
    is_junior=True,
    export_results=True
)
```

### Méthode 3 : Mode Batch (Comparaison multi-offres)

```python
# Analyser votre CV contre plusieurs offres d'un coup
job_offers = {
    'Startup Tech XYZ': 'texte offre 1...',
    'Banque ABC': 'texte offre 2...',
    'Consulting DEF': 'texte offre 3...'
}

results = batch_analysis('mon_cv.pdf', job_offers)
# Affiche un tableau comparatif des scores
```

---

## 🏗️ Architecture Technique

### Stack Technique

| Composant | Technologie |
|-----------|-------------|
| Langage | Python 3.8+ |
| Extraction PDF | PyPDF2 |
| Extraction Word | python-docx |
| NLP | Regex, Collections |
| Interface | Jupyter + ipywidgets |
| Data Analysis | Pandas-like (Counter, Set operations) |

### Structure du Projet

```
cv-analyzer-pro/
│
├── CV_Analyzer_Pro.ipynb      # Notebook principal
├── README.md                   # Documentation
├── requirements.txt            # Dépendances Python
├── LICENSE                     # Licence MIT
├── .gitignore                 # Fichiers à ignorer
│
├── examples/                   # Exemples
│   ├── sample_cv.pdf
│   └── sample_job_offer.txt
│
├── screenshots/                # Captures d'écran
│   ├── demo.png
│   ├── interface.png
│   └── results.png
│
└── outputs/                    # Rapports générés (non versionnés)
```

### Algorithme de Compatibilité

```
1. Extraction du texte (CV + Offre)
   ↓
2. Nettoyage et tokenization
   ↓
3. Extraction des compétences techniques (pattern matching)
   ↓
4. Calcul du score = (mots communs / mots offre) × 100
   ↓
5. Génération des suggestions (règles basées sur contexte)
   ↓
6. Interprétation adaptée au profil (junior/confirmé)
```

### Détection des Compétences

Le système détecte **30+ compétences techniques** organisées en catégories :

- **Langages** : Python, Java, R, SQL, JavaScript
- **Data Tools** : Pandas, NumPy, Spark, Hadoop
- **Visualisation** : Power BI, Tableau, Qlik, Excel
- **Machine Learning** : PyTorch, TensorFlow, scikit-learn
- **Cloud** : AWS, Azure, GCP
- **ETL** : SSIS, SSMS, Power Query, Airflow
- **Méthodologies** : Agile, Scrum

---

## 📸 Exemples

### Exemple de Rapport d'Analyse

```
🎯 SCORE DE COMPATIBILITÉ: 13.5%
   ✅ PROFIL JUNIOR ACCEPTABLE
   Score NORMAL pour un junior. Adaptez 2-3 éléments et POSTULEZ !

💡 RECOMMANDATIONS PERSONNALISÉES

1️⃣ COMPÉTENCES CRITIQUES À AJOUTER

❌ SQL [CRITIQUE]
   
   📝 COMMENT L'AJOUTER :
   
   Dans 'Compétences' :
   • SQL (PostgreSQL, SQL Server - PGAdmin4, SSMS)
   • Requêtes complexes, jointures, agrégations
   
   Dans une expérience :
   "Analysé les données avec Python (Pandas) et SQL pour..."

2️⃣ MOTS-CLÉS À INTÉGRER

🔑 "visualisation" (mentionné 4× dans l'offre)
   → Mentionnez "visualisation de données avec Power BI"

📊 IMPACT ESTIMÉ DES MODIFICATIONS

   Score actuel    : 13.5%
   Score prévu     : 19.5%
   Amélioration    : +6%
```
![Interface Widget](examples/captures d'écran/résultats.png)

### Exemple de Template Lettre de Motivation

```
Objet : Candidature Data Analyst - [Entreprise]

Madame, Monsieur,

Diplômée Business Data Analyst, je me permets de postuler 
au poste de Data Analyst au sein de [Entreprise].

Mon profil combine des compétences techniques solides en :
• Python (Pandas, NumPy)
• SQL (PostgreSQL)
• Power BI (DAX, Power Query)

J'ai notamment développé une solution d'IA pour l'EPHEC 
ayant optimisé les processus pour 5000+ utilisateurs (-70% délais).

[...suite personnalisée...]
```

---

## 🗺️ Roadmap

### Version Actuelle : 2.0 (Jupyter Pro)

✅ Analyse complète CV/Offre  
✅ Suggestions intelligentes par règles  
✅ Template lettre de motivation  
✅ Interface interactive Jupyter  
✅ Mode batch multi-offres  

### Version 2.5 (Q1 2025) - En cours

- [ ] Interface web Flask/FastAPI
- [ ] Export PDF des rapports
- [ ] Graphiques interactifs (score evolution)
- [ ] Base de données pour historique

### Version 3.0 (Q2 2025) - Prévu

- [ ] Intégration IA (API Claude/GPT) pour suggestions avancées
- [ ] Génération automatique de CV optimisé
- [ ] Déploiement cloud (AWS/Heroku)
- [ ] API REST publique

### Idées Futures

- [ ] Extension Chrome pour LinkedIn/Indeed
- [ ] Analyse de profil LinkedIn
- [ ] Scraping automatique d'offres
- [ ] Alertes email pour nouvelles offres match
- [ ] Support multi-langues (EN, NL, etc.)

---

## 🤝 Contribution

Les contributions sont les bienvenues ! Voici comment participer :

### Comment contribuer

1. **Fork** le projet
2. **Créer** une branche (`git checkout -b feature/AmazingFeature`)
3. **Commit** vos changements (`git commit -m 'Add AmazingFeature'`)
4. **Push** sur la branche (`git push origin feature/AmazingFeature`)
5. **Ouvrir** une Pull Request

### Idées de contribution

- 🐛 Reporter des bugs
- 💡 Proposer de nouvelles fonctionnalités
- 📖 Améliorer la documentation
- 🌍 Ajouter le support d'autres langues
- ✨ Améliorer l'algorithme de scoring
- 🎨 Créer une interface web

### Guidelines

- Suivre le style de code existant
- Ajouter des tests si applicable
- Documenter les nouvelles fonctionnalités
- Mettre à jour le README si nécessaire

---

## 👤 Auteur

**Salwa Zaaraoui**

- 🌐 LinkedIn : [linkedin.com/in/salwa-zaaraoui](https://linkedin.com/in/salwa-zaaraoui)
- 📧 Email : zaaraoui.salwa@live.fr
- 💼 Portfolio : AI/ML

### À propos

Data Analyst diplômée avec expertise en Python, SQL, Power BI et Machine Learning. Passionnée par l'utilisation de la data pour résoudre des problèmes concrets. Ce projet est né d'une frustration personnelle face aux filtres ATS et démontre ma capacité à transformer un problème en solution technique.

---

## 📜 Licence

Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

```
MIT License

Copyright (c) 2025 Salwa Zaaraoui

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

---

## 🙏 Remerciements

- Communauté Python pour les excellentes librairies open-source
- EPHEC pour la formation en Business Data Analysis
- Tous les chercheurs d'emploi qui galèrent avec les ATS

---

## 📊 Stats du Projet

![GitHub stars](https://img.shields.io/github/stars/slw-z/cv-analyzer-pro?style=social)
![GitHub forks](https://img.shields.io/github/forks/slw-z/cv-analyzer-pro?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/slw-z/cv-analyzer-pro?style=social)

---

## 📚 Ressources Complémentaires

### Articles & Références

- [Comment fonctionnent les ATS](https://www.jobscan.co/blog/how-applicant-tracking-systems-work/)
- [Optimiser son CV pour les ATS](https://www.indeed.com/career-advice/resumes-cover-letters/ats-resume)
- [Guide prompting Claude](https://docs.anthropic.com/)

### Projets Similaires

- [Jobscan](https://www.jobscan.co/) - Solution commerciale
- [Resume.io](https://resume.io/) - Création de CV
- [Resume Worded](https://resumeworded.com/) - Analyse de CV

### Technologies Utilisées

- [PyPDF2 Documentation](https://pypdf2.readthedocs.io/)
- [python-docx Documentation](https://python-docx.readthedocs.io/)
- [Jupyter Widgets](https://ipywidgets.readthedocs.io/)

---

## 💬 Support

Besoin d'aide ? Plusieurs options :

- 📖 Consultez la [documentation complète](docs/)
- 🐛 Ouvrez une [issue](https://github.com/slw-z/cv-analyzer-pro/issues)
- 💬 Rejoignez la [discussion](https://github.com/slw-z/cv-analyzer-pro/discussions)
- 📧 Contactez directement : zaaraoui.salwa@live.fr

---

## ⭐ Star History

Si ce projet vous aide dans votre recherche d'emploi, pensez à lui donner une étoile ! ⭐

Ça aide d'autres chercheurs d'emploi à découvrir l'outil.

---

<div align="center">

**Fait avec ❤️ par Salwa Zaaraoui**

*Transformez votre recherche d'emploi avec la data !*

[⬆ Retour en haut](#-cv-analyzer-pro)

</div>
