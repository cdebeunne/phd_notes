# Construction de modèles 3D à partir de données vidéo fisheye : application à la localisation en milieu urbain

Author: Julien Moreau

Thèse écrite en 2016

Notes:
---
* Utilisation d'un système stéréo fisheye

Chapitre 2 biblio:
* La géométrie épipolaire est le nom donné aux règles géométriques qui régissent les relations
entre deux points de vue
* Utilisation de mire possible si la baseline est faible
* Etat de l'art de la mise en coresp stéréo

Chapitre 3 sur la calibration d'une caméra fisheye:
* Méthode automatique basée sur la méthode des 9 points
* Orb et descripteur CenSurE = méthode rapide
* test différents modèles de projection: equidistance, angle equisolide, stéréographique
* Dans tout les cas, 1 paramètre: a (=1/f pour equi 1/2f pour les autres)
* Matrice essentielle != matrice fondamentale: elle relie les projections fisheye q1 et q2 au lieu des points images
* Méthode des 9 points initialisée avec a* obtenu avec les données constructeur
* Scale factor pour passer de la mesure en pixel à la mesure en m
* Ne pas utiliser les points du centre pour la calibration car distorsion trop faible
* Méthode pour obtenir des repères épipolaires alignés avec la matrice essentielle E et des images: rien compris 
* Vérification de la stabilité du calibrage en reproduisant 1000 fois la calib
* Images de synthèse avec blender


Chapitre 4 corespondance stereo fisheye

* Carte dense des disparités
* Calcul de la position 3D avec la loi des sinus
* Mise en correspondance avec une méthode basée sur les graphes (programmation dynamique)