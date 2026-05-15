# LU2IN005 - Automates finis en Python

Projet universitaire réalisé dans le cadre de l’UE **LU2IN005 : Mathématiques discrètes** à Sorbonne Université.

L’objectif du projet est de programmer en Python plusieurs algorithmes classiques sur les automates finis, en utilisant les structures de données fournies dans le cadre du TME.

Réalisé par :
- Jalil Keddara


## Présentation du projet

Ce projet porte sur la manipulation d’automates finis.

Le notebook principal contient l’implémentation de plusieurs fonctions permettant de construire, tester et transformer des automates.

Les structures de base sont fournies dans les fichiers Python du projet :

- `state.py`
- `transition.py`
- `automateBase.py`
- `myparser.py`
- `sp.py`

Le travail demandé consistait principalement à compléter le notebook étudiant avec les algorithmes vus en cours et en TD.

## Technologies utilisées

- Python
- Jupyter Notebook
- Programmation orientée objet
- Structures de données
- Graphviz pour l’affichage graphique des automates

## Organisation du projet

Le dépôt contient les fichiers suivants :

- `automate_etudiant_kaouane.ipynb` : notebook principal contenant les réponses du TME ;
- `state.py` : définition de la classe `State` ;
- `transition.py` : définition de la classe `Transition` ;
- `automateBase.py` : classe de base pour les automates ;
- `myparser.py` : outils de parsing pour créer des automates depuis des fichiers ;
- `sp.py` : fonctions utiles fournies avec le sujet ;
- `ExemplesAutomates/` : dossier contenant des exemples d’automates au format texte ;
- `affichage.dot` et `affichage.dot.png` : fichiers générés lors de l’affichage graphique.

## Objectifs du TME

Le projet avait pour objectif d’implémenter plusieurs opérations fondamentales sur les automates finis :

- création et manipulation d’automates ;
- calcul des successeurs ;
- test d’acceptation d’un mot ;
- test de complétude ;
- test de déterminisme ;
- complétion d’un automate ;
- déterminisation ;
- complémentaire d’un langage ;
- intersection de deux langages ;
- union de deux langages ;
- concaténation de deux langages ;
- étoile de Kleene.

## Fonctionnalités implémentées

### Successeurs

La fonction `succ` calcule l’ensemble des états accessibles depuis un ensemble d’états donné par une lettre.

Elle généralise la fonction `succElem`, qui ne traite qu’un seul état.

### Acceptation d’un mot

La fonction `accepte` vérifie si un automate accepte un mot donné.

Elle fonctionne aussi pour les automates non déterministes, en gardant l’ensemble des états courants à chaque étape.

### Complétude

La fonction `estComplet` vérifie si un automate est complet par rapport à un alphabet donné.

La vérification se fait uniquement sur les états accessibles depuis les états initiaux.

### Déterminisme

La fonction `estDeterministe` vérifie qu’un automate possède un seul état initial et qu’il n’existe pas deux transitions de même étiquette sortant du même état.

### Complétion

La fonction `completeAutomate` construit un nouvel automate complet sans modifier l’automate original.

Elle ajoute un état puits lorsque certaines transitions sont manquantes.

### Déterminisation

La fonction `determinisation` construit un automate déterministe équivalent à l’automate initial.

Elle repose sur la construction par ensembles d’états : chaque état du nouvel automate représente un ensemble d’états de l’automate d’origine.

### Complémentaire

La fonction `complementaire` construit un automate reconnaissant le langage complémentaire.

La méthode utilisée est :

1. déterminiser l’automate ;
2. le compléter ;
3. inverser les états finaux et non finaux.

### Intersection

La fonction `intersection` construit un automate reconnaissant l’intersection de deux langages.

Elle utilise une construction par produit synchronisé entre deux automates.

### Union

La fonction `union` construit un automate reconnaissant l’union de deux langages.

Elle utilise aussi une construction par produit, mais un état produit est final si au moins une de ses deux composantes est finale.

### Concaténation

La fonction `concatenation` construit un automate reconnaissant la concaténation des langages de deux automates.

L’idée est de connecter les états finaux du premier automate aux états initiaux du second.

### Étoile de Kleene

La fonction `etoile` construit un automate reconnaissant l’étoile du langage de l’automate initial.

Elle ajoute notamment un nouvel état initial et final afin d’accepter le mot vide.

## Exemples d’automates

Le dossier `ExemplesAutomates/` contient des fichiers texte décrivant des automates.

Un automate peut être créé à partir d’un fichier avec :

```python
automate = Automate.creationAutomate("ExemplesAutomates/exempleAutomate.txt")

