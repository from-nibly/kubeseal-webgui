# Kubeseal-Webgui Helm Chart

* Installs the python based webapp for kubeseal-webgui

## TL;DR

**Clone this repository** and use **helm** to install the kubeseal-webgui

```console
helm template chart/kubeseal-webgui/ | kubectl apply -f - --namespace <namespacename>
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm template --name my-release chart/kubeseal-webgui/ | kubectl apply -f - --namespace <namespacename>
```

## Uninstalling the Chart

To uninstall/delete the my-release deployment:

```console
helm template --name my-release chart/kubeseal-webgui/ | kubectl delete -f - --namespace <namespacename>
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

| Parameter                                 | Description                                     | Default                          |
| ----------------------------------------- | ----------------------------------------------- | -------------------------------- |
| `replicaCount`                            | Number of nodes                                 | `1`                              |
| `annotations`                            | Optional annotations for the pods                                | `{}`                              |
| `image.repository`                        | Image-Repository and name                       | `kubesealwebgui/kubeseal-webgui` |
| `image.tag`                               | Image Tag                                       | `3.1.0`                          |
| `image.pullPolicy`                        | Image Pull Policy                               | `Always`                         |
| `nameOverride`                            | Name-Override for the objects                   | `""`                             |
| `fullnameOverride`                        | Fullname-Override for the objects               | `""`                             |
| `serviceaccount.create`                   | Add serviceaccount for listing namespaces       | `true`                           |
| `displayName`                             | Optional display name for the kubeseal instance | `""`                             |
| `resources.limits.cpu`                    | Limits CPU                                      | `100m`                           |
| `resources.limits.memory`                 | Limits memory                                   | `256Mi`                          |
| `resources.requests.cpu`                  | Requests CPU                                    | `20m`                            |
| `resources.requests.memory`               | Requests memory                                 | `20m`                            |
| `ingress.enabled`                         | Enable an ingress route                         | `false`                          |
| `ingress.annotations`                     | Additional annotations for the ingress object.  | `{}`                             |
| `ingress.ingressClassName`                | Additional ingressClassName.                    | `""`                             |
| `ingress.hostname`                        | The hostname for the ingress route              | `kubeseal-webgui.example.com`    |
| `ingress.tls.enabled`                     | Enable TLS for the ingress route                | `false`                          |
| `ingress.tls.secretName`                  | The secret name for private and public key      | `""`                             |
| `route.enabled`                           | Deploy OpenShift route                          | `false`                          |
| `route.hostname`                          | Set Hostname of the route                       | `""`                             |
| `route.tls.termination`                   | TLS Termination of the route                    | `""`                             |
| `route.tls.insecureEdgeTerminationPolicy` | TLS insecureEdgeTerminationPolicy of the route  | `""`                             |
| `sealedSecrets.autoFetchCert`             | Load the cert from the Controller on start      | `false`                          |
| `sealedSecrets.controllerName`            | Deployment name of the Controller               | `sealed-secrets-controller`      |
| `sealedSecrets.controllerNamespace`       | Namespace the Controller resides in             | `kube-system`                    |
| `sealedSecrets.cert`                      | Public-Key of your SealedSecrets controller     | `""`                             |
| `api.environment`                         | Additional API environment variables            | `{}`                             |
