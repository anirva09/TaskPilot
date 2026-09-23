# TaskPilot

**TaskPilot** is a modern, full-stack task management platform designed to help individuals organize, track, and manage their work efficiently. It provides secure authentication, task management, productivity analytics, calendar scheduling, and personalized user settings through a responsive web interface.

Built with **React, TypeScript, Vite, Java, Spring Boot, PostgreSQL, and JWT-based security**, TaskPilot follows a layered architecture designed for maintainability, scalability, and clean separation of concerns.

---

## 🚀 Key Features

### 🔐 Authentication & Security

* JWT-based authentication
* Secure user registration and login
* Role-based authorization
* BCrypt password hashing
* Protected REST APIs
* Secure session and token management
* Spring Security integration

### 📋 Task Management

* Create, read, update, and delete tasks
* Task status management:

  * Not Started
  * In Progress
  * Completed
* Priority management:

  * Low
  * Medium
  * High
* Due date tracking
* Task categorization
* Search tasks by title and description
* Filter tasks by status and priority
* Sort tasks by priority and date
* Bulk task operations

### 📊 Dashboard & Analytics

* Centralized productivity dashboard
* Task statistics and summaries
* Task distribution visualization
* Progress indicators
* Recent task activity
* Quick task creation
* Productivity insights

### 📅 Calendar

* Dedicated task calendar
* Month, week, and day views
* Task deadline visualization
* Schedule management
* Drag-and-drop task scheduling

### 🎨 User Interface

* Responsive React interface
* Light and dark themes
* Customizable visual preferences
* Collapsible navigation sidebar
* Responsive layouts for different screen sizes
* Reusable UI components
* Smooth client-side navigation

### ⚙️ User Settings

* Profile management
* Personal information editing
* Profile picture management
* Theme preferences
* Password management
* Password strength validation
* User preference synchronization

---

## 🛠️ Technology Stack

### Frontend

| Technology    | Purpose                       |
| ------------- | ----------------------------- |
| React 18      | UI development                |
| TypeScript    | Type-safe development         |
| Vite          | Frontend build tool           |
| React Router  | Client-side routing           |
| CSS3          | Styling and responsive design |
| Lucide React  | UI icons                      |
| React Context | Application state management  |

### Backend

| Technology      | Purpose                          |
| --------------- | -------------------------------- |
| Java 17+        | Backend development              |
| Spring Boot 3.x | REST API framework               |
| Spring Security | Authentication and authorization |
| JWT             | Stateless authentication         |
| Spring Data JPA | Database access                  |
| PostgreSQL      | Relational database              |
| Maven           | Dependency and build management  |

### Development

* Git & GitHub
* RESTful API architecture
* Layered backend architecture
* DTO-based API communication
* Exception handling
* Unit and integration testing
* Feature-based Git workflow

---

## 🏗️ Architecture

TaskPilot follows a layered architecture to separate API handling, business logic, data access, and security responsibilities.

```text
                    ┌─────────────────────┐
                    │      React UI       │
                    │ TypeScript + Vite   │
                    └──────────┬──────────┘
                               │
                               │ REST API
                               ▼
                    ┌─────────────────────┐
                    │    Controllers      │
                    │   REST Endpoints    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │      Services       │
                    │   Business Logic    │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    Repositories     │
                    │   Data Access       │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │     PostgreSQL      │
                    │      Database       │
                    └─────────────────────┘
```

Authentication and authorization are handled through **Spring Security and JWT**.

---

## 📁 Project Structure

```text
TaskPilot/
│
├── backend/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/taskpilot/
│   │   │   │       ├── config/
│   │   │   │       ├── controller/
│   │   │   │       ├── dto/
│   │   │   │       ├── exception/
│   │   │   │       ├── mapper/
│   │   │   │       ├── model/
│   │   │   │       ├── repository/
│   │   │   │       ├── security/
│   │   │   │       └── service/
│   │   │   │
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   │
│   │   └── test/
│   │
│   └── pom.xml
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── context/
│   │   ├── hooks/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── styles/
│   │   ├── types/
│   │   └── utils/
│   │
│   ├── public/
│   ├── package.json
│   └── vite.config.ts
│
├── docs/
│   └── imgs/
│
└── README.md
```

---

## ⚙️ Getting Started

### Prerequisites

Make sure the following are installed:

* Node.js 18+
* npm
* Java 17+
* Maven
* PostgreSQL
* Git

---

### 1. Clone the Repository

```bash
git clone https://github.com/anirva09/TaskPilot.git
cd TaskPilot
```

---

### 2. Configure PostgreSQL

Create a PostgreSQL database for TaskPilot.

Example:

```sql
CREATE DATABASE taskpilot;
```

Configure the database connection in:

```text
backend/src/main/resources/application.properties
```

Example:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/taskpilot
spring.datasource.username=YOUR_USERNAME
spring.datasource.password=YOUR_PASSWORD
```

---

### 3. Start the Backend

```bash
cd backend
mvn clean install
mvn spring-boot:run
```

The Spring Boot API will start on the configured port.

---

### 4. Start the Frontend

Open another terminal:

```bash
cd frontend
npm install
npm run dev
```

Vite will start the frontend development server.

---

## 🔑 Authentication Flow

TaskPilot uses JWT-based authentication.

```text
User
 │
 │ Login
 ▼
React Frontend
 │
 │ POST /api/auth/login
 ▼
Spring Security
 │
 │ Validate credentials
 ▼
Authentication Service
 │
 │ Generate JWT
 ▼
React Frontend
 │
 │ Store authentication state
 ▼
Protected API Requests
 │
 │ Authorization: Bearer <token>
 ▼
Spring Security Filter
 │
 ▼
Protected Controller
```

This allows the backend to remain stateless while protecting authenticated API endpoints.

---

## 🔌 REST API

The backend exposes RESTful endpoints for authentication and task management.

Example endpoint structure:

```text
/api/auth
    POST   /register
    POST   /login

/api/tasks
    GET    /
    GET    /{id}
    POST   /
    PUT    /{id}
    DELETE /{id}

/api/users
    GET    /profile
    PUT    /profile
```

The API follows standard HTTP methods and uses DTOs to separate API contracts from persistence models.

---

## 🧪 Testing

Backend tests can be executed using Maven:

```bash
cd backend
mvn test
```

The project is structured to support:

* Unit testing
* Service-layer testing
* Controller testing
* Repository testing
* Integration testing

---

## 🔄 Development Workflow

TaskPilot follows a feature-oriented Git workflow.

```text
main
 │
 ├── feature/task-management
 │
 ├── feature/authentication
 │
 ├── feature/dashboard
 │
 └── feature/calendar
```

Typical workflow:

```bash
git checkout -b feature/task-management

git add .

git commit -m "Add task management functionality"

git push origin feature/task-management
```

Changes can then be reviewed before being merged into `main`.

---

## 🔮 Future Enhancements

Planned improvements include:

* 👥 Team workspaces
* 🤝 Collaborative task management
* 📈 Advanced productivity analytics
* 🔔 Email and push notifications
* 🔗 Third-party integrations
* 📱 Mobile applications
* 📤 PDF and Excel exports
* 🔄 Recurring tasks
* 💬 Task comments
* 📎 File attachments
* 🏷️ Advanced labels and tagging
* 🤖 AI-assisted task organization

---

## 📌 Project Goals

TaskPilot was developed to demonstrate practical experience with:

* Full-stack application development
* React and TypeScript
* Java and Spring Boot
* REST API development
* JWT authentication
* Spring Security
* PostgreSQL
* JPA/Hibernate
* Layered architecture
* Frontend state management
* API integration
* Testing
* Git-based development workflows

---

## 📄 License

This
