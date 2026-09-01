---
id: 2026-029
titre: Adresser un projet par son URL
domaines: [persistance, cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon-pwa' }
impacts:
  - { regle: RG-projet-dans-adresse, operation: cree }
  - { regle: RG-choix-projet-prealable, operation: cree }
  - { regle: RG-depot-choisi-memorise, operation: modifie }
  - { regle: RG-chargement-hors-quota, operation: touche }
---

## Objectif

Permettre de désigner un projet, et une vue de ce projet, par une adresse — de
sorte qu'elle puisse être envoyée à quelqu'un.

Le produit sert à partager une spécification entre un client et une équipe. Le
partage se fait par un lien : « regarde cette règle », « voici où on en est de ce
cadrage ». Tant que l'adresse ne porte que la vue — `/referentiel/regle/RG-x` —
elle ne dit pas de quel projet il s'agit. Celui qui la reçoit voit la règle
homonyme de *son* dernier projet ouvert, ou une page vide. Le lien ment sans
prévenir, ce qui est pire que de ne pas pouvoir en envoyer.

La cause est que le projet ouvert vivait dans le navigateur, et nulle part
ailleurs. Un état local ne peut pas voyager.

Une seconde gêne, moins visible, tenait à la même cause : rien ne distinguait
« aucun projet choisi » de « le projet mémorisé la dernière fois ». L'application
ouvrait d'office le dernier dépôt, y compris quand on venait pour en ouvrir un
autre.

## Parcours utilisateur

1. Quelqu'un ouvre l'application sans rien préciser. Elle ne charge aucun
   projet : elle demande lequel, et propose ceux qu'il a déjà ouverts ainsi que
   ceux auxquels son accès donne droit.
2. Il en choisit un. L'adresse porte désormais l'organisation et le dépôt, et le
   référentiel se charge.
3. Il navigue — un domaine, une règle, un cadrage. L'adresse garde le projet à
   chaque étape, et rien n'est rechargé tant que le projet ne change pas.
4. Il envoie l'adresse d'une règle à un collègue. Celui-ci l'ouvre et voit la
   même règle, du même projet, quel que soit ce que son navigateur avait
   mémorisé.
5. Il change de projet depuis la barre alors qu'il consultait les cadrages : il
   arrive sur les cadrages de l'autre projet, non sur son accueil.
6. Il ouvre une adresse qui ne désigne aucun projet : elle le ramène au choix,
   plutôt que d'ouvrir un dépôt que personne n'a demandé.

## Énoncés

### RG-projet-dans-adresse

**Toute vue d'un projet est adressée par `/<organisation>/<depot>/<vue>`.**
L'adresse fait autorité sur le projet ouvert ; la mémoire du navigateur ne sert
qu'à proposer, jamais à décider.

C'est ce qui rend un lien partageable : celui qui le reçoit voit le même projet
que celui qui l'a envoyé. Un état gardé dans le navigateur ne voyage pas, et une
adresse qui dépend de lui affiche chez l'un autre chose que chez l'autre — sans
que ni l'un ni l'autre ne puisse s'en apercevoir.

Il s'ensuit que **tout lien interne porte le projet ouvert**. Un lien écrit sans
lui sortirait du projet courant sans le signaler.

Changer de projet **conserve la vue** : passer d'un projet à l'autre en
consultant les cadrages mène aux cadrages de l'autre projet. Une vue de détail
retombe en revanche sur sa liste, un identifiant de cadrage ou de règle n'ayant
aucune raison d'exister ailleurs — mener à une page vide serait pire que ne rien
promettre.

Une adresse qui ne désigne aucun projet ramène au choix. Elle ne peut pas en
deviner un, et en ouvrir un au hasard ferait passer pour consulté un projet que
personne n'a demandé.

### RG-choix-projet-prealable

**Aucun projet n'est ouvert d'office.** L'application demande lequel avant de
charger quoi que ce soit.

Le référentiel d'un projet ne veut rien dire hors de son projet : afficher des
domaines sans dire desquels il s'agit invite à les lire comme ceux qu'on
cherchait. Le choix propose les projets déjà ouverts et ceux que l'accès courant
autorise — les deux, car la mémoire garde ce sur quoi on travaille y compris
sans connexion, quand la découverte, elle, dit ce qui est réellement accessible.

Les vues d'un projet — ses onglets, son rechargement, ses réglages — ne sont pas
proposées tant qu'aucun projet n'est ouvert : elles n'auraient rien à désigner.

### RG-depot-choisi-memorise

Le dépôt de projet est **désigné par l'adresse**, et **mémorisé** par le
navigateur pour être reproposé au choix suivant.

La saisie accepte un nom court `organisation/depot` comme une URL complète.

Une seule instance de l'application dessert ainsi plusieurs projets, et le
changement de dépôt ne demande aucun redéploiement. La mémoire épargne de
ressaisir un dépôt sur lequel on revient ; elle ne détermine plus ce qui
s'affiche, l'adresse en ayant désormais la charge — voir
`RG-projet-dans-adresse`.
