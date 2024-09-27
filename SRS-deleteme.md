# Software Requirements Specification (SRS) for ClearView

<!-- TOC -->
* [Software Requirements Specification (SRS) for ClearView](#software-requirements-specification-srs-for-clearview)
    * [1. Introduction](#1-introduction)
        * [1.1 Purpose](#11-purpose)
        * [1.2 Scope](#12-scope)
        * [1.3 Definitions, Acronyms, and Abbreviations](#13-definitions-acronyms-and-abbreviations)
        * [1.4 References](#14-references)
    * [2. Overall Description](#2-overall-description)
        * [2.1 Product Perspective](#21-product-perspective)
        * [2.2 Product Features](#22-product-features)
        * [2.3 User Classes and Characteristics](#23-user-classes-and-characteristics)
        * [2.4 Operating Environment](#24-operating-environment)
        * [2.5 Assumptions and Dependencies](#25-assumptions-and-dependencies)
    * [3. System Features](#3-system-features)
        * [3.1 Feature 1: Anonymization of Candidate Data](#31-feature-1-anonymization-of-candidate-data)
            * [3.1.1 Description and Priority](#311-description-and-priority)
            * [3.1.2 Functional Requirements](#312-functional-requirements)
        * [3.2 Feature 2: AI-Generated Candidate Profiles and Resume Tips](#32-feature-2-ai-generated-candidate-profiles-and-resume-tips)
            * [3.2.1 Description and Priority](#321-description-and-priority)
            * [3.2.2 Functional Requirements](#322-functional-requirements)
        * [3.3 Feature 3: Similarity Score/Match](#33-feature-3-similarity-scorematch)
            * [3.3.1 Description and Priority](#331-description-and-priority)
            * [3.3.2 Functional Requirements](#332-functional-requirements)
        * [3.4 Feature 4: Reporting and Analytics](#34-feature-4-reporting-and-analytics)
            * [3.4.1 Description and Priority](#341-description-and-priority)
            * [3.4.2 Functional Requirements](#342-functional-requirements)
        * [3.5 Feature 5: Survey Mechanism for Interview Feedback](#35-feature-5-survey-mechanism-for-interview-feedback)
            * [3.5.1 Description and Priority](#351-description-and-priority)
            * [3.5.2 Functional Requirements](#352-functional-requirements)
    * [4. External Interface Requirements](#4-external-interface-requirements)
        * [4.1 User Interfaces](#41-user-interfaces)
            * [4.1.1 Employer Interface](#411-employer-interface)
            * [4.1.2 Job Seeker Interface](#412-job-seeker-interface)
            * [4.1.3 Administrator Interface](#413-administrator-interface)
        * [4.2 Hardware Interfaces](#42-hardware-interfaces)
        * [4.3 Software Interfaces](#43-software-interfaces)
            * [4.3.1 Integration with HR Systems](#431-integration-with-hr-systems)
            * [4.3.2 API Requirements](#432-api-requirements)
        * [4.4 Communication Interfaces](#44-communication-interfaces)
            * [4.4.1 Internal System Communication](#441-internal-system-communication)
            * [4.4.2 Data Transfer Protocols](#442-data-transfer-protocols)
            * [4.4.3 Notification Services](#443-notification-services)
    * [4.5 Compliance and Data Privacy](#45-compliance-and-data-privacy)
    * [5. Non-functional Requirements](#5-non-functional-requirements)
        * [5.1 Performance Requirements](#51-performance-requirements)
        * [5.2 Safety Requirements](#52-safety-requirements)
        * [5.3 Security Requirements](#53-security-requirements)
        * [5.4 Usability Requirements](#54-usability-requirements)
    * [6. Other Requirements](#6-other-requirements)
    * [7. User Journeys](#7-user-journeys)
        * [7.1 Hiring Manager User Journey](#71-hiring-manager-user-journey)
        * [7.2 Job Seeker User Journey](#72-job-seeker-user-journey)
        * [7.3 Admin User Journey](#73-admin-user-journey)
    * [8. Technical Details](#8-technical-details)
<!-- TOC -->

## 1. Introduction

### 1.1 Purpose
ClearView is a supplemental HR platform that anonymizes candidate information while highlighting objective skills and qualifying experience to reduce bias in the hiring process. It also enables DEI consultants to shadow employer interviews to rate the interviewer and report findings to executive management.

### 1.2 Scope
ClearView aims to provide a more equitable hiring experience by leveraging AI to reconstruct job seeker resumes and eliminating biasing factors. The platform will include capabilities for data aggregation and reporting, while integrating with popular HR systems.

### 1.3 Definitions, Acronyms, and Abbreviations
| Term | Definition |
| ---- | ---------- |
| DEI | Diversity, Equity, and Inclusion |
| ATS | Applicant Tracking System |


## 2. Overall Description

### 2.1 Product Perspective
ClearView operates as an independent platform but interfaces with existing HR systems like SAP SuccessFactors, UKG Pro, and Workday to enhance functionality and data accuracy.

### 2.2 Product Features
- Anonymization of candidate data
- AI-generated candidate profiles based on S.M.A.R.T goals
- Similarity score/match with job descriptions
- Auto-generated resume tips
- Reporting capabilities for DEI consultants and employers

### 2.3 User Classes and Characteristics
- **Employers**: Companies focused on equitable hiring processes.
- **Job Candidates**: Professionals seeking a streamlined and fair hiring process.
- **Administrators**: Platform managers who oversee user registrations and generate analytics reports.

### 2.4 Operating Environment
We assume that ClearView will be a cloud-based application accessible via web browsers. Extra user interface form factors, like phone or tablet apps, can be added later.

### 2.5 Assumptions and Dependencies
The platform relies on the availability of APIs from HR systems for integration.

## 3. System Features

### 3.1 Feature 1: Anonymization of Candidate Data

#### 3.1.1 Description and Priority
**Priority: High**

This feature ensures that all personally identifiable information (PII) and potential biasing factors are removed from candidate profiles during the initial stages of the hiring process. This enables hiring managers to make objective decisions based solely on skills, experience, and qualifications.

#### 3.1.2 Functional Requirements
- **Data Obfuscation**: The platform must strip all identifiable personal information from resumes, including but not limited to:
    - Candidate name
    - Contact information (e.g., email, phone number, address)
    - Gender and pronouns
    - Race, ethnicity, and national origin
    - Date of birth and age
    - Marital status and family details
    - Hobbies or extracurricular activities that may indicate lifestyle preferences
- **Education and Job Titles**: While maintaining relevant qualifications like education and job titles, the platform must remove or anonymize details that could bias decision-making (e.g., graduation year, highly specific institution names if unnecessary).
- **Cultural Indicators**: The platform must eliminate any potential cultural, racial, or lifestyle indicators that are not related to job performance, such as organizations or associations that reveal a particular bias or orientation.
- **Anonymized Profiles**: Before a candidate profile is unlocked by the hiring manager, the system will display an anonymized version, highlighting only experience, skills, qualifications, and achievements in a standardized format.

### 3.2 Feature 2: AI-Generated Candidate Profiles and Resume Tips

#### 3.2.1 Description and Priority
**Priority: High**

The system will leverage AI to process job seeker resumes and reconstruct them into a format that focuses on S.M.A.R.T goals (Specific, Measurable, Achievable, Relevant, and Time-bound), qualifications, and relevant experience. The AI will also provide personalized tips to job seekers to improve their resumes.

#### 3.2.2 Functional Requirements
- **Resume Parsing**: The AI must be able to parse uploaded resumes and extract key information, including but not limited to:
    - Work experience
    - Education
    - Certifications and skills
    - Achievements and relevant projects
- **S.M.A.R.T Goal Conversion**: After parsing, the AI will reconstruct the resume into S.M.A.R.T goals by converting achievements and job roles into measurable outcomes. For example:
    - **Original Entry**: "Managed a team of five engineers."
    - **S.M.A.R.T Goal**: "Led a team of five engineers to successfully deliver 3 product launches within a 6-month period, improving time-to-market by 25%."
- **AI-Generated Resume Tips**: Upon uploading a resume, the system must automatically generate feedback for the job seeker. Tips must be specific and tailored to the candidate's experience, such as:
    - Recommendations on adding measurable achievements to bullet points
    - Suggestions for improving alignment with specific job descriptions
    - Advice on optimizing the resume’s structure and content for better readability
- **Anonymization During AI Processing**: While generating the reconstructed profile and resume tips, the AI must ensure all PII remains anonymized and that only relevant details are included in the final profile.

### 3.3 Feature 3: Similarity Score/Match

#### 3.3.1 Description and Priority
**Priority: High**

A core feature of the system is the ability to calculate a similarity score or match rating between a job seeker’s anonymized profile and open job roles posted by employers. This score will help hiring managers objectively assess candidates before reviewing their full profiles.

#### 3.3.2 Functional Requirements
- **Resume-Job Description Matching**: The AI must calculate a similarity score between anonymized resumes and job descriptions based on:
    - Skills listed in the job description versus those on the resume
    - Relevant experience required by the job and present in the candidate’s history
    - Alignment between qualifications (e.g., certifications, degrees) and job requirements
- **Weighting System**: The AI should implement a configurable weighting system where certain skills or qualifications can carry more importance based on the job description. For instance:
    - Critical skills may be weighted higher (e.g., programming languages for a developer role).
    - Secondary or "nice-to-have" qualifications should impact the score less.
- **Threshold for Match**: There should be a configurable threshold for hiring managers to set a minimum match score. Candidates below this threshold will not be considered unless manually reviewed by an employer.
- **Report on Match Factors**: The system must provide a breakdown of the key factors contributing to the match score, such as:
    - Skills that match well versus those that do not
    - Experience gaps (e.g., missing years in a specific role)
    - Overqualified or underqualified indicators (e.g., too much or too little experience)

### 3.4 Feature 4: Reporting and Analytics

#### 3.4.1 Description and Priority
**Priority: Medium**

ClearView must provide comprehensive reporting and analytics capabilities to track various data points throughout the hiring and interviewing process. Reports must cover both the company’s hiring patterns and diversity, equity, and inclusion (DEI) metrics.

#### 3.4.2 Functional Requirements
- **Key Data Points**: The system must collect and report on the following data points:
    - **Data Point 1**: Decision to move forward with a candidate (tracked at each stage).
    - **Data Point 2**: Unlocking of a full candidate profile (when an employer chooses to view the entire resume).
    - **Data Point 3**: 5-question survey sent to the job candidate about the interviewer.
    - **Data Point 4**: 5-question survey sent to the interviewer about the job candidate.
    - **Data Point 5**: Accumulation of demographic data after rejecting or offering a candidate.
- **Monthly Reports**: ClearView must automatically generate monthly reports that present the following key performance indicators (KPIs):
    - Time to fill positions (from posting to hire).
    - Average match score of candidates who moved forward in the process.
    - DEI metrics related to candidate demographics (race, gender, etc.) versus interview outcomes.
    - Comparison of offers made versus rejections and the demographic trends of each.
    - Survey feedback from both candidates and interviewers, aggregated for trends.
- **Custom Reporting**: Administrators should have the ability to create custom reports based on available data points, filtering by role, time frame, or demographic indicators.
- **Data Export**: All reports must be exportable in standard formats (e.g., CSV, PDF) for external use.

### 3.5 Feature 5: Survey Mechanism for Interview Feedback

#### 3.5.1 Description and Priority
**Priority: Low**

ClearView will include a feedback survey system that collects structured feedback from both job candidates and interviewers after each interview. This feedback will be included in the monthly analytics reports.

#### 3.5.2 Functional Requirements
- **Candidate Survey**: A 5-question survey will be sent to candidates after each interview, focusing on the professionalism, fairness, and inclusivity of the interviewer.
- **Interviewer Survey**: A 5-question survey will be sent to interviewers to evaluate the candidate’s preparedness, qualifications, and potential fit for the role.
- **Survey Customization**: Administrators should have the ability to modify survey questions based on company-specific feedback needs.



### 4.2 Hardware Interfaces
Since ClearView is a cloud-based application, there are no hardware interface requirements for users. However, users must have access to standard computing devices with internet connectivity, such as:
- Desktop computers or laptops
- Tablets or smartphones
- Minimum browser support for HTML5 and JavaScript

### 4.3 Software Interfaces

ClearView will integrate with multiple third-party software systems, especially popular HR management platforms, for seamless data exchange. The integration will occur through REST APIs or other secure protocols to allow for pulling and pushing relevant information. The following are key software interfaces required:

#### 4.3.1 Integration with HR Systems
The system must integrate with popular HR platforms such as:
- **SAP SuccessFactors**
    - Sync job postings and candidate details.
    - Allow hiring managers to retrieve applicant data and upload them to ClearView for analysis.
- **UKG Pro**
    - Push candidate profile updates back to the HR system if needed.
    - Synchronize with job openings listed in UKG Pro to align candidates with opportunities.
- **Paycor**
    - Exchange employee records, including historical job and performance data.
    - Collect demographic information (without PII) for diversity and DEI reporting.
- **Workday**
    - Sync recruitment pipelines from Workday, pulling job descriptions and posting data.
    - Push hiring decision metrics, such as match scores and interview data, back to Workday for internal tracking.

#### 4.3.2 API Requirements
- **RESTful APIs**: The platform must support secure, RESTful APIs for interacting with HR systems. These APIs should include:
    - **Authentication and Authorization**: Implement OAuth 2.0 or similar secure token-based access for all API interactions.
    - **Data Transfer**: Enable bulk and real-time data transfer between ClearView and the HR systems. Data transfers should support formats such as JSON or XML.
    - **Error Handling**: Include comprehensive error reporting for failed API requests with retry mechanisms.
- **API Documentation**: Full API documentation must be available for both external HR systems and internal platform services, allowing future expansion and customization by developers.

### 4.4 Communication Interfaces

#### 4.4.1 Internal System Communication
- **Message Queues**: For communication between different system components (e.g., AI processing, reporting, and data aggregation), use a message queue system (e.g., RabbitMQ or AWS SQS) to ensure asynchronous and scalable processing.

#### 4.4.2 Data Transfer Protocols
- **HTTPS**: All data exchanged between clients (employers, job seekers, administrators) and the server must be encrypted using HTTPS.
- **SSL/TLS Encryption**: Secure all API and data transactions using SSL/TLS to ensure the confidentiality and integrity of transmitted information.

#### 4.4.3 Notification Services
- **Email Notifications**: ClearView should support email notifications for critical user events, such as job seeker registration, employer interest in candidates, and new job postings. These notifications must include links to relevant dashboard sections.
- **In-App Notifications**: In-app notifications should be available for both employers and job seekers to provide real-time updates on system activities like profile views, job match scores, or completed interview stages.
- **Webhooks**: The system should support webhooks for notifying external systems or integrations about changes (e.g., when a job seeker is hired or a candidate profile is unlocked).

## 4.5 Compliance and Data Privacy
ClearView must comply with relevant legal and regulatory standards for handling candidate and employer data:
- **GDPR**: If operating in the EU or handling EU citizen data, the platform must comply with the General Data Protection Regulation (GDPR), ensuring candidates can access, update, and request deletion of their data.
- **CCPA**: For candidates based in California, compliance with the California Consumer Privacy Act (CCPA) is mandatory, providing similar rights to data access and deletion.
- **EEOC Reporting**: In cases where demographic data is collected for reporting purposes, ClearView must anonymize this information in compliance with Equal Employment Opportunity Commission (EEOC) guidelines to avoid introducing bias into the hiring process.
- **Data Retention Policies**: ClearView must define data retention policies for job postings, candidate profiles, and survey results, specifying how long data will be stored and when it will be automatically purged.

## 5. Non-functional Requirements

### 5.1 Performance Requirements
The system must handle multiple simultaneous users without degradation in performance.

### 5.2 Safety Requirements
Data privacy regulations must be adhered to in the handling of candidate information.

### 5.3 Security Requirements
Ensure that all personal information is anonymized and securely stored.

### 5.4 Usability Requirements
The platform should have an intuitive user interface for easy navigation by all user classes.

## 6. Other Requirements
The platform should allow for future scalability and integration with additional HR systems as needed.

## 7. User Journeys
### Hiring Manager User Journey
- A Hiring Manager registers themselves on the site.
- They register the employer on the platform. An AI can assist them with completing the profile of the employer.
- They can manage job roles i.e. Create, edit, update and delete job roles.
- Review AI-generated anonymized profiles for candidates with their match scores for a given role.
- Unlock full candidate profiles by completing a payment.
- Select a candidate for follow up.
- Submit survey about a candidate and view survey results by candidates.
- View Job Role and Employer specific aggregate metrics.


### 7.2 Candidate User Journey
- A Candidate registers themselves on the site. 
- They manage their personal profile - demographic details/contact information and their resume. An AI assists with improving their resume. 
- The Candidate them marks themselves as active and an AI converts the profile and resume into an anonymized profile in SMART format. 
- View the roles that have expressed interest in them. 
- Follow up with hiring Manager for the role (outside of the ClearView app)
- Mark themselves as inactive if hired.
- Submit a survey about the role and interviewer.


### 7.3 Admin User Journey
1. An Admin belongs to the employer. 
2. Maintain internal reference and user data.
3. Generate reports and analytics.

#### 4.1.3 Administrator Interface
- **User Management**: Admins can:
    - Register new employers and manage job seeker accounts.
    - Monitor job postings and hiring workflows across the platform.
    - Mark candidates as hired and maintain internal references for all user data.
- **Reporting & Analytics**: Admins will have access to:
    - Generate and schedule out-of-the-box reports on KPIs such as job offer rates, diversity trends, and bias reduction metrics.
    - Customize reports by selecting specific timeframes, job roles, and other parameters.
    - Export aggregated reports in formats like CSV or PDF.
    - View high-level platform health indicators (e.g., number of active employers, candidates, and roles).

## 8. Technical Details
- The solution will use a trained LLM for anonymized candidate profile construction and resume tip generation.
- The solution will use a search engine to match candidates with job openings.
- The platform needs to interface with popular HR systems like SAP SuccessFactors, UKG Pro, Paycor, and Workday via APIs.