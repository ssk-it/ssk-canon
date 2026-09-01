---
id: 01-a-quoi-un-acces-s-attache
titre: À quoi un accès s'attache-t-il ?
statut: retenue
option_retenue: organisation-redefinissable
---

## Description

L'application ne retenait qu'un accès. Renseigner celui d'un second projet
écrasait le premier sans rien dire, et le projet de la veille s'annonçait alors
introuvable — la pire des formes d'échec, puisque la cause était invisible.

Restait à décider à quoi rattacher un accès.

**Un fait a d'abord corrigé la question posée.** On supposait qu'un accès ne
pouvait couvrir qu'une organisation, et que travailler sur deux en imposait
deux. C'est faux : un accès à portée fine couvre plusieurs organisations, et
celui qu'on employait atteignait les quatre organisations du rédacteur.

Le besoin de plusieurs accès demeure, pour d'autres raisons — un accès peut être
restreint à une sélection de projets, une organisation peut exiger son
approbation, et deux accès expirent à des dates différentes.

## Options

### un-acces-par-projet

Un accès rattaché à chaque projet cadré.

**Pour** — le plus précis : un accès en lecture pour l'un, en écriture pour
l'autre, dans la même organisation.
**Contre** — un accès à renseigner par projet, même quand le même conviendrait
aux cinq projets d'une organisation. La granularité coûte à chaque ajout de
projet, pour un besoin qui ne se présente que rarement.

### un-acces-par-organisation

Un accès rattaché à l'organisation seule.

**Pour** — c'est la frontière que la plateforme emploie : approbation,
politiques et restrictions se décident à cette échelle. Un seul accès sert tous
les projets d'une organisation.
**Contre** — ne permet pas de distinguer deux projets d'une même organisation,
alors que le cas existe : écrire dans l'un, lire seulement dans l'autre.

### organisation-redefinissable

**Retenue.** Un accès par organisation, qu'un projet peut redéfinir. Le plus
précis l'emporte.

**Pour** — le cas courant ne demande rien de plus qu'un accès par organisation ;
le cas particulier reste possible sans avoir été anticipé.
**Contre** — deux niveaux à comprendre et à présenter, pour un second niveau qui
ne sert pas encore.

## Décision

**Un accès par organisation, redéfinissable par projet.**

Ce qui tranche : **la plateforme décide à l'échelle de l'organisation, et c'est
donc là que l'accès se règle par défaut.** Rattacher au projet serait plus
précis mais imposerait le coût de cette précision à chaque projet, y compris aux
quatre sur cinq qui n'en ont pas besoin.

La gradation évite le défaut symétrique : sans elle, accorder un accès
particulier à un projet obligerait à le redéclarer pour tous les autres de son
organisation.

**Le fait qui a corrigé la question mérite d'être retenu** : la prémisse du
besoin — « une organisation, un accès » — était fausse, et seule l'interrogation
de la plateforme l'a montré. Le besoin réel était ailleurs, et concevoir sur la
prémisse aurait produit une solution juste pour de mauvaises raisons, donc
fragile au premier cas qui s'en écarte.
