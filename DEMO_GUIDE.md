# DevOps Internship Evaluation - Demo Guide

## Project Overview
- **Project**: Simple Node.js Express App with CI/CD, Docker, and Kubernetes
- **Location**: `c:\Users\admin\Desktop\internship`
- **What it demonstrates**: Containerization, CI/CD pipeline, and orchestration

## What You Will Demo

### 1. Local Application Run (2 min)
```bash
npm install
npm start
```
- Open browser to `http://localhost:3000`
- Shows: **"Hello DevOps World"**
- **Talking point**: "This is our simple Node.js application"

### 2. Docker Containerization (3 min)
```bash
# Build Docker image
docker build -t devops-node-app .

# Run container
docker run -p 3000:3000 devops-node-app
```
- Open browser to `http://localhost:3000`
- **Talking point**: "We've containerized the app for consistent deployment"

### 3. Docker Compose (2 min)
```bash
docker-compose up --build
```
- **Talking point**: "Docker Compose simplifies multi-service orchestration"

### 4. CI/CD Pipeline - GitHub Actions (5 min)
- Show `.github/workflows/docker-image.yml`
- **Pipeline steps**:
  1. Checkout code
  2. Setup Node.js
  3. Install dependencies
  4. Run tests (if available)
  5. Login to Docker Hub
  6. Build and push image
- **Talking point**: "Every push to main automatically builds and pushes a new image"

### 5. Kubernetes Deployment (5 min)
- Show `k8s-deployment.yaml` and `k8s-service.yaml`
```bash
# Deploy to K8s cluster
kubectl apply -f k8s-deployment.yaml -f k8s-service.yaml

# Verify
kubectl get deployments
kubectl get services
```
- Access app at `http://<node-ip>:30000`
- **Talking point**: "Kubernetes manages our container orchestration at scale"

## Setup Required Before Demo

### GitHub Repository
1. Create a new repo on GitHub
2. Push this code:
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <your-github-repo-url>
git push -u origin main
```

### Docker Hub Secrets
In your GitHub repo: **Settings > Secrets and variables > Actions**
- Add `DOCKERHUB_USERNAME` - your Docker Hub username
- Add `DOCKERHUB_TOKEN` - create at https://hub.docker.com/settings/security

### Trigger CI/CD
1. Make any small change (e.g., edit README)
2. Push to main branch
3. Watch the Actions tab for the pipeline running
4. Verify image appears on Docker Hub

## Key Talking Points for Evaluators

**CI/CD Benefits**:
- Automated testing and building
- Consistent deployment process
- Faster delivery cycles

**Docker Benefits**:
- Environment consistency
- Easy scaling
- Portable across systems

**Kubernetes Benefits**:
- Automated scaling
- Self-healing (restarts failed containers)
- Load balancing
- Rolling updates

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Port 3000 in use | Change port in `server.js` or stop other app |
| Docker permission denied | Run terminal as Administrator |
| K8s connection refused | Ensure cluster is running (`minikube start` or Docker Desktop K8s) |

## Quick Demo Script (15 minutes total)

1. **Show project structure** (2 min)
2. **Run locally** (2 min)
3. **Explain Dockerfile** (2 min)
4. **Show GitHub Actions workflow** (3 min)
5. **Show pushed image on Docker Hub** (2 min)
6. **Explain Kubernetes manifests** (4 min)

## Evaluation Success Criteria

You should be able to explain:
- [ ] What CI/CD is and why it matters
- [ ] How Docker containerizes applications
- [ ] What Kubernetes does for orchestration
- [ ] How these tools work together in the pipeline

---

**Remember**: The evaluator cares more about your understanding of the DevOps tools than the complexity of the application code. This simple project perfectly demonstrates all key concepts.
