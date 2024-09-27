## Context
Diversity Cyber Council (https://www.diversitycybercouncil.com/) is a 501c3 Non-Profit that serves under-represented demographics in the tech industry. They would like to enhance diversity and inclusion by facilitating education, training, and staffing opportunities to underrepresented demographics.

## Problem Statement
Diversity Cyber council wants to build ClearView, a HR platform that performs bias-free matching of candidate resumes with potential Employers. Additionally, it will have capabilities for data/metrics collection, aggregation and reporting.  It will also  integrate with external HR systems.

## Definitions, Acronyms, and Abbreviations
| Term | Definition |
| ---- | ---------- |
| DEI | Diversity, Equity, and Inclusion |
| ATS | Applicant Tracking System |

## System Context
```mermaid
 C4Context
    title System Context Diagram for ClearView
    
    %% People interacting with the system
    Person(HM, "Hiring Manager", "Users responsible for managing Job postings")
    Person(C, "Candidate", "Users applying for Job postings")
    Person(Admin, "Administrator", "Users responsible for managing the platform")

    %% The main system
    System(ClearView, "ClearView", "Anonymizes candidate profiles to and matches with job postings to reduce bias.")
    
    %% External system
    System_Ext(primaryHR, "External HR System", "External HR system")
    System_Ext(LLM, "External LLM Provider", "External LLM provider")
    
    %% Relationships between people and the system
    Rel(HM, ClearView, "Manage job postings")
    Rel(C, ClearView, "Manage profile and apply for postings")
    Rel(Admin, ClearView, "Manage the ClearView platform")
    Rel(ClearView, primaryHR, "Integrate with")
    Rel(ClearView, LLM, "Use LLM provider")
```

The system aims to serve the following user journeys:

### Hiring Manager User Journey
- A Hiring Manager registers themselves on the site.
- They register the employer on the platform. An AI can assist them with completing the profile of the employer.
- They can manage job postings i.e. Create, edit,update and delete job postings.
- They can:
  - Review AI-generated anonymized profiles for candidates with their match scores for a given role.
  - Unlock full candidate profiles by completing a payment.
  - Select a candidate for follow up.
  - Submit survey about a candidate and view survey results by candidates.
  - View Job Role and Employer specific aggregate metrics.

### Candidate User Journey
- A Candidate registers themselves on the site.
- They manage their personal profile - demographic details/contact information and their resume. An AI assists with improving their resume.
- The Candidate then marks themselves as active and an AI converts the profile and resume into an anonymized profile in SMART format.
- View the posting that have expressed interest in them.
- Follow up with hiring Manager for the role (outside the ClearView app)
- Mark themselves as inactive if hired.
- Submit a survey about the role and interviewer.

## TODO - Requirements
### Functional 
The following is a list of distilled requirements
- **REQ1**: Candidate must be able to create a profile by providing demographic, contact, and resume information.
- **REQ2**: Candidate can upload and update their resume in the system, and receive AI-generated tips and feedback to improve it.
- **REQ3**: Candidate must be able to view the number of employer interactions (e.g., profile views, expressions of interest).
- **REQ4**: Candidate must be able to mark themselves as inactive when hired.
- **REQ5**: Employers must be able to create a company profile through AI-assisted autofill.
- **REQ6**: Employers can post job descriptions, edit, and delete open roles in the system.
- **REQ7**: Employers must be able to view anonymized candidate profiles with AI-generated summaries (SMART format) and match scores.
- **REQ8**: Employers must be able to pay to unlock full candidate profiles (with demographic and PII data).
- **REQ9**: Employers can request survey feedback from job seekers after interviews.
- **REQ10**: Employers must be able to access analytic reports on hiring metrics, including diversity and DEI performance. .
- **REQ11**: Administrators must be able to generate and schedule out-of-the-box reports on KPIs, such as hiring rates, diversity trends, and performance against DEI goals.
- **REQ12**: Administrators must manage system configurations, such as user permissions, API integrations, and data retention policies.

### Architectural Characteristics
![architectural-context](./resources/arch-characteristics.png)
TODO - Add a blurb of text as to why we chose this ? 

## TODO - Assumptions
- The platform relies on the availability of APIs from HR systems for integration.
- The Admin user is part of the Employer similar to a hiring manager. 
- We assume that the Hiring manager is also the interviewer for the purposes of surveys. 

## WIP - Solution
### Logical Model
Here is a logical model of the system that explores key entities(a logical entity and not necessarily one from database parlance) and their relationships to inform APIs and data models.
**Note:** Some relationships adopt crow's foot notation just for clarity sakes.
**Note:** Some elements in the diagram may just be key attributes of an entity. Example a profile is a key attribute of a Candidate.
![katas2024 logical model.png](./resources/katas2024-logical-model.png)
- The system has multiple user with different roles - Candidate, Hiring Manager, DEI consultant, System Admin. 
- A user can optionally belong to an organization(employer). 
    - A Hiring manager will belong to an organization(Employer). 
    - A DEI consultant may belong to an organization.
    - A Candidate and System Admin don't necessarily belong to an employer but may be part of an internal Organization(for ex. ClearWorks)
- A Hiring Manger manages a job posting that is owned by an Employer
- A Candidate is matched with a Job Posting. 
- A Candidate, job posting and employer each have profiles. Profiles can be public or private(until made viewable)
- A candidate owns the survey results posted by Hiring Managers.
- A Hiring Manager owns the survey results posted by Candidates.
- Metrics are collected pertaining to a particular job posting for ex. candidate acceptance/rejection, candidate unlocks.  

## Architectural Style
TODO: Reference https://www.developertoarchitect.com/downloads/architecture-styles-worksheet.pdf and our priorities and state where we landed

## References
- [Requirements](https://docs.google.com/document/d/1jCHMAvgzqaYaAp09br12OC4ozpVXZR3s9ezgEqncZ9U/edit#heading=h.xvbdsi1e8ttg)
- [Presentation Slides](https://on24static.akamaized.net/event/46/37/41/6/rt/1/documents/resourceList1726751953205/todayskatasslides1726751953205.pdf)
- [C4 Model](https://c4model.com/)