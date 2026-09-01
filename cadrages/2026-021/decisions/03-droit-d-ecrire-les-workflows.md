---
id: 03-droit-d-ecrire-les-workflows
titre: Que faire du droit d'écrire les workflows, que tous les accès n'ont pas ?
statut: retenue
option_retenue: proposer-et-nommer-le-refus
---

## Description

La plateforme traite l'écriture sous `.github/workflows/` comme une permission
distincte de l'écriture de fichiers, parce qu'un workflow s'exécute avec les
droits du dépôt. Un accès qui écrit partout ailleurs peut être refusé là seul.

Mesuré sur notre propre installation : une demande d'accès portant `contents` et
`workflows` est refusée d'un « les permissions demandées ne sont pas accordées à
cette installation », alors que la même sans `workflows` est accordée. Le mode
« identité tierce » ne peut donc pas installer l'automatisation tant qu'un
administrateur ne l'a pas accordé à l'application inscrite.

Le mode « jeton personnel » n'a pas cette limite : le rédacteur peut s'accorder
ce droit lui-même en produisant son jeton.

## Options

### attendre-la-permission

Ne rien proposer tant que l'accès courant ne porte pas le droit.

**Pour** — aucun échec possible ; on ne propose que ce qu'on peut tenir.
**Contre** — savoir si le droit est là suppose de l'éprouver, donc d'écrire. La
seule façon de ne jamais échouer serait de ne jamais proposer en identité
tierce, alors que c'est le mode où l'installation manque le plus souvent.

### installer-par-une-demande-de-fusion

Passer par une branche et une demande de fusion, comme le reste des écritures.

**Pour** — cohérent avec le reste ; la relecture rattrape ce que l'automatisation
aurait dû vérifier.
**Contre** — la même permission est requise pour écrire un workflow sur une
branche : le détour ne lève pas l'obstacle. Et une automatisation qui attend une
relecture ne protège rien pendant qu'elle attend.

### proposer-et-nommer-le-refus

**Retenue.** Proposer dans tous les cas, et faire dire au refus quelle
permission manque.

**Pour** — le rédacteur en jeton personnel se la donne en une minute. Celui en
identité tierce apprend quoi demander à son administrateur, ce qu'un échec muet
ne lui aurait jamais appris.
**Contre** — un échec possible là où l'on avait proposé.

## Décision

**Proposer, et nommer la permission qui manque.**

Le critère est celui de `RG-message-nomme-la-cause`, appliqué à un cas qu'il
n'avait pas prévu : **un droit manquant n'est pas une panne, et les présenter
pareil envoie chercher au mauvais endroit.** « L'installation a échoué » fait
soupçonner l'application ; « cet accès ne permet pas d'écrire les workflows »
désigne l'action à mener, et celui qui peut la mener.

Ce qui reste ouvert est assumé : en identité tierce, l'installation échouera
jusqu'à ce que la permission soit accordée à l'application inscrite. Le cadrage
le consigne plutôt que de le découvrir deux fois.
