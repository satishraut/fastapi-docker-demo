# FastAPI Docker Demo - DevOps Learning Project

A simple FastAPI application containerized with Docker, ready for learning DevOps practices including Docker, Kubernetes, and CI/CD.

## 🏗️ Project Structure

```
fastapi-docker-demo/
├── main.py              # FastAPI application
├── Dockerfile           # Docker image definition
├── docker-compose.yml   # Docker Compose for local development
├── requirements.txt     # Python dependencies
├── .dockerignore        # Files to exclude from Docker build
├── k8s/                 # Kubernetes manifests
│   ├── deployment.yaml  # Kubernetes deployment
│   └── service.yaml     # Kubernetes service
└── .github/workflows/   # CI/CD pipeline (GitHub Actions)
    └── ci-cd.yml
```

## 🚀 Quick Start

### Prerequisites
- Docker installed
- Python 3.12+ (optional, for local development)

### Using Docker

1. **Build the image:**
   ```bash
   docker build -t fastapi-docker-demo .
   ```

2. **Run the container:**
   ```bash
   docker run -p 8000:8000 fastapi-docker-demo
   ```

3. **Access the API:**
   - Main endpoint: http://localhost:8000
   - Health check: http://localhost:8000/health

### Using Docker Compose

```bash
docker-compose up --build
```

Stop with: `docker-compose down`

## 📚 DevOps Learning Path

### 1. **Docker Fundamentals** ✅

**Current Setup:**
- Single-stage Dockerfile
- Basic dependency management
- Health check endpoint

**Try These:**
```bash
# Build with different tags
docker build -t fastapi-docker-demo:v1.0 .

# Run in detached mode
docker run -d -p 8000:8000 --name my-app fastapi-docker-demo

# View logs
docker logs my-app

# Execute commands inside container
docker exec -it my-app /bin/bash

# Stop and remove
docker stop my-app && docker rm my-app

# Inspect image layers
docker history fastapi-docker-demo
```

**Next Steps:**
- [ ] Create multi-stage Dockerfile for smaller images
- [ ] Add environment variables configuration
- [ ] Use Docker volumes for persistent data
- [ ] Experiment with different base images

### 2. **Docker Compose** ✅

**What it does:**
- Orchestrates multi-container applications
- Defines services, networks, and volumes
- Simplifies local development

**Practice:**
```bash
# Start services
docker-compose up

# Start in background
docker-compose up -d

# View logs
docker-compose logs -f

# Rebuild after changes
docker-compose up --build

# Scale services (when applicable)
docker-compose up --scale fastapi-app=3
```

**Next Steps:**
- [ ] Add a database service (PostgreSQL/MySQL)
- [ ] Add Redis for caching
- [ ] Configure networking between services
- [ ] Add volume mounting for development

### 3. **Kubernetes** ✅

**Deployment Steps:**

1. **Apply Kubernetes manifests:**
   ```bash
   kubectl apply -f k8s/deployment.yaml
   kubectl apply -f k8s/service.yaml
   ```

2. **Check deployment status:**
   ```bash
   kubectl get deployments
   kubectl get pods
   kubectl get services
   ```

3. **View pod logs:**
   ```bash
   kubectl logs -f deployment/fastapi-app
   ```

4. **Access the service:**
   ```bash
   # Get service URL (for LoadBalancer type)
   kubectl get service fastapi-service

   # Port forward for local access
   kubectl port-forward service/fastapi-service 8080:80
   ```

5. **Scale the application:**
   ```bash
   kubectl scale deployment fastapi-app --replicas=5
   ```

**Kubernetes Concepts Covered:**
- **Deployment**: Manages replica sets and rolling updates
- **Service**: Exposes pods with stable network identity
- **Liveness/Readiness Probes**: Health checks
- **Resource Limits**: CPU and memory constraints

**Next Steps:**
- [ ] Create ConfigMap for environment variables
- [ ] Add Secrets for sensitive data
- [ ] Create HorizontalPodAutoscaler (HPA)
- [ ] Set up Ingress for external access
- [ ] Create Namespace for environment isolation
- [ ] Add PersistentVolumes for stateful data

### 4. **CI/CD Pipeline** ✅

**Current Setup:**
- GitHub Actions workflow
- Automated build and test
- Docker image creation

**Enable the Pipeline:**

1. Push code to GitHub
2. The workflow automatically triggers on push/PR
3. Check Actions tab in GitHub repository

**Next Steps:**
- [ ] Add automated tests (pytest)
- [ ] Configure Docker Hub/Container Registry push
- [ ] Add deployment to Kubernetes
- [ ] Implement blue-green deployments
- [ ] Add security scanning (Trivy, Snyk)
- [ ] Create staging and production workflows

### 5. **Advanced DevOps Topics**

**Monitoring & Observability:**
- [ ] Add Prometheus metrics
- [ ] Integrate Grafana dashboards
- [ ] Set up distributed tracing (Jaeger/Zipkin)
- [ ] Configure log aggregation (ELK Stack)

**Security:**
- [ ] Scan Docker images for vulnerabilities
- [ ] Use least-privilege security contexts
- [ ] Implement network policies
- [ ] Add secrets management (Vault)

**Infrastructure as Code:**
- [ ] Create Terraform scripts for cloud infrastructure
- [ ] Use Helm charts for Kubernetes deployments
- [ ] Ansible playbooks for configuration management

**Cloud Platforms:**
- [ ] Deploy to AWS (EKS, ECS, App Runner)
- [ ] Deploy to GCP (GKE, Cloud Run)
- [ ] Deploy to Azure (AKS, Container Instances)

## 🎯 Practice Exercises

### Beginner
1. Modify the `/health` endpoint to return more detailed status
2. Add environment variables for app configuration
3. Create a multi-stage Dockerfile
4. Set up a local Kubernetes cluster (minikube/kind)

### Intermediate
1. Add a PostgreSQL database and connect via Docker Compose
2. Create Helm charts for Kubernetes deployment
3. Set up a complete CI/CD pipeline with automated deployment
4. Implement logging and monitoring

### Advanced
1. Build a complete microservices architecture
2. Implement service mesh (Istio/Linkerd)
3. Set up GitOps with ArgoCD/Flux
4. Create disaster recovery procedures

## 📖 Recommended Resources

- **Docker**: [Official Docker Docs](https://docs.docker.com/)
- **Kubernetes**: [Kubernetes.io Documentation](https://kubernetes.io/docs/)
- **FastAPI**: [FastAPI Documentation](https://fastapi.tiangolo.com/)
- **CI/CD**: [GitHub Actions Docs](https://docs.github.com/en/actions)

## 🛠️ Useful Commands

```bash
# Docker
docker build -t fastapi-docker-demo .
docker run -p 8000:8000 fastapi-docker-demo
docker ps
docker logs <container-id>

# Docker Compose
docker-compose up
docker-compose down
docker-compose logs

# Kubernetes
kubectl apply -f k8s/
kubectl get all
kubectl describe deployment fastapi-app
kubectl delete -f k8s/
```

## 📝 Notes

- This is a learning project - adapt it as you learn new concepts
- Always test changes locally before deploying
- Follow security best practices in production
- Keep Docker images small and secure
- Use version tags for your images (avoid `:latest` in production)

## 🤝 Contributing

Feel free to experiment and extend this project as you learn!

---

Happy Learning! 🚀