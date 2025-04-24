# ClassConnect

**ClassConnect** is a full-stack educational management platform that enables seamless interaction between students and teachers. It offers functionalities such as course creation, assignments, exams, feedback, real-time chat, analytics, and AI-powered assistance.

---

## 📑 Table of Contents

- [🌐 Tech Stack](#-tech-stack)
- [🧱 Microservice Architecture (Layered Design)](#-microservice-architecture-layered-design)
- [🚀 Getting Started](#-getting-started)
- [🧪 Testing & Quality](#-testing--quality)
- [📦 Environment Variables](#-environment-variables)
- [📂 Infrastructure](#-infrastructure)
- [🔐 Security](#-security)
- [🧠 Authors](#-authors)
- [📄 License](#-license)
- [📌 Note](#-note)

---

## 🌐 Tech Stack

- **Frontend (Mobile App):** React Native (TypeScript)
- **Backend Services:** Nest.js (TypeScript) + Prisma
- **Databases:** PostgreSQL & MongoDB
- **Microservices Architecture:**
  - Each microservice is maintained in its own repository within the organization.
  - Updated microservices:
    - `users`: Handles authentication, user profiles, and roles.
    - `education`: Manages courses, assignments, exams, and feedback.
    - `communication`: Provides real-time chat and notifications.
    - `backoffice`: Handles platform-wide configuration and administrative roles.
    - `gateway`: A TypeScript-based intermediary that redirects endpoints to the appropriate microservices.
- **External Services:** Firebase, AWS (subject to change)
- **CI/CD:** GitHub Actions
- **Containerization & Deployment:** Docker, Docker Compose, Kubernetes (optional)
- **Real-time & Notifications:** Firebase Realtime Database, FCM, Twilio
- **Monitoring:** Prometheus + Grafana
- **Logging:** @nestjs/common Logger for structured and efficient logging.

---

## 🧱 Microservice Architecture (Layered Design)

Each Nest.js microservice follows a layered architecture:

```
src/
├── controllers/   # HTTP endpoints (REST)
├── services/      # Business logic
├── repositories/  # Data access layer (Prisma)
├── entities/      # Entities, DTOs, interfaces
├── modules/       # NestJS module declarations
└── main.ts        # App entrypoint
```

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/classconnect.git
cd classconnect
```

### 2. Install root dependencies (for npm workspaces)
```bash
npm install
```

### 3. Spin up infrastructure services (PostgreSQL, MongoDB)
```bash
cd infra
docker-compose up -d
```

### 4. Run microservices (example: users)
```bash
cd apps/users
npm install
npx prisma generate
npm run start:dev
```
Repeat for other services.

### 5. Run frontend (React Native)
```bash
cd apps/frontend-mobile
npm install
npx expo start
```

---

## 🧪 Testing & Quality

- **Linting:** ESLint
- **Testing:** Jest for unit testing and Supertest for integration testing.
- **Coverage:** > 75% expected
- **CI/CD:** GitHub Actions runs tests and checks on every commit

---

## 📦 Environment Variables

Each microservice has its own `.env` file (not committed). Example:

```
DATABASE_URL=postgresql://user:pass@localhost:5432/classconnect
JWT_SECRET=mysecretkey
PORT=3001
```

---

## 📂 Infrastructure

The `infra/` folder contains everything related to infrastructure:

- `docker-compose.yml`: Runs PostgreSQL, MongoDB, and optionally microservices
- `kubernetes/`: (optional) Manifests for deploying to a K8s cluster
- `env/`: Example `.env` templates for each service

---

## 🔐 Security

- **Authentication:** JWT-based auth for user identity (via `users` service)
- **Authorization:** Role-based access control (RBAC)
- **Integration:** Firebase and AWS for secure messaging and file storage
- **Logging:** Pino is used across all microservices for consistent and structured logging.

---

## 🧠 Authors

Made with ❤️ by Marcos, Manuel, Sol, Martín, and Lorenzo  
For the Software Engineering II course – 2025 (UBA)

---

## 📄 License

This project is licensed under the MIT License. See the LICENSE file for details.

---

## 📌 Note

This is a university project developed for academic purposes. Some features like AI-based grading, plagiarism detection, or Kubernetes deployment are under active development or optional.

For architecture diagrams, visit [ClassConnect Diagrams](https://app.diagrams.net/#G1UschOvO0-WKVGdOc6sW5xcUUgjp-m-75#%7B%22pageId%22%3A%227CLobzQo_xTtJIu9ze5o%22%7D).
