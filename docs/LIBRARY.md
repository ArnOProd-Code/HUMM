# Bibliothèque musicale

## Stockage et affichage

- ✅ La bibliothèque locale est stockée sur le mSATA.
- **Décision de conception confirmée :** parcourir la bibliothèque en listes Artistes / Albums / Titres, sans cartes artistes.
- **Décision de conception confirmée :** afficher la qualité audio par titre (par exemple `FLAC · 24/192`) et le nombre de titres.
- ⚪ La vue correspondante reste à implémenter.

## Modèle conceptuel

La Bibliothèque est une **vue indexée** du contenu musical du mSATA. Les fichiers restent dans leur stockage physique ; l'index relie les fichiers aux morceaux, albums et artistes.

- Un morceau logique peut avoir plusieurs fichiers physiques ; le chemin ne définit pas son identité.
- Chaque fichier appartient à une source (mSATA ou USB) et porte ses propres attributs techniques et son état de disponibilité.
- Les tags titre, artiste et album sont les informations musicales principales. Les autres métadonnées sont complémentaires.
- Une modification de tag doit mettre à jour les regroupements et la recherche sans casser les identifiants internes ou relations HUMM.

Le modèle complet et les règles pour les sources absentes, les playlists et la suppression figurent dans [DECISIONS.md](DECISIONS.md).

## Administration prévue

Les opérations suivantes sont des besoins futurs, pas des fonctions déclarées disponibles :

- ⚪ Copier morceaux et dossiers depuis une clé USB vers la bibliothèque mSATA.
- ⚪ Copier, déplacer, renommer et supprimer des fichiers ; créer des dossiers.
- ⚪ Gérer les conflits lors des opérations sur les fichiers.
- ⚪ Mettre à jour la bibliothèque MPD après les changements.
- ⚪ Modifier et corriger les métadonnées (tags) audio.
- ⚪ Parcourir une USB dans une vue Fichiers et indexer sa vue Musique de façon progressive et non bloquante.

Les règles de conflits, de confirmation de suppression et de mise à jour restent à préciser avant implémentation. La suppression d'un fichier ne doit pas effacer silencieusement les références de playlist. Voir [UX.md](UX.md) et [DECISIONS.md](DECISIONS.md).
