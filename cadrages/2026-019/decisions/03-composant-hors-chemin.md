---
id: 03-composant-hors-chemin
titre: Le composant doit-il rester sur le chemin des données ?
statut: retenue
option_retenue: appele-a-la-connexion
---

## Description

Le composant détient de quoi obtenir un accès au dépôt. Restait à décider s'il
transmet aussi les requêtes, ou s'il se borne à délivrer l'accès.

C'est la différence entre les deux modes que la gamme distingue, et elle emporte
plus que la mécanique : ce que le mode peut garantir en dépend.

## Options

### relais-de-chaque-requete

Toutes les requêtes passent par lui, et il les vérifie une à une.

**Pour** — permet de refuser un chemin, non seulement un projet. Et l'auteur d'un
enregistrement est alors tenu de l'identité vérifiée, non de ce que l'application
déclare.
**Contre** — sa disponibilité devient celle du produit, et tout le trafic y passe.
La régulation d'appels, qui vit côté client, doit tenir compte du relais.

### appele-a-la-connexion

**Retenue.** Il délivre un accès, puis l'application s'adresse directement à la
plateforme.

**Pour** — une requête par rédacteur et par heure. Rien ne change au quota, à la
latence ni à la régulation. Le composant peut tomber sans interrompre qui est
déjà connecté.
**Contre** — l'autorisation s'arrête au projet, la plateforme ne sachant pas
restreindre plus finement. Et l'auteur d'un enregistrement reste déclaré par
l'application.

## Décision

**Appelé à la connexion, hors du chemin des données.**

C'est ce qui définit ce mode dans la gamme : il lève l'obstacle du compte sans
prendre en charge ce que le relais prendra. Le proposer autrement aurait fait des
deux modes une seule chose, et privé les projets du choix.

Les limites qui en découlent ne sont pas tues — la règle sur les garanties
annoncées l'impose, et l'application les affiche là où le rédacteur se connecte.

Un fait a néanmoins été acquis : **l'auteur d'un enregistrement peut porter le
nom d'une personne sans compte sur la plateforme.** Elle accepte une adresse
qu'elle ne connaît pas, et n'apparaît alors que comme déposant. La traçabilité —
qui est la raison d'être du produit — est donc préservée dans ce mode, même si
elle repose sur ce que l'application déclare plutôt que sur ce qu'un relais
vérifierait.
