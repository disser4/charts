# {{ title .Name }} - {{ template "chart.description" . }}

{{ template "chart.deprecationWarning" . }}

{{ template "chart.badgesSection" . }}

<!---
This README.md file is automatically generated with helm-docs!

Edit the README.gotmpl.md template instead.
-->

## TL;DR;

**K8up Documentation**: {{ template "chart.homepage" . }}

```bash
# Install CRDs for K8s >= 1.16:
kubectl apply -f https://github.com/vshn/k8up/releases/download/{{ template "chart.appVersion" . }}/k8up-crd.yaml
# Install CRDs for K8s <= 1.15 (e.g. OpenShift 3.11):
kubectl apply -f https://github.com/vshn/k8up/releases/download/{{ template "chart.appVersion" . }}/k8up-crd-legacy.yaml

helm repo add appuio https://charts.appuio.ch
helm install {{ template "chart.name" . }} appuio/{{ template "chart.name" . }}
```

## Handling CRDs

* Always upgrade the CRDs before upgrading the Helm release.
* Watch out for breaking changes in the {{ title .Name }} release notes.

{{ template "chart.sourcesSection" . }}

{{ template "chart.requirementsSection" . }}
<!---
The values below are generated with helm-docs!

Document your changes in values.yaml and let `make helm-docs` generate this section.
-->
{{ template "chart.valuesSection" . }}

## Upgrading from Charts 0.x to 1.x

* In `image.repository` the registry domain was moved into its own parameter `image.registry`.
* K8up 1.x features leader election, this enables rolling updates and multiple replicas.
  `k8up.enableLeaderElection` defaults to `true`. Disable this for older Kubernetes versions (<= 1.15)
* `replicaCount` is now configurable, defaults to `1`.
* Note: Deployment strategy type has changed from `Recreate` to `RollingUpdate`.
* CRDs need to be installed separately, they are no longer included in this chart.

<!---
Link references from values.yaml
-->
[supported-units]: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-units-in-kubernetes
[prometheus-operator]: https://github.com/coreos/prometheus-operator
