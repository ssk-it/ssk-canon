---
id: RG-couleur-porteuse
fonctionnalites: [modele-referentiel, consultation-cadrage]
statut: actif
cree_par: 2026-028
modifie_par: []
---

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
