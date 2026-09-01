---
id: 04-reference-de-l-outil
titre: Comment le référentiel référence-t-il l'outil de vérification ?
statut: retenue
option_retenue: branche-principale
---

## Description

Les deux workflows du référentiel consomment l'action de vérification et de
propagation par `uses: ssk-it/ssk-canon-action@v1`.

L'examen a montré que ce tag **n'a jamais été redéplacé** : il pointe encore sur
la toute première release, alors que l'outil en est à sa sixième. Le référentiel
exécutait donc un code d'origine tout en croyant suivre les versions publiées.

C'est le même défaut que celui que ce cadrage corrige par ailleurs : un geste
manuel qu'il faut penser à refaire, et qui ne signale rien quand on l'oublie.

## Options

### tag-latest

Créer un tag `latest`, redéplacé à chaque publication.

**Pour** — le nom dit l'intention, et se lit sans connaître l'histoire des
versions.

**Contre** — `latest` n'est pas une notion de la plateforme : ce qui suit `@` est
une référence Git, jamais résolue vers une release. Le tag devrait être créé et
redéplacé à la main, exactement comme `v1` — donc oublié de la même façon.

### tag-de-version-redeplace

Garder `@v1`, et le redéplacer à chaque publication.

**Pour** — c'est la convention des actions publiées, que les consommateurs
extérieurs attendent.

**Contre** — le geste a déjà été oublié, et rien ne le rappelle. Le référentiel
n'est pas un consommateur extérieur : il éprouve l'outil, et attendre une
publication pour le faire retarde ce qu'on cherche à mesurer.

### branche-principale

**Retenue.** `uses: ssk-it/ssk-canon-action@main`.

**Pour** — la référence est vraie par construction, sans geste à ne pas oublier.
Le référentiel éprouve l'outil dès qu'il avance, ce qui est son rôle : c'est ici
que les défauts se voient en premier.

**Contre** — un merge sur la branche principale de l'outil change immédiatement
la vérification du référentiel, sans étape de publication pour l'amortir. Une
régression atteint donc le référentiel avant d'atteindre les autres projets.

## Décision

Ce qui a tranché : **ce dépôt-ci est le banc d'essai de l'outil, non son
consommateur ordinaire**. Un tag l'y protégerait d'une régression qu'il est
justement chargé de trouver.

Les projets tiers gardent un tag de version : la contrepartie acceptée ici — être
exposé le premier — n'a de sens que pour le dépôt qui développe l'outil.
