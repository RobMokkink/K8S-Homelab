## Haproxy
See the haproy.cfg for the configuration, to balancer the master nodes behind haproxy.
If you use a selinux based distro make sure that the boolean to connect to any port is set, see the following command:
```setsebool -P haproxy_connect_any on```

Also make sure the ports are opened in the firewall.

And create a dns record to point to the haproxy node to create a HA k8s setup, for example ```k8s.lab.local```.
Make sure that ```controlPlaneEndpoint``` in you k8s config file is configured to match this dns name, for example:

```
---
apiVersion: kubeadm.k8s.io/v1beta2
kind: ClusterConfiguration
kubernetesVersion: v1.19.2
controlPlaneEndpoint: "k8s.lab.local:6443"
networking:
  podSubnet: 10.32.0.0/12
```
 
