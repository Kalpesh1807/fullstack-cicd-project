# Fullstack CI/CD Project

A small full-stack application with a React frontend, an Express API, MongoDB, and Nginx. Docker Compose defines the services and exposes the application through Nginx on port 80.

## Project structure

```text
.
├── backend/            # Express API and MongoDB connection
├── frontend/           # React application built with Vite
├── nginx/              # Nginx reverse proxy configuration
└── docker-compose.yml  # Local multi-container setup
```

## Requirements

- Docker Desktop or Docker Engine with the Compose plugin
- Node.js 20 or later for running the frontend or backend outside Docker

## Run with Docker Compose

From the project root, start the services:

```sh
docker compose up --build
```

Open [http://localhost](http://localhost). Nginx serves the frontend and forwards `/api` requests to the backend. Stop the services with `Ctrl+C`, or run `docker compose down` in another terminal.

The backend connects to MongoDB using the `MONGO_URL` environment variable. Set it in the Compose service configuration before starting the stack; for the Compose MongoDB service, use `mongodb://mongodb:27017/fullstack`.

## Run components locally

Start the backend in one terminal:

```sh
cd backend
npm install
$env:MONGO_URL="mongodb://localhost:27017/fullstack" # PowerShell
npm start
```

On macOS or Linux, set the variable with `export MONGO_URL=mongodb://localhost:27017/fullstack` instead. A MongoDB instance must be available at that URL.

Start the frontend in another terminal:

```sh
cd frontend
npm install
npm run dev
```

The frontend development server and API need a proxy configuration or a shared origin for `/api` requests. The Nginx proxy configuration in this project provides that routing in the Docker Compose setup.

## API

- `GET /api` — returns a JSON message indicating that the backend is running.

## Frontend scripts

Run these from the `frontend` directory:

```sh
npm run dev      # Start the Vite development server
npm run build    # Build the production frontend
npm run lint     # Run ESLint
npm run preview  # Preview the production build
```
