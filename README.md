# G3

# Thème : Optimisation de l'évacuation lors d'un incendie

# Problématique : 
Comment assurer une évacuation rapide et sécurisée des personnes en cas d'un incendie sans provoquer de panique.

Quels facteurs influent sur la dynamique du mouvement de foule lors d'une évacuation en cas d'incendie ?

# Hypothèse : 
Une densité élevée de population peut entraîner des ralentissements et des blocages, qui affectent la vitesse et la fluidité de l’évacuation.

# Objectif :
1. Analyser les principaux facteurs qui influent sur la dynamique du mouvement de la foule :
    - facteurs physiques : la densité de la population, la disposition de l'espace(taille, largeur de sorties)
    - facteurs psychologiques : les comportements des individus(vitesse, direction)
  
    (- facteurs environnementaux : la disposition des sorties de secours(sorties bien réparties et clairement signalées))

2. Proposer des recommandations pour optimiser les stratégies d'évacuation

# Critères d'évaluation :
- Évaluer l'efficacité dans le processus d'évacuation : le nombre d'individus évacués avec succès dans un temps limité.
- Comparer des temps de fuite, du choix des itinéraires d'évacuation etc dans différents scénarios, ainsi que de l'existence ou non d'un blocage au cours de la simulation.

-------------------------------------------------------------------------


# Semaine 05/03/2024
On a commencer par créer des paramètres suivants :
- pos : les coordonnées de personnes
  x1 = 30 #coordonnée de l'axe x
  y1 = 50 #coordonnée de l'axe y
  pos1 = np.array((10,y1))
- sortie : les coordonnées d'une sortie
  sx1 = 0 #coordonnée de l'axe x
  sy1 = 0 #coordonnée de l'axe y
  sortie1 = np.array((sx1,sy1))
- v : la vitesse de personne
  v = 1.5 m/s
- dt : un pas de temps
  dt = 1
- tmax : temps limite

On a implémenté les fonctons suivantes:
- direction(pos,sortie) : calcule la direction du prochain pas
- step(pos,sorties,v,dt) : calcule un pas(step) pour un dt, c'est-à-dire la distance qu'on avance sur l'axe x et l'axe y chaque step
- positions_individu(pos,sortie,v,dt,t_max) : donne une liste des coordonnées d'une personne qui se déplace vers la sortie entre chaque dt dans un temps tmax

On a réalisé notre première graphe qui montre la trajectoire d'une personne:
"""""""""graphe png à ajouter""""""""""""


# Semaine 12/03/2024
On a ajouter une fonction : 
- sortiePlusProche(pos,sortie) : qui choisit la sortie plus proche pour éviter tout le monde se déplace vers la même sortie
  
- S'approcher aux sorties plus proches.
- Chercher les sorties qui sont libres.
- Eviter tous les obstacles.

"""""""""graphe png à ajouter""""""""""""



# Semaine 19/03/2024
Pendant cette séance, on essaie d'implémenter une fonction qui créer des obstacles dans l'espace, mais on trouve que c'est difficile pour l'instant(on peut le faire à la fin si on en a le temps), donc c'est mieux d'introduire d'abord d'un plus grand nombre de personnes dans l'espace et étudier leurs trajectoires en fonction de vitesses et leurs orientations en fonction de distance entre les indivdus.



# Semaine 26/03/2024
Sur la base de ce qu'on a résumé la semaine dernière, on a créé une fonction capable de générer aléatoirement la position initiale de n personnes dans un espace de taille xy : generer_people(nb,x_max,y_max)

On a modifié la fonction step : elle calcule d'abord la sortie plus proche avant de determiner la prochaine step en utilisant la fonction sortiePlusProche, puis on a amélioré la fonction positions_individu



# Semaine 02/04/2024
On a amélioré la fonction positions_individu et on le renomme step_people, elle retourne une liste de coord en 3D : [xy][nb peope][tmax] (coordonnées de tout le monde dans tmax). 

On a fait le graphe pour n personnes qui choisissent leur sortie plus proche
"""""""""graphe png à ajouter""""""""""""


# Vacances
17/04 Chenye :
- modification generer_people : ajouter les caractérisques pour chaque personne -> [numéro, x, y, nv de perception, vitesse], donc chaque personne a sa propre vitesse
- modification step_people : j'ai supprimé le paramètre v, on calcule les steps de personnes avec ses propres vitesses
- nouvelle fonction evacuation(liste_step, sorties) : retourne une liste contenant les numéros de personnes évacuées

18/4 Chenye :
- Ajouter la condition de sortie dans step_people, marqué True dans la dernière colonne si la personne est sortie


# Notre planning :

## Partie Code
1. (C'est fait!) Ajoute une condition dans step_people : quand la personne sort, elle s'arrete à bouger
  - calculer la distance entre la dernière position et la sortie, si c'est inférieur à un nombre très petit(1 par exemple, ca dépend de la dimesion de l'espace et la vitesse), pour le temps qui reste, ses coordonnées ne changent pas


2. (C'est fait!) Faire une file d'attente pour visualiser le nombre de perso évacuées : créer une liste d'individus(chacun a son indice/numéro), pour les individus déjà sortis, on les retire de la liste


Mettre à jour les caractéristiques et l'état des individus en fonction de leur comportement et des facteurs influents:

3. (C'est fait!) niveau de perception(modélisation des différentes réactions et capacités de prise de décision) :
    - générer aléatoirement une valeur de niveau de perception pour chaque individu : soit faible soit élevé
    - différences de vitesse de réaction :  les individus ayant de niveau élevé réagissent plus vite et se déplacent plus rapidement et inversement.

4.(C'est fait!) interactions entre les personnes
    - des idées:
      - vitesse ralentie lorsqu'il y a beaucoup de gens autour de l'individu / devant la sortie(blocages)
      - vitesse plus rapide lorsqu'il y a très peu de gens
      - 2 personnes très proches vont se rencontrer au même point : l'un des deux s'arrête ou ralentit


7.(C'est fait!) Ajouter un paramètre sur la largeur de sortie, donc elle peut faire passer plus d'une personne en même temps, faut prendre compte les coordonnées des sorties, elles ne sont plus un point unique
   -> pour un meme nombre de personnes, le temps nécessaire à une évacuation réussie sera réduit

8. Des métriques(voir schelling) ->graphes pour différent metriques

9.(C'est fait!) Animation /video?

10. Commentaire, conclusion
-> on compare le temps d'évacuation et le nombre d'individus évacués à différentes tailles de sortie
-> les autres voir les critères d'éval en haut



##Partie Présentation
1. Faire le plan
2. Chacun prend ses parties à présenter et faire les diapos
3. écrire le script pour la présentation
4. oublie pas de compléter aussi les commentaires de codes dans jupyter

