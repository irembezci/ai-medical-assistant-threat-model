# Asset Inventory

## Overview

The first step in the analytical phase of the threat modeling process is identifying what must be protected.

In the AI Medical Assistant, a wide range of assets are involved in storing, processing, and transmitting sensitive information. These assets include Personal Health Information (PHI), authentication credentials, prompts, model outputs, API keys, and audit logs.

A clear understanding of these assets is essential because every subsequent stage of the assessment—including threat identification, risk analysis, and mitigation planning—depends on knowing which resources are most valuable and most sensitive.

---

## Purpose of the Asset Inventory

The purpose of this section is to answer the following question:

> What assets are critical to the secure and safe operation of the system?

By identifying and classifying these assets, the analysis can determine:

- What requires protection
- Why each asset is important
- Which security properties are most critical
- Which assets represent the highest-value targets

---

## Asset Classification

The identified assets can be grouped into several categories:

- Sensitive Data
- Authentication and Secrets
- AI-Specific Assets
- Data Stores
- Operational Assets
- Security Controls

---

## Asset Inventory Table

| Asset | Description | Security Importance |
|------|------|------|
| Personal Health Information (PHI) | Patient names, symptoms, medical history, and other sensitive health data. | Highly sensitive data requiring strict confidentiality and regulatory protection. |
| Patient Summaries | AI-generated summaries and preliminary medical guidance. | Must remain accurate and accessible only to authorized users. |
| User Credentials | Usernames, passwords, and related authentication data. | Required to prevent unauthorized access. |
| Authentication Tokens | Session identifiers, access tokens, and refresh tokens. | Protect authenticated sessions and authorization context. |
| Prompts | Final prompt payloads containing user input and retrieved context. | May include sensitive information and directly influence model behavior. |
| Retrieved Documents | Clinical references returned from the Medical Knowledge Base. | Must be trustworthy and protected from tampering. |
| LLM Responses | Model-generated medical guidance. | Must be safe, accurate, and free from unauthorized disclosures. |
| Medical Knowledge Base | Curated collection of trusted medical documents. | Integrity is essential to prevent misinformation and poisoning. |
| Patient Database | Structured storage for patient records and generated summaries. | Contains highly sensitive data requiring strong protection. |
| API Keys and Secrets | Credentials used to access external services. | Exposure may lead to unauthorized service use and data leakage. |
| Audit Logs | Records of security-relevant and operational events. | Required for accountability and incident investigation. |
| Configuration Files | Application settings and environment variables. | Misconfiguration may weaken security controls. |
| Output Guardrail Policies | Rules used to validate model responses. | Critical for preventing unsafe or sensitive outputs. |
| Rate Limiting Rules | Policies that restrict abusive requests. | Help preserve service availability. |
| Doctor Notes and Shared Reports | Summaries and records made available to doctors. | Require strong authorization and confidentiality controls. |
| Monitoring Data | Metrics, alerts, and telemetry. | Supports threat detection and operational visibility. |

---

## Most Critical Assets

The following assets represent the highest-value targets:

- Personal Health Information (PHI)
- Patient Database
- Medical Knowledge Base
- Prompts
- LLM Responses
- API Keys and Secrets
- Audit Logs

These assets are particularly attractive to attackers because they contain sensitive data, influence system behavior, or provide access to privileged services.

---

## Security Properties

Each asset must be protected according to one or more core security properties.

### Confidentiality

Prevent unauthorized disclosure of sensitive information such as PHI, prompts, and credentials.

### Integrity

Ensure that records, documents, prompts, and model outputs are accurate and untampered.

### Availability

Maintain reliable access to the application, knowledge base, and supporting services.

### Safety

Prevent the generation and delivery of harmful or misleading medical guidance.

### Auditability

Maintain trustworthy records of actions and security-relevant events.

---

## High-Value Attack Targets

From an adversary perspective, the most attractive assets include:

- PHI for theft and extortion
- API keys for unauthorized service access
- Prompts for instruction leakage
- Medical Knowledge Base for poisoning
- Audit logs for anti-forensics
- Authentication tokens for account takeover

---

## Relationship to Threat Modeling

The Asset Inventory provides the foundation for the remainder of the assessment.

It directly informs:

- Threat Actor Analysis
- Abuse Case Development
- STRIDE Threat Modeling
- Risk Assessment
- Security Control Design

Every identified threat ultimately targets one or more assets listed in this section.

---

## Conclusion

The AI Medical Assistant processes and stores a wide range of sensitive and business-critical assets.

By systematically identifying these assets and understanding their security importance, the assessment establishes a clear basis for evaluating threats, prioritizing risks, and designing effective mitigations.
