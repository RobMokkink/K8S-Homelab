## Install weave with proper options
Make sure you use weave, and install it with the option ```NO_MASQ_LOCAL=1```

See for example:
```
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')&env.NO_MASQ_LOCAL=1"
```

If you happend to install weave without this option, simple uninstall weave and reinstall it with the option like described above.

## Install metallb
Install metallb in layer 2 mode like described in https://metallb.universe.tf/installation/#installation-by-manifest.
