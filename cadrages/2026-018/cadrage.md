---
id: 2026-018
titre: Une gamme de modes d'accès
statut: livree
domaines: [acces, cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-modes-acces, operation: cree }
  - { regle: RG-garanties-annoncees, operation: cree }
  - { regle: RG-connexion-optionnelle, operation: touche }
  - { regle: RG-autorisation-point-unique, operation: touche }
  - { regle: RG-auteur-reel-commit, operation: touche }
  - { regle: RG-reglages-projet, operation: touche }
---

## Objectif

Ouvrir l'outil au client sans imposer une infrastructure à tous les projets.

Un cadrage se rédige à quatre mains, et le client en est la moitié. Or l'accès
actuel suppose qu'il ait un compte sur la plateforme de dépôt et sache s'y créer
un jeton — ce qu'il ne fera pas pour relire une spécification. Cet obstacle est la
raison d'être de la question d'identité.

La réponse évidente — un composant intermédiaire détenant les droits — a un coût
que tous les projets n'ont pas à payer. Une équipe qui travaille seule sur son
propre dépôt n'a besoin de rien de plus que ce qui existe.

Il n'y a donc pas un montage à choisir mais **une gamme à offrir**, dont chaque
degré lève un obstacle de plus, au prix d'un peu plus d'infrastructure. Le projet
choisit le sien, comme il choisit ses transitions de statut.

## Parcours utilisateur

1. Un projet déclare dans sa configuration le mode d'accès qu'il emploie.
2. **Sans rien déclarer**, chacun apporte son propre jeton : rien à héberger, mais
   il faut un compte sur la plateforme de dépôt.
3. **En déclarant une identité tierce**, l'utilisateur se connecte avec un compte
   qui n'a rien à voir avec la plateforme de dépôt ; un composant échange cette
   identité contre un accès temporaire au dépôt.
4. **En déclarant un relais**, chaque requête passe par lui : il vérifie non
   seulement qui écrit, mais où.
5. L'application annonce, dans chaque mode, ce qu'il garantit et ce qu'il ne
   garantit pas.

## Énoncés

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
  temporaire. Le client n'a plus rien à créer ni à comprendre.
- **Relais** — chaque requête passe par un composant qui la vérifie avant de la
  transmettre.

Passer d'un mode au suivant ne demande de reprendre ni le référentiel ni les
cadrages : ce qui change est la façon d'obtenir l'accès, non ce qu'on en fait.

### RG-garanties-annoncees

Chaque mode d'accès **annonce ce qu'il garantit, et ce qu'il ne garantit pas**.

Un mode qui laisserait croire à une protection qu'il n'offre pas serait pire que
son absence : celui qui s'y fie cesse de se méfier là où il devrait.

Deux garanties distinguent les modes, et la distinction est imposée par la
plateforme, non choisie :

- **Jusqu'où descend l'autorisation.** Un accès temporaire se restreint aux
  dépôts et aux permissions, jamais aux chemins : dans les deux premiers modes,
  un rédacteur autorisé sur un projet peut écrire partout dans ce projet. Seul le
  relais peut refuser un chemin.
- **D'où vient l'auteur d'un enregistrement.** Dans les deux premiers modes, il
  est déclaré par l'application, donc falsifiable par qui la contourne. Seul le
  relais le tient de l'identité vérifiée.

L'application dit lequel s'applique. Un projet qui a besoin de la garantie forte
sait qu'il lui faut le relais ; un projet qui n'en a pas besoin sait qu'il peut
s'en passer.
