First, create secret and config map

k apply -f mongo-db-secret.yaml

k apply -f mongo-configmap.yaml


Apply mongo db and mongo express

k apply -f mongo-db.yaml

k apply -f mongo-expres.yaml


From inside cluster, you can access the pod by
curl <mongo-express-pod-ip>:8081


??? What is port 8081: It's listening port of mongo
	# check with: 	k exec -it mongo-express -- sh	
			netstat -tulpn

??? Add load balancer to mongo-express yaml file
