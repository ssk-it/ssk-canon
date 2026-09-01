---
id: 02-lire-une-branche-entiere
titre: Que lire sur la branche d'un cadrage en cours ?
statut: retenue
option_retenue: lire-tout-ne-garder-que-les-cadrages
---

## Description

Une branche de cadrage porte le cadrage, mais peut aussi porter des règles
nouvelles, une configuration modifiée, des décisions. Restait à décider ce que
l'application en retient.

## Options

### lire-le-seul-fichier-de-cadrage

Charger uniquement `cadrages/<id>/cadrage.md` de la branche.

**Pour** — un appel, et rien d'autre ne peut troubler l'état courant.
**Contre** — le cadrage arriverait sans ses décisions, qui sont des fichiers
voisins, et sans ses pièces jointes. Il faudrait redire ici comment un cadrage
se compose, alors que la lecture le sait déjà : deux descriptions du même
assemblage, qui divergeront.

### lire-la-branche-comme-etat-courant

Charger la branche entière et la substituer au référentiel.

**Pour** — montre le référentiel tel qu'il sera après livraison, ce qui a son
intérêt pour relire.
**Contre** — répond à une autre question. Le référentiel décrit ce que le
produit fait **aujourd'hui** ; une branche non livrée décrit une proposition.
Les confondre ferait passer pour acquis ce qui est encore en discussion.

### lire-tout-ne-garder-que-les-cadrages

**Retenue.** Charger la branche comme un référentiel entier, et n'en retenir que
les cadrages.

**Pour** — la lecture n'est écrite qu'une fois : le cadrage arrive complet, avec
ses décisions et ses impacts, sans rien redire de sa composition. Et l'état
courant reste celui de la branche principale.
**Contre** — lit des fichiers dont on ne gardera rien.

## Décision

**Lire la branche entière, ne retenir que ses cadrages.**

Le critère : **ne pas écrire deux fois comment un cadrage se compose.** Une
seconde description, plus étroite, aurait divergé de la première dès le premier
champ ajouté — et l'écart se serait vu à l'écran sous la forme d'un cadrage
amputé, sans que rien ne dise pourquoi.

Le coût de lire des fichiers inutiles est réel mais borné : les demandes
ouvertes sont peu nombreuses, ce sont les cadrages en cours.

**Ce qui a été appris en faisant** : le rendu a montré un défaut que ni le
compilateur ni les tests n'auraient vu. La ligne d'un cadrage est une grille à
trois colonnes ; y ajouter la marque de provenance en créait une quatrième, qui
retombait sous l'identifiant. C'est la cinquième fois sur ce produit qu'un
défaut d'affichage n'apparaît qu'à l'écran.
