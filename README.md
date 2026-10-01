# Analyse des artistes les plus streamés sur Spotify
Analyse exploratoire des artistes les plus écoutés sur Spotify, à partir d’un classement de 500 artistes et d’un tableau de bord Power BI. Le notebook Python documente l’exploration des données ; le fichier Power BI propose une restitution interactive.
> **Périmètre indiqué par la notice du CSV :** janvier à juillet 2026.

## Contenu du dépôt
Fichier	Rôle
`Most Streamed Artists on Spotify (17_07_2026).csv`	Jeu de données principal : 500 lignes et 10 colonnes.
`Analyse_spotify_python (1).ipynb`	Notebook Python d’exploration et de synthèse.
`Spotify.pbix`	Rapport Power BI associé au CSV.

## Objectif du projet
L’objectif de ce projet est d’explorer les artistes les plus écoutés sur Spotify à partir d’un jeu de données, afin d’identifier les tendances qui caractérisent leur popularité et de comparer leurs performances selon différents indicateurs. L’analyse est réalisée avec Python pour examiner et visualiser les données, puis avec Power BI pour présenter les principaux résultats dans un tableau de bord interactif.

## Données
Le CSV contient les colonnes suivantes :
`Artist` : nom de l’artiste ;
`Sex` : catégorie renseignée dans la source (`Male`, `Female` ou `Mixed`) ;
`Country` : pays associé à l’artiste ;
`Langugage` : orthographe présente dans le fichier source ;
`Primary Genre` : genre principal ;
` Artist Type` : type d’artiste, avec un espace initial dans le nom de colonne ;
`Total Streams (in millions)` : streams totaux, en millions ;
`Lead Streams (in millions)` : streams en tant qu’artiste principal, en millions ;
`Feature Streams (in millions)` : streams en featuring, en millions ;
`Solo Streams (in millions)` : streams solo, en millions.

## Contrôles descriptifs reproductibles
500 lignes, 500 artistes distincts et 23 genres principaux distincts ;
aucune valeur manquante dans les colonnes descriptives et `Total Streams` ;
valeurs manquantes dans `Lead Streams` : 3 ;
valeurs manquantes dans `Feature Streams` : 32 ;
valeurs manquantes dans `Solo Streams` : 7.

## Analyse Python
Le notebook importe :
```python
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt
import seaborn as sns
```
Il réalise les étapes suivantes :
chargement du CSV avec `pandas.read_csv` ;
aperçu des premières lignes, dimensions et informations de structure ;
statistiques descriptives et comptage des valeurs manquantes ;
dénombrement des artistes et des genres ;
fréquences par genre et par catégorie `Sex` ;
répartition de `Sex` par `Country` ;
recherche des trois artistes les mieux classés selon le maximum de `Lead Streams`, `Solo Streams` et `Feature Streams`.

## Résultats 

Analyse	Top 3 observé	Valeur (millions)
`Lead Streams`	Taylor Swift, Drake, Bad Bunny	126177,3 ; 94851,1 ; 82189,3
`Solo Streams`	Taylor Swift, Drake, Billie Eilish	113421,5 ; 53323,9 ; 51567,9
`Feature Streams`	Bad Bunny, Drake, Travis Scott	43710,5 ; 42640,9 ; 30027,0
La distribution `Sex` calculée sur les 500 lignes est : Male 390, Female 88, Mixed 22. Le genre principal le plus fréquent est Hip-Hop (115), suivi de Pop (102) et Rock (60).

## Tableau de bord Power BI

Eléments du rapport :
une page principale nommée « Rapport » ;
un graphique en secteurs portant sur les flux `Solo`, `Lead` et `Feature` ;
un histogramme en colonnes groupées sur `Artist` et `Total Streams`, avec un filtre interne sur les 10 premiers artistes ;
un graphique en aires empilées par `Primary Genre` et `Total Streams`, également limité aux 10 premiers genres dans la requête du visuel ;
une carte remplie par `Country` ;
des segments (slicers) sur `Sex`, `Artist`, et `Langugage` ;
un visuel texte et une ressource graphique Spotify ;
une page d’info-bulle contenant une table croisée par artiste avec les flux `Feature`, `Lead` et `Solo`.

