# Hello World App Server Deployment

This repository provides comprehensive instructions for setting up a basic Python web server that displays the "Hello, world" message. It also covers deploying the server using Docker on an Amazon Linux 2 EC2 instance. Additionally, the guide demonstrates how to push the Docker image to a repository for versioning purposes.

## Prerequisites

- Amazon Linux 2 EC2 instance (or a compatible environment with Docker support)
- Basic familiarity with command-line tools
- Docker installed on the EC2 instance
- Git installed on the EC2 instance

## Step-by-Step Setup

### 1. SSH into Your Amazon Linux 2 EC2 Instance:

```bash
chmod 400 hello-world-server.pem
ssh -i your-key.pem ec2-user@your-ec2-instance-ip
```

### 2. Install Docker and Start the Docker Service:

```bash
sudo -s
amazon-linux-extras install docker -y
systemctl start docker
```

### 3. Install Git:

```bash
yum install git-all -y
```

### 4. Clone This Repository:

```bash
git clone https://github.com/SyedMohammedKhalander/hello-app-server.git
cd hello-app-server
```

### 5. Run the Python Web Server Locally:

```bash
python3 main.py
# The server is listening on port 8000
```

### 6. Build the Docker Image:

```bash
docker build -t hello-world-app .
```

### 7. Run the Docker Container on Port 80:

```bash
docker run -d -p 80:8000 hello-world-app
```

### 8. Login to Your Docker Hub Account (or Another Docker Registry):

```bash
docker login
# Pass username and password for your Docker repo
```

### 9. Tag the Docker Image:

```bash
docker tag hello-world-app:latest syedmohammedkhalander/hello-world-app:v1
```

### 10. Push the Tagged Image to the Docker Registry:

```bash
docker push syedmohammedkhalander/hello-world-app:v1
```



Author: [Syed Mohammed Khalander]
```

