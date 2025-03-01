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

![Screenshot 2025-03-02 at 12 13 58 AM](https://github.com/user-attachments/assets/f468b706-2fa5-4f59-9d57-9422302cb314)
