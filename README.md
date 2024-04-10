# Hackathon Météo France 


![image](https://github.com/timotheeQueffelec/Hackathon_Meteo_France-OpenGustMap/assets/91546014/f2bc2291-795d-4595-801c-60b78bf2d401)

## Contexte
Ce projet (OpenGustMap) a été réalisé dans le cadre du Hackathon Météo France du 08 et 09 avril 2024.
Le lien vers le repo contenant le code et la présentation est : documentation GitHub

## La problématique
En cas de tempête de vent en France, l’assuré doit faire valoir ses droits auprès de son assureur pour se faire rembourser au titre de la garantie tempête (non pris en charge par le régime CATNAT). Seules les données aux stations météo France sont accessibles aujourd’hui (10 stations par département produisent la vitesse de vent).

## Proposition de valeur
Attester la vitesse de vent observée en France en tout endroit et à toute heure dans le passé avec une précision de 500m.
Application en OPENDATA/OPENSOURCE, idéalement portée par un organisme public indépendant (MétéoFrance, DINUM, DataGouv, MRN...).

Description de la solution et de ses fonctionnalités
On rentre une adresse (normalisée et géocodée par la BAN) et une période début/fin (date et heure). L'application ira rechercher sur la période les vents observés (données météoFrance) à chaque station météo et estime à l'aide du relief (BDALTI) les vents maxima et moyens sur une coordonnée XY en utilisant une méthode de Krigeage.

## Source de données
Les données horaires d’observation météo historiques pour le vent maxi et moyen par station, les données BDALTI de l’IGN pour l’altitude de la station et de l’adresse, la BAN pour normaliser et géocoder l’adresse saisie.

API Météo france pour les données : https://portail-api.meteofrance.fr/web/fr/   
Carte de relief (MNT) IGN : https://geoservices.ign.fr/bdalti

## Méthode utilisée
Interpolation spatiale par « Krigeage » avec prise en compte du relief en utilisant les données météo et la BDALTI pour donner des fichiers de type RASTER (grilles à une maille de 500m)
Le point XY de l’adresse géocodée est rapproché du point le plus proche de la grille pour afficher les valeurs de vents max et moyens.

## Usages possibles
Estimer la vitesse de vent maxi et moyenne à une adresse donnée en France, heure par heure sur une période donnée.
Cette solution s'adresse aux assurés et aux assureurs pour attester du vent observé en cas de sinistre pour la prise en charge (ou non) des dégâts au titre de la garantie tempête. La transparence de l'information (donnée et méthode de calcul) permettra d'améliorer la relation client et de réduire les coûts (prestation d'une attestation météo ~150k€/an pour l'assureur)
