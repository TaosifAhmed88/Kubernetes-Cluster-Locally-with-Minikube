# 🚀 Kubernetes Deployment using Minikube on AWS EC2

---

## 📌 Objective  
Deploy a sample application on Kubernetes using Minikube, expose it using a Service, and scale pods.

---

## 🛠 Tools Used
- Amazon Linux (AWS EC2)
- Minikube
- Docker
- Kubectl

---

## 📍 Prerequisites on EC2
Before starting Minikube, we installed:
- Docker
- Kubectl
- Minikube
- Required system packages

---

## 🚀 Steps Performed

### 1️⃣ Installed Minikube and Started Cluster
Installed Docker, Kubectl and Minikube on Amazon Linux, then started Minikube using the Docker driver.

**Command:**
```bash
minikube start --driver=docker
✔ Verified the Kubernetes Node
kubectl get nodes

2️⃣ Created Kubernetes Deployment
Created a deployment.yaml file to run an Nginx application with 1 replica.
A Deployment ensures pod management and scaling.

Applied deployment:
kubectl apply -f deployment.yaml

✔ Checked running pods:
kubectl get pods

3️⃣ Exposed Deployment Using Service
Created service.yaml using LoadBalancer type to expose the Nginx application to external traffic.

Applied service:
kubectl apply -f service.yaml

✔ Checked service details:
kubectl get svc

4️⃣ Enabled External Access Using Minikube Tunnel
Minikube runs inside EC2, so minikube tunnel was used to assign an External IP to the LoadBalancer service.
Command:
minikube tunnel
🔎 In another terminal:
kubectl get svc myapp-service

5️⃣ Scaled the Application
Increased number of running replicas from 1 to 3 using scaling.
Command:
kubectl scale deployment myapp-deployment --replicas=3

✔ Verified scaling:
kubectl get pods
