---
id: 01-qui-installe-l-automatisation
titre: Qui installe l'automatisation d'un dépôt cadré ?
statut: retenue
option_retenue: l-application-l-installe
---

## Description

L'automatisation vit dans un dépôt public, et s'installe en copiant deux
workflows sous `.github/workflows/`. C'est peu de chose, et c'est resté non fait
sur le premier dépôt réel amorcé par l'application.

Personne ne l'avait remarqué, parce que rien ne le disait. Un dépôt sans
automatisation se comporte normalement jusqu'à la première livraison
incohérente — le moment où il est trop tard.

## Options

### documenter-l-installation

Expliquer la marche à suivre, et laisser le projet copier les deux fichiers.

**Pour** — aucune écriture non sollicitée ; le projet garde la main sur ce que
contient son dépôt, y compris son intégration continue.
**Contre** — c'est exactement ce qui a échoué. La documentation existait ; le
dépôt est resté sans automatisation. Une étape facultative en fin de mise en
route est une étape qu'on ne fait pas.

### installer-sans-demander

Déposer les workflows avec la structure, sans le proposer.

**Pour** — l'oubli devient impossible.
**Contre** — écrire dans l'intégration continue de quelqu'un sans le lui dire
est d'une autre nature qu'y déposer des fichiers de contenu : un workflow
s'exécute, avec les droits du dépôt. Et le droit de l'écrire peut manquer, ce
qui ferait échouer un amorçage dont ce n'était pas l'objet.

### l-application-l-installe

**Retenue.** L'application propose l'installation, cochée d'emblée pendant
l'amorçage, et la propose encore depuis les réglages tant qu'elle manque.

**Pour** — le cas normal ne demande rien, et le refus reste possible. Le dépôt
qui a sauté l'étape s'en voit rappeler l'existence au lieu de l'ignorer
indéfiniment.
**Contre** — deux points d'entrée à tenir plutôt qu'un.

## Décision

**Proposer, coché d'emblée, et le reproposer tant que ça manque.**

Ce qui tranche est ce qu'on a observé : **la documentation n'a pas suffi.** Le
défaut n'est pas que l'installation soit difficile — elle ne l'est pas — mais
qu'elle soit invisible une fois l'occasion passée. Une case cochée traite
l'oubli ; la rappeler dans les réglages traite les dépôts déjà amorcés, que la
case ne rattrape plus.

Cochée d'emblée, et non à cocher : le cas où l'on ne veut pas d'automatisation
existe, mais il est rare et délibéré, alors que l'oubli est fréquent et
involontaire. Le réglage par défaut doit servir le second.

L'installation vient **après** le dépôt de la structure. Le droit d'écrire les
workflows étant distinct, il peut manquer là où le reste passe : dans l'ordre
inverse, un refus laisserait un dépôt à moitié amorcé.
