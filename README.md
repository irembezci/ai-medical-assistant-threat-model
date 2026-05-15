# AI Medical Assistant Threat Modeling Case Study

## Introduction

Artificial Intelligence is rapidly transforming healthcare. Applications powered by Large Language Models (LLMs) can analyze patient symptoms, retrieve trusted medical references and generate preliminary guidance in seconds.

These capabilities create significant opportunities, but they also introduce serious security and safety risks.

If an AI healthcare application is not properly secured, attackers may be able to steal sensitive patient records, manipulate model behavior, poison trusted medical knowledge sources or generate harmful medical advice.

Because healthcare systems process highly sensitive Personal Health Information (PHI), security failures can affect both patient privacy and patient safety.

This project demonstrates how to perform a complete threat modeling and risk assessment of an AI-powered healthcare application before it is deployed.

The fictional application analyzed in this repository is an AI Medical Assistant that allows patients to:

1. Submit symptoms and medical questions
2. Retrieve trusted medical references using Retrieval-Augmented Generation (RAG)
3. Receive AI-generated medical guidance
4. Share summaries with authorized doctors

Rather than building a functional application, this project focuses on the security assessment process itself.

The objective is to answer a critical question:

> How can we systematically identify and mitigate the security risks of a high-risk AI healthcare application before deployment?

## Methodology

This project follows a structured methodology commonly used in professional threat modeling engagements.

The assessment begins by modeling the system architecture, data flows, trust boundaries and operational workflows.

Next, the analysis identifies the critical assets that must be protected, the threat actors most likely to target the system and the assumptions that define the security baseline.

Realistic abuse cases are then developed to illustrate how the application could be intentionally misused.

The STRIDE methodology is applied to systematically identify threats affecting each component.

These findings are mapped to the OWASP Top 10 for LLM Applications and MITRE ATLAS to align the analysis with recognized AI security frameworks.

Finally, each threat is evaluated based on likelihood and impact and practical mitigation strategies are proposed.

## Project Deliverables

This repository contains a complete threat modeling and risk assessment package.

### Architecture and Design Artifacts

- [System Architecture Diagram](docs/architecture/system-architecture.md)
- [Data Flow Diagram (DFD)](docs/architecture/data-flow-diagram.md)
- [Trust Boundary Diagram](docs/architecture/trust-boundary-diagram.md)
- [Sequence Diagram](docs/architecture/sequence-diagram.md)

### Threat Modeling Documentation

- [Asset Inventory](docs/asset-inventory.md)
- [Threat Actors](docs/threat-actors.md)
- [Security Assumptions](docs/security-assumptions.md)
- [Abuse Cases](docs/abuse-cases.md)
- [STRIDE Threat Model](docs/stride-threat-model.md)

### Security Framework Mappings

- [OWASP Top 10 for LLM Applications Mapping](docs/owasp-llm-mapping.md)
- [MITRE ATLAS Mapping](docs/mitre-atlas-mapping.md)

### Risk Analysis and Recommendations

- [Risk Assessment](docs/risk-assessment.md)
- [Security Controls and Mitigations](docs/mitigations.md)
- [Executive Summary](docs/executive-summary.md)
- [References](docs/references.md)

## Analysis Narrative

This project follows the same logical process that security architects use when evaluating real-world systems.

The assessment begins by understanding how the AI Medical Assistant works. Architecture and design diagrams are used to visualize the system, the movement of sensitive data, the boundaries where trust changes and the sequence of events that occurs when a patient interacts with the application.

Once the system is clearly understood, the analysis identifies the assets that must be protected, the adversaries most likely to target those assets and the assumptions that define the security baseline.

Realistic abuse cases are then developed to illustrate how the application could be intentionally misused.

The STRIDE methodology is applied to systematically identify threats affecting each component.

The resulting findings are mapped to the OWASP Top 10 for LLM Applications and MITRE ATLAS to align the assessment with widely recognized AI security frameworks.

Each threat is then evaluated using a qualitative risk assessment based on likelihood and impact.

Finally, practical technical and procedural controls are proposed to reduce the most critical risks.

## Architecture and Design Artifacts

Understanding how the system works is the foundation of effective threat modeling. To build a complete picture of the AI Medical Assistant, four complementary diagrams were created.

Each diagram focuses on a different aspect of the system.

- The System Architecture Diagram shows the major components and how they are connected.
- The Data Flow Diagram shows how sensitive information moves through the application.
- The Trust Boundary Diagram highlights where trust changes and where additional security controls are required.
- The Sequence Diagram illustrates what happens step by step when a patient submits symptoms and receives AI-generated guidance.

Together, these diagrams provide the architectural foundation for all subsequent analysis.

### [System Architecture Diagram](docs/architecture/system-architecture.md)

![System Architecture Diagram](diagrams/system-architecture.png)

This diagram presents a high-level view of the AI Medical Assistant and identifies the core components involved in user interaction, authentication, AI processing, data storage and monitoring.

### [Data Flow Diagram (DFD)](docs/architecture/data-flow-diagram.md)

![Data Flow Diagram](diagrams/data-flow-diagram.png)

This diagram traces how Personal Health Information (PHI), prompts, retrieved documents and model outputs move throughout the system.

### [Trust Boundary Diagram](docs/architecture/trust-boundary-diagram.md)

![Trust Boundary Diagram](diagrams/trust-boundary-diagram.png)

This diagram highlights where trust levels change, such as when sensitive prompts are sent to the external LLM provider or when users access protected resources.

### [Sequence Diagram](docs/architecture/sequence-diagram.md)

![Sequence Diagram](diagrams/symptom-analysis-sequence.png)

This diagram illustrates the chronological workflow of a patient request, from authentication and document retrieval to model inference, validation, storage and optional sharing with doctors.

## [Asset Inventory](docs/asset-inventory.md)

Before analyzing threats, it is essential to understand what needs to be protected.

This section identifies the most valuable assets in the AI Medical Assistant, including Personal Health Information (PHI), prompts, model outputs, API keys, authentication tokens and audit logs.

Each asset is classified according to its security importance and the properties that must be preserved, such as confidentiality, integrity, availability and safety.

## [Threat Actors](docs/threat-actors.md)

Once the critical assets are identified, the next step is to determine who might attempt to compromise them.

This section defines the adversaries most likely to target the system, including malicious patients, external attackers, insider threats, supply chain adversaries and healthcare-focused advanced persistent threat (APT) groups.

For each actor, the analysis explains typical motivations, capabilities and likely attack objectives.

## [Security Assumptions](docs/security-assumptions.md)

Every threat model depends on a set of baseline assumptions.

This section documents the conditions assumed to be true during the assessment, such as the use of encryption, authentication, authorization, audit logging and secure secrets management.

If any of these assumptions are incorrect, the actual risk level may be significantly higher.

## [Abuse Cases](docs/abuse-cases.md)

Abuse cases describe how the application could be intentionally misused.

Rather than focusing on normal user behavior, this section models realistic attack scenarios such as prompt injection, knowledge base poisoning, credential theft and unsafe output generation.

These scenarios provide concrete examples of how threats may materialize in practice.

## [STRIDE Threat Model](docs/stride-threat-model.md)

This section applies the STRIDE methodology to each major component of the system.

For every component, threats are categorized as Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service or Elevation of Privilege.

This structured approach ensures that both traditional web security risks and AI-specific threats are systematically identified.

## [OWASP Top 10 for LLM Applications Mapping](docs/owasp-llm-mapping.md)

After identifying threats, this section maps them to the OWASP Top 10 for LLM Applications.

This framework highlights the most important risks affecting systems built with Large Language Models, including Prompt Injection, Sensitive Information Disclosure and Overreliance.

Mapping findings to OWASP demonstrates that the assessment aligns with current industry best practices.

## [MITRE ATLAS Mapping](docs/mitre-atlas-mapping.md)

This section maps the identified threats to MITRE ATLAS, a framework that catalogs adversarial tactics and techniques targeting AI systems.

It connects architectural findings to realistic attacker behaviors such as Prompt Injection, Data Poisoning and Exfiltration via ML Inference API.

## [Risk Assessment](docs/risk-assessment.md)

After identifying and categorizing threats, the next step is to determine which risks deserve immediate attention.

This section evaluates each threat using two factors:

- Likelihood
- Impact

The combination of these factors produces an overall risk rating such as Low, Medium, High or Critical.

Threats such as Prompt Injection, Sensitive Data Disclosure, Medical Knowledge Base Poisoning and Unsafe Output Generation are identified as the highest-priority risks because they could directly affect patient privacy and patient safety.

## [Security Controls and Mitigations](docs/mitigations.md)

This section proposes practical recommendations to reduce the identified risks.

The mitigations include both technical controls and operational measures, such as prompt isolation, encryption, rate limiting, human review and incident response procedures.

Each recommendation is directly linked to one or more high-priority threats.

## [Executive Summary](docs/executive-summary.md)

The Executive Summary provides a concise overview of the entire assessment.

It highlights the most important risks, explains their business and security implications and summarizes the highest-priority recommendations.

This section is intended for managers, executives and decision-makers who need a high-level understanding of the findings.

## [References](docs/references.md)

This section lists the standards, frameworks and authoritative resources used throughout the project.

Examples include the OWASP Top 10 for LLM Applications, MITRE ATLAS, Microsoft STRIDE and the NIST AI Risk Management Framework.

These references provide the theoretical foundation for the assessment and allow readers to explore each methodology in greater depth.
