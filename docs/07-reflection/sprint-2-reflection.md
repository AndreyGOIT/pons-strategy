# Sprint 2 Reflection

## 1. Sprint Goal

The main goal of Sprint 2 was to improve the technical quality and maintainability of the backend architecture.

The focus areas were:

- centralized error handling
- validation improvements
- backend structure consistency
- cleaner controller architecture
- preparation for production-level practices

---

# 2. Main Improvements

## 2.1 Centralized Error Handling

One of the most important improvements during Sprint 2 was the introduction of centralized backend error handling.

The backend was refactored to use:

- custom `AppError` objects
- reusable `catchAsync` wrappers
- global error middleware
- unified API response structure

Previously, many controllers used duplicated try/catch blocks and inconsistent error responses.

After the refactoring:

- backend behavior became more predictable
- controller code became cleaner
- frontend integration became easier
- debugging became simpler

Several major controllers were fully migrated to the new architecture:

- userController
- courseController
- enrollmentController
- trainerController
- membershipPaymentController
- contactController
- adminController

---

## 2.2 Validation Improvements

Validation handling was improved using:

- class-validator
- entity validation
- centralized validation error responses

Validation logic was integrated together with the new AppError architecture.

This improved:

- API consistency
- data integrity
- maintainability

At the same time, the project documentation was updated to describe the current validation strategy and future plans.

---

## 2.3 Backend Structure Improvements

Sprint 2 also focused on improving backend structure and separation of concerns.

Several architectural improvements were implemented:

- cleaner controller structure
- reusable backend utilities
- reduced duplicated logic
- clearer request flow
- improved TypeScript consistency

The backend architecture now better reflects professional software development practices.

---

# 3. Git Workflow

Development during Sprint 2 followed a structured Git workflow.

Changes were implemented using:

- dedicated feature branches
- small focused commits
- incremental refactoring
- regular pushes to GitHub

This improved:

- traceability
- development safety
- project organization

---

# 4. Challenges

The main challenges during Sprint 2 were:

- refactoring existing controllers without breaking functionality
- maintaining API consistency across different modules
- improving architecture while continuing feature development

The project already contained a large amount of working functionality, so careful incremental refactoring was important.

---

# 5. What I Learned

During Sprint 2, I improved my understanding of:

- backend architecture
- centralized error handling
- reusable middleware patterns
- API consistency
- TypeScript backend development
- maintainable project structure

I also learned how important architecture and code consistency become as a project grows.

---

# 6. Future Improvements

Planned future improvements include:

- DTO-based validation architecture
- stronger service layer separation
- structured logging
- automated testing
- CI/CD improvements

---

# 7. Summary

Sprint 2 transformed the project from a working backend system into a more structured and professionally organized software project.

The improvements implemented during this sprint significantly increased backend quality, maintainability, and architectural consistency.

This sprint was an important step toward production-level development practices and preparation for the final näyttö presentation.
