# ingress-nginx

## Installation
Make sure that the wildcard dns record exists
Install the ingress controller as describe in https://kubernetes.github.io/ingress-nginx/deploy/#bare-metal-clusters

## Configuration
Adjust the service:

```
kubectl -n ingress-nginx get svc
NAME                                 TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                      AGE
ingress-nginx-controller             NodePort    10.96.202.195   <none>        80:30406/TCP,443:32287/TCP   67s
ingress-nginx-controller-admission   ClusterIP   10.99.105.61    <none>        443/TCP                      67s
```

Now adjust the nodeport to match haproxy config
```
kubectl -n ingress-nginx edit svc ingress-nginx-controller

<SNIP>
ports:
- appProtocol: http
  name: http
  nodePort: 30080
  port: 80
  protocol: TCP 
  targetPort: http
- appProtocol: https
  name: https
  nodePort: 30443
  port: 443 
  protocol: TCP 
  targetPort: https
<SNIP>
```

Check:
```
kubectl -n ingress-nginx get svc
NAME                                 TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)                      AGE
ingress-nginx-controller             NodePort    10.96.202.195   <none>        80:30080/TCP,443:30443/TCP   5m8s
ingress-nginx-controller-admission   ClusterIP   10.99.105.61    <none>        443/TCP                      5m8s
```

You can also have a look at the status page of haproxy http://lb:8443/stats

Scale the amount of ingress pods to 3, to match the amount of workers:

```
kubectl -n ingress-nginx scale deployment.apps/ingress-nginx-controller --replicas=3
```

Check:

```
kubectl -n ingress-nginx get pods -o wide
NAME                                        READY   STATUS      RESTARTS   AGE   IP          NODE      NOMINATED NODE   READINESS GATES
ingress-nginx-admission-create-b6rn2        0/1     Completed   0          17m   10.44.0.1   worker3   <none>           <none>
ingress-nginx-admission-patch-6hbds         0/1     Completed   1          17m   10.32.0.2   worker2   <none>           <none>
ingress-nginx-controller-84b9776df8-2rrqw   1/1     Running     0          68s   10.44.0.2   worker3   <none>           <none>
ingress-nginx-controller-84b9776df8-c2znp   1/1     Running     0          17m   10.32.0.3   worker2   <none>           <none>
ingress-nginx-controller-84b9776df8-flj6h   1/1     Running     0          68s   10.40.0.3   worker1   <none>           <none>
``` 

## Create a test deployment

```
kubectl create ns test-ingress
kubectl -n test-ingress run nginx --image=nginx:alpine
kubectl -n test-ingress expose pod nginx --port 80
```

Create an ingress definition like so:

```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress-ngninx
  namespace: test-ingress
  annotations:
    kubernetes.io/ingress.class: nginx
spec:
  rules:
  - host: nginx.apps.lab.local
    http:
      paths:
      - pathType: Prefix
        path: "/"
        backend:
          service:
            name: nginx
            port:
              number: 80
```

You can now access the website using ```nginx.apps.lab.local```
