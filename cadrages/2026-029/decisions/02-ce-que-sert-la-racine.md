---
id: 02-ce-que-sert-la-racine
titre: Que montre l'application quand l'adresse ne désigne aucun projet ?
statut: retenue
option_retenue: ecran-de-choix
---

## Description

L'adresse portant désormais le projet, la racine `/` n'en désigne aucun. Elle
reste pourtant l'adresse qu'on tape, celle du signet, celle où l'on retombe.

Il fallait décider si elle devine un projet ou si elle en demande un.

## Options

### rediriger-vers-le-dernier

Rediriger `/` vers le dernier projet ouvert, mémorisé par le navigateur, ou vers
le projet de démonstration à défaut.

**Pour** — un pas de moins pour qui revient sur le même projet, c'est-à-dire le
cas courant. L'application s'ouvre sur du contenu plutôt que sur une question.
**Contre** — rien ne distingue alors « je reviens » de « je viens en ouvrir un
autre ». Et sur un poste neuf, ou après un vidage du navigateur, la redirection
choisit le projet de démonstration : quelqu'un venu pour son propre projet
consulte celui d'un autre sans qu'aucun écran ne le lui dise.

### ecran-de-choix

**Retenue.** `/` sert un écran « Ouvrir un projet » : les projets déjà ouverts,
ceux que l'accès autorise, et un champ de saisie. Rien n'est chargé tant qu'aucun
projet n'est choisi.

**Pour** — l'état « aucun projet » devient représentable, donc affichable.
Chaque projet reste à un clic pour qui revient. Aucun quota n'est consommé pour
un projet que personne n'a demandé.
**Contre** — un écran de plus avant le contenu, pour l'usage le plus fréquent.

## Décision

**Ce qui a tranché : une redirection ne peut pas se tromper visiblement.**
Ouvrir le mauvais projet d'office produit un référentiel qui s'affiche
normalement — des domaines, des règles — et rien n'indique qu'il n'est pas
celui qu'on cherchait. Le coût de l'écran supplémentaire se paie une fois par
session ; le coût d'un référentiel lu pour un autre se paie en décisions prises
sur la mauvaise base.

Le contre reste vrai et n'est pas nié : c'est un pas de plus pour l'usage
courant. Il est réduit en plaçant les projets récents en tête, sans attendre que
la découverte des dépôts autorisés aboutisse — ils sont déjà connus, et les
faire attendre un appel réseau les rendrait moins accessibles qu'avant.

## Ce qu'on a appris en faisant

Le garde de route recharge le référentiel **seulement si le projet change**.
Sans ce contrôle, chaque navigation interne — ouvrir un domaine, revenir à la
liste — rejouerait la cinquantaine de lectures d'un chargement complet, sur un
quota de soixante requêtes par heure pour un lecteur non connecté. La règle
`RG-chargement-hors-quota` tenait déjà cette contrainte pour le chargement
initial ; l'adressage par URL la fait porter aussi sur la navigation.
