---
id: RG-garanties-annoncees
fonctionnalites: [authentification, autorisation]
statut: actif
cree_par: 2026-018
modifie_par: []
---

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
