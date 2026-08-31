---
id: RG-emetteur-declare
fonctionnalites: [authentification, autorisation]
statut: actif
cree_par: 2026-019
modifie_par: []
---

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
