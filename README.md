# Kustomize – Base & Overlays Example

This repository demonstrates a clean folder structure for managing Kubernetes manifests using **Kustomize**.  
It follows the recommended pattern of keeping reusable configuration in the **base** directory and environment-specific customizations in **overlays**.

---

## 📁 Folder Structure

kustomize/
├── base/
│ ├── kustomization.yaml
│ └── (base manifests)
└── overlays/
├── dev/
│ ├── kustomization.yaml
│ └── (patches for dev)
├── stage/
└── prod/

yaml
Copy code

---

## ✅ Purpose

- Manage Kubernetes manifests using Kustomize layering  
- Keep YAML DRY and reusable  
- Override configuration per environment (dev/stage/prod)  
- Demonstrate how patches modify base manifests

---

## 🚀 Usage

### Apply base  
kubectl apply -k base/

bash
Copy code

### Apply dev environment  
kubectl apply -k overlays/dev/

bash
Copy code

### Apply prod environment  
kubectl apply -k overlays/prod/

yaml
Copy code

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

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
📚 Kustomize Commands
Build manifest output:

bash
Copy code
kustomize build overlays/dev
View diff between environments:

bash
Copy code
diff <(kustomize build overlays/dev) <(kustomize build overlays/prod)
Validate before applying:

bash
Copy code
kubectl diff -k overlays/dev
🧑‍💻 Author
Suraj Jadhav
DevOps • AWS • Kubernetes • Terraform • Jenkins

yaml
Copy code

---

If you want, I can also generate:

✅ Base Deployment + Service  
✅ Dev/Prod overlays  
✅ Best practices for EKS  
✅ Jenkins pipeline using `kubectl apply -k`  

Just tell me!






