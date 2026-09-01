---
id: 2026-020
titre: Amorcer un dépôt vide
domaines: [cadrage, persistance]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-amorcage-depot, operation: cree }
  - { regle: RG-documentation-non-entite, operation: cree }
  - { regle: RG-chargement-hors-quota, operation: modifie }
  - { regle: RG-message-nomme-la-cause, operation: touche }
  - { regle: RG-verification-integrite, operation: touche }
  - { regle: RG-format-fichier, operation: touche }
---

## Objectif

Permettre à un projet de commencer.

Un dépôt fraîchement créé sur la plateforme ne porte rien — pas même une branche,
la sienne étant annoncée sans exister. L'application ne savait qu'en dire qu'elle
ne pouvait pas le lire, laissant au projet le soin de composer à la main une
arborescence dont il ne connaît pas encore les conventions.

C'est le premier contact avec l'outil, et c'était le moment où il en demandait le
plus. Un projet qui doit lire la documentation du format avant d'avoir vu son
premier écran ne commencera pas.

## Parcours utilisateur

1. Quelqu'un ouvre un dépôt qu'il vient de créer, encore vide.
2. L'application le lui dit, et propose d'y déposer la structure d'un
   référentiel.
3. Il donne le nom du projet — proposé depuis celui du dépôt — et ce qu'il fait
   en une phrase.
4. L'application dépose la configuration, un fichier d'accueil, et les
   répertoires attendus, chacun expliquant ce qu'on y dépose.
5. Le référentiel se charge, vide de contenu mais prêt à en recevoir.

## Énoncés

### RG-amorcage-depot

L'application **dépose la structure d'un référentiel** dans un dépôt qui n'en a
pas encore.

Signaler qu'un dépôt est vide ne suffit pas : le projet devrait alors composer à
la main une arborescence dont il ne connaît pas les conventions, au moment précis
où il découvre l'outil.

L'amorçage écrit directement, sans passer par une demande de fusion. C'est la
seule écriture dans ce cas : il n'y a rien à relire dans un dépôt vide, et une
branche ne peut de toute façon pas diverger de ce qui n'existe pas encore.

Chaque répertoire reçoit une note expliquant ce qu'on y dépose. Un répertoire
vide n'étant pas conservé par le support, il lui faut de toute façon un fichier :
autant qu'il serve à celui qui ouvre le dépôt sur la plateforme.

### RG-documentation-non-entite

Un fichier d'accueil placé dans un répertoire de contenu est de la
**documentation, non une entité** : ni la lecture ni la vérification ne le
traitent comme telle.

Sans cela, la documentation qu'on y dépose est signalée comme mal formée — et la
vérification échouant bloque la livraison, un dépôt amorcé de la sorte ne pouvant
plus rien livrer du tout.

La règle vaut pour les deux côtés qui lisent le format. Ce qui explique un
répertoire à celui qui l'ouvre ne doit pas être confondu avec ce que le
répertoire contient.

### RG-chargement-hors-quota

Le chargement d'un dépôt consomme **une seule requête décomptée**, quel que soit
le nombre de fichiers.

L'arborescence est obtenue par un appel unique ; les contenus sont ensuite
récupérés par un canal non décompté.

Cette contrainte n'est pas une optimisation mais une condition de
fonctionnement : sans connexion, la limite est de soixante appels par heure,
alors qu'un référentiel modeste compte déjà plusieurs dizaines de fichiers.

**Le canal des contenus bascule sur celui de l'arborescence** lorsque le premier
ne dessert pas le dépôt, au prix d'un appel par fichier. C'est le cas des dépôts
privés : le canal non décompté leur répond comme à un dépôt absent, même à qui y
a droit. La bascule est automatique — attendre un réglage manuel reviendrait à
présenter un dépôt privé comme introuvable à celui qui vient d'y écrire.

Elle se demande aussi de son propre chef, pour afficher immédiatement ce qui
vient d'être livré, le canal ordinaire servant ses réponses avec un délai.
