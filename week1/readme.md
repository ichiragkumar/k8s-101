create a clusters.yml file

```yml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
```



create kind cluster now

```shell
kind create cluster --config clusters.yml --name local
```



verify with docker ps

docker ps