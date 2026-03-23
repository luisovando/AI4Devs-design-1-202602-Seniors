# LTI — ATS Project Brief

LTI is a startup that wants to develop an ATS (Applicant Tracking System).
Among the functions an ATS performs are:

- Creating job postings (jobs)
- Publishing jobs on boards, websites, social media, etc.
- Receiving applications to said jobs from applicants
- Reviewing job applications
- Conducting online tests for candidates
- Scheduling interviews
- Selected candidates are hired.

```mermaid
flowchart TD
    A[Create job posting] --> B[Define profile, requirements, and screening questions]
    B --> C[Publish opening]
    C --> C1[Job boards]
    C --> C2[Company website]
    C --> C3[Social media]
    C --> C4[Internal referrals]

    C1 --> D[Application reception]
    C2 --> D
    C3 --> D
    C4 --> D

    D --> E[Register candidate in ATS]
    E --> F[CV parsing and data extraction]
    F --> G[Create Job Application]
    G --> H[Automated filters]
    H --> H1[Knockout questions]
    H --> H2[Skill matching]
    H --> H3[Duplicates / blacklist]
    
    H1 --> I{Meets minimum criteria?}
    H2 --> I
    H3 --> I

    I -- No --> R[Auto-reject or archive in talent pool]
    I -- Yes --> J[Manual review by recruiter]

    J --> K{Advances to evaluation?}
    K -- No --> R
    K -- Yes --> L[Invite to online test]

    L --> M[Test completion and scoring]
    M --> N{Passes test?}
    N -- No --> R
    N -- Yes --> O[Schedule interviews]

    O --> O1[Recruiter interview]
    O1 --> O2[Technical interview]
    O2 --> O3[Hiring manager interview]
    O3 --> O4[Final interview / cultural fit]

    O4 --> P[Feedback consolidation]
    P --> Q{Candidate selected?}

    Q -- No --> S[Rejection with optional feedback]
    Q -- Yes --> T[Generate job offer]
    T --> U{Candidate accepts offer?}

    U -- No --> V[Close process or return to finalists]
    U -- Yes --> W[Hiring]
    W --> X[Onboarding and system registration]

    R --> Y[Talent pool for future openings]
    S --> Y
```

## Strategic Objectives

LTI wants to define the key features that differentiate it from its main competitors. Among its objectives are:

1. **Increase operational efficiency** of HR teams by reducing manual tasks and administrative overhead in the recruitment process.
2. **Improve real-time collaboration** between recruiters, hiring managers, and other process participants through a centralized, traceable, and shared workflow.
3. **Automate key pipeline stages** to accelerate time-to-fill and increase the scalability of the talent acquisition function.
4. **Integrate AI capabilities** that support job description writing, candidate evaluation, prioritization, and tracking.
5. **Provide actionable analytics** to optimize decision-making and identify improvement opportunities at each stage of the process.
6. **Deliver a better experience** for both candidates and internal teams through faster, more consistent, and more transparent processes.