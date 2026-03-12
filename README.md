# TP 3 : Orchestration de Microservices avec Kubernetes

Ce projet déploie deux microservices communicants dans un cluster Kubernetes (Docker Desktop).

## Architecture
1. **service-user** : Un microservice Flask qui renvoie une liste d'utilisateurs sur le port **5001**.
2. **service-order** : Un microservice Flask qui appelle `service-user` pour afficher des commandes sur le port **5002**.

## Déploiement (Étape par étape)

### 1. Construire les images Docker
Kubernetes utilise des images locales. Tapez ces commandes :
```powershell
docker build -t user-service:latest ./service-user
docker build -t order-service:latest ./service-order
```

### 2. Déployer sur Kubernetes
On applique les fichiers de configuration :
```powershell
kubectl apply -f Deployment.yaml
kubectl apply -f Service.yaml
```

### 3. Vérifier que tout est prêt
Attendez que les pods soient en état **Running** :
```powershell
kubectl get pods
```

## Comment tester l'API ?
Une fois les pods lancés, vous pouvez tester l'application directement depuis votre navigateur ou avec `curl` :

```powershell
curl http://localhost:9000/orders
```

## Résultat attendu
Vous devriez recevoir cette réponse JSON :
```json
{"orders":["Order 1 for Alice","Order 2 for Bob"]}
```
