---
id: RG-projets-connus
fonctionnalites: [authentification, consultation-cadrage]
statut: actif
cree_par: 2026-024
modifie_par: []
---

L'application **retient les projets déjà ouverts**, et propose ceux que l'accès
courant autorise.

Deux origines qui ne se remplacent pas. La mémoire garde les projets sur
lesquels on travaille, y compris sans accès ; la découverte dit ce que l'accès
autorise réellement, ce qu'aucune mémoire ne peut savoir — un projet privé sans
l'accès qu'il faut s'annonçait « introuvable ».

**Un projet n'est retenu qu'une fois ouvert avec succès.** Retenir ce qu'on a
seulement demandé remplirait la liste de projets qu'on n'a jamais pu lire.

Les projets qui portent un référentiel sont proposés en premier, **vérifié et
non supposé** : le nom d'un dépôt ne dit pas s'il porte un référentiel ou du
code. Les autres restent proposés — un dépôt vide qu'on veut amorcer n'a pas
encore de référentiel.

La découverte interroge **tous les accès connus**, non le seul accès courant :
celui-ci ne couvre que le projet ouvert, et s'y limiter masquerait justement les
projets qu'on cherche en voulant changer.
