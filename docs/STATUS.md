# Statut du projet

HUMM est un projet en cours de construction. Le chemin de lecture audio est opérationnel et validé sur la plateforme réelle ; l'expérience produit et l'administration de la bibliothèque restent à réaliser.

## Validé

- ✅ Carte HummingBoard i2eX avec Linux / Armbian.
- ✅ Lecture MPD vers ALSA et codec SGTL5000, validée sur matériel réel.
- ✅ Bibliothèque musicale locale stockée sur le mSATA.
- ✅ Volume PCM ALSA de référence : `numid=1` = `180`.
- ✅ Arrêt propre : `sudo poweroff` avant déconnexion de l'alimentation.
- ✅ USB validées sur le matériel : deux ports, montage à la demande, intégration MPD, retrait/réinsertion et lecture après remontage.
- Décision de conception confirmée : Bibliothèque en liste, sans cartes artistes, avec navigation Artistes / Albums / Titres.
- Décision de conception confirmée : rendre visibles la qualité audio et le nombre de titres.

## En cours

- 🟡 Construction du projet HUMM autour du socle matériel et audio validé.

## Prévu

- ⚪ Interface complète et commandes de lecture accessibles depuis l'interface.
- ⚪ Recherche HUMM, vues USB Musique/Fichiers, file de lecture, playlists et couche HUMM/API.
- ⚪ Administration des fichiers, mise à jour de la bibliothèque et correction des tags.

Les décisions UX confirmées ne signifient pas que les écrans ou parcours sont déjà implémentés. Voir [DECISIONS.md](DECISIONS.md) pour la référence regroupée et [ROADMAP.md](ROADMAP.md) pour les étapes restantes.
