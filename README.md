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

##  Screenshots

###  Home Page (Anime List)
<!-- Add screenshot of the main UI showing anime cards -->
<img width="1470" height="956" alt="startup page" src="https://github.com/user-attachments/assets/8dd00a72-14ff-446f-9703-947cb422b54a" /> <p style="text-align: center;">Home Page</p>


### ➕ Add Anime Form
<!-- Add screenshot of the form where user fills in anime name, link, description -->
<img width="1470" height="956" alt="adding anime" src="https://github.com/user-attachments/assets/73e4fcf0-3890-4d86-a05f-57f3c141f4f2" />
<img width="1470" height="956" alt="added anime" src="https://github.com/user-attachments/assets/fe3333fe-aa82-4e72-b2ef-d652b8a7d984" /> <p style="text-align: center;">Adding anime into watch list.</p>



### 🐳 Docker Containers Running
<!-- Run `docker ps` in terminal and screenshot the output -->
<img width="977" height="151" alt="dokcker ps" src="https://github.com/user-attachments/assets/e9168857-1dde-458f-ace0-fef431b448c9" />
<p style="text-align: center;">"docker ps" command in action.</p>

### 🔨 Docker Compose Build
<!-- Screenshot of `docker compose up --build` terminal output showing all 3 services starting -->
 <img width="357" height="171" alt="successfully created" src="https://github.com/user-attachments/assets/6d647015-af50-49b6-8f73-2e0709e6970f" />
 <p style="text-align: center;">Successfully built all three services.</p>


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

## 🚀 Getting Started

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
B.Tech CSE  
[GitHub](https://github.com/lakshh004)
