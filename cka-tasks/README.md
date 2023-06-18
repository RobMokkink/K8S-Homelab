## CKA-Tasks
See the tasks below to start prepping for the cka exam

NOTE: there are NO solutions, you must learn to figure it out yourself!

### 1: Run container
Task: run a container name nginx with image nginx

### 2: Run container on masternodes
Task: run a container name schedule-on-masters, using image```busybox``` and command ```sleep 7200```

### 3: Run container in specific master node
Task: same a previous task, but run the pod on a specific master node (no static pod)

### 4: Create a new single node master and worker cluster manually
Task: destroy the current cluster and adjust the terraform vars file to only deply one master and one worker. Instead of using the ansible prep tools, use the [k8s docs](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/) to get it up and running. Use weave of calico overlay network.

### 5: Create and restore etcd
Task: create and restore a backup of etcd (do it on the cluster from task 3)

### 6: Install the metrics-server
Task: install the metrics-server, see the following [github page](https://github.com/kubernetes-sigs/metrics-server)

### 7: Show resource usage per node
Task: show the resource usage per node (you need to complete task 6 first)

### 8: Show the resource usage of all pods
Task: show the resource usage per pod and also show the resource usage of the containers inside the pods (you need to complete task 6 first)
