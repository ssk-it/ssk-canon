---
id: RG-parseur-partage
fonctionnalites: [modele-referentiel, stockage-git]
statut: actif
cree_par: null
modifie_par: [2026-016]
---

La lecture du format et les règles qui la vérifient sont **écrites une seule
fois**, dans une bibliothèque que l'application et l'automatisation partagent.

Elles ont d'abord été implémentées deux fois, la duplication étant assumée tant
que le format n'était pas stabilisé : le montage d'un paquet partagé semblait
coûter plus que le risque qu'il éviterait.

Ce n'est plus vrai. Le besoin de vérifier un cadrage pendant sa rédaction aurait
doublé une seconde fois la même règle, et le partage s'est révélé peu coûteux :
rien dans ces règles ne dépendait du support, seulement le chargement qui les
précède.

Ce qui va chercher le référentiel reste propre à chaque côté ; ce qui raisonne
dessus est commun.
