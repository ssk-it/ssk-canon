---
id: 03-portee-de-l-immuabilite
titre: Que peut-on encore modifier dans un cadrage livré ?
statut: retenue
option_retenue: immuabilite-totale
---

## Description

Le référentiel est la projection des cadrages livrés. Modifier un cadrage livré
change donc rétroactivement ce que le référentiel devrait contenir, sans que rien
ne le repropage.

Reste à savoir jusqu'où l'interdiction porte. Le fichier de cadrage est
clairement en cause, puisqu'il porte les énoncés et les impacts. Les décisions
sont plus discutables : elles ne sont pas propagées, et on peut vouloir consigner
après coup un point tranché tardivement.

## Options

### cadrage-fige-decisions-ouvertes

Le fichier de cadrage et ses impacts sont figés à la livraison ; les décisions
restent ouvertes en ajout.

**Pour** — ce qui alimente la propagation est protégé, et une décision tardive
trouve où se consigner sans qu'il faille ouvrir un cadrage pour elle seule.
L'ajout ne réécrit rien.

**Contre** — la validation a porté sur ce qui était présent au moment où elle a
été donnée. Une décision ajoutée ensuite n'a été relue par personne, et se trouve
pourtant dans un cadrage que le référentiel présente comme validé puis livré. La
validation cesse de dire ce qu'elle prétend.

### immuabilite-totale

**Retenue.** Rien ne se modifie sous le répertoire d'un cadrage livré — ni
l'énoncé, ni les impacts, ni les décisions, ajouts compris. Ce qu'on veut changer
se change par un nouveau cadrage.

**Pour** — la règle tient en une phrase et ne demande aucune exception à retenir.
Ce qui a été relu est exactement ce qui reste. Le contrôle est simple : toute
modification sous le répertoire d'un cadrage présent sur la branche principale
est refusée.

**Contre** — corriger une faute de frappe dans un cadrage livré demande un
nouveau cadrage, ce qui est disproportionné. Une décision tranchée juste après la
livraison doit trouver un autre support.

## Décision

Ce qui a tranché : **admettre les ajouts viderait la validation de son sens**.
Un cadrage validé puis complété n'a plus été relu dans l'état où il se trouve, et
le référentiel continue pourtant de l'afficher comme relu.

Le coût est assumé et connu : une correction mineure passera par un nouveau
cadrage. C'est le prix d'une règle sans exception, et une exception « pour les
petites corrections » n'aurait pas de frontière défendable.
