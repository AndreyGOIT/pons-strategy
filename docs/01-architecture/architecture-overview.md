# Architecture Overview – Pons.fi

## 1. Purpose

This document provides a high-level overview of the architecture of the Pons.fi system.  
The goal is to describe how the system is structured, how its main components interact, and what design principles guide its implementation.

This document is intended to:

- Demonstrate architectural understanding
- Provide a clear system-level view
- Support further technical decisions and evaluation

---

## 2. System Context

Pons.fi is a full-stack web application designed for a local sports organization.  
It replaces manual email-based workflows with a structured digital solution.

### Primary users:

- Administrators (club management)
- Coaches
- Participants / parents

### Core responsibilities:

- Enrollment management
- User role management
- Communication support
- Administrative control of training groups

---

## 3. High-Level Architecture

The system follows a **client–server architecture** with clear separation between frontend, backend, and data storage.

### Main components:

1. Frontend (React + TypeScript)
2. Backend (Node.js + Express)
3. Database (SQL)
4. External environment (deployment, hosting)

---

## 4. Component Breakdown

### 4.1 Frontend

The frontend is a single-page application built with React and TypeScript.

**Responsibilities:**

- User interface rendering
- Form handling
- Client-side validation
- Communication with backend API

**Key characteristics:**

- Component-based structure
- State management (local + global if applicable)
- Separation between UI and logic

---

### 4.2 Backend

The backend is implemented using Node.js with Express.

**Responsibilities:**

- API endpoint handling (REST)
- Business logic execution
- Authentication and authorization
- Data validation
- Communication with database

**Structure (conceptual):**

- Routes (API endpoints)
- Controllers (request handling)
- Services (business logic)
- Data access layer (DB interaction)

---

### 4.3 Database

A relational database (PostgreSQL / MariaDB) is used.

**Responsibilities:**

- Persistent data storage
- Data integrity
- Relationship management

**Key aspects:**

- Structured schema
- Relations between users, enrollments, and groups
- Support for transactional operations

---

### 4.4 API Layer

The frontend and backend communicate via a REST API.

**Characteristics:**

- JSON-based communication
- Stateless requests
- Clear endpoint structure

---

## 5. Data Flow (Simplified)

1. User interacts with UI (frontend)
2. Frontend sends HTTP request to backend API
3. Backend processes request:
   - validates input
   - applies business logic
   - interacts with database
4. Backend returns response
5. Frontend updates UI accordingly

---

## 6. Architectural Principles

The system is guided by the following principles:

### Separation of Concerns

Each layer has a clearly defined responsibility.

### Modularity

Components are structured to allow independent development and modification.

### Maintainability

Code is organized to support long-term evolution.

### Scalability (basic level)

Architecture allows future extension (e.g., new features, roles, endpoints).

### Simplicity

Solutions are chosen to match project scope without unnecessary complexity.

---

## 7. Strengths of Current Architecture

- Clear separation between frontend and backend
- Use of widely adopted technologies
- Structured API communication
- Suitable for real-world operational use
- Flexible for incremental improvements

---

## 8. Known Limitations

- Limited formalization of architecture (initially implementation-driven)
- Potential tight coupling in some backend areas
- Error handling and validation may require centralization
- Limited testing coverage (to be improved)

---

## 9. Future Improvements (Planned)

- Introduce clearer service layer separation
- Centralized error handling strategy
- Improved validation (schema-based)
- Enhanced documentation of architectural decisions (ADR)
- CI/CD integration and deployment standardization

---

## 10. Relation to Näyttö Criteria

This architecture demonstrates:

- Understanding of system structure
- Ability to design and justify technical solutions
- Integration of frontend, backend, and database
- Foundation for further professional improvements

---

## 11. Summary

The Pons.fi system is built as a structured full-stack application with a clear separation of responsibilities between layers.

While initially developed as a practical solution, the architecture is being refined to meet professional standards, improve maintainability, and support long-term development.

This document serves as a foundation for deeper architectural analysis and decision-making.
