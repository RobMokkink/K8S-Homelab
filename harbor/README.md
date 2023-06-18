## Harbor
Create your own harbor registry instance, see the following [site](https://goharbor.io).

### Add certification to the node
Running harbor in this setup i assume you are using the HTTP for traffic to harbor.
The setup is explained in this [doc](https://goharbor.io/docs/2.8.0/install-config/configure-https/).

Make sure to add the certificates to the trust store ```/usr/local/share/ca-certificates``` on the Ubuntu nodes and run command ```sudo update-ca-certificates```.
After that restart the containerd service ```sudo systemctl restart containerd```
