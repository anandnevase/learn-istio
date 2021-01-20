# Installation Steps for Minikube

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
$ cd learn-istio/1-install-istio/
```

## Create IStio CRD's

```bash
$ ls
1-istio-init.yaml  2-istio-minikube.yaml  3-kiali-secret.yaml  4-label-default-namespace.yaml

$ kubectl apply -f 1-istio-init.yaml
namespace/istio-system unchanged
Warning: apiextensions.k8s.io/v1beta1 CustomResourceDefinition is deprecated in v1.16+, unavailable in v1.22+; use apiextensions.k8s.io/v1 CustomResourceDefinition
customresourcedefinition.apiextensions.k8s.io/authorizationpolicies.security.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/destinationrules.networking.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/envoyfilters.networking.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/gateways.networking.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/istiooperators.install.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/peerauthentications.security.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/requestauthentications.security.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/serviceentries.networking.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/sidecars.networking.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/virtualservices.networking.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/workloadentries.networking.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/workloadgroups.networking.istio.io unchanged
customresourcedefinition.apiextensions.k8s.io/monitoringdashboards.monitoring.kiali.io unchanged
```

## Install Istio and its Add-ons

```bash
$ kubectl apply -f 2-istio-minikube.yaml
serviceaccount/istio-egressgateway-service-account unchanged
serviceaccount/istio-ingressgateway-service-account unchanged
serviceaccount/istio-reader-service-account unchanged
serviceaccount/istiod-service-account unchanged
clusterrole.rbac.authorization.k8s.io/istio-reader-istio-system unchanged
clusterrole.rbac.authorization.k8s.io/istiod-istio-system unchanged
clusterrolebinding.rbac.authorization.k8s.io/istio-reader-istio-system unchanged
clusterrolebinding.rbac.authorization.k8s.io/istiod-istio-system unchanged
Warning: admissionregistration.k8s.io/v1beta1 ValidatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 ValidatingWebhookConfiguration
validatingwebhookconfiguration.admissionregistration.k8s.io/istiod-istio-system configured
envoyfilter.networking.istio.io/metadata-exchange-1.6 unchanged
envoyfilter.networking.istio.io/metadata-exchange-1.7 unchanged
envoyfilter.networking.istio.io/metadata-exchange-1.8 unchanged
envoyfilter.networking.istio.io/stats-filter-1.6 unchanged
envoyfilter.networking.istio.io/stats-filter-1.7 unchanged
envoyfilter.networking.istio.io/stats-filter-1.8 unchanged
envoyfilter.networking.istio.io/tcp-metadata-exchange-1.6 unchanged
envoyfilter.networking.istio.io/tcp-metadata-exchange-1.7 unchanged
envoyfilter.networking.istio.io/tcp-metadata-exchange-1.8 unchanged
envoyfilter.networking.istio.io/tcp-stats-filter-1.6 unchanged
envoyfilter.networking.istio.io/tcp-stats-filter-1.7 unchanged
envoyfilter.networking.istio.io/tcp-stats-filter-1.8 unchanged
configmap/istio unchanged
configmap/istio-sidecar-injector unchanged
Warning: admissionregistration.k8s.io/v1beta1 MutatingWebhookConfiguration is deprecated in v1.16+, unavailable in v1.22+; use admissionregistration.k8s.io/v1 MutatingWebhookConfiguration
mutatingwebhookconfiguration.admissionregistration.k8s.io/istio-sidecar-injector configured
deployment.apps/istio-egressgateway configured
deployment.apps/istio-ingressgateway configured
deployment.apps/istiod configured
poddisruptionbudget.policy/istio-egressgateway unchanged
poddisruptionbudget.policy/istio-ingressgateway unchanged
poddisruptionbudget.policy/istiod unchanged
role.rbac.authorization.k8s.io/istio-egressgateway-sds unchanged
role.rbac.authorization.k8s.io/istio-ingressgateway-sds unchanged
role.rbac.authorization.k8s.io/istiod-istio-system unchanged
rolebinding.rbac.authorization.k8s.io/istio-egressgateway-sds unchanged
rolebinding.rbac.authorization.k8s.io/istio-ingressgateway-sds unchanged
rolebinding.rbac.authorization.k8s.io/istiod-istio-system unchanged
service/istio-egressgateway unchanged
service/istio-ingressgateway unchanged
service/istiod unchanged
serviceaccount/prometheus unchanged
configmap/prometheus unchanged
clusterrole.rbac.authorization.k8s.io/prometheus unchanged
clusterrolebinding.rbac.authorization.k8s.io/prometheus unchanged
service/prometheus unchanged
deployment.apps/prometheus configured
serviceaccount/grafana unchanged
configmap/grafana unchanged
service/grafana unchanged
deployment.apps/grafana configured
configmap/istio-grafana-dashboards configured
configmap/istio-services-grafana-dashboards configured
deployment.apps/jaeger unchanged
service/tracing unchanged
service/zipkin unchanged
service/jaeger-collector unchanged
serviceaccount/kiali unchanged
configmap/kiali unchanged
clusterrole.rbac.authorization.k8s.io/kiali-viewer unchanged
clusterrole.rbac.authorization.k8s.io/kiali unchanged
clusterrolebinding.rbac.authorization.k8s.io/kiali unchanged
service/kiali unchanged
deployment.apps/kiali unchanged
monitoringdashboard.monitoring.kiali.io/envoy unchanged
monitoringdashboard.monitoring.kiali.io/go unchanged
monitoringdashboard.monitoring.kiali.io/kiali unchanged
monitoringdashboard.monitoring.kiali.io/micrometer-1.0.6-jvm-pool unchanged
monitoringdashboard.monitoring.kiali.io/micrometer-1.0.6-jvm unchanged
monitoringdashboard.monitoring.kiali.io/micrometer-1.1-jvm unchanged
monitoringdashboard.monitoring.kiali.io/microprofile-1.1 unchanged
monitoringdashboard.monitoring.kiali.io/microprofile-x.y unchanged
monitoringdashboard.monitoring.kiali.io/nodejs unchanged
monitoringdashboard.monitoring.kiali.io/quarkus unchanged
monitoringdashboard.monitoring.kiali.io/springboot-jvm-pool unchanged
monitoringdashboard.monitoring.kiali.io/springboot-jvm unchanged
monitoringdashboard.monitoring.kiali.io/springboot-tomcat unchanged
monitoringdashboard.monitoring.kiali.io/thorntail unchanged
monitoringdashboard.monitoring.kiali.io/tomcat unchanged
monitoringdashboard.monitoring.kiali.io/vertx-client unchanged
monitoringdashboard.monitoring.kiali.io/vertx-eventbus unchanged
monitoringdashboard.monitoring.kiali.io/vertx-jvm unchanged
monitoringdashboard.monitoring.kiali.io/vertx-pool unchanged
monitoringdashboard.monitoring.kiali.io/vertx-server unchanged
```

## Create label for automatic istio sidecar injection
```
$ kubectl apply -f 4-label-default-namespace.yaml
namespace/default changed
```