---
id: RG-regles-partagees
fonctionnalites: [modele-referentiel, stockage-git]
statut: actif
cree_par: 2026-016
modifie_par: []
---

Les règles du format ne sont écrites **qu'une fois**, et les deux côtés qui les
appliquent — l'automatisation et l'application — partagent cette écriture au lieu
de la répéter.

Deux implémentations d'une même règle divergent : c'est une question de temps,
pas de rigueur. Et la divergence est silencieuse, puisque chacune reste cohérente
avec elle-même.

La ligne de partage n'est pas le domaine mais la dépendance au support : ce qui
raisonne sur un référentiel déjà chargé est commun, ce qui va le chercher ne
l'est pas. L'automatisation le lit sur un disque, l'application l'obtient d'un
dépôt distant, et les règles ignorent d'où il vient.

Ce qui est partagé est publié comme une bibliothèque, avec sa version : une
évolution des règles ne s'applique qu'aux consommateurs qui l'adoptent, et
chacun sait laquelle il applique.
