# T4SYSTEMS — Webhook Sender

Application web 100 % front-end pour créer, prévisualiser et envoyer des webhooks Discord riches (embeds, fichiers, mentions, threads) sans backend ni données stockées ailleurs que dans votre navigateur.

## Points forts
- Multi-embeds (jusqu’à 10) avec onglets + champs personnalisés dynamiques (jusqu’à 25 champs, inline au choix).
- Aperçu temps réel : Markdown rendu par Marked 16.2.1, nettoyé par DOMPurify 3.3.3 pour éviter le XSS.
- Options complètes du webhook : override username/avatar, TTS, suppression d’aperçus, allowed_mentions fines (users/roles IDs, everyone/here), envoi dans un thread (thread_id).
- Pièces jointes multiples (fichiers) et images locales référencées dans les embeds.
- Historique local (10 derniers envois), templates sauvegardés, import/export JSON complet.
- Mode clair/sombre, design modernisé (Space Grotesk, fonds animés, glass + néomorphism léger).
- 100 % client-side : tout est dans `localStorage`, aucun serveur tiers.

## Démarrage rapide
1) Clone ou zip :  
```bash
git clone https://github.com/votre_profil/t4systems-webhook.git
```
2) Ouvre le dossier `T4SYSTEMS-Webhook-Discord`.
3) Double-clique `index.html` dans un navigateur récent (Chrome, Firefox, Edge, Safari).

## Workflow conseillé
1. Page **Configuration** (`pages/config.html`) : ajoute tes webhooks (URL validées), exporte/importe un JSON si besoin.  
2. Page **Messages & Embeds** (`pages/message.html`) :
   - Choisis un webhook, éventuellement un thread ID.
   - Renseigne username/avatar/TTS/flags, allowed_mentions (IDs ou parse).
   - Édite le message texte + un ou plusieurs embeds (titre, URL, description, images, footer, author, champs dynamiques, timestamp).
   - Ajoute des pièces jointes si nécessaire, puis envoie.
   - Sauvegarde comme template ou recharge un historique récent.

## Fichiers clés
- `index.html` : hub d’accueil.
- `pages/config.html` : gestion des webhooks, import/export.
- `pages/message.html` : éditeur complet (embeds, options avancées, fichiers, mentions).
- `assets/styles/shared.css` : thème clair/sombre, layout, animations.
- `assets/images/` : logos.

## Sécurité & limites Discord
- Les URLs de webhook donnent le droit de poster : garde-les privées, ne publie pas le site en ligne avec des webhooks hardcodés.
- Limites Discord respectées : 2000 chars (content), 4096 (description), 256 (titre), 25 champs par embed, 1024 par valeur de champ.
- Aperçu sécurisé : Marked épinglé en 16.2.1 + DOMPurify 3.3.3 pour filtrer le HTML issu du markdown.

## Personnalisation rapide
- Couleurs/typo : variables CSS dans `assets/styles/shared.css` (`:root` et `html[data-theme="dark"]`).
- Logos : remplace `assets/images/logo-dark.png` / `logo-light.png`.
- Comportement embeds : le JS est centralisé dans `pages/message.html` (fonctions `updatePreview`, `sendBtn`).

## Historique des versions (récent)
- 2.0.x : multi-embeds, toasts, historique local.
- 2.1.x : options avancées webhook (mentions fines, TTS, flags, thread_id), pièces jointes multiples, champs custom dynamiques, aperçus sécurisés avec libs épinglées, refonte visuelle.
