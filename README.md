## 🚀 GitHub Actions Docker CI/CD Project

### 📌 Project Description

This project demonstrates how to automate Docker image building and pushing using GitHub Actions.
Whenever code is pushed to the ```main``` branch, a GitHub Actions workflow automatically builds a Docker image and pushes it to Docker Hub.

This is a basic CI/CD pipeline used in DevOps environments.

### 🧱 Project Architecture
```
Developer
   │
   │ Push Code
   ▼
GitHub Repository
   │
   │ Trigger Workflow
   ▼
GitHub Actions
   │
   ├── Build Docker Image
   ├── Login to DockerHub
   └── Push Image to DockerHub
```

### 🐳 Dockerfile Explanation

The Dockerfile is used to create a Docker image that runs a simple website using Nginx.

Steps inside Dockerfile

- Pull base image (Ubuntu / Nginx)
- Install required packages
- Copy website files
- Start Nginx server

  ### ⚙️ GitHub Actions Workflow

  Workflow file location:
  ```
  .github/workflows/docker.yml
  ```

The workflow runs when:

- Code is pushed to the main branch
- A pull request is created
-Workflow is manually triggered

---

# 🔄 Workflow Steps

## 1️⃣ Checkout Repository
Downloads the repository code into the GitHub runner.

```yaml
uses: actions/checkout@v4
```

---

## 2️⃣ Build Docker Image
Creates a Docker image from the Dockerfile.

```bash
docker build -t <dockerhub-username>/docker-project-image-push:main .
```

---

## 3️⃣ Login to DockerHub
Secure login using GitHub Secrets.

```bash
docker login
```

Secrets used:

```
DOCKER_HUB_USERNAME
DOCKER_HUB_TOKEN
```

---

## 4️⃣ Push Image to DockerHub
Uploads the image to DockerHub.

```bash
docker push <dockerhub-username>/docker-project-image-push:main
```

---

# 🔐 GitHub Secrets Setup

Go to:

```
Repository
→ Settings
→ Secrets and variables
→ Actions
```

Add the following secrets:

### DOCKER_HUB_USERNAME
Your DockerHub username.

### DOCKER_HUB_TOKEN
DockerHub access token.

To create token:

```
DockerHub → Account Settings → Security → Access Token
```

---

# ▶️ Running the Container Locally

## Pull Image

```bash
docker pull <yourusername>/docker-project-image-push:main
```

## Run Container

```bash
docker run -d -p 8080:80 <yourusername>/docker-project-image-push:main
```

Open browser:

```
http://localhost:8080
```

You will see the website from **index.html**.

---

# 📦 DockerHub Repository

After successful workflow execution, the Docker image is available on DockerHub.

Example:

```
https://hub.docker.com/r/<yourusername>/docker-project-image-push
```

---

# 🎯 Key Learning Outcomes

Through this project, I learned:

- GitHub Actions workflow creation
- CI/CD pipeline basics
- Docker image building
- DockerHub integration
- Secure credential management using GitHub Secrets
- Containerized web application deployment

---

# 🛠️ Technologies Used

- GitHub
- GitHub Actions
- Docker
- DockerHub
- Nginx
- HTML
- CSS
- Linux

---

# 🚀 Future Improvements

- Automatic deployment to AWS EC2
- Kubernetes deployment
- Terraform infrastructure automation
- Version tagging for Docker images
- Monitoring and logging integration
