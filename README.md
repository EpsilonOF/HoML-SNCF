# Analyse de la régularité des trains SNCF

Ce projet vise à prédire différentes métriques liées aux retards des trains SNCF en utilisant des techniques de machine learning. L'analyse se concentre notamment sur la prédiction du nombre de trains en retard et du retard moyen en fonction de différentes variables comme le mois, les gares de départ et d'arrivée.

## Données

Les données utilisées dans ce projet proviennent de deux sources principales :
- [Dataset Kaggle sur la régularité mensuelle des TGV](https://www.kaggle.com/datasets/elliotx1000/french-railway-monthly-tgv-regularity)
- [Données SNCF sur la régularité mensuelle des TGV (AQST)](https://ressources.data.sncf.com/explore/dataset/regularite-mensuelle-tgv-aqst/information/)

Ce projet utilise le fichier CSV dans la section Export du second lien.

## Prérequis

Le projet requiert les bibliothèques Python suivantes :
- pandas
- numpy
- scikit-learn
- matplotlib
- pathlib

Vous pouvez installer ces dépendances avec la commande :
```
pip install -r requirements.txt
```

## Structure du projet

```
.
├── project.py          # Script principal
├── data/               # Dossier contenant les données
│   ├── regularite-mensuelle-tgv-aqst.csv    # Données brutes
│   ├── sncf_data.csv                        # Données nettoyées
│   └── correspondance_gare.csv              # Correspondance indices-gares
├── meilleur_resultat.txt   # Résultats optimisés
└── README.md           # Ce fichier
```

## Fonctionnalités

Le script réalise plusieurs analyses séquentielles :

1. **Prétraitement des données** : Chargement, nettoyage et encodage des variables catégorielles
2. **Analyse de corrélation** : Identification des variables les plus corrélées aux cibles
3. **Entraînement de modèles** pour prédire 4 cibles distinctes :
   - Nombre de trains en retard à l'arrivée
   - Nombre de trains en retard au départ
   - Retard moyen de tous les trains au départ
   - Retard moyen des trains en retard à l'arrivée
4. **Évaluation des modèles** : Comparaison des performances via validation croisée
5. **Optimisation d'hyperparamètres** : Recherche des meilleurs paramètres via GridSearchCV
6. **Visualisation des résultats** : Graphiques comparant prédictions et données réelles

## Modèles testés

Plusieurs modèles de régression sont évalués pour chaque cible :
- Régression linéaire simple
- Régression polynomiale
- Ridge Regression
- Lasso Regression
- Random Forest
- Gradient Boosting

## Utilisation

Pour exécuter l'analyse complète, téléchargez le projet et exécutez les cellules une par une, selon la tâche que vous souhaitez réaliser. Le projet suit une ligne directrice au fur et à mesure du notebook, il est donc conseillé de l'exécuter dans l'ordre.

## Résultats

Les meilleures performances ont été obtenues pour la prédiction du nombre de trains en retard à l'arrivée, avec un score R² d'environ 0.73, ce qui indique une bonne capacité prédictive du modèle.

Le script sauvegarde les meilleurs hyperparamètres trouvés dans un fichier `meilleur_resultat.txt`, consultable dans le dossier `data`.