---
id: 03-eprouver-sur-le-corpus
titre: Comment s'assurer qu'une convention non garantie tient ?
statut: retenue
option_retenue: balayer-le-corpus
---

## Description

La dérivation repose sur une convention de rédaction : le choix s'énonce en tête
du corps de l'option retenue, derrière un marqueur. Rien dans le format ne
l'impose, et la vérification ne la contrôle pas.

Une convention qu'on croit tenue sans l'avoir mesurée est une hypothèse. Restait
à savoir ce qu'on faisait de celle-ci.

## Options

### faire-confiance

Se fier à la convention, puisqu'elle est suivie dans les cadrages qu'on a sous
les yeux.

**Pour** — rien à faire.
**Contre** — l'échantillon est celui qu'on a regardé, non le corpus. Un cas
divergent ne se découvrirait qu'à l'écran, sur le cadrage de quelqu'un d'autre.

### imposer-le-marqueur

Faire contrôler le marqueur par la vérification, et refuser une décision qui ne
le porte pas.

**Pour** — la convention devient une garantie, la dérivation ne peut plus
échouer.
**Contre** — durcit le format pour un besoin d'affichage. Une décision reste
valide sans ce marqueur ; refuser une livraison pour cette raison ferait payer
à la rédaction le confort de la consultation.

### balayer-le-corpus

**Retenue.** Éprouver la dérivation sur toutes les options retenues du
référentiel, sans rien imposer au format.

**Pour** — mesure ce qu'on supposait, et l'écart éventuel se voit avant la
livraison plutôt qu'après.
**Contre** — ne vaut que pour l'état constaté ; une rédaction future peut
s'écarter de la convention sans que rien ne le signale.

## Décision

**Mesurer sans contraindre.**

Le balayage a porté sur les **82 options retenues** du référentiel : aucune
justification vide, aucune aberrante. La convention est donc tenue partout — et
c'est bien ce que le code ne présume pas, puisqu'il dégrade proprement quand le
marqueur manque.

Ce qui a tranché : la mesure lève le doute sans rien coûter au format. Imposer
le marqueur aurait fait payer à la rédaction un besoin qui est celui de la
consultation, alors que la dérivation sait déjà se taire.

Enseignement : **une convention qu'on ne veut pas imposer se mesure au moins une
fois.** Sans quoi on ne sait pas si le code dégrade proprement dans un cas rare
ou dans la moitié des cas.
