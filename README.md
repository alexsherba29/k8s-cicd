# k8s-cicd

## pre-requisites

List of tools to install

- [Docker](https://docs.docker.com/get-docker/)
- [Kubernetes](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Helm](https://helm.sh/docs/intro/install/)
- [K9s](https://k9scli.io/)


## Install Docker and kubenetes

**Only: Turn on Docker Desktop WSL 2**

[Link to installtion](https://docs.docker.com/desktop/windows/wsl/)

In the Docker Desktop settings, go to Resources > WSL Integration and check the Enable integration with my default WSL distro option.

Enable Kubernetes in Docker Desktop

## Install Helm

[Link to installtion](https://helm.sh/docs/intro/install/)

```cmd
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
sudo apt-get install apt-transport-https --yes
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
```

## Install K9s (Optional)

[Link to installtion](https://k9scli.io/)

```cmd
brew install k9s
```

## Install Jenkins

[Link to installtion](https://www.jenkins.io/doc/book/installing/)

Add Jenkins Helm repository

```cmd
helm repo add jenkins https://charts.jenkins.io
```

Download Jenkins Helm chart

```cmd
helm pull jenkins/jenkins
tar -xvzf jenkins-<version>.tgz
```

Install Jenkins

```cmd
helm upgrade --install jenkins ./ --values values.yaml -n jenkins
```

Check Jenkins pod

```cmd
kubectl get pods -n jenkins
```

If running you can port forward to access Jenkins

```cmd
kubectl port-forward svc/jenkins -n jenkins 8080:8080
```

