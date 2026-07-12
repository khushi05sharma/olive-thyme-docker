# Olive & Thyme - Docker Setup

This folder contains the Docker configuration for running the **Olive & Thyme** full-stack application locally using **Docker Compose**.

The application consists of:

- **Frontend:** React + TypeScript + Vite (served with Nginx)
- **Backend:** Express + TypeScript
- **Database:** MongoDB Atlas (Cloud)

---

## Project Structure

```text
olive-thyme/
│
├── frontend/
│   ├── Dockerfile
│   └── .dockerignore
│
├── backend/
│   ├── Dockerfile
│   └── .dockerignore
│
├── docker-compose.yml
├── .env.example
└── README.md
```

---

## Prerequisites

Before running the project, make sure you have:

- Docker Desktop installed
- Git installed
- A MongoDB Atlas database
- Spoonacular API Key

---

## Setup

### 1. Clone the frontend and backend repositories

```bash
git clone <frontend-repository>
git clone <backend-repository>
```

Place both repositories inside the same root folder.

---

### 2. Create a `.env` file

Copy the example file:

```bash
cp .env.example .env
```

Fill in your own values:

- MongoDB Atlas URI
- JWT Secret
- Email credentials
- Spoonacular API Key
- Other required environment variables

---

### 3. Start the application

```bash
docker compose up --build
```

Docker Compose will:

- Build the frontend image
- Build the backend image
- Create a Docker network
- Start both containers
- Inject environment variables
- Connect the frontend and backend

---

## Access the Application

Frontend

```
http://localhost:5173
```

Backend

```
http://localhost:5000
```

---

## Docker Files Included

### Frontend

- Multi-stage Docker build
- Nginx for serving production files
- Build arguments for Vite environment variables

### Backend

- Multi-stage Docker build
- Production dependencies only
- Runtime environment variables using Docker Compose

---

## Useful Commands

Start

```bash
docker compose up
```

Rebuild and start

```bash
docker compose up --build
```

Stop containers

```bash
docker compose down
```

View running containers

```bash
docker ps
```

View logs

```bash
docker compose logs
```

---

## Notes

- MongoDB runs on **MongoDB Atlas** (cloud), not inside Docker.
- Environment variables are **not committed** to GitHub.
- Use `.env.example` as a template for creating your own `.env`.

## Repositories

This Docker Compose setup coordinates these three repositories:

- **Frontend:** https://github.com/khushi05sharma/olive-and-thyme-frontend
- **Backend:** https://github.com/khushi05sharma/olive-and-thyme-backend
- **Docker Orchestration:** https://github.com/yourusername/olive-thyme-docker (this repo)

Each application repo contains its own Dockerfile for independent deployment.