---
id: RG-amorcage-depot
fonctionnalites: [redaction-cadrage, stockage-git]
statut: actif
cree_par: 2026-020
modifie_par: []
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
