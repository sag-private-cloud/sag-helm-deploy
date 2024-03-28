# webMethods Helm Chart Deploy GitHub Action
Github Action for deploying (installing/upgrading) webMethods Helm Charts

## Usage
| Setting        | Default value           | Description  |
| :-------------: | :-------------: | ------------- |
| release-name      |  | The name of the release to deploy |
| helm-chart      |  | The name of the Helm chart to deploy |
| namespace      |  | The namespace of the deployment |
| values-file      |  | Values file path to pass to the Helm command |
| extra-args      |  | Extra arguments to pass to the Helm command |
| docker-registry      |  | The docker registry server for which a docker-registry Kubernetes secret will be created. If not provided, such secret will not be created |
| docker-registry-secret-name      | regcred | The docker registry secret name. |
| docker-username      |  | The docker registry username |
| docker-password      |  | The docker registry password |

## Example

```yml
- name: Deploy solution
  uses: sag-private-cloud/sag-helm-deploy@v3
  with: 
    release-name: "my-release"
    helm-chart: webMethods/microservices-runtime
    docker-registry: ${{ secrets.DOCKER_REGISTRY }}
    docker-username: ${{ secrets.DOCKER_USER }}
    docker-password: ${{ secrets.DOCKER_PASSWORD }}
    values-file: ${{ github.workspace }}/custom/values.yaml
    extra-args: >- 
      --set "my.prop=my.value"
      --set "my.second.prop=my.second.value" 
```
