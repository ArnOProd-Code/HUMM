# Architecture

## Plateforme validée

```text
HummingBoard i2eX
└── Linux / Armbian
    ├── MPD ── ALSA ── codec SGTL5000 ── sortie audio
    └── Bibliothèque musicale locale sur mSATA
```

- ✅ Le fonctionnement MPD/ALSA/SGTL5000 et la lecture audio ont été validés sur le matériel réel.
- ✅ La bibliothèque locale réside sur le mSATA.
- ✅ La référence actuelle du volume PCM ALSA est `numid=1` = `180`.

## Architecture cible

```text
Interface HUMM
      ↓
Couche HUMM / API
      ├── MPD et commandes de lecture
      ├── système Linux et périphériques USB
      ├── index de bibliothèque
      └── opérations de gestion des fichiers
```

La couche HUMM doit isoler l'interface des commandes directes `mpc` et shell. Cette séparation est une décision d'architecture ; l'API complète et son implémentation restent à réaliser.

## Modèle musical

```text
Source (mSATA ou USB)
  └── Fichier physique (chemin, qualité, disponibilité)
       └── Morceau logique (titre, artiste(s), album)

Playlist persistante ──> entrées référençant des fichiers physiques
Session de lecture ────> file temporaire ordonnée
```

La Bibliothèque est la vue indexée du contenu mSATA. Elle ne duplique pas les fichiers. Les détails et règles de cohérence figurent dans [DECISIONS.md](DECISIONS.md).

## Composants à réaliser

- ⚪ Interface de contrôle et affichage de la bibliothèque.
- ⚪ Couche HUMM / API entre l'interface et MPD/le système.
- ⚪ Recherche, indexation des sources et modèle de données applicatif.
- ⚪ Outils d'administration des fichiers et métadonnées.

Ces composants sont des objectifs, pas des fonctions annoncées comme disponibles. Voir [UX.md](UX.md), [LIBRARY.md](LIBRARY.md) et [ROADMAP.md](ROADMAP.md).
