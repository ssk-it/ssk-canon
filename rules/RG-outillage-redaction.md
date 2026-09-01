---
id: RG-outillage-redaction
fonctionnalites: [redaction-cadrage, impacts-regles]
statut: actif
cree_par: 2026-022
modifie_par: [2026-023]
---

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

**Ce qui sert à le maintenir est distribué avec lui.** Un outil de maintenance
gardé à part de ce qu'il maintient est le premier à diverger, n'étant employé
qu'au moment où l'on constate déjà un problème.
