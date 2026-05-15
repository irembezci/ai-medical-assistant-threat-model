# AI Medical Assistant Threat Modeling Case Study

## Introduction

Large Language Models are increasingly being integrated into healthcare applications to provide symptom analysis, patient guidance, and clinical decision support. While these systems offer significant benefits, they also introduce new security and safety challenges. Sensitive medical information, third-party model providers, retrieval pipelines, and AI-specific attack techniques create a broad and complex attack surface.

In this project, I perform a comprehensive threat modeling and risk assessment of a fictional AI-powered Medical Assistant. The system allows patients to submit symptoms, retrieves trusted medical references using Retrieval-Augmented Generation (RAG), and generates preliminary medical guidance through a Large Language Model (LLM). Patients may also choose to share AI-generated summaries with authorized doctors.

Rather than building a working application, this repository models the system architecture, data flows, trust boundaries, and potential attack paths. The analysis applies STRIDE, OWASP Top 10 for LLM Applications, and MITRE ATLAS to identify and prioritize the most significant risks.

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

## Architecture and Design Artifacts

Understanding how the system works is the foundation of any effective threat model. To build a complete picture of the AI Medical Assistant, I created four complementary diagrams.

### System Architecture Diagram

![System Architecture Diagram](diagrams/system-architecture.png)

This diagram provides a high-level view of the system and identifies the core components involved in patient interactions, AI processing, data storage, and monitoring.

### Data Flow Diagram (DFD)

![Data Flow Diagram](diagrams/data-flow-diagram.png)

This diagram traces the movement of sensitive information throughout the system, from symptom submission to response generation and audit logging.

### Trust Boundary Diagram

![Trust Boundary Diagram](diagrams/trust-boundary-diagram.png)

This diagram highlights where trust levels change and where sensitive data crosses security boundaries, including interactions with the external LLM provider.

### Sequence Diagram

![Sequence Diagram](diagrams/symptom-analysis-sequence.png)

This diagram shows the chronological processing of a patient request, illustrating how authentication, retrieval, inference, validation, and logging occur over time.

---

## Asset Inventory

The first step in the analytical phase is identifying what must be protected. In this system, the most critical assets include Personal Health Information (PHI), prompts, model outputs, API keys, and audit logs.

<!-- Asset Inventory content -->

---

## Threat Actors

After identifying the assets, I defined the adversaries most likely to target the system, including malicious patients, external attackers, insider threats, supply chain adversaries, and healthcare-focused APT groups.

<!-- Threat Actors content -->

---

## Security Assumptions

Every threat model depends on a set of assumptions regarding authentication, authorization, encryption, logging, and third-party model usage.

<!-- Security Assumptions content -->

---

## Abuse Cases

With the system context established, I developed realistic misuse scenarios such as prompt injection, knowledge base poisoning, sensitive data exfiltration, and unsafe medical output generation.

<!-- Abuse Cases content -->

---

## STRIDE Threat Model

Using the STRIDE methodology, I analyzed each major component to identify threats affecting confidentiality, integrity, availability, accountability, and privilege boundaries.

<!-- STRIDE Threat Model content -->

---

## OWASP Top 10 for LLM Applications Mapping

The identified threats are mapped to OWASP categories to align the findings with current best practices in LLM security.

<!-- OWASP Mapping -->

---

## MITRE ATLAS Mapping

The threats are also mapped to MITRE ATLAS to contextualize them within adversarial tactics and techniques targeting AI systems.

<!-- MITRE ATLAS Mapping -->

---

## Risk Assessment

Each threat is evaluated based on likelihood and impact to prioritize remediation efforts.

<!-- Risk Assessment -->

---

## Security Controls and Mitigations

For every high-priority risk, I propose practical technical and procedural controls.

<!-- Mitigations -->

---

## Executive Summary

The final section summarizes the most critical findings and recommended security improvements.

<!-- Executive Summary -->

---

## References

This section includes the standards and frameworks used throughout the assessment.

<!-- References -->
