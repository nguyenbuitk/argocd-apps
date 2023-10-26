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