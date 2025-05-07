# Kubernetes Deployment Examples (Improved – kubeadm Cluster)

## 📌 Purpose
This project demonstrates a more production-ready deployment of a three-tier application on a Kubernetes cluster installed via **kubeadm**. It includes frontend, backend, and database components with best practices like liveness probes, resource limits, and persistent volumes.

---

## ⚙️ Technologies Used

- Kubernetes (kubeadm cluster)
- Docker
- YAML manifests
- NGINX, Python HTTP server
- MySQL 8.0

---

## 📁 Project Structure

```
kubernetes-deployment-updated/
├── manifests/
│   ├── namespace.yaml
│   ├── frontend-deployment.yaml
│   ├── frontend-service.yaml
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── mysql-deployment.yaml
│   ├── mysql-service.yaml
│   └── mysql-pvc.yaml
└── README.md
```

---

## 🚀 Deployment Order

Apply the manifests in the following order:

```bash
kubectl apply -f manifests/namespace.yaml
kubectl apply -f manifests/mysql-pvc.yaml
kubectl apply -f manifests/mysql-deployment.yaml
kubectl apply -f manifests/mysql-service.yaml
kubectl apply -f manifests/backend-deployment.yaml
kubectl apply -f manifests/backend-service.yaml
kubectl apply -f manifests/frontend-deployment.yaml
kubectl apply -f manifests/frontend-service.yaml
```

---

## 📡 Access

The frontend is exposed via NodePort at port `30080`. Access it via:

```
http://<NodeIP>:30080
```

---

## 🧩 Component Summary

- `frontend`: NGINX container with liveness probe
- `backend`: Python HTTP server with liveness probe
- `mysql`: MySQL with persistent storage (`PersistentVolumeClaim`)
- All components include basic resource limits

---

## 👤 Author

Erkan Baran  
[GitHub](https://github.com/ErkanBarann) · [Portfolio](https://www.erkanbaran.me)
