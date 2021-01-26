# Istio mTLS

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

## Navigate to 1-install-istio
```
$ cd learn-istio/mtls
```

## Deploy Sample App
```bash
$ kubectl apply -f application-no-istio.yaml
```

## Get minikube IP
```bash
$ minikube ip
```

## Test Vehicle Api 
```bash

# You will observe, we can call service running inside istio-enable-namespace api from non-istio namespace
$ curl http://10.1.10.7:32001/vehicles/
```

# Apply Strict mTLS
```
$ kubectl apply -f strict-mtls-conf.yaml
```

## Test Vehicle Api after Strict mTLS
```bash
# Error after strict mTLS we cant call service running inside istio-enable-namespace api from non-istio namespace
$ curl http://10.1.10.7:32001/vehicles/
curl: (35) error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol

```

## Test from istio-enable-namespace to non-istio-enable-namespace
```
$ kubectl create ns hello
$ kubectl run hello --image=openshift/hello-openshift -n hello
$ kubectl expose pod hello --port=8080  -n hello
$ kubectl get svc -n hello
$ curl <hello-srvice-cluster-ip>:8080
$ kubectl get po
$ kubectl exec -i -t position-tracker-5b767bb48b-tcsxv bash

# From inside position-tracker container call Hello api
$ curl <hello-srvice-cluster-ip>:8080
```

## Clean up task

```
$ kubectl delete ns hello
$ kubectl delete -f .
```
