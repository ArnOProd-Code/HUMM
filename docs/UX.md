# Expérience utilisateur

## Bibliothèque

- **Décision de conception confirmée :** liste simple sans cartes artistes, avec navigation Artistes / Albums / Titres.
- **Décision de conception confirmée :** afficher la qualité audio par titre et le nombre de titres ; exemple `FLAC · 24/192`.
- ⚪ L'interface correspondante reste à implémenter.

## Recherche et sources

- **Décision de conception confirmée :** recherche globale en sections Artistes / Albums / Titres, instantanée et tolérante, sans IA générative.
- **Décision de conception confirmée :** le mSATA est la source interne permanente ; chaque USB est une source externe temporaire identifiée séparément.
- **Décision de conception confirmée :** une USB propose les vues Musique et Fichiers. Musique reprend la Bibliothèque ; Fichiers est un explorateur hiérarchique selon la charte HUMM.
- ⚪ L'indexation USB doit démarrer à l'ouverture de Musique sans bloquer l'interface. Les parcours restent à implémenter.

## Lecture et playlists

- **Décision de conception confirmée :** séparer la File temporaire de lecture des playlists persistantes.
- **Décision de conception confirmée :** utiliser les actions communes Lire maintenant, Ajouter à la file et Ajouter à une playlist depuis les différentes vues musicales.
- **Décision de conception confirmée :** accès direct à la File depuis le lecteur ; playlists dans la navigation musicale.
- **Décision de conception confirmée :** privilégier la continuité de lecture ; une source absente rend ses titres indisponibles, sans les supprimer automatiquement ni interrompre la lecture avec une boîte de dialogue.
- ⚪ Ces comportements restent à implémenter. Les règles détaillées sont dans [DECISIONS.md](DECISIONS.md).

## Administration

- ⚪ Prévoir des parcours pour importer et gérer les fichiers, résoudre les conflits, actualiser la bibliothèque et corriger les tags (détails dans [LIBRARY.md](LIBRARY.md)).

Les décisions de conception sont distinguées des validations sur matériel réel. Aucun écran ou parcours non implémenté n'est présenté comme existant. Voir aussi [ARCHITECTURE.md](ARCHITECTURE.md) et [DECISIONS.md](DECISIONS.md).
