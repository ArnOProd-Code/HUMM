# HUMM

**HUMM — High-fidelity Universal Music Machine — Digital audio player**

HUMM est un lecteur audio numérique haute fidélité en cours de construction, basé sur une **HummingBoard i2eX**. Le socle de lecture a été validé sur le matériel réel ; l'interface et les outils d'administration restent à développer.

## État du projet

- ✅ **Lecture audio validée sur matériel réel** : Linux / Armbian, MPD, ALSA et codec SGTL5000.
- ✅ **Bibliothèque locale** stockée sur le mSATA.
- ✅ **Arrêt propre** avec `sudo poweroff` avant de déconnecter l'alimentation.
- 🟡 Le projet est en cours de construction ; la documentation distingue les validations des travaux à venir.
- ⚪ L'interface complète et l'administration de la bibliothèque sont prévues, pas encore implémentées.

## Plateforme

| Élément | Choix |
| --- | --- |
| Carte | HummingBoard i2eX |
| Système | Linux / Armbian |
| Moteur de lecture | MPD |
| Sortie audio | ALSA + codec SGTL5000 |
| Bibliothèque locale | mSATA |
| Volume PCM ALSA de référence | `numid=1` = `180` |

## Documentation

- [Statut du projet](docs/STATUS.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Audio](docs/AUDIO.md)
- [Exploitation](docs/OPERATIONS.md)
- [Bibliothèque](docs/LIBRARY.md)
- [Expérience utilisateur](docs/UX.md)
- [Feuille de route](docs/ROADMAP.md)
- [Sécurité](docs/SECURITY.md)
- [Journal des changements](CHANGELOG.md)

## Statuts

- ✅ vérifié/validé sur matériel réel
- 🟡 en cours
- ⚪ prévu

Le dépôt public ne contient ni fichiers musicaux, ni base de données privée, ni secrets ou données personnelles. Voir [SECURITY.md](docs/SECURITY.md).
