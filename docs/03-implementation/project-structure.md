# Project Structure

## 1. Overview

The PONS project follows a modular full stack architecture with separate repositories for:

- application source code (`pons-web`)
- project strategy and documentation (`pons-strategy`)

The backend is implemented using:

- Node.js
- Express
- TypeScript
- TypeORM

The frontend is implemented as a separate React-based client application.

The structure was improved during Sprint 2 to increase maintainability, readability, and architectural consistency.

---

# 2. Backend Structure

Main backend source directory:

```text
server/src
├── controllers
├── routes
├── middlewares
├── services
├── models
├── dto
├── utils
├── migration
├── scripts
└── data-source.ts
```

---

## 2.1 Controllers

Controllers handle incoming HTTP requests and return API responses.

Responsibilities:

- request handling
- response formatting
- invoking business logic
- throwing operational errors

During Sprint 2, controllers were refactored to:

- use centralized error handling
- use `catchAsync`
- throw `AppError` instances
- remove duplicated try/catch blocks

Example controllers:

- `userController.ts`
- `courseController.ts`
- `enrollmentController.ts`
- `trainerController.ts`

---

## 2.2 Routes

Routes define API endpoints and connect them to controllers.

Example:

```ts
router.post("/login", loginUser);
```

Responsibilities:

- endpoint definitions
- middleware chaining
- controller mapping

---

## 2.3 Middlewares

Middlewares provide reusable request-processing logic.

Current middlewares:

- authentication middleware
- role-based access control
- admin-only protection
- global error middleware

Examples:

- `authMiddleware.ts`
- `adminOnly.ts`
- `roleMiddleware.ts`

---

## 2.4 Services

Services contain reusable business logic.

The service layer is currently partially implemented and will be expanded further in future iterations.

Goal:

```text
routes → controllers → services → database layer
```

This separation improves:

- maintainability
- scalability
- testability

---

## 2.5 Models

Models are implemented using TypeORM entities.

Examples:

- `User`
- `Course`
- `Enrollment`
- `MembershipPayment`
- `Attendance`

Responsibilities:

- database mapping
- validation decorators
- entity relationships

---

## 2.6 DTO

DTO (Data Transfer Object) structures are prepared for future validation improvements.

Current validation mainly relies on:

- entity validation
- class-validator
- request validation inside controllers

Future plans include:

- reusable DTO validation schemas
- centralized validation layer

---

## 2.7 Utils

Utility modules provide reusable helper functionality.

Important utilities introduced during Sprint 2:

- `catchAsync.ts`
- `AppError.ts`

These utilities support:

- centralized error handling
- cleaner controller logic
- reusable async wrappers

---

## 2.8 Migration

The project uses TypeORM migrations for production database management.

Development environment:

- SQLite
- synchronize enabled

Production environment:

- MySQL
- migrations enabled

---

# 3. Frontend Structure

The frontend is implemented as a separate client application.

Main responsibilities:

- UI rendering
- API communication
- authentication state handling
- admin dashboard
- enrollment and payment workflows

The frontend communicates with the backend through REST API endpoints.

---

# 4. Request Flow

Typical backend request flow:

```text
Client Request
    ↓
Route
    ↓
Middleware
    ↓
Controller
    ↓
Service / Repository
    ↓
Database
```

Error handling flow:

```text
Controller
    ↓
throw AppError
    ↓
globalErrorHandler
    ↓
Unified API response
```

---

# 5. Separation of Concerns

The project architecture follows separation of concerns principles.

Examples:

- routes define endpoints
- controllers handle requests
- middlewares handle authorization
- models define entities
- utils provide reusable helpers

This structure improves:

- readability
- maintainability
- scalability
- debugging

---

# 6. Improvements During Sprint 2

Major backend structure improvements implemented during Sprint 2:

- centralized error handling
- introduction of `AppError`
- reusable `catchAsync` wrapper
- controller cleanup
- unified API response structure
- reduction of duplicated logic
- improved TypeScript consistency

Several controllers were fully refactored:

- user management
- course management
- enrollments
- trainer functionality
- payment handling
- contact messaging

---

# 7. Benefits of Current Structure

Current architecture provides:

- cleaner backend code
- easier maintenance
- more predictable API behavior
- improved debugging
- easier onboarding for developers
- better scalability potential
- stronger TypeScript integration

---

# 8. Future Improvements

Planned future improvements:

- stronger service layer separation
- DTO-based validation architecture
- structured logging system
- automated backend tests
- API documentation generation
- dependency injection improvements

---

# 9. Summary

The project structure evolved significantly during Sprint 2.

The backend architecture is now more modular, maintainable, and aligned with professional software development practices.

The introduction of centralized error handling and reusable backend utilities significantly improved code quality and system consistency.
