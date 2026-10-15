# 🏥 CogniCare
### Cognitive Optimization & Guidance for Next-Gen Intelligent Care

> **Where Intelligence Meets Care.**  
> Turning fragmented healthcare information into clearer, evidence-backed decisions.

CogniCare is an AI-powered healthcare decision-support concept designed to help patients and caregivers understand insurance coverage, compare hospital options, estimate potential out-of-pocket costs, and navigate a care journey with more confidence.

Healthcare information is often spread across policy documents, hospital listings, treatment estimates, and disconnected systems. CogniCare aims to bring these pieces together into one decision-support experience, with recommendations that explain their reasoning rather than presenting a score without context.

> **Project note:** This README describes the project's intended capabilities and proposed architecture. Availability of individual features depends on the current implementation; CogniCare is not a substitute for medical advice, insurer confirmation, or emergency care.

---

## 📌 Table of Contents

- [The Problem](#-the-problem)
- [Our Approach](#-our-approach)
- [Core Capabilities](#-core-capabilities)
- [How It Works](#-how-it-works)
- [System Architecture](#️-system-architecture)
- [Technology Stack](#️-technology-stack)
- [Proposed Project Structure](#-proposed-project-structure)
- [Privacy and Responsible Use](#-privacy-and-responsible-use)
- [Roadmap](#-roadmap)
- [Team](#-team)
- [License](#-license)

## 🚨 The Problem

Patients and caregivers may need to make important healthcare decisions while dealing with uncertainty, time pressure, and complex paperwork. Common challenges include:

- Interpreting insurance coverage, exclusions, co-payments, and deductibles
- Identifying hospitals that match a policy's network and eligibility rules
- Comparing estimated treatment costs and possible out-of-pocket expenses
- Understanding how a room category or treatment choice may affect coverage
- Keeping track of admission, treatment, and discharge-related information
- Finding the evidence behind a recommendation instead of relying on a black-box score

When this information is scattered across documents and portals, comparing options can become slow, stressful, and expensive.

## 💡 Our Approach

CogniCare is designed as a healthcare decision-intelligence layer connecting insurance policy information, hospital details, treatment options, and estimated costs.

The goal is to help users:

- **Understand** relevant policy clauses in accessible language
- **Compare** hospital options against available policy and care information
- **Estimate** potential costs and coverage gaps
- **See why** a recommendation was made, including supporting evidence
- **Track** key stages in a care journey and identify issues that may need attention

CogniCare supports informed decisions; final coverage, costs, and clinical decisions must be confirmed with the relevant insurer, hospital, and qualified healthcare professionals.

## ✨ Core Capabilities

### 📄 Policy Document Intelligence
Designed to extract and organize useful details from insurance documents, such as:

- Coverage rules and exclusions
- Room-rent eligibility
- Co-payment and deductible details
- Network-hospital information
- Conditions that may affect a claim

**Proposed approach:** OCR, language models, and retrieval-augmented generation (RAG), with source references wherever possible.

### 🏥 Hospital Compatibility
A proposed scoring and comparison layer can evaluate hospitals using available information such as:

- Policy/network compatibility
- Coverage eligibility
- Specialty availability
- Location
- Estimated treatment cost

Scores should be treated as decision-support signals, not guarantees of admission, treatment suitability, or claim approval.

### 📊 Explainable Recommendations
Recommendations are intended to show:

- Why an option was selected
- Which policy details informed the result
- Relevant cost considerations
- Uncertainties or information that still needs confirmation

### 🚨 Policy-Aware Alerts
The system aims to flag potential issues for review, including:

- Possible room-category mismatches
- Coverage conflicts
- Exclusions or eligibility concerns
- Information gaps that could affect a claim

Alerts are prompts to verify details—not definitive insurer decisions.

### 💰 Cost Estimation
A planned cost breakdown can help users reason about:

- Estimated out-of-pocket expenses
- Co-payments and deductibles
- Potential coverage gaps
- Differences between alternative care options

Actual bills and insurer payments may differ from estimates.

### 🩺 Care Journey Tracking
A proposed journey view follows major stages:

**Emergency → Admission → Treatment → Recovery → Discharge**

It can organize relevant updates and help caregivers identify questions that need follow-up.

### 🔍 What-If Comparison
Compare alternative hospital or care pathways using available cost and compatibility information. Any sample values should be treated as illustrative, not real patient estimates.

### 🤖 Caregiver Copilot
A policy-grounded assistant is envisioned to answer questions such as:

- What policy details are relevant to this admission?
- Is this room category potentially covered?
- Why did an option receive its score?
- What information should be confirmed before proceeding?

Responses should link back to source material and clearly communicate uncertainty.

## 🔄 How It Works

1. **Provide policy information** — upload or supply an insurance document, where supported.
2. **Extract relevant details** — identify coverage terms, limits, exclusions, and conditions.
3. **Structure the information** — organize extracted details for retrieval and comparison.
4. **Evaluate available options** — compare hospital and treatment information against policy rules.
5. **Explain the results** — present rankings, cost considerations, and supporting evidence.
6. **Surface potential risks** — flag details that may need confirmation.
7. **Compare alternatives** — explore possible differences between available pathways.
8. **Support the care journey** — organize updates and questions for patients and caregivers.

## 🏗️ System Architecture

The following is the **proposed logical architecture**, not a claim that every component is already implemented.

```text
Insurance Policy Documents
          |
          v
     OCR / Parsing
          |
          v
   Policy Information
      Extraction
          |
          v
 Structured Policy Store <----> RAG / Retrieval Layer
          |                              |
          +--------------+---------------+
                         |
             Policy Rules & Cost Logic
                         |
       +-----------------+-----------------+
       |                 |                 |
       v                 v                 v
 Hospital Data      Cost Estimates    Eligibility Checks
       |                 |                 |
       +-----------------+-----------------+
                         |
                         v
             Compatibility & Ranking
                         |
                         v
             Explainable Recommendations
                         |
              +----------+----------+
              |                     |
              v                     v
         Alerts / Risks       What-If Comparison
              |                     |
              +----------+----------+
                         |
                         v
                Caregiver Copilot
```

## 🛠️ Technology Stack

The project README currently outlines the following intended stack. Please refer to the source code and dependency files for the technologies actually configured in the repository.

| Layer | Technologies |
|---|---|
| Frontend | React, TypeScript, Tailwind CSS |
| Visualization and maps | Recharts, Leaflet |
| Backend API | FastAPI, Pydantic |
| Data access | SQLAlchemy |
| AI and retrieval | LLMs, embedding models, RAG pipeline |
| Data storage | PostgreSQL, vector database |
| Deployment | Docker, Render, AWS |

## 📂 Proposed Project Structure

The following illustrates the intended organization; actual folders may differ as implementation evolves.

```text
CogniCare/
├── frontend/
│   └── src/
│       ├── components/
│       ├── pages/
│       └── services/
├── backend/
│   └── app/
│       ├── api/
│       ├── services/
│       ├── models/
│       ├── database/
│       └── rag/
├── docs/
├── scripts/
├── docker-compose.yml
├── requirements.txt
└── README.md
```

## 🔐 Privacy and Responsible Use

Healthcare and insurance information can be sensitive. A responsible implementation should prioritize:

- Collecting only the information needed for the task
- Protecting stored documents and data in transit
- Restricting access based on user roles
- Avoiding exposure of personal or policy information in logs
- Making AI-generated summaries traceable to source documents
- Communicating uncertainty and asking users to verify critical details

Security controls and regulatory compliance must be verified against the actual implementation; design intentions alone do not establish compliance. Do not upload real patient or policy data to an untrusted environment.

## 🗺️ Roadmap

Potential next steps include:

- [ ] Improve policy extraction and source citations
- [ ] Add or validate hospital and insurer data integrations
- [ ] Refine cost estimates and clearly show assumptions
- [ ] Build policy-aware alerts and care journey tracking
- [ ] Add side-by-side what-if comparisons
- [ ] Develop a caregiver assistant grounded in retrieved evidence
- [ ] Explore multilingual and voice-enabled interactions
- [ ] Evaluate privacy, security, and recommendation quality

