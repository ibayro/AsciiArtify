## AsciiArtify Proof of Concept for deploying GitOps system with ArgoCD on a Kubernetes cluster via Kind

> POC is the stage when the developers check whether it is technically possible to implement the product concept. At this stage, developers use a minimal set of features to demonstrate that the product can work and perform its core functions.

### Installing and configuring command access to the ArgoCD GUI in a kind cluster

#### Preconditions

- kind installed on a local machine;
- kind cluster is created.

#### Preparation

1. Create a namespace

```
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```
2. Expose ArgoCD service in a background to reach GUI on a local machine:

   ```
   kubectl port-forward svc/argocd-server -n argocd 8080:443&
   ```

#### Command Access 

1. Install the latest version of ArgoCD CLI
 ```
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64
 ```
 
 2. Sing in to ArgoCD by using initial admin-secret
 ```
argocd admin initial-password -n argocd
 ```
 
 3. Login to ArgoCD via CLI and change password
 ```
argocd login <ARGOCD_SERVER>
argocd account update-password
 ```
4. Save password in a safe place and provide credentials to the team 
![ArgoCD login](https://github.com/ibayro/AsciiArtify/assets/104074570/4df597c1-3fd1-4a25-bf81-2ed799c4c7a0)



