# Backend Architecture – Pons.fi

## 1. Purpose

This document describes the architecture of the backend system of Pons.fi.  
It focuses on structure, responsibilities, data flow, and design decisions behind the server-side implementation.

The goal is to demonstrate:

- Clear separation of responsibilities
- Structured backend design
- Maintainability and scalability considerations

---

## 2. Technology Stack

The backend is built using:

- Node.js (runtime environment)
- Express (web framework)
- SQL database (PostgreSQL / MariaDB)

Supporting tools:

- Environment configuration (dotenv or similar)
- Authentication libraries (e.g., JWT-based)
- Validation libraries (planned/improving)

---

## 3. Architectural Style

The backend follows a **layered architecture**:

```
Client → Routes → Controllers → Services → Data Access Layer → Database
```

Each layer has a clearly defined responsibility and communicates only with adjacent layers.

---

## 4. Layer Responsibilities

### 4.1 Routes Layer

**Purpose:**
Defines API endpoints and maps them to controller functions.

**Responsibilities:**

- URL structure definition
- HTTP method handling (GET, POST, PUT, DELETE)
- Middleware integration (auth, validation)

**Example:**

```
POST /api/enrollments
GET /api/users
```

---

### 4.2 Controllers Layer

**Purpose:**
Handles incoming requests and outgoing responses.

**Responsibilities:**

- Extract request data
- Call appropriate service functions
- Return formatted responses
- Handle basic errors

**Important:**
Controllers should remain thin and not contain business logic.

---

### 4.3 Service Layer

**Purpose:**
Contains core business logic.

**Responsibilities:**

- Implement application rules
- Coordinate multiple operations
- Validate business conditions
- Prepare data for persistence

**Examples:**

- Enrollment processing
- Role-based access decisions
- Group assignment logic

---

### 4.4 Data Access Layer (DAL)

**Purpose:**
Handles communication with the database.

**Responsibilities:**

- Execute SQL queries
- Map database results to application models
- Isolate database logic from business logic

**Benefits:**

- Easier refactoring
- Database independence (to some extent)
- Cleaner service layer

---

### 4.5 Database

Relational database used for persistent storage.

**Key entities (conceptual):**

- Users
- Enrollments
- Groups
- Roles

**Characteristics:**

- Structured schema
- Foreign key relationships
- Support for transactions

---

## 5. Request Lifecycle (Example)

Example: User submits enrollment form

1. Frontend sends POST request to `/api/enrollments`
2. Route forwards request to controller
3. Controller extracts data and calls service
4. Service:
   - validates business rules
   - calls DAL to store data
5. DAL executes SQL query
6. Database stores data
7. Response is returned through layers back to client

---

## 6. Authentication and Authorization

The backend implements role-based access control.

**Authentication:**

- User identity verification (e.g., JWT)

**Authorization:**

- Role-based permissions (admin, coach, user)

**Responsibility split:**

- Middleware: verifies token
- Services: enforce business-level permissions

---

## 7. Error Handling Strategy

(Current state: partially implemented, improving)

**Goals:**

- Centralized error handling
- Consistent error responses
- Clear separation between operational and system errors

**Planned improvements:**

- Global error middleware
- Standard error format
- Logging integration

---

## 8. Validation Strategy

(Current: partially implemented)

**Levels of validation:**

- Request-level validation (input format)
- Business validation (rules inside services)

**Planned improvements:**

- Schema-based validation (e.g., Zod / Joi)
- Reusable validation modules

---

## 9. Configuration Management

Environment-based configuration is used.

**Examples:**

- Database connection
- Port settings
- Secret keys

**Goal:**

- Separate configuration from code
- Enable multiple environments (development, production)

---

## 10. Strengths of Current Backend

- Clear layered structure (conceptually)
- Separation between request handling and logic
- REST API design
- Real-world usage validation
- Flexible for refactoring and improvement

---

## 11. Known Limitations

- Some business logic may still exist in controllers
- Incomplete separation of service and data layers
- Error handling not fully centralized
- Validation not fully standardized
- Limited automated testing

---

## 12. Planned Improvements

- Strengthen service layer abstraction
- Fully isolate database access
- Introduce centralized error handling
- Implement schema validation
- Add logging system
- Improve testability (unit + integration)

---

## 13. Relation to Overall Architecture

The backend acts as the central processing unit of the system:

- Connects frontend and database
- Enforces business rules
- Controls data flow and security

It is designed to be independent from frontend implementation and adaptable to future extensions.

---

## 14. Summary

The backend of Pons.fi is structured as a layered system built with Node.js and Express.

While initially developed with a focus on functionality, it is being progressively refined into a more modular, maintainable, and professionally structured architecture.

This evolution supports both real-world usage and the requirements of the näyttö evaluation.
