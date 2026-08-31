---
id: 2026-019
titre: Se connecter sans compte sur la plateforme
statut: livree
domaines: [acces, cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-acces-temporaire, operation: cree }
  - { regle: RG-emetteur-declare, operation: cree }
  - { regle: RG-modes-acces, operation: modifie }
  - { regle: RG-auteur-reel-commit, operation: touche }
  - { regle: RG-garanties-annoncees, operation: touche }
  - { regle: RG-reglages-projet, operation: touche }
---

## Objectif

Lever l'obstacle qui motivait toute la question de l'identité : un cadrage se
rédige à quatre mains, et le client en est la moitié — mais il devait jusqu'ici
disposer d'un compte sur la plateforme de dépôt et savoir s'y créer un jeton.

Il ne le fera pas pour relire une spécification. La gamme des modes d'accès
prévoyait ce mode ; il restait à le construire.

Le principe : le rédacteur se fait vérifier auprès de l'émetteur d'identité que
son projet déclare, et un composant échange cette identité vérifiée contre un
accès temporaire au dépôt. Ce composant existe parce qu'une application qui
s'exécute dans un navigateur n'a nulle part où cacher de quoi obtenir cet accès.

## Parcours utilisateur

1. Le rédacteur ouvre l'application. Le projet déclare qu'il fait vérifier les
   identités auprès de son propre fournisseur.
2. Il se connecte auprès de ce fournisseur, avec un compte qui n'a rien à voir
   avec la plateforme de dépôt.
3. L'application obtient un accès temporaire aux projets que son identité ouvre,
   et le lui annonce.
4. Il rédige. Ce qu'il enregistre porte son nom, non celui de l'application.
5. L'accès expire au bout d'une heure. Se reconnecter en rend un nouveau.

## Énoncés

### RG-acces-temporaire

L'accès obtenu contre une identité vérifiée est **temporaire**, et l'application
ne le conserve pas au-delà de la session.

Sa durée est fixée par la plateforme et ne se raccourcit pas. Le garder d'une
session à l'autre le ferait retrouver expiré, et le présenter alors produirait un
refus dont la cause serait invisible au rédacteur — le perdre en rechargeant est
le comportement juste, une nouvelle identité vérifiée en rendant aussitôt un
autre.

Un accès expiré n'est jamais présenté : l'application l'oublie plutôt que de le
laisser échouer.

L'accès prime sur un jeton personnel qui existerait par ailleurs : quelqu'un qui
vient de s'identifier attend d'écrire sous cette identité, non sous un jeton
saisi la veille.

### RG-emetteur-declare

Le projet déclare **où les identités sont vérifiées** : l'émetteur, l'identifiant
sous lequel l'application s'y présente, et le composant qui échange une identité
contre un accès.

Rien de tout cela n'est secret. Ce sont les valeurs que porte toute application
s'exécutant dans un navigateur, et les déclarer dans le projet permet à chaque
projet d'avoir le sien — un client, son fournisseur d'identité.

Les projets qu'une identité peut atteindre sont portés par l'identité elle-même,
non par une table tenue ailleurs. Les droits se gèrent alors là où se gèrent les
comptes, et changer ce qu'un rédacteur atteint ne demande de redéployer aucun
composant.

Un mode déclaré sans ses paramètres est signalé plutôt que subi : l'application
ne le propose pas à l'enregistrement, et le dit. Les découvrir manquants à la
première connexion coûterait davantage.

### RG-modes-acces

Un projet **déclare son mode d'accès** dans sa configuration, et l'application
s'y conforme.

Trois modes, qui ne se substituent pas mais s'empilent : chacun lève un obstacle
que le précédent laissait, sans annuler ce qu'il apportait.

- **Jeton personnel** — chacun apporte le sien. Rien à héberger, et c'est le mode
  par défaut : un projet qui ne déclare rien fonctionne. Il suppose que chaque
  rédacteur ait un compte sur la plateforme de dépôt.
- **Identité tierce** — le rédacteur se connecte avec un compte indépendant de la
  plateforme de dépôt, et un composant échange cette identité contre un accès
  temporaire. Le client n'a plus rien à créer ni à comprendre. Ce composant n'est
  pas sur le chemin des données : il est appelé à la connexion, puis l'application
  s'adresse directement à la plateforme.
- **Relais** — chaque requête passe par un composant qui la vérifie avant de la
  transmettre.

Passer d'un mode au suivant ne demande de reprendre ni le référentiel ni les
cadrages : ce qui change est la façon d'obtenir l'accès, non ce qu'on en fait.
