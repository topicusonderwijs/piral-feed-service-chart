# Piral Feed Service Helm Chart

Chart version: `0.3.0`
Status: `beta`

## Introduction

This chart bootstraps a **Feed Service deployment** to a Kubernetes Cluster using the Helm package manager. The specific configuration values will be added to a config map and will be injected as environment variables into the pod, which executes the Feed Service. The sensitive values are injected via Kubernetes secrets.

**Remark:** This Helm chart version supports version `1.13.3` of the Feed Service.

Additional configuration options can be configured via environment variables, which can be added as required in section `extendedConfig` in the `values.yaml` file.

For the description of all configuration settings, please visit the Feed Service online documentation: 
 - [Configuration of the Docker Image (Free Version)](https://docs.piral.cloud/setup/03-configuration-free)
 - [Configuration of the Docker Image (Pro Version)](https://docs.piral.cloud/setup/03-configuration-pro).

## Getting started

The deployment parameters can be configured via the `values.yaml` file. For getting started the following steps need to be executed:

1. In case the Feed Service docker image will be pulled directly from the Piral Cloud Azure Container Registry (ACR), a corresponding **image pull secret** with the name `feed-service-pull-secret` must be created including the provided credentials for the ACR. See [Pull an Image from a Private Registry](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry) for further details.

2. The provided **license key** for executing the Feed Service must be added in section `license` to the property `licenseKey`. When using a K8s secret, the license key must be added as value with the key `PIRAL_LICENSE_KEY`.

3. Provide an **administrator password** for the local authentication in section `authentication` using the property `local.password`. When using a K8s secret for the credentials, the username and password must be added with the keys `PIRAL_AUTH_LOCAL_USER` and `PIRAL_AUTH_LOCAL_PASS`.

4. Install the service using `helm`:

    ```sh
    helm install feed-service . 
    ```

## Further Reading

Further information regarding the configuration of the Piral Feed Service and a tutorial for the deployment of the service to a Kubernetes cluster can be found in the online documentation: [Piral Cloud Docs](https://docs.piral.cloud).

## License

The Helm chart is released using the MIT license. For more information see the [license file](./LICENSE).
