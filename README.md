# K8S Homelab
This repo contains a tutorial on how-to setup k8s in HA mode for training purposes.

## Disclaimer
This repo and it's contents is not ment to be distributed for commercials purposes"

## 1 Setting up your shell and exam tips
This are some settings you can set quickly for the exam:

### vim settings
Create/edit file ```~/.vimrc```, add the following:

```
autocmd FileType yaml setlocal ts=2 sw=2 et ai
```

### alias for kubectl
Set an alias for kubectl.
```
$ alias k='kubectl'
```

### kubectl explain is your friend
If the doccumentation is not clear, use:

```
$ kubectl explain <name of resource>
```

## 2 Dnsmasq with networkmanager
If you use the dnsmasq plugin with NetworkManager, see https://fedoramagazine.org/using-the-networkmanagers-dnsmasq-plugin/
Make sure that ```/etc/nsswitch.conf``` is configure correctly, this must be set to ```hosts:       dns files```, and disable ```systemd-resolved``` with ```sudo systemctl is-disabled systemd-resolved``` and reboot you system.

Make sure dns entries are there, see the following example:

```/etc/hosts```:

```
10.0.0.10	lb.lab.local lb 
10.0.0.20	master1.lab.local master1
10.0.0.21	master2.lab.local master2
10.0.0.22	master3.lab.local master3
10.0.0.30	worker1.lab.local worker1
10.0.0.31	worker2.lab.local worker2
10.0.0.32	worker3.lab.local worker3
```

And the following for k8s api and wildcard ingress ```/etc/NetworkManager/dnsmasq.d/02-lab.conf```

```
# K8S api points to lb
address=/k8s.lab.local/10.0.0.10

# wildcard dns entry points to lb
address=/.apps.lab.local/10.0.0.10
```

Reload networkmanager ```sudo systemctl reload NetworkManager```


## 3 Deploy haproxy node
See the folder [haproxy](haproxy) with the config for haproxy

## 4 Deploy nodes
See the following [repo](https://github.com/RobMokkink/terraform/tree/main/libvirt-k8s-ubuntu) on how-to deploy ubuntu nodes with

## 5 Prep the nodes Ansible
See the folder [ansible](ansible) contains a prep playbook to setup ubuntu nodes with containerd

## 6 Installation
There is an example configuration file in [install-k8s](install-k8s) directory which is needed for kubeadm
in combination with containerd

## 7 Overlay Network
See folder [overlay-network](overlay-network) for instructions

## 8 Check cluster and label nodes
See folder [check-cluster-label-nodes](check-cluster-label-nodes) for instructions

## 9 Ingress
See folder [ingress](ingress) for instructions

## 10 Create harbor instance
See folder [harbor](harbor) for instructions
