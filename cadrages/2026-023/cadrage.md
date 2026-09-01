---
id: 2026-023
titre: Maintenir l'outillage sans le laisser diverger
statut: livree
domaines: [cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-maintien-outillage, operation: cree }
  - { regle: RG-outillage-redaction, operation: modifie }
  - { regle: RG-automatisation-versionnee, operation: touche }
  - { regle: RG-verification-integrite, operation: touche }
---

## Objectif

Publier l'outillage de rédaction ne suffit pas : il faut pouvoir le corriger.

Une fois distribué, il n'existe plus à un seul endroit. Il y a la source, la
copie que chacun a installée, et ce que la publication sert. Corriger la copie
installée est le geste naturel — c'est celle qui s'exécute, celle dont on voit
le défaut — et c'est le mauvais : le changement fonctionne chez soi, disparaît à
la réinstallation suivante, et n'atteint personne.

Rien ne signale cette divergence. Elle se découvre en constatant qu'une
correction faite il y a un mois n'a jamais existé pour les autres.

## Parcours utilisateur

1. Quelqu'un trouve un défaut dans l'outillage de rédaction.
2. Avant de modifier quoi que ce soit, il compare les exemplaires : s'ils
   divergent déjà, c'est qu'une modification a été faite au mauvais endroit, et
   l'écraser perdrait ce que quelqu'un avait voulu.
3. Il corrige la source, l'éprouve dans les conditions de celui qui l'exécute,
   et publie.
4. Une fois la publication faite, il compare de nouveau et se réinstalle.
5. Ceux qui l'avaient installé ne sont pas prévenus : rien ne les met à jour, et
   il faut le leur dire.

## Énoncés

### RG-maintien-outillage

L'outillage distribué porte **de quoi être mis à jour sans diverger**.

Une fois distribué, il existe en plusieurs exemplaires : la source, la copie
installée, la version publiée. Corriger la copie installée est le geste naturel
et le mauvais — le changement disparaît à la réinstallation suivante, sans
jamais atteindre personne d'autre.

**La comparaison des exemplaires précède toute modification.** Une divergence
constatée avant d'écrire est un renseignement ; découverte après, c'est du
travail perdu. L'outil de comparaison nomme lequel a bougé, sans trancher à la
place de celui qui lit.

**Ce que rien ne vérifie doit être dit.** L'outillage n'est contrôlé par aucune
intégration continue : la procédure qui le décrit est la seule vérification qui
existe, et elle doit donc énoncer comment l'éprouver — dans les conditions de
celui qui l'exécute, jamais sur une approximation.

Une mise à jour ne se propage pas d'elle-même. Ceux qui ont installé l'outillage
ne sont ni prévenus ni mis à jour : un changement qui modifie leur façon de
travailler se dit.

### RG-outillage-redaction

L'outillage de rédaction est **distribué avec le format, non avec
l'application.**

Il décrit ce qu'est un cadrage — les champs, les pièges, le moment où une règle
doit exister. C'est la même chose que vérifie l'automatisation : les publier
séparément ferait deux descriptions du format, qui divergeraient dès la première
correction.

Il ne se recopie pas dans les projets qui l'emploient. Une copie par projet est
une divergence par projet, et l'outillage cesse alors de décrire le format pour
ne plus décrire que l'état où on l'a laissé.

**L'application indique comment l'installer et le configurer**, en reprenant ce
que le projet ouvert déclare déjà plutôt qu'un exemple générique. Un exemple
qu'on recopie par-dessus sa propre déclaration l'efface.

Ce qui décrit la machine du rédacteur — où les référentiels sont clonés — vit
chez lui, et ne se commite nulle part. Ce qui décrit le projet vit dans le
référentiel.

**Ce qui sert à le maintenir est distribué avec lui.** Un outil de maintenance
gardé à part de ce qu'il maintient est le premier à diverger, n'étant employé
qu'au moment où l'on constate déjà un problème.
