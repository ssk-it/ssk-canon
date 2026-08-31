---
id: 2026-017
titre: Ce que l'application s'autorise sur un projet
statut: livree
domaines: [cadrage, acces, persistance]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-reglages-projet, operation: cree }
  - { regle: RG-cycle-parametre, operation: cree }
  - { regle: RG-reflet-demande-fusion, operation: cree }
  - { regle: RG-statuts-cadrage, operation: modifie }
  - { regle: RG-reprise-cadrage, operation: touche }
  - { regle: RG-branche-par-cadrage, operation: touche }
  - { regle: RG-histoire-derivee, operation: touche }
---

## Objectif

Faire avancer un cadrage dans son cycle depuis l'application, sans décider à la
place du projet de ce qu'il s'autorise.

Le statut était jusqu'ici hors de portée : ouvrir un cadrage et le reprendre
étaient possibles, mais le faire passer en relecture demandait d'éditer le
fichier à la main. La raison de ce report tenait : passer un cadrage à l'état
livré déclenche des contrôles qu'un brouillon ne subit pas, et ce n'est donc pas
une saisie ordinaire.

La réponse n'était pas de fixer le cycle dans le produit. Les projets ne
travaillent pas tous pareil — certains veulent qu'un cadrage puisse revenir en
arrière, d'autres non ; certains vivent sur la plateforme, d'autres seulement
dans l'application. Ce que l'outil s'autorise doit se régler par projet, dans le
projet.

## Parcours utilisateur

1. Le rédacteur ouvre un cadrage et le reprend.
2. L'application lui montre son statut et les transitions que le projet autorise.
3. Il fait avancer le cadrage, à condition qu'il soit cohérent — un statut avancé
   sur un cadrage que la vérification refuserait ne ferait que déplacer le
   problème plus près de la livraison.
4. Si le projet l'a demandé, la demande de fusion suit : ouverte en brouillon
   tant que le cadrage l'est, prête à relire dès qu'il passe en relecture.
5. Les réglages eux-mêmes se modifient depuis l'application, et la modification
   est soumise à relecture comme toute autre.

## Énoncés

### RG-reglages-projet

Ce que l'application s'autorise sur un projet est **réglé dans le projet**, non
dans l'outil ni dans le navigateur.

Ces réglages valent pour tous ceux qui y travaillent : les loger dans le
navigateur les ferait varier d'un poste à l'autre, ce qui ne règle rien. Ils
suivent le dépôt, se relisent avec lui, et survivent au changement d'outil comme
au changement d'équipe.

Ils se modifient depuis l'application, et cette modification est **soumise à
relecture** comme toute autre : ce qui décide du comportement de l'outil pour
tout le monde ne prend pas effet parce qu'une personne a coché une case.

Un projet qui ne règle rien fonctionne : des valeurs par défaut s'appliquent. Un
réglage illisible est signalé sans empêcher la consultation — un référentiel se
lit même quand sa configuration est fautive.

### RG-cycle-parametre

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

### RG-reflet-demande-fusion

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

### RG-statuts-cadrage

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
