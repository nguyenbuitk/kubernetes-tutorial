# Configure pod to use persistent volume
## Process
- Create persistent volume (pv) supported by storage physical, not accosiate with volume in any pod
- Create persistent volume claim (pvc) bound to pv just created
- Create pod to use above pvc for storage

## Script
```sh
sudo mkdir /mnt/data && echo sh -c "echo 'Hello from Kubernetes storage' > /mnt/data/index.html"

kubectl apply -f pv-claim.yaml
kubectl apply -f pv-volume.yaml
kubectl apply -f pv-pod.yaml

kubectl exec -it task-pv-pod -- /bin/bash
apt update
apt install curl
curl http://localhost/
```