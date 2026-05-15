# Threat Actors

## Overview

Once the critical assets have been identified, the next step is to determine who might attempt to compromise them.

The AI Medical Assistant operates in a high-risk healthcare environment and processes sensitive Personal Health Information (PHI). As a result, the system may be targeted by a diverse range of adversaries, including opportunistic attackers, malicious insiders, sophisticated AI-focused adversaries and healthcare-targeting advanced persistent threat (APT) groups.

Understanding these threat actors is essential because their capabilities, motivations, and attack methods directly influence the types of risks that must be addressed.

---

## Purpose of the Threat Actor Analysis

The purpose of this section is to answer the following question:

> Who is most likely to attack the system and what are they trying to achieve?

By identifying likely adversaries, the analysis can determine:

- Which attack scenarios are realistic
- What capabilities attackers may possess
- Which assets are most likely to be targeted
- How threats should be prioritized

---

## Threat Actor Categories

The identified threat actors can be grouped into the following categories:

- External Adversaries
- Malicious Users
- Insider Threats
- Supply Chain Adversaries
- AI-Specific Adversaries
- Advanced Persistent Threat (APT) Groups

---

## Threat Actor Inventory

| Threat Actor | Description | Primary Motivations |
|------|------|------|
| Malicious Patient | An authenticated user who intentionally attempts to manipulate the system. | Bypass safeguards, extract sensitive data, or generate unsafe outputs. |
| External Attacker | An unauthenticated adversary operating over the internet. | Gain unauthorized access, steal data, or disrupt services. |
| Insider Threat | An employee or contractor who abuses legitimate access. | Data theft, misuse of privileges, or unauthorized disclosure. |
| Curious Employee | A staff member who accesses patient records without a legitimate need. | Privacy violations and unauthorized viewing of PHI. |
| Supply Chain Adversary | An attacker who compromises dependencies, libraries, or model artifacts. | Introduce malicious code or poisoned components. |
| Malicious Data Contributor | An actor who inserts false or harmful content into the knowledge base. | Influence retrieval results and model outputs. |
| Compromised LLM Provider | A third-party provider that is breached or behaves insecurely. | Exposure or retention of prompts and sensitive data. |
| Credential Thief | An attacker who steals passwords, session tokens, or API keys. | Account takeover and unauthorized service access. |
| Denial-of-Service Attacker | An adversary who floods the system with excessive requests. | Disrupt service availability. |
| Adversarial Prompt Engineer | A specialized attacker who crafts sophisticated prompt injection payloads. | Override instructions, exfiltrate data, and bypass guardrails. |
| Healthcare-Focused APT Group | A sophisticated nation-state or organized threat group targeting healthcare organizations. | Espionage, ransomware, and large-scale theft of patient data. |

---

## Highest-Risk Threat Actors

The following adversaries represent the most significant threats to this system:

- Malicious Patient
- External Attacker
- Insider Threat
- Supply Chain Adversary
- Adversarial Prompt Engineer
- Healthcare-Focused APT Group

These actors combine strong motivation with realistic opportunities to target high-value assets.

---

## AI-Specific Threat Actors

Several adversaries are particularly relevant to AI-enabled systems:

- Adversarial Prompt Engineer
- Malicious Data Contributor
- Supply Chain Adversary
- Compromised LLM Provider

These actors focus on manipulating prompts, poisoning data, and compromising model dependencies.

---

## Typical Attack Objectives

Threat actors may attempt to:

- Steal Personal Health Information (PHI)
- Manipulate prompts and system instructions
- Poison the Medical Knowledge Base
- Generate unsafe medical advice
- Compromise doctor and administrator accounts
- Abuse API keys and secrets
- Tamper with audit logs
- Deploy ransomware
- Disrupt service availability

---

## Most Attractive Targets

The assets most likely to be targeted include:

- Personal Health Information (PHI)
- Patient Database
- Medical Knowledge Base
- Prompts and model outputs
- API keys and secrets
- Audit logs

---

## Security Significance

Threat actor analysis helps ensure that the assessment is grounded in realistic adversarial behavior.

Rather than considering theoretical risks in isolation, this section connects each threat to specific attacker motivations and capabilities.

This improves the quality of:

- Abuse Cases
- STRIDE Threat Modeling
- Risk Assessment
- Mitigation Planning

---

## Key Security Questions

This section helps answer the following questions:

- Who is most likely to target the system?
- Which attackers are unique to AI-enabled applications?
- What are their motivations?
- Which assets are most attractive?
- Which threats are most realistic?

---

## Conclusion

The AI Medical Assistant faces threats from a broad range of adversaries, from malicious users and insiders to sophisticated healthcare-focused APT groups.

By understanding who may attack the system and why, the assessment establishes a realistic foundation for identifying abuse cases, modeling threats, and prioritizing security controls.
