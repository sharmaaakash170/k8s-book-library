# 📚 Kubernetes 3-Tier Book Library Manager

## 🚀 Project Overview
This repository demonstrates a **full 3-tier microservices application** running on Kubernetes.  
Built with:
- **Frontend**: React + NGINX
- **Backend**: FastAPI (Python)
- **Database**: MongoDB (secure, root user)
- **Monitoring**: Prometheus & Grafana
- **Autoscaling**: Kubernetes HPA

---

## 🎯 Key Features
- **CRUD** operations on books (list, add, delete)
- **Secure MongoDB** with Kubernetes Secrets
- **Multi-stage Docker builds** for production-ready images
- **End-to-end monitoring**: metrics scraped and visualized
- **Horizontal Pod Autoscaler (HPA)** reacts to real workload
- **NodePort** services for local access without cloud LB
- **Easy local testing** with Docker Desktop Kubernetes

---

## 📂 Repository Structure
```
k8s-book-library/
├── backend/
│   ├── app/
│   │   └── main.py
│   ├── Dockerfile
│   ├── requirements.txt
│   ├── deployment.yaml
│   ├── service.yaml
│   └── hpa.yaml
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── index.js
│   │   └── App.js
│   ├── Dockerfile
│   ├── deployment.yaml
│   └── service.yaml
│
├── database/
│   ├── mongodb-secret.yaml
│   ├── deployment.yaml
│   └── service.yaml
│
├── monitoring/
│   ├── prometheus-config.yaml
│   ├── deployment.yaml
│   └── service.yaml
│
└── README.md  ← (this file)
```

---

## 🔧 Prerequisites
- Docker Desktop with Kubernetes enabled
- `kubectl` CLI configured
- Node.js & npm (for local builds if needed)
- Python 3.11+

---

## ⚡️ Quick Start

1. **Database**  
   ```bash
   kubectl apply -f database/
   ```

2. **Backend**  
   ```bash
   docker build -t youruser/book-backend:latest backend/
   kubectl apply -f backend/
   ```

3. **Frontend**  
   ```bash
   docker build -t youruser/book-frontend:latest frontend/
   kubectl apply -f frontend/
   ```

4. **Monitoring**  
   ```bash
   kubectl apply -f monitoring/
   ```

5. **Access the App**  
   - **Frontend UI**: http://localhost:32098  
   - **API Health**: http://localhost:32080/books  
   - **Prometheus**: http://localhost:32024  
   - **Grafana**: http://localhost:31497

---

## 🌟 Show HPA in Action
Generate load and watch pods scale:
```bash
for i in {1..50}; do while true; do curl -s http://localhost:32080/books > /dev/null; done & done; sleep 180
kubectl get hpa -w
```

---

## 🙌 Contributing
Feel free to open issues, submit pull requests, or connect with me for enhancements!

---

## 📬 Contact & Careers
I'm passionate about DevOps, Cloud Native, and Kubernetes.  
🇦🇺 **Open to opportunities** in Australia and worldwide.  
Connect with me on LinkedIn!

---

## 📜 License
MIT © 2025

