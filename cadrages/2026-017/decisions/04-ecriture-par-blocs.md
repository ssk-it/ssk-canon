---
id: 04-ecriture-par-blocs
titre: Comment écrire dans un fichier que des humains relisent ?
statut: retenue
option_retenue: remplacer-les-blocs
---

## Description

Modifier un réglage depuis l'application suppose de réécrire le fichier de
configuration du projet. Ce fichier n'est pas une base de données : il se relit
sur la plateforme, et ses commentaires expliquent à quoi servent les réglages.

Le réécrire entièrement à partir de sa représentation en mémoire est la façon
évidente de faire. Elle a été mesurée : **les cinq commentaires du fichier
disparaissent**, et les textes longs sont reformatés sans que personne l'ait
demandé.

## Options

### reecrire-le-document

Relire le fichier, modifier la valeur, réécrire le tout.

**Pour** — simple, et garantit un document bien formé.
**Contre** — détruit tout ce qui n'est pas une donnée : commentaires, mise en
forme, ordre choisi. Un fichier écrit par un humain revient méconnaissable après
un simple changement de case à cocher.

### remplacer-les-blocs

**Retenue.** Ne remplacer, dans le texte, que les blocs concernés.

**Pour** — tout le reste est conservé au caractère près, y compris ce que
l'application ne sait pas lire. La relecture ne montre que ce qui a changé.
**Contre** — manipulation de texte plutôt que de données, donc plus fragile : il
faut savoir où un bloc commence et finit.

## Décision

**Remplacer les blocs, et rien d'autre.**

Le critère : **un fichier que des humains relisent doit revenir tel qu'ils l'ont
laissé, à l'exception de ce qui a changé.** Une relecture qui montre trente
lignes modifiées pour un réglage n'est plus une relecture — personne n'y cherche
la vraie modification.

Un détail l'a confirmé au-delà du principe. Les commentaires réécrits employaient
des apostrophes typographiques là où le fichier utilisait des apostrophes
droites : quatre lignes apparaissaient modifiées sans que rien n'y ait bougé.
Le format valide, les valeurs justes, et pourtant du bruit à chaque relecture.

Aucun test ne l'aurait signalé : il a fallu regarder la comparaison produite. **Ce
qu'on écrit pour être relu se vérifie sur ce que le relecteur verra**, pas sur
ce que le format autorise.
