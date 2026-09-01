---
id: RG-cadrage-livre-immuable
fonctionnalites: [cycle-vie-cadrage, impacts-regles]
statut: actif
cree_par: 2026-032
modifie_par: []
---

Un cadrage livré **ne se modifie plus** — ni son énoncé, ni ses impacts, ni ses
décisions.

Le référentiel est la projection des cadrages livrés. Modifier un cadrage livré
change rétroactivement ce que le référentiel est censé contenir, sans que rien
ne le repropage : le référentiel et ses cadrages cessent alors de coïncider,
silencieusement.

L'interdiction couvre aussi les **décisions**, y compris leur ajout. Une décision
ajoutée après la livraison n'a été relue par personne, alors que la validation
portait sur ce qui était présent au moment où elle a été donnée. Admettre ces
ajouts viderait la validation de son sens.

Ce qui a été livré et qu'on veut changer se change par **un nouveau cadrage**.
C'est ce que le référentiel sait faire, et l'histoire reste lisible.

La vérification refuse donc toute modification sous le répertoire d'un cadrage
déjà présent sur la branche principale. Elle a besoin pour cela de comparer la
demande de fusion à cette branche, et non de lire un seul état.
