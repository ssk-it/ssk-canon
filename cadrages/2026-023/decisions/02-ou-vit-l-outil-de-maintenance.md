---
id: 02-ou-vit-l-outil-de-maintenance
titre: Où vit ce qui sert à maintenir l'outillage ?
statut: retenue
option_retenue: avec-ce-qu-il-maintient
---

## Description

Un cadrage précédent a établi que l'outillage de rédaction est publié avec le
format qu'il décrit. La même question se repose d'un cran au-dessus : ce qui
sert à corriger cet outillage, où vit-il ?

## Options

### dans-la-documentation-du-depot

Un paragraphe du fichier d'accueil expliquant la marche à suivre.

**Pour** — rien de plus à distribuer, et c'est là qu'on cherche par réflexe.
**Contre** — une documentation ne s'exécute pas. Elle peut décrire la
comparaison des exemplaires ; elle ne peut pas la faire, alors que c'est
justement l'étape qu'on saute.

### chez-celui-qui-maintient

Chacun se donne ses propres moyens de vérifier.

**Pour** — aucune contrainte imposée.
**Contre** — c'est l'état d'où l'on part quand personne n'a rien : la
comparaison n'est pas faite, faute d'exister. Et ce qui vit chez un seul
disparaît avec lui.

### avec-ce-qu-il-maintient

**Retenue.** L'outil de maintenance est distribué avec l'outillage qu'il
maintient, dans le même dépôt.

**Pour** — il est là quand on en a besoin, versionné avec ce qu'il connaît. Il
sait où sont les trois exemplaires parce qu'il vit auprès de l'un d'eux.
**Contre** — un objet de plus à maintenir, qui pose à son tour la question qu'il
résout.

## Décision

**Distribuer l'outil de maintenance avec ce qu'il maintient.**

Le critère : **un outil de maintenance gardé à part de ce qu'il maintient est le
premier à diverger.** Il n'est employé qu'au moment où l'on constate déjà un
problème, donc rarement, donc son décalage passe inaperçu le plus longtemps.

C'est la même raison qui avait fait publier l'outillage avec le vérificateur, et
le vérificateur séparément de l'application : le découpage suit ce qui doit
changer ensemble.

**Le défaut qui a le plus appris** est venu de l'épreuve, non du raisonnement.
La première version de l'outil de maintenance échouait au chargement à cause de
la ligne même qui mettait en garde contre une construction dangereuse : la
plateforme ne distingue pas une citation de la chose citée. Une mise en garde
peut donc produire le défaut qu'elle décrit, et seule l'exécution le montre.
