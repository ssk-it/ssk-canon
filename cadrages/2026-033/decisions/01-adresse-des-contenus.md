---
id: 01-adresse-des-contenus
titre: Comment faire qu'une lecture montre ce qui vient d'être écrit ?
statut: retenue
option_retenue: adresse-du-commit
---

## Description

Les contenus sont lus par un canal non décompté du quota, qui sert ses réponses
avec cinq minutes de cache. L'adresse demandée porte le nom de la branche : elle
ne change pas quand le contenu change. Après une écriture, le navigateur ressert
donc sa copie sans même revalider, et le réseau de diffusion la sienne derrière
lui.

La difficulté tient à ce qu'une écriture ne peut rien invalider : rien, dans la
requête suivante, ne la distingue de la précédente. Le problème n'est pas la
durée du cache, mais le fait que deux contenus différents partagent une adresse.

Le canal était par ailleurs choisi pour une raison qui tient toujours : sans
connexion, la limite est de soixante appels par heure, et un référentiel modeste
compte plusieurs dizaines de fichiers. Toute option qui repasse par l'API se paie
en quota.

## Options

### adresse-de-branche

Ne rien changer, et documenter le délai — ce qui était l'état des lieux : la
contrepartie était connue, constatée, et laissée telle quelle.

**Pour** — rien à faire. Sans conséquence pour la consultation ordinaire, où l'on
ne vient pas de récrire ce qu'on lit.

**Contre** — le délai frappe exactement au moment où l'on veut vérifier son
travail. Il n'est pas explicable à un client : l'application affirme avoir
enregistré, et montre le contraire.

### revalidation-demandee

Demander explicitement une revalidation à chaque lecture, par les en-têtes prévus
pour cela.

**Pour** — ne change ni le canal ni l'adressage, et le format des réponses
l'admet.

**Contre** — ne traite que la moitié du chemin. Le navigateur redemanderait, mais
le réseau de diffusion resservirait sa copie : le cache qui gêne n'est pas celui
du poste. L'option paraît suffisante et ne l'est pas, ce qui est pire que de ne
rien faire.

### canal-api

Basculer les contenus sur l'API, immédiate, après chaque écriture — le réglage
existait déjà pour les dépôts privés.

**Pour** — la fraîcheur est garantie, par un mécanisme déjà écrit et éprouvé.

**Contre** — un appel décompté par fichier. Sans connexion, un seul chargement
épuise le quota horaire ; c'est la contrainte qui a fait choisir l'autre canal.
Et il faudrait décider quand rebasculer, ce qui ajoute un état à tenir pour un
défaut qu'on peut supprimer.

### adresse-du-commit

**Retenue.** Demander chaque fichier à l'empreinte du commit que l'appel
d'arborescence vient de résoudre, non au nom de la branche.

**Pour** — l'adresse est neuve à chaque écriture, donc jamais déjà en cache, ni
au poste ni au réseau de diffusion. Le cache cesse de nuire sans cesser de
servir : une adresse datée est immuable, elle mérite d'être gardée. Aucun appel
supplémentaire, aucun point de quota — l'appel d'arborescence rend déjà
l'empreinte du commit, et non celle de l'objet arbre comme on pouvait le croire.

**Contre** — après chaque commit, toutes les adresses changent : les fichiers
sont retéléchargés au lieu d'être revalidés. Sur un canal hors quota qui sert du
texte, l'effet n'est pas mesurable ; et l'ancien comportement ne revalidait rien,
il servait périmé.

## Décision

Ce qui a tranché : **l'empreinte du commit était déjà dans une réponse qu'on
obtenait de toute façon.** L'option la plus juste se trouvait aussi être la moins
coûteuse — vérifié plutôt que supposé : `git/trees/main` rend l'empreinte du
commit, `44a74bb…`, quand l'arbre de ce commit vaut `79b2cbd…`.

Le principe qui en ressort dépasse le cas : un cache ne se combat pas en changeant
de canal, mais en changeant d'adresse. C'est ce que le projet fait déjà pour les
pièces jointes, adressées par le contenu ; la lecture n'y échappait que par
habitude.
