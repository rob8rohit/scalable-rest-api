# 🚀 Scalable REST API with Authentication & Role-Based Access

## 📘 Overview

This project is built as part of the **Backend Developer Internship Assignment**.
It implements a **secure, scalable REST API** with authentication, role-based access control, and a simple frontend UI for interacting with the APIs.

### 🔧 Tech Stack

**Backend:** Node.js, Express.js, PostgreSQL, Sequelize ORM
**Frontend:** React (Vite)
**Authentication:** JWT (JSON Web Token)
**API Documentation:** Swagger UI / Postman Collection
**Deployment:** Docker & Docker Compose

---

## 🗂️ Project Structure

```
.
├── backend/
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middlewares/
│   │   ├── models/
│   │   ├── routes/
│   │   └── app.js
│   ├── .env.example
│   ├── Dockerfile
│   ├── docker-compose.yml
│   ├── package.json
│   └── swagger.yaml
│
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   ├── api.js
│   │   └── App.jsx
│   ├── package.json
│   └── vite.config.js
│
├── README.md
└── postman_collection.json
```

---

## ⚙️ Features Implemented

### ✅ Backend

* User Registration & Login with password hashing (bcrypt)
* JWT Authentication & Role-Based Access (User/Admin)
* CRUD APIs for Tasks entity
* Input Validation (express-validator)
* Centralized Error Handling
* Secure Headers (Helmet) & XSS Protection
* API Versioning (`/api/v1`)
* Swagger UI for API documentation

### ✅ Frontend

* Built with React (Vite)
* Simple UI for:

  * Register & Login
  * Protected Dashboard (JWT required)
  * CRUD operations for Tasks
* Displays success/error messages from API

### ✅ Security

* Password hashing using bcrypt
* JWT-based stateless authentication
* Input sanitization using xss-clean
* Role-based route access (admin/user)

---

## 🏃‍♂️ Quick Start

### 1️⃣ Run using Docker (Recommended)

```bash
cd backend
docker-compose up --build
```

**Access Points:**

* Backend API: [http://localhost:4000/api/v1](http://localhost:4000/api/v1)
* Swagger Docs: [http://localhost:4000/docs](http://localhost:4000/docs)
* Postgres DB: localhost:5432

---

### 2️⃣ Manual Setup (Without Docker)

**Backend Setup**

```bash
cd backend
npm install
cp .env.example .env
# Update .env with your local PostgreSQL connection
npm run dev
```

**Frontend Setup**

```bash
cd frontend
npm install
npm run dev
```

Frontend runs on [http://localhost:5173](http://localhost:5173) (Vite default).

---

## 🔐 API Endpoints

### Authentication

| Method | Endpoint                | Description         |
| ------ | ----------------------- | ------------------- |
| POST   | `/api/v1/auth/register` | Register new user   |
| POST   | `/api/v1/auth/login`    | Login & receive JWT |

### Tasks

| Method | Endpoint            | Description                                | Access |
| ------ | ------------------- | ------------------------------------------ | ------ |
| GET    | `/api/v1/tasks`     | List tasks (admin sees all, user sees own) | Auth   |
| POST   | `/api/v1/tasks`     | Create new task                            | Auth   |
| GET    | `/api/v1/tasks/:id` | Get single task                            | Auth   |
| PUT    | `/api/v1/tasks/:id` | Update task                                | Auth   |
| DELETE | `/api/v1/tasks/:id` | Delete task                                | Auth   |

**Authorization Header:**

```
Authorization: Bearer <your_jwt_token>
```

---

## 🧠 Example Request

### Register User

```bash
POST /api/v1/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "mypassword"
}
```

### Login

```bash
POST /api/v1/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "mypassword"
}
```

### Create Task

```bash
POST /api/v1/tasks
Authorization: Bearer <token>
Content-Type: application/json

{
  "title": "Finish Assignment",
  "description": "Submit the backend project"
}
```

---

## 🧩 Database Schema (PostgreSQL)

**User Table**

| Field    | Type             | Description     |
| -------- | ---------------- | --------------- |
| id       | UUID (PK)        | Unique user ID  |
| name     | String           | User’s name     |
| email    | String           | Unique email    |
| password | String           | Hashed password |
| role     | Enum(user/admin) | Role            |

**Task Table**

| Field       | Type                             | Description       |
| ----------- | -------------------------------- | ----------------- |
| id          | UUID (PK)                        | Unique task ID    |
| title       | String                           | Task title        |
| description | Text                             | Task details      |
| status      | Enum(pending, in-progress, done) | Task state        |
| userId      | FK                               | Reference to user |

---

## 📄 API Documentation

After running backend:

* Swagger UI: **[http://localhost:4000/docs](http://localhost:4000/docs)**
* Postman Collection: `postman_collection.json` (included)

---

## 🧱 Scalability & Deployment Notes

| Area                 | Strategy                                                                        |
| -------------------- | ------------------------------------------------------------------------------- |
| **Architecture**     | Modular structure (auth, tasks, etc.) enabling microservice split.              |
| **Database Scaling** | Start with PostgreSQL, use read replicas, partitioning, and connection pooling. |
| **Caching Layer**    | Add Redis for frequently accessed data (e.g., user sessions, task list).        |
| **Load Balancing**   | Deploy behind Nginx or AWS ALB for traffic distribution.                        |
| **Security**         | Use HTTPS, JWT rotation, secret management, and rate-limiting.                  |
| **Observability**    | Use Winston for structured logs; integrate with Grafana/Prometheus for metrics. |
| **Containerization** | Dockerized app; can be deployed to ECS/Kubernetes.                              |
| **CI/CD**            | Automate builds, linting, and deployment with GitHub Actions.                   |

---

## 🧪 Evaluation Checklist

| Criteria                      | Status |
| ----------------------------- | ------ |
| RESTful API design            | ✅      |
| Authentication & JWT          | ✅      |
| Role-based Access             | ✅      |
| Secure Password Hashing       | ✅      |
| Validation & Error Handling   | ✅      |
| Swagger/Postman Documentation | ✅      |
| Database Schema               | ✅      |
| Functional Frontend           | ✅      |
| Scalability Notes             | ✅      |

---

## 👨‍💻 Author

**Name:** R ROHIT
**Role:** Backend Developer Intern Candidate
**Contact:** rob8rohit@gamil.com +917000313940
**Date:** October 2025

---

## 📚 License

This project is developed solely for educational and assessment purposes.
