# MalScan

## Description

**MalScan** est un outil open-source conçu pour analyser des fichiers et des URL afin de détecter des menaces potentielles telles que des virus, des malwares et d'autres contenus malveillants. Le projet intègre plusieurs technologies et outils open-source pour fournir une analyse complète et précise des menaces.

## Fonctionnalités

- **Analyse de fichiers** : Scannez des fichiers pour détecter des virus et des malwares en utilisant ClamAV et Cuckoo Sandbox.
- **Analyse d'URL** : Analysez des URL pour identifier des contenus malveillants en utilisant Cuckoo Sandbox.
- **Mises à jour automatiques** : Maintenez la base de données virale à jour grâce à des mises à jour automatiques de ClamAV et des règles YARA.
- **Indexation et recherche** : Utilisez Elasticsearch pour indexer les résultats des analyses et Kibana pour les visualiser de manière interactive.
- **API RESTful** : Fournit une API RESTful pour soumettre des fichiers et des URL à analyser et obtenir les résultats.

## Technologies Utilisées

- **ClamAV** : Un moteur antivirus open-source utilisé pour scanner les fichiers.
- **Cuckoo Sandbox** : Une sandbox open-source pour analyser les comportements des malwares.
- **YARA** : Un outil pour identifier et classifier les malwares en fonction de règles définies.
- **Elasticsearch** : Pour l'indexation et la recherche des résultats d'analyse.
- **Kibana** : Pour la visualisation interactive des données d'analyse.
- **Flask** : Un micro-framework web pour créer l'API RESTful.

## Prérequis

- Docker
- Docker Compose

## Installation

1. Clonez ce dépôt :
   ```bash
   git clone https://github.com/votre-utilisateur/malscan.git
   cd malscan
   ```

2. Démarrez les services avec Docker Compose :
   ```bash
   docker-compose up -d
   ```

3. Accédez à Kibana via [http://localhost:5601](http://localhost:5601) pour visualiser les résultats d'analyse.

## Utilisation

### Analyse de fichier

Pour analyser un fichier, envoyez une requête POST à `/scan/file` avec le fichier en tant que champ de formulaire.

Exemple avec `curl` :
```bash
curl -F "file=@/path/to/your/file" http://localhost:5000/scan/file
```

### Analyse d'URL

Pour analyser une URL, envoyez une requête POST à `/scan/url` avec l'URL en tant que JSON.

Exemple avec `curl` :
```bash
curl -X POST -H "Content-Type: application/json" -d '{"url": "http://example.com"}' http://localhost:5000/scan/url
```

## Mise à jour des bases de données virales

### ClamAV

Le service `freshclam` est configuré pour mettre à jour automatiquement les bases de données de signatures de virus de ClamAV. Vous pouvez vérifier les journaux de `freshclam` pour vous assurer que les mises à jour sont effectuées correctement.

### YARA

Un script de mise à jour des règles YARA est configuré pour s'exécuter à intervalles réguliers à l'aide de cron. Vous pouvez modifier le fichier `update_yara_rules.sh` pour inclure des sources supplémentaires de règles YARA.

## Contribution

Les contributions sont les bienvenues ! Veuillez soumettre des pull requests ou ouvrir des issues pour les bugs et les fonctionnalités.

### Licence

Ce projet est sous licence MIT.
