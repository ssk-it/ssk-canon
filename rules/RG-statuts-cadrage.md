---
id: RG-statuts-cadrage
fonctionnalites: [cycle-vie-cadrage]
statut: actif
cree_par: 2026-001
modifie_par: [2026-002, 2026-014, 2026-017, 2026-032]
---

Un cadrage passe par quatre statuts : **brouillon**, **en relecture**,
**validée**, **livrée**.

Le statut n'est **pas porté par le cadrage** : il se déduit de l'état du dépôt.

| Statut | Ce qui l'établit |
|---|---|
| brouillon | une branche porte le cadrage, sans demande de fusion ouverte |
| en relecture | une demande de fusion est ouverte, qu'elle soit en brouillon ou non |
| validée | cette demande porte une validation en cours de validité |
| livrée | le cadrage est présent sur la branche principale |

**La branche principale l'emporte sur toute autre lecture.** Un cadrage qu'elle
porte est livré, quoi qu'indiquent les branches ou les demandes de fusion qui le
mentionnent encore. Les trois autres statuts ne se lisent que pour un cadrage
qu'elle ne porte pas.

Un champ de statut dans le fichier serait une seconde source pour un fait que le
dépôt établit déjà. Deux sources divergent : un cadrage a été fusionné en portant
`brouillon`, et ses impacts n'ont pas été propagés faute que quiconque ait
corrigé le champ. Le dépôt, lui, ne se trompe pas sur ce qu'il contient.

L'état d'avancement d'une demande de fusion — brouillon ou prête à relire —
n'entre pas dans le statut. C'est une commodité d'affichage sur la plateforme,
que le rédacteur règle comme il l'entend, et non un moment du cycle de vie.

La propagation retient donc les cadrages présents sur la branche principale, sans
plus rien avoir à interroger. Elle reste idempotente et tout ou rien.

Deux réglages de projet perdent par là même leur objet : la liste des
**transitions** autorisées, puisqu'un statut déduit ne se choisit plus, et le
**reflet de la demande de fusion**, puisque le statut ne commande plus son état
d'avancement. Un projet qui les déclare encore les voit ignorés, sans erreur :
ce sont des réglages devenus sans effet, non des réglages invalides.
