# Testing the behavior of dns in cluster
## Connect through pod
```bash
$ k exec -it test -- bash
$ podIP=10.42.1.183
$ podIPConverted=10-42-1-183
$ ping $podIPConverted
PING 10.42.1.183 (10.42.1.183) 56(84) bytes of data.
64 bytes from 10.42.1.183: icmp_seq=1 ttl=63 time=0.074 ms

$ host 10.42.1.183
183.1.42.10.in-addr.arpa domain name pointer $podIPConverted.nginx-service.test-ns.svc.cluster.local.

$ cat /etc/resolv.conf
search test-ns.svc.cluster.local svc.cluster.local cluster.local ap-southeast-1.compute.internal
nameserver 10.43.0.10 # ip of coreDNS service
options ndots:5
```

```bash
curl $podIPConverted.test-ns.pod.cluster.local.
curl $podIPConverted.test-ns.pod.cluster.local
curl $podIPConverted.test-ns.pod
curl $podIPConverted.test-ns -> ERROR
```
thêm pod.cluster.local vào search của /etc/resolv.conf

```bash
curl $podIPConverted.test-ns -> OK
```

```bash
curl $podIPConverted.nginx-service.test-ns.svc.cluster.local.
curl $podIPConverted.nginx-service.test-ns.svc.cluster.local
curl $podIPConverted.nginx-service.test-ns.svc
curl $podIPConverted.nginx-service.test-ns
curl $podIPConverted.nginx-service
```

## Connect through service
```bash
serviceIP=10.43.166.188
serviceIPConverted=10-43-166-188
serviceName=nginx-service
```


```bash
curl $serviceIP
curl $serviceName
curl $serviceIPConverted.test-ns -> OK
curl $serviceIPConverted -> ERROR
```
