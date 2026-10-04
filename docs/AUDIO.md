# Audio

## Chaîne validée

- ✅ MPD assure la lecture sur Linux / Armbian.
- ✅ ALSA et le codec SGTL5000 assurent la sortie audio sur HummingBoard i2eX.
- ✅ Le fonctionnement de la chaîne et la lecture ont été validés sur le matériel réel.
- ✅ Réglage PCM de référence actuel : contrôle ALSA `numid=1` à `180`.

Cette valeur est une référence de configuration du projet, pas une consigne universelle pour d'autres cartes ou sorties.

## Informations dans l'interface

- ⚪ Afficher une indication de qualité audio par titre, par exemple `FLAC · 24/192`.
- ⚪ Afficher le nombre de titres de la bibliothèque.

Ces éléments d'interface sont prévus et ne sont pas déclarés comme implémentés.
