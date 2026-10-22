# MLP — Classification du jeu de données Dry Bean

Ce projet contient un notebook Jupyter qui construit et évalue un perceptron multicouche (MLP) pour classifier les variétés de haricots secs du jeu de données **Dry Bean**.

## Contenu

- `TP_MLP_Dry_Bean.ipynb` : analyse des données, préparation, entraînement et évaluation du MLP.

Le notebook couvre notamment :

- le chargement du jeu de données Dry Bean via `ucimlrepo` ;
- l’analyse exploratoire et la vérification des doublons et valeurs manquantes ;
- une séparation stratifiée entraînement/validation/test sans fuite de données ;
- la standardisation des variables numériques ;
- la comparaison de plusieurs architectures et méthodes de régularisation ;
- l’utilisation d’`EarlyStopping` ;
- l’évaluation avec l’accuracy, la balanced accuracy, le F1 macro, le rapport de classification et la matrice de confusion ;
- la sauvegarde et le rechargement du modèle et du prétraitement.

## Prérequis

- Python 3.9 ou supérieur ;
- Jupyter Notebook ou JupyterLab ;
- un environnement compatible avec TensorFlow.

Les principales dépendances sont :

```bash
pip install numpy pandas matplotlib seaborn tensorflow scikit-learn ucimlrepo jupyter
```

## Exécution

1. Ouvrir `TP_MLP_Dry_Bean.ipynb` dans Jupyter ou JupyterLab.
2. Sélectionner un kernel Python disposant de TensorFlow.
3. Exécuter les cellules dans l’ordre.

Le notebook télécharge les données depuis le dépôt UCI au premier chargement ; une connexion Internet peut donc être nécessaire.

## Méthodologie

Les doublons sont retirés avant la séparation des données. Le jeu est ensuite divisé en ensembles d’entraînement, de validation et de test avec stratification. Le scaler est ajusté uniquement sur l’ensemble d’entraînement afin d’éviter toute fuite d’information vers la validation ou le test.

Le jeu de test est conservé pour l’évaluation finale, après la sélection de l’architecture et des paramètres à partir de la validation.

## Fichiers générés

À la fin du notebook, les fichiers suivants sont créés dans le répertoire courant :

- `modele_dry_bean.keras` : modèle TensorFlow/Keras entraîné ;
- `dry_bean_preprocessing.npz` : moyennes, échelles, noms des classes et ordre des variables nécessaires au prétraitement.

Pour réutiliser correctement le modèle, conserver ces deux fichiers ensemble et respecter l’ordre des variables enregistré dans `dry_bean_preprocessing.npz`.
