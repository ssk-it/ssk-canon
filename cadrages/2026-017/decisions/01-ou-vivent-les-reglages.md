---
id: 01-ou-vivent-les-reglages
titre: Où régler ce que l'application s'autorise ?
statut: retenue
option_retenue: dans-le-projet
---

## Description

Les projets ne travaillent pas tous de la même façon. Certains veulent qu'un
cadrage puisse revenir en arrière, d'autres non ; certains vivent sur la
plateforme, d'autres seulement dans l'application.

Fixer un fonctionnement unique dans le produit imposerait à tous celui d'un seul.
Reste à savoir où le réglage vit — et la réponse décide de qui il engage.

## Options

### en-dur-dans-le-produit

Un cycle fixe, sans réglage.

**Pour** — rien à écrire, rien à lire, aucun état à tenir.
**Contre** — impose un fonctionnement à tous les projets, y compris ceux dont
l'organisation diffère. Et la question reviendrait au premier client dont le
cycle ne colle pas.

### dans-le-navigateur

Un réglage local, comme le dépôt consulté.

**Pour** — immédiat, sans écriture ni relecture.
**Contre** — chacun aurait le sien. Un réglage d'équipe qui varie d'un poste à
l'autre ne règle rien : deux personnes verraient des transitions différentes sur
le même cadrage, sans pouvoir en discuter.

### dans-le-projet

**Retenue.** Un réglage dans le fichier de configuration du projet, versionné
avec lui.

**Pour** — vaut pour tous ceux qui travaillent sur le projet, se relit sur la
plateforme, suit le dépôt s'il change de mains. Et sa modification est relisible
comme toute autre.
**Contre** — modifier un réglage demande une écriture et une relecture, là où
une case à cocher serait immédiate.

## Décision

**Dans le projet, avec ses autres réglages.**

Le critère est celui que le produit applique déjà partout : **ce qui engage
plusieurs personnes vit dans le dépôt.** Un réglage de confort personnel — le
dépôt consulté, le jeton — reste local ; un réglage qui décide de ce que l'outil
autorise à toute une équipe ne peut pas dépendre du navigateur de celui qui l'a
coché en dernier.

La lourdeur est réelle et assumée : passer par une relecture pour changer un
réglage, c'est reconnaître qu'il engage autre chose que soi.
