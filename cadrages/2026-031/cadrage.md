---
id: 2026-031
titre: Ce qu'un cadrage a tranché, lisible sans le parcourir
statut: brouillon
domaines: [cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon-pwa/pull/5' }
impacts:
  - { regle: RG-recapitulatif-tranchees, operation: cree }
  - { regle: RG-justification-derivee, operation: cree }
  - { regle: RG-sommaire-place-disponible, operation: touche }
  - { regle: RG-decisions-options, operation: touche }
---

## Objectif

Savoir ce qu'un cadrage a tranché sans avoir à le relire.

Un cadrage consulté après coup l'est le plus souvent pour une question précise :
qu'a-t-on décidé ici ? Le sommaire ne répond pas à celle-là. Il répond à « où
est la décision sur le stockage ? » — il situe, il n'énonce pas. Pour connaître
le choix retenu, il faut ouvrir chaque décision et lire son corps.

L'écart se creuse avec la maturité du référentiel. Un cadrage nourri porte
quatre décisions ou plus, chacune longue de plusieurs écrans ; ce qui a été
décidé y tient en quatre phrases, dispersées sur toute la hauteur de la fiche.
Le lecteur qui revient parcourt une fiche entière pour reconstituer ce qui
pourrait se lire d'un regard.

C'est un défaut de consultation, non de rédaction : l'information est écrite,
correctement, et reste introuvable sans un parcours complet.

## Parcours utilisateur

1. Un lecteur ouvre un cadrage déjà instruit, pour se rappeler ce qui y a été
   décidé.
2. À côté de la fiche, un récapitulatif liste les décisions tranchées : pour
   chacune, la question posée, l'option retenue et la phrase qui l'énonce.
3. Le récapitulatif reste visible pendant qu'il parcourt le reste de la fiche.
4. Une entrée le mène à la décision correspondante, dont il lit alors le
   raisonnement complet, les options écartées comprises.
5. Sur un cadrage dont rien n'est encore tranché, aucun récapitulatif
   n'apparaît : il n'y aurait rien à y mettre.
6. Sur un écran trop étroit, le récapitulatif s'efface et la fiche reprend toute
   la largeur.

## Énoncés

### RG-recapitulatif-tranchees

La consultation d'un cadrage s'accompagne d'un **récapitulatif des décisions
tranchées**, qui reste visible pendant le défilement.

Chaque entrée porte la **question posée**, l'**option retenue** et la **phrase
qui énonce le choix**. Sélectionner une entrée mène à la décision correspondante
dans la fiche.

Le récapitulatif répond à « qu'a-t-on décidé ? », là où le sommaire répond à
« où est-ce écrit ? ». Ce sont deux questions distinctes : la seconde situe, la
première énonce. Un lecteur qui revient sur un cadrage instruit pose le plus
souvent la première, et devait jusqu'ici parcourir toute la fiche pour y
répondre.

Le raisonnement, les options écartées et leurs motifs restent dans la fiche : le
récapitulatif donne le résultat, il ne remplace pas ce qui l'a produit.

Une **décision annulée en est exclue**, même lorsqu'elle désigne encore une
option retenue. Elle n'a plus rien tranché, et l'afficher présenterait un choix
révoqué comme acquis.

Le récapitulatif n'apparaît qu'à défaut de réduire la zone de lecture, comme le
sommaire, et disparaît lorsqu'aucune décision n'est tranchée.

### RG-justification-derivee

La phrase qui énonce un choix est **dérivée du corps de l'option retenue**, non
saisie séparément.

Elle s'arrête avant l'argumentaire : ce qui pèse un choix — ses avantages, ses
coûts — ne l'énonce pas.

**Lorsqu'elle ne peut pas être dérivée, rien n'est affiché.** L'entrée conserve
la question et l'option retenue. Une phrase prise au hasard dans le corps
serait présentée comme la raison du choix alors qu'elle ne l'est pas ; une
information absente se voit et s'interprète, une information fausse se croit.

Dériver plutôt que saisir vaut ici pour la même raison qu'ailleurs dans le
produit : un champ à remplir en plus du texte qui le dit déjà finit par diverger
de lui, et c'est alors le récapitulatif qui ment.
