---
id: 02-garanties-annoncees
titre: Que dire de ce qu'un mode ne garantit pas ?
statut: retenue
option_retenue: annoncer-les-deux-limites
---

## Description

Les trois modes n'offrent pas les mêmes garanties, et la différence n'est pas un
choix de conception : elle est imposée par ce que la plateforme permet.

Vérifié à la source : un accès temporaire se restreint aux dépôts — jusqu'à cinq
cents — et aux permissions, mais **jamais aux chemins**. Il expire au bout d'une
heure. Aucun paramètre ne permet de dire « celui-ci n'écrit que dans ce
répertoire ».

Il en découle que les deux premiers modes laissent un rédacteur autorisé écrire
partout dans les dépôts qu'il atteint, et que l'auteur d'un enregistrement y est
déclaré par l'application plutôt que vérifié.

## Options

### taire-la-difference

Présenter les modes par leur commodité, sans détailler ce qu'ils garantissent.

**Pour** — un choix plus simple à présenter : plus c'est cher, mieux c'est.
**Contre** — laisse croire à une protection qui n'existe pas. Celui qui s'y fie
cesse de se méfier là où il devrait, ce qui est pire que de n'avoir aucune
protection et de le savoir.

### garantir-partout

Chercher à offrir l'autorisation par chemin dans tous les modes.

**Pour** — une promesse uniforme.
**Contre** — impossible sans relais : la plateforme ne sait pas restreindre par
chemin, et un contrôle qui s'exécuterait chez celui qu'il contrôle ne contrôle
rien.

### annoncer-les-deux-limites

**Retenue.** Chaque mode dit jusqu'où descend son autorisation, et d'où vient
l'auteur d'un enregistrement.

**Pour** — un projet peut décider en connaissance de cause. Celui qui a besoin de
la garantie forte sait qu'il lui faut le relais ; celui qui n'en a pas besoin sait
qu'il peut s'en passer.
**Contre** — oblige à expliquer une limite technique à qui ne l'a pas demandée.

## Décision

**Annoncer les deux limites, dans chaque mode.**

Le principe est celui que le produit applique déjà à la divergence entre un
énoncé et sa règle : ce qui pourrait être pris pour une incohérence doit être
expliqué, sans quoi le lecteur perd confiance dans tout le reste.

Ici l'enjeu est plus grand qu'une gêne de lecture. **Une garantie annoncée qui
n'existe pas cause plus de dommage que son absence assumée** : elle transforme
une précaution que l'utilisateur aurait prise en une précaution qu'il croit
inutile.
