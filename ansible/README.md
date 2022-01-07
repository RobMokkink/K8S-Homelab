# Ansible prep playbook
The ansible playbook pre-install.yml is a quick and dirty playbook to prep the k8s nodes.
It will open the right ports for k8s and the overlay network.

Adjust the variables:

```
k8s_version: "1.23.1-00"
k8s_network: "weave"
```
