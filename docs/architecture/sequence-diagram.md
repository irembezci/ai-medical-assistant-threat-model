# Sequence Diagram

![Sequence Diagram](../../diagrams/symptom-analysis-sequence.png)

## Overview

The Sequence Diagram illustrates the dynamic behavior of the AI Medical Assistant by showing how a single patient request is processed over time.

Unlike the previous diagrams, which focus on structure, data movement, and trust boundaries, the Sequence Diagram captures the chronological order of interactions between components. This time-based view makes it easier to understand where authentication, retrieval, model inference, validation, persistence, and logging occur during a real user workflow.

---

## Purpose of the Diagram

The primary purpose of this diagram is to answer the following question:

> What happens step by step when a patient submits symptoms and receives AI-generated medical guidance?

By visualizing the exact execution order, the diagram helps identify:

- When security controls are applied
- Which components participate in the workflow
- Where sensitive data is processed
- Where failures may occur
- Which actions are recorded for auditing

---

## Scenario Description

The modeled scenario represents a typical interaction in which:

1. A patient signs into the application.
2. The patient submits symptoms and medical questions.
3. The system retrieves relevant medical references.
4. A Large Language Model generates preliminary medical guidance.
5. The response is validated by safety controls.
6. The response is stored and displayed.
7. The interaction is logged.
8. The patient may optionally share the generated summary with a doctor.

---

## Participating Components

The following components are involved in the sequence:

- Patient
- Patient Web Interface
- Authentication Service
- API Gateway
- LLM Orchestrator
- Retrieval Engine
- Medical Knowledge Base
- External LLM Provider
- Output Guardrails
- Patient Database
- Logging and Monitoring
- Doctor Dashboard (optional)

---

## Step-by-Step Workflow

### 1. Authentication

The patient submits credentials through the Patient Web Interface. The Authentication Service verifies identity and returns a valid session.

### 2. Symptom Submission

The patient submits symptoms and medical questions. The request is forwarded through the API Gateway to the LLM Orchestrator.

### 3. Document Retrieval

The LLM Orchestrator requests relevant clinical references from the Retrieval Engine, which queries the Medical Knowledge Base.

### 4. Prompt Construction

The LLM Orchestrator combines:

- Patient symptoms
- Retrieved documents
- System instructions
- Safety constraints

to construct the final prompt.

### 5. Model Inference

The prompt is sent to the External LLM Provider, which generates a response.

### 6. Output Validation

The response is passed to Output Guardrails, where privacy and safety checks are performed.

### 7. Data Persistence

The validated response and associated metadata are stored in the Patient Database.

### 8. Audit Logging

Security and operational events are sent to Logging and Monitoring.

### 9. Response Delivery

The validated medical guidance is displayed to the patient.

### 10. Optional Doctor Sharing

If the patient grants consent, the summary becomes available to authorized doctors through the Doctor Dashboard.

---

## Security Significance

The Sequence Diagram is valuable because it shows the precise order in which security controls are applied.

This includes:

- Authentication before access
- Retrieval before prompt construction
- Guardrails before response delivery
- Logging after critical events
- Consent before doctor sharing

This sequencing helps verify that controls are applied at the appropriate stages.

---

## Potential Failure Points

The workflow also reveals several points where security issues may arise:

- Authentication bypass
- Retrieval of poisoned documents
- Prompt injection during prompt construction
- Data exposure to the External LLM Provider
- Guardrail bypass
- Unauthorized database access
- Incomplete audit logging
- Improper sharing with doctors

---

## Key Security Questions

This diagram helps answer the following questions:

- At what point is the user authenticated?
- When is sensitive data sent externally?
- Where are safety controls applied?
- When is information persisted?
- How is doctor access authorized?

---

## Relationship to Threat Modeling

The Sequence Diagram supports:

- Abuse Case Development
- STRIDE Analysis
- Risk Assessment
- Security Control Validation

It provides the dynamic context needed to understand how threats unfold during actual execution.

---

## Conclusion

The Sequence Diagram offers a detailed, time-based view of how the AI Medical Assistant processes a patient request.

By modeling the exact sequence of events, the diagram clarifies where critical decisions are made, where sensitive data is handled, and where security controls must operate to protect both privacy and patient safety.
