---
id: RG-verification-a-la-saisie
fonctionnalites: [redaction-cadrage, impacts-regles]
statut: actif
cree_par: 2026-016
modifie_par: []
---

L'application signale, **pendant la rédaction**, ce qui empêcherait la livraison
du cadrage, dans les termes exacts de la vérification finale.

Elle emploie pour cela les règles partagées, non une seconde lecture du format :
un contrôle qui dirait autre chose que la vérification serait pire que pas de
contrôle du tout, puisqu'il ferait douter de celui qui fait autorité.

L'application ne dispose que du référentiel courant augmenté du cadrage en cours ;
un cadrage voisin, encore ouvert ailleurs, lui échappe. Certains contrôles y sont
donc moins conclusifs qu'à la livraison.

L'écart ne va jamais que dans un sens : l'application signale moins, jamais plus.
Ce qu'elle affirme est vrai ; ce qu'elle tait peut encore apparaître à la
livraison, où la vérification demeure l'autorité.
