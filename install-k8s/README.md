# Installing k8s with containerd
We will use a config file with some basic settings for the cluster, remember to fill in the right
fqdn for api, this can be a loadbalancer of single master (depends on your setup)

Run the installation the following way:

```
sudo kubeadm init --config cluster.yml --upload-certs
```
