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

## Composants à venir

- ⚪ Interface de contrôle et affichage de la bibliothèque.
- ⚪ Outils d'administration des fichiers et métadonnées.

Les détails d'implémentation de ces composants restent à définir. Cette page ne suppose ni services HUMM supplémentaires ni interface déjà disponible.
