# TP4 DevOps – Application MERN avec Docker et Docker Compose

## 1. Création des Dockerfiles

Deux fichiers Dockerfile ont été créés pour construire les images de l'application.

### 1.1 Dockerfile du serveur (Server)

Le Dockerfile du serveur permet de :
- Utiliser l'image officielle Node.js `lts-alpine`.
- Définir le répertoire de travail `/app`.
- Copier les fichiers `package.json` et `package-lock.json`.
- Installer les dépendances avec `npm install`.
- Copier les fichiers du serveur.
- Démarrer le serveur avec `npm start`.

### 1.2 Dockerfile du client (Client)

Le Dockerfile du client permet de :
- Utiliser l'image officielle Node.js `lts-alpine`.
- Définir le répertoire de travail.
- Copier les fichiers de configuration.
- Installer les dépendances avec `npm install`.
- Copier le code source du client.
- Construire l'application avec `npm run build`.
- Installer l'outil `serve` pour servir l'application frontend.

## 3. Configuration Docker Compose

Le fichier `docker-compose.yml` permet de gérer les trois services de l'application :

- **MongoDB :** utilise l'image officielle `mongo`.
- **Server :** construit à partir du dossier `./server` et expose le port `9000`.
- **Client :** construit à partir du dossier `./client` et expose le port `3000`.

Les trois services sont connectés au réseau Docker `mern-network`, ce qui permet leur communication.

Le service Server dépend de MongoDB et le service Client dépend du Server.

## 4. Exécution de l'application

Pour construire les images et démarrer les conteneurs, exécuter la commande suivante dans le répertoire racine du projet :

```bash
docker compose up --build
```

Cette commande permet de :
- Construire les images Docker du client et du serveur.
- Créer et démarrer les conteneurs.
- Lancer les trois services de l'application.

## 5. Vérification des conteneurs

Pour vérifier que les conteneurs fonctionnent correctement, utiliser :

```bash
docker ps
```

Les trois conteneurs attendus sont :
- mongodb
- server
- client

Le serveur fonctionne sur le port `9000` et le client est accessible sur le port `3000`.

### Accès à l'application

- Frontend : http://localhost:3000
- Backend : http://localhost:9000

## 6. Pipeline Jenkins

Cette partie présente les captures d'écran du pipeline Jenkins réalisé dans le cadre du projet.

Le pipeline permet d'automatiser les différentes étapes de construction et de déploiement du projet.

**Capture d'écran :** `Screenshots/Jenkins_Pipeline.png`

## 7. Images et conteneurs Docker

Les images Docker construites pour le projet sont :

- `mern-client`
- `mern-server`

Les conteneurs créés sont :

- `mongodb`
- `server`
- `client`

**Captures d'écran :**
- `Screenshots/Docker_Image.png`
- `Screenshots/Docker_Containers.png`
- `Screenshots/Docker_Compose.png`

## 8. Liens du projet

- **GitHub :** [Ajouter le lien du repository GitHub]
- **Docker Hub :** [Ajouter le lien des images Docker publiées]
