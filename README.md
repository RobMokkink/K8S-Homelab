# CKA-CKAD-Prep

This repo contains some stuff to setup and practice for CKA and CKAD.
This is not meant to be a full step by step tutorial, but it can give you good pointers about how to setup
a full lab environment


## Ansible
This contains a prep playbook to setup ubuntu 16/18 LTS nodes with containerd

## Installation
There is an example configuration file in install-k8s directory which is needed for kubeadm
in combination with containerd

## Wildcard dns
If you use the dnsmasq plugin with NetworkManager, see https://fedoramagazine.org/using-the-networkmanagers-dnsmasq-plugin/
Make sure that ```/etc/nsswitch.conf``` is configure correctly, this must be set to ```hosts:       dns files```
