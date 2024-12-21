# ArgoCD

## Installation
> Reference: https://argo-cd.readthedocs.io/en/stable/getting_started/#1-install-argo-cd
1. Create Kubernetes namespace for ArgoCD: `kubectl create namespace argocd`
2. Deploy ArgoCD in Kubernetes: `kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`

## Access ArgoCD UI
1. Find password of default `admin` user: `kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"`
2. Copy the password which is in Base64.
3. Open any website to decode the Base64 password.
4. Do port forward for the ArgoCD Server deployed in Docker Desktop Kubernetes: `kubectl port-forward --namespace=ingress-nginx service/ingress-nginx-controller 30443:443`
5. Open the URL: [https://localhost:30443/](https://localhost:30443/)
6. Login by default user and the password.

## Add Project
1. Go Projects feature: Menu>Settings>Projects
2. Add project:
> - Press `+ NEW PROJECT` button
> - keyin `devsecops` in project name
> - create project by press `CREATE` button

## Edit Project
1. Go Your Project to edit: Menu>Settings>Projects>devsecops
2. Allowed all source repositories:
> - Find `SOURCE REPOSITORIES` 
> - press `EDIT`,
> - press `ADD SOURCE`
> - save by press `SAVE` button
3. Allowed all destinations to deploy:
> - Find `DESTINATIONS` 
> - press `EDIT`,
> - press `ADD DESTINATION`
> - save by press `SAVE` button
4. Allowed all cluster resource and namespace resource to deploy:
> - Find `CLUSTER RESOURCE ALLOW LIST` 
> - press `EDIT`,
> - press `ADD RESOURCE`
> - Find `NAMESPACE RESOURCE ALLOW LIST` 
> - press `ADD RESOURCE`
> - save by press `SAVE` button

## Add ArgoCD Application
1. Go Applications feature: Menu>APPLICATIONS
2. Add application:
> - Press `+ NEW APP` button
> - press `EDIT AS YAML`
> - copy and patse the manifest in [dso-demo/dev/argocd-app.yaml](/dso-demo/dev/argocd-app.yaml)
> - press `SAVE`
> - press `CREATE`
> - wait the deployment finish and success.
