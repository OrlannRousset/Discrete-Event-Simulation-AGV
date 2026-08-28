Simulation à événements discrets d’un système logistique avec AGV

Présentation

Projet réalisé en groupe dans le cadre de l’UE SY15 à l’Université de Technologie de Troyes (UTT).

L’objectif du projet était de modéliser et simuler le fonctionnement d’un système logistique industriel comprenant deux véhicules autonomes (AGV), une zone de chargement et plusieurs zones de déchargement.

À partir de l’observation du système réel, le travail consistait à identifier les flux, les événements et les temps caractéristiques, puis à développer un simulateur à événements discrets en langage C permettant d’analyser les performances du système et d’étudier l’impact de modifications de fonctionnement.

Système étudié

Le système simulé comprend :

2 AGV assurant le transport des lots

1 zone de chargement

4 zones de déchargement

une file d’attente pour les lots en attente de prise en charge

des temps de déplacement, de chargement et de déchargement représentés par des lois probabilistes

Principe de la simulation

Le programme repose sur une approche de simulation à événements discrets.

Les principaux événements représentés sont :

arrivée d’un nouveau lot

fin du chargement d’un lot

arrivée d’un AGV dans une zone de déchargement

fin du déchargement

retour de l’AGV

Un échéancier conserve les prochains événements à traiter. La simulation avance directement d’un événement au suivant jusqu’à atteindre l’horizon de simulation défini.

Modélisation probabiliste

Plusieurs lois sont utilisées pour représenter le caractère aléatoire du système :

loi exponentielle pour les temps entre deux arrivées de lots

loi discrète pour l’affectation des lots aux différentes zones de dépôt

loi normale pour certains temps de chargement, déplacement et déchargement

La génération des valeurs suivant une loi normale est réalisée à l’aide de la méthode de Box-Muller à partir de nombres pseudo-aléatoires uniformes.

Indicateurs de performance

Le simulateur mesure plusieurs indicateurs afin d’analyser le fonctionnement du système :

nombre de lots traités

nombre d’attentes liées à l’indisponibilité de la zone de chargement

nombre d’attentes lorsqu’un AGV arrive sur une zone de déchargement occupée

longueur maximale de la file d’attente

Ces indicateurs permettent de comparer différentes configurations ou règles de fonctionnement du système.
