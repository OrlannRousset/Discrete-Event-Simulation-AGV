# Simulation à événements discrets d’un système logistique avec AGV

## Présentation

Projet réalisé en groupe dans le cadre de l’UE **SY15** à l’Université de Technologie de Troyes (UTT).

L’objectif était de modéliser puis de simuler le fonctionnement d’un système logistique industriel utilisant des véhicules autonomes de manutention (AGV).

À partir de l’observation d’une plateforme physique, nous avons identifié les flux, les différents événements du système ainsi que les temps caractéristiques nécessaires à sa modélisation.

Un simulateur à événements discrets a ensuite été développé en **langage C** afin de reproduire le fonctionnement du système, mesurer ses performances et permettre l’étude de différentes configurations.

---

## Système étudié

La plateforme est composée de :

- 2 AGV assurant le transport des lots
- 1 zone de chargement
- 4 zones de déchargement
- 1 zone de recharge
- une file d’attente pour les lots en attente de prise en charge

Les AGV assurent le transfert des lots depuis la zone de chargement vers différentes zones de dépôt selon une règle d’affectation probabiliste.

---

## Principe de la simulation

Le programme repose sur une approche de **simulation à événements discrets**.

Le temps de simulation évolue directement d’un événement au suivant grâce à un échéancier contenant les prochains événements à traiter.

Les principaux événements modélisés sont :

1. Arrivée d’un nouveau lot
2. Fin du chargement d’un lot
3. Arrivée d’un AGV dans une zone de déchargement
4. Fin du déchargement
5. Retour de l’AGV vers la zone de chargement

Le programme gère également :

- l’état des différentes zones
- la disponibilité des AGV
- les files d’attente
- l’affectation des lots
- les conflits liés à l’occupation des zones

---

## Modélisation probabiliste

Le fonctionnement du système comporte plusieurs phénomènes aléatoires.

Différentes lois de probabilité sont donc utilisées dans la simulation :

### Loi exponentielle

Utilisée pour représenter le temps entre deux arrivées successives de lots.

### Loi discrète

Utilisée pour déterminer la zone de déchargement attribuée à chaque lot.

### Loi normale

Utilisée pour représenter certains temps de :

- chargement
- déplacement
- déchargement

La génération des variables suivant une loi normale est réalisée à l’aide de la **méthode de Box-Muller** à partir de nombres pseudo-aléatoires uniformes.

---

## Indicateurs de performance

Plusieurs KPI sont calculés pendant la simulation afin d’évaluer le fonctionnement du système :

- nombre de lots traités
- nombre d’attentes liées à l’indisponibilité de la zone de chargement
- nombre d’attentes lorsqu’un AGV arrive sur une zone de déchargement occupée
- longueur maximale de la file d’attente
- nombre total de lots arrivés pendant l’horizon de simulation

Ces indicateurs permettent d'analyser le comportement du système et de comparer différentes règles ou configurations de fonctionnement.

---

## Structure du programme

Le simulateur est organisé autour de plusieurs fonctions principales :

- génération des variables aléatoires
- gestion de la file d’attente
- ajout et suppression des événements dans l’échéancier
- traitement des différents types d’événements
- mise à jour de l’état des AGV et des zones
- calcul des indicateurs de performance

L’algorithme principal traite successivement les événements jusqu’à atteindre l’horizon de simulation défini.

