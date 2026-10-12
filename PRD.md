# Product Requirements Document — Engineering Career Intelligence Platform

**Working title:** CareerGraph
**Document version:** 1.0
**Status:** MVP / Product Definition
**Product type:** AI-powered career intelligence platform for software engineers

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Problem Statement](#2-problem-statement)
3. [Product Vision](#3-product-vision)
4. [Product Goals](#4-product-goals)
5. [Non-Goals](#5-non-goals)
6. [Target Users](#6-target-users)
7. [Core Product Concept](#7-core-product-concept)
8. [Core Principles](#8-core-principles)
9. [High-Level User Journey](#9-high-level-user-journey)
10. [Feature Requirements](#10-feature-requirements)
11. [AI Agent Architecture](#11-ai-agent-architecture)
12. [AI Agents](#12-ai-agents)
13. [Data Architecture](#13-data-architecture)
14. [Evidence Model](#14-evidence-model)
15. [Confidence System](#15-confidence-system)
16. [Privacy & Security](#16-privacy--security)
17. [Proprietary Code Protection](#17-proprietary-code-protection)
18. [GitHub Sync](#18-github-sync)
19. [Dashboard](#19-dashboard)
20. [Career Profile Page](#20-career-profile-page)
21. [Job Match Page](#21-job-match-page)
22. [CV Generation Workflow](#22-cv-generation-workflow)
23. [Tech Stack Recommendation](#23-tech-stack-recommendation)
24. [API Architecture](#24-api-architecture)
25. [Asynchronous Analysis](#25-asynchronous-analysis)
26. [MVP](#26-mvp)
27. [MVP Exclusions](#27-mvp-exclusions)
28. [Phase 2](#28-phase-2)
29. [Phase 3](#29-phase-3)
30. [Phase 4](#30-phase-4)
31. [Job Recommendation Engine](#31-job-recommendation-engine)
32. [Anti-Hallucination Requirements](#32-anti-hallucination-requirements)
33. [Explainability](#33-explainability)
34. [Success Metrics](#34-success-metrics)
35. [Monetization](#35-monetization)
36. [Competitive Differentiation](#36-competitive-differentiation)
37. [Key Product Risks](#37-key-product-risks)
38. [MVP Development Plan](#38-mvp-development-plan)
39. [AI Evaluation Framework](#39-ai-evaluation-framework)
40. [Example End-to-End Experience](#40-example-end-to-end-experience)
41. [Long-Term Vision](#41-long-term-vision)

---

## 1. Executive Summary

CareerGraph is an AI-powered platform that reconstructs a software engineer's **actual professional experience from evidence** rather than relying solely on self-reported CVs.

A user connects their GitHub account. CareerGraph analyzes repositories, commits, pull requests, code structure, technologies, project history, and other available engineering signals. An AI agent transforms that evidence into a structured **Engineering Profile** describing the user's skills, technical depth, project experience, career progression, specialization, strengths, weaknesses, and likely job level.

The platform then uses that profile to help the user:

- Build an evidence-backed CV
- Improve their LinkedIn profile
- Discover suitable jobs
- Match themselves against job descriptions
- Identify skill gaps
- Tailor applications
- Prepare for interviews
- Track their job search
- Continuously update their professional profile as they continue coding

The fundamental product philosophy is:

> **Don't ask developers what they think they know. Analyze what they've actually demonstrated.**

---

## 2. Problem Statement

Most software engineers have difficulty accurately communicating their professional experience.

A developer may have spent years building:

- payment systems
- authentication systems
- SaaS platforms
- APIs
- databases
- realtime systems
- distributed workflows
- infrastructure
- internal tools

but their CV might simply say:

> "Developed backend APIs using Node.js."

This creates several problems.

### 2.1 Experience is difficult to quantify

Developers often don't remember:

- when they started using a technology
- which projects they used it on
- how extensively they used it
- what systems they actually built
- what their responsibilities were

### 2.2 CVs depend heavily on self-reporting

Traditional CVs are based on what the candidate remembers and chooses to write down.

There is no systematic verification layer.

### 2.3 Developers undersell themselves

Many engineers are technically strong but poor at describing their work.

### 2.4 Job descriptions are difficult to interpret

Candidates frequently apply to jobs without knowing:

- how well they match
- which requirements they satisfy
- which requirements they lack
- whether they are overqualified
- whether the job is actually appropriate for their level

### 2.5 Career development is reactive

Most developers only evaluate their skills when:

- searching for a job
- preparing a CV
- preparing for an interview

CareerGraph turns career analysis into a **continuous process**.

---

## 3. Product Vision

CareerGraph should become the **career intelligence layer for software engineers**.

Instead of:

> GitHub → CV

the long-term product becomes:

> **Engineering activity → Professional identity → Career decisions**

The platform should continuously understand:

- what the engineer has built
- what technologies they use
- what problems they solve
- how their technical complexity is evolving
- what jobs they are suited for
- what skills they should develop next

---

## 4. Product Goals

### Primary Goals

#### G1 — Reconstruct engineering experience

Automatically derive a structured professional profile from software-development evidence.

#### G2 — Create evidence-backed professional documents

Generate CVs, LinkedIn profiles, portfolio content, and application material from verified evidence.

#### G3 — Improve job targeting

Determine which jobs are genuinely appropriate for the user.

#### G4 — Explain job fit

Show exactly why a candidate matches or doesn't match a position.

#### G5 — Identify skill gaps

Show the difference between the user's demonstrated capabilities and market requirements.

#### G6 — Continuously update the profile

Allow the professional profile to evolve as the user continues working.

---

## 5. Non-Goals

The initial product will **not** attempt to:

- guarantee employment
- guarantee job interviews
- automatically fabricate experience
- invent business metrics
- falsely inflate seniority
- automatically apply to thousands of jobs without user approval
- replace recruiters
- replace technical interviews
- judge a developer purely by commit count
- treat GitHub activity as a perfect representation of someone's ability

---

## 6. Target Users

### Primary Persona — Software Engineer

A developer with at least several months of professional/project experience who wants to:

- find a job
- improve their CV
- understand their technical profile
- identify suitable jobs
- prepare for interviews

#### Example

A backend engineer has worked on 15 repositories over three years.

They know:

> "I use Node.js, PostgreSQL and React."

CareerGraph discovers:

> The engineer has demonstrated experience with multi-tenancy, payment processing, Redis queues, realtime systems, PostgreSQL schema design, authentication, and service-to-service APIs.

### Secondary Persona — Junior Developer

A junior developer wants to understand:

- what skills they are developing
- whether they are ready for internships/jobs
- what technologies they have actually practiced

### Future Persona — Engineering Manager

Managers could eventually use CareerGraph to understand:

- employee technical development
- engineering contributions
- skill progression
- technology exposure

This is **not an MVP target**.

---

## 7. Core Product Concept

The product revolves around an internal object called the:

### Engineering Evidence Graph

Instead of sending raw GitHub history directly to an LLM and asking:

> "Tell me about this developer."

CareerGraph creates structured evidence.

```text
Developer
   │
   ├── Repository
   │      ├── Technology
   │      ├── Commit
   │      ├── Pull Request
   │      ├── Feature
   │      └── Architecture
   │
   ├── Skill
   │      ├── Evidence
   │      ├── Confidence
   │      └── Recency
   │
   ├── Project
   │      ├── Role
   │      ├── Technologies
   │      └── Complexity
   │
   └── Career Phase
          ├── Skills
          ├── Projects
          └── Technical progression
```

This evidence layer becomes the foundation for every AI feature.

---

## 8. Core Principles

### 8.1 Evidence over claims

The system should prefer:

> "Repository X contains 27 NestJS modules."

over:

> "User is an expert in NestJS."

### 8.2 Fact vs inference

Every important conclusion should have one of:

| Type | Meaning |
| --- | --- |
| **FACT** | Directly observable from the evidence. |
| **INFERENCE** | Reasonable conclusion derived from multiple pieces of evidence. |
| **SELF-REPORTED** | Information provided by the user but not independently verified. |

### 8.3 Confidence scoring

Every major extracted skill should have a confidence score.

Example:

```text
NestJS
Confidence: 97%

Evidence:
- 8 repositories
- 1,200+ NestJS source files
- 18 months of activity
- 1,500+ related commits
```

### 8.4 Recency matters

Recent experience should generally carry more weight than very old experience.

### 8.5 Complexity matters more than volume

The system must not equate:

> 10,000 commits = better engineer.

It should consider:

- architecture
- ownership
- complexity
- consistency
- problem types
- production systems
- testing
- collaboration
- code quality

---

## 9. High-Level User Journey

```text
Landing Page
     ↓
Create Account
     ↓
Connect GitHub
     ↓
Select Repositories
     ↓
Analysis
     ↓
Engineering Profile
     ↓
Career Timeline
     ↓
Skills & Evidence
     ↓
Job Matching
     ↓
CV / LinkedIn
     ↓
Applications
     ↓
Interview Preparation
```

---

## 10. Feature Requirements

### 10.1 Authentication

Users must be able to:

- create an account
- sign in
- sign out
- reset credentials
- connect GitHub
- disconnect GitHub

Preferred authentication:

- GitHub OAuth
- Google OAuth
- email/password as fallback

### 10.2 GitHub Integration

Users authorize CareerGraph to access their GitHub data.

#### Required initial data

For each repository:

- repository name
- description
- visibility
- primary language
- languages
- creation date
- last update
- contributors
- commits
- branches where available
- pull requests where available
- README
- dependency manifests
- file structure

#### Commit data

Collect:

- SHA
- author
- timestamp
- message
- files changed
- additions
- deletions
- parent commits

#### Pull request data

Collect:

- title
- description
- author
- created date
- merged date
- changed files
- review activity
- labels

### 10.3 Repository Discovery

After connecting GitHub, display:

> **We found 42 repositories**

Categorize them:

| Category | Meaning |
| --- | --- |
| **Professional** | Likely work-related repositories. |
| **Personal** | Personal projects. |
| **Learning** | Tutorials, exercises, experiments. |
| **Unknown** | Require user classification. |

The user can manually override classifications.

### 10.4 Repository Analysis Agent

Each selected repository is analyzed independently.

The agent determines:

#### Project metadata

- project type
- estimated development period
- project maturity
- architecture
- major technologies

#### Technical features

Examples:

- authentication
- payments
- queues
- realtime communication
- caching
- databases
- APIs
- notifications
- geospatial functionality
- file processing
- AI integration

#### Engineering patterns

Examples:

- modular architecture
- multi-tenancy
- idempotency
- concurrency control
- RBAC
- event-driven architecture
- service-to-service authentication

#### Contribution analysis

Estimate:

- primary contributor
- significant contributor
- supporting contributor

Never claim sole ownership solely from commit counts.

### 10.5 Engineering Timeline

Generate a chronological timeline.

Example:

```text
2024
Frontend foundations

2025
Backend/API development
↓
Authentication
↓
Payments
↓
Database architecture

2026
Multi-tenancy
↓
Distributed processing
↓
Realtime systems
↓
Offline-first systems
↓
Observability
```

Each timeline event must link to evidence.

### 10.6 Skills Intelligence

Skills are categorized.

#### Languages

- TypeScript
- JavaScript
- Python
- SQL

#### Backend

- Node.js
- NestJS
- Express
- Django

#### Frontend

- React
- Next.js
- Tailwind

#### Infrastructure

- Docker
- CI/CD
- AWS

#### Architecture

- distributed systems
- multi-tenancy
- queues
- realtime systems

#### Skill scoring

Each skill receives:

```text
Skill
Level
Confidence
Evidence count
First seen
Last seen
Projects
```

Example:

```text
NestJS

Level: Advanced
Confidence: 95%

First seen: Oct 2025
Last seen: Aug 2026

Repositories: 7
Evidence events: 1,240

Evidence:
- production APIs
- modular architecture
- authentication
- payments
- queues
```

The system should avoid claiming "expert" by default.

### 10.7 Engineering Depth Analysis

Analyze the engineer across dimensions:

| Dimension | Level |
| --- | --- |
| Backend | Advanced |
| Database Design | Strong |
| API Architecture | Advanced |
| Authentication | Strong |
| Payments | Strong |
| Distributed Systems | Competent |
| Testing | Competent |
| Infrastructure | Developing |

Every score must be explainable.

### 10.8 Professional Specialization

The AI should determine likely specialization.

Possible outputs:

- Backend Engineer
- Full-Stack Engineer
- Frontend Engineer
- Platform Engineer
- DevOps Engineer
- Data Engineer
- ML Engineer

The system can recommend:

#### Primary positioning

> Backend-focused Full-Stack Engineer

#### Secondary positioning

> Node.js / TypeScript Backend Engineer

#### Specialization

> SaaS, payments and customer-engagement systems

### 10.9 Career Level Assessment

Evaluate:

- technical complexity
- ownership
- architecture
- independence
- production exposure
- breadth
- collaboration evidence

Possible result:

```text
Recommended level:

Mid-level Backend Engineer

Strong candidate for:
- Mid-level
- selective Senior roles

Not enough evidence for:
- Staff
- Principal
```

The system must explicitly explain its reasoning.

### 10.10 Career Strengths

Generate:

#### Top strengths

1. Backend architecture
2. TypeScript/NestJS
3. PostgreSQL
4. Payments
5. API design

Each strength should link to evidence.

### 10.11 Career Gaps

Example:

> AWS infrastructure experience is limited compared with backend experience.

Then recommend:

> Learn AWS ECS/EKS, RDS, S3, CloudWatch and Terraform.

This becomes the foundation for the **Career Development Agent**.

### 10.12 Job Description Analyzer

User can paste a job description.

The AI extracts:

- required skills
- preferred skills
- experience requirements
- responsibilities
- seniority
- location
- work authorization requirements

### 10.13 Job Match Engine

Output:

```text
# 87% Match

### Strong matches
- TypeScript
- Node.js
- PostgreSQL
- REST APIs
- payments

### Partial matches
- AWS
- Kubernetes

### Missing
- Terraform

### Recommendation
> **Apply**
```

And explain why.

### 10.14 Job Match Evidence

Every match must be traceable.

Example:

> **PostgreSQL — Strong Match**

Evidence:

> Used PostgreSQL across Vemtap, McomMall and McomReward.

The user can click:

**View evidence**

and see the relevant project.

### 10.15 CV Generator

The CV generator uses the Engineering Evidence Graph.

Templates:

- Backend Engineer
- Full-Stack Engineer
- Software Engineer
- Startup Engineer

The user can select:

- target role
- target company
- target job description

The AI produces a tailored CV.

#### Critical rule

No unsupported claims.

### 10.16 LinkedIn Optimizer

Generate:

- headline
- About section
- experience descriptions
- skills
- project descriptions

The system should prioritize evidence-backed achievements.

### 10.17 Application Agent

The agent helps with:

- application questions
- cover letters
- recruiter messages
- application tracking
- follow-ups

The user must approve anything sent externally.

### 10.18 Interview Agent

Once a user applies to a job:

The system generates:

#### Technical questions

Based on:

- job requirements
- user's experience
- projects

#### Behavioral questions

Based on:

- career history
- projects
- leadership evidence

#### Project questions

Example:

> "Explain how you implemented idempotency in your payment system."

The AI can then conduct a mock interview.

### 10.19 Application Tracker

Statuses:

```text
Saved
Applied
Recruiter
Assessment
Interview
Technical
Final
Offer
Rejected
Withdrawn
```

Dashboard metrics:

```text
Applications: 84
Responses: 12
Interviews: 6
Final rounds: 2
Offers: 1
```

The system should calculate:

- response rate
- interview rate
- offer rate

### 10.20 Job Search Analytics

The AI should identify patterns.

Example:

> You have applied to 73 backend roles.
>
> Node.js roles: 14% response rate.
>
> Python roles: 2% response rate.
>
> Fintech roles: 19% response rate.
>
> Senior roles: 3% response rate.

Then:

> Your strongest market appears to be Node.js/TypeScript backend roles in fintech/SaaS.

---

## 11. AI Agent Architecture

The product should NOT use one giant AI prompt.

Use specialized agents.

```text
                    Orchestrator
                         │
        ┌────────────────┼────────────────┐
        ↓                ↓                ↓
 Repository Agent   Career Agent     Job Agent
        │                │                │
        ↓                ↓                ↓
 Evidence Store ←──────→ Profile ←──────→ Job Graph
                         │
                         ↓
                  Application Agent
                         │
                         ↓
                  Interview Agent
```

---

## 12. AI Agents

### 12.1 Repository Analysis Agent

Input:

- repository metadata
- commit history
- PRs
- dependency manifests
- code structure

Output:

```json
{
  "project_type": "...",
  "technologies": [],
  "features": [],
  "architecture_patterns": [],
  "contribution_level": "...",
  "evidence": []
}
```

### 12.2 Evidence Agent

Combines repository findings.

Responsibilities:

- deduplicate evidence
- calculate confidence
- resolve conflicts
- identify recurring skills

### 12.3 Career Intelligence Agent

Produces:

- career timeline
- specialization
- strengths
- weaknesses
- level assessment

### 12.4 Job Intelligence Agent

Analyzes job descriptions.

### 12.5 Matching Agent

Compares:

```text
Candidate Evidence
        +
Job Requirements
        ↓
Match Analysis
```

### 12.6 CV Agent

Creates evidence-backed professional documents.

### 12.7 Interview Agent

Generates personalized preparation.

---

## 13. Data Architecture

Core entities:

```text
User
GitHubAccount
Repository
Commit
PullRequest
RepositoryAnalysis
Evidence
Skill
SkillEvidence
Project
CareerPhase
CareerProfile
Job
JobRequirement
JobMatch
Resume
Application
InterviewSession
InterviewQuestion
```

### Relationship

```text
User
 ├── GitHubAccount
 │     └── Repository
 │           ├── Commit
 │           ├── PullRequest
 │           └── RepositoryAnalysis
 │
 └── CareerProfile
       ├── Skill
       │    └── SkillEvidence
       ├── Project
       └── CareerPhase

Job
 └── JobRequirement

CareerProfile
 └── JobMatch
        └── JobRequirement
```

---

## 14. Evidence Model

This is one of the most important parts of the system.

Example:

```json
{
  "type": "technology_usage",
  "technology": "NestJS",
  "repository_id": "repo_123",
  "evidence": "Production API contains modular NestJS architecture",
  "source": "repository_analysis",
  "confidence": 0.96,
  "first_seen": "2025-10-01",
  "last_seen": "2026-08-01"
}
```

Possible evidence types:

- technology usage
- architectural pattern
- feature
- responsibility
- project ownership
- contribution
- collaboration
- production deployment
- testing
- integration

---

## 15. Confidence System

Confidence should consider:

```text
Evidence quantity
+
Evidence diversity
+
Recency
+
Duration
+
Project importance
+
Direct code evidence
```

Example:

```text
TypeScript

Evidence:
12 repositories
2 years
5 production applications
1,500 commits

Confidence: 98%
```

---

## 16. Privacy & Security

This is a **critical requirement**.

Users may connect private company repositories.

### Requirements

- OAuth token encryption
- encrypted secrets
- least-privilege GitHub scopes
- repository-level selection
- revoke GitHub access
- delete all imported data
- configurable retention
- no training on user source code by default
- audit logs
- secure AI provider handling

### Privacy controls

User must be able to:

> Delete my GitHub data
>
> Delete my entire CareerGraph profile
>
> Disconnect GitHub
>
> Exclude repository
>
> Exclude commit history

---

## 17. Proprietary Code Protection

The platform should avoid sending unnecessary source code to external AI models.

Prefer analyzing:

- Git metadata
- AST information
- file names
- dependency manifests
- framework structure
- diffs
- commit messages

Only send source-code snippets when necessary for a specific analysis.

---

## 18. GitHub Sync

Initial sync:

```text
Connect GitHub
↓
Repository discovery
↓
Select repositories
↓
Import history
↓
Analyze
```

Future sync:

```text
New commits
↓
Incremental analysis
↓
Update evidence
↓
Update career profile
```

The system should not repeatedly analyze unchanged history.

---

## 19. Dashboard

The dashboard should show:

### Professional Identity

> Backend-focused Full-Stack Engineer

### Top Skills

```text
TypeScript       96%
NestJS           94%
PostgreSQL       91%
Node.js          90%
React            84%
```

### Career Timeline

Visual timeline.

### Engineering Strength

> Backend architecture

### Recommended Roles

```text
Backend Engineer        94%
Full-Stack Engineer     89%
Platform Engineer       78%
```

### Job Search

```text
Applications      32
Interviews         5
Response rate     15.6%
```

---

## 20. Career Profile Page

Sections:

1. Professional identity
2. Summary
3. Technical skills
4. Engineering depth
5. Career timeline
6. Projects
7. Evidence
8. Strengths
9. Gaps
10. Recommended roles

---

## 21. Job Match Page

```text
Backend Engineer
Acme Inc.

87% MATCH

█████████████████░░░

Strong matches
✓ TypeScript
✓ Node.js
✓ PostgreSQL
✓ REST APIs

Partial
△ AWS

Missing
✕ Kubernetes

Recommendation
APPLY
```

---

## 22. CV Generation Workflow

```text
Select role
     ↓
Select job description
     ↓
Select evidence
     ↓
AI generates CV
     ↓
Evidence validation
     ↓
User review
     ↓
Export PDF/DOCX
```

The validation layer should flag unsupported claims.

---

## 23. Tech Stack Recommendation

Given the product's nature, an initial stack could be:

### Frontend

**Next.js + TypeScript**

- App Router
- Tailwind
- TanStack Query
- Zustand/Redux where necessary

### Backend

**NestJS + TypeScript**

### Database

**PostgreSQL**

### ORM

**Prisma**

### Queue

**Redis + BullMQ**

### Authentication

GitHub OAuth + Google OAuth

### AI

Provider abstraction supporting:

- OpenAI
- Anthropic
- Gemini
- other compatible providers

### Infrastructure

Initially:

- Docker
- Vercel for frontend
- managed PostgreSQL
- managed Redis
- object storage

Don't introduce Kubernetes early.

---

## 24. API Architecture

Example:

```text
/api/auth
/api/github
/api/repositories
/api/analysis
/api/evidence
/api/profile
/api/skills
/api/jobs
/api/job-matches
/api/resumes
/api/applications
/api/interviews
```

---

## 25. Asynchronous Analysis

GitHub analysis can be expensive.

Do not process everything synchronously.

Use:

```text
POST /analysis
        ↓
Create Analysis Job
        ↓
BullMQ
        ↓
Repository Agent
        ↓
Evidence Agent
        ↓
Career Agent
        ↓
Profile Ready
```

Frontend receives progress through polling or WebSockets/SSE.

Example:

```text
Analyzing repositories...

██████████████░░░░ 72%

Analyzed:
18 / 26 repositories

Extracted:
1,492 evidence items
```

---

## 26. MVP

The MVP should be significantly smaller than the full vision.

### MVP must include

#### Authentication

- account
- GitHub OAuth

#### GitHub

- repository discovery
- repository selection
- commits
- basic repository analysis

#### AI

- repository summaries
- skills extraction
- evidence extraction
- career timeline
- professional summary

#### Career profile

- skills
- projects
- timeline
- strengths
- weaknesses
- specialization

#### Job analysis

- paste job description
- match score
- requirements analysis
- skill gaps
- recommendation

#### CV

- evidence-backed CV generation

---

## 27. MVP Exclusions

Do NOT build initially:

- automatic job applications
- LinkedIn integration
- recruiter marketplace
- browser automation
- interview voice agent
- team analytics
- Kubernetes infrastructure
- complex social features
- mobile app

---

## 28. Phase 2

Add:

- job aggregation
- application tracking
- LinkedIn optimization
- interview preparation
- GitHub incremental sync
- career recommendations
- job search analytics

---

## 29. Phase 3

Add:

- autonomous career agent
- automatic job discovery
- personalized learning plans
- interview simulator
- recruiter interactions
- portfolio generation
- public engineering profile

---

## 30. Phase 4

Potential platform expansion:

### Engineering Passport

A portable professional identity backed by evidence.

Instead of:

> "I know TypeScript."

The candidate can share:

> "Here is my verified engineering history."

Recruiters could potentially view:

- technologies
- project history
- experience timeline
- engineering strengths
- verified evidence

This could eventually become a **developer professional identity platform**.

---

## 31. Job Recommendation Engine

The system should rank jobs using:

```text
Technical Match
+
Seniority Match
+
Domain Match
+
Location Match
+
Experience Match
+
Technology Recency
```

Example:

```text
Overall: 91%

Technical: 96%
Seniority: 88%
Domain: 93%
Location: 100%
Experience: 86%
```

---

## 32. Anti-Hallucination Requirements

The AI must never:

- invent users
- invent revenue
- invent performance improvements
- invent team size
- invent leadership
- invent years of experience
- invent production scale
- claim technologies without evidence

If uncertain:

> **Insufficient evidence**

must be an acceptable answer.

---

## 33. Explainability

Every important AI conclusion should have:

**Conclusion**

> Strong PostgreSQL experience.

**Evidence**

> Found across 8 repositories.

**Reasoning**

> Used PostgreSQL for production APIs, complex schemas and migrations over 18 months.

This is essential to user trust.

---

## 34. Success Metrics

### Activation

Percentage of users who:

> Sign up → connect GitHub → complete analysis.

Target: **>60%**

### Profile completion

Percentage who view generated profile.

Target: **>80%**

### Job match usage

Percentage who analyze at least one job.

Target: **>50%**

### CV generation

Percentage who generate a CV.

Target: **>40%**

### Retention

Users returning within 30 days.

Target: **>25% initially**

### User satisfaction

After analysis:

> "Did this profile accurately represent your experience?"

Target: **>85% yes**

This metric may be more important than raw signup numbers.

---

## 35. Monetization

### Free

- GitHub analysis
- basic career profile
- limited job matches
- one CV

### Pro

Potentially **$10–20/month**.

Includes:

- unlimited analysis
- advanced evidence
- unlimited job matching
- tailored CVs
- LinkedIn optimization
- interview preparation
- application tracking

### Career Pro

Higher tier:

- autonomous job discovery
- advanced application assistant
- interview simulator
- career planning
- continuous GitHub monitoring

---

## 36. Competitive Differentiation

The product should NOT position itself as:

> "AI CV generator."

That market is crowded.

The differentiation is:

> **AI career intelligence built from your actual engineering history.**

Competitors generally start with:

**CV → AI → improved CV**

CareerGraph starts with:

**Engineering evidence → AI → professional identity → CV**

That distinction should be central to the product.

---

## 37. Key Product Risks

### Risk 1 — GitHub doesn't represent the entire career

Solution:

Allow users to add:

- previous jobs
- private work
- freelance projects
- manually verified experience

Label them:

**Self-reported**

rather than pretending they're Git-verified.

### Risk 2 — Large repositories create expensive AI analysis

Solution:

Use:

- deterministic preprocessing
- repository summaries
- incremental analysis
- caching
- smaller models for classification
- stronger models only for synthesis

### Risk 3 — AI exaggerates seniority

Solution:

Evidence-backed seniority model with explicit confidence.

### Risk 4 — Privacy concerns

Solution:

Privacy-first architecture and transparent controls.

### Risk 5 — Commit quantity becomes the primary signal

Solution:

Make commits only one of many signals.

---

## 38. MVP Development Plan

### Sprint 1

- project setup
- authentication
- GitHub OAuth
- database
- basic dashboard

### Sprint 2

- GitHub repository discovery
- repository selection
- commit ingestion
- background jobs

### Sprint 3

- repository analyzer
- technology detection
- project classification
- evidence model

### Sprint 4

- career profile
- skill intelligence
- career timeline

### Sprint 5

- job description analyzer
- job matching

### Sprint 6

- CV generator
- evidence validation

### Sprint 7

- UX refinement
- onboarding
- privacy controls
- billing

### Sprint 8

- beta testing
- performance optimization
- AI evaluation

---

## 39. AI Evaluation Framework

Before launching, create a benchmark using real repositories.

For each repository, manually establish ground truth:

```text
Technology:
NestJS ✓

Feature:
Payments ✓

Architecture:
Multi-tenant ✓

Ownership:
Primary contributor ✓
```

Then compare AI output.

Metrics:

- precision
- recall
- hallucination rate
- evidence attribution accuracy
- skill classification accuracy

The most important metric:

> **Unsupported claim rate**

Target: **Near zero.**

---

## 40. Example End-to-End Experience

A developer signs up.

### Step 1 — Connect GitHub

They authorize access.

### Step 2 — Repository selection

CareerGraph finds:

> 37 repositories

The user selects 21.

### Step 3 — Analysis

```text
Repositories       21/21
Commits            18,420
Projects           14
Evidence items     6,214
Skills discovered  47
```

### Step 4 — Professional profile

CareerGraph produces:

> **Backend-focused Full-Stack Engineer**

Strongest skills:

- TypeScript
- Node.js
- PostgreSQL
- NestJS
- React

Specializations:

- SaaS
- payments
- marketplaces
- customer engagement

### Step 5 — Job matching

User pastes a job:

> Senior Backend Engineer — Fintech

CareerGraph:

> **91% match**

### Step 6 — Gap identification

It identifies:

**Strong**

- Node.js
- TypeScript
- PostgreSQL
- payments
- APIs

**Gap**

- AWS
- Kubernetes

### Step 7 — CV generation

User clicks:

> Generate tailored CV

CareerGraph produces a CV based on **verified evidence**.

### Step 8 — Application tracking

User applies.

CareerGraph tracks the application.

### Step 9 — Interview preparation

Before the interview:

> "This company is likely to ask you about payment idempotency, PostgreSQL transactions, queues and NestJS architecture."

The interview agent prepares the candidate.

---

## 41. Long-Term Vision

The ultimate product isn't a CV generator.

It's:

# An AI career operating system for software engineers.

The system continuously knows:

```text
What you've built
       ↓
What you're good at
       ↓
What you're qualified for
       ↓
What the market wants
       ↓
Where the gaps are
       ↓
What you should learn
       ↓
Which jobs to pursue
       ↓
How to present yourself
       ↓
How to prepare
       ↓
How your career evolves
```

---

## Core Idea

The GitHub analysis is effectively the **first prototype of the core intelligence layer** — raw development history transformed into a structured professional narrative, with explicit evidence and caveats.

If building this, start with only one promise:

> **"Connect your GitHub. We'll show you what your engineering career actually looks like."**

Then build the job-search functionality around that.
