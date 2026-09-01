---
id: 2026-022
titre: Rédiger un cadrage depuis un dépôt de code
domaines: [cadrage, persistance]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-depots-code-declares, operation: cree }
  - { regle: RG-outillage-redaction, operation: cree }
  - { regle: RG-automatisation-distribuee, operation: modifie }
  - { regle: RG-format-fichier, operation: touche }
  - { regle: RG-installation-automatisation, operation: touche }
---

## Objectif

Permettre de rédiger un cadrage sans quitter le dépôt de code sur lequel on
travaille.

Le référentiel vit à part du code, et c'est ce qui le rend consultable. Mais
celui qui vient de comprendre ce qu'il faut décider est dans le dépôt de code,
pas dans celui du cadrage. L'écart se paie en cadrages qu'on remet à plus tard,
puis qu'on n'écrit pas.

Un premier outillage l'avait montré autrement : il nommait un dépôt en dur onze
fois, et n'était donc utilisable que par un projet. La deuxième copie aurait
divergé de la première le jour où on l'aurait faite.

## Parcours utilisateur

1. Quelqu'un travaille dans un dépôt de code et veut cadrer ce qu'il vient de
   décider.
2. L'outil de rédaction reconnaît ce dépôt et trouve le référentiel du projet,
   sans qu'on lui dise lequel.
3. Il y voit aussi les autres dépôts qui composent le projet, et peut donc
   chercher ce qui existe déjà dans l'ensemble du code, non dans le seul dépôt
   d'où il part.
4. Le cadrage s'écrit dans le dépôt de cadrage, jamais dans celui du code.
5. Si le référentiel ne déclare pas encore ses dépôts de code, l'outil le dit et
   montre quoi déclarer.

## Énoncés

### RG-depots-code-declares

Un référentiel **déclare les dépôts de code que le projet réalise.**

La vue « projet » appartient au référentiel : plusieurs dépôts de code la
composent — une application, une interface de programmation, un client mobile —
et aucun d'eux ne connaît les autres.

**Le lien est déclaré une seule fois, du côté qui a autorité.** Le déclarer dans
chaque dépôt de code écrirait *n* fois ce qui est un fait unique, sans rien qui
garantisse que les copies restent d'accord.

Rien n'est donc à configurer dans un dépôt de code : la plateforme le nomme
déjà, et ce nom suffit à retrouver le projet qui le déclare.

Une déclaration mal formée est écartée et signalée, sans rendre le référentiel
illisible : elle sert à se situer, et une entrée douteuse ne doit pas empêcher
de consulter.

### RG-outillage-redaction

L'outillage de rédaction est **distribué avec le format, non avec
l'application.**

Il décrit ce qu'est un cadrage — les champs, les pièges, le moment où une règle
doit exister. C'est la même chose que vérifie l'automatisation : les publier
séparément ferait deux descriptions du format, qui divergeraient dès la première
correction.

Il ne se recopie pas dans les projets qui l'emploient. Une copie par projet est
une divergence par projet, et l'outillage cesse alors de décrire le format pour
ne plus décrire que l'état où on l'a laissé.

**L'application indique comment l'installer et le configurer**, en reprenant ce
que le projet ouvert déclare déjà plutôt qu'un exemple générique. Un exemple
qu'on recopie par-dessus sa propre déclaration l'efface.

Ce qui décrit la machine du rédacteur — où les référentiels sont clonés — vit
chez lui, et ne se commite nulle part. Ce qui décrit le projet vit dans le
référentiel.

### RG-automatisation-distribuee

L'automatisation du cadrage — vérification d'intégrité et propagation — est
**publiée séparément de l'application**, sous une licence ouverte.

Elle s'exécute chez l'utilisateur, sur son dépôt, dans son environnement
d'intégration continue. Une automatisation qui s'exécute chez l'utilisateur mais
qu'il ne peut ni lire ni atteindre est une dépendance opaque au cœur de son
processus de livraison.

La contrainte qui l'impose est vérifiée : une automatisation hébergée dans un
dépôt fermé n'est référençable que depuis la même organisation. La rendre
publique supprime la question plutôt que de la contourner — un dépôt cadré peut
appartenir à qui veut.

Le partage suit la nature de ce qui est distribué, non la commodité du
découpage : ce qui tourne chez l'utilisateur lui est accessible, ce qui tourne
chez l'éditeur ne l'est pas.

**Ce qui décrit le format y est publié avec ce qui le vérifie**, et non avec
l'application : une description du format et le contrôle qui l'applique doivent
changer ensemble, sous peine de se contredire sans que rien ne le signale.
