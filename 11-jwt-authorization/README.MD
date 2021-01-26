# Istio HTTP Authorization

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

## Navigate to 11-jwt-authorization
```
$ cd learn-istio/11-jwt-authorization
```

## Deploy Sample Hello World App
```bash
$ kubectl apply -f 1-deployment.yaml
```

## Get service
```bash
$ kubectl get svc
```

## Access application

```bash

$ curl http://<service-cluster-ip>:8080
Hello Openshift V1

```


## Apply requestauthentication & authorizationpolicy.
```base
$ kubectl apply -f 2-request-authenticator.yaml
requestauthentication.security.istio.io/jwt-example created

$ kubectl apply -f 3-auth-policy.yaml
authorizationpolicy.security.istio.io/require-jwt created
```

## Try to access application without token
```base

$ curl <service-cluster-ip>:8080
RBAC: access denied
```


## Generate Token
```bash
$ TOKEN=$(curl https://raw.githubusercontent.com/istio/istio/release-1.8/security/tools/jwt/samples/demo.jwt -s) && echo "$TOKEN" | cut -d '.' -f2 - | base64 --decode -
{"exp":4685989700,"foo":"bar","iat":1532389700,"iss":"testing@secure.istio.io","sub":"testing@secure.istio.io"}
```

## Access app by passing token as header
```
$ curl -H "Authorization: Bearer $TOKEN"  1<service-cluster-ip>:8080
Hello Openshift V1

```

##Clean up
``` bash
$ kubectl delete all --all
```
