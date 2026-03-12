# TP2 - Microservices avec Docker Compose

Ce projet contient deux microservices Flask (`service-user` et `service-order`) orchestrés avec **Docker Compose**.

## Structure du Projet

- **service-user** : Gère les informations des utilisateurs (Port 5001).
- **service-order** : Gère les commandes et communique avec le service utilisateur (Port 5002).
- **docker-compose.yml** : Fichier de configuration pour lancer les deux services simultanément.

## Prérequis

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Installation et Lancement

1. Accédez au répertoire du TP2 :
   ```bash
   cd tp2
   ```

2. Lancez les services avec Docker Compose :
   ```bash
   docker-compose up --build
   ```

## Utilisation

Une fois les conteneurs lancés, vous pouvez tester les endpoints suivants :

- **Service User** : [http://localhost:5001/users](http://localhost:5001/users)
- **Service Order** : [http://localhost:5002/orders](http://localhost:5002/orders)

Le `service-order` appelle internement le `service-user` via le réseau Docker pour récupérer les noms des utilisateurs.

## Commandes Utiles

- Arrêter les services : `docker-compose down`
- Voir les logs : `docker-compose logs -f`
