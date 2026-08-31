---
id: 03-canal-des-contenus
titre: Comment lire un dépôt que le canal ordinaire ne dessert pas ?
statut: retenue
option_retenue: bascule-automatique
---

## Description

Les contenus d'un référentiel sont lus par un canal non décompté, ce qui permet
de charger des dizaines de fichiers sans épuiser le quota. Ce canal **ne dessert
pas les dépôts privés** : il leur répond comme à un dépôt absent, même à qui y a
droit.

La bascule vers l'autre canal était prévue depuis longtemps, mais comme un
réglage à activer soi-même. Et elle n'avait jamais fonctionné : la lecture
demandait du texte brut par un chemin qui analyse une structure, et échouait sur
une réponse pourtant valide.

Le défaut est resté invisible aussi longtemps qu'aucun dépôt privé n'a été
ouvert.

## Options

### laisser-le-reglage-manuel

Conserver la bascule comme une case à cocher.

**Pour** — le projet décide, et le coût supplémentaire — un appel par fichier —
n'est jamais subi sans qu'on l'ait voulu.
**Contre** — un dépôt privé se présente comme introuvable à celui qui vient d'y
écrire. Il faudrait avoir lu la documentation pour comprendre qu'une case
décochée en est la cause.

### toujours-employer-l-autre-canal

Renoncer au canal non décompté.

**Pour** — un seul chemin, aucune bascule.
**Contre** — épuiserait le quota d'une consultation anonyme en un chargement.
C'est la contrainte qui a façonné toute la stratégie de lecture.

### bascule-automatique

**Retenue.** Basculer de soi-même quand le premier canal ne dessert pas le dépôt,
en gardant le réglage manuel pour l'autre besoin.

**Pour** — un dépôt privé se lit sans rien comprendre au montage. Le canal non
décompté reste employé partout où il fonctionne.
**Contre** — le coût supplémentaire est encouru sans qu'on l'ait demandé, sur les
dépôts qui l'exigent.

## Décision

**Basculer automatiquement, et garder le réglage pour l'autre usage.**

Le critère : **un réglage n'a de sens que si son absence laisse un choix.** Ici
il n'y en a pas — un dépôt privé se lit par ce canal ou ne se lit pas — et
demander à l'utilisateur de deviner cela n'est pas un choix, c'est une énigme.

Le réglage garde son autre raison d'être : afficher immédiatement ce qui vient
d'être livré, le canal ordinaire servant ses réponses avec un délai. Là, le
compromis est réel et appartient au lecteur.

Enseignement à retenir : **une voie de secours qui n'a jamais servi n'a jamais
été éprouvée.** Celle-ci était écrite, documentée, et cassée depuis toujours.
