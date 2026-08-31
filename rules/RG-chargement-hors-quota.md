---
id: RG-chargement-hors-quota
fonctionnalites: [stockage-git]
statut: actif
cree_par: 2026-006
modifie_par: [2026-008, 2026-020]
---

Le chargement d'un dépôt consomme **une seule requête décomptée**, quel que soit
le nombre de fichiers.

L'arborescence est obtenue par un appel unique ; les contenus sont ensuite
récupérés par un canal non décompté.

Cette contrainte n'est pas une optimisation mais une condition de
fonctionnement : sans connexion, la limite est de soixante appels par heure,
alors qu'un référentiel modeste compte déjà plusieurs dizaines de fichiers.

**Le canal des contenus bascule sur celui de l'arborescence** lorsque le premier
ne dessert pas le dépôt, au prix d'un appel par fichier. C'est le cas des dépôts
privés : le canal non décompté leur répond comme à un dépôt absent, même à qui y
a droit. La bascule est automatique — attendre un réglage manuel reviendrait à
présenter un dépôt privé comme introuvable à celui qui vient d'y écrire.

Elle se demande aussi de son propre chef, pour afficher immédiatement ce qui
vient d'être livré, le canal ordinaire servant ses réponses avec un délai.
