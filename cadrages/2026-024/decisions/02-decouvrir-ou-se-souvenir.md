---
id: 02-decouvrir-ou-se-souvenir
titre: Comment retrouver les projets sur lesquels on travaille ?
statut: retenue
option_retenue: les-deux-sans-se-remplacer
---

## Description

Retaper l'adresse d'un projet à chaque fois qu'on y revient est une friction qui
n'apprend rien à personne. Mais se souvenir ne suffit pas : un projet mémorisé
peut être devenu inaccessible, et rien ne le dit avant d'échouer à le lire.

## Options

### seulement-se-souvenir

Retenir les projets ouverts, sans rien demander à la plateforme.

**Pour** — aucun appel, fonctionne sans accès, et couvre le cas de celui qui
revient sur ses projets habituels.
**Contre** — ne distingue pas un projet accessible d'un projet qui ne l'est
plus. Le rédacteur choisit un projet mémorisé et découvre l'échec après coup.

### seulement-decouvrir

Ne proposer que ce que l'accès autorise, sans mémoire.

**Pour** — toujours exact, et découvre les projets qu'on ne connaissait pas.
**Contre** — sans accès, plus rien n'est proposé, y compris le projet public
qu'on consultait la veille. Et la liste ignore ce sur quoi on travaille
réellement : elle mêle les référentiels aux dépôts de code.

### les-deux-sans-se-remplacer

**Retenue.** La mémoire d'abord, la découverte ensuite, présentées ensemble.

**Pour** — la mémoire est immédiate et survit à l'absence d'accès ; la
découverte dit ce qui est réellement autorisé, ce qu'aucune mémoire ne sait. Les
projets mémorisés s'affichent avant que la découverte n'aboutisse.
**Contre** — un appel par projet pour savoir lequel porte un référentiel.

## Décision

**Les deux, chacune pour ce qu'elle sait.**

Le critère : **la mémoire dit ce sur quoi on travaille, la découverte dit ce
qu'on peut atteindre.** Ce sont deux questions différentes, et aucune des deux
réponses ne se déduit de l'autre.

Un projet n'est retenu **qu'une fois ouvert avec succès**, non quand on le
demande. Le défaut inverse était présent et n'a pas été trouvé par
raisonnement : la mémorisation avait d'abord été placée au changement de projet,
si bien que le projet ouvert au démarrage — le cas de tout utilisateur
existant — n'y serait jamais entré.

Les projets portant un référentiel sont distingués **par vérification, non par
supposition** : le nom d'un dépôt ne dit pas s'il porte un référentiel ou du
code. Les autres restent proposés, un dépôt vide qu'on veut amorcer n'ayant pas
encore de référentiel.
