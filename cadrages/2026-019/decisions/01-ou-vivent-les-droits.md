---
id: 01-ou-vivent-les-droits
titre: Où déclarer les projets qu'une identité peut atteindre ?
statut: retenue
option_retenue: dans-l-identite
---

## Description

Le composant qui échange une identité contre un accès doit savoir quels projets
cette identité ouvre. La question n'est pas de savoir s'il décide — il reste le
seul endroit où l'autorisation s'applique — mais d'où il tient l'information.

Deux endroits s'offraient, et ils ne se valent pas à l'usage.

## Options

### une-table-dans-le-composant

Le composant connaît, par sa configuration, quels projets chaque rôle ouvre.

**Pour** — le composant ne fait confiance qu'à sa propre configuration. Un
émetteur mal réglé ne peut pas ouvrir un projet qu'il n'admet pas.
**Contre** — deux endroits à tenir d'accord : les comptes chez l'émetteur, les
droits dans le composant. Et changer ce qu'un rédacteur atteint demande de
redéployer, pour une information qui n'est pas du code.

### dans-l-identite

**Retenue.** L'identité vérifiée porte elle-même les projets qu'elle ouvre.

**Pour** — les droits se gèrent là où se gèrent les comptes, par ceux qui les
gèrent déjà. Aucun redéploiement pour ouvrir un projet à quelqu'un.
**Contre** — le composant fait confiance à ce que l'émetteur affirme. Un émetteur
compromis ou mal réglé étend la portée de ce qu'il délivre.

## Décision

**Les droits vivent dans l'identité.**

Le contre est réel mais sans portée pratique : le composant fait déjà confiance à
cet émetteur pour dire qui est qui. Lui refuser de dire à quoi cette personne a
droit reviendrait à n'accepter qu'une moitié de ce qu'il affirme, sans que la
seconde soit plus vérifiable que la première.

Ce qui tranche est l'usage : **une information qui change souvent doit vivre là
où on la change**. Les comptes bougent — quelqu'un arrive, quelqu'un part, un
projet s'ouvre — et faire dépendre ces mouvements d'un redéploiement les
rendrait pénibles au point d'être différés.

Ce que le composant retient reste borné : ce qui n'est pas un nom de projet
recevable est écarté, plutôt que transmis à la plateforme qui le refuserait plus
loin et plus mal.
