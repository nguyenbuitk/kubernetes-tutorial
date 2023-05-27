# This folder for testing about ingress in k8s

## Get ingress
```bash
k get ingress
NAME             CLASS    HOSTS   ADDRESS                           PORTS   AGE
my-app-ingress   <none>   *       10.0.0.160,10.0.0.185,10.0.0.44   80      7m13s
```
These IP addresses are node IP
Depending on your cluster configuration, requests to the Ingress will be routed to one of these IP addresses, allowing the traffic to reach the appropriate backend service or application.

## Edit in hosts file
18.143.108.45 test-ingress.com

## Browser
```bash
curl http://test-ingress.com/banana
curl http://test-ingress.com/apple
```
