---
id: RG-statuts-cadrage
fonctionnalites: [cycle-vie-cadrage]
statut: actif
cree_par: 2026-001
modifie_par: [2026-002, 2026-014, 2026-017]
---

Un cadrage passe par quatre statuts : **brouillon**, **en relecture**,
**validée**, **livrée**.

Le statut est **porté par le cadrage lui-même**, dans son fichier. C'est la
source unique : la vérification d'intégrité et la propagation le lisent là, et un
référentiel reste ainsi entièrement lisible sans interroger aucune demande de
fusion — y compris dans une copie locale, ou une fois le dépôt archivé.

L'application fait avancer un cadrage d'un statut à l'autre, selon ce que le
projet autorise. Elle ne le déclare jamais livré : c'est la fusion de sa demande
qui l'établit, et la propagation qui s'ensuit.

Chaque statut a son reflet dans le cycle d'une demande de fusion : branche créée,
demande ouverte, demande approuvée, demande fusionnée. Le projet peut demander
que ce reflet soit tenu ; il n'en devient pas pour autant une seconde source de
vérité, et c'est celle qui vit dans le dépôt qui fait foi.

L'historique des transitions, lui, n'est pas stocké : il se dérive des
événements de la demande de fusion, chacun daté et attribué.
