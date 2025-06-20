# 🧠 Brain Tasks App – Full-Stack DevOps Deployment 🚀

A production-grade deployment of the **Brain Tasks React App** using **Docker**, **AWS ECR**, **AWS CodePipeline**, **CodeBuild**, **Kubernetes on EKS**, and **CloudWatch monitoring**.

---

## 🛠️ Tech Stack

* **Frontend:** React
* **Containerization:** Docker
* **CI/CD:** AWS CodePipeline + CodeBuild
* **Image Registry:** AWS ECR
* **Orchestration:** Kubernetes (EKS)
* **Monitoring:** CloudWatch
* **Infra:** EC2, IAM, EKS, S3

---

## 📂 Folder Structure

```
.
├── Dockerfile
├── buildspec.yml
├── manifests/
│   ├── deployment.yaml
│   └── service.yaml
├── Brain-Task-Output/
│   └── (CodePipeline, kubectl, app screenshot, etc.)
└── README.md
```

---

## 🚀 Application URL

**✅ Live URL (Kubernetes LoadBalancer ARN):**

🔗 [http://a79f5711a37d940fc90792c766d7f9b6-2008028657.us-east-1.elb.amazonaws.com](http://a79f5711a37d940fc90792c766d7f9b6-2008028657.us-east-1.elb.amazonaws.com)

---

## 🔧 Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/HeisenbergZS/Brain-Tasks-App.git
cd Brain-Tasks-App
```

---

### 2. Docker Image Build & Push (Handled via CodeBuild)

```bash
# (Auto done via buildspec.yml during CodeBuild)
docker build -t brain-tasks-app .
docker tag brain-tasks-app:latest <aws_account_id>.dkr.ecr.us-east-1.amazonaws.com/brain-tasks-app
docker push <aws_account_id>.dkr.ecr.us-east-1.amazonaws.com/brain-tasks-app
```

---

## 📆 AWS CodePipeline Flow

```
GitHub (Dev Branch)
     ⬇️ Commit Push
AWS CodePipeline
     ⬇️
AWS CodeBuild → buildspec.yml
     ⬇️
Docker Image Build → Push to ECR
     ⬇️
Manual kubectl apply to EKS Cluster (EC2)
```

---

## ☘️ Kubernetes Deployment

**Deployment + Service Manifest: `manifests/`**

```bash
kubectl apply -f manifests/deployment.yaml
kubectl apply -f manifests/service.yaml

kubectl get pods
kubectl get svc
```

---

## 📈 Monitoring (CloudWatch)

* CodeBuild logs are automatically sent to **CloudWatch Logs**
* Use `kubectl logs <pod-name>` for app logs
* Health can be checked from browser via LoadBalancer URL

---

## 🖼️ Screenshots

All screenshots included in `/Brain-Task-Output` folder:

* ✅ CodePipeline execution
* ✅ CodeBuild success log
* ✅ Docker image in ECR
* ✅ `kubectl get pods` / `kubectl get svc`
* ✅ Live application in browser

---

## 👤 Author

* **GitHub:** [HeisenbergZS](https://github.com/HeisenbergZS)
* **Docker Hub:** [heisenbergzz](https://hub.docker.com/u/heisenbergzz)

---

## ✅ Submission Summary

* GitHub Repo: [https://github.com/HeisenbergZS/Brain-Tasks-App](https://github.com/HeisenbergZS/Brain-Tasks-App)
* App URL: [http://a79f5711a37d940fc90792c766d7f9b6-2008028657.us-east-1.elb.amazonaws.com](http://a79f5711a37d940fc90792c766d7f9b6-2008028657.us-east-1.elb.amazonaws.com)
* Includes: CI/CD, Docker, ECR, Kubernetes, CloudWatch monitoring

---
