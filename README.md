# DevOps Internship Assignment

This repository contains a Docker Compose-based setup of two backend services (one in Go and one in Python) behind an Nginx reverse proxy.

## 📁 Project Structure

.
├── docker-compose.yml # Orchestrates all services
├── nginx/
│ ├── nginx.conf # Nginx reverse proxy config
│ └── Dockerfile # Builds custom Nginx image
├── service_1/
│ ├── main.go # Golang backend
│ ├── go.mod
│ └── Dockerfile
├── service_2/
│ ├── app.py # Python (Flask) backend
│ ├── pyproject.toml
│ ├── requirements.txt
│ └── Dockerfile
└── README.md


## 🚀 Setup Instructions

1. **Clone the Repository**

git clone https://github.com/<your-username>/devops-intern-assignment.git
cd devops-intern-assignment
Run the Application

docker-compose up --build
This command builds and launches all three containers:

nginx (reverse proxy)

service1 (Go app)

service2 (Python Flask app)

Access the Services

Service	URL
Service 1	http://localhost:8080/service1
Service 2	http://localhost:8080/service2

🌐 How Routing Works
The Nginx container acts as a reverse proxy:

Requests to /service1 are routed to the Go app on port 8001

Requests to /service2 are routed to the Python app on port 5000

Nginx also logs incoming requests with timestamps and paths.

Example from nginx.conf:
location /service1 {
    proxy_pass http://service1:8001;
    access_log /var/log/nginx/access.log main;
}

location /service2 {
    proxy_pass http://service2:5000;
    access_log /var/log/nginx/access.log main;
}
Bonus Implementations
 Healthchecks for both services using curl

 Nginx logging enabled with timestamp and path

 All services on a single exposed port (8080)

 Clean and modular Dockerfile setups for each service

Tech Stack
Docker + Docker Compose

Nginx (in container)

Golang (Service 1)

Python + Flask (Service 2)

uv for dependency management (Service 2)
