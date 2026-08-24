# Online Examination Process (OEP) System

Welcome to the official repository for the **Online Examination Process System**. This repository documents the end-to-end software engineering lifecycle of a modern, secure, and scalable Online Examination System.

---

## 👥 Team Roles & Responsibilities Matrix

Below is the project organizational structure and role allocation for the development and management of the Online Examination System:

| Role | Team Member | Primary Responsibilities | Key Deliverables |
| :--- | :--- | :--- | :--- |
| **Project Manager / Scrum Master** | Sandesh Chaudhary | Sprint planning, team alignment, risk mitigation, resource allocation | Gantt Chart, Sprint Backlog, Final Project Report |
| **Lead System Architect** | Alex Rivera | System architecture, technology stack selection, UML modeling | Architecture Overview, UML Diagrams |
| **Requirements Analyst / BA** | Morgan Vance | Gathering stakeholder requirements, user stories, domain analysis | SRS Document, Traceability Matrix |
| **Full Stack Developer** | Jordan Lee | Frontend assessment UI, Backend REST APIs, Question engine | Core Module Implementation, API Specs |
| **Database & Security Engineer** | Taylor Swift | Database schema design, RBAC, anti-cheating proctoring | Database Migration, Audit Logging, Security Spec |
| **QA Lead / Test Engineer** | Casey Kim | Test plan creation, manual & automated test case execution | Test Cases & Matrix Excel, Bug Reports |

---

## 📁 Repository Directory Structure

```
online-examination-process/
├── README.md                          ← Team roles, structure, commit plan
├── requirements/
│   ├── README.md                      ← Overview of requirements artifacts
│   └── requirements_document.md       ← Complete SRS (Functional & Non-Functional)
├── design/
│   ├── README.md                      ← Architecture topology & rendering guide
│   └── uml_diagrams.md                ← 4 Mermaid diagrams (Use Case, Class, Sequence, State/Activity)
├── testing/
│   ├── README.md                      ← Test strategy & QA overview
│   └── test_cases_and_matrix.xlsx     ← Excel Test Cases & Traceability Matrix
└── reports/
    ├── README.md                      ← Project reports overview
    ├── gantt_chart.xlsx               ← WBS Schedule & Gantt Chart workbook
    ├── product_backlog_and_sprint_plan.md ← Product Backlog & 4-Sprint execution plan
    └── final_report.md                ← Project completion summary & retrospective
```

---

## 🌿 Git Branching Strategy & Commit Plan

To ensure clean, conflict-free collaboration, we adhere to the **GitFlow** branching model with standardized commit conventions.

### 1. Branching Strategy
- **`main`**: Production-ready code and finalized baseline documentation. Protected branch.
- **`develop`**: Integration branch for current sprint features.
- **`feature/<feature-name>`**: Dedicated branch for specific features or documentation modules (e.g., `feature/req-srs`, `feature/uml-design`, `feature/qa-testmatrix`).
- **`bugfix/<issue-id>`**: Hotfixes and targeted bug resolves.

### 2. Commit Message Conventions
Commits must strictly follow the **Conventional Commits** standard:

```bash
<type>(<scope>): <short description>
```

#### Commit Types:
- `docs`: Documentation changes (e.g., `docs(requirements): complete SRS section 3`)
- `feat`: A new feature implementation
- `fix`: A bug fix or correction
- `test`: Adding or updating test cases / matrix
- `chore`: Maintenance tasks (e.g., file reorganization, dependency updates)

### 3. Execution & Commit Milestone Plan

| Phase | Target Branch | Commit Message Example | Deliverable |
| :--- | :--- | :--- | :--- |
| **Phase 1** | `feature/docs-init` | `docs(readme): setup team roles, repo structure and commit plan` | `README.md` |
| **Phase 2** | `feature/requirements` | `docs(srs): add functional and non-functional requirements` | `requirements/requirements_document.md` |
| **Phase 3** | `feature/design-uml` | `docs(design): create 4 UML diagrams in mermaid format` | `design/uml_diagrams.md` |
| **Phase 4** | `feature/testing-matrix` | `test(qa): add test cases and traceability matrix workbook` | `testing/test_cases_and_matrix.xlsx` |
| **Phase 5** | `feature/sprint-reports` | `docs(reports): finalize gantt chart, sprint plan and project report` | `reports/*` |

---

## 🔗 Quick Links

- 📋 [Requirements Document](./requirements/requirements_document.md)
- 📐 [UML Diagrams](./design/uml_diagrams.md)
- 🧪 [Test Cases & Traceability Matrix](./testing/test_cases_and_matrix.xlsx)
- 📊 [Gantt Chart](./reports/gantt_chart.xlsx)
- 🚀 [Product Backlog & Sprint Plan](./reports/product_backlog_and_sprint_plan.md)
- 📝 [Final Report](./reports/final_report.md)
