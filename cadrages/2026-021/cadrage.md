---
id: 2026-021
titre: Installer l'automatisation, et cesser d'inventer une description
domaines: [cadrage, persistance]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-installation-automatisation, operation: cree }
  - { regle: RG-rien-inventer, operation: cree }
  - { regle: RG-amorcage-depot, operation: modifie }
  - { regle: RG-message-nomme-la-cause, operation: touche }
  - { regle: RG-automatisation-distribuee, operation: touche }
  - { regle: RG-verification-integrite, operation: touche }
---

## Objectif

Un dépôt amorcé par l'application ne portait pas son automatisation. Rien n'y
vérifiait qu'un cadrage est cohérent avant sa livraison, et rien n'y mettait les
règles à jour une fois livré : le référentiel cessait d'être la projection des
cadrages livrés, ce dont tout le reste dépend.

Deux fichiers à copier suffisaient — assez peu pour qu'on le remette à plus tard,
assez conséquent pour que l'oubli se paie. Le premier dépôt réel amorcé est resté
sans automatisation, et personne ne l'a vu, parce que rien ne le disait.

Dans le même mouvement, l'application inventait la description du projet quand
le champ était laissé vide. « Le référentiel de X » n'est ni faux ni vrai : c'est
une phrase que personne n'a écrite, et que ceux qui la lisent ensuite prennent
pour une intention.

## Parcours utilisateur

1. Quelqu'un amorce un dépôt vide. Une case, cochée d'emblée, propose d'y
   installer l'automatisation ; il la laisse cochée.
2. L'application dépose la structure du référentiel, puis les workflows.
3. S'il n'a pas le droit d'écrire les workflows, le dépôt reste amorcé et le
   message nomme la permission qui manque.
4. Sur un dépôt déjà amorcé qui n'a pas son automatisation, les réglages le
   disent et proposent de l'installer.
5. Sur un dépôt qui l'a déjà, sous quelque nom de fichier que ce soit, rien
   n'est proposé.

## Énoncés

### RG-installation-automatisation

L'application **installe l'automatisation** dans un dépôt cadré qui n'en a pas :
pendant l'amorçage, par une case cochée d'emblée, et depuis les réglages tant
qu'elle manque.

Un dépôt cadré sans automatisation ne tient pas la promesse du format. Rien n'y
empêche de livrer un cadrage incohérent, et les règles n'y sont jamais mises à
jour. L'oubli ne se voit qu'à la première livraison incohérente, c'est-à-dire
trop tard.

**La présence de l'automatisation se reconnaît à l'appel de l'action, non au nom
des fichiers.** Un dépôt outillé avant que l'application ne sache le faire a
nommé ses workflows autrement ; chercher les noms qu'elle dépose lui proposerait
d'installer ce qu'il a déjà, puis de le doubler.

**Écrire un workflow demande une permission distincte de celle d'écrire un
fichier**, la plateforme traitant à part ce qui s'exécute avec les droits du
dépôt. Un accès qui écrit partout ailleurs peut être refusé là seul. Le refus
nomme donc cette permission, faute de quoi il se lit comme une panne alors que
le rédacteur peut souvent se l'accorder lui-même.

L'installation écrit directement sur la branche principale, comme l'amorçage :
une automatisation qui attend une relecture ne protège rien pendant qu'elle
attend, et c'est la période où le dépôt est le plus exposé.

### RG-rien-inventer

L'application **n'écrit dans le dépôt aucun contenu que personne n'a saisi.**

Un champ laissé vide le reste. Ce qui manque s'annonce comme manquant — un
commentaire disant ce qu'on attend là — plutôt que d'être comblé par une phrase
composée.

Une phrase inventée est indiscernable d'une phrase choisie : rien ne signale à
qui la lit ensuite que personne ne l'a voulue. Elle est donc prise pour une
intention, et se recopie — la description inventée d'un dépôt réel s'était déjà
propagée dans son fichier d'accueil avant qu'on ne la remarque.

La règle ne vise pas ce que l'application dérive et sait redériver, ni les notes
qui expliquent un répertoire : celles-là ne se donnent jamais pour la parole du
projet.

### RG-amorcage-depot

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
