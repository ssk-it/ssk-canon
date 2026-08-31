---
id: RG-cycle-parametre
fonctionnalites: [cycle-vie-cadrage, redaction-cadrage]
statut: actif
cree_par: 2026-017
modifie_par: []
---

L'application ne propose que les **transitions de statut que le projet
autorise**, et n'en invente aucune.

Le statut **livrée** n'est jamais proposé, et aucun réglage ne peut l'ajouter :
il résulte de la fusion de la demande, non d'une saisie. L'affirmer autrement
annoncerait une livraison qui n'a pas eu lieu, et un référentiel qui ment sur ce
qui est livré ne sert plus à rien.

Un cadrage qui ne vit pas sur sa propre branche ne bouge pas non plus : son
statut décrit alors ce qui est déjà dans le référentiel, et le changer sans
passer par une demande de fusion contournerait la vérification.

Aucune transition n'est possible sur un cadrage incohérent. Avancer un cadrage
que la vérification refuserait ne ferait que rapprocher le problème de la
livraison, là où il coûte le plus cher à corriger.
