---
id: RG-installation-automatisation
fonctionnalites: [impacts-regles, stockage-git]
statut: actif
cree_par: 2026-021
modifie_par: []
---

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
