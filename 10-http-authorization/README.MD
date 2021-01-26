# Authorization for HTTP traffic

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

## Navigate to 10-http-authorization
```
$ cd learn-istio/10-http-authorization
```

## Deploy Sample Book-Info APP
```bash
$ kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.8/samples/bookinfo/platform/kube/bookinfo.yaml
```

## Create book-info gateway
```bash
$ kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.8/samples/bookinfo/networking/bookinfo-gateway.yaml

$ kubectl get gateway
NAME               AGE
bookinfo-gateway   32s

$ export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT
```

## Access application in browser

```bash

URL   - http://$GATEWAY_URL/productpage

```

# Apply policy 
```bash
# By running below policy, we can't able to load productpage
$ kubectl apply -f 1-deny-all.yaml           

# By running below policy, we can able to load productpage
# But you can see other services
$ kubectl apply -f  2-productpage-viewer.yaml

# Detail page will load
$ kubectl apply -f 3-details-viewer.yaml  

# Review Page will load
$ kubectl apply -f 4-reviews-viewer.yaml

# We can see rating as well
$ kubectl apply -f 5-rating-viewer.yaml


```
