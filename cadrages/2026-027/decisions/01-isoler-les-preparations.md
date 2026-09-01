---
id: 01-isoler-les-preparations
titre: Comment préparer plusieurs cadrages sans qu'ils se mêlent ?
statut: retenue
option_retenue: un-espace-lie-par-cadrage
---

## Description

L'outillage travaillait dans la copie du dépôt : s'y placer, y créer une branche,
y enregistrer. Tant qu'un seul cadrage se prépare, rien ne le distingue d'une
bonne solution.

Deux préparations simultanées se mêlent en silence. Celle qui change de branche
la change pour l'autre, et un enregistrement ramasse ce que la voisine écrivait.
Aucune erreur n'est signalée : le travail se retrouve simplement dans le mauvais
cadrage.

## Options

### une-convention-d-usage

Écrire dans la procédure qu'on ne prépare qu'un cadrage à la fois.

**Pour** — rien à construire, et la contrainte est explicite.
**Contre** — interdit ce que le travail réel demande. Deux sujets ouverts en même
temps est le cas ordinaire, pas l'exception, et une règle qui interdit
l'ordinaire est enfreinte le premier jour.

### une-copie-complete-par-cadrage

Recopier le dépôt entier pour chaque cadrage.

**Pour** — isolation totale, sans rien connaître du support.
**Contre** — chaque copie recharge tout, et rien ne relie les copies entre
elles : l'identifiant se choisirait à l'aveugle, sans voir ce qui est déjà pris
ailleurs.

### un-espace-lie-par-cadrage

**Retenue.** Un espace de travail rattaché au dépôt : son répertoire, sa
branche, le même dépôt en dessous.

**Pour** — les espaces s'ignorent l'un l'autre mais partagent l'historique : ce
qui est en cours ailleurs reste visible, ce dont dépend le choix de
l'identifiant. La copie d'origine n'est jamais touchée.
**Contre** — un espace de plus à retirer une fois le cadrage livré, et ce que
l'espace ne partage pas doit être reconstruit.

## Décision

**Un espace lié par cadrage.**

Le critère : **l'isolation ne doit pas couper du reste.** Une copie séparée
isolerait aussi bien, mais perdrait ce qui permet de ne pas choisir deux fois le
même identifiant. Ce qu'on cherche n'est pas la séparation, c'est la séparation
du travail avec le partage de ce qui le situe.

L'option « une convention d'usage » a été écartée sur un motif qui vaut au-delà
de ce cas : **une règle qui interdit ce que le travail demande n'est pas suivie.**
Elle déplace la faute sur celui qui l'enfreint au lieu de traiter la cause.

**Ce qui a été mesuré, et qu'on n'aurait pas deviné** : un espace lié n'hérite
pas de ce qu'un projet installe pour être construit. Reconstituer cela coûte du
temps et de la place — c'est le prix réel de l'isolation, à peser avant d'ouvrir
un second espace pour une correction de deux lignes.

Ce qui reste ouvert est consigné : deux préparations au même instant peuvent
retenir le même identifiant. La procédure dit quoi faire plutôt que d'annoncer
une garantie qu'elle n'a pas.
