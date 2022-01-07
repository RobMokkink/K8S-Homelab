# Check cluster and label nodes
Now that the overlay network is there, time to check the cluster:

```
kubectl get nodes
NAME      STATUS   ROLES                  AGE    VERSION
master1   Ready    control-plane,master   151m   v1.23.1
master2   Ready    control-plane,master   145m   v1.23.1
master3   Ready    control-plane,master   136m   v1.23.1
worker1   Ready    <none>                 136m   v1.23.1
worker2   Ready    <none>                 130m   v1.23.1
worker3   Ready    <none>                 128m   v1.23.1
```


## Label worker nodes
Label the worker nodes:

```
kubectl label node worker1 node-role.kubernetes.io/worker=
kubectl label node worker2 node-role.kubernetes.io/worker=
kubectl label node worker3 node-role.kubernetes.io/worker=
```

Check the nodes:

```
kubectl get nodes
NAME      STATUS   ROLES                  AGE    VERSION
master1   Ready    control-plane,master   153m   v1.23.1
master2   Ready    control-plane,master   148m   v1.23.1
master3   Ready    control-plane,master   138m   v1.23.1
worker1   Ready    worker                 138m   v1.23.1
worker2   Ready    worker                 133m   v1.23.1
worker3   Ready    worker                 130m   v1.23.1
```
