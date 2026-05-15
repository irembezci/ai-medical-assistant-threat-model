# AI Medical Assistant Threat Modeling Case Study

## Introduction

Large Language Models are increasingly being integrated into healthcare applications to provide symptom analysis, patient guidance, and clinical decision support. While these systems offer significant benefits, they also introduce new security and safety challenges. Sensitive medical information, third-party model providers, retrieval pipelines and AI-specific attack techniques create a broad and complex attack surface.

In this project, I perform a comprehensive threat modeling and risk assessment of a fictional AI-powered Medical Assistant. The system allows patients to submit symptoms, retrieves trusted medical references using Retrieval-Augmented Generation (RAG) and generates preliminary medical guidance through a Large Language Model (LLM). Patients may also choose to share AI-generated summaries with authorized doctors.

Rather than building a working application, this repository models the system architecture, data flows, trust boundaries and potential attack paths. The analysis applies STRIDE, OWASP Top 10 for LLM Applications and MITRE ATLAS to identify and prioritize the most significant risks.

The goal of this project is to answer a simple but critical question:

> How can we systematically assess and secure a high-risk AI healthcare application before it is deployed?

---

## Methodology

The assessment follows a structured methodology.

First, the system is modeled from multiple perspectives using architecture and design diagrams. Once the system boundaries and workflows are clearly defined, critical assets are identified and potential threat actors are analyzed.

Next, realistic abuse cases are developed to describe how the application may be intentionally misused. These abuse cases form the basis for a STRIDE-based threat model.

The resulting threats are then mapped to the OWASP Top 10 for LLM Applications and MITRE ATLAS to align the findings with recognized AI security frameworks.

Finally, each threat is assessed using likelihood and impact, and practical mitigation strategies are proposed.

---

## Project Deliverables

This repository includes the following deliverables:

### Architecture and Design Artifacts

- System Architecture Diagram
- Data Flow Diagram (DFD)
- Trust Boundary Diagram
- Sequence Diagram

### Threat Modeling Documentation

- Asset Inventory
- Threat Actors
- Security Assumptions
- Abuse Cases
- STRIDE Threat Model

### Planned Deliverables

- OWASP Top 10 for LLM Applications Mapping
- MITRE ATLAS Mapping
- Risk Assessment
- Security Controls and Mitigations
- Executive Summary
- References

---

## Analysis Narrative

The assessment begins by modeling the fictional AI Medical Assistant and defining its architecture, workflows, and trust boundaries.

Once the system design is established, the analysis identifies the critical assets that require protection, including Personal Health Information (PHI), prompts, model outputs, API keys, and audit logs. Potential threat actors are then defined, ranging from malicious patients and external attackers to healthcare-focused APT groups and supply chain adversaries.

The security context is further refined through a set of assumptions regarding authentication, authorization, encryption, logging, and third-party model usage.

Based on this foundation, realistic abuse cases are developed to illustrate how the system may be intentionally misused, including prompt injection, knowledge base poisoning, sensitive data exfiltration, and unsafe output generation.

The core threat modeling phase applies the STRIDE methodology to each major component of the system in order to systematically identify threats affecting confidentiality, integrity, availability, accountability, and privilege boundaries.

The identified threats are then mapped to the OWASP Top 10 for LLM Applications and MITRE ATLAS to align the findings with recognized industry frameworks for AI and LLM security.

Next, each threat is evaluated using a qualitative risk assessment based on likelihood and impact.

For every high-priority finding, practical security controls and mitigation strategies are proposed to strengthen the overall security posture of the system.

Finally, the project concludes with an executive summary that highlights the most critical risks and recommended actions.

---

## Architecture and Design Artifacts

Understanding how the system works is the foundation of any effective threat model. To build a complete picture of the AI Medical Assistant, I created four complementary diagrams. Each diagram answers a different question and serves as a foundation for the subsequent security analysis.

### [System Architecture Diagram](docs/architecture/system-architecture.md)

![System Architecture Diagram](diagrams/system-architecture.png)

This diagram provides a high-level view of the system and identifies the core components involved in patient interactions, AI processing, data storage, and monitoring.

### [Data Flow Diagram (DFD)](docs/architecture/data-flow-diagram.md)

![Data Flow Diagram](diagrams/data-flow-diagram.png)

This diagram traces the movement of sensitive information throughout the system, from symptom submission to response generation and audit logging.

### [Trust Boundary Diagram](docs/architecture/trust-boundary-diagram.md)

![Trust Boundary Diagram](diagrams/trust-boundary-diagram.png)

This diagram highlights where trust levels change and where sensitive data crosses security boundaries, including interactions with the external LLM provider.

### [Sequence Diagram](docs/architecture/sequence-diagram.md)

![Sequence Diagram](diagrams/symptom-analysis-sequence.png)

This diagram shows the chronological processing of a patient request, illustrating how authentication, retrieval, inference, validation, and logging occur over time.

---

## [Asset Inventory](docs/asset-inventory.md)

The first step in the analytical phase is identifying what must be protected. This section defines the most critical assets, including Personal Health Information (PHI), prompts, model outputs, API keys, and audit logs.

---

## [Threat Actors](docs/threat-actors.md)

This section identifies the adversaries most likely to target the system, including malicious patients, external attackers, insider threats, supply chain adversaries, and healthcare-focused APT groups.

---

## [Security Assumptions](docs/security-assumptions.md)

Every threat model depends on a set of assumptions regarding authentication, authorization, encryption, logging, and third-party model usage.

---

## [Abuse Cases](docs/abuse-cases.md)

This section describes realistic misuse scenarios such as prompt injection, knowledge base poisoning, sensitive data exfiltration, and unsafe medical output generation.

---

## [STRIDE Threat Model](docs/stride-threat-model.md)

Using the STRIDE methodology, this section analyzes each major component to identify threats affecting confidentiality, integrity, availability, accountability, and privilege boundaries.

---

## [OWASP Top 10 for LLM Applications Mapping](docs/owasp-llm-mapping.md)

The identified threats are mapped to OWASP categories to align the findings with current best practices in LLM security.

---

## [MITRE ATLAS Mapping](docs/mitre-atlas-mapping.md)

The threats are mapped to MITRE ATLAS tactics and techniques to contextualize them within adversarial behavior targeting AI systems.

---

## [Risk Assessment](docs/risk-assessment.md)

Each threat is evaluated based on likelihood and impact in order to prioritize remediation efforts.

---

## [Security Controls and Mitigations](docs/mitigations.md)

This section proposes practical technical and procedural controls to reduce the identified risks.

---

## [Executive Summary](docs/executive-summary.md)

The final section summarizes the most critical findings and recommended security improvements.

---

## [References](docs/references.md)

This section includes the standards, frameworks, and supporting resources used throughout the assessment.
