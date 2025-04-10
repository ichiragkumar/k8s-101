## 🚀 Docker: Run NGINX Locally
```bash
docker run -p 3000:80 nginx
```
- Runs an NGINX container.
- Maps container port `80` → host port `3000`.

---

## ☸️ Kubernetes with `kind` (Kubernetes IN Docker)

### ✅ Create Clusters
```bash
kind create cluster --name kind-cluster
kind create cluster --name sunday
```

---

## 📦 Creating Pods

### ✅ Run Pods from CLI
```bash
kubectl run moongo-pod --image=nginx --port=80
kubectl run nginx-pod --image=nginx --port=80
```

### ❌ Delete Pods
```bash
kubectl delete pod moongo-pod
kubectl delete pod nginx-pod
```

---

## 📄 Deployments

### ✅ Apply a Deployment Manifest
```bash
kubectl apply -f deployment.yml
```

### 🧠 Learn About Deployments
```bash
kubectl explain deployment
```

### 🔍 Get All Deployments
```bash
kubectl get deployments
```

### 🔍 Get All Pods (including ones created by deployments)
```bash
kubectl get pods
```

### ❌ Delete a Pod from Deployment
```bash
kubectl delete pod <pod-name>
```
- The **Deployment will automatically recreate it** to maintain desired replica count.

### 🔍 Get ReplicaSets (created by Deployment)
```bash
kubectl get replicasets
```

### ❌ Delete Deployment (and everything it created)
```bash
kubectl delete deployment nginx-deployment
```

> 📝 **Important Concepts:**
>
> 1. **Deployment** creates and manages **ReplicaSet**
> 2. **ReplicaSet** creates and maintains **Pods**
> 3. Deleting a Deployment will delete:
>    - the Deployment itself
>    - its associated ReplicaSet
>    - the Pods managed by that ReplicaSet

---

## 🔁 ReplicaSet (without Deployment)

### ✅ Apply a ReplicaSet YAML
```bash
kubectl apply -f replicaset.yml
```

Example output:
```bash
replicaset.apps/nginx-replicaset created
```

### 🔍 View ReplicaSets
```bash
kubectl get rs
```

Example output:
```bash
NAME               DESIRED   CURRENT   READY   AGE
nginx-replicaset   3         3         3       10s
```

> ✔️ **Yes, a ReplicaSet also creates and manages Pods**  
> ❌ **But it does not support rolling updates, rollback, etc. like a Deployment does**

### ⚠️ Common Misconception

> “If you delete the ReplicaSet, the Pods will not be deleted” — ❌ **Incorrect**

Actually:
- **Pods will be deleted**, because they are **owned by the ReplicaSet** (via `ownerReferences`).
- You can verify this with:
  ```bash
  kubectl get pods -o wide
  ```

---

## 🎯 Summary

| Object        | Manages         | Can Be Used Alone | Supports Rollout | Deletes Pods on Deletion |
|---------------|------------------|-------------------|------------------|---------------------------|
| Pod           | —                | ✅ Yes            | ❌ No            | ✅ Yes                    |
| ReplicaSet    | Pods             | ✅ Yes            | ❌ No            | ✅ Yes                    |
| Deployment    | ReplicaSet → Pods| ✅ Yes            | ✅ Yes           | ✅ Yes                    |

