# Sprint 2 – Quality & Professionalization

## 1. Sprint Overview

Sprint 2 focused on improving the quality, reliability, and maintainability of the Pons.fi backend.

The goal was to transform an already working system into a more structured and professional solution by introducing consistent error handling, validation, and cleaner architecture.

---

## 2. Sprint Goals

- Introduce centralized error handling
- Standardize API error responses
- Implement validation strategy
- Improve backend structure
- Reduce code duplication
- Strengthen TypeScript usage

---

## 3. Work Completed

### 3.1 Centralized Error Handling

Implemented global error handling middleware:

- `errorHandler.ts` (Express middleware)
- Standardized error format:
  ```
  {
    success: false,
    message: string,
    code: string
  }
  ```

Applied across all admin endpoints.

---

### 3.2 catchAsync Wrapper

Introduced async wrapper:

- `catchAsync.ts`

Purpose:

- Remove try/catch from controllers
- Automatically forward errors to middleware

---

### 3.3 Controller Refactoring

Refactored multiple endpoints:

- adminLogin
- getUsers
- getTrainers
- createTrainer
- deleteTrainer
- assignTrainerToCourse
- unassignTrainerFromCourse
- generateCourseSessions
- getCourseSessions
- deleteCourseSession

Changes:

- Removed inline try/catch
- Replaced manual responses with `throw error`
- Unified error handling flow

---

### 3.4 Typed Error Model

Introduced:

- `AppError` type

Used to:

- Add `status`, `code`, and `details`
- Replace `any`
- Improve type safety

---

### 3.5 Validation

Implemented validation using `class-validator`:

- Validation at entity level
- Integrated with error handling

Example:

- createTrainer endpoint validates input before saving

---

### 3.6 Code Quality Improvements

- Removed duplicated error handling logic
- Improved readability of controllers
- Enforced separation of concerns
- Standardized response patterns

---

## 4. Architectural Improvements

Key improvements:

- Controllers simplified (orchestration only)
- Business logic separated from error handling
- Middleware used for cross-cutting concerns
- Clear error propagation chain:

```
Controller → catchAsync → next(err) → errorHandler
```

---

## 5. Challenges

- Transition from inline error handling to centralized approach
- Ensuring backward compatibility with frontend
- Avoiding breaking changes in API responses
- Managing TypeScript typing without overcomplication

---

## 6. Solutions

- Incremental refactoring (endpoint by endpoint)
- Preserved success response format
- Introduced AppError for safe typing
- Tested critical endpoints after each change

---

## 7. Näyttö Criteria Coverage

### Covered areas:

- Backend architecture improvement
- Error handling strategy
- Validation and data integrity
- Code quality and maintainability
- TypeScript usage

### Target level:

Hyvä 4 → Kiitettävä 5

---

## 8. Reflection

This sprint marked a transition from a functional system to a more professional and maintainable architecture.

Key learning points:

- Importance of centralized error handling
- Value of consistent API design
- Role of validation in system reliability
- Benefits of TypeScript for enforcing structure
- Incremental refactoring as a safe strategy

---

## 9. Next Steps (Sprint 3)

- Deployment and production setup
- Security improvements
- Final architectural refinements
- Complete documentation
- Final näyttö preparation

---

## 10. Summary

Sprint 2 successfully improved the internal quality of the Pons.fi system.

The backend is now more consistent, maintainable, and aligned with professional software development practices.
