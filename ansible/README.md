# Ansible prep playbook
The ansible playbook pre-install.yml is a quick and dirty playbook to prep the k8s nodes. It is for learning purposes only!
It will open the right ports for k8s for the overlay network and install the containerd runtime.

Adjust the variables inside the playbook or specify them on the commandline

```
k8s_version: "1.26.0-00"
k8s_network: "weave"
```
