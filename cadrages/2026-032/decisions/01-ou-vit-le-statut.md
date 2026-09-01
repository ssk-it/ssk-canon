---
id: 01-ou-vit-le-statut
titre: Où vit le statut d'un cadrage ?
statut: retenue
option_retenue: deduit-du-depot
---

## Description

Un cadrage a été fusionné en portant `statut: brouillon`, et ses impacts n'ont
pas été propagés : le propagateur ne retient que les cadrages déclarés livrés. Le
relevé a montré trois cadrages sur vingt-neuf dans ce cas.

La question n'est pas de rattraper ces trois-là, mais de savoir si le statut doit
continuer à être déclaré dans le fichier, alors que le dépôt porte déjà les faits
qui le déterminent.

La difficulté tient à ce que le propagateur s'exécute dans une action, sur une
copie du dépôt : il ne voit que des fichiers. Retirer le champ sans lui donner
autre chose à lire le rendrait incapable de distinguer un cadrage livré d'un
brouillon fusionné par erreur.

## Options

### champ-declare

Le statut reste dans le frontmatter. L'application l'écrit, et une action le
passe à livré au moment de la fusion.

**Pour** — le référentiel reste lisible sans interroger la plateforme, y compris
hors ligne ou une fois le dépôt archivé. Le propagateur ne change pas. C'est ce
que la règle en vigueur affirmait, avec ces raisons.

**Contre** — deux sources pour un même fait, et c'est déjà ce qui a échoué. Le
champ ne devient sûr que si personne ne peut plus l'écrire à la main, ce qui
demande de contrôler chaque écriture au lieu de supprimer le problème. Il
contredit l'invariant du projet : l'histoire se dérive, elle ne se stocke pas.

### champ-restreint-a-livree

Le fichier ne porte que `livree`, absent tant que le cadrage ne l'est pas. Les
trois autres statuts se dérivent de la demande de fusion.

**Pour** — le propagateur garde un fichier à lire, et la duplication disparaît
pour les états transitoires.

**Contre** — un statut mi-dérivé mi-déclaré demande de retenir lequel est lequel.
Le champ reste écrit par une machine dans un fichier que des humains relisent, ce
qui invite à le corriger à la main. Et il ne survit pas à l'examen : si la
présence sur la branche principale suffit à établir la livraison, le champ ne dit
rien de plus.

### deduit-du-depot

**Retenue.** Aucun champ. Le statut se lit de l'état du dépôt : branche seule,
demande de fusion ouverte, demande validée, présence sur la branche principale.

**Pour** — une seule source, celle qui ne peut pas se tromper sur ce qu'elle
contient. Le propagateur devient plus simple, non plus complexe : il retient ce
que porte la branche principale, sans rien interroger, et garde son idempotence.
La divergence constatée devient impossible plutôt que rattrapée.

**Contre** — le statut d'un cadrage non livré n'est plus lisible hors de
l'application : il faut lister branches et demandes de fusion, ce qui consomme du
quota d'API là où la lecture des contenus n'en consommait pas. Le chantier touche
la lecture, l'écriture, le tri et l'affichage, et vingt-neuf fichiers sont à
nettoyer.

## Décision

Ce qui a tranché : **la propagation n'a pas besoin du champ**. L'objection qui
tenait — le propagateur ne voit que des fichiers — tombe dès lors que « présent
sur la branche principale » établit la livraison. Le propagateur lit alors ce
qu'il a sous la main, et son idempotence est préservée.

L'objection de la lisibilité hors ligne subsiste, et c'est le prix payé. Elle
pesait moins que la divergence : un référentiel lisible qui affirme un statut
faux est pire qu'un référentiel qui demande la plateforme pour le connaître.
