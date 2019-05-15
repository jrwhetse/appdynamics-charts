# AppDynamics

AppDynamics is an application intelligence platform that provides end-to-end visibility into performance of business-critical applications.
This chart deploys AppDynamics MachineAgent Daemonset to the cluster.

## Prerequisites

* Kubernetes 1.7+ OpenShift 3.7+
* Helm and tiller installed in the cluster with the appropriate RBAC settings

## Quick start

To install the chart run. the following command:

```
helm install stable/appdynamics-agent \
--set controller.accessKey=5a8a4d47-78a8-40d6-8b07-1a4f90c51789 \
--set controller.host=tenant.saas.appdynamics.com
--set controller.accountName=<accountName>
--set controller.globalAccountName=<globalAccountName>

```

## Configuration settings

| Parameter                 | Description                                                  | Default                    |
| ------------------------- | ------------------------------------------------------------ | -------------------------- |
| `controller.host`                 | Host name of AppDynamics controller                 |                          |
| `controller.port`              | Appdynamics Controller port number | `443`|
| `controller.ssl`                  | Use ssl to connect to AppDynamics controller                |   `true`                      |
| `controller.accountName`     | AppDynamics account name | customer1
| `controller.globalAccountName` | AppDynamics global account name | |
| `controller.accessKey`             | Access key to the AppDynamics controller                             |                     |
| `agent.simEnabled`         | Infrastructure monitoring enabled                          | `true`                    |
| `agent.dockerEnabled`             | Container monitoring enabled                                       | `true`  |
| `agent.logLevel`        | Agent logging level                                             | `info`             |
| `agent.stdoutLogging`               | Send logging to console                        | `false`            |
| `agent.hierarchyPath`               | Path of host names in AppDynamics controller                 |      |
| `agent.uniqueHostId`              | Unique host id override                   |                  |
| `agent.metricsLimit`            | Max number of metrics accepted by the controller from the agent                             | `2000`                      |
| `agent.proxyHost`             | Proxy host name |                      |
| `agent.proxyPort`          | Proxy host name |            |
| `agent.proxyUser`             | Proxy username               |         
| `agent.proxyPass`             | Proxy password                  |
| `analytics.eventEndpoint`     | Analytics service endpoint   | `https://analytics.api.appdynamics.com/`
| `analytics.port`             | Analytics service port       | 
| `serviceAccount.create`       | Flag indicating that the service account will be created | `true`
| `serviceAccount.name`       | Service account name.   | appdynamics-infraviz
| `rbac.create`            | Flag indicating that the roles for the service account will be created | `true`
| `openshift.scc`    | Should create scc for the service account. | `false`
| `daemonset.image.repository` | Name of the machine agent image | `docker.io/appdynamics/machine-agent-analytics`
| `daemonset.image.tag` | Tag of the machine agent image | `docker.io/appdynamics/latest`
| `daemonset.image.pullPolicy` | The machine agent image pull policy| `IfNotPresent`
| `daemonset.nodeSelector` | Node selector directive |
| `daemonset.tolerations ` | Tolerations directive |
| `daemonset.resources ` | Resources directive  | See below


Example resource limits:

```
   resources:
    limits:
      cpu: 600m
      memory: "1G"
    requests: 
      cpu: 300m
      memory: "800M"
```



 