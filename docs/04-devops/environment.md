# Environment Configuration – Pons.fi

## 1. Purpose

This document describes the environment configuration used in the Pons.fi project.

The goal is to:

- Separate configuration from source code
- Improve deployment flexibility
- Protect sensitive information
- Support different environments (development / production)

---

## 2. Environment Variables

### Multiple Environment Files

The project uses separate environment configurations for development and production.

Example:

- `.env.development` → local development environment
- `.env` → production environment

The active environment file is selected dynamically based on the `NODE_ENV` value.

The backend uses a `.env` file to store configuration values.

Example:

```env
PORT=
DB_HOST=
DB_USER=
DB_PASSWORD=
JWT_SECRET=
```

---

## 3. Main Configuration Variables

### PORT

Defines the server port used by the backend application.

Example:

```env
PORT=5000
```

---

### DB_HOST

Database server address.

Example:

```env
DB_HOST=localhost
```

---

### DB_USER

Database username used for authentication.

---

### DB_PASSWORD

Database password.

This value must never be committed to Git.

---

### JWT_SECRET

Secret key used for signing JWT authentication tokens.

Security note:

- Must remain private
- Should be strong and unpredictable
- Different values should be used in development and production

---

## 4. Configuration Principles

### Separation of Concerns

Sensitive configuration is separated from application code.

Benefits:

- Better security
- Easier deployment
- Environment flexibility

---

### Git Safety

The `.env` file is excluded from Git using `.gitignore`.

This prevents accidental exposure of:

- passwords
- secrets
- production configuration

---

## 5. Development vs Production

Different environments may use different values.

Examples:

| Variable   | Development  | Production               |
| ---------- | ------------ | ------------------------ |
| PORT       | 5000         | 80 / 443                 |
| DB_HOST    | localhost    | production database      |
| JWT_SECRET | local secret | secure production secret |

### Environment Selection Logic

The backend dynamically selects which environment file to load.

This logic is implemented in:

- `src/data-source.ts`

Example:

```ts
const envFile =
  process.env.NODE_ENV === "production" ? ".env" : ".env.development";
```

This approach provides:

- safer local development
- separation between development and production databases
- flexible deployment configuration
- reduced risk of accidentally using production settings during development

Example:

- Development → SQLite (`.env.development`)
- Production → MySQL / MariaDB (`.env`)

---

## 6. Deployment Relation

Environment variables are required for:

- Backend startup
- Database connection
- Authentication
- Secure deployment

Without correct environment configuration, the application cannot run properly.

---

## 7. Security Considerations

Security-related practices:

- `.env` excluded from repository
- Secrets stored outside source code
- JWT secret protected
- Production credentials separated from development

---

## 8. Future Improvements

Possible future improvements:

- `.env.example` template
- Secret management system
- Environment validation on startup
- Docker environment configuration

---

## 9. Summary

Environment configuration in Pons.fi supports secure and flexible deployment.

Using environment variables improves maintainability, portability, and security while keeping sensitive data separated from the application source code.
