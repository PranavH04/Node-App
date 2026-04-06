# DevOps Node.js Sample Project

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub-PranavH04%2Finternship-blue?logo=docker)](https://hub.docker.com/r/PranavH04/internship)

A simple Node.js Express application designed to demonstrate containerization, CI/CD, and Kubernetes deployment for a DevOps internship project.

## Technology Stack

- Node.js
- Express.js
- Docker
- Docker Compose
- GitHub Actions
- Kubernetes

## Folder Structure

```text
internship/
├── .github/
│   └── workflows/
│       └── docker-image.yml
├── Dockerfile
├── .dockerignore
├── docker-compose.yml
├── k8s-deployment.yaml
├── k8s-service.yaml
├── package.json
├── package-lock.json
├── server.js
└── README.md
```

## Project Description

This project includes a small Express server that responds with `Hello DevOps World` on the root route. The repository includes Docker and Docker Compose support, a GitHub Actions workflow for CI/CD, and Kubernetes manifests for deployment.

## Run Locally

1. Install dependencies:
   ```bash
   npm install
   ```
2. Start the application:
   ```bash
   npm start
   ```
3. Open your browser and navigate to:
   ```text
   http://localhost:3000
   ```

## Run Using Docker

### Pull from Docker Hub
```bash
docker pull PranavH04/internship:latest
docker run -p 3000:3000 PranavH04/internship:latest
```

### Build Locally
1. Build the Docker image:
   ```bash
   docker build -t devops-node-app .
   ```
2. Run the container:
   ```bash
   docker run -p 3000:3000 devops-node-app
   ```
3. Open your browser and navigate to:
   ```text
   http://localhost:3000
   ```

## Run Using Docker Compose

1. Start the service:
   ```bash
   docker-compose up --build
   ```
2. Open your browser and navigate to:
   ```text
   http://localhost:3000
   ```

## CI/CD Pipeline

The GitHub Actions workflow is configured in `.github/workflows/docker-image.yml`.

It performs the following steps on every push to the `main` branch:

1. Checkout repository code.
2. Set up Node.js.
3. Install project dependencies with `npm install`.
4. Run tests if a valid test script is present.
5. Authenticate with Docker Hub using repository secrets.
6. Build and push the Docker image to Docker Hub.

### Required GitHub Secrets

- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

## Kubernetes Deployment

The Kubernetes manifests are `k8s-deployment.yaml` and `k8s-service.yaml`.

Replace `YOUR_DOCKERHUB_USERNAME` in `k8s-deployment.yaml` with your Docker Hub username before applying.

The GitHub Actions workflow builds and pushes the Docker image as:
`<DOCKERHUB_USERNAME>/internship:latest`.

To deploy the application on a Kubernetes cluster:
1. Apply the manifests:
   ```bash
   kubectl apply -f k8s-deployment.yaml -f k8s-service.yaml
   ```
2. Verify the deployment and service:
   ```bash
   kubectl get deployments
   kubectl get services
   ```
3. Access the application on the NodePort service at port `30000`:
   ```text
   http://<node-ip>:30000
   ```

> Note: Ensure your cluster nodes allow NodePort access on port `30000`.

## Notes

- The application uses port `3000` inside the container.
- The Kubernetes service exposes the app as a `NodePort` service so it can be accessed from outside the cluster.
- Update the Docker image tag in the workflow to match your Docker Hub repository if needed.
