# PathSync

**A student-focused academic management application.**

PathSync is a computer science capstone project designed to provide students with an interactive platform for accessing academic tools and information. The application uses a React and TypeScript frontend, a Java Spring Boot backend, and a PostgreSQL database.

This repository serves as the central documentation hub for PathSync, connecting the frontend and backend codebases and providing an overview of the project's goals, architecture, technology stack, and setup process.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Screenshots](#screenshots)
- [Technology Stack](#technology-stack)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Repository Links](#repository-links)
- [Future Improvements](#future-improvements)

---

## Project Overview

PathSync is being developed as a student-focused academic management application and computer science capstone project.

The project separates its frontend and backend into independent codebases, allowing the user interface, application logic, and data persistence to be developed and maintained as distinct components.

### Project Goals

- Provide an interactive user interface.
- Connect the frontend to a dedicated REST API.
- Organize application logic within a Spring Boot backend.
- Use PostgreSQL for relational data storage.
- Maintain a modular codebase that supports future development.
- Document the implementation for academic review and continued development.

### Current Development Status

The frontend and backend have been organized into separate GitHub repositories.

The backend includes Spring Boot configuration, REST controllers, data models, and repositories. The frontend uses React, TypeScript, and Vite.

PathSync remains a work in progress, with additional enhancements planned as development continues.

---

## Screenshots

Screenshots will be added here to demonstrate the application's interface, design, and functionality.

<!-- Add screenshots to a screenshots/ directory and update the image paths below. -->

### Application Overview

![PathSync application overview](screenshots/pathsync-overview.png)

### Additional Screens

Potential additions include:

- Main application interface
- Student-related interface
- Course-related interface
- API interaction demonstrations

*Note: The screenshot above is a placeholder until an actual image is added to the repository.*

---

## Technology Stack

| Technology | Purpose |
|---|---|
| React | Frontend user interface |
| TypeScript | Type-safe frontend development |
| Vite | Frontend development server and build tooling |
| Java 21 | Backend programming language |
| Spring Boot | Backend application framework |
| Spring Data JPA | Database access and persistence |
| Hibernate | Object-relational mapping |
| PostgreSQL | Relational database |
| Maven | Backend dependency management and build tooling |
| Git and GitHub | Version control and source code hosting |

---

## Architecture

PathSync uses a separated frontend-backend architecture. The frontend communicates with the backend through HTTP requests to REST API endpoints, while the backend manages application logic and database interactions.

### High-Level Architecture

```text
┌──────────────────────────────┐
│        User / Browser        │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│           Frontend           │
│                              │
│       React + TypeScript     │
│             Vite             │
└──────────────┬───────────────┘
               │
               │ HTTP / REST API
               ▼
┌──────────────────────────────┐
│           Backend            │
│                              │
│           Java 21            │
│         Spring Boot          │
│                              │
│ Controllers / Models         │
│ Repositories                 │
└──────────────┬───────────────┘
               │
               │ Database access
               ▼
┌──────────────────────────────┐
│           Database           │
│                              │
│          PostgreSQL          │
└──────────────────────────────┘
```

### Component Responsibilities

**Frontend**

The frontend provides the user-facing interface. React and TypeScript organize the interface and its behavior, while Vite supports local development and production builds.

**Backend**

The backend exposes REST API endpoints and organizes application functionality through Spring Boot controllers, models, and repositories.

**Database**

PostgreSQL provides relational data storage. Spring Data JPA and Hibernate support database access and object-relational mapping.

### Example API Endpoint

The backend includes a student ID validation endpoint:

```http
GET /api/students/validate?studentId=PS1001
```

A successful validation request returns a JSON response similar to:

```json
{
  "valid": true,
  "message": "Student ID recognized"
}
```

When the backend is running locally on port `8083`, the complete endpoint is:

```text
http://localhost:8083/api/students/validate?studentId=PS1001
```

---

## Getting Started

The following instructions describe how to prepare the frontend and backend for local development.

### Prerequisites

- Git
- Node.js and npm
- Java Development Kit (JDK) 21
- PostgreSQL 18
- A terminal or IDE capable of running the frontend and backend

### 1. Clone the Repositories

Clone the frontend and backend repositories separately:

```bash
git clone https://github.com/poeticmaestro-hub/PathSync-Frontend.git
git clone https://github.com/poeticmaestro-hub/PathSync-Backend.git
```

### 2. Configure the Database

Create a PostgreSQL database named:

```text
pathsync
```

Configure a PostgreSQL user with the necessary permissions to access the database.

The backend reads its database connection settings from environment variables:

| Variable | Purpose |
|---|---|
| `DB_URL` | PostgreSQL JDBC connection URL |
| `DB_USERNAME` | PostgreSQL username |
| `DB_PASSWORD` | PostgreSQL password |

For local development, the JDBC URL can use this format:

```text
jdbc:postgresql://localhost:5432/pathsync
```

Set the environment variables in your terminal or development environment before starting the backend. Never commit database passwords, API keys, or other secrets to GitHub.

### 3. Start the Backend

Open a terminal in the cloned `PathSync-Backend` directory.

In Windows PowerShell, configure the environment variables:

```powershell
$env:DB_URL = "jdbc:postgresql://localhost:5432/pathsync"
$env:DB_USERNAME = "your_database_username"
$env:DB_PASSWORD = "your_database_password"
```

Replace the example credentials with your local database credentials.

Start the backend using the Maven Wrapper:

```powershell
.\mvnw.cmd spring-boot:run
```

The backend is configured to run on port `8083`.

Test the student ID validation endpoint at:

```text
http://localhost:8083/api/students/validate?studentId=PS1001
```

### 4. Start the Frontend

Open a separate terminal in the cloned `PathSync-Frontend` directory.

Install the dependencies:

```bash
npm install
```

Start the Vite development server:

```bash
npm run dev
```

Open the local address printed by Vite in your browser.

**Frontend-backend communication:** The frontend must use the correct backend API address. Any required API base URL or CORS configuration should match the actual project configuration.

### 5. Development Notes

- Keep the frontend and backend running in their respective terminals during local development.
- Keep database credentials in environment variables rather than source code.
- Do not commit `.env` files containing secrets.
- Consult the individual repositories for additional configuration details.

---

## Repository Links

PathSync is organized into three repositories.

| Repository | Description |
|---|---|
| [PathSync-Project](https://github.com/poeticmaestro-hub/PathSync-Project) | Main project overview and documentation |
| [PathSync-Frontend](https://github.com/poeticmaestro-hub/PathSync-Frontend) | React and TypeScript frontend |
| [PathSync-Backend](https://github.com/poeticmaestro-hub/PathSync-Backend) | Java and Spring Boot backend |

The frontend and backend repositories contain the application source code. This repository serves as the central documentation and project overview.

---

## Future Improvements

PathSync is an evolving project. Potential areas for future development include:

- **Expanded academic management functionality:** Continue developing and refining student- and course-related features.
- **Frontend-backend integration:** Strengthen communication between the user interface and backend services.
- **Validation and error handling:** Improve input validation, API error responses, and user feedback.
- **Testing:** Expand automated testing for backend functionality and frontend behavior.
- **Security:** Strengthen authentication, authorization, input validation, and secure configuration where appropriate.
- **User experience:** Continue refining the interface, accessibility, and responsive behavior.
- **Documentation:** Add screenshots, API documentation, and detailed development instructions.
- **Deployment:** Explore deployment options for the frontend, backend, and database.

These items are potential improvements, not claims that the functionality is already implemented.

---

## Project Information

**Project:** PathSync  
**Purpose:** Academic management application and computer science capstone  
**Frontend:** React, TypeScript, and Vite  
**Backend:** Java 21 and Spring Boot  
**Database:** PostgreSQL

For implementation details, visit the [frontend repository](https://github.com/poeticmaestro-hub/PathSync-Frontend) or the [backend repository](https://github.com/poeticmaestro-hub/PathSync-Backend).
