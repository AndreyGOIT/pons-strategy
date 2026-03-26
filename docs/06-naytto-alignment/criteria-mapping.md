# Näyttö Criteria Mapping – Pons.fi

## 1. Purpose

This document maps project activities and artifacts to the evaluation criteria for:

- Ohjelmistokehittäjänä toimiminen (45 osp)
- Ohjelmiston toteuttaminen ohjelmistokomponenttikirjastolla (30 osp)

The goal is to demonstrate clear alignment between practical work and required competencies.

---

## 2. Evaluation Strategy

Each criterion is mapped to:

- Project evidence (what proves it)
- Location (where it can be found)
- Sprint (when it was addressed)
- Target level (Hyvä 4 / Kiitettävä 5)

---

## 3. Criteria Mapping Table

| Criteria Area | Evidence | Location | Sprint | Target Level |
| ------------- | -------- | -------- | ------ | ------------ |

### 3.1 Planning & Work Process (45 osp)

| Criteria         | Evidence                              | Location         | Sprint   | Level      |
| ---------------- | ------------------------------------- | ---------------- | -------- | ---------- |
| Work planning    | Project structure, backlog definition | docs/00-overview | Sprint 1 | Kiitettävä |
| Independent work | Self-managed development & decisions  | ADR, reflection  | All      | Kiitettävä |
| Time management  | Sprint structure and milestones       | sprint docs      | All      | Hyvä       |

---

### 3.2 Software Development (45 osp)

| Criteria                   | Evidence                                      | Location            | Sprint   | Level             |
| -------------------------- | --------------------------------------------- | ------------------- | -------- | ----------------- |
| Application implementation | Full-stack system (React + Node)              | pons-web repo       | All      | Kiitettävä        |
| Logic implementation       | Backend services and controllers              | backend docs        | All      | Kiitettävä        |
| Database integration       | SQL schema and queries                        | database-design.md  | All      | Kiitettävä        |
| Error handling             | Centralized error strategy (planned/improved) | implementation docs | Sprint 2 | Hyvä → Kiitettävä |

---

### 3.3 Version Control & DevOps (45 osp)

| Criteria           | Evidence                  | Location     | Sprint   | Level             |
| ------------------ | ------------------------- | ------------ | -------- | ----------------- |
| Git usage          | Commit history, branching | GitHub repos | All      | Kiitettävä        |
| Branching strategy | main/dev/feature workflow | devops docs  | Sprint 1 | Kiitettävä        |
| Deployment         | Docker / hosting setup    | devops docs  | Sprint 3 | Hyvä → Kiitettävä |
| CI/CD              | Basic pipeline            | devops docs  | Sprint 2 | Hyvä              |

---

### 3.4 Communication & Documentation (45 osp)

| Criteria                | Evidence               | Location           | Sprint | Level      |
| ----------------------- | ---------------------- | ------------------ | ------ | ---------- |
| Documentation           | Structured docs system | docs/              | All    | Kiitettävä |
| Technical communication | Architecture + ADRs    | architecture + ADR | All    | Kiitettävä |
| Reflection              | Sprint reflections     | reflection docs    | All    | Kiitettävä |

---

### 3.5 Component Library Usage (30 osp)

| Criteria                    | Evidence             | Location      | Sprint   | Level             |
| --------------------------- | -------------------- | ------------- | -------- | ----------------- |
| Component-based development | React components     | frontend code | All      | Kiitettävä        |
| Reusability                 | Shared UI components | frontend docs | Sprint 2 | Hyvä → Kiitettävä |
| State management            | React state / logic  | frontend docs | All      | Hyvä              |

---

### 3.6 Environment & Configuration (30 osp)

| Criteria                 | Evidence                  | Location     | Sprint | Level      |
| ------------------------ | ------------------------- | ------------ | ------ | ---------- |
| Environment setup        | Local + production config | devops docs  | All    | Kiitettävä |
| Configuration management | Env variables             | backend docs | All    | Hyvä       |
| Tooling                  | VSCode, Git, Docker       | devops docs  | All    | Kiitettävä |

---

## 4. Evidence Strategy

To support evaluation, each area includes:

- Direct links to code (pons-web repository)
- Documentation references (docs folder)
- Architectural decisions (ADR)
- Reflection notes (learning and improvements)

---

## 5. Target Level Justification

### Hyvä 4

- Functional system
- Basic documentation
- Working implementation

### Kiitettävä 5

- Structured architecture
- Documented decisions (ADR)
- Clear reasoning and trade-offs
- Professional workflow (Git, DevOps)
- Reflection and continuous improvement

---

## 6. Summary

This mapping ensures that all project activities are directly aligned with näyttö evaluation criteria.

The project is structured not only to function technically, but also to demonstrate professional competence at a high level.
