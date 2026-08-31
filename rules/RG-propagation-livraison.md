---
id: RG-propagation-livraison
fonctionnalites: [impacts-regles]
statut: actif
cree_par: 2026-001
modifie_par: [2026-002]
---

À la livraison d'un cadrage, ses impacts sont appliqués au référentiel
**automatiquement**, dans un commit distinct de celui du merge.

La séparation est délibérée : le merge porte l'intention rédigée par un humain, le
commit suivant porte l'écriture faite par la machine. Les distinguer rend
l'historique lisible et permet de rejouer une propagation sans toucher au cadrage.
