# Jenkins/Kube/Helm demo for Index 2018

The accompanying presentation can be found on [SlideShare](https://www.slideshare.net/davidcurrie/continuous-delivery-to-kubernetes-with-jenkins-and-helm).

## Pre-reqs

```bash
brew cask install minikube
minikube start
minikube addons enable ingress
minikube addons enable registry
brew install kubectl
brew install kubernetes-helm
```

## Set up Helm

```bash
helm init --wait
```

## Deploy Jenkins

```bash
helm install --name cd -f overrides.yaml stable/jenkins
printf $(kubectl get secret --namespace default cd-jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
minikube service cd-jenkins
```

## Deploy app

1. Create a pipline job with a fork of this repository as the Git source for the pipeline.
2. Clicking *Build now* will push an image to the registry.
3. Run `helm create hello` and modify `values.yaml` to enable ingress and provide a hostname (`hello.192.168.99.100.nip.io`).
4. Uncomment the helm container and deploy stages in `Jenkinsfile`.
5. Push changes and re-build.
