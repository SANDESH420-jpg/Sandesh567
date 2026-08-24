# System Architecture & UML Diagrams
## Online Examination Process System

This document provides four comprehensive UML diagrams representing the structural, behavioral, and lifecycle aspects of the system.

---

## 1. Use Case Diagram

The Use Case diagram below models the interactions between system actors (Student, Instructor, Proctor, Administrator) and the core capabilities within the Online Examination System boundary.

![Use Case Diagram](./use_case_diagram.png)

```mermaid
flowchart LR
    subgraph SystemBoundary ["Online Examination System"]
        UC1["Login & Authenticate MFA"]
        UC2["Browse Available Exams"]
        UC3["Take Exam & Submit Answers"]
        UC4["View Exam Results & Reports"]
        
        UC5["Create & Manage Question Banks"]
        UC6["Schedule & Configure Exam"]
        UC7["Grade Subjective Submissions"]
        
        UC8["Live Session Proctoring"]
        UC9["Review Integrity Flags"]
        
        UC10["Manage Users & Roles"]
        UC11["Audit System Logs"]
    end

    Student["Student / Candidate"] --> UC1
    Student --> UC2
    Student --> UC3
    Student --> UC4

    Instructor["Instructor / Examiner"] --> UC1
    Instructor --> UC5
    Instructor --> UC6
    Instructor --> UC7
    Instructor --> UC9

    Proctor["Proctor System / Staff"] --> UC8
    Proctor --> UC9

    Admin["System Administrator"] --> UC10
    Admin --> UC11
```

---

## 2. Class Diagram

The Class Diagram defines the object-oriented structure, domain models, entity relationships, attributes, and key methods.

![Class Diagram](./class_diagram.png)

```mermaid
classDiagram
    class User {
        +String userId
        +String name
        +String email
        +String passwordHash
        +UserRole role
        +login() Boolean
        +logout() Void
    }

    class Student {
        +String studentId
        +String enrollmentNo
        +registerForExam(examId) Boolean
    }

    class Instructor {
        +String instructorId
        +String department
        +createQuestionBank() QuestionBank
        +createExam() Exam
    }

    class Exam {
        +String examId
        +String title
        +Integer durationMinutes
        +DateTime startTime
        +DateTime endTime
        +Double totalMarks
        +Double passingMarks
        +Boolean isPublished
        +publishExam() Void
    }

    class Question {
        +String questionId
        +String stemText
        +QuestionType type
        +Double markValue
        +String category
        +validateAnswer(response) Boolean
    }

    class Option {
        +String optionId
        +String optionText
        +Boolean isCorrect
    }

    class ExamSubmission {
        +String submissionId
        +DateTime startTimestamp
        +DateTime submitTimestamp
        +SubmissionStatus status
        +Double totalScore
        +calculateObjectiveScore() Double
    }

    class AnswerRecord {
        +String recordId
        +String questionId
        +String selectedOptionId
        +String subjectiveText
        +Double scoreObtained
    }

    class ProctorLog {
        +String logId
        +DateTime timestamp
        +String eventType
        +String screenshotUrl
        +Double severityScore
    }

    User <|-- Student
    User <|-- Instructor
    Instructor "1" -- "*" Exam : creates
    Exam "1" *-- "*" Question : contains
    Question "1" *-- "*" Option : choices
    Student "1" -- "*" ExamSubmission : submits
    ExamSubmission "1" *-- "*" AnswerRecord : includes
    ExamSubmission "1" *-- "*" ProctorLog : tracks
```

---

## 3. Sequence Diagram

The Sequence Diagram details the real-time interaction flow between a Student, the Client Web App, the Examination Engine, Proctoring Service, and Database during an active assessment session.

![Sequence Diagram](./sequence_diagram_take_exam.png)

```mermaid
sequenceDiagram
    autonumber
    actor S as Student
    participant UI as Web Assessment UI
    participant Engine as Exam Engine API
    participant Proc as AI Proctoring Service
    participant DB as Database

    S->>UI: Select Exam & Click "Start Exam"
    UI->>Engine: POST /api/exams/{id}/start
    Engine->>DB: Verify Token & Check Exam Schedule
    DB-->>Engine: Schedule Validated
    Engine->>DB: Initialize ExamSubmission State
    Engine-->>UI: Return Question Sheet & Server Timer

    UI->>Proc: Start Camera & Browser Lockdown
    Proc-->>UI: Monitoring Active

    loop Every 10 Seconds / Navigation
        UI->>Engine: POST /api/exams/auto-save (Answers)
        Engine->>DB: Persist Answer Records (Async)
        Engine-->>UI: 200 OK (Saved)
    end

    opt Proctoring Violation Detected
        Proc->>Engine: POST /api/proctor/flag (Tab Change / Face Missing)
        Engine->>DB: Log Proctor Violation Event
        Engine-->>UI: Display Warning Overlay to Student
    end

    S->>UI: Click "Submit Exam"
    UI->>Engine: POST /api/exams/{id}/submit
    Engine->>DB: Update Submission Status = "SUBMITTED"
    Engine->>Engine: Evaluate Objective Questions
    Engine->>DB: Store Final Objective Score
    Engine-->>UI: Display Submission Confirmation
```

---

## 4. State / Activity Diagram

The State Diagram illustrates the complete lifecycle states of an Examination within the system, from creation to final grading and archiving.

![Activity Diagram](./activity_diagram_exam_workflow.png)

```mermaid
stateDiagram-v2
    [*] --> Draft : Instructor Creates Exam

    state Draft {
        [*] --> AddingQuestions
        AddingQuestions --> SettingRules : Add Questions from Bank
        SettingRules --> DraftReady : Set Time & Passing Criteria
    }

    DraftReady --> Published : Instructor Publishes Exam

    state Published {
        [*] --> Scheduled
        Scheduled --> OpenForRegistration : Registration Window Opens
    }

    OpenForRegistration --> Active : Exam Start Time Reached

    state Active {
        [*] --> CandidateInSession
        CandidateInSession --> AnswersAutoSaving : Real-time Assessment
        AnswersAutoSaving --> CandidateSubmitted : Click Submit / Time Expires
    }

    Active --> InEvaluation : Exam End Time Reached

    state InEvaluation {
        [*] --> AutoGradingObjective
        AutoGradingObjective --> InstructorGradingSubjective : Evaluate MCQs
        InstructorGradingSubjective --> ReviewingProctorLogs : Grade Short Answers
    }

    InEvaluation --> ResultsPublished : Grades Approved by Instructor

    state ResultsPublished {
        [*] --> ReportsGenerated
        ReportsGenerated --> Archived : Transcripts Released
    }

    Archived --> [*]
```
