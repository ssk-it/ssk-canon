---
id: RG-verification-a-la-saisie
fonctionnalites: [redaction-cadrage, impacts-regles]
statut: actif
cree_par: 2026-016
modifie_par: [2026-026]
---

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
