# Mini App CI/CD

This is the Mini App, which includes a Node.js backend with SQLite and a Vue.js frontend. The application is containerized using Docker, and Docker Compose is used to manage both services.

## Prerequisites

- Docker Desktop
- Node.js (version 22.12.0)
- pnpm

## Getting Started

### Running Locally

1. Clone the repository:

```sh
git clone https://github.com/yourusername/mini-app-cicd.git
cd mini-app-cicd
```

2. Start the services with Docker Compose:

```sh
docker compose --env-file .env up --build
```

- The `--build` flag is used to build the images before starting the services.

3. Access the application:

- Frontend: [http://localhost:8000](http://localhost:8000)
- Backend: [http://localhost:3000](http://localhost:3000)

4. Stop the services:

```sh
docker compose down
```

5. Get Jenkins Password

```sh
docker exec -it jenkins-container-id bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword

```
