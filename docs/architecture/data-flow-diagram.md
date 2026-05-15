# Data Flow Diagram (DFD)

![Data Flow Diagram](../../diagrams/data-flow-diagram.png)

## Overview

The Data Flow Diagram (DFD) illustrates how information moves through the AI Medical Assistant during a typical patient interaction.

While the System Architecture Diagram focuses on structural components, the Data Flow Diagram emphasizes the movement of data between those components. This perspective is essential for understanding where sensitive information is created, transmitted, processed, and stored.

Because the system handles Personal Health Information (PHI), prompts, model outputs, and audit logs, tracing these flows is a critical step in identifying security risks and determining where controls must be applied.

---

## Purpose of the Diagram

The primary purpose of this diagram is to answer the following question:

> How does sensitive information move throughout the system?

By visualizing the complete lifecycle of a patient request, the diagram helps identify:

- Entry points for untrusted input
- Internal data processing steps
- External data transfers
- Storage locations for sensitive information
- Logging and monitoring points

---

## Main Data Flow

A typical patient interaction follows this sequence:

1. A patient signs in and submits symptoms and medical questions.
2. The request is authenticated and routed through the API Gateway.
3. The LLM Orchestrator receives the request.
4. Relevant documents are retrieved from the Medical Knowledge Base.
5. A final prompt is constructed using patient input and retrieved references.
6. The prompt is sent to the External LLM Provider.
7. The model returns a generated response.
8. Output Guardrails validate the response.
9. The response is stored in the Patient Database.
10. The response is presented to the patient.
11. All relevant events are recorded by Logging and Monitoring.
12. The patient may optionally share the generated summary with a doctor.

---

## Data Types Processed

The system processes several categories of data.

### Patient Data

- Personal Health Information (PHI)
- Symptoms
- Medical history
- Consent preferences

### AI Data

- System prompts
- User prompts
- Retrieved context
- Model responses

### Security Data

- Credentials
- Session tokens
- API keys
- Audit logs

### Operational Data

- Metrics
- Error logs
- Monitoring events

---

## Critical Data Stores

### Patient Database

Stores:

- Patient profiles
- Symptom submissions
- AI-generated summaries
- Sharing preferences

### Medical Knowledge Base

Stores:

- Clinical guidelines
- Trusted medical references
- Curated documents

### Logging and Monitoring

Stores:

- Authentication events
- API requests
- Security alerts
- Audit trails

---

## External Data Transfers

One of the most significant data flows occurs when prompts are sent to the External LLM Provider.

This transfer may include:

- Patient symptoms
- Retrieved medical context
- System instructions

This flow is particularly sensitive because data leaves the organization's security boundary.

---

## Security Significance

The Data Flow Diagram is essential for identifying where security controls are needed.

It highlights:

- Where untrusted data enters the system
- Where PHI is transmitted
- Where prompts are constructed
- Where data is stored
- Where information leaves the environment
- Where events are logged

---

## Key Security Questions

This diagram helps answer the following questions:

- Where does sensitive medical data travel?
- Which components process PHI?
- Which data is sent to third-party services?
- Where are prompts and responses stored?
- Where should encryption and access controls be applied?

---

## Security Controls Informed by the DFD

The data flows identified in this diagram inform several important controls:

- TLS encryption for data in transit
- Encryption at rest
- Access control enforcement
- Prompt minimization
- Output filtering
- Audit logging
- Rate limiting
- Data retention policies

---

## Example High-Risk Flows

The following flows are considered particularly sensitive:

- Patient input to the LLM Orchestrator
- Prompt transfer to the External LLM Provider
- Retrieval of documents from the Medical Knowledge Base
- Storage of AI-generated summaries
- Sharing summaries with doctors

---

## Relationship to Threat Modeling

The Data Flow Diagram serves as a direct input to:

- Trust Boundary Analysis
- STRIDE Threat Modeling
- OWASP LLM Top 10 Mapping
- MITRE ATLAS Mapping
- Risk Assessment

Without a clear understanding of data movement, it is difficult to accurately identify confidentiality, integrity, and availability risks.

---

## Conclusion

The Data Flow Diagram provides a detailed view of how sensitive information moves through the AI Medical Assistant.

By tracing each step from symptom submission to response delivery, the diagram reveals where critical data is processed, where external transfers occur, and where security controls must be applied.
