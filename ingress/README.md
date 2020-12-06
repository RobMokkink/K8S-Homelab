## ingress-nginx
Make sure metallb is installed.

Install ingress-nginx, see their [website](https://kubernetes.github.io/ingress-nginx/).
Install the cloud configuration manifest:

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.41.2/deploy/static/provider/cloud/deploy.yaml
```

The service ingress-nginx-controller will be of type Loadbalancer and get's an ip.

Create a wildcard dns record if you use the dnsmasq plugin with NetworkManager (see main README.md), like so:

```
address=/.apps.lab.local/10.0.128.100
```

And do a ```systemctl reload NetworkManager```


To test is, create a pod/deployment, expose it with a service (normal ClusterIP).
Create an ingress definition like so:

```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: ingress-ngninx
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
