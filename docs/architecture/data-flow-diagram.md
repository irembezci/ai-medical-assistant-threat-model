# Data Flow Diagram (DFD)

![Data Flow Diagram](../../diagrams/data-flow-diagram.png)

## Overview

After identifying the major components of the AI Medical Assistant, the next step is to understand how information moves between them.

The Data Flow Diagram (DFD) provides this perspective by tracing the path of data as it enters the system, is processed by internal services, is transmitted to external providers and is ultimately stored or presented to users.

While the System Architecture Diagram answers the question "What components make up the system?", the Data Flow Diagram answers a different and equally important question:

> How does sensitive information move throughout the system?

This distinction is critical for security analysis.

Many security risks are not tied to a specific component but to the way data moves between components. Sensitive information may be exposed during transmission, altered while being processed or stored without adequate protection.

Because this application processes Personal Health Information (PHI), prompts, retrieved medical references, model outputs and audit logs, understanding these flows is essential for identifying confidentiality, integrity and availability risks.

## Why This Diagram Matters

Threat modeling requires more than knowing what components exist.

Security teams must understand:

- Where untrusted data enters the system
- Which services process sensitive information
- Where data is transmitted externally
- Where data is stored
- Where security controls should be applied

The Data Flow Diagram provides this visibility.

It reveals the complete lifecycle of a patient request from the moment symptoms are submitted to the moment a validated response is delivered and recorded.

## Purpose of the Diagram

The primary purpose of this diagram is to identify how critical information moves through the application and where security controls are required.

By tracing data movement, the diagram helps identify:

- Entry points for untrusted input
- Internal processing steps
- External data transfers
- Storage locations for sensitive information
- Logging and monitoring points

This perspective is particularly important when evaluating:

- Data exposure risks
- Prompt injection opportunities
- Third-party privacy concerns
- Data integrity dependencies
- Audit and compliance requirements

## High-Level Request Flow

The following workflow describes how the system processes a typical patient request.

1. A patient signs in and submits symptoms and medical questions.
2. The Authentication Service verifies identity and issues an access token.
3. The API Gateway routes the request to internal services.
4. The LLM Orchestrator receives the patient input.
5. The Retrieval Engine searches the Medical Knowledge Base.
6. Relevant medical references are returned to the LLM Orchestrator.
7. A final prompt is constructed using patient symptoms, retrieved context and system instructions.
8. The prompt is sent to the External LLM Provider.
9. The model generates a response.
10. Output Guardrails validate the response.
11. The validated response is stored in the Patient Database.
12. The response is returned to the patient.
13. All relevant events are recorded by Logging and Monitoring.
14. The patient may optionally share the generated summary with an authorized doctor.

## Data Types Processed

The application processes several categories of sensitive and operational data.

### Patient Data

- Personal Health Information (PHI)
- Symptoms and medical questions
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

Understanding these categories helps determine which protections are required for each type of information.

## Critical Data Stores

The Data Flow Diagram highlights the locations where important information is stored.

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

These repositories represent high-value targets and require strong access controls and monitoring.

## Core Data Flows

The following table summarizes the most important flows in the system.

| Source | Destination | Data Transferred | Security Concern |
|------|------|------|------|
| Patient | Patient Web Interface | Symptoms and medical questions | Untrusted input |
| API Gateway | LLM Orchestrator | PHI and prompts | Sensitive processing |
| Retrieval Engine | Medical Knowledge Base | Search queries | Data integrity |
| LLM Orchestrator | External LLM Provider | Prompt and medical context | Third-party exposure |
| Output Guardrails | Patient Database | Validated response | Secure storage |
| Patient | Doctor Dashboard | Shared summaries | Authorization and consent |
| All Components | Logging and Monitoring | Audit events | Integrity and accountability |

This table highlights where confidentiality, integrity and privacy controls are most important.

## External Data Transfers

One of the most sensitive flows occurs when the LLM Orchestrator sends prompts to the External LLM Provider.

This transfer may include:

- Patient symptoms
- Retrieved medical references
- System instructions

Because this information leaves the organization's environment, this flow introduces significant privacy and compliance considerations.

Key concerns include:

- Exposure of PHI to third parties
- Provider-side data retention
- Jurisdiction and regulatory requirements
- Dependence on external availability

This is one of the most critical trust relationships in the system.

## High-Risk Data Flows

Although every flow is important, several are particularly sensitive.

### Patient Input to the LLM Orchestrator

Untrusted data enters the core AI workflow and may contain malicious instructions.

### Prompt Transfer to the External LLM Provider

Sensitive context leaves the organization.

### Retrieval from the Medical Knowledge Base

The integrity of retrieved references directly affects model outputs.

### Storage of AI-Generated Summaries

Generated responses may contain PHI and must be protected.

### Sharing Summaries with Doctors

Authorization and patient consent must be strictly enforced.

## Security Controls Informed by the DFD

The flows identified in this diagram inform several important security controls.

- TLS encryption for data in transit
- Encryption at rest
- Role-Based Access Control (RBAC)
- Prompt minimization
- Output filtering
- Audit logging
- Rate limiting
- Data retention policies
- Consent enforcement

Each control corresponds to a specific point where sensitive information is processed, transmitted or stored.

## Architectural Insights

By tracing the movement of data, several important insights emerge.

- PHI is processed across multiple components.
- Prompt data crosses organizational boundaries.
- The Medical Knowledge Base is a critical integrity dependency.
- Generated responses become part of the medical record.
- Logging is required throughout the workflow.

These observations directly influence later threat modeling and risk analysis.

## Security Questions Answered by This Diagram

This diagram helps answer the following questions:

- Where does sensitive medical data travel?
- Which components process PHI?
- Which information is sent to third-party services?
- Where are prompts and responses stored?
- Where should encryption be applied?
- Which flows present the highest privacy risk?

## Relationship to Threat Modeling

The Data Flow Diagram serves as a direct input to several subsequent analyses.

- Trust Boundary Analysis
- STRIDE Threat Modeling
- OWASP Top 10 for LLM Applications Mapping
- MITRE ATLAS Mapping
- Risk Assessment

Without a clear understanding of data movement, it would be difficult to accurately identify attack paths and prioritize security controls.

## Conclusion

The Data Flow Diagram provides a detailed view of how sensitive information moves through the AI Medical Assistant.

By tracing each step from symptom submission to response delivery, the diagram reveals where critical data is created, processed, transmitted, stored and shared.

This understanding is essential for identifying privacy risks, external exposure points and the security controls required to protect both patient data and patient safety.
