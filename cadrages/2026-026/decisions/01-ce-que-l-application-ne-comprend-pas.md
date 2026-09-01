---
id: 01-ce-que-l-application-ne-comprend-pas
titre: Que faire du contenu qu'une entité porte et que l'application ne présente pas ?
statut: retenue
option_retenue: conserver-tel-quel
---

## Description

Un cadrage se compose de parties reconnues — objectif, parcours, énoncés — et
peut en porter d'autres que son auteur a jugées utiles. L'application
reconstruisait le fichier à partir des seules parties reconnues.

Le défaut n'a pas été trouvé par raisonnement ni par les contrôles : il est
apparu en relisant l'historique d'un dépôt réel, où un enregistrement retirait
vingt-trois lignes. C'étaient cinq questions ouvertes, instruites, sur un cadrage
en brouillon — exactement ce qu'un brouillon porte de plus utile.

## Options

### presenter-tout-ce-qui-existe

Ajouter à l'éditeur chaque partie qu'un cadrage peut porter.

**Pour** — rien n'échappe à l'application, et tout devient éditable.
**Contre** — impossible à tenir : un auteur écrit ce qu'il veut, et la liste des
parties possibles n'est pas close. Le défaut réapparaîtrait à la première partie
qu'on n'avait pas prévue, avec le même silence.

### refuser-ce-qui-n-est-pas-reconnu

Signaler au chargement qu'une partie n'est pas comprise, et empêcher
l'enregistrement.

**Pour** — aucune perte possible, et le rédacteur est prévenu.
**Contre** — bloque l'édition d'un cadrage parfaitement valide, pour la seule
raison qu'il contient quelque chose de plus. Punit l'auteur d'avoir écrit
davantage.

### conserver-tel-quel

**Retenue.** Ce que l'application ne présente pas, elle le transporte sans
l'interpréter et le réécrit tel quel.

**Pour** — rien ne se perd, quelle que soit la partie, y compris celles qu'on
n'a pas imaginées. L'application n'a pas besoin de comprendre ce qu'elle
préserve.
**Contre** — ces parties ne sont pas éditables depuis l'application, et se
retrouvent regroupées à la fin plutôt qu'à leur place d'origine.

## Décision

**Conserver sans interpréter.**

Le critère : **la perte silencieuse est le seul défaut qu'un outil de mémoire ne
peut pas se permettre.** Tout le reste se corrige ; celui-là détruit ce qu'on lui
a confié, et ne se découvre qu'en relisant l'historique — c'est-à-dire rarement,
et trop tard.

L'option « présenter tout » a été écartée parce qu'elle repose sur une
énumération qui ne peut pas être complète. Une correction qui suppose qu'on a
tout prévu échoue exactement là où l'on n'avait pas prévu.

**Ce que le défaut apprend sur les contrôles** : aucun test ne l'a vu, parce
qu'aucun test n'écrivait un cadrage portant autre chose que ce que l'éditeur
connaît. Les contrôles éprouvaient ce qu'on avait conçu, non ce qu'un auteur
écrit. Le jeu d'essai était fait à l'image de l'outil, quand il aurait dû l'être
à l'image de ce qu'il rencontre.
