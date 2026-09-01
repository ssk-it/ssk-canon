---
id: 01-ou-declarer-le-lien
titre: Où déclarer le lien entre un référentiel et le code qu'il cadre ?
statut: retenue
option_retenue: dans-le-referentiel
---

## Description

Un outil de rédaction invoqué depuis un dépôt de code doit trouver le
référentiel du projet. Encore faut-il que quelque chose, quelque part, dise
lequel.

Le cas n'est pas celui d'un dépôt face à un autre : un projet compte plusieurs
dépôts de code — deux pour l'un des projets observés, trois pour un autre — et
aucun d'eux ne connaît ses frères.

## Options

### dans-chaque-depot-de-code

Chaque dépôt de code porte un fichier nommant son référentiel.

**Pour** — explicite et lisible sur place : celui qui ouvre le dépôt voit
immédiatement où va le cadrage.
**Contre** — écrit *n* fois ce qui est un fait unique, cinq fois pour les deux
projets observés. Rien ne garantit que les copies restent d'accord, et une seule
qui diverge envoie un cadrage dans le mauvais référentiel.

### deduire-par-convention-de-nommage

Déduire le référentiel du nom du dépôt — `<projet>-front` donnerait
`<projet>-cadrage`.

**Pour** — rien à déclarer nulle part.
**Contre** — infirmée par l'observation : la convention tient pour l'un des
projets, mais le second n'a pas de dépôt de cadrage portant ce nom. Un outil qui
devine se trompe silencieusement sur le premier projet hors convention, et
écrire un cadrage au mauvais endroit est plus coûteux que de le déclarer.

### dans-le-referentiel

**Retenue.** Le référentiel déclare les dépôts de code que le projet réalise, et
l'outil reconnaît le dépôt courant au nom que la plateforme lui donne déjà.

**Pour** — une seule déclaration par projet, du côté qui porte la vue
d'ensemble. Rien à ajouter dans les dépôts de code, y compris ceux qu'on
ajoutera plus tard.
**Contre** — le lien n'est pas visible depuis le dépôt de code : celui qui
l'ouvre ne sait pas qu'il est cadré tant qu'il n'invoque pas l'outil.

## Décision

**Déclarer dans le référentiel, reconnaître le dépôt courant à son nom de
plateforme.**

Ce qui tranche : **le référentiel porte la vue « projet », les dépôts de code
n'en portent qu'un morceau.** Le lien appartient donc au premier. C'est la même
raison qui fait que l'histoire ne se stocke pas — la déclarer deux fois, c'est
garantir qu'elle divergera.

Éprouvé sur un dépôt où rien n'avait jamais été configuré : il trouve seul son
référentiel et son dépôt frère.

Le fait retenu contre la convention de nommage vaut d'être noté : elle
fonctionnait sur le projet qu'on avait sous les yeux, et pas sur le suivant. Une
convention qu'on observe sur un exemple n'est pas une règle.
