# 📦 Deploying a React Todo List App on Kubernetes with Minikube 🚀

This guide walks you through running a **React Todo List Application** on **Kubernetes (K8s)** using **Minikube** and **Docker driver**. Perfect for beginners exploring Kubernetes service deployment and port forwarding.  

---

## 🛠 Step-by-Step Guide

### 1️⃣ Start Minikube Cluster with Docker Driver 🐳
```bash
minikube start --driver=docker
```
*Starts your local Kubernetes cluster using Docker as the container runtime.*

---

### 2️⃣ Verify Your Nodes 📋
```bash
kubectl get nodes
```
*Checks if your Minikube node is up and running.*

---

### 3️⃣ Deploy the React Todo List App 📥
```bash
kubectl run todolistapp --image=kubekode/react-todo-list-app
```
*Creates a pod named `todolistapp` using the provided React app image.*

---

### 4️⃣ Check Pod Status ✅
```bash
kubectl get pods
```
*Ensures the pod is running and ready.*

---

### 5️⃣ Expose the Pod as a Service 🌐
```bash
kubectl expose pod todolistapp --type=NodePort --port=80 --name=todolistapp-service
```
*Makes your application accessible by creating a NodePort service on port 80.*

---

### 6️⃣ List All Services 🗂
```bash
kubectl get svc
```
*Displays all active services in your cluster.*

---

### 7️⃣ Get Service Access URL via Minikube 🔗
```bash
minikube service todolistapp-service --url
```
*Shows the Minikube URL for accessing the app, e.g.:*  
`http://<MINIKUBE-IP>:<NODE-PORT>`

---

### 8️⃣ Test the App Using curl 🧪
```bash
curl http://<MINIKUBE-IP>:<NODE-PORT>
```
*Checks if your application is responding.*

---

### 9️⃣ Forward Service Port to Your Machine 🔄
```bash
kubectl port-forward svc/todolistapp-service 3000:80 --address 0.0.0.0 &
```
*Maps your local machine's port `3000` to the app's port `80` so it’s accessible externally.*

---

### 🔟 Configure EC2 Security Group (if running on cloud) ☁️
- Edit inbound rules in your EC2 security group.  
- Allow **TCP traffic** on **port 3000** from **`0.0.0.0/0` (Anywhere)**.

---

### 1️⃣1️⃣ Access Your App in Browser 🌍
```
http://<EC2-IP>:3000
```
*Replace `<EC2-IP>` with your actual EC2 instance public IP.*  
💡 Example: `http://54.123.45.67:3000`  

You should now see your **React Todo List App** running successfully! 🎉
