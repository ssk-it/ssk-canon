---
id: RG-cadrages-en-cours-visibles
fonctionnalites: [cycle-vie-cadrage, consultation-cadrage]
statut: actif
cree_par: 2026-025
modifie_par: [2026-032]
---

Les cadrages **non livrés sont visibles**, avec ceux du référentiel.

Ils vivent sur la branche de leur demande de fusion, jamais sur la branche
principale : ne lire que celle-ci revient à ne montrer que les cadrages terminés,
c'est-à-dire pas ceux sur lesquels on travaille.

**Ils se trouvent par les demandes de fusion ouvertes et par les branches.** Une
demande de fusion est un fait, et reste la voie principale ; mais un cadrage
commencé n'en a pas encore, et c'est précisément le brouillon. Ne lire que les
demandes de fusion rendrait invisible tout cadrage avant sa première relecture.

Le nom de la branche n'est toujours pas un critère de rattachement : c'est le
cadrage trouvé sur la branche qui la rattache, non l'inverse. Les deux formes
`cadrage-<id>` et `cadrage/<id>` sont acceptées à la lecture, la seconde étant
celle que l'application propose désormais à la création.

**Chacun porte la marque de sa demande de fusion**, faute de quoi il passerait
pour appartenir déjà au référentiel.

Une branche illisible n'emporte ni les autres ni le référentiel, qui reste
consultable.
