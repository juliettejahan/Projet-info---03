# Projet-info---03
But : développer un indicateur d'accessibilité aux transports. Les niveaux d’accessibilité des transports publics (PTALS) sont une mesure détaillée et précise de l’accessibilité d’un point au réseau de transport en commun, compte tenu du temps d’accès à pied et la disponibilité des services.
Le but est essentiellement de proposer un moyen pour mesurer la densité de réseau de transport public à n’importe quel endroit.

A disposition sur TerriSTORY, nous avons : * Un indicateur sur la densité des infrastructures cyclables * Un indicateur sur l’accessibilité aux services * Et bientôt un indicateur sur l’accessibilité à l’emploi



Modèle : 
Entrée : - Un fichier qui contient un ensemble de vecteurs (X, Y, D), où (X, Y) représentent des coordonnées géographiques et où D correspond à la distance d’éloignement par rapport à ce point (X,Y). Ce vecteur forme donc un cercle de rayon D et de centre (X,Y) 
- Des données relatives aux transports en commun (Bus)

Sortie : deux fichiers csv qui contiennent des données directement exploitables pour présenter cet indicateur sur des clients cartographiques (par exemple : OpenLayers) :
-Un fichier csv qui représente les points (x, y) entrée en paramètres structuré par catégorie : (Id_point, X, Y, PTAL) Ces données de sortie seront utilisées pour modéliser l’accessibilité aux transports en commun au départ de différents emplacement géographique (communes,…) 
-Un fichier csv qui représente les catégories 



Etapes : * Identification des lignes de transports et des arrêts présents dans le périmètre défini en entrée (cercle de rayon D et de centre (X,Y)) 
* Pour chaque ligne de transports identifiée : - Identification de l’arrêt le plus proche 
                                                - Calcul de la distance entre l’arrêt et le point de départ (X,Y), et du temps de parcours associé (à pied) 
                                                - Calcul du temps d’attente moyen au niveau de l’arrêt (basé sur la fréquence du bus) 
                                                - Somme du temps d’attente et du temps de parcours 
                                                - Transformation pour avoir une fréquence (appelé Equivalent Doorstep Frequency - EDF) 
* Calcul d’un indice d’accessibilité IA basé sur les fréquences EDF des différentes lignes de transport disponibles autour du point (X,Y). 
* Rangement de cet indice dans la catégorie d’accessibilité PTAL correspondante (cf. Figure 2 ci-dessous)
