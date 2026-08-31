---
id: 2026-016
titre: Une seule implémentation des règles du format
statut: livree
domaines: [referentiel, persistance, cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon-action' }
impacts:
  - { regle: RG-regles-partagees, operation: cree }
  - { regle: RG-verification-a-la-saisie, operation: cree }
  - { regle: RG-parseur-partage, operation: modifie }
  - { regle: RG-impacts-controles, operation: touche }
  - { regle: RG-verification-integrite, operation: touche }
  - { regle: RG-automatisation-distribuee, operation: touche }
---

## Objectif

Faire dire à l'application, pendant la rédaction, exactement ce que la
vérification dira à la livraison.

Un cadrage incohérent était refusé, mais tard : le rédacteur avait quitté le
sujet, et rouvrait un travail qu'il croyait terminé pour comprendre le message
d'un automate. La cause était pourtant connue au moment de la saisie.

Le contrôle pouvait s'écrire dans l'application. Mais les règles du format y
existent déjà en double — la lecture du format est implémentée des deux côtés, et
une règle plus ancienne l'assume en constatant que l'extraire coûterait plus que
le risque évité. Ajouter la vérification à cette duplication aurait aggravé ce
que le produit sait déjà être une dette.

La boucle a donc traité le problème par sa cause : sortir les règles du format de
l'automatisation, pour que les deux côtés les partagent au lieu de les répéter.

## Parcours utilisateur

1. Le rédacteur déclare un impact sur une règle.
2. L'application signale aussitôt ce qui empêcherait la livraison, dans les
   mêmes termes que la vérification finale.
3. Il corrige pendant qu'il y est, sans quitter le cadrage.
4. À la livraison, la vérification confirme : elle n'a rien de nouveau à dire de
   ce qui avait été signalé.

## Énoncés

### RG-regles-partagees

Les règles du format ne sont écrites **qu'une fois**, et les deux côtés qui les
appliquent — l'automatisation et l'application — partagent cette écriture au lieu
de la répéter.

Deux implémentations d'une même règle divergent : c'est une question de temps,
pas de rigueur. Et la divergence est silencieuse, puisque chacune reste cohérente
avec elle-même.

La ligne de partage n'est pas le domaine mais la dépendance au support : ce qui
raisonne sur un référentiel déjà chargé est commun, ce qui va le chercher ne
l'est pas. L'automatisation le lit sur un disque, l'application l'obtient d'un
dépôt distant, et les règles ignorent d'où il vient.

Ce qui est partagé est publié comme une bibliothèque, avec sa version : une
évolution des règles ne s'applique qu'aux consommateurs qui l'adoptent, et
chacun sait laquelle il applique.

### RG-verification-a-la-saisie

L'application signale, **pendant la rédaction**, ce qui empêcherait la livraison
du cadrage, dans les termes exacts de la vérification finale.

Elle emploie pour cela les règles partagées, non une seconde lecture du format :
un contrôle qui dirait autre chose que la vérification serait pire que pas de
contrôle du tout, puisqu'il ferait douter de celui qui fait autorité.

L'application ne dispose que du référentiel courant augmenté du cadrage en cours ;
un cadrage voisin, encore ouvert ailleurs, lui échappe. Certains contrôles y sont
donc moins conclusifs qu'à la livraison.

L'écart ne va jamais que dans un sens : l'application signale moins, jamais plus.
Ce qu'elle affirme est vrai ; ce qu'elle tait peut encore apparaître à la
livraison, où la vérification demeure l'autorité.

### RG-parseur-partage

La lecture du format et les règles qui la vérifient sont **écrites une seule
fois**, dans une bibliothèque que l'application et l'automatisation partagent.

Elles ont d'abord été implémentées deux fois, la duplication étant assumée tant
que le format n'était pas stabilisé : le montage d'un paquet partagé semblait
coûter plus que le risque qu'il éviterait.

Ce n'est plus vrai. Le besoin de vérifier un cadrage pendant sa rédaction aurait
doublé une seconde fois la même règle, et le partage s'est révélé peu coûteux :
rien dans ces règles ne dépendait du support, seulement le chargement qui les
précède.

Ce qui va chercher le référentiel reste propre à chaque côté ; ce qui raisonne
dessus est commun.
