# Décisions de référence HUMM

Cette page consolide les décisions du projet « Lecteur audio hi-fi », en particulier le plan UX/IHM et ses points consacrés à la recherche, aux sources, aux playlists et au modèle de données. Elle sert de référence transversale ; elle ne décrit pas des fonctions comme déjà implémentées.

## Statuts

- ✅ vérifié/validé sur matériel réel
- 🟡 en cours
- ⚪ prévu

Les choix d'interface ci-dessous sont des **décisions de conception confirmées**. Ils ne portent pas le statut ✅, réservé aux validations sur le matériel réel.

## Architecture et méthode

- La chaîne actuellement validée est HummingBoard i2eX, Linux / Armbian, MPD, ALSA et codec SGTL5000.
- La cible logicielle sépare l'interface de la logique du produit : **IHM → couche HUMM / API → MPD et système**.
- L'IHM ne doit pas dépendre directement de commandes shell ou de commandes MPD. La couche HUMM doit abstraire MPD, le système, les sources USB et les opérations de fichiers.
- La conception progresse par décisions explicites ; l'implémentation et les validations matérielles restent des étapes distinctes.

## Principes d'expérience

Les choix d'expérience confirmés sont : simplicité, rapidité, lisibilité, priorité à la musique et esthétique sombre, épurée, premium et hi-fi. La direction visuelle définie utilise un fond charbon/noir, des accents jaune-vert lumineux et une touche rétro-futuriste.

### Bibliothèque et recherche

- Bibliothèque : présentation en liste, sans cartes artistes, avec navigation logique **Artistes / Albums / Titres**.
- Rendre visibles la qualité audio d'un titre et le nombre de titres ; exemple de qualité : `FLAC · 24/192`.
- Recherche globale organisée en sections Artistes, Albums et Titres ; résultats instantanés et tolérants aux erreurs, avec une recherche algorithmique, sans IA générative.

### Sources

- Le mSATA est le stockage interne permanent de la Bibliothèque.
- Une clé USB est une source externe temporaire, identifiée séparément des autres clés.
- Chaque USB expose deux vues : **Musique**, qui reprend l'expérience de la Bibliothèque, et **Fichiers**, un navigateur hiérarchique habillé selon HUMM.
- Les opérations de gestion des fichiers restent dans Administration.
- L'indexation musicale d'une USB démarre à l'ouverture de sa vue Musique et doit rester progressive et non bloquante. Le retrait d'une source doit être géré proprement.

### File de lecture et playlists

- **File** : session de lecture temporaire, ordonnée et modifiable. **Playlist** : sélection persistante, indépendante de la session.
- Depuis Bibliothèque, Recherche, USB → Musique et une playlist, garder les mêmes actions : **Lire maintenant**, **Ajouter à la file**, **Ajouter à une playlist**.
- Lire maintenant construit/remplace la file et démarre la lecture. Ajouter à la file ajoute à la suite sans interrompre la lecture. Ajouter à une playlist ne change pas la file et ne démarre pas la lecture.
- La file présente le morceau en cours et les suivants ; elle peut être réordonnée, modifiée ou vidée. Vider la file ne supprime pas le morceau déjà en cours. Les doublons sont autorisés.
- Shuffle et répétition sont des modes de la session de lecture, pas des propriétés de playlist. En mode shuffle, l'ordre affiché dans la file reste inchangé.
- Les playlists sont ordonnées, renommables et modifiables ; la première version n'a pas de dossiers. Elles peuvent référencer des morceaux de la Bibliothèque ou d'une USB et affichent au minimum nom, nombre de titres et durée totale.
- Une entrée indisponible reste dans la playlist. Si elle arrive dans la file, HUMM la saute sans dialogue bloquant afin de préserver la continuité de lecture. Le retour de la même source peut rendre l'entrée à nouveau disponible.
- Supprimer une playlist demande confirmation, mais ne supprime jamais de fichier audio. Retirer un titre d'une playlist n'agit que sur cette sélection.
- La File est accessible depuis le lecteur ; les Playlists sont dans l'espace musical, pas dans Administration.

### Modèle de données conceptuel

- Distinguer le **morceau logique**, son ou ses **fichiers physiques** et leur **source**. Un morceau peut avoir plusieurs occurrences physiques ; son identité ne dépend pas du chemin.
- Titre, artiste et album sont les métadonnées musicales principales. Artistes et albums sont des entités distinctes ; plusieurs artistes peuvent contribuer à un morceau ou à un album. Un album contient des titres ordonnés et peut être multi-disque. Un morceau sans album connu reste possible.
- Format, fréquence, profondeur, débit, durée, taille et canaux décrivent le fichier physique. La qualité affichée est une synthèse de ces propriétés.
- La Bibliothèque est une vue indexée du contenu du mSATA, pas une seconde copie des fichiers.
- Les playlists référencent des fichiers physiques précis et conservent les informations nécessaires à l'affichage en cas d'indisponibilité. La File contient des entrées temporaires ordonnées.
- La disponibilité d'un fichier évolue avec sa source. Débrancher une USB rend ses fichiers indisponibles, sans les effacer du modèle ou des playlists.
- Supprimer un fichier physique ne supprime pas silencieusement le morceau logique ni les entrées qui le référencent. Pas de suppression en cascade automatique.
- Les entités principales ont des identifiants internes stables et opaques. Corriger un tag met à jour l'index et les affichages sans casser inutilement les références internes.

## Administration

Le gestionnaire de fichiers prévu permet d'explorer les sources, copier des morceaux ou dossiers d'une USB vers le mSATA, déplacer, renommer et supprimer des fichiers, créer des dossiers, gérer les conflits et actualiser l'index. La correction des métadonnées audio est également prévue. Ces fonctions restent à implémenter et à valider.

## État technique

- ✅ Lecture MPD → ALSA → SGTL5000 validée sur le matériel réel.
- ✅ La lecture haute résolution a également été validée sur le matériel réel.
- ✅ La gestion matérielle USB a été validée : deux ports utilisés simultanément, clés variées, montage à la demande, intégration MPD, retrait/réinsertion et lecture après remontage. Un rescan global n'est pas requis à chaque insertion.
- ✅ Bibliothèque locale sur mSATA ; valeur de référence PCM ALSA `numid=1` = `180`.
- ✅ Arrêt propre avec `sudo poweroff` avant de déconnecter l'alimentation.
- ⚪ Les interfaces, le moteur de recherche HUMM, le modèle de données applicatif et les fonctions d'administration décrits ici restent des objectifs de conception, sauf lorsqu'une autre page indique explicitement une validation réelle.

La configuration rapportée lors des validations comprend Armbian 26.8.1 Minimal / Debian 13 Trixie, le noyau `6.18.43-current-imx6`, MPD 0.24.x et la sortie ALSA `hw:CARD=Codec,DEV=0`. Ces versions identifient l'environnement documenté ; elles ne constituent pas une recommandation de mise à jour.

## Échanges de référence

Les décisions ont été consolidées à partir des conversations du projet : « 0. Architecture UX HUMM », « 1. Définir expérience HUMM », « 2. Plan UX Recherche », « 3. Décision UX playlists », « Point 10 UX HUMM », « Validation audio de HUMM » et « Gérer les clés USB génériques ». Les premières pistes de reconnaissance matériel et de NAS ont été dépassées par la plateforme réellement validée et le stockage local mSATA. Le plan directeur prévoit ensuite les réglages, l'API HUMM, le prototype, l'implémentation, la connexion progressive à MPD et les tests sur matériel réel.
