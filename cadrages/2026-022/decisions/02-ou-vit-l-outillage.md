---
id: 02-ou-vit-l-outillage
titre: Où vit l'outillage de rédaction, et qui le distribue ?
statut: retenue
option_retenue: avec-le-verificateur
---

## Description

L'outillage décrit ce qu'est un cadrage : les champs, leur forme, les pièges, le
moment où une règle doit exister. Il dit la même chose que ce que
l'automatisation vérifie.

Le premier exemplaire vivait dans un projet client, et s'y trouvait par accident
plutôt que par choix — c'est là qu'on en avait eu besoin.

## Options

### dans-chaque-projet-qui-l-emploie

Une copie par projet, adaptée à chacun.

**Pour** — chaque projet ajuste ce qui le concerne, et rien ne dépend de
l'extérieur.
**Contre** — c'est l'état d'où l'on part, et il ne passe pas à l'échelle : un
dépôt nommé en dur onze fois, donc utilisable par un projet. La deuxième copie
diverge de la première le jour où on la fait.

### embarque-dans-l-application

L'application porte l'outillage et le sert.

**Pour** — aucun appel extérieur, rien qui puisse échouer, et l'application
maîtrise ce qu'elle distribue.
**Contre** — deux descriptions du format à tenir d'accord, celle de
l'application et celle du vérificateur. Elles changeraient séparément, et une
description qui contredit le contrôle qui l'applique est pire qu'aucune
description : elle fait perdre du temps avec autorité.

### avec-le-verificateur

**Retenue.** L'outillage est publié avec l'automatisation qui vérifie le format,
et l'application indique comment l'installer.

**Pour** — une seule description du format au monde, versionnée avec le contrôle
qui l'applique. Quand le format change, les deux changent ensemble.
**Contre** — l'application dépend d'un dépôt extérieur pour cette fonction, et
n'installe rien elle-même : elle montre quoi faire.

## Décision

**Publier l'outillage avec le vérificateur.**

Le critère : **ce qui décrit le format et ce qui le contrôle doivent changer
ensemble.** Séparés, ils se contredisent tôt ou tard, et rien ne le signale —
c'est exactement la dérive silencieuse que le produit s'emploie à rendre visible
ailleurs.

C'est la même raison qui avait fait publier l'automatisation séparément de
l'application : le découpage suit la nature de ce qui est distribué, non la
commodité.

L'application ne se contente pas de renvoyer à une documentation : elle donne la
commande, la configuration, et **le bloc à déclarer rempli de ce que le projet
ouvert déclare déjà.** Un exemple générique recopié par-dessus une déclaration
existante l'efface.
