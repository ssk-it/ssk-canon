---
id: 01-ou-vivent-les-regles
titre: Où écrire les règles que les deux côtés appliquent ?
statut: retenue
option_retenue: une-bibliotheque-partagee
---

## Description

Vérifier un cadrage pendant sa rédaction demandait d'appliquer, dans
l'application, des règles qui vivaient dans l'automatisation.

Le contexte pesait : la lecture du format était déjà implémentée deux fois, et
une règle du référentiel l'assumait explicitement — la duplication était tenue
pour moins coûteuse que le montage d'un paquet partagé. Ajouter la vérification
aurait doublé une seconde fois la même chose.

## Options

### reecrire-dans-l-application

Implémenter les contrôles côté application.

**Pour** — immédiat, sans dépendance nouvelle ; l'application reste maîtresse de
ce qu'elle affiche.
**Contre** — deux implémentations d'une même règle divergent, et silencieusement,
puisque chacune reste cohérente avec elle-même. Le désaccord n'apparaîtrait qu'au
moment où quelqu'un se fie à l'une contre l'autre.

### copier-en-verifiant-l-identite

Dupliquer le fichier, et faire échouer l'intégration continue si les deux copies
diffèrent.

**Pour** — aucune dépendance, et la divergence est détectée.
**Contre** — déplace le problème sans le traiter : la copie reste une copie, et
le contrôle d'identité interdit toute adaptation légitime à l'un des deux
contextes.

### une-bibliotheque-partagee

**Retenue.** Extraire les règles dans une bibliothèque publiée, que les deux
côtés consomment.

**Pour** — une seule écriture, donc aucune divergence possible. Versionnée : une
évolution ne s'applique qu'aux consommateurs qui l'adoptent. Et le partage
règle du même coup la dette antérieure sur la lecture du format.
**Contre** — une publication à faire à chaque évolution, et une dépendance de
plus.

## Décision

**Une bibliothèque partagée.**

Ce qui a changé depuis la décision d'assumer la duplication n'est pas la
difficulté du partage mais son bénéfice : il ne s'agissait plus d'éviter une
divergence hypothétique, mais d'en empêcher une seconde, certaine, sur des règles
dont l'application allait devenir dépendante.

Le coût s'est révélé plus faible qu'estimé, et pour une raison qui méritait
d'être vue : **rien dans ces règles ne dépendait du support.** Le vérificateur
n'employait le chargement qu'à sa première ligne. Ce qui semblait un module lié à
un système de fichiers était en réalité une fonction pure derrière une façade.

Enseignement transposable : **une dette estimée trop chère à rembourser mérite
d'être réexaminée quand un nouveau besoin s'y adosse** — l'estimation d'origine
portait sur un bénéfice plus petit.
