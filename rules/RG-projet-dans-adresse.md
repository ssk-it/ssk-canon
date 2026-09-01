---
id: RG-projet-dans-adresse
fonctionnalites: [stockage-git, consultation-cadrage]
statut: actif
cree_par: 2026-029
modifie_par: []
---

**Toute vue d'un projet est adressée par `/<organisation>/<depot>/<vue>`.**
L'adresse fait autorité sur le projet ouvert ; la mémoire du navigateur ne sert
qu'à proposer, jamais à décider.

C'est ce qui rend un lien partageable : celui qui le reçoit voit le même projet
que celui qui l'a envoyé. Un état gardé dans le navigateur ne voyage pas, et une
adresse qui dépend de lui affiche chez l'un autre chose que chez l'autre — sans
que ni l'un ni l'autre ne puisse s'en apercevoir.

Il s'ensuit que **tout lien interne porte le projet ouvert**. Un lien écrit sans
lui sortirait du projet courant sans le signaler.

Changer de projet **conserve la vue** : passer d'un projet à l'autre en
consultant les cadrages mène aux cadrages de l'autre projet. Une vue de détail
retombe en revanche sur sa liste, un identifiant de cadrage ou de règle n'ayant
aucune raison d'exister ailleurs — mener à une page vide serait pire que ne rien
promettre.

Une adresse qui ne désigne aucun projet ramène au choix. Elle ne peut pas en
deviner un, et en ouvrir un au hasard ferait passer pour consulté un projet que
personne n'a demandé.
