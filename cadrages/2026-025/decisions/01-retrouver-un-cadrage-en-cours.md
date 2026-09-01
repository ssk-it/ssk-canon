---
id: 01-retrouver-un-cadrage-en-cours
titre: Comment retrouver un cadrage qui n'est pas encore livré ?
statut: retenue
option_retenue: par-les-demandes-de-fusion
---

## Description

Un cadrage non livré vit sur une branche. Encore faut-il savoir laquelle, et
l'application n'avait pour cela que le nom.

Le problème s'est révélé sur un dépôt réel : un cadrage correctement formé,
posé sur sa branche avec sa demande de fusion, restait invisible.

## Options

### chercher-par-le-nom-de-branche

Reconnaître les branches à leur nom, selon une convention déclarée.

**Pour** — un seul appel, aucune dépendance à autre chose que Git.
**Contre** — **infirmée par l'usage.** L'application créait `cadrage/<id>` avec
une barre oblique, tandis que l'outillage de rédaction enseignait
`cadrage-<id>` avec un tiret. Deux conventions pour une seule chose, qui ne se
sont jamais rencontrées. Un cadrage rédigé à la main était donc absent de la
liste sans que rien ne l'explique.

### imposer-la-convention-partout

Garder la recherche par nom, et corriger l'outillage pour qu'il emploie le même.

**Pour** — le défaut immédiat disparaît, sans changer la façon de chercher.
**Contre** — traite l'occurrence, pas la cause. Une convention qui doit être
respectée par tout ce qui touche au dépôt — l'application, l'outillage, et
quiconque crée une branche à la main — sera enfreinte de nouveau, et le symptôme
sera le même : un cadrage bien formé, invisible, sans message.

### par-les-demandes-de-fusion

**Retenue.** Lire les demandes de fusion ouvertes, et prendre la branche que
chacune désigne.

**Pour** — le nom cesse d'avoir des conséquences. Un cadrage est visible dès
qu'il a une demande de fusion, ce que le cycle de vie exige déjà pour le livrer.
**Contre** — un appel pour lister les demandes, plus un par branche lue. Peu
nombreuses par nature : ce sont les cadrages en cours.

## Décision

**Suivre les demandes de fusion, non les noms de branches.**

Le critère qui tranche : **un nom est une convention, une demande de fusion est
un fait.** Faire dépendre la visibilité d'un cadrage d'une convention revient à
la faire dépendre de la mémoire de celui qui crée la branche.

L'option « imposer la convention partout » aurait fonctionné et n'a pas été
retenue pour cette raison : elle laissait le mécanisme fragile intact. La
divergence constatée n'était pas une négligence — les deux conventions étaient
écrites, chacune dans son coin, et chacune paraissait la bonne à qui la lisait.

Ce qui reste vrai : l'application continue de nommer les branches qu'elle crée.
Mais ce nom n'est plus qu'une commodité de lecture pour l'humain, sans effet sur
ce que l'outil sait retrouver.
