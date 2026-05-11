# Error Handling Strategy – Pons.fi

## 1. Purpose

This document describes the error handling strategy used in the Pons.fi backend.

The goal is to:

- Provide consistent error responses
- Improve reliability and debugging
- Demonstrate professional backend practices

---

## 2. Current State

Initially, error handling was implemented directly inside controllers.

Limitations:

- Inconsistent error responses
- Repeated logic
- Harder to maintain and debug

---

## 3. Target Approach

The system introduces a **centralized error handling strategy**.

Key principles:

- All errors are passed to a global error handler
- Controllers remain clean (no heavy error logic)
- Responses follow a consistent structure

---

## 4. Error Response Format

All API errors follow this structure:

```json
{
  "success": false,
  "message": "Error description",
  "code": "ERROR_CODE"
}
```

### Example:

```json
{
  "success": false,
  "message": "User not found",
  "code": "USER_NOT_FOUND"
}
```

---

## 5. Implementation (Backend)

### 5.1 Global Error Middleware

```ts
import { Request, Response, NextFunction } from "express";
import { AppError } from "../../server/src/utils/AppError";

export const globalErrorHandler = (
  err: any,
  req: Request,
  res: Response,
  next: NextFunction,
) => {
  console.error("💥 ERROR:", err);

  if (err instanceof AppError) {
    return res.status(err.status).json({
      success: false,
      message: err.message,
      code: err.code,
      details: err.details,
    });
  }

  return res.status(500).json({
    success: false,
    message: "Internal server error",
    code: "INTERNAL_ERROR",
  });
};
```

---

### 5.2 Usage in Express App

```ts
import { globalErrorHandler } from "./middlewares/errorMiddleware";

app.use(globalErrorHandler);
```

---

### 5.3 Throwing Errors in Services

```ts
throw new AppError("User not found", 404, "USER_NOT_FOUND");
```

---

### 5.4 Controller Example

```ts
export const getUser = catchAsync(async (req, res) => {
  const user = await userService.getUserById(req.params.id);

  if (!user) {
    throw new AppError("User not found", 404, "USER_NOT_FOUND");
  }

  res.json({
    success: true,
    data: user,
  });
});
```

---

### 5.5 AppError Class

The backend uses a custom `AppError` class to standardize operational errors.

Main features:

- HTTP status support
- Error code support
- Optional validation details
- Better TypeScript compatibility
- Cleaner controller logic

Example:

```ts
throw new AppError(
  "Validation failed",
  400,
  "VALIDATION_ERROR",
  validationErrors,
);
```

---

## 6. Error Types

### Operational Errors

- User not found
- Invalid input
- Unauthorized access

Handled and returned to client.

---

### System Errors

- Database failure
- Unexpected exceptions

Logged and returned as generic errors.

---

## 7. Benefits

- Consistent API responses
- Cleaner controller logic
- Easier debugging
- Better maintainability
- Improved user experience
- Better API consistency across controllers
- Easier frontend integration
- Improved TypeScript type safety

---

## 8. Future Improvements

- Add structured logging (e.g., Winston)
- Add error tracking (monitoring)
- Standardize error codes across system

---

## 9. Relation to Architecture

Error handling is part of backend architecture:

- Controllers delegate errors
- Services define business errors
- Middleware handles responses

This supports separation of concerns.

---

## 10. Summary

The centralized error handling strategy improves reliability, maintainability, and clarity of the backend system.

It transforms error handling from ad-hoc implementation into a structured and professional practice.

During Sprint 2, the error handling strategy was fully integrated into the main backend controllers, including user, course, enrollment, trainer, contact, and payment management modules.

This refactoring significantly improved backend consistency and brought the project architecture closer to production-level practices.
