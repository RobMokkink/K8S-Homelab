# Add disk to the worker nodes
Make sure you add a disk to each worker node

# Upstream website
Go to the upstream website https://rook.io/

# Quickstart
See the documentation quick-start on howto install rook-ceph on a cluster

## Clone repo
Clone the rook-ceph gitrepo

## Deploy the manifests
Goto the ```deploy/examples``` directory.

```
$ kubectl create -f crds.yaml -f common.yaml -f operator.yaml
```

Wait until the operator pod is ready and deploy the cluster

```
$ kubectl create -f cluster.yaml
```

Create the toolbox pod
```
$ kubectl  apply -f toolbox.yaml
```

## Create storageclasses
See the following [link](https://rook.io/docs/rook/latest-release/Getting-Started/quickstart/#storage) for creating the storageclasses
