# Validation Strategy – Pons.fi

## 1. Purpose

This document describes the validation approach used in the Pons.fi backend.

The goal is to:

- Ensure data correctness
- Prevent invalid or unsafe input
- Improve system reliability
- Demonstrate professional backend practices

---

## 2. Current Approach

Validation is implemented using `class-validator`.

The project currently uses entity-based validation together with TypeScript models and centralized error handling.

Validation is applied at the **entity level**, ensuring that data stored in the database meets defined constraints.

Example:

- Required fields (email, password)
- Field formats (email)
- Optional fields (phone number)

---

## 3. Validation Flow

The validation process follows this sequence:

```text
Request → Controller → Entity → validate() → Error / Success
```

### Steps:

1. User sends request
2. Controller maps input to entity
3. `validate(entity)` is called
4. If errors exist → throw AppError
5. If valid → save to database

---

## 4. Example (createTrainer)

```ts
const user = new User();
user.email = email;
user.password = password;

const errors = await validate(user);

if (errors.length > 0) {
  throw new AppError("Validation failed", 400, "VALIDATION_ERROR", errors);
}
```

---

## 5. Error Format

Validation errors are returned using the centralized error handling system:

```json
{
  "success": false,
  "message": "Validation failed",
  "code": "VALIDATION_ERROR",
  "details": [ ... ]
}
```

---

## 6. Strengths

- Centralized validation logic
- Reusable validation rules
- Integrated with entities
- Works seamlessly with error handling middleware
- TypeScript-friendly validation workflow
- Integrated with centralized AppError handling
- Consistent validation response structure

---

## 7. Limitations

- Validation occurs after data mapping (controller layer)
- No strict schema validation before entity creation
- Error messages may not be user-friendly
- Validation is still partially controller-dependent

---

## 8. Future Improvements

- Introduce schema-based validation (e.g., Zod)
- Validate input before creating entities
- Improve error message clarity
- Standardize validation across all endpoints
- Introduce reusable DTO validation schemas

---

## 9. Relation to Architecture

Validation is part of the backend architecture:

- Controllers initiate validation
- Entities define constraints
- Errors handled by middleware
- Validation integrates with centralized AppError middleware

This supports separation of concerns and improves maintainability.

---

## 10. Summary

Validation in Pons.fi ensures data integrity and reliability.

Combined with centralized error handling, it provides a structured and professional approach to managing user input and preventing invalid data from entering the system.

During Sprint 2, validation handling was improved together with centralized error handling to create more predictable API behavior and cleaner backend architecture.

This approach improves maintainability and supports future migration to schema-based validation solutions such as Zod.
