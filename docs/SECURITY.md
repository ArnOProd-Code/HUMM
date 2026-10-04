# Sécurité et dépôt public

Le dépôt GitHub est public. Les contributions doivent exclure tout contenu privé ou secret.

## Ne jamais publier

- mots de passe, clés SSH, tokens, clés privées ou fichiers de configuration contenant des secrets ;
- adresses IP privées ou données personnelles ;
- fichiers musicaux, bases de données privées ou exports de bibliothèque ;
- journaux ou sauvegardes susceptibles de contenir ces informations.

## Protections du dépôt

Le `.gitignore` protège les fichiers d'environnement et de clés courants, les journaux, caches, répertoires locaux de données (`data/`, `music/`, `library/`) et fichiers temporaires. Des règles couvrent également les fichiers de base de données locale.

Ces protections réduisent les ajouts accidentels ; elles ne remplacent pas la vérification du contenu avant chaque commit. Ne jamais copier de données privées dans la documentation ou les exemples.
