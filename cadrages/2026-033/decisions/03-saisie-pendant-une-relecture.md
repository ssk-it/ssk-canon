---
id: 03-saisie-pendant-une-relecture
titre: Que devient une saisie en cours quand le référentiel est relu ?
statut: retenue
option_retenue: garde-sur-le-cadrage-charge
---

## Description

Le formulaire de reprise se remplit dès que le magasin est prêt, en observant son
état. Toute relecture du référentiel le repeuplait donc depuis le dépôt — y
compris pendant que quelqu'un tapait.

Le défaut existait déjà, sans que personne l'ait rencontré : il fallait recharger
à la main tout en éditant. Ajouter la relecture automatique de la décision 02
l'aurait rendu courant, et aurait transformé une correction en perte de travail.

## Options

### relecture-systematique

Laisser le formulaire se recharger à chaque relecture du référentiel.

**Pour** — le formulaire ne montre jamais d'état vieilli, et rien n'est à retenir.

**Contre** — écrase une saisie en cours, sans avertissement et sans retour
possible. Un rédacteur ne peut pas voir venir un effacement décidé ailleurs.

### garde-sur-le-cadrage-charge

**Retenue.** Le formulaire ne charge un cadrage qu'une fois ; les relectures qui
suivent ne le repeuplent pas. Un échec de chargement, lui, reste retentable.

**Pour** — la saisie est protégée par construction. Le formulaire lit d'ailleurs
le cadrage par l'API, à sa propre initiative : il n'a pas besoin du magasin pour
être à jour au moment où il s'ouvre.

**Contre** — un formulaire resté ouvert longtemps ignore ce qui a changé dans le
dépôt entre-temps. Le conflit se produira à l'écriture, où il est visible et
traité, plutôt qu'à l'affichage, où il ne l'est pas.

### fusionner-les-deux-etats

Comparer ce qui est saisi à ce qui a été relu, et ne remplacer que les champs non
touchés.

**Pour** — préserve la saisie tout en montrant ce qui a changé ailleurs.

**Contre** — demande de savoir ce que « touché » veut dire pour chaque champ, et
produit un état qui n'est ni celui du dépôt ni celui du rédacteur. Beaucoup de
mécanique pour un cas rare, et une fusion silencieuse est plus difficile à
comprendre qu'un conflit annoncé.

## Décision

Ce qui a tranché : **le conflit doit se produire là où il est visible.** Une
saisie effacée par une relecture ne laisse aucune trace ; une écriture refusée
parce que la version lue a changé se voit, s'explique et se reprend — c'est déjà
ce que le cadrage garantit entre deux rédacteurs.

Enseignement de la boucle : une correction qui ajoute un rechargement doit
d'abord regarder ce que ce rechargement traverse. Le défaut ici n'a pas été
introduit par la correction, il a été révélé par elle — à une heure près, il
aurait été livré avec.
