# k8s-playground

Playing around with Kubernetes...

## Minikube

**Start Minikube**
```sh
minikube start
```

**Enable Ingress addon:**
```sh
minikube addons enable ingress
minikube tunnel
```

# Argo CD

Argo CD is ment to be configured self-managed by leveraging the [argo-cd-aoa-boilerplate](https://github.com/SelfhostedPro/argo-cd-aoa-boilerplate)
repository with some adjustments.

Build and apply argo by invoking
```sh
kustomize build argo-cd/ | kubectl apply -n argocd -f -
```
And retrieve the admin secret using
```pwsh
[System.Text.Encoding]::UTF8.GetString([Convert]::FromBase64String((kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}")))
```

TODO:
- Add a declarative admin secret
- Add GitHub Secrets, Keys, etc..
- Add this repository as a configuration source