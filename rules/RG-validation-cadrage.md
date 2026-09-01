---
id: RG-validation-cadrage
fonctionnalites: [cycle-vie-cadrage, autorisation]
statut: actif
cree_par: 2026-032
modifie_par: []
---

Une validation constate qu'**une personne a relu le cadrage et l'approuve**. Elle
porte toujours un **message obligatoire** : la validation sans motif n'apprend
rien à qui la lira ensuite.

Elle prend la forme d'une **approbation de la demande de fusion** partout où la
plateforme le permet — le mécanisme est natif, daté, attribué, et se périme de
lui-même quand la branche reçoit de nouveaux commits, ce qui est le comportement
attendu : un cadrage modifié après validation redevient à relire.

La plateforme refuse cependant qu'on approuve sa propre demande de fusion. Là où
l'application agit sous une identité tierce, elle porte l'approbation et nomme le
valideur dans le message. Là où elle agit sous le compte du rédacteur — et que
celui-ci est l'auteur de la demande — l'approbation est impossible, et la
validation prend alors la forme d'un **commentaire structuré** portant le
valideur, la date, le motif, et le commit sur lequel elle porte.

**Une validation ne se modifie pas : elle s'annule par un nouvel événement.** Un
commentaire édité perdrait la date où la validation valait, et rien
n'empêcherait de la réécrire. L'état courant est celui du dernier événement en
date, validation ou annulation, quelle que soit sa forme.

Une validation portée par commentaire est **périmée si la branche a avancé**
depuis le commit qu'elle nomme. C'est ce que l'approbation native fait
d'elle-même, et une validation qui survivrait à la modification de son objet ne
voudrait plus rien dire.

L'application **annonce laquelle des deux formes elle emploie** : une approbation
est vérifiée par la plateforme, un commentaire déclare une identité que rien ne
vérifie. Conformément à RG-garanties-annoncees, taire la différence ferait se
fier à une garantie absente.
