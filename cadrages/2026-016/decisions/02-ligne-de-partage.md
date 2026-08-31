---
id: 02-ligne-de-partage
titre: Que partager, et que laisser à chaque côté ?
statut: retenue
option_retenue: la-dependance-au-support
---

## Description

Partager suppose de tracer une ligne. Elle décide de ce qui devra rester d'accord
entre les deux côtés, et de ce que chacun reste libre de faire à sa manière.

Un découpage par domaine — « tout ce qui touche au référentiel » — aurait forcé à
partager le chargement lui-même, alors que les deux côtés le font pour de bonnes
raisons différemment : l'un lit un disque, l'autre interroge un dépôt distant en
ménageant un quota d'appels.

## Options

### par-domaine

Partager tout ce qui concerne le référentiel, chargement compris.

**Pour** — une seule bibliothèque, une seule façon de lire un référentiel.
**Contre** — obligerait à rendre le chargement indifférent au support, donc à
inventer une abstraction que ni l'un ni l'autre ne réclame. Et le chargement de
l'application porte des contraintes qui n'existent pas ailleurs : régulation des
appels, canaux distincts, progression affichée.

### la-dependance-au-support

**Retenue.** Est commun ce qui raisonne sur un référentiel déjà chargé ; reste
propre à chaque côté ce qui va le chercher.

**Pour** — la ligne est nette et se vérifie mécaniquement : le module partagé ne
doit rien importer du support. Chaque côté garde la liberté sur ce qui le
distingue vraiment.
**Contre** — impose de définir la forme d'un référentiel chargé, sur laquelle les
deux côtés doivent s'accorder.

## Décision

**La dépendance au support trace la ligne.**

Le critère a l'avantage d'être vérifiable plutôt qu'interprétable : on peut
constater qu'un module ne dépend d'aucun support, on ne peut que discuter de
savoir s'il « concerne le référentiel ».

Il a aussi révélé que la séparation existait déjà sans qu'on l'ait vue : le
vérificateur n'employait le chargement qu'à sa première ligne, tout le reste
raisonnant sur des données en mémoire. Extraire n'a pas demandé de réécrire, mais
de déplacer.

La forme du référentiel chargé, que les deux côtés doivent partager, est décrite
par des déclarations de types accompagnant la bibliothèque. Elles ont
immédiatement servi : elles ont refusé un appel où l'application passait ses
entités sous leurs noms à elle, un désaccord qui serait autrement resté invisible
jusqu'à l'exécution.
