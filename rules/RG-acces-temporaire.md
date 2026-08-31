---
id: RG-acces-temporaire
fonctionnalites: [authentification, autorisation]
statut: actif
cree_par: 2026-019
modifie_par: []
---

L'accès obtenu contre une identité vérifiée est **temporaire**, et l'application
ne le conserve pas au-delà de la session.

Sa durée est fixée par la plateforme et ne se raccourcit pas. Le garder d'une
session à l'autre le ferait retrouver expiré, et le présenter alors produirait un
refus dont la cause serait invisible au rédacteur — le perdre en rechargeant est
le comportement juste, une nouvelle identité vérifiée en rendant aussitôt un
autre.

Un accès expiré n'est jamais présenté : l'application l'oublie plutôt que de le
laisser échouer.

L'accès prime sur un jeton personnel qui existerait par ailleurs : quelqu'un qui
vient de s'identifier attend d'écrire sous cette identité, non sous un jeton
saisi la veille.
