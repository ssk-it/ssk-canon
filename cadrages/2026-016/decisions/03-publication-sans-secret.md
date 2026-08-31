---
id: 03-publication-sans-secret
titre: Comment publier la bibliothèque partagée ?
statut: retenue
option_retenue: depuis-l-integration-continue
---

## Description

Une bibliothèque partagée doit être publiée pour être consommée. Les premières
publications ont été faites à la main, et ont produit précisément ce qu'on
cherchait à éviter.

Une version s'est retrouvée en ligne alors que le dépôt avait déjà avancé, sans
que rien ne le signale — la même divergence silencieuse que le partage venait de
supprimer entre les deux implémentations.

## Options

### a-la-main

Publier depuis un poste, quand on le juge utile.

**Pour** — rien à mettre en place.
**Contre** — la version publiée ne dit pas de quel état du dépôt elle vient. Et
la publication dépend d'un poste particulier, de ses identifiants et de la
mémoire de celui qui la fait.

### depuis-l-integration-continue

**Retenue.** Publier sur pose d'une version étiquetée, après avoir rejoué les
contrôles.

**Pour** — chaque version publiée correspond à un état identifiable du dépôt. Les
contrôles passent avant, ce qui compte d'autant plus qu'une version publiée ne se
retire pas librement. Et l'étiquette est refusée si elle ne correspond pas à la
version déclarée.
**Contre** — une mécanique de plus à maintenir.

## Décision

**Publier depuis l'intégration continue, sur pose d'une version étiquetée.**

L'authentification se fait par attestation : la plateforme d'intégration atteste
de l'identité du traitement, et le registre la vérifie. Aucun secret n'est
détenu, donc aucun à renouveler, aucun à voir fuir, et l'origine de chaque
version publiée est vérifiable par quiconque.

Une leçon de forme mérite d'être gardée : deux suites de versions coexistaient
sur les mêmes étiquettes, l'une pour l'automatisation, l'autre pour la
bibliothèque. Le traitement se serait déclenché sur les étiquettes de la première
en exigeant la version de la seconde. Elles ont été alignées — **deux choses
publiées depuis un même dépôt, et qui évoluent ensemble, n'ont pas de raison de
porter deux numérotations.**
