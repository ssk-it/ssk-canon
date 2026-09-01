---
id: 2026-024
titre: Travailler sur plusieurs projets, chacun avec son accès
statut: livree
domaines: [acces, cadrage]
liens:
  - { tag: issue_github, url: 'https://github.com/ssk-it/ssk-canon' }
impacts:
  - { regle: RG-projets-connus, operation: cree }
  - { regle: RG-acces-par-portee, operation: cree }
  - { regle: RG-modes-acces, operation: modifie }
  - { regle: RG-message-nomme-la-cause, operation: touche }
  - { regle: RG-chargement-hors-quota, operation: touche }
---

## Objectif

Permettre de travailler sur plusieurs projets sans repartir de zéro à chaque
fois.

L'application ne retenait qu'un dépôt et un accès. Passer d'un projet à l'autre
demandait de retaper le dépôt, et surtout : saisir un accès pour le second
écrasait celui du premier, sans un mot. Le projet qui fonctionnait la veille
s'annonçait alors introuvable.

Un rédacteur ne travaille pas sur un projet mais sur plusieurs, appartenant
souvent à des organisations différentes. C'est le cas ordinaire, et l'outil le
traitait comme l'exception.

## Parcours utilisateur

1. Quelqu'un ouvre le choix de projet et retrouve ceux sur lesquels il travaille.
2. L'application y ajoute ceux que ses accès autorisent, en distinguant ceux qui
   portent un référentiel de ceux qui n'en portent pas.
3. Il choisit un projet ; l'application présente l'accès qui lui correspond.
4. Au moment de renseigner un accès, il voit ce que celui-ci ouvre — et si le
   projet courant en fait partie — avant de l'enregistrer.
5. Renseigner un accès pour une organisation ne touche pas à celui d'une autre.

## Énoncés

### RG-projets-connus

L'application **retient les projets déjà ouverts**, et propose ceux que l'accès
courant autorise.

Deux origines qui ne se remplacent pas. La mémoire garde les projets sur
lesquels on travaille, y compris sans accès ; la découverte dit ce que l'accès
autorise réellement, ce qu'aucune mémoire ne peut savoir — un projet privé sans
l'accès qu'il faut s'annonçait « introuvable ».

**Un projet n'est retenu qu'une fois ouvert avec succès.** Retenir ce qu'on a
seulement demandé remplirait la liste de projets qu'on n'a jamais pu lire.

Les projets qui portent un référentiel sont proposés en premier, **vérifié et
non supposé** : le nom d'un dépôt ne dit pas s'il porte un référentiel ou du
code. Les autres restent proposés — un dépôt vide qu'on veut amorcer n'a pas
encore de référentiel.

La découverte interroge **tous les accès connus**, non le seul accès courant :
celui-ci ne couvre que le projet ouvert, et s'y limiter masquerait justement les
projets qu'on cherche en voulant changer.

### RG-acces-par-portee

Un accès s'applique à une **portée** — une organisation, ou un projet
particulier — et l'application présente celui qui correspond au projet ouvert.

N'en retenir qu'un revenait à écraser le précédent en silence, puis à présenter
un projet parfaitement lisible comme introuvable. La cause en était invisible :
rien ne disait que l'accès avait changé.

**Deux niveaux, parce que la plateforme en emploie deux.** L'organisation est
l'échelle où se décident l'approbation et les politiques : c'est le cas courant.
Un projet peut néanmoins demander le sien — un accès en écriture là où le reste
de l'organisation est en lecture. Le plus précis l'emporte, faute de quoi
accorder un accès particulier à un projet obligerait à le redéclarer pour tous
les autres.

**Ce qu'un accès ouvre se vérifie avant de l'enregistrer**, et l'application dit
si le projet courant en fait partie. Un accès restreint à une sélection de
projets est autrement refusé sans motif lisible, et la cause se cherche ailleurs.

### RG-modes-acces

Un projet **déclare son mode d'accès** dans sa configuration, et l'application
s'y conforme.

Trois modes, qui ne se substituent pas mais s'empilent : chacun lève un obstacle
que le précédent laissait, sans annuler ce qu'il apportait.

- **Jeton personnel** — chacun apporte le sien. Rien à héberger, et c'est le mode
  par défaut : un projet qui ne déclare rien fonctionne. Il suppose que chaque
  rédacteur ait un compte sur la plateforme de dépôt.
- **Identité tierce** — le rédacteur se connecte avec un compte indépendant de la
  plateforme de dépôt, et un composant échange cette identité contre un accès
  temporaire. Le client n'a plus rien à créer ni à comprendre. Ce composant n'est
  pas sur le chemin des données : il est appelé à la connexion, puis l'application
  s'adresse directement à la plateforme.
- **Relais** — chaque requête passe par un composant qui la vérifie avant de la
  transmettre.

Le mode est déclaré par projet, et un rédacteur travaille sur plusieurs projets :
**l'accès du mode « jeton personnel » se choisit donc selon le projet ouvert**,
et non globalement. Voir `RG-acces-par-portee`.
