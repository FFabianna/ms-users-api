# 👤 ms-users-api

This microservice manages user-related operations and authentication logic. It is built with Java using Maven, and packaged as a Spring Boot JAR file.

---

## 🔗 Project Links

- 📋 [Trello Board](https://trello.com/invite/b/680296aa17864e87fc6c7fed/ATTI82505e108ae3e7a005ede0081ec437f87CDDDEF1/microservice)
- 📄 [Project Documentation](https://docs.google.com/document/d/1FER2lpkZJk2eI5tpMnMy8mFhd42g3f4jioasHwZ0klo/edit?usp=sharing)

---


## 🐳 Docker Image

The Dockerfile uses a two-stage build:

1. **Stage 1**: Uses Maven to compile the Java project and generate the JAR.
2. **Stage 2**: Copies the JAR into a lightweight OpenJDK Alpine image and starts the application with `java -jar`.

Default port exposed: **8083**.

---

## ☸️ Kubernetes Deployment

- Deploys one replica of the container labeled `app: usersapi`.
- Exposes the internal port 8083 via a `ClusterIP` service.
- The image is pulled from Azure Container Registry (`usersapi-image`).

---

## 🔁 CI/CD Pipeline

CI/CD is handled by GitHub Actions:

1. Checkout the repository.
2. Tag the image using the current commit SHA.
3. Login to Azure and ACR.
4. Build and push the Docker image to ACR (both `:latest` and SHA-based tag).
5. Apply Kubernetes manifests.
6. Update the deployment to ensure the latest image is used.

---

## 📢 Slack Integration

A secondary GitHub Actions workflow notifies a Slack channel when changes are pushed to the `main` branch. This helps keep the team informed of updates in the `ms-users-api` microservice repository.


---

## 📦 Environment Variables

| Variable        | Description                             |
|-----------------|-----------------------------------------|
| `JWT_SECRET`     | Secret key for JWT token verification  |
| `SERVER_PORT`    | Internal API port (default: 8083)      |

## <b> Made by </b>

+ [Fabiana Valderruten](https://github.com/FFabianna "FFabianna")
+ [Gloria Vicuña](https://github.com/Vanesa155 "Vanesa V.")

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)