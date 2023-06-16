# Installing k8s with containerd
We will use a config file with some basic settings for the cluster, remember to fill in the right
fqdn for api, this can be a loadbalancer of single master (depends on your setup)

See k8s [documentation](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/#initializing-your-control-plane-node)


## Determine the overlay network requirements
Weave requires pod network cidr ```10.32.0.0/12```
Calico requires pod network cird ```192.168.0.0/16```


Run the installation with one of the following methods


## Config file
Make adjustments to the ```cluster.yml```
```
sudo kubeadm init --config cluster.yml --upload-certs
```

## Commandline

```
sudo kubeadm init --pod-network-cidr=<cidr you need for overlay network> --control-plane-endpoint=<dns name of loadbalancer> --upload-certs
```

This is an example with the weave overlay network
```
sudo kubeadm init --pod-network-cidr=10.32.0.0/12 --control-plane-endpoint=k8s.lab.local:6443 --upload-certs
```

## Add the rest of the master and worker nodes
See the output from the ```kubeadm init``` command and add the rest of the master and worker nodes
