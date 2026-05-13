# Deployment Strategy – Pons.fi

## 1. Purpose

This document describes the deployment approach used in the Pons.fi project.

The deployment strategy focuses on:

- simplicity
- reliability
- low operational overhead
- safe updates for a live production system

---

## 2. Deployment Context

Pons.fi is a real-world full-stack application used by an active sports organization.

Because the system is already in operational use, deployment changes must minimize the risk of downtime and breaking changes.

The project uses:

- React + TypeScript frontend
- Node.js + Express backend
- PM2 process management
- SSH-based deployment workflow

---

## 3. Production Structure

### Frontend

Frontend build output:

```text
client/dist
```

Production target:

```text
/data01/virt141059/domeenid/www.pons.fi/htdocs
```

---

### Backend

Backend build output:

```text
server/dist
```

Production target:

```text
/data01/virt141059/node/pons-server/dist
```

Backend process management:

```text
PM2
```

Process name:

```text
pons-api
```

---

## 4. Deployment Workflow

The deployment workflow includes:

1. Build frontend
2. Build backend
3. Upload frontend build
4. Upload backend build
5. Restart backend process using PM2

This approach provides a simple but effective production deployment pipeline.

---

## 5. Deployment Automation

Deployment is partially automated using a local deployment script.

The script:

- builds frontend and backend
- uploads files via SSH using rsync
- removes outdated production files
- restarts the backend service

---

## 6. Deployment Script Example

Example deployment script:

```bash
#!/bin/bash

SERVER="virt141059@sn-242-129.hel01.zoneas.eu"

echo "🔨 Building frontend..."
cd client
npm run build || { echo "❌ Frontend build failed"; exit 1; }

echo "🔨 Building backend..."
cd ../server
npm run build || { echo "❌ Backend build failed"; exit 1; }

echo "📦 Uploading FRONTEND..."
rsync -avz --delete ./dist/ $SERVER:/data01/virt141059/domeenid/www.pons.fi/htdocs/

echo "📦 Uploading BACKEND..."
rsync -avz --delete ./dist/ $SERVER:/data01/virt141059/node/pons-server/dist/

echo "♻️ Restarting backend service..."
ssh $SERVER "pm2 restart pons-api --update-env"

echo "✅ DEPLOY COMPLETE!"
```

---

## 7. Deployment Advantages

Current deployment approach provides:

- simple deployment workflow
- centralized deployment process
- faster updates compared to manual uploads
- reduced risk of deployment mistakes
- ability to deploy frontend and backend together

---

## 8. Operational Safety

Deployment safety considerations:

- production deployment performed intentionally
- environment separation between development and production
- PM2 used for backend process management
- deployment workflow tested incrementally
- production stability prioritized during refactoring

---

## 9. Current Limitations

Current deployment limitations:

- deployment triggered manually
- no automated CI/CD pipeline
- no automated rollback mechanism
- no automated deployment testing
- deployment depends on local development environment

---

## 10. Future Improvements

Possible future improvements:

- GitHub Actions based CI/CD
- automated testing before deployment
- Docker-based deployment
- deployment versioning
- rollback support
- staging environment
- automated monitoring

---

## 11. Relation to Professional Workflow

The deployment process demonstrates:

- production awareness
- operational thinking
- environment management
- backend process management
- deployment automation principles

The deployment workflow supports maintainable and repeatable software delivery.

---

## 12. Summary

Pons.fi uses a lightweight but practical deployment strategy suitable for a real-world full-stack application.

The deployment workflow balances simplicity, operational safety, and maintainability while supporting incremental development of a live production system.
