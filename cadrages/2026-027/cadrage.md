---
id: 2026-027
titre: Préparer plusieurs cadrages à la fois, et se fier au contrôle qui le dit
statut: livree
domaines: [cadrage, persistance]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-preparation-isolee, operation: cree }
  - { regle: RG-maintien-outillage, operation: modifie }
  - { regle: RG-branche-par-cadrage, operation: touche }
  - { regle: RG-outillage-redaction, operation: touche }
---

## Objectif

Permettre de préparer plusieurs cadrages en même temps.

C'est le cas ordinaire : deux sujets ouverts, deux sessions de travail, ou
simplement un cadrage commencé qu'on reprend pendant qu'un autre avance.
L'outillage travaillait pourtant dans la copie du dépôt, comme s'il n'y avait
jamais qu'un cadrage à la fois — celle qui change de branche la change pour
tout le monde, et un enregistrement y ramasse ce qu'une autre session écrivait.

En le corrigeant, le contrôle censé prévenir ces mélanges s'est révélé
lui-même trompeur : il annonçait un travail en attente là où il n'y en avait
plus, et désignait le mauvais côté comme modifié.

## Parcours utilisateur

1. Quelqu'un commence un cadrage : l'outillage lui prépare un espace à lui, avec
   son identifiant et sa branche.
2. Il en commence un second, sans avoir livré le premier : il obtient un autre
   espace, un autre identifiant.
3. Ce qu'il écrit dans l'un reste invisible à l'autre, et la copie d'origine du
   dépôt n'est jamais touchée.
4. Chacun se livre indépendamment, quand il est prêt.
5. L'espace est retiré une fois le cadrage livré.

## Énoncés

### RG-preparation-isolee

Chaque cadrage se prépare dans un **espace de travail qui lui est propre**, non
dans la copie du dépôt.

Plusieurs cadrages se préparent en même temps, et une copie partagée les mêle :
changer de branche la change pour tous, et un enregistrement ramasse ce qu'une
autre session écrivait. Le travail se perd sans qu'aucune erreur ne soit
signalée.

L'espace porte son propre répertoire et sa propre branche, sur le même dépôt.
La copie d'origine reste sur sa branche principale, intacte.

**L'identifiant est choisi en regardant ce qui est en cours ailleurs**, non le
seul contenu du dépôt : un cadrage préparé dans un autre espace n'y est pas
encore, et deux préparations choisiraient le même numéro.

Une course subsiste, et se dit plutôt que de se taire : deux préparations
lancées au même instant peuvent retenir le même identifiant, la seconde étant
alors refusée à la livraison. Annoncer une garantie qu'on n'a pas est pire que
d'énoncer la limite.

Reprendre un espace déjà préparé le rend tel quel : c'est le cas ordinaire d'un
travail qu'on poursuit, non une collision.

### RG-maintien-outillage

L'outillage distribué porte **de quoi être mis à jour sans diverger**.

Une fois distribué, il existe en plusieurs exemplaires : la source, la copie
installée, la version publiée. Corriger la copie installée est le geste naturel
et le mauvais — le changement disparaît à la réinstallation suivante, sans
jamais atteindre personne d'autre.

**La comparaison des exemplaires précède toute modification.** Une divergence
constatée avant d'écrire est un renseignement ; découverte après, c'est du
travail perdu. L'outil de comparaison nomme lequel a bougé, sans trancher à la
place de celui qui lit.

**Il compare ce qui existe, non une liste de ce qu'il croit exister.** Un
inventaire écrit à la main oublie le fichier suivant, et ce qu'il oublie diverge
sans que rien ne le dise — ce que l'outil existe précisément pour empêcher.

**Il lit la version publiée sans intermédiaire.** Une lecture servie depuis un
cache peut rendre un état révolu, et le contrôle annonce alors un travail en
attente qui n'existe plus.

**Un contrôle qui se trompe coûte plus cher que pas de contrôle.** Il fait
douter d'un travail correct, et conduit à défaire ce qui était juste. Un message
doit donc désigner le côté qui a réellement bougé, jamais le supposer.

**Ce que rien ne vérifie doit être dit.** L'outillage n'est contrôlé par aucune
intégration continue : la procédure qui le décrit est la seule vérification qui
existe, et elle doit donc énoncer comment l'éprouver — dans les conditions de
celui qui l'exécute, jamais sur une approximation.

Une mise à jour ne se propage pas d'elle-même. Ceux qui ont installé l'outillage
ne sont ni prévenus ni mis à jour : un changement qui modifie leur façon de
travailler se dit.
