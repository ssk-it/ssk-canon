---
id: RG-chargement-hors-quota
fonctionnalites: [stockage-git]
statut: actif
cree_par: 2026-006
modifie_par: []
---

Le chargement d'un dépôt consomme **une seule requête de quota**, quel que soit
le nombre de fichiers.

L'arborescence est obtenue par un appel unique à l'API ; les contenus sont
ensuite récupérés par un canal non décompté du quota.

Cette contrainte n'est pas une optimisation mais une condition de
fonctionnement : le quota anonyme est de soixante requêtes par heure et par
adresse IP, alors qu'un référentiel de taille modeste compte déjà plusieurs
dizaines de fichiers. Charger fichier par fichier par l'API rendrait
l'application inutilisable dès la seconde visite.
