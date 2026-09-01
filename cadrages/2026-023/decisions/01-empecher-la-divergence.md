---
id: 01-empecher-la-divergence
titre: Comment empêcher les exemplaires de l'outillage de diverger ?
statut: retenue
option_retenue: comparer-avant-de-modifier
---

## Description

L'outillage distribué existe en trois exemplaires : la source, la copie
installée chez chacun, et la version publiée. Le geste naturel — corriger la
copie qu'on voit fonctionner — est celui qui perd le travail.

Rien ne signale la divergence quand elle s'installe. On la découvre en
constatant qu'une correction ancienne n'a jamais existé pour les autres.

## Options

### interdire-de-modifier-la-copie-installee

Rendre la copie installée non modifiable, ou l'écraser à chaque démarrage.

**Pour** — la divergence devient impossible.
**Contre** — supprime aussi l'essai local, qui est la façon normale de mettre au
point une correction avant de la publier. On corrigerait à l'aveugle, ce qui
produit de moins bonnes corrections, pas moins de divergences.

### une-verification-automatique

Faire échouer l'intégration continue quand les exemplaires diffèrent.

**Pour** — le contrôle ne dépend de la vigilance de personne.
**Contre** — l'intégration continue ne voit ni la copie installée ni celle des
autres. Elle ne pourrait comparer que la source à elle-même. La divergence qui
compte est précisément celle qu'elle ne peut pas voir.

### comparer-avant-de-modifier

**Retenue.** Un outil qui montre les trois exemplaires et dit lequel a bougé,
employé avant toute modification.

**Pour** — traite la divergence quand elle est encore un renseignement, et non
une fois qu'elle a coûté du travail. Ne décide rien à la place de celui qui lit :
une copie modifiée sur place porte peut-être quelque chose qui vaut d'être
récupéré.
**Contre** — dépend de la vigilance : rien n'oblige à l'employer.

## Décision

**Comparer avant de modifier, et laisser lire.**

Le critère qui tranche : **la divergence qui compte est celle qu'aucune machine
ne peut voir.** L'intégration continue ne connaît ni la copie installée chez
l'un, ni celle de l'autre. Ce qui n'est pas vérifiable automatiquement doit être
dit, à l'endroit et au moment où quelqu'un s'apprête à agir.

L'outil ne tranche pas de lui-même. Écraser une copie divergente serait le
comportement évident et le mauvais : elle porte peut-être une correction que
personne n'a encore publiée, et c'est justement le cas qu'on cherche à
rattraper.

Ce qui reste assumé : rien n'oblige à l'employer, et rien ne prévient ceux qui
ont installé l'outillage qu'une version nouvelle existe. Le cadrage le consigne
plutôt que de laisser croire que la procédure suffit.
