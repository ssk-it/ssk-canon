---
id: RG-maintien-outillage
fonctionnalites: [redaction-cadrage, impacts-regles]
statut: actif
cree_par: 2026-023
modifie_par: [2026-027]
---

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
