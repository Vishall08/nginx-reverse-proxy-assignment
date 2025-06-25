# 🚀 DevOps Intern Assignment: Nginx Reverse Proxy + Docker
---

This project demonstrates the use of **Docker Compose** to orchestrate two microservices (a Golang app and a Python Flask app) behind an **Nginx reverse proxy**. All services are containerized and accessible via a single port using **path-based routing**.

---


## 🌐 Services Overview

| Service     | Description               | Language | Path                    |
|-------------|---------------------------|----------|--------------------------|
| `service_1` | Golang backend app        | Go       | `/service1/hello`        |
| `service_2` | Python Flask backend app  | Python   | `/service2/hello`        |
| `nginx`     | Reverse proxy             | Nginx    | Routes to both services  |

---

## 🧑‍💻 How to Run

Make sure **Docker and Docker Compose** are installed on your machine.

> Open terminal or PowerShell inside the `assignment/` folder.

### 🔧 Build and Start All Containers

```bash
docker-compose up --build

```
This will:

Build images for all 3 services

Start Nginx reverse proxy

Launch Golang and Python services on an internal Docker network


## 🧪 Test the Services
After everything is running, go to your browser and access:

## ✅ Service 1 (Go):

http://localhost:8080/service1/hello

http://localhost:8080/service1/ping

## ✅ Service 2 (Flask):

http://localhost:8080/service2/hello

http://localhost:8080/service2/ping


## 🩺 Health Check
Each service exposes a simple /ping endpoint for health checks:

GET /service1/ping → { "status": "ok", "service": "1" }

GET /service2/ping → { "status": "ok", "service": "2" }

These can be monitored or logged by Nginx or an external system.


## 📦 Docker Compose Services
Here’s a summary from docker-compose.yml:

service_1 — Go app (port 8001 inside container)

service_2 — Python Flask app (port 8002 inside container)

nginx — Reverse proxy listening on port 8080

