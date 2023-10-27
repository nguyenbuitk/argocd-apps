# ArgoCD Apps

![ArgoCD Logo](argo-logo.png)

This repository contains a collection of [ArgoCD](https://argoproj.github.io/argo-cd/) applications and manifests for deploying various applications and services.

## Table of Contents
- [Introduction](#introduction)
- [Applications](#applications)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Introduction

[ArgoCD](https://argoproj.github.io/argo-cd/) is a declarative, GitOps continuous delivery tool for Kubernetes. This repository is meant to be used with ArgoCD and contains a set of application manifests and configurations.

## Applications

Here are some of the applications and services included in this repository:

- **App 1**: Description of App 1.
- **App 2**: Description of App 2.
- **App 3**: Description of App 3.

You can find more details in the respective subdirectories.

## Usage

the initial password is available from a secret named argocd-initial-admin-secret .
**c4 is stands for chapter 4**
## Chapter 4
Example:
- Define an Argo CD application declaratively using Yaml.
    + Source: Use this directory manifests as a source: https://github.com/mabusaa/argocd-example-apps/tree/master/guestbook
    + Destination: use local Kubernetes cluster.
- Apply the Argo CD Application using kubectl.
- View the app in Web and sync it, also verify resources are created in destination cluster

Simply apply

```kubectl apply -f c4-application.yaml```

## Chapter 5
Example:
- Define and create Argo CD Project declaratively with below info:
    + Allow all sources (repos)
    + Allow all destinations
    + Allow all cluster and namespace scoped resources
- Then, define and create and Argo CD Application that is related  to the new project
```bash
k apply -f c5-01-project.yaml
k apply -f c5-04-application-dev-project.yaml
```

## Chapter 6
- Define and add a private git repo to Argo CD.
- Verify its connected successfully in repositories page in Web UI
- Then, create an Argo CD application that use the private repo as source of manifests.
```bash
k apply -f c6-private-repo-creds-https.yaml
k apply -f c6-application-with-private-repo.yaml
```

## Chapter 7
- Define an Argo CD application and enable the automated sync only.
    + Manifests as source : https://github.com/mabusaa/argocd-exampleapps/tree/master/guestbook-with-sub-directories.
- Apply the application using kubectl and verify that its synced directly.
- Delete the service file from git repo and notice that its not deleted from destination cluster.
- Then, enable the auto pruning in application definition and verify the service is deleted from destination cluster.
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
Create an application with manifests synced as below:
- One job in PreSync phase, this job should be deleted once Succeeded.
- One job in Sync phase, this job should be deleted if new resource is created.
- One job in PostSync phase, this job should be deleted if failed.
- Add a job manifest that will be skipped by ArgoCD.
```bash
k apply -f c10-application-sync-waves.yaml
```

## Chapter 11
Create a new k8s cluster in any remote environment using argocd CLI with kubeconfig (cloud or  on-premise or local.)
```bash
k apply -f c11-application-remote-cluster.yaml
```

## Chapter 12
1. Deploy one application into all clusters:
- Application name should include cluster name.
- Use one ApplicationSet manifest with cluster generator to achieve this.
```bash
k apply -f c12-list-generator.yaml
```

2. Deploy one application into all clusters with matching label non-prod=true.
- Application name should include cluster name.
- Use one ApplicationSet with cluster generator to achieve this.
```bash
k apply -f c12-cluster-generator-matching-labels.yaml
```