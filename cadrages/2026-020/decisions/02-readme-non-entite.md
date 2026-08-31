---
id: 02-readme-non-entite
titre: Un fichier d'accueil dans un répertoire de contenu est-il une entité ?
statut: retenue
option_retenue: documentation-ecartee
---

## Description

L'amorçage dépose dans chaque répertoire une note expliquant ce qu'on y dépose.
Le référentiel les a aussitôt signalées comme mal formées : elles n'ont pas de
frontmatter, n'étant pas des entités.

Le défaut allait plus loin que l'affichage. La vérification d'intégrité en
faisait autant, et elle bloque la livraison — un dépôt amorcé de la sorte ne
pouvait plus rien livrer, chaque demande de fusion échouant sur sa propre
documentation.

## Options

### exiger-un-frontmatter-partout

Donner un frontmatter à ces fichiers pour qu'ils passent le contrôle.

**Pour** — aucune exception à écrire ; tout fichier d'un répertoire de contenu
est traité pareil.
**Contre** — ferait apparaître des entités qui n'en sont pas, dans la navigation
comme dans les comptes. Un « domaine README » n'a aucun sens.

### ne-rien-deposer-dans-les-repertoires

Renoncer aux notes, et ne créer les répertoires qu'au premier contenu.

**Pour** — le problème disparaît.
**Contre** — le support ne conserve pas un répertoire vide : il n'y aurait donc
plus de structure du tout, et celui qui ouvre le dépôt sur la plateforme ne
verrait rien de ce qu'on y attend.

### documentation-ecartee

**Retenue.** Un fichier d'accueil dans un répertoire de contenu n'est pas une
entité, et n'est examiné ni par la lecture ni par la vérification.

**Pour** — la documentation reste où elle est utile, sans être confondue avec ce
qu'elle documente.
**Contre** — une convention de nom à connaître, et une exception à tenir des deux
côtés qui lisent le format.

## Décision

**Écarter la documentation, des deux côtés.**

Le principe : **ce qui explique un répertoire n'est pas ce que le répertoire
contient.** La confusion venait d'une règle trop large — tout fichier de ce type
est une entité — qui n'avait jamais rencontré de contre-exemple parce que
personne n'avait encore documenté un répertoire.

L'enseignement est de méthode : le défaut n'est apparu qu'en amorçant un vrai
dépôt, avec un vrai compte, sur un projet qui n'était pas le nôtre. Le dépôt de
référence ne l'aurait jamais montré — il n'est ni vide, ni privé, et ses
répertoires ne portent pas de documentation.
