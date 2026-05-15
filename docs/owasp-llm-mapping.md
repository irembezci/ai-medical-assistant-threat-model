# OWASP Top 10 for LLM Applications Mapping

## Overview

After identifying threats using the STRIDE methodology, the next step is to map those findings to the [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/), published by the [OWASP Foundation](https://owasp.org/).

This framework provides a structured view of the most significant risks affecting applications that use Large Language Models (LLMs). By aligning the identified threats with these categories, the assessment demonstrates that the AI Medical Assistant is evaluated against current industry best practices in AI and LLM security.

---

## Purpose of the Mapping

The purpose of this section is to answer the following question:

> Which OWASP LLM risk categories are relevant to the identified threats?

This mapping helps:

- Validate that the assessment covers major LLM security risks
- Organize findings according to a recognized framework
- Improve communication with security professionals and stakeholders
- Support risk prioritization and mitigation planning

---

## OWASP LLM Risk Mapping

| OWASP Category | Relevant Threats | Applicability to the AI Medical Assistant |
|------|------|------|
| LLM01: Prompt Injection | Prompt Injection and Indirect Prompt Injection | Malicious users or poisoned documents may override system instructions. |
| LLM02: Insecure Output Handling | Unsafe Output Generation and Guardrail Bypass | Model responses may contain harmful or sensitive content. |
| LLM03: Training Data Poisoning | Medical Knowledge Base Poisoning | Retrieved medical references may be manipulated. |
| LLM04: Model Denial of Service | Model Denial of Service and Excessive Token Consumption | Adversarial prompts may exhaust computational resources. |
| LLM05: Supply Chain Vulnerabilities | Supply Chain Adversary and Compromised Dependencies | Libraries, models and providers may be compromised. |
| LLM06: Sensitive Information Disclosure | PHI Exposure, Prompt Leakage and API Key Exposure | Sensitive data may be disclosed to users or third parties. |
| LLM07: Insecure Plugin Design | Excessive Agency and Unauthorized Tool Access | Tool invocation may perform unauthorized actions. |
| LLM08: Excessive Agency | Prompt Injection and Privilege Escalation | The model may gain access beyond intended permissions. |
| LLM09: Overreliance | Unsafe Output Generation and Misinformation | Users may trust inaccurate medical guidance. |
| LLM10: Model Theft | API Abuse and Unauthorized Model Access | Attackers may misuse provider access or extract model behavior. |

---

## Most Relevant Categories

Although all categories are considered, several are especially important for this project.

### LLM01: Prompt Injection

The most significant AI-specific risk. Malicious patients or poisoned documents may manipulate the prompt and override intended instructions.

### LLM02: Insecure Output Handling

The model may generate dangerous or privacy-violating responses if outputs are not properly validated.

### LLM03: Training Data Poisoning

Tampering with the Medical Knowledge Base may lead to harmful medical recommendations.

### LLM06: Sensitive Information Disclosure

Personal Health Information (PHI), prompts and secrets may be exposed.

### LLM09: Overreliance

Patients may act on AI-generated advice without consulting healthcare professionals.

---

## Detailed Category Analysis

### LLM01: Prompt Injection

The application accepts untrusted natural language input from patients and incorporates external documents into prompts. Both sources may contain malicious instructions intended to manipulate model behavior.

### LLM02: Insecure Output Handling

Model outputs may contain harmful medical recommendations, confidential information or policy-violating content if guardrails fail.

### LLM03: Training Data Poisoning

Although the underlying model is not trained by the organization, the RAG pipeline depends on a curated Medical Knowledge Base whose integrity is critical.

### LLM04: Model Denial of Service

Large or adversarial prompts may consume excessive tokens and increase latency or cost.

### LLM05: Supply Chain Vulnerabilities

The application depends on open-source libraries, vector databases and third-party providers.

### LLM06: Sensitive Information Disclosure

PHI and internal instructions may be exposed through prompts, responses, logs or external providers.

### LLM07: Insecure Plugin Design

If future tool integrations are introduced, insecure tool interfaces may allow unauthorized actions.

### LLM08: Excessive Agency

Prompt injection may cause the model to access data or functions beyond intended limits.

### LLM09: Overreliance

Patients may misinterpret the system as a replacement for licensed medical advice.

### LLM10: Model Theft

Unauthorized use of API keys may enable abuse of paid model access and reveal system behavior.

---

## Highest-Priority OWASP Risks

The highest-priority categories for this system are:

- LLM01: Prompt Injection
- LLM02: Insecure Output Handling
- LLM03: Training Data Poisoning
- LLM06: Sensitive Information Disclosure
- LLM09: Overreliance

These risks have the greatest potential impact on patient privacy and patient safety.

---

## Security Significance

This mapping confirms that the AI Medical Assistant is exposed to both traditional application risks and AI-specific threats identified by current industry guidance.

It also demonstrates that:

- Prompt-based attacks are central to the threat landscape
- Safety controls are as important as confidentiality controls
- Data integrity directly affects clinical reliability
- Human oversight remains essential

---

## Relationship to Other Sections

This section builds on:

- Abuse Cases
- STRIDE Threat Model

It also informs:

- MITRE ATLAS Mapping
- Risk Assessment
- Security Controls and Mitigations

---

## Conclusion

The OWASP Top 10 for LLM Applications mapping shows that the AI Medical Assistant is affected by nearly every major LLM security risk category.

The most critical concerns include prompt injection, insecure output handling, knowledge base poisoning, sensitive information disclosure and user overreliance on AI-generated medical advice.
