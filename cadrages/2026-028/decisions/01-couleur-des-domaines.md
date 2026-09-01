---
id: '01'
titre: D'où vient la couleur d'un domaine
statut: retenue
---

## Description

Quatre domaines s'affichaient en quatre cartes grises identiques. Leur donner
une couleur suppose de dire d'où elle vient — et le référentiel ne déclare
aucune couleur.

## Options

### Déclarer la couleur dans le référentiel — écartée

Un champ `couleur:` dans le frontmatter du domaine.

Écartée : c'est un réglage de plus à tenir, dans un fichier qui décrit le
produit et non son affichage. Il faudrait le renseigner à chaque domaine créé,
et rien ne garantirait que deux domaines n'aient pas la même.

### Dériver la teinte d'une empreinte de l'identifiant — écartée sur mesure

Une empreinte du slug, projetée sur une liste de teintes lisibles. Stable,
sans rien à configurer, et calculable sans connaître les autres domaines.

**Écartée parce qu'elle ne marchait pas.** Projeter une empreinte sur douze
teintes rend les collisions probables bien avant d'avoir douze domaines :
environ quarante pour cent dès quatre, par le paradoxe des anniversaires. Le
dépôt de référence en a donné l'exemple immédiatement — « persistance » et
« referentiel » recevaient la même couleur.

Le défaut est dans le modulo, non dans la fonction de hachage : une meilleure
empreinte n'y aurait rien changé.

### Attribuer les teintes par rang — retenue

Les domaines sont ordonnés par identifiant, et l'espace des teintes est réparti
entre eux.

Deux domaines ont ainsi toujours deux couleurs, et d'autant plus éloignées
qu'ils sont peu nombreux. L'ordre est celui des identifiants et non celui du
chargement : l'arborescence que rend la plateforme n'a pas d'ordre garanti, et
une couleur qui en dépendrait changerait au gré d'un ajout de fichier.

Contrepartie assumée : la teinte d'un domaine dépend de l'ensemble des domaines,
donc en ajouter un décale les autres. C'est acceptable — un domaine s'ajoute
rarement, et la couleur reste un repère de lecture, non une identité gravée.

## Option retenue

Attribuer les teintes par rang.
