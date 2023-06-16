# Ansible prep playbook
The ansible playbook pre-install.yml is a quick and dirty playbook to prep the k8s nodes. It is for learning purposes only!
It will open the right ports for k8s for the overlay network and install the containerd runtime.

Adjust the variables inside the playbook or specify them on the commandline

```
k8s_version: "1.26.0-00"
k8s_network: "weave"
```

## Containerd config file
The containerd config file, see [config.toml](files/config.toml), is generated using the following commando:

```
sudo containerd config dump | tee -a ~/config.toml
```

After that it is adjusted to use systemd cgroup driver by adjust line:

```
SystemdCgroup = false
```

To:

```
SystemdCgroup = true
```

For more information see the [k8s docs for the cgroup driver](systemd_cgroup = true)
