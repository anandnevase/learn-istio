# Istio Mirroring Demo

## Istio installation
Follow below url for istio installation on Minikube
https://github.com/anandnevase/learn-istio/blob/main/1-install-istio/README.MD 


## Clone install repo

```bash
$ git clone https://github.com/anandnevase/learn-istio
Cloning into 'learn-istio'...
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 10 (delta 0), reused 7 (delta 0), pack-reused 0
Unpacking objects: 100% (10/10), done.
```

## Navigate to 7-mirroring
```
$ cd learn-istio/7-mirroring
```

## Deploy Sample Hello World App
```bash
$ kubectl apply -f 1-deployment.yaml
```
## Apply Istio  rules 

```bash
$ kubectl apply -f istio-rules.yaml
```

## Access application

```bash

$ curl http://<minikube-ip>:31380
Hello Openshift V1

```