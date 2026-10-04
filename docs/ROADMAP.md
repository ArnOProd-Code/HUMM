# Feuille de route

Cette feuille de route présente les besoins identifiés, sans annoncer de dates ni assimiler une intention à une livraison.

## Socle

- ✅ Lecture MPD → ALSA → codec SGTL5000 validée sur HummingBoard i2eX sous Linux / Armbian.
- ✅ Bibliothèque locale sur mSATA ; valeur PCM de référence documentée.

## Interface

- Décisions de conception confirmées : bibliothèque en liste Artistes / Albums / Titres, recherche groupée, sources internes/USB et séparation File/Playlists (voir [DECISIONS.md](DECISIONS.md)).
- ⚪ Implémenter ces parcours, avec la qualité de chaque titre et le nombre de titres visibles.
- ⚪ Définir et réaliser les réglages ainsi que l'interface complète du lecteur.

## Architecture logicielle

- Décision de conception confirmée : intercaler une couche HUMM / API entre l'interface et MPD/le système.
- ⚪ Définir l'API, implémenter le modèle de données et connecter progressivement les vues à MPD.

## Administration

- ⚪ Importer morceaux et dossiers depuis une clé USB vers le mSATA.
- ⚪ Copier, déplacer, renommer, supprimer et créer des dossiers.
- ⚪ Définir la gestion des conflits et les confirmations adaptées.
- ⚪ Mettre à jour la bibliothèque après les changements.
- ⚪ Modifier ou corriger les tags audio.
- ⚪ Préserver playlists et file lors de l'indisponibilité temporaire d'une source ; éviter les interruptions modales.

## Exploitation

- 🟡 Compléter les procédures d'installation, de sauvegarde et de restauration lorsque celles-ci seront définies et validées.

## Plan de conception

Le plan UX/IHM de référence comprend l'expérience, les fonctionnalités, les écrans, la navigation, Now Playing, Bibliothèque, Recherche, Sources, File et playlists, Réglages, modèle de données, API HUMM, prototype, implémentation, connexion à MPD et validations sur matériel. Les points déjà définis servent de base ; les étapes de spécification ou de réalisation non validées restent ouvertes.
