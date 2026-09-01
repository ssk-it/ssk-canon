---
id: 02-un-controle-qui-se-trompe
titre: Que faire d'un contrôle qui signale ce qui n'existe pas ?
statut: retenue
option_retenue: corriger-la-lecture-et-le-message
---

## Description

L'outil qui compare les exemplaires de l'outillage annonçait un travail en
attente pour un travail qui venait d'être livré. Et il désignait la copie
installée comme modifiée alors que c'était la source qui avait bougé.

Deux causes distinctes, mesurées :

- la version publiée était lue à travers un cache qui servait encore un état
  révolu — deux lectures de la même adresse rendaient deux contenus différents ;
- le message supposait que l'écart venait de la copie installée, sans regarder
  ce que la version publiée disait.

S'y ajoutait un troisième défaut du même ordre : l'outil comparait une liste de
fichiers écrite à la main, si bien qu'un fichier ajouté depuis n'était surveillé
par rien.

## Options

### s-en-remettre-au-jugement

Laisser le contrôle imprécis, et compter sur celui qui le lit pour interpréter.

**Pour** — rien à corriger, et un lecteur averti sait déjà quoi vérifier.
**Contre** — c'est exactement ce qui a failli faire réinstaller par-dessus une
source qui était la bonne. Un contrôle qu'il faut interpréter n'en est plus un.

### supprimer-le-controle-du-publie

Ne comparer que la source et la copie installée, les seules lectures sûres.

**Pour** — supprime la cause du faux signalement.
**Contre** — supprime aussi le seul signal qui dit qu'un travail attend d'être
livré, celui qui a le plus de valeur. On perdrait le renseignement pour éliminer
le bruit.

### corriger-la-lecture-et-le-message

**Retenue.** Lire la version publiée sans intermédiaire, et faire dire au message
quel côté a réellement bougé.

**Pour** — garde le signal utile et supprime le faux. La version publiée sert
même à départager : si la copie installée lui est identique, c'est la source qui
a changé.
**Contre** — deux corrections plutôt qu'une, sur un outil qu'on croyait fini.

## Décision

**Corriger la lecture et le message.**

Le critère : **un contrôle qui se trompe coûte plus cher que pas de contrôle.**
Il fait douter d'un travail correct, et pousse à défaire ce qui était juste. Un
contrôle absent laisse prudent ; un contrôle faux rend confiant à tort.

C'est la troisième fois dans le même cycle que ce motif se présente — après un
signalement de domaine inexistant, et une règle qui affirmait ne jamais signaler
de trop. Il mérite d'être tenu pour un enseignement, non pour trois accidents.

**Ce qui a le plus appris** : les deux lectures de la même adresse rendaient des
contenus différents, selon la manière de la demander. Rien dans le raisonnement
ne pouvait le prédire — seule la comparaison de deux résultats l'a montré.

**Sur l'inventaire écrit à la main** : le fichier ajouté n'était surveillé par
rien, dans l'outil même qui existe pour empêcher ce genre d'oubli. Ce qui
compose une chose se découvre, il ne se recopie pas — un inventaire ne vieillit
jamais bien.
