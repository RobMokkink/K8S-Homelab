## Haproxy
See the [haproy.cfg](haproxy.cfg) for the configuration, to balancer the master nodes behind haproxy.
If you use a selinux based distro make sure that the boolean to connect to any port is set, see the following command:
```setsebool -P haproxy_connect_any on```

Also make sure the ports are opened in the firewall.
```
# Add ports
sudo firewall-cmd --add-port=80/tcp --add-port=443/tcp --add-port=6443/tcp --add-port=8443/tcp --permanent

# Restart service
sudo systemctl restart firewalld

# Verify
sudo firewall-cmd --list-all
```

### Verify haproxy status
Go to the url of the haproxy server, for example:
```
http://lb.lab.local:8443/stats
```
