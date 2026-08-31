---
id: RG-reglages-projet
fonctionnalites: [autorisation, stockage-git]
statut: actif
cree_par: 2026-017
modifie_par: []
---

Ce que l'application s'autorise sur un projet est **réglé dans le projet**, non
dans l'outil ni dans le navigateur.

Ces réglages valent pour tous ceux qui y travaillent : les loger dans le
navigateur les ferait varier d'un poste à l'autre, ce qui ne règle rien. Ils
suivent le dépôt, se relisent avec lui, et survivent au changement d'outil comme
au changement d'équipe.

Ils se modifient depuis l'application, et cette modification est **soumise à
relecture** comme toute autre : ce qui décide du comportement de l'outil pour
tout le monde ne prend pas effet parce qu'une personne a coché une case.

Un projet qui ne règle rien fonctionne : des valeurs par défaut s'appliquent. Un
réglage illisible est signalé sans empêcher la consultation — un référentiel se
lit même quand sa configuration est fautive.
