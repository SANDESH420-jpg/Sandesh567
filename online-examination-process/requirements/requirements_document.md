# Software Requirements Specification (SRS)
## Online Examination Process System

**Document Version:** 1.0  
**Status:** Approved  
**Author:** Requirements Engineering Team  

---

## 1. Introduction

### 1.1 Purpose
The purpose of this document is to specify the complete functional and non-functional requirements for the **Online Examination Process System**. This system provides an end-to-end web platform for creating, scheduling, delivering, proctoring, and grading assessments electronically.

### 1.2 Scope
The Online Examination Process System enables educational institutions and certification bodies to automate traditional paper-based testing into a secure, web-enabled digital assessment flow.

---

## 2. User Classes and Roles

The system supports four distinct user roles:

1. **System Administrator (Admin)**
   - Manages user accounts, institutional settings, system logs, and security parameters.
2. **Examiner / Instructor**
   - Creates question banks, constructs assessments, schedules exams, reviews proctor flags, and approves final grades.
3. **Candidate / Student**
   - Registers for exams, verifies identity, completes assessments under timed conditions, and views score reports.
4. **Proctor (Human / AI)**
   - Monitors active examination sessions live, reviews automated webcam/browser alerts, and flags suspicious behavior.

---

## 3. Functional Requirements (FR)

### Module 1: User Authentication & RBAC
- **FR-01**: The system shall provide secure multi-factor authentication (MFA) via email/TOTP.
- **FR-02**: The system shall enforce Role-Based Access Control (RBAC) ensuring users only access authorized views and actions.
- **FR-03**: The system shall record full session logs and audit trails for all authentication events.

### Module 2: Question Bank & Exam Authoring
- **FR-04**: Instructors shall be able to create question banks supporting Multiple Choice Questions (MCQ), True/False, Short Answer, and Coding questions.
- **FR-05**: The system shall support tagging questions by category, difficulty level (Easy, Medium, Hard), and bloom taxonomy level.
- **FR-06**: Instructors shall be able to configure exam settings including duration, total marks, passing percentage, randomization of questions, and shuffling of choices.

### Module 3: Exam Delivery & Real-time Assessment Engine
- **FR-07**: The candidate assessment interface shall render a countdown timer synchronized with server time.
- **FR-08**: The system shall auto-save candidate answers every 10 seconds and immediately upon question navigation.
- **FR-09**: The engine shall handle unexpected network disconnections, allowing candidates to resume seamlessly within an admin-configurable window without losing elapsed time or answers.

### Module 4: Proctoring & Integrity Verification
- **FR-10**: The system shall enforce full-screen lock and detect window switching/tab changing during an examination.
- **FR-11**: The system shall capture periodic webcam snapshots and analyze for multiple faces, absence of candidate, or object detection (mobile phones).
- **FR-12**: The proctoring module shall log integrity violations with exact timestamps and video clips for instructor review.

### Module 5: Automated Evaluation & Result Reporting
- **FR-13**: Objective questions (MCQs, True/False) shall be automatically evaluated instantly upon submission.
- **FR-14**: Subjective and short-answer questions shall be routed to the instructor's grading queue with rubrics.
- **FR-15**: The system shall generate comprehensive candidate performance analytics including score distributions, percentile ranks, and item discrimination indices.

---

## 4. Non-Functional Requirements (NFR)

### 4.1 Performance & Scalability
- **NFR-01 (Concurrent Users)**: The system shall support up to 10,000 concurrent examination sessions without exceeding 500ms API response latency.
- **NFR-02 (Throughput)**: The assessment engine shall process up to 1,000 answer submissions per second during peak exam completion windows.

### 4.2 Security & Data Privacy
- **NFR-03 (Encryption)**: All data in transit shall be encrypted using TLS 1.3. All data at rest (including student grades and proctor logs) shall be encrypted using AES-256.
- **NFR-04 (GDPR / Privacy)**: Webcam proctoring feeds and biometric images shall be retained only for 30 days post-examination and purged automatically.

### 4.3 Reliability & Availability
- **NFR-05 (Uptime)**: The system shall maintain 99.9% uptime during scheduled examination windows.
- **NFR-06 (Disaster Recovery)**: System state and candidate answer databases shall be backed up continuously with a Recovery Point Objective (RPO) < 1 minute.

### 4.4 Usability & Accessibility
- **NFR-07 (Accessibility)**: The assessment interface shall comply with WCAG 2.1 AA accessibility standards, supporting screen readers and full keyboard navigation.

---

## 5. System Constraints & Assumptions

1. **Browser Compatibility**: Supported on modern evergreen browsers (Chrome 100+, Firefox 100+, Edge 100+, Safari 15+).
2. **Hardware Constraint**: Candidates must possess a working webcam and microphone for proctored exams.
3. **Network Assumption**: Candidates require a minimum network bandwidth of 1 Mbps.
