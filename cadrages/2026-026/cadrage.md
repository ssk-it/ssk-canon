---
id: 2026-026
titre: Écrire les décisions, sans rien perdre de ce qui était écrit
domaines: [cadrage, persistance]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-preservation-integrale, operation: cree }
  - { regle: RG-decisions-options, operation: modifie }
  - { regle: RG-verification-a-la-saisie, operation: modifie }
  - { regle: RG-format-fichier, operation: touche }
  - { regle: RG-cadrages-en-cours-visibles, operation: touche }
---

## Objectif

Permettre d'écrire une décision depuis l'application.

Le produit savait lire les décisions, les afficher, les mettre en valeur — et
n'a jamais su en produire une. Ce qu'il montrait de plus précieux, les options
écartées et le motif qui a tranché, ne pouvait s'écrire qu'à la main, hors de
l'outil dont c'est la raison d'être.

En l'éprouvant sur un projet réel, un défaut plus grave est apparu :
réenregistrer un cadrage effaçait toute section que l'éditeur ne présente pas.
Un cadrage a perdu vingt-trois lignes de questions ouvertes, sans un mot.

## Parcours utilisateur

1. Quelqu'un ouvre un cadrage et y ajoute une décision : la question posée, ce
   qui la rendait ouverte.
2. Il déclare les options envisagées, et désigne d'un geste celle qui est
   retenue.
3. Il écrit ce qui a tranché, puis enregistre.
4. Ce qu'il n'a pas touché n'est pas réécrit ; ce que l'éditeur ne présente pas
   lui survit.
5. Le cadrage rouvert montre exactement ce qui a été enregistré.

## Énoncés

### RG-preservation-integrale

Réenregistrer une entité **ne perd rien de ce qu'elle portait**, y compris ce
que l'application ne sait pas présenter.

Un cadrage porte ce que son auteur juge utile : des questions ouvertes, un état
de l'art, une note. Reconstruire le fichier à partir des seules parties
reconnues les efface — et l'efface en silence, ce qui est le pire : rien ne
distingue une perte d'une absence, et le travail disparu ne se découvre qu'en
relisant l'historique.

Le contenu inconnu est conservé tel quel, sans être interprété. L'application
n'a pas à comprendre ce qu'elle préserve.

**Réenregistrer sans modification n'écrit rien.** Un enregistrement qui touche
des fichiers que personne n'a changés emplit l'historique de bruit, et rend
illisible ce qui a réellement bougé. Ce qui est écrit est comparé à ce qui avait
été lu.

La perte silencieuse est le seul défaut qu'un outil de mémoire ne peut pas se
permettre : tout le reste se corrige, celui-là détruit ce qu'on lui a confié.

### RG-decisions-options

Une décision porte une description, les **options envisagées**, et l'option
retenue ou l'annulation, chacune pouvant être commentée.

Les options écartées sont conservées avec leur motif. C'est ce qui distingue une
décision d'un simple choix : six mois plus tard, savoir ce qui a été envisagé et
pourquoi ça ne l'a pas emporté vaut souvent plus que la décision elle-même.

**L'application écrit les décisions, elle ne fait pas que les lire.** Un outil
qui montre ce qu'il ne sait pas produire renvoie à la main pour ce qu'il présente
comme essentiel.

Désigner l'option retenue est un geste, non une saisie : le nom recopié à deux
endroits diverge, et une option retenue qui ne correspond à aucune option est
une incohérence que rien n'empêcherait.

Renommer l'option retenue la garde retenue ; la retirer libère le choix. Sans
cela, corriger une faute de frappe déferait la décision sans le dire.

### RG-verification-a-la-saisie

L'application signale, **pendant la rédaction**, ce qui empêcherait la livraison
du cadrage, dans les termes exacts de la vérification finale.

Elle emploie pour cela les règles partagées, non une seconde lecture du format :
un contrôle qui dirait autre chose que la vérification serait pire que pas de
contrôle du tout, puisqu'il ferait douter de celui qui fait autorité.

**Elle vérifie contre le référentiel de la branche où le cadrage vit**, non
contre l'état livré. Un cadrage crée souvent le domaine et les règles qu'il
déclare : les chercher ailleurs les dirait inconnus, alors que la vérification
de la livraison les accepte.

L'écart ne va jamais que dans un sens : l'application signale moins, jamais
plus. Ce qu'elle affirme est vrai ; ce qu'elle tait peut encore apparaître à la
livraison, où la vérification demeure l'autorité. **Un signalement de trop est
un défaut, non une prudence** — il fait douter d'un travail correct, et s'il
bloque l'enregistrement, il arrête le travail au lieu de le protéger.

Un cadrage voisin, encore ouvert ailleurs, échappe toujours à l'application :
certains contrôles y restent moins conclusifs qu'à la livraison.
