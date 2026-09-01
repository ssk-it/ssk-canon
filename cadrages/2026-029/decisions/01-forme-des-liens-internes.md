---
id: 01-forme-des-liens-internes
titre: Comment un lien interne porte-t-il le projet ouvert ?
statut: retenue
option_retenue: fabrique-centrale
---

## Description

Une fois toute vue placée sous `/<organisation>/<depot>/`, chaque lien de
l'application doit mener au bon projet. Les liens étaient écrits en absolu —
`/referentiel`, `/cadrages/<id>` — à une vingtaine d'endroits répartis dans les
pages. Chacun d'eux sortait désormais du projet.

La difficulté n'est pas de les corriger une fois, mais d'empêcher qu'un lien
écrit plus tard reparte en absolu. Un tel lien ne casse rien de visible : il
mène à une page qui s'affiche, avec le contenu d'un autre projet.

## Options

### liens-relatifs

Écrire les liens relativement à la route courante, en remontant le nombre de
niveaux voulu — `['../..', 'cadrages']`.

**Pour** — mécanisme du routeur, sans code à soi.
**Contre** — le nombre de niveaux à remonter dépend de la page d'où l'on part.
Le même lien s'écrit différemment depuis une liste et depuis une fiche de
détail, et déplacer une vue dans l'arborescence invalide silencieusement tous
ses liens. La justesse dépend d'un comptage que rien ne vérifie.

### fabrique-centrale

**Retenue.** Un service unique construit les chemins à partir du projet ouvert :
`liens.vers('cadrages', id)`. Les pages ne connaissent plus le préfixe.

**Pour** — un seul endroit fabrique le préfixe, donc un seul endroit à changer
si la forme de l'adresse évolue. L'écriture est la même partout, quelle que soit
la profondeur de la page.
**Contre** — chaque page doit injecter le service, et un lien écrit en absolu
reste possible : rien dans le compilateur ne l'interdit.

## Décision

**Ce qui a tranché : la relative se trompe en silence, la fabrique se trompe de
façon repérable.** Un lien relatif mal compté mène à une page plausible ; un lien
absolu oublié se voit à la relecture, parce qu'il ne ressemble pas aux autres.
Entre deux mécanismes faillibles, celui dont l'erreur est visible l'emporte.

Le contre retenu — l'absence de garde-fou automatique — est réel. Une
vérification l'attraperait, mais à vingt-et-un liens et une forme d'écriture
uniforme, elle coûterait plus que la relecture qu'elle remplace. À reconsidérer
si un lien absolu réapparaît.
