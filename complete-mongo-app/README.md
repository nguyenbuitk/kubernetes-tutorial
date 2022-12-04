# Complete mongo application

## Step 1:
Create mongodb deployment
```sh
k apply -f mongo-db-secret.yaml
k apply -f mongo-db.yaml
```

## Step 2:
Create internal service, so that other component and other pod can talk to mongodb
```sh
k apply -f mongodb-service.yaml
```

## Step 3:
Create configmap for mongo express connect to mongodb
```sh
k apply -f mongo-configmap.yaml
```

## Step 4:
Apply mongo db and mongo express
```sh
k apply -f mongo-express.yaml
```
## Summarize
From inside cluster, you can access the pod by
curl <mongo-express-pod-ip>:8081 in the node of cluster
because node have internal ip 10.42.0.0/32


What is port 8081? It's listening port of mongo
check with:
```sh
k exec -it mongo-express -- sh
netstat -tulpn
```
