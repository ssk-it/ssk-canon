---
id: 02-eprouver-sur-un-projet-reel
titre: Où éprouver l'écriture, puisque la lire ne suffit pas ?
statut: retenue
option_retenue: sur-un-projet-reel-en-restaurant
---

## Description

L'écriture d'une entité met en jeu ce qu'aucune lecture ne montre : ce qui est
réellement enregistré, ce qui est réécrit sans l'être, ce qui disparaît. Les
contrôles automatisés vérifiaient que ce qui est écrit se relit — pas ce qui
arrive au reste du dépôt.

## Options

### s-en-tenir-aux-controles

Éprouver la sérialisation par des contrôles d'aller-retour.

**Pour** — rapide, reproductible, sans effet sur un dépôt réel.
**Contre** — ils prouvent que ce qui est écrit se relit, et rien de plus. Les
trois défauts trouvés portaient tous sur ce qui entoure l'écriture : une entité
refusée, des fichiers réécrits pour rien, un contenu effacé. Aucun n'était
visible sous cet angle.

### sur-un-depot-fabrique

Créer un dépôt d'essai reproduisant la structure attendue.

**Pour** — aucun risque pour un projet réel.
**Contre** — le dépôt fabriqué ressemble à ce qu'on a conçu, non à ce qu'on
rencontre. C'est précisément ce qui avait laissé passer la perte : le jeu d'essai
ne contenait que des parties reconnues, puisqu'il avait été écrit par ceux qui
les avaient définies.

### sur-un-projet-reel-en-restaurant

**Retenue.** Éprouver sur un projet réel, en relevant l'état de départ et en le
rétablissant.

**Pour** — le seul endroit où l'on rencontre ce qu'on n'a pas prévu. Les trois
défauts sont apparus là, dont un que rien d'autre n'aurait montré.
**Contre** — touche le travail de quelqu'un, et demande de savoir revenir en
arrière.

## Décision

**Éprouver sur un projet réel, après avoir relevé l'état de départ.**

Le critère : **un jeu d'essai fait à l'image de l'outil ne montre que ce que
l'outil sait déjà faire.** Il faut un dépôt écrit par quelqu'un qui n'avait pas
l'outil en tête.

Ce qui rend la chose tenable est la restauration : chaque fichier est relevé
avant, comparé après, et rétabli à l'octet près. La vérification de la
restauration compte autant que celle de l'écriture — un essai qu'on ne sait pas
défaire n'est pas un essai mais une modification.

L'enseignement dépasse ce cas : **un jeu d'essai construit par ceux qui ont conçu
le format ne contient que ce que le format prévoit.** C'est le deuxième constat
de cette nature, après celui qui disait qu'un référentiel réel se rencontre vide,
privé ou incomplet.
