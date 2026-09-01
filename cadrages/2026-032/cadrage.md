---
id: 2026-032
titre: 'Déduire le statut d''un cadrage de l''état du dépôt, plutôt que le déclarer'
statut: brouillon
domaines: [cadrage, acces]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon-pwa' }
impacts:
  - { regle: RG-statuts-cadrage, operation: modifie }
  - { regle: RG-cadrages-en-cours-visibles, operation: modifie }
  - { regle: RG-verification-integrite, operation: modifie }
  - { regle: RG-cadrage-livre-immuable, operation: cree }
  - { regle: RG-validation-cadrage, operation: cree }
  - { regle: RG-branches-survivantes-signalees, operation: cree }
  - { regle: RG-branche-par-cadrage, operation: touche }
  - { regle: RG-garanties-annoncees, operation: touche }
---

## Objectif

Qu'un cadrage affiche l'état où il se trouve réellement, sans que personne ait à
le tenir à jour.

Un cadrage a été fusionné en portant `statut: brouillon`. Ses impacts n'ont pas
été propagés, et rien ne l'a signalé : le propagateur ne retient que les cadrages
déclarés livrés, et celui-ci ne l'était pas. La fusion — le fait qui établit la
livraison — n'avait aucun effet sur le champ censé la décrire.

Le relevé montre que ce n'est pas un accident isolé : sur vingt-neuf cadrages
présents sur la branche principale, trois portent un statut qui n'est pas
`livree`. Deux sont restés en brouillon, un en relecture. Le geste manuel de
passer le statut avant de fusionner marche la plupart du temps, et échoue sans
bruit le reste du temps.

Le défaut n'est pas l'oubli, il est dans le fait qu'un oubli soit possible. Le
statut duplique une information que le dépôt porte déjà — une branche, une
demande de fusion, une approbation, une fusion. Deux sources pour un seul fait
finissent toujours par diverger, et c'est l'invariant que le projet s'est donné :
l'histoire ne se stocke pas, elle se dérive.

Ce cadrage retire la duplication. Il traite au passage deux questions qui en
dépendent : ce qu'on peut encore modifier dans un cadrage livré, et comment
valider quand la plateforme s'y refuse.

## Parcours utilisateur

1. Un rédacteur ouvre un cadrage. L'application lit l'état du dépôt et affiche le
   statut qui en découle. Aucun champ à renseigner, aucun à corriger.
2. Il rédige sur sa branche. Tant qu'aucune demande de fusion n'existe, le
   cadrage est en brouillon.
3. Il demande la relecture. L'application ouvre la demande de fusion ; le cadrage
   passe en relecture, du seul fait que la demande existe.
4. Un relecteur valide depuis l'application. Elle lui demande un message, qui est
   obligatoire, et le porte sur la demande de fusion. Le cadrage est validé.
5. La demande est fusionnée. Le cadrage est livré, et la propagation applique ses
   impacts. Personne n'a rien déclaré.
6. Le rédacteur rouvre un cadrage déjà livré et tente de le modifier. La
   vérification refuse : ce qui est livré ne se reprend pas.
7. Une branche est restée après une fusion. L'application le signale sur le
   cadrage concerné, sans rien interdire.

## Ce qui a été appris en instruisant

**Le format de branche documenté n'a jamais été appliqué.** Le cadrage
d'architecture annonce `cadrage/<id>` ; les onze branches du dépôt sont toutes en
`cadrage-<id>`. Aucune n'a jamais suivi la convention écrite. L'application, elle,
teste `startsWith('cadrage/')` pour décider si elle propose les transitions de
statut — ce test échoue donc sur la totalité des branches réelles, et contredit
`RG-branche-par-cadrage`, qui interdit précisément de se fier au nom.

**Les branches ne sont pas supprimées après fusion.** Neuf des dix branches
ouvertes portent un cadrage déjà présent sur la branche principale. Un statut
dérivé doit donc trancher entre deux lectures du même cadrage, et non supposer
qu'une seule existe.

**L'auto-approbation n'est pas refusée partout.** La plateforme refuse qu'on
approuve sa propre demande de fusion. Ce n'est pas une limite du mode d'accès
mais une limite de personne : un client qui relit un cadrage dont il n'est pas
l'auteur approuve sans obstacle, même en jeton personnel. Le cas réellement
bloqué est celui où l'auteur est seul à pouvoir agir sur la plateforme.

**Une validation par commentaire édité perd ce qu'elle prétend porter.** L'API ne
rend qu'un état d'un commentaire, le dernier. Annuler une validation en éditant
le commentaire qui la porte efface la date où elle valait, et rien n'empêche de
réécrire l'ensemble. Un commentaire réécrit est un champ d'historique déguisé,
dans un support qui en garantit moins que Git.

## Énoncés

### RG-statuts-cadrage

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

### RG-cadrages-en-cours-visibles

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

### RG-validation-cadrage

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
depuis le commit qu'elle nomme. C'est ce que l'approbation native fait d'
elle-même, et une validation qui survivrait à la modification de son objet ne
voudrait plus rien dire.

L'application **annonce laquelle des deux formes elle emploie** : une approbation
est vérifiée par la plateforme, un commentaire déclare une identité que rien ne
vérifie. Conformément à RG-garanties-annoncees, taire la différence ferait se
fier à une garantie absente.

### RG-cadrage-livre-immuable

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

### RG-branches-survivantes-signalees

Une branche qui porte un cadrage **déjà livré** est signalée sur ce cadrage, avec
son nom.

Elle est sans effet — la branche principale l'emporte — mais son existence
signifie presque toujours qu'une fusion n'a pas été suivie du ménage. La relever
évite qu'on la reprenne en croyant travailler sur un cadrage en cours.

Le signalement n'interdit rien et ne bloque rien : une branche conservée
délibérément reste légitime. Il informe.

### RG-verification-integrite

Une vérification d'intégrité s'exécute à l'ouverture et à chaque modification
d'une pull request. Une erreur **empêche le merge**.

Elle contrôle ce que le format seul ne peut pas garantir : un impact référençant
une règle inexistante, un identifiant dupliqué, un énoncé manquant pour un impact
`cree` ou `modifie`, une règle abrogée par un cadrage non livré, un rattachement
vers une entité inconnue, une règle rattachée à aucune fonctionnalité, et **la
modification d'un cadrage déjà livré**.

Ce dernier contrôle porte sur un écart, non sur un état : il compare la demande
de fusion à la branche principale. La vérification a donc besoin de l'historique,
là où les autres contrôles se contentent du dernier état.

Une règle créée par un cadrage encore en relecture n'existe pas dans le
référentiel : c'est normal, et la vérification ne l'exige qu'à la livraison.

La distinction entre ce qui bloque et ce qui informe est un choix, pas un défaut
de rigueur : bloque ce qui rendrait le référentiel faux ou inatteignable, informe
ce qui relève de l'incomplétude passagère d'un travail en cours.

Un contrôle ne bloque que s'il est déclaré requis dans les règles de protection
de la branche principale. Sans cette déclaration, il signale sans empêcher, et
l'intégrité n'est plus garantie que par la bonne volonté.
