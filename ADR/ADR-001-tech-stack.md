ADR-001: Technology Stack Selection

Status

Accepted

⸻

Context

The Pons.fi system is a full-stack web application designed to replace manual enrollment workflows in a local sports organization.

The system requires:
• Web-based user interface
• Backend API
• Database for persistent storage
• Role-based authentication
• Maintainability and ease of development

The technology stack needed to support rapid development, clarity, and real-world usability.

⸻

Decision

The following technology stack was selected:

Frontend
• React
• TypeScript

Backend
• Node.js
• Express

Database
• Relational database (PostgreSQL / MariaDB)

Other
• REST API communication
• Git for version control

⸻

Rationale

React + TypeScript
• Component-based architecture
• Strong ecosystem
• Type safety improves reliability
• Suitable for scalable UI

Node.js + Express
• JavaScript across full stack
• Fast development cycle
• Lightweight and flexible
• Good ecosystem support

SQL Database
• Structured data (users, enrollments, groups)
• Strong relational support
• Data integrity and constraints
• Transaction support

REST API
• Simplicity and predictability
• Widely adopted standard
• Easy integration between frontend and backend

⸻

Alternatives Considered

Frontend
• Angular → more complex, heavier for project scope
• Vue → viable, but React chosen due to familiarity and ecosystem

Backend
• NestJS → more structured, but adds complexity for current scope
• .NET → strong option, but less aligned with current stack and learning goals

Database
• NoSQL (MongoDB)
• Pros: flexible schema
• Cons: weaker relational support
• Not suitable for structured relational data in this project

API
• GraphQL
• Pros: flexible queries
• Cons: added complexity
• REST chosen for simplicity

⸻

Consequences

Positive
• Fast development with unified language (JavaScript/TypeScript)
• Clear separation between frontend and backend
• Strong community support
• Suitable for current project scale

Negative
• Express requires manual structure (less opinionated)
• Potential need for refactoring as system grows
• Limited built-in structure compared to frameworks like NestJS

⸻

Future Considerations
• Possible migration to more structured backend (e.g., NestJS)
• Introduction of stricter architectural patterns
• Scaling considerations if user base grows

⸻

Summary

The selected technology stack provides a balance between simplicity, flexibility, and real-world applicability.

It enables efficient development while supporting the architectural and functional requirements of the Pons.fi system.

⸻

Implementation reference:
https://github.com/AndreyGOIT/pons-web
