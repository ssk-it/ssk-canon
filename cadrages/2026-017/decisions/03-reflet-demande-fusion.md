---
id: 03-reflet-demande-fusion
titre: La demande de fusion doit-elle suivre le statut du cadrage ?
statut: retenue
option_retenue: sur-demande-du-projet
---

## Description

Un cadrage en cours a deux états parallèles : son statut, dans son fichier, et
l'état de sa demande de fusion sur la plateforme — brouillon ou prête à relire.

Ils décrivent la même chose sans être liés. Quelqu'un qui parcourt les demandes
ouvertes ne peut pas voir ce qui attend une relecture sans ouvrir chaque cadrage.

## Options

### aucun-reflet

Le statut vit dans le fichier, la demande reste telle quelle.

**Pour** — une seule écriture, aucun état à tenir d'accord.
**Contre** — les deux racontent des histoires différentes. Une équipe qui
travaille depuis la plateforme ne voit pas ce qui l'attend.

### reflet-systematique

La demande suit toujours le statut.

**Pour** — pas de réglage à comprendre ; les deux vues concordent partout.
**Contre** — impose une écriture supplémentaire aux projets qui n'en ont pas
l'usage, et un point d'échec de plus à chaque transition.

### sur-demande-du-projet

**Retenue.** Le reflet est tenu si le projet le demande.

**Pour** — un projet dont le client ne regarde que l'application n'a rien à
refléter ; un projet dont l'équipe vit sur la plateforme y gagne. Le choix
appartient à celui qui en connaît l'usage.
**Contre** — un réglage de plus, et deux comportements à éprouver.

## Décision

**Sur demande du projet, et le statut garde l'autorité.**

L'ordre des écritures porte cette hiérarchie : le statut d'abord, le reflet
ensuite. Un reflet qui échoue laisse un statut juste et une demande en retard,
ce qui se rattrape ; l'ordre inverse laisserait une demande annonçant un statut
que le cadrage n'a pas.

Le reflet manqué est signalé, non tu. **Une désynchronisation qu'on ignore vaut
moins qu'une désynchronisation qu'on sait devoir corriger.**

Deux constats méritent d'être conservés :

- **Une bascule demandée par le moyen apparent peut n'avoir aucun effet.** La
  voie ordinaire de modification accepte l'état de brouillon et l'ignore
  silencieusement ; il faut la voie dédiée. Un reflet qui ne reflète rien serait
  pire que pas de reflet.
- **L'état relu juste après une bascule peut être l'ancien.** Comparer avant
  d'agir laissait alors la demande figée sur le premier état. L'état voulu est
  désormais affirmé, non comparé : demander ce qui est déjà vrai ne coûte rien,
  comparer sur une lecture périmée coûtait la transition.
