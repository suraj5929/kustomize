# Kustomize – Base & Overlays Example

This repository demonstrates a clean folder structure for managing Kubernetes manifests using **Kustomize**.  
It follows the recommended pattern of keeping reusable configuration in the **base** directory and environment-specific customizations in **overlays**.

---





---

## ✅ Purpose

- Manage Kubernetes manifests using Kustomize layering  
- Keep YAML DRY and reusable  
- Override configuration per environment (dev/stage/prod)  
- Demonstrate how patches modify base manifests

---

## 🚀 Usage

### Apply base  
```
kubectl apply -k base/
```


### Apply dev environment  
```
kubectl apply -k overlays/dev/
```


### Apply stage environment  
```
kubectl apply -k overlays/stage/
```


---

## 🛠️ Common Customizations in Overlays

- Replica count changes  
- Image overrides  
- ConfigMap/Secret updates  
- Resource limits  
- Ingress available only in prod  
- Environment-specific labels/annotations  
- EKS IAM role (IRSA) annotations  

Example patch file:

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3

 ```

📚 Kustomize Commands

Build manifest output:

````
kustomize build overlays/dev
````

View diff between environments:
```
diff <(kustomize build overlays/dev) <(kustomize build overlays/prod)
```

Validate before applying:

```
kubectl diff -k overlays/dev
```

🧑‍💻 Author
Suraj Jadhav









