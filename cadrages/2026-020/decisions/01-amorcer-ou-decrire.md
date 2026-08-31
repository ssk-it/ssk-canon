---
id: 01-amorcer-ou-decrire
titre: Que faire d'un dépôt qui ne porte rien ?
statut: retenue
option_retenue: amorcer-depuis-l-application
---

## Description

Un dépôt fraîchement créé sur la plateforme est vide au sens strict : il n'a
aucun enregistrement, et sa branche principale est annoncée sans exister. Toute
lecture y échoue.

L'application savait le signaler, d'abord mal — « le dépôt n'a pas pu être
chargé », vrai et inutile — puis correctement. Restait à décider si le signaler
suffisait.

## Options

### seulement-le-dire

Nommer la cause, et laisser le projet composer sa structure.

**Pour** — rien à écrire ; le projet garde la main sur ce que contient son dépôt.
**Contre** — il devrait connaître les conventions du format avant d'avoir vu son
premier écran. C'est le moment où l'outil en demande le plus, et celui où il en a
le moins expliqué.

### fournir-un-modele-a-copier

Documenter la structure attendue, et laisser le projet la reproduire.

**Pour** — aucune écriture non sollicitée dans le dépôt de quelqu'un.
**Contre** — déplace le travail sans le supprimer, et une structure recopiée à la
main diverge : un répertoire oublié, un nom au pluriel plutôt qu'au singulier, et
le référentiel ne se charge pas.

### amorcer-depuis-l-application

**Retenue.** L'application dépose la structure, sur demande explicite.

**Pour** — le projet commence en donnant son nom, sans rien connaître du format.
Et ce qui est déposé est exactement ce que l'application sait lire, ce qu'aucune
recopie ne garantit.
**Contre** — l'application écrit dans un dépôt sans passer par une relecture, ce
qu'elle ne fait nulle part ailleurs.

## Décision

**Amorcer, sur demande explicite.**

Ce qui tranche est le moment : **le premier contact avec un outil est celui où il
doit demander le moins.** Un projet qui doit lire la documentation du format
avant de voir son premier écran n'ira pas plus loin.

L'écriture sans relecture est assumée pour ce seul cas, et pour une raison qui ne
vaut que là : il n'y a rien à relire dans un dépôt vide, et une branche ne peut
pas diverger de ce qui n'existe pas.

Chaque répertoire reçoit une note disant ce qu'on y dépose. Le support ne
conservant pas un répertoire vide, il lui faut de toute façon un fichier — autant
qu'il serve plutôt que d'être un fichier vide dont on se demande à quoi il sert.
