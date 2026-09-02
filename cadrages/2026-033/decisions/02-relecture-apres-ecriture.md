---
id: 02-relecture-apres-ecriture
titre: Que montre l'application juste après un enregistrement ?
statut: retenue
option_retenue: relire-le-depot
---

## Description

Après un enregistrement, rien ne relisait le référentiel. La vue lecture
continuait d'afficher l'état chargé à l'ouverture de l'application, sans limite
de temps : le rédacteur devait recharger de lui-même, sans que rien ne le lui
dise.

C'est ce qui rendait le cache visible. Le seul recours — recharger — était aussi
le geste sur lequel le cache mordait, d'où l'impression d'un enregistrement qui
n'aboutit pas.

## Options

### rechargement-manuel

Laisser le rédacteur recharger, la barre d'outils portant déjà un bouton pour
cela.

**Pour** — aucun appel supplémentaire, et le rédacteur garde la main sur le
moment où l'état change sous ses yeux.

**Contre** — il faut savoir qu'il faut le faire. Rien ne distingue à l'écran un
état non relu d'un état à jour, et c'est exactement la confusion rapportée.

### corriger-en-memoire

Appliquer à l'état chargé ce qu'on vient d'écrire, sans relire.

**Pour** — immédiat, et sans le moindre appel.

**Contre** — affiche ce qu'on croit avoir écrit, non ce qui est écrit. Un cadrage
en cours vit sur une branche ; ce qui y arrive par ailleurs — une propagation, un
autre rédacteur — resterait invisible, et la mémoire divergerait du dépôt sans
que rien ne le signale. C'est le raisonnement qui avait déjà écarté cette option
pour l'ajout d'un lien.

### relire-le-depot

**Retenue.** Relire le référentiel après un enregistrement réussi, et afficher ce
que le dépôt rend.

**Pour** — l'écran montre l'état réel, pas une hypothèse. Ce qu'un autre a écrit
entre-temps apparaît par la même occasion. La lecture au commit — décision 01 —
rend cette relecture fidèle, ce qu'elle n'aurait pas été seule.

**Contre** — un chargement complet après chaque enregistrement. Un appel décompté,
le reste hors quota ; et la relecture des cadrages en cours se poursuit après
coup, si bien que ce qui vit sur une branche peut arriver une seconde plus tard.

## Décision

Ce qui a tranché : **une relecture révèle les écarts qu'une correction en mémoire
masque.** Les deux options rapides — ne rien faire, ou corriger l'état — laissent
l'écran affirmer quelque chose que personne n'a vérifié. C'est précisément ce
qu'un outil de cadrage ne peut pas se permettre.

Le coût est un chargement par enregistrement, sur une action rare et délibérée.
Le cas des cadrages en branche, relus en second, reste signalé à l'écran plutôt
que masqué : dire qu'on attend vaut mieux que de laisser conclure à un échec.
