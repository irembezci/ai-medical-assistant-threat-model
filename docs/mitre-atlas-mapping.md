# MITRE ATLAS Mapping

## Overview

After mapping the identified threats to the OWASP Top 10 for LLM Applications, the next step is to align the findings with the MITRE ATLAS framework developed by :contentReference[oaicite:0]{index=0} and :contentReference[oaicite:1]{index=1}.

MITRE ATLAS is a knowledge base of tactics and techniques used by adversaries to attack artificial intelligence systems. It extends the logic of adversary emulation to machine learning and LLM-enabled applications.

By mapping threats to MITRE ATLAS, this assessment connects architectural risks to realistic attacker behavior.

---

## Purpose of the Mapping

The purpose of this section is to answer the following question:

> Which adversarial tactics and techniques are most relevant to the AI Medical Assistant?

This mapping helps:

- Align identified threats with a recognized AI attack framework
- Describe how adversaries may target the system
- Improve realism and technical depth
- Support mitigation planning

---

## MITRE ATLAS Mapping Table

| Threat Scenario | Relevant MITRE ATLAS Technique | Description |
|------|------|------|
| Prompt Injection | Prompt Injection | Malicious instructions manipulate model behavior. |
| Indirect Prompt Injection | Prompt Injection | Instructions embedded in retrieved documents influence the model. |
| Medical Knowledge Base Poisoning | Data Poisoning | Malicious content is inserted into the retrieval corpus. |
| Sensitive Data Exfiltration | Exfiltration via ML Inference API | Sensitive information is extracted through model interactions. |
| Unsafe Output Generation | LLM Prompt Crafting | Carefully designed prompts induce harmful responses. |
| Model Denial of Service | Denial of Service | Adversarial requests exhaust computational resources. |
| Credential Theft | Credential Access | Stolen credentials enable unauthorized access. |
| API Key Exposure | Credential Access | Secrets are used to abuse external services. |
| Audit Log Tampering | Defense Evasion | Attackers remove evidence of malicious activity. |
| Model Theft | Model Extraction | Adversaries attempt to replicate system behavior. |
| Supply Chain Compromise | Supply Chain Compromise | Dependencies or model artifacts are compromised. |
| Ransomware Deployment | Impact | Critical systems and data are disrupted. |

---

## Most Relevant MITRE ATLAS Techniques

The following techniques are especially significant for this project:

### Prompt Injection

The most important LLM-specific attack technique. Malicious instructions may override system prompts and lead to unauthorized behavior.

### Data Poisoning

Attackers may compromise the Medical Knowledge Base by inserting inaccurate or malicious content.

### Exfiltration via ML Inference API

Sensitive patient information may be extracted through repeated model interactions.

### Denial of Service

Adversarial prompts may consume excessive tokens and degrade service availability.

### Credential Access

Stolen credentials and API keys may provide unauthorized access to users and external services.

---

## Tactics Represented in the Assessment

The mapped techniques span several adversarial tactics, including:

- Initial Access
- Credential Access
- Defense Evasion
- Collection
- Exfiltration
- Impact

These tactics reflect the broad attack surface of AI-enabled healthcare systems.

---

## AI-Specific Attack Techniques

The following techniques are unique or particularly relevant to AI systems:

- Prompt Injection
- LLM Prompt Crafting
- Data Poisoning
- Model Extraction
- Exfiltration via ML Inference API

These techniques target model behavior, inference interfaces and supporting data pipelines.

---

## Security Significance

The MITRE ATLAS mapping demonstrates that the identified threats correspond to realistic adversarial methods rather than purely theoretical concerns.

This provides:

- A structured attacker-centric perspective
- Alignment with established AI security research
- Additional technical credibility
- Improved mitigation planning

---

## Relationship to Other Sections

This section builds on:

- Abuse Cases
- STRIDE Threat Model
- OWASP Top 10 for LLM Applications Mapping

It also informs:

- Risk Assessment
- Security Controls and Mitigations

---

## Key Security Questions

This section helps answer the following questions:

- How would attackers operationalize the identified threats?
- Which AI-specific techniques are most relevant?
- Which adversarial tactics are represented?
- How do these techniques map to real-world attack behavior?

---

## Conclusion

The MITRE ATLAS mapping confirms that the AI Medical Assistant is exposed to a broad set of adversarial techniques targeting both traditional infrastructure and AI-specific components.

The most significant techniques include Prompt Injection, Data Poisoning, Exfiltration via ML Inference API, Credential Access and Denial of Service.
