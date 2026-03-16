# 🚀 MEAN Stack CRUD Application – Production-Ready DevOps Project

## 📌 Project Overview

This is a  end‑to‑end DevOps project showcasing the complete containerization, deployment, and automation of a full-stack **MEAN (MongoDB, Express, Angular, Node.js)** application.  
The app manages a collection of tutorials and supports full **CRUD operations** plus search — all built and shipped with a production mindset.

What I implemented:

* Docker containerization
* Cloud deployment
* Reverse proxy
* CI/CD automation

---

## 🏗️ Architecture Overview


```
Developer → GitHub → GitHub Actions (CI/CD)
        → Docker Hub → AWS EC2 → Docker Compose
        → MongoDB → Backend → Frontend → Nginx Reverse Proxy
```

---

## 🛠️ Tech Stack

### 🔹 Backend

* Node.js
* Express.js
* MongoDB
* Mongoose

### 🔹 Frontend

* Angular 15
* HTTPClient

### 🔹 DevOps & Cloud

* Docker
* Docker Compose
* AWS EC2 (Ubuntu)
* Nginx
* GitHub Actions
* Docker Hub

---

## ✨ Features

✔ Create, Read, Update, Delete tutorials
✔ Search tutorials by title
✔ REST API based architecture
✔ Containerized microservices
✔ Cloud deployment
✔ Reverse proxy on port 80
✔ Automated CI/CD pipeline
✔ GitOps-style, zero-touch deployments

---

## 📂 Project Structure

```
crud-dd-task-mean-app
│
├── backend
│   ├── app
│   ├── server.js
│   └── Dockerfile
│
├── frontend
│   ├── src
│   └── Dockerfile
│
├── docker-compose.yml
└── README.md
```

---

## ⚙️ Setup & Installation

### 🔹 Clone the repository

```
git clone https://github.com/deep-priyo/mean-crud-devops
cd mean-crud-devops
```

---

### 🔹 Backend Setup

```
cd backend
npm install
node server.js
```

---

### 🔹 Frontend Setup

```
cd frontend
npm install
ng serve
```

Application runs on:

```
http://localhost:4200
```

---

## 🐳 Docker Containerization

Both frontend and backend are containerized using Docker.

### 🔹 Build images

```
docker build -t <docker-username>/mean-backend ./backend
docker build -t <docker-username>/mean-frontend ./frontend
```

### 🔹 Push to Docker Hub

```
docker push <docker-username>/mean-backend
docker push <docker-username>/mean-frontend
```

---

## ☁️ Cloud Deployment (AWS EC2)

An Ubuntu EC2 instance was configured with:

* Docker
* Docker Compose
* Nginx

The application is deployed using:

```
docker compose up -d
```

MongoDB is deployed as an official Docker container.

---

## 🔄 CI/CD Pipeline

GitHub Actions is configured to automate:

* Docker image build
* Image push to Docker Hub
* Automatic deployment on AWS EC2

### ✔ Pipeline triggers

The CI/CD workflow is scoped to application and infra changes to avoid unnecessary builds on docs-only commits.

It runs on changes to:

* Backend source code

* Frontend source code

* Dockerfiles and container configurations

* Deployment and infrastructure configuration files

Documentation-only updates do not trigger the pipeline.
This optimization reduces cloud usage and avoids redundant Docker Hub pushes.

---

## 🌐 Nginx Reverse Proxy

Nginx is configured to:

* Route frontend and backend traffic
* Expose the application on **port 80**
* Hide internal container ports
* Enable production-style deployment

---
### 🌐 Application Access

Users can access the deployed application using the EC2 public IPv4 address:

`http://<EC2-public-ipv4-address>`

Example:

`http://13.127.148.3`

> ⚠️ Note: The public IPv4 address of the EC2 instance is dynamic and may change when the instance is stopped and restarted.  
> In production, pin with an **Elastic IP** or use a **custom domain + DNS + HTTPS (SSL)**.

---


## 💾 Persistent Database & Storage Optimization

To ensure production reliability and prevent data loss, additional improvements were implemented in the infrastructure.

### 🔹 MongoDB Persistent Storage

Initially, MongoDB data was lost whenever Docker containers were restarted.  
To solve this, a **named Docker volume** was configured:

```yaml
mongo:
  image: mongo
  container_name: mongo
  restart: always
  ports:
    - "27017:27017"
  volumes:
    - mongo-data:/data/db
```
---
## 🔐 Security Considerations

✔ Docker containers isolated
✔ MongoDB internal network
✔ SSH secure access
✔ Secrets managed using GitHub Actions
✔ Reverse proxy architecture
---
## 📸 Screenshots & Demo

### 🔹 1. Application UI – Cloud Deployment

![Tutorials List – Cloud Deployment UI](screenshots/mainui.png)

This is the main dashboard of the MEAN stack CRUD app deployed on AWS EC2.  
Served via Nginx on port 80 — confirming successful cloud deployment.

---

### 🔹 2. Tutorial Details & Update Operations

![Tutorial Details & Edit](screenshots/ui_edit.png)

Full CRUD in action: update, publish, delete.  
All actions hit REST APIs (Node.js/Express) with data persisted in MongoDB (Dockerized).

---

### 🔹 3. Add Tutorial – Create Operation

![Add Tutorial](screenshots/ui_add.png)

Create flow from Angular → Backend → MongoDB, validating end‑to‑end cloud integration.

---

### 🔹 4. Docker Images in Docker Hub

![Docker Hub](screenshots/dockerhub.png)

Docker images for frontend and backend in Docker Hub — built and pushed automatically via GitHub Actions.

---

### 🔹 5. Running Containers on AWS EC2

![EC2 Containers](screenshots/ec2_instance.png)

All services (frontend, backend, MongoDB) running on AWS EC2 via Docker Compose.

---

### 🔹 6. GitHub Actions CI/CD Workflow

![GitHub Actions](screenshots/github_actions.png)

Automated CI/CD pipeline execution: image build → push → deploy to cloud infra.

---

### 🔹 7. Successful Deployment Logs

![Deployment Logs](screenshots/deployment_logs.png)

Successful automated deployment: remote container updates and service restarts on EC2.

---

### 🔹 8. Nginx Reverse Proxy Configuration

![Nginx Reverse Proxy](screenshots/reverse_proxy.png)

Served through Nginx reverse proxy on port 80.  
Internal container ports hidden for production-style security and ergonomics.

## 📊 Why This Approach

This project demonstrates a production-ready DevOps workflow:

* Scalable architecture
* Automated deployment
* Containerized services
* Cloud-ready
* High availability

This approach ensures:
✔ Faster deployment
✔ Reduced manual errors
✔ Improved scalability
✔ Easy maintenance

---

## 🚀 What’s Next

* HTTPS with SSL (Let’s Encrypt / ACM)
* Custom domain + DNS
* Kubernetes (EKS/K3s) deployment
* Monitoring with Prometheus & Grafana
* Load balancing (ALB/Nginx)
* Blue‑Green/Canary deployments
* IaC with Terraform or Pulumi

---

## 👨‍💻 About Me

Hi, I’m **P M** — DevOps | Full‑Stack | Cloud | Automation.  
I built this project to showcase real‑world DevOps skills across build, ship, and run.

---

## 📬 Contact

Let’s connect for collaboration or opportunities! ✉️

---

⭐ If you found this useful, consider leaving a star — it helps recruiters discover it! ✨

—

Made with ❤️ for learning, reliability, and speed.
