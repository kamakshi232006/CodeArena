# CodeArena

<p align="center">
  <strong>A Complete Online Coding Practice, Skill Assessment, Contest, Learning & Certification Platform</strong>
</p>

<p align="center">
  Build skills. Practice consistently. Assess knowledge. Compete fairly. Earn verifiable achievements.
</p>

<p align="center">
  <a href="https://github.com/kanchi2006/CodeArena">GitHub Repository</a>
</p>

---

## Table of Contents

- [Overview](#overview)
- [Project Vision](#project-vision)
- [Core Objectives](#core-objectives)
- [Platform Capabilities](#platform-capabilities)
  - [Coding Practice](#1-coding-practice)
  - [Online IDE and Code Execution](#2-online-ide-and-code-execution)
  - [User Dashboard](#3-user-dashboard)
  - [Assessments](#4-assessments)
  - [Assessment Security and Proctoring](#5-assessment-security-and-proctoring)
  - [Contests](#6-contests)
  - [Courses and Learning](#7-courses-and-learning)
  - [Certificates and Achievements](#8-certificates-and-achievements)
  - [Organization Portal](#9-organization-portal)
  - [Authentication and Account Security](#10-authentication-and-account-security)
  - [Email, OTP and Notifications](#11-email-otp-and-notifications)
  - [Search, Bookmarks and Support](#12-search-bookmarks-and-support)
  - [Localization](#13-localization)
  - [AI-Assisted Features](#14-ai-assisted-features)
- [User Roles](#user-roles)
- [Application Workflow](#application-workflow)
- [Architecture](#architecture)
- [Technology Stack](#technology-stack)
- [Repository Structure](#repository-structure)
- [Database and Data Management](#database-and-data-management)
- [Code Execution Architecture](#code-execution-architecture)
- [Security Architecture](#security-architecture)
- [Environment Configuration](#environment-configuration)
- [Local Development Setup](#local-development-setup)
- [Docker](#docker)
- [Production Deployment](#production-deployment)
- [Render Deployment](#render-deployment)
- [Continuous Deployment](#continuous-deployment)
- [Testing and Verification](#testing-and-verification)
- [Troubleshooting](#troubleshooting)
- [Git Workflow](#git-workflow)
- [Project Status](#project-status)
- [Future Enhancements](#future-enhancements)
- [Security and Responsible Use](#security-and-responsible-use)
- [Contributing](#contributing)
- [License](#license)

---

# Overview

**CodeArena** is a full-stack online coding practice and skill assessment management platform designed to support the complete learning and evaluation journey in one application.

The platform combines programming practice, an online code editor, automated code execution, submissions, assessments, contests, courses, progress analytics, certificates, organization verification, notifications, localization, and AI-assisted functionality.

CodeArena is designed for three primary categories of users:

| Role | Primary Responsibilities |
|---|---|
| **User** | Practice coding problems, run and submit code, take assessments, participate in contests, complete courses, track progress, and earn certificates. |
| **Administrator** | Manage platform content, users, organizations, assessments, contests, courses, certificates, support, and operational workflows. |
| **Organization** | Register, verify organizational identity, create assessments and contests, manage participants, and review evaluation results. |

The project is implemented as a modern web application with a React/Vite frontend, Node.js/Express backend, MySQL database, dedicated execution services, email infrastructure, and Docker support.

---

# Project Vision

CodeArena aims to provide a unified environment where a learner can move through a continuous development cycle:

```text
                    CODEARENA
                        │
          ┌─────────────┴─────────────┐
          │                           │
        LEARN                      PRACTICE
          │                           │
       Courses                   Problems
          │                           │
          └─────────────┬─────────────┘
                        │
                      ASSESS
                        │
                   Assessments
                        │
                     COMPETE
                        │
                    Contests
                        │
                TRACK PROGRESS
                        │
                 Analytics /
                 Achievements
                        │
                 EARN CERTIFICATES
                        │
                  Career-ready
                    Portfolio
```

The objective is not only to provide a coding editor, but to build an end-to-end platform for learning, evaluation, competition, verification, and measurable skill development.

---

# Core Objectives

CodeArena is built around the following engineering and product objectives:

1. Provide an accessible coding-practice experience with structured problems, topics, constraints, examples, hints, and submissions.
2. Provide an integrated online IDE and automated execution workflow.
3. Enable structured assessments with configurable attempts, timers, scoring, results, and security controls.
4. Provide contest registration, problem solving, submissions, scoring, ranking, and result workflows.
5. Support course-based learning and completion certificates.
6. Track long-term user progress and achievements.
7. Allow verified organizations to conduct assessments and contests.
8. Provide auditable security-event tracking for monitored assessments and contests.
9. Centralize notifications, transactional email, verification, and account workflows.
10. Maintain a scalable deployment model using environment configuration and Dockerized services.

---

# Platform Capabilities

## 1. Coding Practice

The coding-practice system provides the core learning environment for programming problems.

### Problem Management

Problems can include:

- Problem title
- Description
- Examples
- Input/output expectations
- Constraints
- Difficulty
- Topic/category
- Editorial or explanation content
- Hints
- Test cases
- Starter code/templates
- Supported languages

### User Experience

Users can:

- Browse available problems
- Filter by topic/category
- Filter by difficulty
- Search for problems
- Open a detailed problem page
- Read examples and constraints
- Review hints/editorial content
- Select a programming language
- Write code in the integrated editor
- Run code
- Submit a solution
- Review results and submission history
- Track accepted-problem progress
- Bookmark problems

The problem system is intended to support structured preparation for technical interviews, academic assessments, coding competitions, and general programming practice.

---

## 2. Online IDE and Code Execution

The Online IDE is one of the central components of CodeArena.

The backend contains a dedicated execution service:

```text
backend/services/executionService.js
```

The execution service is integrated with the application so that user code can be:

```text
Written in editor
      ↓
Validated by backend
      ↓
Sent to execution service
      ↓
Compiled / interpreted
      ↓
Executed against input / test cases
      ↓
Execution result generated
      ↓
Returned to frontend
      ↓
Displayed to user
```

### Execution Responsibilities

The execution layer is responsible for handling the configured programming languages and their runtime requirements.

Typical environment dependencies may include language compilers/interpreters such as:

- C compiler
- C++ compiler
- Java runtime/compiler
- Python runtime
- JavaScript runtime
- Other languages enabled by the current application configuration

The exact supported language matrix is determined by the implementation of the current execution service and should be treated as the source of truth.

### Execution Safety

Submitted source code is untrusted input. A production deployment should apply controls around:

- Execution time
- Memory consumption
- Process lifetime
- Temporary files
- File-system access
- Process cleanup
- User permissions
- Network access
- Compiler/runtime availability

The application should never expose a general-purpose shell to end users.

---

## 3. User Dashboard

The dashboard consolidates a user's activity across the platform.

It can include:

- Accepted problem count
- Coding progress
- Assessment history
- Contest activity
- Course progress
- Certificates
- Achievements
- Notifications
- Profile information
- Learning activity

The dashboard serves as the user's central progress and achievement workspace.

---

## 4. Assessments

The Assessment System allows administrators and verified organizations to conduct structured skill evaluations.

### Assessment Capabilities

- Assessment creation
- Assessment configuration
- Question management
- Coding questions
- Objective questions where configured
- Difficulty configuration
- Time limits
- Attempt limits
- Candidate enrollment
- Assessment instructions
- Scoring
- Result calculation
- Assessment history
- Candidate/result views
- Retake handling
- Security configuration
- Violation monitoring
- Certificate workflows where configured

### Assessment Lifecycle

```text
Create Assessment
        ↓
Configure Questions & Rules
        ↓
Publish / Schedule
        ↓
Candidate Enrollment
        ↓
Security Verification
        ↓
Start Attempt
        ↓
Answer / Code / Submit
        ↓
Timer + Security Monitoring
        ↓
Finalize Attempt
        ↓
Calculate Results
        ↓
Display Result
```

---

## 5. Assessment Security and Proctoring

CodeArena contains browser-level monitoring for assessment sessions.

The current implementation includes the following areas:

- Security & System Verification screen
- Camera permission/check
- Microphone permission/check
- Screen-sharing verification
- Fullscreen mode
- Fullscreen-exit detection
- Browser visibility/tab-switch detection
- Window blur/focus detection
- Copy attempt detection/prevention
- Paste attempt detection/prevention
- Cut attempt detection/prevention
- Right-click/context-menu restriction
- Warning counter
- Configurable warning threshold
- Automatic escalation when the threshold is reached
- Security-event persistence
- Assessment violation history
- Security state associated with an assessment attempt
- Cleanup of media streams and listeners at the end of an attempt
- Server-side validation of security events

### Security Verification Flow

```text
Assessment Details
        ↓
Security & System Verification
        ↓
Camera / Microphone / Screen / Fullscreen Checks
        ↓
Candidate Confirmation
        ↓
Assessment Attempt Starts
        ↓
Security Monitoring Remains Active
```

### Security Status

During an assessment, the workspace can expose live security state such as:

```text
Camera: Active / Inactive
Screen: Active / Inactive
Fullscreen: Active / Off
Warnings: X / Y
```

A proctor-camera preview can also be shown where the configured assessment security mode enables it.

### Warning Policy

Security warnings can be generated for events such as:

- Page hidden / tab switch
- Window blur
- Fullscreen exit
- Copy attempt
- Cut attempt
- Paste attempt
- Right-click attempt
- Screen-sharing stopped

The exact warning threshold and escalation action are configuration-driven by the assessment rules.

### Persistence

Security-event information is associated with the assessment attempt and stored server-side so that administrative views can inspect relevant violations.

---

## 6. Contests

The Contest System provides a coding-competition workflow for platform administrators and verified organizations.

### Contest Features

- Contest discovery
- Contest details
- Contest registration
- Registration confirmation
- Schedule information
- Contest duration
- Problem sets
- Problem ordering
- Supported languages
- Run code
- Submit code
- Submission persistence
- Score calculation
- Solved count
- Penalty calculation
- Leaderboard
- Result page
- Contest completion
- Organization-hosted contests
- Contest security monitoring

### Contest Lifecycle

```text
Create Contest
      ↓
Add Problems
      ↓
Configure Rules
      ↓
Schedule
      ↓
Publish
      ↓
Registration
      ↓
Enter Contest
      ↓
Security Verification
      ↓
Start Attempt
      ↓
Solve Problems
      ↓
Run / Submit
      ↓
Timer + Security Monitoring
      ↓
End Contest
      ↓
Results + Leaderboard
```

### Submission Flow

```text
Submit
   ↓
Authenticate User
   ↓
Validate Contest Attempt
   ↓
Validate Problem
   ↓
Validate Language
   ↓
Execute Code
   ↓
Evaluate Test Cases
   ↓
Save Submission
   ↓
Update Score / Solved Count / Penalty
   ↓
Update Result / Leaderboard
```

The same underlying execution infrastructure is intended to be reused between general coding practice, assessments, and contests rather than maintaining unrelated compiler implementations.

---

## 7. Courses and Learning

The Course System provides structured learning content inside CodeArena.

### Course Capabilities

- Admin course management
- Course publishing
- User course library
- Slide/content-based learning workspace
- Course progress tracking
- Completion state
- Course completion certificates

### Learning Flow

```text
Browse Course
     ↓
Open Course
     ↓
Study Content
     ↓
Move Through Lessons / Slides
     ↓
Track Progress
     ↓
Complete Course
     ↓
Generate Certificate
```

Course-related UI components are organized under:

```text
frontend/src/components/courses/
```

---

## 8. Certificates and Achievements

CodeArena supports multiple achievement pathways.

### Milestone Certificates

The milestone system is designed around accepted-problem achievements.

Current planned milestone thresholds are:

| Milestone | Accepted Problems |
|---|---:|
| Milestone 1 | 30 |
| Milestone 2 | 50 |
| Milestone 3 | 100 |
| Milestone 4 | 120 |
| Milestone 5 | 150 |
| Milestone 6 | 200 |

### Course Completion Certificates

Users can receive certificates when configured course-completion conditions are satisfied.

Certificate details can include:

- Recipient name
- Course or achievement name
- Award information
- CodeArena branding
- QR verification information
- Certificate viewer
- Public verification page

Certificates are intended to provide a verifiable representation of platform achievements rather than simply a visual badge inside the dashboard.

---

## 9. Organization Portal

CodeArena provides an organization workflow for institutions and companies that need to conduct assessments and contests.

### Organization Registration

Organizations can register through the platform and complete account/email verification.

### Verification Workflow

```text
Organization Registration
        ↓
Email Verification
        ↓
Organization Profile
        ↓
Document Submission
        ↓
Administrative Review
        ↓
Verification Decision
        ↓
Verified Organization Workspace
```

### Organization Verification States

The application supports status concepts including:

```text
PENDING_VERIFICATION
UNDER_REVIEW
VERIFIED
REJECTED
RESUBMISSION_REQUIRED
SUSPENDED
```

### Organization Features

After the required verification state is reached, organization workflows can include:

- Organization profile management
- Verification document management
- Assessments
- Contests
- Participant management
- Candidate results
- Analytics
- Certificates
- Notifications
- Settings

---

## 10. Authentication and Account Security

CodeArena contains role-aware authentication and access control for platform users.

### Authentication Capabilities

- User registration
- User login
- Organization registration/login
- Email verification
- OTP verification
- Password reset
- Authenticated API requests
- Role-aware authorization
- Session/token management

Authentication data and secrets must always be provided through environment variables in deployed environments.

---

## 11. Email, OTP and Notifications

The backend includes a centralized email service:

```text
backend/services/emailService.js
```

The email system supports transactional communication for workflows such as:

- Welcome messages
- Email verification
- OTP delivery
- Password reset
- Course completion
- Assessment enrollment/result communication
- Contest registration and related communication
- Milestone achievement notifications
- Organization verification events

### Email Architecture

```text
CodeArena Event
      ↓
Email Service
      ↓
SMTP Provider
      ↓
Recipient Inbox
      ↓
Email Log / Delivery Record
```

The application is designed to work with SMTP providers such as Brevo. Production credentials must be configured through deployment environment variables.

---

## 12. Search, Bookmarks and Support

CodeArena includes platform usability features such as:

- Problem search
- Problem bookmarks
- Topic-based filtering
- Support Center
- Rules and guidelines
- FAQ/help content
- Administrative support management

These features are designed to reduce friction when navigating a large coding and assessment platform.

---

## 13. Localization

The frontend includes an internationalization layer under:

```text
frontend/src/i18n/
```

The localization system contains language configuration and translation resources that can be extended as additional languages are introduced.

---

## 14. AI-Assisted Features

The backend contains AI-related services, including:

```text
backend/services/geminiService.js
backend/services/adminGeminiService.js
backend/services/translatorService.js
```

These services support AI/chatbot and translation-oriented workflows that are part of the CodeArena platform architecture.

AI provider credentials are treated as secrets and must never be committed to source control.

---

# User Roles

## User

A standard learner/candidate can:

- Register and verify an account
- Practice coding problems
- Run and submit code
- Track accepted solutions
- Take assessments
- Participate in contests
- Complete courses
- View certificates
- Monitor achievements
- Update profile details
- Receive notifications
- Use support/search features

## Administrator

An administrator can perform platform-level management tasks including:

- User administration
- Problem management
- Assessment management
- Contest management
- Course management
- Certificate management
- Organization verification/review
- Results and violation review
- Support management
- Notifications
- Platform configuration

## Organization

An organization can, subject to verification and authorization rules:

- Maintain organization identity information
- Submit verification documents
- Monitor verification status
- Create assessments
- Create contests
- Manage participants
- Review results
- Use organization-level analytics and certificates

---

# Application Workflow

## General User Journey

```text
Landing Page
     ↓
Sign Up / Sign In
     ↓
Email / OTP Verification
     ↓
User Dashboard
     ↓
Choose:
 ├── Problems
 ├── Assessments
 ├── Contests
 ├── Courses
 ├── Certificates
 ├── Profile
 ├── Notifications
 └── Support
```

## Assessment Journey

```text
Assessment List
      ↓
Assessment Details
      ↓
Enrollment
      ↓
Security Verification
      ↓
Attempt Workspace
      ↓
Questions + Code Editor
      ↓
Submit / Auto Submit / Termination
      ↓
Scoring
      ↓
Result
```

## Contest Journey

```text
Contest Hub
      ↓
Contest Details
      ↓
Register
      ↓
Registration Confirmation
      ↓
Enter Contest
      ↓
Security Verification
      ↓
Contest Workspace
      ↓
Problems + Editor + Timer
      ↓
Run / Submit
      ↓
Finalization
      ↓
Result + Leaderboard
```

## Organization Journey

```text
Organization Sign Up
      ↓
Email Verification
      ↓
Organization Profile
      ↓
Verification Documents
      ↓
Admin Review
      ↓
Verification Status
      ↓
Verified Organization Workspace
      ↓
Assessments / Contests / Participants / Analytics
```

---

# Architecture

## High-Level Architecture

```text
                         ┌──────────────────────┐
                         │       Browser        │
                         │  React + Vite UI     │
                         └──────────┬───────────┘
                                    │ HTTPS / REST
                                    ▼
                         ┌──────────────────────┐
                         │    Node + Express    │
                         │      Backend API     │
                         └──────┬──────┬────────┘
                                │      │
                    ┌───────────┘      └──────────────┐
                    ▼                                  ▼
          ┌──────────────────┐              ┌──────────────────┐
          │      MySQL       │              │ Service Layer    │
          │ Persistent Data  │              │ Email / AI /     │
          │ Users / Problems │              │ Execution /      │
          │ Assessments etc. │              │ Scoring etc.     │
          └──────────────────┘              └────────┬─────────┘
                                                     │
                                                     ▼
                                            ┌──────────────────┐
                                            │ Code Execution   │
                                            │ Compiler /        │
                                            │ Runtime Sandbox   │
                                            └──────────────────┘
```

## Application Layers

### Presentation Layer

Located primarily under:

```text
frontend/src/
```

Responsible for:

- User interface
- Routing/navigation
- Forms
- Dashboards
- Workspace screens
- State handling
- Localization

### API Layer

Located primarily in:

```text
backend/server.js
```

Responsible for:

- HTTP endpoints
- Authentication
- Authorization
- Request validation
- Business workflows
- Database operations
- Execution orchestration

### Service Layer

Located under:

```text
backend/services/
```

Contains dedicated service modules for:

- Code execution
- Email
- Assessment scoring
- Assessment timing
- AI
- Translation

### Data Layer

Includes:

```text
backend/db.js
backend/schema.sql
```

and the associated MySQL tables used throughout the platform.

---

# Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React + Vite |
| UI | CSS / application design system |
| Backend | Node.js + Express |
| Database | MySQL |
| Database Driver | MySQL-compatible Node database access |
| Code Execution | Dedicated execution service |
| Email | SMTP / transactional email provider |
| AI | Gemini-related backend services |
| Translation | Translation service integration |
| Containerization | Docker |
| Source Control | Git + GitHub |
| Deployment Architecture | Containerized frontend/backend + persistent database/storage |

---

# Repository Structure

```text
CodeArena/
│
├── backend/
│   ├── server.js
│   ├── db.js
│   ├── schema.sql
│   ├── package.json
│   ├── package-lock.json
│   ├── Dockerfile
│   ├── problems_seed.json
│   ├── seed_10_problems.sql
│   ├── create_contests.js
│   ├── list_tables.js
│   ├── seed_test_org.js
│   └── services/
│       ├── executionService.js
│       ├── emailService.js
│       ├── geminiService.js
│       ├── adminGeminiService.js
│       ├── translatorService.js
│       ├── assessmentScoringService.js
│       └── assessmentTimerService.js
│
├── frontend/
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   ├── Dockerfile
│   ├── vite.config.js
│   ├── public/
│   └── src/
│       ├── App.jsx
│       ├── components/
│       │   ├── assessments/
│       │   ├── contests/
│       │   ├── courses/
│       │   └── support/
│       ├── i18n/
│       └── ...
│
├── .gitattributes
├── .gitignore
├── README.md
└── ...
```

---

# Database and Data Management

CodeArena uses MySQL as its primary relational data store.

The repository includes schema and seed resources such as:

```text
backend/schema.sql
backend/seed_10_problems.sql
backend/problems_seed.json
```

The database stores the platform's operational data for areas such as:

- Users
- Authentication/verification
- Problems
- Submissions
- Assessments
- Assessment attempts
- Assessment violations
- Contests
- Contest problems
- Contest registrations
- Contest attempts
- Contest submissions
- Contest security events
- Contest results
- Certificates
- Courses
- Organizations
- Organization verification information
- Notifications
- Email logs

### Example Security Tables

Assessment security includes tables such as:

```text
assessment_violations
assessment_attempts
```

Contest security includes:

```text
contest_security_events
contest_attempts
```

The exact schema should always be taken from the current `backend/schema.sql` rather than assumed from this document.

---

# Code Execution Architecture

Because CodeArena executes source code submitted by users, deployment requirements are different from a typical web application.

## Execution Flow

```text
Browser
  │
  │ language + source + input/problem context
  ▼
Backend API
  │
  │ validate request
  ▼
Execution Service
  │
  ├── create temporary workspace
  ├── write source file
  ├── compile if required
  ├── execute with limits
  ├── capture stdout/stderr
  ├── capture exit status
  ├── clean temporary files
  ▼
Execution Result
  │
  ├── success / failure
  ├── output
  ├── error
  ├── execution time
  └── verdict information
  ▼
Frontend Output Panel
```

## Docker Requirement

A standard Node.js runtime alone may not be enough for CodeArena's Online IDE. The Docker environment needs the operating-system dependencies required by the configured languages.

The current project already contains:

```text
backend/Dockerfile
frontend/Dockerfile
```

The backend image should be treated as the controlled execution environment for the services that require compiler/runtime support.

### Recommended Production Isolation

For higher security, the long-term architecture should separate the API from the untrusted execution worker:

```text
                Public API
                    │
                    ▼
             Execution Queue
                    │
                    ▼
            Isolated Runner
                    │
         ┌──────────┴──────────┐
         ▼                     ▼
      Compiler              Runtime
         │                     │
         └──────────┬──────────┘
                    ▼
             Result / Verdict
```

The execution worker should not have access to application secrets or unrestricted internal services.

---

# Security Architecture

CodeArena implements security at multiple levels.

## Authentication

- Authenticated access to protected workflows
- Role-based access
- Verification workflows
- Password/OTP controls

## Backend Authorization

Sensitive operations should validate:

- authenticated identity
- role
- resource ownership
- attempt ownership
- organization authorization
- assessment/contest state
- submission validity

Frontend checks alone are not considered sufficient authorization.

## Assessment and Contest Monitoring

Browser-based security monitoring can include:

- Camera
- Microphone
- Screen sharing
- Fullscreen
- Tab visibility
- Window focus
- Copy/paste/cut
- Right-click
- Configurable warning thresholds
- Server-side event logging

## Secret Management

Never store production secrets in Git.

Never place secrets inside:

```text
frontend/src/
frontend/public/
README.md
```

Browser-delivered JavaScript must not contain server-only credentials.

---

# Environment Configuration

The repository contains environment templates:

```text
backend/.env.example
frontend/.env.example
```

Use these as the authoritative source for the variable names expected by the current codebase.

## Typical Backend Configuration

```env
PORT=5000

DB_HOST=localhost
DB_PORT=3306
DB_USER=your_database_user
DB_PASSWORD=your_database_password
DB_NAME=codearena

JWT_SECRET=your_production_jwt_secret

FRONTEND_URL=http://localhost:5173

SMTP_HOST=smtp-relay.brevo.com
SMTP_PORT=587
SMTP_USER=your_smtp_username
SMTP_PASSWORD=your_smtp_password
EMAIL_FROM=CodeArena <your_verified_sender@example.com>

# AI / translation provider variables as required by .env.example
```

Do not copy this example blindly. The repository `.env.example` file is the authoritative configuration reference.

---

# Local Development Setup

## Prerequisites

Install the following on the development machine:

- Node.js
- npm
- MySQL
- Git
- Docker Desktop (recommended for deployment parity and execution testing)

---

## Step 1 — Clone the Repository

```bash
git clone https://github.com/kanchi2006/CodeArena.git
cd CodeArena
```

---

## Step 2 — Install Backend Dependencies

```bash
cd backend
npm install
```

Create:

```text
backend/.env
```

Use:

```text
backend/.env.example
```

as the starting template.

---

## Step 3 — Set Up MySQL

Create a MySQL database for CodeArena.

For example:

```sql
CREATE DATABASE codearena;
```

Then apply the schema:


```bash
mysql -u your_database_user -p codearena < schema.sql
```

Apply any seed scripts required by your development environment.

Example:

```bash
mysql -u your_database_user -p codearena < seed_10_problems.sql
```

Additional JavaScript seed/utility scripts may be run from the backend directory where applicable.

---

## Step 4 — Start Backend

From `backend/`:

```bash
node server.js
```

or use the configured npm script:

```bash
npm start
```

Expected development address:

```text
http://localhost:5000
```

---

## Step 5 — Start Frontend

Open another terminal:

```bash
cd frontend
npm install
npm run dev
```

Expected development address:

```text
http://localhost:5173
```

Configure the frontend API base URL according to the current frontend environment configuration.

---

# Docker

Docker is a core deployment option for CodeArena because the application combines a web stack with programming-language execution requirements.

## Existing Dockerfiles

```text
backend/Dockerfile
frontend/Dockerfile
```

## Recommended Responsibilities

### Backend Container

The backend container should contain:

- Node.js runtime
- npm dependencies
- CodeArena backend
- Required compiler/runtime packages
- Execution-service dependencies

### Frontend Container

The frontend container should:

- Install frontend dependencies
- Build the Vite application
- Serve the generated production assets

## Local Docker Validation

Build the backend image:

```bash
docker build -t codearena-backend ./backend
```

Build the frontend image:

```bash
docker build -t codearena-frontend ./frontend
```

Run the containers according to the environment variables and networking required by your deployment setup.

Before deployment, confirm that the backend container can:

1. Start successfully.
2. Connect to MySQL.
3. Load required services.
4. Execute the supported programming languages.
5. Handle timeouts and cleanup correctly.
6. Return execution results to the API.

---

# Production Deployment

CodeArena is best deployed as multiple cooperating services rather than treating the frontend, backend, database, and execution environment as one undifferentiated process.

## Recommended Production Architecture

```text
GitHub
  │
  ├──────────────► Frontend Service
  │                  │
  │                  └── React / Vite
  │
  ├──────────────► Backend Service
  │                  │
  │                  ├── Node / Express
  │                  ├── Auth
  │                  ├── Email
  │                  ├── Assessment
  │                  ├── Contest
  │                  └── Execution orchestration
  │
  └──────────────► Database Service
                     │
                     └── MySQL

External / Supporting Services
  ├── SMTP provider
  ├── Durable file storage
  └── AI / translation providers
```

---

# Render Deployment

The repository is prepared for containerized deployment and can be organized on Render using separate services for the frontend and backend, with a persistent database and durable file storage.

## Frontend Service

Create a frontend deployment using the `frontend/` directory.

Typical build configuration:

```text
Root Directory: frontend
Build Command: npm install && npm run build
Publish Directory: dist
```

If deploying the frontend with its Dockerfile instead, use:

```text
frontend/Dockerfile
```

The production frontend must point to the deployed backend URL.

---

## Backend Service

Create a backend service using:

```text
backend/
```

The Docker deployment should use:

```text
backend/Dockerfile
```

The server should respect the hosting platform's assigned `PORT` value.

Recommended Node pattern:

```js
const PORT = process.env.PORT || 5000;

app.listen(PORT, '0.0.0.0', () => {
  console.log(`Server running on port ${PORT}`);
});
```

The exact server startup command remains defined by the project's Dockerfile/application scripts.

---

## Database Service

Provision a persistent MySQL database for production.

Configure the backend environment with:

```text
DB_HOST
DB_PORT
DB_USER
DB_PASSWORD
DB_NAME
```

Then:

1. Create the database.
2. Apply `backend/schema.sql`.
3. Run required migrations/initialization.
4. Apply required seed data.
5. Verify database connectivity.
6. Verify all expected application tables.

Do not use an ephemeral database for production data.

---

## Uploaded Document Storage

The organization verification workflow uses uploaded documents.

Do not assume normal container filesystem storage is durable across all production lifecycle events.

Use durable storage such as:

- Persistent disk, where appropriate
- Object storage
- Managed file storage

For organization documents, apply strict authorization and avoid accidental public exposure.

---

## Email Configuration

Configure the SMTP credentials on the backend service.

For example:

```env
SMTP_HOST=smtp-relay.brevo.com
SMTP_PORT=587
SMTP_USER=your_smtp_username
SMTP_PASSWORD=your_smtp_password
EMAIL_FROM=CodeArena <your_verified_sender@example.com>
```

Then verify:

- Signup email
- OTP
- Verification
- Password reset
- Assessment messages
- Contest messages
- Course completion
- Organization verification messages

---

# Continuous Deployment

The personal GitHub repository is:

```text
https://github.com/kanchi2006/CodeArena.git
```

A typical deployment pipeline is:

```text
Local changes
     ↓
git add .
     ↓
git commit
     ↓
git push personal kamakshi:main
     ↓
GitHub main
     ↓
Connected deployment service
     ↓
Build
     ↓
Deploy
     ↓
Production verification
```

Configure the hosting platform to watch the production branch used by the corresponding service.

For the personal repository, the intended production branch is:

```text
main
```

The local development branch can remain:

```text
kamakshi
```

---

# Testing and Verification

Before sharing a public deployment, validate the system end-to-end.

## Frontend Build

```bash
cd frontend
npm install
npm run build
```

## Backend Syntax Check

```bash
cd backend
node --check server.js
```

## Backend Startup

```bash
node server.js
```

## Functional Test Matrix

### Authentication

- [ ] Registration works
- [ ] Login works
- [ ] Email verification works
- [ ] OTP works
- [ ] Password reset works
- [ ] Role-based access works

### Coding Practice

- [ ] Problem listing works
- [ ] Topic filtering works
- [ ] Search works
- [ ] Constraints display correctly
- [ ] Editor loads
- [ ] Language selection works
- [ ] Run Code works
- [ ] Submit works
- [ ] Test cases evaluate correctly
- [ ] Submission history loads
- [ ] Accepted count updates
- [ ] Bookmarks work

### Assessments

- [ ] Assessment list works
- [ ] Enrollment works
- [ ] Questions load
- [ ] Timer works
- [ ] Attempts are enforced
- [ ] Code execution works
- [ ] Results calculate correctly
- [ ] Retake rules work
- [ ] Security verification works
- [ ] Camera state behaves correctly
- [ ] Screen sharing works
- [ ] Fullscreen behavior works
- [ ] Warnings are persisted
- [ ] Violation history is available

### Contests

- [ ] Contest list works
- [ ] Registration works
- [ ] Registration confirmation works
- [ ] Security verification works
- [ ] Timer works
- [ ] Problems load
- [ ] Language switching works
- [ ] Run Code works
- [ ] Submit works
- [ ] Accepted submissions are saved
- [ ] Score updates
- [ ] Solved count updates
- [ ] Penalty updates
- [ ] Result page shows actual data
- [ ] Leaderboard updates

### Courses

- [ ] Course list works
- [ ] Course content opens
- [ ] Progress persists
- [ ] Completion is detected
- [ ] Certificate is generated/displayed

### Organizations

- [ ] Organization registration works
- [ ] Email verification works
- [ ] Document submission works
- [ ] Verification status updates
- [ ] Admin review works
- [ ] Verified organization access works
- [ ] Organization assessment creation works
- [ ] Organization contest creation works
- [ ] Participant/result views work

### Certificates

- [ ] Milestone eligibility updates
- [ ] Course certificates appear after completion
- [ ] Certificate viewer opens
- [ ] QR information is generated/available
- [ ] Public certificate verification works where enabled

### Notifications / Email

- [ ] Notifications appear
- [ ] Transactional email sends
- [ ] OTP delivery works
- [ ] Duplicate suppression behaves correctly
- [ ] Email logs record delivery attempts

---

# Troubleshooting

## Backend Port Already in Use

If the backend reports an error such as:

```text
EADDRINUSE
```

another process is already using the configured port.

On Windows, identify the process:

```powershell
netstat -ano | findstr :5000
```

Then terminate the relevant process if appropriate.

---

## Frontend Receives HTML Instead of JSON

An error resembling:

```text
Unexpected token '<' ... not valid JSON
```

often indicates that the frontend sent an API request to a URL that returned HTML rather than JSON.

Check:

- API base URL
- Frontend environment variables
- Backend URL
- CORS configuration
- Reverse proxy configuration
- Authentication redirects

---

## Code Execution Works Locally but Not in Docker

Check whether the Docker image contains the required compiler/runtime.

For example, verify the tools required by the current execution service are installed inside the container.

Also check:

- file permissions
- executable paths
- working directory
- timeout handling
- process cleanup
- shell command compatibility
- environment variables

A compiler installed on Windows is not automatically available inside a Linux Docker image.

---

## Email Works Locally but Not in Production

Check:

- SMTP host
- SMTP port
- SMTP credentials
- verified sender
- environment variables on the hosting platform
- TLS configuration
- provider-side delivery logs

Never place SMTP secrets in frontend variables.

---

## Uploaded Files Disappear After Deployment

Check whether the deployment service uses an ephemeral filesystem.

Move important uploads to durable storage or a supported persistent disk.

---

## Database Connection Failure

Verify:

```text
DB_HOST
DB_PORT
DB_USER
DB_PASSWORD
DB_NAME
```

Also verify that the production database is running, reachable from the backend service, and initialized with the current schema.

---

# Git Workflow

This project uses two remotes in the local development environment.

## Internship Repository

Remote:

```text
origin
```

The local branch is:

```text
kamakshi
```

Normal internship push:

```bash
git push
```

## Personal Repository

Remote:

```text
personal
```

Repository:

```text
https://github.com/kanchi2006/CodeArena.git
```

Personal repository push:

```bash
git push personal kamakshi:main
```

This maps:

```text
local kamakshi → personal GitHub main
```

Keeping the remotes separate prevents an intentional personal push from being redirected to the internship repository.

---

# Project Status

CodeArena currently contains the major modules required for a full coding and skill-assessment ecosystem, including:

- Problem management and coding practice
- Online IDE and code execution
- Submission and result handling
- User dashboard and progress tracking
- Assessments
- Assessment security/proctoring
- Contests
- Contest security/proctoring integration
- Courses
- Course completion certificates
- Milestone achievements/certificates
- User profiles and analytics
- Organization onboarding and verification
- Organization assessments and contests
- Search
- Notifications
- Support content
- Localization/internationalization
- AI-assisted services
- Email/OTP workflows
- Docker configuration

Production readiness still depends on validating the deployed infrastructure, particularly code-execution isolation, persistent database/storage, SMTP delivery, environment configuration, and end-to-end security behavior.

---

# Future Enhancements

Potential areas for continued development include:

- Dedicated isolated execution workers
- Stronger sandboxing and container-per-execution isolation
- Queue-based code execution
- Resource-aware judging
- Scalable object storage for uploads
- Advanced analytics and skill recommendations
- Expanded learning paths
- Richer organization analytics
- More assessment question types
- Advanced contest ranking policies
- Enhanced security telemetry
- Automated deployment health checks
- Expanded API documentation
- Automated integration/end-to-end testing

These items are architectural opportunities rather than claims about functionality already implemented in the current build.

---

# Security and Responsible Use

CodeArena processes authentication information, assessment activity, contest activity, organization verification information, uploaded documents, and untrusted source code.

Recommended security practices include:

1. Keep credentials in environment variables.
2. Never commit `.env` files or provider secrets.
3. Use HTTPS in production.
4. Validate authorization on the backend.
5. Treat source-code execution as untrusted workload.
6. Apply execution time and resource limits.
7. Restrict filesystem and network access for execution workloads.
8. Store uploaded verification documents securely.
9. Avoid exposing sensitive operational details in error responses.
10. Rotate credentials when accidental exposure is suspected.

Client-side proctoring controls are monitoring mechanisms, not a complete security boundary. Sensitive contest/assessment rules and result calculations must remain server-validated.

---

# Contributing

For development contributions:

1. Create a feature branch.
2. Keep changes focused on a specific feature or bug.
3. Test frontend and backend flows affected by the change.
4. Run the production build before merging deployment-sensitive changes.
5. Do not commit secrets or generated dependency directories.
6. Update documentation when behavior or deployment requirements change.

Before committing:

```bash
git status
git diff
```

After committing:

```bash
git log -1 --oneline
```

---

# License

This repository is maintained as an academic/personal software project.

No open-source license is declared by this README. Add an explicit license file and update this section when the intended reuse and distribution terms have been finalized.

---

# Acknowledgement

CodeArena is developed as a comprehensive learning and assessment platform combining software engineering, database systems, web development, code execution, security monitoring, and AI-assisted functionality into one project.

---

<p align="center">
  <strong>CodeArena</strong><br>
  <em>Learn • Practice • Assess • Compete • Achieve</em>
</p>
