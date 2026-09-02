---
id: 2026-033
titre: 'Lire ce qui vient d''être écrit, sans attendre qu''un cache expire'
domaines: [persistance, cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon-pwa' }
impacts:
  - { regle: RG-lecture-refletant-ecriture, operation: cree }
  - { regle: RG-chargement-hors-quota, operation: modifie }
  - { regle: RG-reprise-cadrage, operation: modifie }
  - { regle: RG-cadrages-en-cours-visibles, operation: touche }
  - { regle: RG-rien-inventer, operation: touche }
---

## Objectif

Qu'un rédacteur qui vient d'enregistrer voie son travail en relisant le cadrage,
immédiatement, sans avoir à recharger ni à attendre.

Le défaut rapporté : une option tranchée dans une décision, enregistrée sans
erreur, n'apparaissait comme retenue dans la vue lecture qu'après plusieurs
dizaines de secondes. Rien n'indiquait quoi faire — ni message, ni progression —
et le seul geste disponible était de recharger jusqu'à ce que ça vienne.

Ce que la lecture montrait n'était pas faux au moment où elle l'avait obtenu :
c'était l'état d'avant, servi par un cache. Un outil de cadrage ne peut pas
laisser douter de ce qu'il a enregistré. Le rédacteur y écrit une décision qu'il
vient de prendre en réunion, et l'écran lui répond qu'elle n'y est pas.

Ce cadrage supprime les trois causes du délai, qui étaient distinctes et se
masquaient l'une l'autre : l'adresse à laquelle les contenus sont demandés, le
fait que rien ne relisait le référentiel après une écriture, et une relecture qui
aurait effacé la saisie en cours si on l'avait simplement ajoutée.

## Parcours utilisateur

1. Un rédacteur reprend un cadrage, tranche une option d'une décision et
   enregistre.
2. L'application confirme l'enregistrement, puis relit le référentiel d'elle-même.
3. Il revient à la vue lecture : l'option est marquée comme retenue. Il n'a rien
   rechargé, et n'a pas eu à savoir qu'un cache existait.
4. S'il continue à saisir pendant que la relecture se termine, sa saisie reste :
   la relecture ne repeuple pas un formulaire déjà ouvert.
5. Le cadrage vit sur une branche, relue en second : le temps que sa lecture
   aboutisse, l'application dit ce qu'elle attend plutôt que de laisser conclure
   à un échec.

## Ce qui a été appris en instruisant

**Deux canaux de lecture, deux fraîcheurs.** Le formulaire d'édition lit par
l'API, immédiate ; la vue lecture lit par le canal non décompté, servi avec cinq
minutes de cache. Le même cadrage se montrait donc à jour d'un côté et périmé de
l'autre, ce qui rendait le défaut incompréhensible : l'écriture avait
manifestement eu lieu, puisqu'on la relisait dans le formulaire.

**Un cache ne se combat pas en changeant de canal, mais en changeant d'adresse.**
L'ancienneté servie tenait à ce que l'adresse d'une branche ne change pas quand
son contenu change. Rien, dans la requête suivante, ne la distinguait de la
précédente : ni le navigateur ni le réseau de diffusion n'avaient de raison de
redemander. Une écriture ne peut pas invalider ce cache — il n'y a rien à
invalider.

**L'adresse du commit était déjà là.** Interrogé sur une branche, l'appel qui rend
l'arborescence répond avec l'empreinte du **commit** résolu, non celle de l'objet
arbre. Vérifié sur ce dépôt même : `git/trees/main` rend `44a74bb…`, quand
l'arbre du commit vaut `79b2cbd…`. La correction ne coûte donc aucun appel
supplémentaire, ni aucun point de quota.

**Le défaut visible en cachait un autre, plus grave.** Rien ne relisait le
référentiel après un enregistrement : la vue lecture serait restée sur l'état
d'avant indéfiniment. Le cache n'a été remarqué que parce qu'il rendait le
rechargement manuel — le seul recours — inopérant pendant quelques minutes.

**Ajouter la relecture aurait introduit une perte de saisie.** Le formulaire se
remplit à partir de l'état du magasin ; toute relecture du référentiel le
repeuplait, donc écrasait ce qui était en cours de frappe. Le défaut existait déjà
pour le rechargement manuel, sans que personne l'ait rencontré.

## Énoncés

### RG-lecture-refletant-ecriture

Ce qui vient d'être écrit est **lisible immédiatement**, sans geste
supplémentaire et sans délai d'attente.

Deux conditions, l'une et l'autre nécessaires :

**Les contenus se demandent à une adresse qui change quand ils changent.** Le
canal non décompté sert ses réponses avec un cache de plusieurs minutes, portant
sur l'adresse demandée. L'adresse d'une branche est stable alors que son contenu
ne l'est pas : elle sert donc l'état d'avant, sans qu'une écriture puisse rien y
faire. L'adresse d'un état daté du dépôt — le commit — est neuve à chaque
écriture, donc jamais déjà en cache. La contrepartie assumée : après un commit,
tous les fichiers sont redemandés au lieu d'être revalidés ; sur un canal hors
quota qui sert du texte, elle est sans effet mesurable, et l'ancien comportement
ne revalidait rien puisqu'il servait périmé.

**Une écriture est suivie d'une relecture.** L'application ne suppose pas ce
qu'elle vient d'écrire : elle le relit, et affiche ce que le dépôt rend. Corriger
l'état en mémoire afficherait ce qu'on croit avoir écrit, non ce qui est écrit,
et masquerait précisément les écarts qu'une relecture révèle.

Tant qu'une lecture attendue n'est pas revenue, **l'application dit ce qu'elle
attend** plutôt que de laisser conclure à un échec. Ce cas subsiste pour les
cadrages en cours, lus en second sans bloquer le premier affichage.

### RG-chargement-hors-quota

Le chargement d'un dépôt consomme **une seule requête décomptée**, quel que soit
le nombre de fichiers.

L'arborescence est obtenue par un appel unique ; les contenus sont ensuite
récupérés par un canal non décompté, **à l'empreinte du commit que cet appel a
résolu** — jamais au nom d'une branche, dont l'adresse stable ferait resservir un
état périmé après une écriture. L'empreinte est rendue par l'appel
d'arborescence : la lecture datée ne coûte donc rien de plus.

Cette contrainte n'est pas une optimisation mais une condition de
fonctionnement : sans connexion, la limite est de soixante appels par heure,
alors qu'un référentiel modeste compte déjà plusieurs dizaines de fichiers.

**Le canal des contenus bascule sur celui de l'arborescence** lorsque le premier
ne dessert pas le dépôt, au prix d'un appel par fichier. C'est le cas des dépôts
privés : le canal non décompté leur répond comme à un dépôt absent, même à qui y
a droit. La bascule est automatique — attendre un réglage manuel reviendrait à
présenter un dépôt privé comme introuvable à celui qui vient d'y écrire.

Elle ne se demande plus pour afficher ce qui vient d'être écrit : la lecture au
commit le garantit sur les deux canaux, et un réglage n'a de sens que si son
absence laisse un choix.

### RG-reprise-cadrage

Un cadrage se **reprend tant qu'il n'est pas livré**, depuis l'endroit où son
travail se trouve : sa propre branche.

La branche du cadrage fait autorité sur la branche principale, qui ne le connaît
pas encore. Un cadrage qui n'en a pas — rédigé hors de l'application, ou déjà
dans le référentiel — se reprend depuis la branche principale, et l'application
le signale plutôt que de laisser croire à un travail isolé qui n'existe pas.

Chaque écriture se fonde sur la version lue. Deux rédacteurs travaillant
simultanément sur le même cadrage produisent alors un conflit, plutôt qu'un
écrasement silencieux du travail de l'un par l'autre.

**Une saisie ouverte ne se repeuple pas.** Un cadrage repris est lu une fois ;
les relectures du référentiel qui suivent — celle d'un enregistrement, celle
qu'un lecteur demande — ne réécrivent pas le formulaire. Le seul écrasement
silencieux qu'un rédacteur ne peut pas voir venir est celui que l'application
s'inflige à elle-même.

Un cadrage livré ne se reprend plus : ses impacts sont propagés, et le rouvrir
ferait diverger le référentiel des cadrages qui le produisent.
