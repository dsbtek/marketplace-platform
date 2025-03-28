# Deployment Guide

## Prerequisites

-   Docker & Docker Compose installed
-   Node.js & Yarn installed
-   PostgreSQL database configured
-   Environment variables set in `.env` file

## Deployment Steps

### 1. Clone the Repository

```sh
git clone https://github.com/your-repo/marketplace-platform.git
cd marketplace-platform
```

### 2. Set Up Environment Variables

Copy `.env.example` and rename it to `.env`. Fill in the required values.

```sh
cp .env.example .env
```

### 3. Build and Start Services with Docker

```sh
docker-compose up --build -d
```

### 4. Run Database Migrations

```sh
docker exec -it backend-service alembic upgrade head
```

### 5. Access the Application

-   Frontend: `http://localhost:3000`
-   Backend API: `http://localhost:8000`
-   Admin Panel (if applicable): `http://localhost:8000/admin`

### 6. Monitoring & Logs

Check logs for debugging:

```sh
docker logs -f backend-service
```

### 7. CI/CD Deployment

-   Use **GitHub Actions** for automated deployment.
-   Configure **Kubernetes** for scaling.

## Production Deployment

-   Use **Nginx** as a reverse proxy.
-   Enable **SSL** with Let’s Encrypt.
-   Set up **Load Balancing** for high availability.

For troubleshooting, refer to `docs/troubleshooting.md`.
