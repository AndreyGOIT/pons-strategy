Database Design – Pons.fi

1. Purpose

This document describes the database design of the Pons.fi system. It outlines the data model, key entities, relationships, and design decisions used to support the application’s functionality.

The goal is to demonstrate:
• Understanding of relational database design
• Clear mapping between business requirements and data structures
• Data integrity and consistency considerations

⸻

2. Database Technology

The system uses a relational database (PostgreSQL / MariaDB).

Reasons for choice:
• Structured data model (users, enrollments, groups)
• Strong support for relationships
• Transactional integrity (ACID)
• Wide industry adoption

⸻

3. Core Entities

3.1 Users

Represents all system users.

Fields (example):
• id (PK)
• name
• email
• password_hash
• role_id (FK)
• created_at

⸻

3.2 Roles

Defines user roles and permissions.

Fields:
• id (PK)
• name (admin, coach, user)

⸻

3.3 Groups

Represents training groups.

Fields:
• id (PK)
• name
• schedule
• coach_id (FK → Users)

⸻

3.4 Enrollments

Represents user participation in groups.

Fields:
• id (PK)
• user_id (FK)
• group_id (FK)
• status
• created_at

⸻

4. Relationships
   • Users → Roles (many-to-one)
   • Groups → Users (coach relationship)
   • Enrollments → Users (many-to-one)
   • Enrollments → Groups (many-to-one)

This structure supports:
• Flexible role management
• Clear enrollment tracking
• Separation between users and group assignments

⸻

5. Data Integrity

Constraints
• Primary keys for all entities
• Foreign keys for relationships
• Unique constraint on user email

Transactions

Used for operations like:
• Creating enrollment
• Updating group assignments

⸻

6. Normalization

The database is designed with basic normalization principles:
• No duplicated user data
• Roles separated into dedicated table
• Relationships handled via foreign keys

⸻

7. Example Data Flow

Enrollment process: 1. User submits form 2. Backend validates input 3. New record created in Enrollments 4. Linked to Users and Groups via foreign keys

⸻

8. Strengths
   • Clear relational structure
   • Scalable for additional entities
   • Supports role-based logic
   • Maintains data consistency

⸻

9. Limitations
   • Some constraints may not yet be fully enforced
   • Indexing strategy may require optimization
   • Limited documentation of schema evolution

⸻

10. Planned Improvements
    • Add indexes for performance
    • Expand schema documentation
    • Introduce migration strategy
    • Improve constraint definitions

⸻

11. Summary

The database design of Pons.fi provides a structured and reliable foundation for managing users, roles, groups, and enrollments.

It supports current functionality while allowing future extensions and improvements.
