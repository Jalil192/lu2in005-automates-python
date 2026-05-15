# Projet Automates Finis — LU2IN005

> **Auteur :** KAOUANE Walid  
> **UE :** LU2IN005 — Mathématiques discrètes  
> **Université :** Sorbonne Université  
> **Année :** 2024–2025

---

## 📖 Description

Ce projet implémente en Python plusieurs algorithmes classiques sur les **automates finis**, vus en cours et en TD dans le cadre de l'UE de Mathématiques discrètes.

Il repose sur des structures de données fournies (`State`, `Transition`, `AutomateBase`) et un notebook Jupyter (`automate_etudiant.ipynb`) contenant toutes les fonctions à implémenter.

---

## 📁 Structure du projet

```
Projet-Automates/
│
├── automate_etudiant.ipynb   # Notebook principal (fonctions implémentées)
├── automateBase.py           # Classe de base AutomateBase (fournie, ne pas modifier)
├── state.py                  # Classe State — représentation d'un état (fournie)
├── transition.py             # Classe Transition — représentation d'une transition (fournie)
├── myparser.py               # Parser pour lire les automates depuis des fichiers (fourni)
├── sp.py                     # Bibliothèque Simple Parser (fournie)
│
└── ExemplesAutomates/
    ├── exempleAutomate.txt   # Exemple d'automate au format texte
    └── auto2.txt             # Second exemple d'automate
```

---

##  Structures de données

### `State` — un état
| Attribut | Type | Description |
|---|---|---|
| `id` | `int` | Identifiant unique de l'état |
| `init` | `bool` | `True` si l'état est initial |
| `fin` | `bool` | `True` si l'état est final |
| `label` | `str` | Étiquette affichée (par défaut = `str(id)`) |

### `Transition` — une transition
| Attribut | Type | Description |
|---|---|---|
| `stateSrc` | `State` | État source |
| `etiquette` | `str` | Lettre de la transition |
| `stateDest` | `State` | État destination |

### `Automate` — un automate fini
| Attribut | Type | Description |
|---|---|---|
| `allStates` | `set[State]` | Ensemble de tous les états |
| `allTransitions` | `set[Transition]` | Ensemble de toutes les transitions |
| `label` | `str` | Nom de l'automate (optionnel) |

---

##  Fonctions implémentées

### 3. Tests et complétion

| Fonction | Signature | Description |
|---|---|---|
| `succ` | `Automate × set[State] × str → set[State]` | Successeurs d'un ensemble d'états par une lettre |
| `accepte` | `Automate × str → bool` | Teste si un mot est accepté par l'automate |
| `estComplet` | `Automate × set[str] → bool` | Vérifie si l'automate est complet sur un alphabet |
| `estDeterministe` | `Automate → bool` | Vérifie si l'automate est déterministe |
| `completeAutomate` | `Automate × set[str] → Automate` | Retourne l'automate complété (avec état puits) |

### 4. Déterminisation

| Fonction | Signature | Description |
|---|---|---|
| `newLabel` | `set[State] → str` | Construit l'étiquette canonique d'un ensemble d'états |
| `determinisation` | `Automate → Automate` | Retourne l'automate déterminisé |
| `determinisation_etats` | *(auxiliaire récursive)* | Construction incrémentale de l'automate déterminisé |

### 5. Opérations sur les langages

#### Opérations ensemblistes
| Fonction | Signature | Description |
|---|---|---|
| `complementaire` | `Automate × set[str] → Automate` | Automate du langage complémentaire |
| `intersection` | `Automate × Automate → Automate` | Automate de l'intersection des langages (produit synchronisé) |
| `union` | `Automate × Automate → Automate` | Automate de l'union des langages |

#### Opérations rationnelles
| Fonction | Signature | Description |
|---|---|---|
| `concatenation` | `Automate × Automate → Automate` | Automate de la concaténation des langages |
| `etoile` | `Automate → Automate` | Automate de l'étoile de Kleene du langage |

---

## 🚀 Lancement

### Prérequis

- Python 3 je pense minimum pas tester avec autres versions que 3
- Jupyter Notebook ou JupyterLab
- Graphviz (pour la visualisation des automates) si vous voulez

```bash
pip install notebook
# Graphviz : https://graphviz.org/download/
```

### Exécution

```bash
jupyter notebook automate_etudiant.ipynb
```

Exécuter les cellules dans l'ordre. Attention !!! La cellule d'import doit être exécutée en premier.

- `#E:` — liste de tous les états
- `#I:` — états initiaux
- `#F:` — états finaux
- `#T:` — transitions au format `(src lettre dest)`

```python
automate = Automate.creationAutomate("ExemplesAutomates/monAutomate.txt")
automate.show()
```

---

## 💡 Exemples d'utilisation

```python
from transition import *
from state import *
from automateBase import AutomateBase

class Automate(AutomateBase):
    pass

# Création d'un automate
s0 = State(0, True, False)   # état initial
s1 = State(1, False, False)
s2 = State(2, False, True)   # état final

t1 = Transition(s0, "a", s0)
t2 = Transition(s0, "b", s1)
t3 = Transition(s1, "a", s2)

auto = Automate({t1, t2, t3})
auto.show()

# Test d'acceptation
auto.accepte("aba")   # True
auto.accepte("aa")    # False

# Déterminisation
auto_det = auto.determinisation()

# Complémentaire
auto_compl = auto.complementaire({'a', 'b'})

# Intersection de deux automates
inter = auto.intersection(autre_auto)
```

---

## 📚 Tous les concepts majeurs abordés dans ce projet 

- Automates finis déterministes (AFD) et non déterministes (AFN)
- Algorithme de **déterminisation** (construction par sous-ensembles)
- **Complétion** d'un automate (ajout d'un état puits)
- **Complémentaire** d'un langage régulier
- **Intersection** et **union** par produit synchronisé
- **Concaténation** et **étoile de Kleene** (opérations rationnelles)

---

Projet académique — Sorbonne Université. Les fichiers de base (`automateBase.py`, `state.py`, `transition.py`, `sp.py`, `myparser.py`) sont fournis par l'équipe pédagogique et ne doivent pas être modifiés.

-- KW--
