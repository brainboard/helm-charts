# Brainboard self hosted runner chart

![Version: 1.0.3](https://img.shields.io/badge/Version-1.0.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.0.0](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

Helm chart to deploy Brainboard self hosted runner

## Installation

```sh
helm repo add brainboard https://brainboard.github.io/helm-charts/
helm install runner brainboard/brainboard-runner
```

## Configuration

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| additionalLabels | object | `{}` |  |
| affinity | object | `{}` | Affinity for pod assignment https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity |
| config.api.endpoint | string | `"https://api.us1.brainboard.co"` | brainboard API url |
| config.concurrency | int | `4` | maximum number of concurrent jobs |
| config.credentials.existingSecretName | string | `""` | name of an existing kubernetes secret containing RUNNER_TOKEN environment variable value if this is set, credentials.token value is ignored |
| config.credentials.token | string | `"changeme"` | runner token generated in Brainboard Private selfhosted runner settings |
| config.job_max_execution_time | string | `""` | maximum job execution time, in minutes - EX: 60. Leave empty for no limit |
| config.logLevel | string | `"info"` |  |
| config.max_job_wait_time | string | `"1s"` | maximum time to wait before starting a job - minimum=100ms |
| config.name | string | `"brainboard-runner"` | Name of the runner |
| config.plugins.ecr.aws_region | string | `""` | AWS ECR registry region |
| config.plugins.ecr.enabled | bool | `false` | Set this value to true if you host runner plugins in AWS ECR registry |
| config.plugins.registry | string | `"registry.gitlab.com/brainboard/plugins"` |  |
| config.poll_interval | int | `10` | interval between each runner API request to check for new jobs |
| dind.image.pullPolicy | string | `"IfNotPresent"` |  |
| dind.image.repository | string | `"docker"` |  |
| dind.image.tag | string | `"23.0.2-dind"` |  |
| dind.resources.requests.cpu | string | `"10m"` |  |
| dind.resources.requests.memory | string | `"128Mi"` |  |
| extraVolumeMounts | list | `[]` | Extra volume mounts to be added in addition to the default VolumeMounts |
| extraVolumes | list | `[]` | Extra volumes to be added in addition to the default Volumes |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"ghcr.io/brainboard/runner"` |  |
| image.tag | string | `"latest"` |  |
| initContainers | list | `[]` | Additional custom init containers |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` | nodeSelector to apply for pod assignment https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/ |
| resources.requests.cpu | string | `"10m"` |  |
| resources.requests.memory | string | `"128Mi"` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `nil` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations | list | `[]` | Tolerations for pod assignment https://kubernetes.io/docs/concepts/configuration/taint-and-toleration/ |