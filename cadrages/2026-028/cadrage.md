---
id: 2026-028
titre: Distinguer les domaines par la couleur, et choisir son thème
statut: livree
domaines: [referentiel, cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon-pwa' }
impacts:
  - { regle: RG-couleur-porteuse, operation: cree }
  - { regle: RG-theme-choisi, operation: cree }
  - { regle: RG-bornes-consultables, operation: touche }
---

## Objectif

Rendre le référentiel lisible d'un coup d'œil, et laisser choisir son thème.

Deux écrans quasi monochromes : la couleur ne servait qu'aux statuts de cadrage,
et quatre domaines s'affichaient en quatre cartes grises identiques. Rien ne
disait, en parcourant une liste de fonctionnalités ou de règles, de quel domaine
relevait ce qu'on lisait.

Le thème sombre, lui, suivait déjà le réglage du système. Ce qui manquait était
de pouvoir ne pas le suivre : forcer le sombre sur un poste resté en clair était
impossible.

## Parcours utilisateur

1. À l'ouverture du référentiel, chaque domaine porte sa couleur : quatre cartes
   distinctes plutôt que quatre cartes grises.
2. En ouvrant la fiche d'un domaine, la même couleur l'accompagne — c'est un
   repère qui suit le domaine, non un ornement de la page d'accueil.
3. Le bouton de thème de la barre passe de clair à sombre, puis au suivi du
   système, et revient.
4. Le choix est retenu d'une visite à l'autre. Tant qu'il vaut « système »,
   l'affichage bascule tout seul quand l'appareil bascule.

## Énoncés

### RG-couleur-porteuse

Une couleur employée dans l'application **porte une information**, jamais un
ornement.

Trois familles seulement en emploient : le **statut** d'un cadrage, l'**opération**
d'un impact, et le **domaine** auquel un contenu se rattache. Une couleur qui ne
distingue rien n'apprend rien et fatigue la lecture.

**La couleur d'un domaine n'est pas déclarée dans le référentiel.** Ce serait un
réglage de plus à tenir dans un fichier qui décrit le produit, non son
affichage. Elle est calculée, et se retrouve donc identique pour tous ceux qui
ouvrent le même dépôt.

**Elle est attribuée par rang, non tirée d'une empreinte de l'identifiant.**
Projeter une empreinte sur un petit nombre de teintes produit des collisions
bien avant d'avoir épuisé les teintes disponibles — l'ordre de quarante pour
cent dès quatre domaines. Répartir la roue entre les domaines ordonnés garantit
que deux domaines ont deux couleurs, et d'autant plus éloignées qu'ils sont peu
nombreux.

**L'ordre est celui des identifiants, non celui du chargement.** L'arborescence
que rend la plateforme n'a pas d'ordre garanti : une couleur qui en dépendrait
changerait au gré d'un ajout de fichier, et cesserait d'être un repère.

**Les teintes illisibles sont écartées, non atténuées.** À clarté utile, une
bande de la roue rend un olive terne à côté de ses voisines. Resserrer la
répartition ne fait que déplacer l'endroit où elle tombe : la bande se saute.

**La couleur ne remplace jamais le nom**, qui reste écrit à côté. Elle accélère
la lecture de qui la perçoit, et n'en prive pas les autres.

### RG-theme-choisi

L'application suit le thème clair ou sombre de l'appareil, **et se laisse
contredire**.

Trois états, non deux : clair, sombre, et le suivi du système. Ce dernier est le
défaut et un choix à part entière — le seul qui puisse changer sans que personne
ne touche à l'application.

Le choix explicite l'emporte sur le réglage de l'appareil, dans les deux sens :
forcer le clair sur un système sombre vaut autant que l'inverse.

Le choix est retenu d'une visite à l'autre. Un stockage refusé — navigation
privée, réglage du navigateur — le fait valoir pour la session seule : perdre la
mémoire d'un choix d'affichage ne justifie pas d'échouer.

Les valeurs du thème sombre sont **définies une fois** et appliquées tant au
réglage du système qu'au choix explicite. Les écrire deux fois garantirait qu'un
jour l'une des deux soit oubliée.
