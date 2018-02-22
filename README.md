# Jenkins/Kube/Helm demo for Index 2018

## Pre-reqs

```bash
brew cask install minikube
minikube start
brew install kubectl
brew install kubernetes-helm
```

## Set up Helm

```bash
helm init
kubectl rollout status deployment -n kube-system tiller-deploy
```
## Deploy Jenkins

```bash
helm install --name cd -f overrides.yaml stable/jenkins
printf $(kubectl get secret --namespace default cd-jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
minikube service cd-jenkins
```


