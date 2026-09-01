---
id: RG-modes-acces
fonctionnalites: [authentification, autorisation]
statut: actif
cree_par: 2026-018
modifie_par: [2026-019, 2026-024]
---

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

Le mode est déclaré par projet, et un rédacteur travaille sur plusieurs projets :
**l'accès du mode « jeton personnel » se choisit donc selon le projet ouvert**,
et non globalement. Voir `RG-acces-par-portee`.
