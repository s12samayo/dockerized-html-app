# Dockerized HTML Application

## Project Overview

This project is a containerized static web application built using HTML, CSS, and JavaScript and deployed using Docker with the lightweight Nginx Alpine image.

The goal of this project was to learn and practice:
- Docker fundamentals
- Dockerfile creation
- Building Docker images
- Running containers
- Port mapping
- Container inspection and troubleshooting
- Git and GitHub workflow

The application files were packaged into a Docker container and served through Nginx.

---

## Technologies Used

- HTML5
- CSS3
- JavaScript
- Docker
- Nginx
- Alpine Linux
- Git
- GitHub
- VS Code
- WSL2 Ubuntu

---

## Project Structure

```bash
.
├── Dockerfile
├── README.md
├── index.html
├── about.html
├── article.html
├── css/
├── img/
└── favicon.ico
```

---

## Dockerfile

```Dockerfile
FROM nginx:alpine

COPY . /usr/share/nginx/html/

EXPOSE 80
```

---

## Build Docker Image

```bash
docker build -t dockerized-html-app .
```

---

## Run Docker Container

```bash
docker run -d --name my-html-app -p 8080:80 dockerized-html-app
```

---

## Access the Application

Open the browser and visit:

```text
http://localhost:8080
```

---

## Verify Running Containers

```bash
docker ps
```

---

## Verify Docker Images

```bash
docker images
```

---

## Access the Running Container

```bash
docker exec -it my-html-app sh
```

---

## Verify Application Files Inside Container

```bash
cd /usr/share/nginx/html
ls
```

---

## Stop the Container

```bash
docker stop my-html-app
```

---

## Start the Container Again

```bash
docker start my-html-app
```

---

## Remove the Container

```bash
docker rm -f my-html-app
```

---

## Troubleshooting Notes

### Problem: Docker command not found in WSL2

Error:

```text
The command 'docker' could not be found in this WSL 2 distro.
```

Solution:
- Open Docker Desktop
- Enable WSL2 integration
- Go to:
  - Settings
  - Resources
  - WSL Integration
- Enable Ubuntu distro
- Restart terminal

---

### Problem: Default Nginx page appeared instead of application

Cause:
- Application files were not copied correctly into the Nginx web root directory.

Solution:
- Confirm Dockerfile contains:

```Dockerfile
COPY . /usr/share/nginx/html/
```

- Rebuild image without cache:

```bash
docker build --no-cache -t dockerized-html-app .
```

---

### Problem: Unable to access container shell

Error:

```text
exec: "-app": executable file not found in $PATH
```

Cause:
- Incorrect docker exec command syntax.

Correct command:

```bash
docker exec -it my-html-app sh
```

---

## Key Learning Outcomes

Through this project, I learned:
- How Docker images are built
- Difference between images and containers
- How to use Dockerfile instructions
- How to run and manage containers
- How Nginx serves static applications
- Basic container troubleshooting
- Git branching and GitHub workflow

---

## Future Improvements

- Add Docker Compose
- Add custom Nginx configuration
- Add CI/CD with GitHub Actions
- Deploy container to AWS EC2
- Add reverse proxy configuration
