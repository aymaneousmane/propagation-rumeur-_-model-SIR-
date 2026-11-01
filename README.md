# Propagation d'une rumeur — modèle SIR

Ce projet étudie la propagation d'une rumeur sur un réseau social à l'aide d'une simulation stochastique inspirée du modèle SIR. Chaque personne est représentée par un nœud d'un graphe et la rumeur se propage uniquement entre personnes connectées.

Le modèle distingue trois états :

- **S — Susceptible** : la personne n'a pas encore entendu la rumeur ;
- **I — Infected** : la personne connaît et propage activement la rumeur ;
- **R — Recovered** : la personne a rejeté ou oublié la rumeur.

## Démonstration et documents

- [Voir l'animation de la simulation](./SIR.mp4)
- [Ouvrir le notebook](./propagation_rumeur_SIR.ipynb)
- [Consulter le document de modélisation](./Mod%C3%A9lisation_de_la_propagation_des_rumeurs_sur_les_r%C3%A9seaux_sociaux.pdf)

## Principe du modèle SIR

Dans sa formulation classique, le modèle est décrit par le système :

```text
dS/dt = -βSI/N
dI/dt =  βSI/N - γI
dR/dt =  γI
```

où :

- `N = S + I + R` est la population totale ;
- `β` représente le taux de transmission de la rumeur ;
- `γ` représente le taux de rejet ou d'oubli de la rumeur.

Le notebook adapte ce modèle à un réseau social et à un temps discret. À chaque étape, une personne dans l'état `I` peut transmettre la rumeur à chacun de ses voisins `S` avec la probabilité `β`, puis peut passer dans l'état `R` avec la probabilité `γ`. Les mises à jour sont synchronisées à l'aide d'une copie de l'état courant.

## Réseau social simulé

Le réseau est généré avec le modèle **Barabási–Albert** :

- 50 nœuds représentant les personnes ;
- 2 connexions ajoutées lors de l'intégration d'un nouveau nœud ;
- quelques nœuds très connectés, analogues à des influenceurs ;
- une propagation limitée aux voisins reliés par une arête.

La génération du graphe et la sélection des personnes initialement infectées utilisent une graine aléatoire afin de rendre l'expérience reproductible.

## Paramètres de la simulation

| Paramètre | Valeur | Description |
|---|---:|---|
| `N` | `50` | Nombre de personnes dans le réseau |
| `beta` | `0.3` | Probabilité de transmission par contact |
| `gamma` | `0.1` | Probabilité de rejet par étape |
| `initial_infected` | `2` | Nombre de personnes propageant initialement la rumeur |
| `frames` | `100` | Nombre d'étapes de l'animation |

## Installation

Python 3 et Jupyter sont nécessaires. Installez les dépendances avec :

```bash
pip install numpy matplotlib networkx notebook
```

## Exécution

1. Clonez le dépôt :

   ```bash
   git clone https://github.com/aymaneousmane/propagation-rumeur-_-model-SIR-.git
   cd propagation-rumeur-_-model-SIR-
   ```

2. Lancez Jupyter Notebook :

   ```bash
   jupyter notebook
   ```

3. Ouvrez `propagation_rumeur_SIR.ipynb` et exécutez les cellules dans l'ordre.

L'animation affiche simultanément le réseau coloré selon l'état de chaque nœud et l'évolution des populations `S`, `I` et `R` au fil du temps.

## Technologies utilisées

- Python 3
- NumPy
- NetworkX
- Matplotlib
- Jupyter Notebook

## Auteur

Projet réalisé par [aymaneousmane](https://github.com/aymaneousmane).
