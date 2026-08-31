---
id: RG-reflet-demande-fusion
fonctionnalites: [cycle-vie-cadrage, stockage-git]
statut: actif
cree_par: 2026-017
modifie_par: []
---

Lorsque le projet le demande, la **demande de fusion suit le statut du
cadrage** : ouverte en brouillon tant qu'il l'est, prête à relire dès qu'il
passe en relecture.

C'est un confort, non une source de vérité : le statut vit dans le fichier, et
la demande n'en est que le reflet. L'ordre des écritures le dit — le statut
d'abord, le reflet ensuite. Un reflet qui échoue laisse un statut juste et une
demande en retard, ce qui se rattrape ; l'ordre inverse laisserait une demande
annonçant un statut que le cadrage n'a pas.

Le reflet manqué est signalé plutôt que passé sous silence. Une désynchronisation
qu'on ignore vaut moins qu'une désynchronisation qu'on sait devoir corriger.

Le réglage existe parce que tous les projets ne travaillent pas de la même
façon : celui dont le client ne regarde que l'application n'a rien à refléter.
