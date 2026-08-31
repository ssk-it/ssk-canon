---
id: 02-livraison-hors-portee
titre: L'application peut-elle déclarer un cadrage livré ?
statut: retenue
option_retenue: jamais
---

## Description

Le cycle compte quatre statuts, et l'application sait désormais les faire
avancer. La question s'est posée pour le dernier : peut-elle déclarer un cadrage
livré ?

Un fait a tranché avant la discussion. Passer un cadrage à l'état livré déclenche
des contrôles qu'un brouillon ne subit pas : une règle qu'il crée doit alors
exister, ses index dérivés doivent concorder. Vérifié — un cadrage passé à livré
sans que son référentiel suive fait échouer la vérification.

## Options

### comme-les-autres

Traiter la livraison comme n'importe quelle transition.

**Pour** — un cycle homogène, sans cas particulier à expliquer.
**Contre** — un cadrage pourrait être déclaré livré sans que sa demande de fusion
soit fusionnée. Le référentiel affirmerait une livraison qui n'a pas eu lieu, et
la propagation n'aurait rien appliqué.

### parametrable

Laisser chaque projet décider s'il autorise la livraison depuis l'application.

**Pour** — cohérent avec le reste des réglages.
**Contre** — offre un réglage dont aucune valeur n'est correcte. Ce n'est pas une
préférence d'organisation mais une propriété du produit : la livraison est ce que
la fusion établit.

### jamais

**Retenue.** L'application ne déclare jamais un cadrage livré, et aucun réglage
ne peut l'y autoriser.

**Pour** — le référentiel ne peut pas mentir sur ce qui est livré. La livraison
reste ce qu'elle est : la fusion de la demande, suivie de la propagation.
**Contre** — un cas particulier à expliquer dans le cycle.

## Décision

**Jamais, et le réglage lui-même le refuse.**

Un projet qui déclarerait cette transition dans sa configuration la voit écartée,
avec le motif. Interdire à l'interface aurait suffi pour l'usage courant ; le
refuser au réglage vaut mieux, parce qu'un fichier de configuration se modifie à
la main, et qu'une règle qu'on peut contourner en éditant un fichier n'est pas
une règle.

Enseignement à retenir : **tout n'est pas paramétrable.** Un réglage dont une des
valeurs rendrait le produit faux n'est pas un choix offert à l'utilisateur, c'est
une erreur de conception déguisée en souplesse.
