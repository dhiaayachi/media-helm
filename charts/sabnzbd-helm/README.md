# Sabnzbd Software Media System

This is a helm chart for [Sabnzbd](https://github.com/sabnzbd/sabnzbd/)

## Prerequisites

- Kubernetes 1.19+
- Helm 3+

## TL;DR;

```shell
$ git clone https://github.com/brianmcarey/sabnzbd-helm.git
$ helm install ./sabnzbd-helm
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
git clone https://github.com/brianmcarey/sabnzbd-helm.git
helm install  my-release ./sabnzbd-helm
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Sabnzbd chart and their default values.

| Parameter                  | Description                         | Default                                                 |
|----------------------------|-------------------------------------|---------------------------------------------------------|
| `image.repository`         | Image repository | `docker.io/sabnzbd/sabnzbd` |
| `image.tag`                | Image tag. Possible values listed [here](https://hub.docker.com/r/sabnzbd/sabnzbd/tags/).| `latest`|
| `image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `Service.type`          | Kubernetes service type for the sabnzbd GUI | `ClusterIP` |
| `Service.port`          | Kubernetes port where the sabnzbd GUI is exposed| `8096` |
| `Service.annotations`   | Service annotations for the sabnzbd GUI | `{}` |
| `Service.labels`        | Custom labels | `{}` |
| `Service.loadBalancerIP` | Loadbalance IP for the sabnzbd GUI | `{}` |
| `Service.loadBalancerSourceRanges` | List of IP CIDRs allowed access to load balancer (if supported)      | None
| `ingress.enabled`              | Enables Ingress | `false` |
| `ingress.annotations`          | Ingress annotations | `{}` |
| `ingress.labels`               | Custom labels                       | `{}`
| `ingress.path`                 | Ingress path | `/` |
| `ingress.hosts`                | Ingress accepted hostnames | `chart-example.local` |
| `ingress.tls`                  | Ingress TLS configuration | `[]` |
| `persistence.config.enabled`      | Use persistent volume to store configuration data | `false` |
| `persistence.config.size`         | Size of persistent volume claim | `1Gi` |
| `persistence.config.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.config.storageClass` | Type of persistent volume claim | `-` |
| `persistence.config.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.media.enabled`      | Use persistent volume to store configuration data | `true` |
| `persistence.media.size`         | Size of persistent volume claim | `10Gi` |
| `persistence.media.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.media.storageClass` | Type of persistent volume claim | `-` |
| `persistence.media.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.extraExistingClaimMounts`  | Optionally add multiple existing claims | `[]` |
| `resources`                | CPU/Memory resource requests/limits | `{}` |
| `nodeSelector`             | Node labels for pod assignment | `{}` |
| `tolerations`              | Toleration labels for pod assignment | `[]` |
| `affinity`                 | Affinity settings for pod assignment | `{}` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Read through the [values.yaml](values.yaml) file. It has several suggested values.
