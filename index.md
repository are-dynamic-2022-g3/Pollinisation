## Description du projet 

Notre projet consiste à étudier le comportement des différents pollinisateurs et comment les plantes évoluent et se propagent. Nous avons décidé d’étudier le comportement des principaux pollinisateurs : le vent, les insectes et animaux pollinisateurs (ici on prendra les abeilles), et l’humain.  


## Problématique 

Quel est le moyen de pollinisation le plus efficace au bon développement des plantes ?
<div style="text-align:right"><img src="https://www.lesdorloteurs.fr/uploads/2021/05/2.png" /></div>

## Description du modèle  

Notre modèle permet de simuler l’évolution des plantes dans un environnement donné grâce à la propagation du pollen par les différents pollinisateurs mis en jeu et leurs caractéristiques (ex : le sens du vent, le nombre d’abeilles, ...). Notre modèle dynamique fonctionne ainsi : 


### Base du modèle :

Le modèle consiste en une parcelle de terrain carrée dans laquelle se situe une population de plantes. Chaque jour, les plantes sont arrosées et on suppose qu'aucune espèce envahissante ne perturbe la croissance de l'espèce. 
Chaque individu de la population sera représenté par un chiffre (float) qui indiquera son "âge" (ou son état de vie). 

- 0.0 correspond à une surface vide; 
- 0.5 correspond à un germe qui a été inséré dans la surface; 
- Une valeur dans l'intervalle {1.0 ; 2.0} décrit le cycle de vie de la plante (1.0 étant son éclosion et 2.0 la "veille" de sa mort (l'individu est encore fertile) pour simplifier le modèle). 
 
De plus, on notera un indicateur "P" (PLEIN), "M" (MOITIE) et "V" (VIDE) qui informera sur la réserve de nectar d'un individu (il faut 2 jours à un individu pour "remplir ses réserves"). 


### Critères de la dispersion du pollen par le vent :

1. La fonction cherche au hasard une plante qui est arrivée à maturité (>1.25) et une direction dans laquelle le vent souffle; 
2. Elle calcule les coordonnées d'une surface sur laquelle déposer le germe de la plante émettrice (elle ne cherche qu'UNE FOIS un emplacement, si cet emplacement n'est pas libre/en dehors de la parcelle, la pollinisation ne se fait pas); 
3. Le germe est déposé dans la surface obtenue (0.5) et devra croître pour donner une nouvelle plante. 
 
**AINSI, ON CONTRÔLERA LA FORCE DU VENT EN APPLIQUANT PLUSIEURS FOIS LA FONCTION (le nombre de répétitions correspond à l'index de la force du vent).**


### Critères de la pollinisation par les abeilles :

1. On libère un nombre d'abeilles que l'utilisateur définit dans la parcelle; 
2. Chaque abeille visite un individu mature au hasard (par simplicité), se nourrit du nectar de la plante et collecte son pollen (on notera que s'il y a plus d'abeilles que d'individus, certaines abeilles ne feront "rien"); 
3. L'abeille dépose le pollen récupéré sur une surface comprise dans un rayon de 2 surfaces ("2 cases dans le tableau, selon x et y") et si celle-ci est vide, alors un germe y est planté. 


### Critères du modèle de pollinisation par l'homme :

L'humain pourra polliniser "à la main" un maximum de 6 plantes par jours. Il s'occupe seul de la parcelle en suivant la démarche ci-dessous : 

- On (utilisateur) définit une liste de (6) coordonnées de SURFACES VIDES dans lesquelles il souhaite faire apparaître de nouveaux individus (si la liste comporte plus de 6 coordonnées, il n'en prendra que 6 au hasard); 
- L'humain introduit des germes sur les surfaces désignées, sans toucher aux réserves de nectar des individus. 



## Hypothèse 

Le moyen de pollinisation par les abeilles est le plus efficace.

 

## Objectif

Mesurer l'efficacité des moyens de pollinisation. 

 

## Critères d’évaluation  

L’évolution des fleurs sur la parcelle en fonction du temps et l'influence des facteurs sur leur reproduction. 

Le nombre de plantes à la fin d'un cycle de pollinisation.

 

## Résultats  

Simulation de l'évolution du nombre de plantes et du nombre de germes grâce au vent avec un taux de germination :

![Vent_taux](https://github.com/are-dynamic-2022-g3/Pollinisation/blob/gh-pages/Images/res_vent_taux_moy_12_10j.PNG)


Simulation de l'évolution du nombre de plantes et du nombre de germes grâce aux abeilles avec un taux de germination :

![Abeilles_taux](https://github.com/are-dynamic-2022-g3/Pollinisation/blob/gh-pages/Images/res_abeilles_taux_moy_9_10j.PNG)


Simulation de l'évolution du nombre de plantes et du nombre de germes grâce au vent (avec taux de germination) et aux abeilles (avec taux de germination) :

![Multi_taux](https://github.com/are-dynamic-2022-g3/Pollinisation/blob/gh-pages/Images/res_multi_taux_moy_8_5_10j.PNG)


Simulation de l'évolution du nombre de plantes et du nombre de germes grâce aux abeilles sur une plus grande parcelle :

![Abeilles_taux_grandeparcelle](https://raw.githubusercontent.com/are-dynamic-2022-g3/Pollinisation/gh-pages/Images/res_abeilles_moy_grande_parcelle.PNG)


La pollinisation par le vent semble être plus efficace que la pollinisation par les abeilles. Cependant, cela résulte du fait que la puissance du vent utilisée dans nos graphiques est très forte (= 12) et ce, durant plusieurs jours, ce qui rend la pollinisation par le vent vraiment très efficace. De plus, nous appliquons ces mesures dans une parcelle restreinte, ce qui rend la pollinisation par les abeilles moins efficace. On peut le voir sur le dernier graphique : nous avons agrandi la taille de la parcelle et on remarque que la pollinisation par les abeilles est désormais plus performante dans une parcelle de terre plus grande.  



## Compte rendu


### Semaine 1 

Lors de cette première séance, nous avons fait beaucoup de recherches sur notre sujet. Nous avons récolté de nombreuses informations à propos des différents pollinisateurs : insectes, animaux, eau, vent, être-humain (pollinisation artificielle), … 

Nous avons décidé d’utiliser les abeilles pour représenter le comportement de tous les insectes et animaux pollinisateurs dans notre modèle. 

Nous avons également prévu de simuler la pollinisation par le vent, et par l’humain. 


### Semaine 2 

Cette semaine, nous avons débuté le programme en codant tout d’abord plusieurs fonctions permettant de créer une parcelle de terre vide, mais aussi de simuler l’évolution des fleurs au cours du temps jusqu’à leur mort.  

Ensuite, nous avons codé une fonction permettant de simuler le comportement des abeilles au sein de la parcelle, et ainsi la propagation du pollen parmi les fleurs. Nous avons également codé la fonction simulant la pollinisation par le vent selon ses différentes caractéristiques, c’est-à-dire son sens, mais également sa force. De plus, la fonction “humain”, consistant à laisser l’utilisateur du modèle la possibilité de polliniser lui-même, a aussi été créé lors de cette séance.  

Finalement, nous avons les simulations des comportements de tous les pollinisateurs que nous voulions étudier. 


### Semaine 3 

Aujourd’hui, nous avons beaucoup avancé dans le code de notre modèle dynamique. En effet, nous avons réalisé 3 versions finales de l’étude de la pollinisation selon le nombre de pollinisateurs et le nombre de jours voulus : 

- Etude de l’évolution de la pollinisation par un pollinisateur pendant un jour. 
- Etude de l’évolution de la pollinisation par un pollinisateur durant plusieurs jours. 
- Etude de l’évolution de la pollinisation par deux pollinisateurs durant plusieurs jours. 

D’autre part, nous avons aussi créé le site web via GitHub et avons fait plusieurs recherches afin de comprendre comment utiliser au mieux GitHub et ainsi pouvoir alimenter le site en intégrant photos, liens, etc. 

  
### Semaine 4 

Cette semaine nous avons commencé à travailler la partie graphique de notre modèle. Pour cela, nous avons utilisé la bibliothèque graphique tkinter sur Python. Nous avons ainsi pu créer un rectangle vert numéroté représentant la surface de la parcelle vide étudiée lors de notre simulation. 

Nous avons également travaillé sur plusieurs visualisations graphiques modélisant l’évolution de la pollinisation au cours du temps et selon le ou les pollinisateurs mis en jeu, via Matplotlib. 

Nous avons aussi continué nos recherches et avons établi les informations principales à mettre dans notre site web (description du projet, hypothèses, ...).

  
### Semaine 5

Cette semaine, sur tkinter, nous avons réussi à créer une fleur, et la faire apparaître sur la parcelle. 

Nous avons aussi amélioré le programme en implémentant le taux de germination des plantes (la probabilité qu’elles ont de créer une nouvelle fleur ou non). Nous pouvons par exemple voir à l’aide de ces deux graphiques que le nombre de plantes est plus important sur le graphique sans le taux de germination que celui avec :







   - Sans taux
                              
                              
                              
                              
        ![Vent_avec_taux](https://raw.githubusercontent.com/are-dynamic-2022-g3/Pollinisation/gh-pages/Images/Vent_sans_taux.png)
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   - Avec
                        
                        
                        
                        
                        
        ![Vent_sans_taux](https://raw.githubusercontent.com/are-dynamic-2022-g3/Pollinisation/gh-pages/Images/Vent_avec_taux.PNG)
 

### Semaine 6

Cette semaine nous avons finalisé la mise en forme de notre site web. Nous avons également continué la partie graphique sur tkinter en modélisant l’apparition des abeilles sur la parcelle de terre. De plus, nous avons continué de créer des visualisations graphiques représentant différents graphiques montrant l’évolution du nombre de plantes (et du nombre de germes pour certains) selon les différents pollinisateurs modélisés (un ou plusieurs). Ensuite, nous avons essayé de rattacher la partie graphique (tkinter) au corps du programme (sur Jupyter Notebook) afin de mieux visualiser le comportement des abeilles au sein de la parcelle.  



## Membres du groupe 

Simon RIGOLLIER 

Huy Lam HUYNH 

Maryam NEMRA

Mélanie DELLUC 
