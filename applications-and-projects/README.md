the initial password is available from a secret named argocd-initial-admin-secret .
**c4 is stands for chapter 4**
## Chapter 4
Example: Create Argo CD Application
- Define an Argo CD application declaratively using Yaml.
    + Source: Use this directory manifests as a source: https://github.com/mabusaa/argocd-example-apps/tree/master/guestbook
    + Destination: use local Kubernetes cluster.
- Apply the Argo CD Application using kubectl.
- View the app in Web and sync it, also verify resources are created in destination cluster

Simply apply

```kubectl apply -f c4-application.yaml```

ArgoCD supports the below tools as source and options relative to each tools: helm charts, directory and kustomize. Following file is example:
- c4-application-directory-options.yaml
- c4-application-helm-options.yaml
- c4-application-kustomize-options.yaml