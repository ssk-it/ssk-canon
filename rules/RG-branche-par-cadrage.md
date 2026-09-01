---
id: RG-branche-par-cadrage
fonctionnalites: [cycle-vie-cadrage, stockage-git]
statut: actif
cree_par: 2026-001
modifie_par: [2026-025]
---

Chaque cadrage est rédigé sur sa **propre branche**, et livré par le merge de sa
demande de fusion.

Deux cadrages simultanés n'entrent donc jamais en conflit. Deux personnes
éditant le même cadrage produisent en revanche un conflit Git, que l'application
doit présenter intelligemment.

**Le nom de la branche n'emporte aucune conséquence.** L'application en propose
un lorsqu'elle crée la branche, mais ne s'y fie jamais pour retrouver un
cadrage : c'est la demande de fusion qui l'y rattache.

Faire dépendre quoi que ce soit du nom d'une branche rend l'outil aveugle à tout
cadrage rédigé autrement — et le nommage est le premier endroit où deux
conventions divergent, l'une portée par l'application, l'autre par ce qu'on
enseigne au rédacteur. C'est arrivé, et le cadrage écrit à la main était absent
de la liste tout en étant parfaitement formé.
