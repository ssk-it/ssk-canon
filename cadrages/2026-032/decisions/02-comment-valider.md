---
id: 02-comment-valider
titre: Comment valider un cadrage quand on ne peut pas approuver sa propre demande ?
statut: retenue
option_retenue: approbation-native-et-repli-commente
---

## Description

Le statut « validée » se dérive d'une approbation de la demande de fusion. Mais
la plateforme refuse qu'on approuve la sienne : l'auteur d'un cadrage ne peut pas
le valider.

L'examen a précisé le cas réellement bloqué. Ce n'est pas le mode d'accès : un
client qui relit un cadrage dont il n'est pas l'auteur approuve sans obstacle,
même quand chacun apporte son propre jeton. Le cas bloqué est celui où la
personne qui valide n'a pas de compte sur la plateforme, ou est l'auteur.

Ce cas n'est pas marginal. Un client valide un cadrage sans nécessairement
disposer d'un compte sur la plateforme de dépôt, et c'est même la situation
ordinaire d'un projet où le client relit sans coder.

## Options

### approbation-seule

Seule l'approbation native porte la validation. Là où elle est impossible,
l'application désactive l'action en expliquant pourquoi, et le cycle va de la
relecture à la livraison sans passer par la validation.

**Pour** — un seul mécanisme, natif, avec sa péremption et son attribution.
Aucune double lecture. « Validée » signifie alors toujours qu'un tiers a relu,
ce qui lui donne sa valeur.

**Contre** — un client sans compte ne peut jamais valider, alors que sa
validation est le fait que le produit existe pour consigner. L'état devient
inatteignable dans une situation courante, ce qui n'est pas une limite technique
mais un renoncement fonctionnel.

### commentaire-edite

La validation est un commentaire structuré, qu'on édite pour l'annuler en y
ajoutant une date et un motif d'annulation.

**Pour** — un seul emplacement à lire, et l'état courant tient dans un
commentaire.

**Contre** — l'API ne rend qu'un état du commentaire, le dernier. L'édition
efface la date à laquelle la validation valait, et rien n'empêche de réécrire
l'annulation pour retrouver un état validé. C'est un champ d'historique déguisé,
dans un support qui garantit moins que Git — exactement ce que le projet
s'interdit.

### approbation-native-et-repli-commente

**Retenue.** L'approbation native partout où elle est possible ; ailleurs, un
commentaire structuré. Aucun des deux ne se modifie : l'état courant est celui du
dernier événement en date, validation ou annulation.

**Pour** — le cas courant emprunte le mécanisme natif, avec sa péremption et son
attribution vérifiée. Le cas bloqué est couvert sans inventer d'historique
réécrit. Le commentaire nommant le commit qu'il vise, la péremption est
reproduite là où elle n'existe pas nativement.

**Contre** — deux chemins à lire et à tenir d'accord, avec une règle de
préséance. C'est la double lecture qu'on cherchait à éviter, et elle restera.

## Décision

Ce qui a tranché : **un client sans compte doit pouvoir valider**. C'est le seul
argument qui justifie un second mécanisme, et il suffit — aucun mécanisme natif
ne couvre ce cas, et le renoncement priverait le produit de ce qu'il sert à
consigner.

L'édition a été écartée pour une raison mesurable et non pour une préférence :
l'API ne rend qu'un état du commentaire. Un événement par annulation coûte le
même effort et conserve les dates.

Le champ nommant le commit visé n'est pas un ornement : sans lui, une validation
par commentaire survivrait à la modification de son objet, là où l'approbation
native se périme. Les deux formes se comportent alors pareil, ce qui est la
condition pour que la règle de préséance ait un sens.
