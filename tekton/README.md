# Tekton
Tekton is made up by several components that need to be installed.
See the [upstream documentation](https://tekton.dev/docs/installation)

# Pipelines
See https://tekton.dev/docs/installation/pipelines/

# Triggers
https://tekton.dev/docs/installation/triggers/

# Dashboard
See https://tekton.dev/docs/dashboard/
Ingress is setup in this cluster, so use https://tekton.dev/docs/dashboard/install/#using-an-ingress-rule
See the [ingress-example.yaml](ingress-example.yaml)

# Commandline
See https://tekton.dev/docs/cli

# Create secret for registry
Example:

```
$ kubectl create secret docker-registry harbor --docker-server https://harbor.lab.local --docker-username tekton --docker-password "SuperSecretPassw0rd!" -n tekton-pipelines
```

# Setup authentication to git repository
See https://tekton.dev/docs/pipelines/auth/
