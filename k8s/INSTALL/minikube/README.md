## HOW TO INSTALL K8S ON UBUNTU(LINUX) MACHINE - MINIKUBE


## 1. Create 1 EC2 instance.

ami  = ubuntu-22   ------>  instance types = t2.medium 

key pair  =  k8s.pem   ---->  sg  =  ubuntu-SG (all traffic = ANYWHERE)


## 2. Connect k8s-master instance & install docker - minikube


```sh
sudo apt update
sudo apt install docker.io -y
docker --version
```


To install the latest minikube ; Follw this link 👉👉 https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download 


```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```

To check minikube version

```sh
minikube version
```

To allow permission for docker to run on any user & group

```sh
sudo usermod -aG docker $USER && newgrp docker
```


To start minikube service

```sh
minikube start --driver=docker
```


sudo snap install kubectl --classic

kubectl get nodes

kubectl cluster-info

kubectl get po -A

============end========================
