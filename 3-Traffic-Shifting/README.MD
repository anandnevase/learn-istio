# Istio Traffic Shifting Demo

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
$ cd learn-istio/3-Traffic-Solution
```

## Deploy Sample App
```bash
$ kubectl apply -f application-no-istio.yaml
```

## Get minikube IP
```bash
$ minikube ip
```

## Observer Graph in Kiali
  Kiali     :   <minikube-ip>:31000

## Deploy Safe and Risky Version for staffing service
```bash
# Delete load deployment
$ kubectl apply -f application-no-istio.yaml

# Deploy fresh apps again
$ kubectl apply -f application-no-istio-safe-risky.yaml
```

## Apply Istio  rules 
Note : Same can be done by Kiali - in that case below Virtual Service and Destination Rule created by Kiali

```bash
$ kubectl apply -f istio-rules.yaml
```
