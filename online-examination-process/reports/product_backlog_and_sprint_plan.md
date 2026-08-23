# Agile Product Backlog & Sprint Execution Plan
## Online Examination Process System

**Agile Framework:** Scrum  
**Sprint Duration:** 3 Weeks per Sprint (4 Sprints total)  
**Estimation Scale:** Fibonacci Story Points (1, 2, 3, 5, 8, 13)  

---

## 1. Product Backlog (Prioritized via MoSCoW)

The backlog contains user stories prioritized by business value, risk, and technical dependencies.

| Story ID | Priority | User Story Summary | Story Points | Target Sprint | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **US-01** | Must Have | As a user, I want MFA login so that my account is secure against unauthorized access. | 5 | Sprint 1 | Completed |
| **US-02** | Must Have | As an Admin, I want RBAC role enforcement so that users only see valid options. | 5 | Sprint 1 | Completed |
| **US-03** | Must Have | As an Instructor, I want to create MCQ & True/False questions in a Question Bank. | 8 | Sprint 1 | Completed |
| **US-04** | Must Have | As an Instructor, I want to configure exam duration, passing score, and shuffle rules. | 5 | Sprint 1 | Completed |
| **US-05** | Must Have | As a Student, I want to see a synchronized countdown timer during the exam. | 3 | Sprint 2 | Completed |
| **US-06** | Must Have | As a Student, I want my answers auto-saved every 10 seconds so I don't lose progress. | 8 | Sprint 2 | Completed |
| **US-07** | Must Have | As a System, I want to auto-grade objective MCQ questions immediately upon submission. | 5 | Sprint 2 | Completed |
| **US-08** | Must Have | As a Proctor, I want window lockdown & tab-switch detection to prevent cheating. | 8 | Sprint 3 | Completed |
| **US-09** | Must Have | As a Proctor, I want webcam facial recognition to detect missing or multiple faces. | 13 | Sprint 3 | Completed |
| **US-10** | Should Have | As an Instructor, I want to grade short answer questions with rubrics. | 5 | Sprint 3 | Completed |
| **US-11** | Should Have | As a Student, I want network recovery to resume exams after temporary dropouts. | 8 | Sprint 3 | Completed |
| **US-12** | Should Have | As an Instructor, I want class performance analytics and percentile distributions. | 5 | Sprint 4 | Completed |
| **US-13** | Could Have | As an Admin, I want exportable audit logs in CSV/PDF format. | 3 | Sprint 4 | Completed |
| **US-14** | Could Have | As a Student, I want dark mode support during examination sessions. | 2 | Sprint 4 | Completed |

---

## 2. Sprint Execution Plan

### 🚀 Sprint 1: Foundation & Core Setup (Weeks 1 - 3)
- **Sprint Goal**: Establish system architecture, database schema, RBAC authentication, and initial Question Bank engine.
- **Planned Velocity**: 23 Story Points
- **Delivered Deliverables**:
  - Auth Service with JWT + TOTP MFA
  - Database schema migrations for Users, Roles, Question Bank, Exams
  - Basic Question Bank authoring UI

### 🚀 Sprint 2: Exam Engine & Real-time Auto-Save (Weeks 4 - 6)
- **Sprint Goal**: Deliver the candidate assessment UI, server-synchronized countdown timer, and background auto-save engine.
- **Planned Velocity**: 24 Story Points
- **Delivered Deliverables**:
  - Responsive Exam Delivery UI with accessibility support
  - 10-second heartbeat auto-save mechanism
  - Automated MCQ grading microservice

### 🚀 Sprint 3: Security, Integrity & Proctoring (Weeks 7 - 9)
- **Sprint Goal**: Integrate AI proctoring, lockdown controls, tab switch detection, and network reconnection handler.
- **Planned Velocity**: 34 Story Points
- **Delivered Deliverables**:
  - WebRTC periodic webcam frame processor
  - Browser focus change event monitor
  - Session state restoration API

### 🚀 Sprint 4: Analytics, QA & Final Release (Weeks 10 - 12)
- **Sprint Goal**: Performance optimization, full QA test matrix execution, reporting analytics, and final sign-off.
- **Planned Velocity**: 25 Story Points
- **Delivered Deliverables**:
  - Instructor Gradebook & Statistical Analytics Dashboard
  - Load testing validation up to 10,000 concurrent sessions
  - Production deployment pipeline
