---
id: 02-reconnaitre-l-automatisation
titre: À quoi reconnaît-on qu'un dépôt a déjà son automatisation ?
statut: retenue
option_retenue: par-l-appel-a-l-action
---

## Description

Proposer d'installer ce qui est déjà là est pire que ne rien proposer : le
rédacteur qui accepte se retrouve avec deux workflows faisant le même travail,
et l'application perd la confiance qu'on lui accordait sur le reste.

La question n'est donc pas de savoir installer, mais de savoir reconnaître.

## Options

### par-le-nom-des-fichiers

Chercher les chemins exacts que l'application dépose.

**Pour** — un seul appel, aucune lecture de contenu.
**Contre** — **infirmée par l'épreuve.** Notre propre dépôt de référence, qui a
son automatisation depuis toujours, a été déclaré dépourvu : ses workflows
s'appellent `propagation.yml` et `verification.yml`, non les noms que
l'application dépose. Tout dépôt outillé avant que l'application ne sache le
faire est dans ce cas.

### par-l-appel-a-l-action

**Retenue.** Lire les workflows du dépôt, et chercher l'appel à l'action.

**Pour** — reconnaît l'automatisation quel que soit le nom, le nombre de
fichiers ou leur découpage. C'est la propriété qui compte, et la seule qui ne
dépende pas d'une convention que le dépôt n'a jamais eu à connaître.
**Contre** — un appel de plus par workflow présent. Négligeable : un dépôt en a
quelques-uns, et la question ne se pose qu'une fois par chargement.

### demander-au-depot-ses-executions

Interroger l'historique d'exécution de l'intégration continue.

**Pour** — atteste que l'automatisation tourne vraiment, pas seulement qu'elle
est déclarée.
**Contre** — un dépôt qui vient d'installer ses workflows n'a encore rien
exécuté, et serait déclaré dépourvu. Répond à une autre question que celle
posée.

## Décision

**Reconnaître à l'appel de l'action.**

Le critère qui tranche est celui-ci : **le nom d'un fichier est une convention
de celui qui l'a écrit, l'appel à l'action est un fait.** Se fonder sur le nom
revient à exiger d'un dépôt qu'il ait deviné nos conventions avant que nous ne
sachions les lui appliquer.

Le défaut n'a pas été trouvé par raisonnement mais **en regardant l'écran sur le
dépôt de référence** : les tests de structure passaient, et l'application
proposait sereinement d'installer ce qui était déjà là. C'est le genre de faute
qu'aucun test ne rattrape, parce que le code fait exactement ce qu'on lui a
demandé.

Quand la question ne peut pas être posée — le dépôt ne répond pas — l'état reste
indéterminé et rien n'est proposé. Affirmer l'absence sur une lecture qui a
échoué reproduirait le même défaut par un autre chemin.
