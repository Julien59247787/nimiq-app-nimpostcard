# NIM Postcard — Nimiq Mini Apps Competition (Cycle II)

## Concept
Une carte postale numérique : un message court, un décor, une signature native du wallet
(`sign()`), et un petit cadeau NIM strictement optionnel envoyé directement au moment de l'envoi.
Pas de cagnotte, pas de custody — le cadeau part du wallet de l'expéditeur avec sa confirmation.

Pourquoi ce concept : c'est la mini app la plus simple et la plus "shareable" de la famille NIM —
un cas d'usage social léger (dire merci, féliciter, penser à quelqu'un) qui ne demande aucune
compréhension crypto pour être compris, et qui montre la signature native Nimiq Pay sans qu'une
transaction soit obligatoire.

## Ce qui est déjà construit
- `index.html` — page marketing + démo interactive complète (single file, vanilla JS, aucune
  dépendance backend), même famille visuelle que NIM Drop (Fraunces + Sora), palette différenciée
  (teal/parchemin plutôt que garnet/or) pour se distinguer tout en restant cohérente.
- Composeur de carte : message, choix de décor, cadeau NIM optionnel (désactivé par défaut).
- Simulation de réception (onglet "Reçues") avec cartes entrantes aléatoires, certaines avec cadeau.
- Détection progressive du vrai environnement Nimiq Pay (`window.nimiqPay`), mêmes appels SDK que
  NIM Drop (`init()`, `sign()`, `sendBasicTransactionWithData()`).
- FAQ "Qui paie quoi ?" intégrée dès la première version (retour d'expérience direct de NIM Drop,
  où cette question a été posée après coup).

## Ce qui manque pour une vraie soumission
1. Génération d'un lien/QR réel par carte (actuellement pas de partage effectif, juste la démo).
2. Persistance des cartes envoyées/reçues (actuellement tout est en mémoire, perdu au rechargement).
3. Hébergement public HTTPS (prévu : sur l'infra des validateurs, comme NIM Drop — pas de
   dépendance au cloud Claude).
4. Test réel dans Nimiq Pay via "Load a local Mini App".

## Stack
Identique à NIM Drop : HTML/CSS/JS vanilla, Fraunces + Sora (+ Special Elite pour le cachet postal),
`@nimiq/mini-app-sdk` chargé dynamiquement depuis jsDelivr uniquement si `window.nimiqPay` est
détecté. Aucune donnée personnelle ni clé privée gérée côté app.
