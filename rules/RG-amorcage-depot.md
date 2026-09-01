---
id: RG-amorcage-depot
fonctionnalites: [redaction-cadrage, stockage-git]
statut: actif
cree_par: 2026-020
modifie_par: [2026-021]
---

L'application **dépose la structure d'un référentiel** dans un dépôt qui n'en a
pas encore.

Signaler qu'un dépôt est vide ne suffit pas : le projet devrait alors composer à
la main une arborescence dont il ne connaît pas les conventions, au moment précis
où il découvre l'outil.

L'amorçage écrit directement, sans passer par une demande de fusion. C'est la
seule écriture dans ce cas : il n'y a rien à relire dans un dépôt vide, et une
branche ne peut de toute façon pas diverger de ce qui n'existe pas encore.

Chaque répertoire reçoit une note expliquant ce qu'on y dépose. Un répertoire
vide n'étant pas conservé par le support, il lui faut de toute façon un fichier :
autant qu'il serve à celui qui ouvre le dépôt sur la plateforme.

**L'amorçage propose d'installer l'automatisation**, et ne demande que le nom du
projet. Le reste est facultatif : ce que le produit fait ne se devine pas, et
un dépôt amorcé sans automatisation ne protège rien.

**L'installation vient après le dépôt de la structure, non pendant.** Le droit
d'écrire les workflows est distinct, et peut manquer là où le reste passe : si
l'ordre était inverse, un refus laisserait un dépôt à moitié amorcé.
