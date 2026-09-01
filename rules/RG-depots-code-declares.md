---
id: RG-depots-code-declares
fonctionnalites: [modele-referentiel, stockage-git]
statut: actif
cree_par: 2026-022
modifie_par: []
---

Un référentiel **déclare les dépôts de code que le projet réalise.**

La vue « projet » appartient au référentiel : plusieurs dépôts de code la
composent — une application, une interface de programmation, un client mobile —
et aucun d'eux ne connaît les autres.

**Le lien est déclaré une seule fois, du côté qui a autorité.** Le déclarer dans
chaque dépôt de code écrirait *n* fois ce qui est un fait unique, sans rien qui
garantisse que les copies restent d'accord.

Rien n'est donc à configurer dans un dépôt de code : la plateforme le nomme
déjà, et ce nom suffit à retrouver le projet qui le déclare.

Une déclaration mal formée est écartée et signalée, sans rendre le référentiel
illisible : elle sert à se situer, et une entrée douteuse ne doit pas empêcher
de consulter.
