# Jenkins Logs to S3 Backup Script 🚀

Ce script Bash permet de télécharger les logs des builds Jenkins créés aujourd'hui et de les envoyer vers un bucket S3 spécifié.

## 📌 Prérequis

- **AWS CLI** installé (vérifie avec `aws --version`).
- Un **compte AWS** avec les permissions nécessaires pour interagir avec S3.
- **AWS CLI** configuré avec `aws configure`.
- Un **serveur Jenkins** avec des jobs et builds générés.

## 🛠️ Fonctionnalités

- **Sauvegarde des logs Jenkins** : Le script parcourt les répertoires des jobs Jenkins et vérifie les logs des builds créés aujourd'hui.
- **Téléchargement vers S3** : Si un log a été créé aujourd'hui, il est téléchargé dans un bucket S3 spécifié.
- **Vérification de l'installation d'AWS CLI** : Le script s'assure qu'AWS CLI est installé avant de tenter de télécharger les fichiers.

## 📝 Configuration

1. **Modifier les variables du script** :
   - **`JENKINS_HOME`** : Chemin vers le répertoire d'installation de Jenkins.
   - **`S3_BUCKET`** : Nom du bucket S3 où les logs seront téléchargés.

Exemple de configuration dans le script :

```bash
JENKINS_HOME="/var/lib/jenkins"  # Remplace avec le chemin de ton répertoire Jenkins
S3_BUCKET="s3://ton-bucket-s3"  # Remplace avec ton nom de bucket S3
```

## 💻 Utilisation
Clone ce repository :

```bash
git clone https://github.com/ton-utilisateur/ton-repository.git
cd ton-repository
```

Assure-toi que AWS CLI est installé :

Vérifie l'installation avec la commande aws --version.
Si non installé, suis le guide d'installation : Guide d'installation AWS CLI.

Exécute le script :

```bash
./jenkins_logs_to_s3.sh
```

Le script parcourra tous les jobs Jenkins et les builds créés aujourd'hui, puis téléchargera les logs dans le bucket S3 spécifié.

Exemple d'exécution
Si le script fonctionne correctement, tu verras un message pour chaque log téléchargé :

```bash
Uploaded: job1/42 to s3://ton-bucket-s3/job1-42.log
```

En cas d'échec, tu verras un message d'erreur :

```bash
Failed to upload: job1/42
```

## ⚠️ Sécurité
Veille à ce que les logs Jenkins que tu sauvegardes sur S3 ne contiennent pas d'informations sensibles ou confidentielles. Utilise des permissions S3 appropriées pour restreindre l'accès aux logs.

