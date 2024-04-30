# Modélisation de l'évacuation en cas d'incendie

Notre projet vise à modéliser et simuler l'évacuation de personnes en cas d'urgence dans un espace, comme un incendie. Nous avons utilisé des méthodes de simulation informatique pour étudier les différents scénarios d'évacuation et évaluer l'efficacité d'évacuation. 
L’objectif est d’évacuer les personnes dans un espace rapidement et efficacement en cas d’incendie, ce qui est essentiel  pour minimiser les risques de blessures et de pertes humaines. Nos résultats obtenus indiquent que l'efficacité de l'évacuation dépend de plusieurs facteurs, notamment la vitesse de déplacement des personnes, la densité de population et la configuration des sorties.

# Description synthétique du projet
## Problématique
Quels facteurs influent sur la dynamique du mouvement de foule lors d'une évacuation en cas d'incendie ?

## Hypothèses
- Une densité élevée de population peut entraîner des ralentissements et des blocages, qui affectent la vitesse et la fluidité de l’évacuation.
- Les caractéristiques individuelles des personnes, telles que leur vitesse de déplacement et leur perception du danger, influencent le temps d'évacuation.

## Objectifs
Analyser les principaux facteurs qui influent sur la dynamique du mouvement de la foule :
- Évaluer l'impact des caractéristiques des personnes sur le temps d'évacuation. 
- Comparer les résultats d'évacuation en fonction de la densité de population, du choix de la sortie et des niveaux de perception, de la disposition de l'espace(dimensions, largeur de sorties)
- Proposer les stratégies d'évacuation pour minimiser le temps d'évacuation et maximiser la sécurité des personnes. 

## Critères d'évaluation
Évaluer l'efficacité dans le processus d'évacuation en comparant des temps total et des taux de réussite de l'évacuation dans différents scénarios, ainsi que de l'existence ou non d'un blocage au cours de la simulation.


# Présentation structurée des résultats
## Choix de modélisation et outils
Nous avons utilisé le langage de programmation Python pour modéliser des simulations. Nous avons implémenté un modèle d'évacuation où chaque personne est modélisée comme un agent qui se déplace dans un espace vers une sortie proche. Nous avons utilisé les bibliothèques NumPy et Matplotlib pour manipuler les données et visualiser les résultats.

## Démarches
Pour commencer, nous avons implémenté des fonctions pour générer aléatoirement les identifiants, les positions et les caractéristiques des sorties et des personnes ayant différents niveaux de perception du danger sous forme de tableaux numpy. 
Ensuite, en utilisant ces données, nous arrivons à implémenter plusieurs fonctions telles que : 
- sortiePlusProche : cherche la sortie la plus proche parmi plusieurs sorties
- direction : calcule la direction de personne pour le prochain pas(step)
- step : calcule le prochain step de la personne vers la sortie proche en fonction de leur vitesse
- new_position : met à jours la nouvelle position de la personne
- est_sortie : determine si la personne est sortie
- update_status : met à jours les informations de la personne une fois elle est sortie
- update_times : gère le temps de passage pour chaque sortie

Dans la fonction step_people, nous utilisons les fonctions listées ci-dessus pour faire une simulation d’évacuation complète. step_people retourne un tableau numpy de 3D qui représente les informations des personnes du début jusqu'à la fin de la simulation, ainsi que le temps total de la simulation et le temps de parcours moyen par chaque personne. Nous avons également implémenté la fonction évacuation qui calcule le nombre de personnes évacuées avec succès à la fin de la simulation. 

Après avoir obtenu des données de la simulation, nous souhaitons visualiser les résultats. Ainsi, nous avons mis en œuvre l’animation d'évacuation en fichier GIF et les trajectoires des personnes sous forme de graphe en utilisant la bibliothèque Matplotlib.

Enfin, nous avons réalisé des graphiques et des histogrammes à partir des données obtenues pour analyser les données obtenues, évaluer l'efficacité d'évacuation et discuter des facteurs influençant le temps d'évacuation et le taux de réussite. 

## Résultats et analyses
Nous allons évaluer le temps d'évacuation total, le temps moyen et le taux d'évacuation, qui sont des mesures importantes dans l'évaluation de l'efficacité des stratégies d'évacuation. 
Le temps d'évacuation total représente la durée totale nécessaire pour que l'ensemble des personnes évacuent l'espace, tandis que le temps moyen indique la moyenne du temps nécessaire à chaque personne pour atteindre une sortie depuis son point de départ. 
Le taux d'évacuation représente le pourcentage de personnes évacuées par rapport au nombre total de personnes dans l'espace.

### Densité de population
Situation : Nous avons un espace de dimensions 30 m x 30 m, équipé de 2 sorties pour l'évacuation. Nous simulons le déplacement de 10 jusqu'à 100 personnes à travers cet espace, avec une vitesse variant entre 0.3 et 0.8 m/s pour le niveau de perception faible, et entre 1.0 et 1.6 m/s pour le niveau élevé.
1. Temps d'évacuation total/moyen en fonction de densité de population
2. Taux d'évacuation en fonction de la densité de personnes (pour 120 secondes)¶

### Nombre de sorties 
Situation : un espace de 30x30 avec deux sorties disponibles. Nous avons pris en compte tous les niveaux de perception du danger avec deux plages de vitesses : de 0.3 à 0.8 m/s pour la faible et de 1.0 à 1.6 m/s pour l'élevée.
1. Temps d'évacuation en fonction du nombre de sortie
2. Taux d'évacuation en fonction du nombre de sortie

### Niveau de perception du danger
Situation : Nous avons un espace de dimensions 30 mètres x 30 mètres, équipé de 2 sorties pour l'évacuation. Nous simulons le déplacement de 60 personnes à travers cet espace, avec une vitesse variant entre 0.3 et 0.7 m/s pour le niveau de perception faible, et entre 1.0 et 1.8 m/s pour le niveau élevé. 
1. Temps d'évacuation total en fonction du niveau de perception du danger
2. Taux d'évacuation en fonction du niveau de perception¶


En résumé, le temps d’évacuation total est un indicateur important pour mesurer l’efficacité globale de l’évacuation. La réduction du temps total indique une meilleure capacité des personnes à réagir pendant l'évacuation. Elle peut être affectée par des facteurs externes tels que la densité de population et la configuration des sorties. 
D'ailleurs, en raison des différences de vitesse de déplacement et de perception du danger entre les personnes, le temps d'évacuation moyen sera différent pour chaque personne. Cela peut être affecté par des différences individuelles et des comportements imprévisibles des personnes.
Cependant, le taux de réussite de l'évacuation n'est peut-être pas le meilleur indicateur pour définir une évacuation réussie. Par exemple, il peut ne pas tenir compte des personnes qui sont déjà en danger pendant l'évacuation.

(https://ibb.co/47Y61RY)
