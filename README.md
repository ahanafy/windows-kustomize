# windows-kustomize

This repo has a kustomize file at root, that references the bases and resources to apply.

This public repo github.com/ahanafy/windows-kustomize can be referenced in a remote kustomize file as a base

```
bases:
- github.com/ahanafy/windows-kustomize?ref=master
```

To render the manifests here without applying them run customize build on the root directory of the git repo.

```
kustomize build .
```
OR
```
kustomize build $(git rev-parse --show-toplevel)
```

Get the Istio Ingressgateway public ip address:

```
kubectl -n istio-system get service istio-ingressgateway
```

Update the hosts entry in the windows/networking/virtualservice.yaml file under spec.hosts
Replace the ip address with your ingressgateway public address.
For more information on xip.io addresses: http://xip.io/