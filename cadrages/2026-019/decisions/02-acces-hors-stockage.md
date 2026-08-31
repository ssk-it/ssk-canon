---
id: 02-acces-hors-stockage
titre: L'accès temporaire doit-il survivre à la session ?
statut: retenue
option_retenue: non-conserve
---

## Description

L'accès obtenu contre une identité vérifiée expire au bout d'une heure, et cette
durée est fixée par la plateforme — elle ne se raccourcit ni ne s'allonge.

Un jeton personnel, lui, est conservé par le navigateur : le rédacteur le saisit
une fois et le retrouve. La question était de savoir si l'accès temporaire devait
suivre le même chemin.

## Options

### conserve-comme-un-jeton

Garder l'accès dans le stockage du navigateur, comme le jeton personnel.

**Pour** — le rédacteur retrouve sa session en rechargeant, sans repasser par
l'émetteur.
**Contre** — il le retrouverait aussi le lendemain, expiré. La première écriture
échouerait alors sur un refus d'autorisation dont la cause serait invisible : ni
le rédacteur ni l'application ne verraient que le problème est l'âge de l'accès.

### non-conserve

**Retenue.** L'accès vit le temps de la session, et se perd en rechargeant.

**Pour** — ce qui est là est valide. Une nouvelle identité vérifiée en rend
aussitôt un autre, et le passage par l'émetteur est bref pour qui y est déjà
connu.
**Contre** — un rechargement oblige à se reconnecter.

## Décision

**Ne pas le conserver.**

Le principe : **ce qui expire ne doit pas être retrouvé.** Un accès périmé qu'on
présente produit une erreur qui parle d'autorisation, jamais d'expiration — et le
rédacteur cherche alors du côté de ses droits un problème qui est celui du temps.

La même logique gouverne l'usage : un accès expiré n'est pas présenté du tout.
L'application l'oublie et se déclare déconnectée, ce qui est vrai, plutôt que de
tenter un appel dont elle connaît l'issue.

L'accès prime enfin sur un jeton personnel qui existerait par ailleurs. Quelqu'un
qui vient de s'identifier attend d'écrire sous cette identité — écrire sous un
jeton saisi la veille produirait des enregistrements signés de quelqu'un d'autre.
