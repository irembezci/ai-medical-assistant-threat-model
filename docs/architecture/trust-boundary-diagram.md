# Trust Boundary Diagram

![Trust Boundary Diagram](../../diagrams/trust-boundary-diagram.png)

## Overview

The Trust Boundary Diagram identifies the major security zones within the AI Medical Assistant and highlights the points where trust levels change.

In any complex system, not all components operate under the same level of trust. Some elements are fully controlled by the organization, while others are external, user-controlled, or managed by third parties. Whenever data crosses from one trust zone to another, additional security controls are required.

This diagram is particularly important because many high-impact security incidents occur at these boundaries.

---

## Purpose of the Diagram

The primary purpose of this diagram is to answer the following question:

> Where does trust change within the system?

By identifying trust boundaries, the diagram helps reveal:

- Where untrusted input enters the application
- Where sensitive data leaves the internal environment
- Where stronger authentication and authorization controls are required
- Where additional monitoring is needed
- Which transitions present the highest risk

---

## Trust Zones

The architecture is divided into five major trust zones.

### 1. Public Internet

This zone contains entities outside the organization's control.

**Components:**
- Patient
- Doctor

Users in this zone are considered untrusted until they are successfully authenticated and authorized.

---

### 2. Internal Application Boundary

This zone contains application services operated by the organization.

**Components:**
- Patient Web Interface
- Doctor Dashboard
- Authentication Service
- API Gateway
- LLM Orchestrator
- Retrieval Engine
- Output Guardrails

This is the primary processing environment for application and AI workflows.

---

### 3. Third-Party Boundary

This zone contains services operated by external providers.

**Components:**
- External LLM Provider

This boundary introduces privacy, availability, and compliance risks because sensitive prompt data may be transmitted outside the organization.

---

### 4. Data Security Boundary

This zone contains sensitive storage systems.

**Components:**
- Patient Database
- Medical Knowledge Base

These systems store critical assets and require strong confidentiality and integrity protections.

---

### 5. Monitoring Boundary

This zone contains systems responsible for visibility and auditing.

**Components:**
- Logging and Monitoring

These systems support detection, investigation, and compliance.

---

## Critical Trust Transitions

Several trust transitions are particularly important.

### Public Internet → Internal Application Boundary

Patients and doctors submit requests and access sensitive information.

**Key Controls:**
- Authentication
- Authorization
- Input validation
- Rate limiting
- Session management

### Internal Application Boundary → Third-Party Boundary

Prompts and contextual data are sent to the External LLM Provider.

**Key Controls:**
- Data minimization
- TLS encryption
- Contractual privacy controls
- Provider due diligence

### Internal Application Boundary → Data Security Boundary

Services access patient records and medical documents.

**Key Controls:**
- Role-Based Access Control (RBAC)
- Encryption at rest
- Database auditing

### All Boundaries → Monitoring Boundary

Events are transmitted to logging and monitoring systems.

**Key Controls:**
- Log integrity
- Access controls
- Retention policies

---

## High-Risk Boundary Crossings

The following interactions represent the most sensitive trust transitions:

- Patient input entering the system
- PHI included in prompts sent to the External LLM Provider
- Retrieval of medical documents
- Storage of AI-generated summaries
- Doctor access to shared patient data

---

## Security Significance

Trust boundaries are among the most important concepts in threat modeling.

This diagram helps identify:

- Where attacker-controlled input is introduced
- Where sensitive data leaves organizational control
- Which interfaces require stronger defenses
- Where additional monitoring should be deployed

---

## Key Security Questions

This diagram helps answer the following questions:

- Which components are fully trusted?
- Which services are external?
- Where does PHI cross security boundaries?
- Where should stronger controls be implemented?
- Which transitions carry the highest risk?

---

## Relationship to Threat Modeling

The Trust Boundary Diagram is used directly in:

- STRIDE Threat Modeling
- OWASP Top 10 for LLM Applications Mapping
- Risk Assessment
- Security Control Design

Many threats are best understood by analyzing what happens when data crosses from one trust zone to another.

---

## Conclusion

The Trust Boundary Diagram highlights where trust changes throughout the AI Medical Assistant.

By identifying security zones and critical transitions, the diagram reveals the areas where the strongest controls are required and where the most significant risks are likely to emerge.
