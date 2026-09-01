---
id: 03-eprouver-l-outillage
titre: Comment éprouver un outillage qui s'exécute ailleurs ?
statut: retenue
option_retenue: l-executer-pour-de-bon
---

## Description

L'outillage de rédaction ne s'exécute pas dans l'application : il tourne chez le
rédacteur, dans un environnement qu'aucun test du produit n'atteint. Deux
défauts y ont été trouvés, et aucun n'était visible autrement qu'en l'exécutant
pour de bon.

## Options

### relire-et-raisonner

Vérifier par lecture que l'outillage est correct.

**Pour** — immédiat, et suffisant pour ce qui relève de la forme.
**Contre** — les deux défauts trouvés étaient invisibles à la lecture. Le code
faisait exactement ce qu'on lui avait demandé ; c'est ce qu'on lui avait demandé
qui était faux.

### une-sonde-simplifiee

Éprouver le mécanisme sur un cas réduit, puis en déduire que le vrai cas passe.

**Pour** — rapide à écrire, et répond à la question posée.
**Contre** — **infirmée en cours de route.** Une sonde avait établi que
l'injection de commande fonctionnait ; elle employait une commande autorisée
d'emblée. La vraie commande demandait une approbation à chaque invocation et
faisait échouer le chargement. La sonde répondait à une question voisine de
celle qu'on croyait poser.

### l-executer-pour-de-bon

**Retenue.** Exécuter l'outillage tel qu'un rédacteur l'exécutera, depuis un
dépôt où rien n'a été préparé, et exécuter la commande d'installation dans un
environnement neuf.

**Pour** — les deux défauts sont apparus ainsi, et seulement ainsi.
**Contre** — plus lent, et demande de fabriquer les conditions.

## Décision

**Exécuter pour de bon, dans les conditions du rédacteur.**

Ce qui tranche est ce qu'on a mesuré : **une sonde simplifiée peut répondre à
une autre question que celle qu'on croit poser**, et rendre une réponse
rassurante sur un mécanisme qui ne fonctionne pas.

Le second défaut confirme la règle par un autre chemin : les exemples affichés
étaient composés avant que le référentiel ne soit chargé, si bien qu'un projet
déclarant déjà ses dépôts se voyait proposer l'exemple générique. Les tests
passaient, le compilateur ne disait rien — c'est l'écran qui l'a montré, pour
la quatrième fois sur ce produit.

Ce n'est pas un enseignement sur l'outillage, mais sur la manière de l'éprouver.
Il vaut pour tout ce qui s'exécute hors de l'application : les workflows, le
composant d'échange, et ce qui viendra.
