---
id: RG-verification-integrite
fonctionnalites: [impacts-regles, modele-referentiel]
statut: actif
cree_par: 2026-002
modifie_par: [2026-011, 2026-032]
---

Une vérification d'intégrité s'exécute à l'ouverture et à chaque modification
d'une pull request. Une erreur **empêche le merge**.

Elle contrôle ce que le format seul ne peut pas garantir : un impact référençant
une règle inexistante, un identifiant dupliqué, un énoncé manquant pour un impact
`cree` ou `modifie`, une règle abrogée par un cadrage non livré, un rattachement
vers une entité inconnue, une règle rattachée à aucune fonctionnalité, et **la
modification d'un cadrage déjà livré**.

Ce dernier contrôle porte sur un écart, non sur un état : il compare la demande
de fusion à la branche principale. La vérification a donc besoin de l'historique,
là où les autres contrôles se contentent du dernier état.

Une règle créée par un cadrage encore en relecture n'existe pas dans le
référentiel : c'est normal, et la vérification ne l'exige qu'à la livraison.

La distinction entre ce qui bloque et ce qui informe est un choix, pas un défaut
de rigueur : bloque ce qui rendrait le référentiel faux ou inatteignable, informe
ce qui relève de l'incomplétude passagère d'un travail en cours.

Un contrôle ne bloque que s'il est déclaré requis dans les règles de protection
de la branche principale. Sans cette déclaration, il signale sans empêcher, et
l'intégrité n'est plus garantie que par la bonne volonté.
