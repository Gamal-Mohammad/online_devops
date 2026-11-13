# vProfile – Java Web App with Jenkins CI/CD & Kubernetes

![Java](https://img.shields.io/badge/Java-007396?logo=openjdk&logoColor=white) ![Spring](https://img.shields.io/badge/Spring-6DB33F?logo=spring&logoColor=white) ![Maven](https://img.shields.io/badge/Maven-C71A36?logo=apachemaven&logoColor=white) ![Tomcat](https://img.shields.io/badge/Tomcat-F8DC75?logo=apachetomcat&logoColor=black) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white) ![Memcached](https://img.shields.io/badge/Memcached-2C5BB4) ![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white) ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?logo=jenkins&logoColor=white) ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)

> Multi-tier Java web application with a full Jenkins → Docker → Kubernetes pipeline.

## Overview

**vProfile** is a multi-tier Java web application (Spring MVC, Spring Security, Spring Data JPA, JSP) packaged as a WAR and served by **Tomcat**, backed by **MySQL**, **Memcached** and **RabbitMQ**. This repository wraps it in a complete DevOps workflow: build with Maven, containerise with Docker, and deploy to Kubernetes through a Jenkins pipeline.

## Tech Stack

- **Java**
- **Spring**
- **Maven**
- **Tomcat**
- **MySQL**
- **Memcached**
- **RabbitMQ**
- **Docker**
- **Jenkins**
- **Kubernetes**

## Repository Structure

```text
Dockerfile
index.html
Jenkinsfile
kubernetes/app-secret.yml
kubernetes/app-service.yml
kubernetes/db-cip.yml
kubernetes/deployment-app.yml
kubernetes/deployment-db.yml
kubernetes/deployment-mc.yml
kubernetes/deployment-rmq.yml
kubernetes/mc-cip.yml
kubernetes/rmq-cip.yml
new-file
pom.xml
README.md
src/main/java/ …
src/main/resources/ …
src/main/webapp/ …
src/test/java/ …
```

## Getting Started

### Prerequisites

- JDK 11 and Maven 3
- Docker
- A Kubernetes cluster (e.g. Minikube) and `kubectl`

### Build & Run Locally

```bash
mvn clean install -DskipTests
docker build -t vprofile-app .
docker run -d -p 8080:8080 vprofile-app
```

Then open http://localhost:8080.

### Deploy to Kubernetes

```bash
kubectl apply -f kubernetes/
```

## CI/CD Pipeline

The `Jenkinsfile` defines the following stages:

```mermaid
flowchart LR
    S0["BUILD Artifact WAR File"]
    S1["Build Docker Image"]
    S2["Test Docker Image"]
    S3["Remove Container"]
    S4["Deploy App On KuberNetes"]
    S0 --> S1 --> S2 --> S3 --> S4
```

## Author

**Gamal Mohammad**

[![GitHub](https://img.shields.io/badge/GitHub-Gamal--Mohammad-181717?logo=github)](https://github.com/Gamal-Mohammad)
