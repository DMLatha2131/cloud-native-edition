# oxtrust

![Version: 1.6.3](https://img.shields.io/badge/Version-1.6.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 4.3.0](https://img.shields.io/badge/AppVersion-4.3.0-informational?style=flat-square)

Gluu Admin UI. This shouldn't be internet facing.

**Homepage:** <https://gluu.org/docs/gluu-server>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Mohammad Abudayyeh | support@gluu.org | https://github.com/moabu |

## Source Code

* <https://github.com/GluuFederation/docker-oxtrust>
* <https://github.com/GluuFederation/cloud-native-edition/tree/4.3/pygluu/kubernetes/templates/helm/gluu/charts/oxtrust>

## Requirements

Kubernetes: `>=v1.17.0-0`

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| dnsConfig | object | `{}` | Add custom dns config |
| dnsPolicy | string | `""` | Add custom dns policy |
| hpa.behavior | object | `{}` | Scaling Policies |
| hpa.enabled | bool | `true` |  |
| hpa.maxReplicas | int | `10` |  |
| hpa.metrics | list | `[]` | metrics if targetCPUUtilizationPercentage is not set |
| hpa.minReplicas | int | `1` |  |
| hpa.targetCPUUtilizationPercentage | int | `50` |  |
| image.pullPolicy | string | `"IfNotPresent"` | Image pullPolicy to use for deploying. |
| image.repository | string | `"gluufederation/oxtrust"` | Image  to use for deploying. |
| image.tag | string | `"4.3.0_b1"` | Image  tag to use for deploying. |
| livenessProbe | object | `{"exec":{"command":["python3","/app/scripts/healthcheck.py"]},"initialDelaySeconds":30,"periodSeconds":30,"timeoutSeconds":5}` | Configure the liveness healthcheck for the auth server if needed. |
| livenessProbe.exec | object | `{"command":["python3","/app/scripts/healthcheck.py"]}` | Executes the python3 healthcheck. https://github.com/GluuFederation/docker-oxauth/blob/4.3/scripts/healthcheck.py |
| readinessProbe | object | `{"exec":{"command":["python3","/app/scripts/healthcheck.py"]},"initialDelaySeconds":25,"periodSeconds":25,"timeoutSeconds":5}` | Configure the readiness healthcheck for the auth server if needed. https://github.com/GluuFederation/docker-oxauth/blob/4.3/scripts/healthcheck.py |
| replicas | int | `1` | Service replica number. |
| resources | object | `{"limits":{"cpu":"2500m","memory":"2500Mi"},"requests":{"cpu":"2500m","memory":"2500Mi"}}` | Resource specs. |
| resources.limits.cpu | string | `"2500m"` | CPU limit. |
| resources.limits.memory | string | `"2500Mi"` | Memory limit. |
| resources.requests.cpu | string | `"2500m"` | CPU request. |
| resources.requests.memory | string | `"2500Mi"` | Memory request. |
| service.clusterIp | string | `"None"` |  |
| service.name | string | `"http-oxtrust"` | The name of the oxtrust port within the oxtrust service. Please keep it as default. |
| service.oxTrustServiceName | string | `"oxtrust"` | Name of the oxtrust service. Please keep it as default. |
| service.port | int | `8080` | Port of the oxtrust service. Please keep it as default. |
| service.type | string | `"ClusterIP"` |  |
| usrEnvs | object | `{"normal":{},"secret":{}}` | Add custom normal and secret envs to the service |
| usrEnvs.normal | object | `{}` | Add custom normal envs to the service variable1: value1 |
| usrEnvs.secret | object | `{}` | Add custom secret envs to the service variable1: value1 |
| volumeMounts | list | `[]` | Configure any additional volumesMounts that need to be attached to the containers |
| volumes | list | `[]` | Configure any additional volumes that need to be attached to the pod |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)