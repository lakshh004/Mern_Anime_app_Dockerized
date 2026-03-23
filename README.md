# 🚀 MERN Anime App (Dockerized)

A full-stack MERN application containerized using Docker Compose that allows users to share and explore anime with persistent storage.

---

## 🧠 Overview

This project demonstrates a **multi-container architecture** using Docker, where the frontend, backend, and database run as isolated services while communicating over a shared network.

Users can:
- Add anime with name, link, and description
- View a list of shared anime
- Access links directly from the UI

---

## ⚙️ Tech Stack

- **Frontend:** React (Vite)
- **Backend:** Node.js, Express.js
- **Database:** MongoDB
- **DevOps:** Docker, Docker Compose

---

## 🏗️ Architecture
Frontend (React)
↓
Backend API (Node.js / Express)
↓
MongoDB (Database)

(All services containerized using Docker Compose)


---

## 🐳 Docker Setup

This project uses Docker Compose to run 3 services:

- `web` → React frontend  
- `api` → Node.js backend  
- `db` → MongoDB database  

### Key Features:
- Multi-container setup
- Service-to-service communication via Docker network
- Persistent data using Docker volumes

---

## 🚀 How to Run Locally


docker compose up --build

Then open:
Frontend → http://localhost:5173
Backend → http://localhost:8000
