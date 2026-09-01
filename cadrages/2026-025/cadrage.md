---
id: 2026-025
titre: Voir les cadrages en cours, quel que soit le nom de leur branche
domaines: [cadrage, persistance]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-branche-par-cadrage, operation: modifie }
  - { regle: RG-cadrages-en-cours-visibles, operation: cree }
  - { regle: RG-outillage-redaction, operation: touche }
  - { regle: RG-statuts-cadrage, operation: touche }
---

## Objectif

Montrer les cadrages sur lesquels on travaille.

L'application ne lisait que la branche principale. Or un cadrage en brouillon ou
en relecture n'y est jamais : il y arrive à sa livraison. L'outil affichait donc
les statuts « brouillon » et « en relecture », proposait les transitions
correspondantes, et ne pouvait montrer aucun cadrage qui les portait.

Un outil de cadrage qui ne montre pas les cadrages en cours ne tient pas sa
promesse : ce sont précisément ceux dont on discute.

## Parcours utilisateur

1. Quelqu'un rédige un cadrage sur une branche et ouvre sa demande de fusion,
   depuis l'application ou à la main.
2. Il ouvre la liste des cadrages et l'y trouve, avec son objectif, ses impacts
   et ses décisions.
3. Le cadrage porte la marque de sa demande de fusion : rien ne le fait passer
   pour livré.
4. À la livraison, la marque disparaît — le cadrage a rejoint le référentiel.

## Énoncés

### RG-cadrages-en-cours-visibles

Les cadrages **non livrés sont visibles**, avec ceux du référentiel.

Ils vivent sur la branche de leur demande de fusion, jamais sur la branche
principale : ne lire que celle-ci revient à ne montrer que les cadrages
terminés, c'est-à-dire pas ceux sur lesquels on travaille.

**Ils se trouvent par les demandes de fusion ouvertes, non par le nom de leur
branche.** Un nom est une convention que celui qui l'écrit peut ignorer ; une
demande de fusion est un fait. Chercher un nom fait dépendre la visibilité d'un
cadrage d'une convention que rien n'impose au moment de la rédaction.

**Chacun porte la marque de sa demande de fusion**, faute de quoi il passerait
pour appartenir déjà au référentiel — l'inverse de ce que le cycle de statut
établit.

La branche principale fait foi : un cadrage qu'elle porte est livré, et sa
version de branche n'apporte rien. Une branche illisible n'emporte ni les
autres ni le référentiel, qui reste consultable.

### RG-branche-par-cadrage

Chaque cadrage est rédigé sur sa **propre branche**, et livré par le merge de sa
demande de fusion.

Deux cadrages simultanés n'entrent donc jamais en conflit. Deux personnes
éditant le même cadrage produisent en revanche un conflit Git, que l'application
doit présenter intelligemment.

**Le nom de la branche n'emporte aucune conséquence.** L'application en propose
un lorsqu'elle crée la branche, mais ne s'y fie jamais pour retrouver un
cadrage : c'est la demande de fusion qui l'y rattache.

Faire dépendre quoi que ce soit du nom d'une branche rend l'outil aveugle à tout
cadrage rédigé autrement — et le nommage est le premier endroit où deux
conventions divergent, l'une portée par l'application, l'autre par ce qu'on
enseigne au rédacteur. C'est arrivé, et le cadrage écrit à la main était absent
de la liste tout en étant parfaitement formé.
