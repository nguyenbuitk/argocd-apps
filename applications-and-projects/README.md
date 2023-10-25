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

## Chapter 5
Create project and create application with project
```bash
k apply -f c5-01-project.yaml
k apply -f c5-04-application-dev-project.yaml
```

## Chapter 6
Apply for private repo and application point to that repo
```bash
k apply -f c6-private-repo-creds-https.yaml
k apply -f c6-application-with-private-repo.yaml
```

## Chapter 7
Just apply the application using kubectl and verify that its synced directly.
```bash
k apply -f c7-04-application-automated.yaml
```

## Chapter 8
Define an Argo CD application that track and deploy a helm chart latest version, and if there is any new release, it should be discovered and synced by Argo CD.
```bash
k apply -f c8-application-tracking-helm-latest-version.yaml
```

## Chapter 9
Define an Argo CD application that ignore the differences for the deployment replicas.
```bash
k apply -f c9-application-diffing-customization.yaml
```

## Chapter 10
Argo CD executes a sync operation in a number of steps. At a high-level, there are three phases pre-sync, sync and post-sync.
```bash
k apply -f c10-application-sync-waves.yaml
```

