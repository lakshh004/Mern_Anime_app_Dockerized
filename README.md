# 🎌 MERN Anime App — Dockerized

A full-stack MERN application containerized with Docker Compose that lets users share and explore anime with persistent storage. Built as a hands-on DevOps learning project demonstrating multi-container architecture, service networking, and volume management.

---

##  Overview

Users can:
- Add anime with a name, link, and description
- View a community list of shared anime
- Click "Watch" to open the anime link directly

All services (frontend, backend, database) run as isolated Docker containers communicating over a shared Docker network.

---

##  Tech Stack

| Layer      | Technology              |
|------------|-------------------------|
| Frontend   | React (Vite)            |
| Backend    | Node.js, Express.js     |
| Database   | MongoDB                 |
| DevOps     | Docker, Docker Compose  |

---

##  Architecture

```
Frontend (React + Vite)
        ↓  HTTP requests via Docker network
Backend API (Node.js / Express)
        ↓  Mongoose ODM
MongoDB (Database)
        ↓
Docker Volume (Persistent Storage)
```

All three services are defined in `docker-compose.yml` and communicate via Docker's internal network — no `localhost` references between containers.

---

## 🐳 Docker Setup

Three services are orchestrated via Docker Compose:

| Service | Description              | Port  |
|---------|--------------------------|-------|
| `web`   | React frontend (Vite)    | 5173  |
| `api`   | Node.js backend          | 8000  |
| `db`    | MongoDB                  | 27017 |

**Key DevOps features:**
- Multi-container setup with isolated service responsibilities
- Inter-service communication via Docker internal network (`api`, `db` as hostnames)
- Persistent data storage using a named Docker volume (`anime:/data/db`)
- Docker Compose watch mode for live sync during development

---

##  Getting Started

### Prerequisites
- [Docker](https://www.docker.com/) installed and running
- Ports `5173`, `8000`, and `27017` should be free

### Run the App

```bash
git clone https://github.com/lakshh004/Mern_Anime_app_Dockerized.git
cd Mern_Anime_app_Dockerized
docker compose up --build
```

Then open:
- **Frontend** → http://localhost:5173
- **Backend API** → http://localhost:8000

---

## 🧪 How to Use

1. Open the app at `http://localhost:5173`
2. Click **"Share"**
3. Fill in:
   - Anime name
   - Link (e.g. Crunchyroll or YouTube URL)
   - Short description
4. Submit the form
5. Your anime appears in the list on the home page
6. Click **"Watch"** to open the link

---

## 🗄️ Data Persistence

- Data is stored in MongoDB via a named Docker volume
- Data survives container restarts automatically
- To fully reset all data:

```bash
docker compose down -v
docker compose up --build
```

---

## 🔍 Verify Containers Are Running

```bash
docker ps
```

You should see three containers:
- `mern-docker-web-1` (frontend)
- `mern-docker-api-1` (backend)
- `mern-docker-db-1` (MongoDB)

---

## 🔑 Environment Variables

**Backend** (`api` service):
```
DB_URL=mongodb://db:27017/anime
```

**Frontend** (`web` service):
```
VITE_API_URL=http://api:8000
```

> ⚠️ Note: Inside Docker, services communicate using their **service names** as hostnames (e.g. `db`, `api`) — not `localhost`.

---

## 💡 Key Learnings

- Containerizing a full-stack application using Docker
- Managing multi-service architecture with Docker Compose
- Handling inter-service communication via Docker's internal network
- Implementing persistent storage using Docker volumes
- Difference between development (Vite dev server) and production (Nginx) Docker setups

---

## 🚀 Planned Improvements

- [ ] Add JWT-based authentication
- [ ] Deploy on AWS EC2 with public URL
- [ ] Add CI/CD pipeline via GitHub Actions
- [ ] Integrate Nginx as a reverse proxy
- [ ] Add Redis caching for anime list

---

## 👨‍💻 Author

**Lakshya Purohit**  
B.Tech CSE | Rajasthan, India  
[GitHub](https://github.com/lakshh004)


