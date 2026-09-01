---
id: '02'
titre: Que faire des teintes illisibles
statut: retenue
---

## Description

Réparties sur la roue entière, certaines teintes tombent dans les jaunes
verdâtres, qui rendent un olive terne à la clarté utile sur fond clair. Un
domaine y perdait visiblement en lisibilité face à ses voisins.

## Options

### Réduire l'amplitude de la roue — écartée à l'écran

Couvrir 320 degrés au lieu de 360, pour « éviter » la zone.

**Écartée parce que c'est un raisonnement faux, et que seule la vérification
visuelle l'a montré.** Réduire l'amplitude ne supprime pas la zone : elle
déplace seulement l'endroit où la répartition tombe. Un domaine y atterrissait
toujours, et le calcul semblait pourtant juste.

### Corriger la clarté teinte par teinte — écartée

Rattraper les teintes ternes en les éclaircissant individuellement.

Écartée : cela revient à tenir une table de corrections à la main, que chaque
changement de palette invalide.

### Sauter franchement la bande — retenue

La répartition se fait sur la roue amputée de la bande illisible, puis la teinte
est replacée. Les couleurs restent également espacées, et aucune ne tombe dans
la zone.

## Option retenue

Sauter la bande.

Le domaine qui rendait un olive terne est passé à un teal franc, vérifié à
l'écran dans les deux thèmes. Un contrôle automatisé couvre désormais l'absence
de teinte dans la bande, jusqu'à quarante domaines.

**Enseignement** : le calcul paraissait juste et le contrôle passait ; c'est la
capture d'écran qui a montré le défaut. Une propriété visuelle ne s'établit pas
en raisonnant sur le code qui la produit.
