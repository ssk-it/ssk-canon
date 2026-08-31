---
id: 01-gamme-de-modes
titre: Un montage unique, ou une gamme ?
statut: retenue
option_retenue: une-gamme-reglee-par-le-projet
---

## Description

Ouvrir l'outil au client suppose qu'il n'ait pas à créer de compte sur la
plateforme de dépôt. Cela demande un composant intermédiaire détenant les droits,
donc une infrastructure à héberger.

Or tous les projets n'en ont pas besoin. Une équipe qui travaille seule sur son
propre dépôt fonctionne très bien avec ce qui existe : chacun apporte son jeton.
Lui imposer une infrastructure pour un problème qu'elle n'a pas serait absurde.

## Options

### le-montage-le-plus-complet-pour-tous

Retenir le relais, et l'imposer à tous les projets.

**Pour** — un seul comportement à écrire, à documenter et à éprouver. Les
garanties les plus fortes partout.
**Contre** — impose une infrastructure à qui n'en a pas besoin, et fait dépendre
la consultation d'un composant supplémentaire. Un projet qui veut simplement lire
un référentiel devrait attendre qu'on lui héberge un relais.

### le-montage-le-plus-simple-pour-tous

S'en tenir au jeton personnel, et renoncer à l'ouverture au client.

**Pour** — aucune infrastructure, aucun choix à expliquer.
**Contre** — laisse le client dehors, alors que le produit prétend être partagé
entre lui et l'équipe. C'est renoncer à la moitié de sa raison d'être.

### une-gamme-reglee-par-le-projet

**Retenue.** Trois modes, déclarés dans la configuration du projet, du plus
simple au plus garanti.

**Pour** — chaque projet paie ce dont il a besoin. Le mode le plus simple reste
le défaut, donc rien ne se complique pour qui s'en contente. Et passer d'un mode
au suivant ne demande de reprendre ni le référentiel ni les cadrages.
**Contre** — trois comportements à écrire et à tenir, et une gamme à expliquer.

## Décision

**Une gamme, réglée par le projet.**

Ce qui la rend praticable est que les modes **s'empilent** : chacun lève un
obstacle que le précédent laissait, sans annuler ce qu'il apportait. Ce n'est pas
trois produits mais un seul, dont l'accès se règle.

Le réglage a sa place naturelle : la configuration du projet porte déjà ce que
l'application s'autorise à faire. Le mode d'accès est de la même nature — il
engage tous ceux qui travaillent sur le projet, donc il vit dans le projet.

Enseignement à retenir : **quand une contrainte ne vaut que pour une partie des
usages, la traiter comme un réglage plutôt que comme une décision.** L'imposer à
tous fait payer à chacun le problème du plus exigeant.
