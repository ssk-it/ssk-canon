---
id: 03-depot-proxy-ecarte
titre: Un dépôt supplémentaire peut-il tenir lieu de relais ?
statut: retenue
option_retenue: non-mais-utile-ailleurs
---

## Description

L'automatisation de la plateforme offre du calcul et un magasin de secrets, sans
machine à administrer. Le produit s'en sert déjà pour la propagation.

L'idée était séduisante : un dépôt supplémentaire, éventuellement hors de
l'organisation du dépôt cadré, dont les traitements détiendraient les droits. Le
relais existerait sans serveur.

## Options

### relais-par-automatisation

Faire déclencher un traitement par l'application à chaque opération.

**Pour** — aucun serveur à héberger ; le secret vit dans le magasin de la
plateforme, jamais servi au navigateur.
**Contre** — deux faits mesurés l'écartent. **Déclencher un traitement exige une
authentification** : l'application devrait porter un accès permettant de le faire,
donc lisible par l'utilisateur, qui pourrait alors déclencher directement — le
contrôle serait contourné exactement comme si le secret était chez lui. Et **un
traitement coûte dix à quinze secondes**, contre quelques centaines de
millisecondes en direct : chaque chargement, chaque enregistrement y passerait.

### non-mais-utile-ailleurs

**Retenue.** L'automatisation ne convient pas comme relais, mais reste le bon
outil pour ce qui est déjà différé.

**Pour** — la propagation, la vérification et la collecte s'y prêtent
naturellement : leur latence est sans conséquence, et rien n'y est déclenché par
un utilisateur.
**Contre** — la question du relais reste entière.

## Décision

**Non comme relais, oui pour ce qui est déjà différé.**

Le critère qui tranche : **un mécanisme d'automatisation sert ce qui n'attend
personne.** La propagation s'exécute après une livraison, sans que quiconque
regarde ; une écriture de cadrage se fait sous les yeux du rédacteur.

Le second motif est plus profond que la latence. Un traitement qu'un utilisateur
peut déclencher lui-même n'est pas une frontière de sécurité : il faut un accès
pour le déclencher, et cet accès est aussi contournable que le secret qu'on
cherchait à cacher. **Déplacer un secret ne suffit pas ; ce qui compte est qui
peut atteindre ce qu'il protège.**
