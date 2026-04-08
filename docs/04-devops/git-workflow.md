# Git Workflow – Pons.fi

## 1. Purpose

This document describes the Git workflow used in the Pons.fi project.

The goal is to demonstrate:

- Professional version control practices
- Structured development process
- Ability to manage changes and resolve conflicts

---

## 2. Repository Structure

The project is split into two repositories:

### 1. Implementation Repository

https://github.com/AndreyGOIT/pons-web

Contains:

- Frontend (React + TypeScript)
- Backend (Node.js + Express)
- Database integration

### 2. Strategy Repository

https://github.com/AndreyGOIT/pons-strategy

Contains:

- Documentation
- Architectural decisions (ADR)
- Näyttö alignment
- Sprint reports

---

## 3. Branching Strategy

The following branching model is used:

- `main` → stable version
- `dev` → integration branch (planned)
- `feature/*` → individual changes

Current state:

- Work primarily on `main` (small team / solo project)
- Structured commits used to simulate professional workflow

---

## 4. Commit Strategy

Commits follow a structured format (inspired by Conventional Commits):

- `docs:` documentation changes
- `feat:` new features
- `fix:` bug fixes
- `chore:` maintenance tasks

### Examples

- `docs: add architecture overview`
- `docs: sprint 1 architecture and strategy foundation`
- `chore: ignore .DS_Store files`

---

## 5. Workflow Process

Typical workflow:

1. Make changes locally
2. Stage changes:
   ```
   git add .
   ```
3. Create commit:
   ```
   git commit -m "type: description"
   ```
4. Sync with remote:
   ```
   git pull --rebase
   ```
5. Push changes:
   ```
   git push
   ```

---

## 6. Conflict Resolution (Real Case)

During development, a merge conflict occurred when:

- README was modified both locally and on GitHub

### Resolution approach:

1. Pull with rebase:
   ```
   git pull --rebase
   ```
2. Resolve conflict manually in file
3. Stage resolved file:
   ```
   git add README.md
   ```
4. Continue rebase:
   ```
   git rebase --continue
   ```
5. Push changes:
   ```
   git push
   ```

### Outcome

- Clean commit history preserved
- No forced push required
- Conflict resolved safely

Example commit:
be82b56 docs: add README

---

## 7. Best Practices Applied

- Use of `git pull --rebase` instead of merge
- Clear and meaningful commit messages
- Separation of repositories (code vs strategy)
- Avoid committing system files (`.DS_Store`)
- Incremental commits reflecting real progress

---

## 8. Lessons Learned

- Git conflicts are a normal part of development
- Rebase helps maintain a clean history
- Clear structure reduces confusion
- Version control is part of professional competence, not just a tool

---

## 9. Future Improvements

- Introduce `dev` branch workflow
- Simulate pull request process
- Add CI/CD integration
- Introduce release tagging

---

## 10. Summary

The Git workflow in this project demonstrates structured version control practices and real-world problem solving.

It reflects a professional approach to managing changes, collaboration (even in a solo project), and maintaining code quality.
