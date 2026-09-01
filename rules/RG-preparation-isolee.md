---
id: RG-preparation-isolee
fonctionnalites: [redaction-cadrage, stockage-git]
statut: actif
cree_par: 2026-027
modifie_par: []
---

Chaque cadrage se prépare dans un **espace de travail qui lui est propre**, non
dans la copie du dépôt.

Plusieurs cadrages se préparent en même temps, et une copie partagée les mêle :
changer de branche la change pour tous, et un enregistrement ramasse ce qu'une
autre session écrivait. Le travail se perd sans qu'aucune erreur ne soit
signalée.

L'espace porte son propre répertoire et sa propre branche, sur le même dépôt.
La copie d'origine reste sur sa branche principale, intacte.

**L'identifiant est choisi en regardant ce qui est en cours ailleurs**, non le
seul contenu du dépôt : un cadrage préparé dans un autre espace n'y est pas
encore, et deux préparations choisiraient le même numéro.

Une course subsiste, et se dit plutôt que de se taire : deux préparations
lancées au même instant peuvent retenir le même identifiant, la seconde étant
alors refusée à la livraison. Annoncer une garantie qu'on n'a pas est pire que
d'énoncer la limite.

Reprendre un espace déjà préparé le rend tel quel : c'est le cas ordinaire d'un
travail qu'on poursuit, non une collision.
