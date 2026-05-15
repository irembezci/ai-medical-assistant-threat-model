# STRIDE Threat Model

## Overview

After defining the system architecture, critical assets, threat actors, security assumptions and realistic abuse cases, the next step is to systematically identify threats affecting each major component of the AI Medical Assistant.

For this purpose, the assessment uses the [STRIDE](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats) methodology developed by [Microsoft](https://www.microsoft.com/).

STRIDE categorizes threats into six groups:

- **Spoofing** — Impersonating users or services
- **Tampering** — Modifying data or system behavior
- **Repudiation** — Denying actions without reliable audit trails
- **Information Disclosure** — Exposing sensitive information
- **Denial of Service** — Disrupting availability
- **Elevation of Privilege** — Gaining unauthorized permissions

By applying STRIDE to each component, the analysis ensures a comprehensive and structured evaluation of security risks.

---

## Purpose of the STRIDE Analysis

The purpose of this section is to answer the following question:

> What threats affect each major component of the system?

This analysis helps:

- Identify threats systematically
- Reduce the chance of overlooking risks
- Map threats to architectural components
- Support risk assessment and mitigation planning

---

## STRIDE Categories Explained

| Category | Description |
|------|------|
| Spoofing | Pretending to be another user, service or system component. |
| Tampering | Unauthorized modification of data, prompts, configurations or code. |
| Repudiation | Denial of actions due to insufficient logging or accountability. |
| Information Disclosure | Unauthorized exposure of sensitive information. |
| Denial of Service | Disruption of system availability. |
| Elevation of Privilege | Gaining access beyond intended permissions. |

---

## Threat Model by Component

### Patient Web Interface

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Attackers impersonate legitimate users using stolen credentials. |
| Tampering | Client-side parameters are modified before submission. |
| Repudiation | Users deny having submitted specific medical requests. |
| Information Disclosure | Sensitive data is exposed through browser storage or insecure transport. |
| Denial of Service | Automated requests overwhelm the interface. |
| Elevation of Privilege | Session manipulation grants unauthorized access. |

---

### Authentication Service

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Credential stuffing and password spraying attacks. |
| Tampering | Authentication tokens are altered or forged. |
| Repudiation | Failed login attempts are not properly logged. |
| Information Disclosure | Tokens or credentials are exposed. |
| Denial of Service | Repeated login attempts exhaust resources. |
| Elevation of Privilege | Authorization flaws grant higher privileges. |

---

### API Gateway

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Unauthenticated requests bypass gateway controls. |
| Tampering | API requests are modified in transit. |
| Repudiation | Requests are not attributable to a specific identity. |
| Information Disclosure | Sensitive data is exposed in API responses. |
| Denial of Service | Excessive API requests exhaust capacity. |
| Elevation of Privilege | Broken access control exposes restricted endpoints. |

---

### LLM Orchestrator

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Unauthorized services invoke orchestration functions. |
| Tampering | Prompt templates or system instructions are modified. |
| Repudiation | Prompt construction events are not logged. |
| Information Disclosure | PHI is included in prompts sent to unauthorized parties. |
| Denial of Service | Adversarial prompts trigger excessive token consumption. |
| Elevation of Privilege | Prompt injection causes unauthorized data access. |

---

### Retrieval Engine

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Unauthorized requests query the retrieval service. |
| Tampering | Retrieval parameters are manipulated. |
| Repudiation | Document access events are not recorded. |
| Information Disclosure | Sensitive documents are returned to unauthorized users. |
| Denial of Service | Expensive queries degrade performance. |
| Elevation of Privilege | Access restrictions are bypassed. |

---

### Medical Knowledge Base

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Untrusted contributors pose as authorized publishers. |
| Tampering | Documents are poisoned or modified. |
| Repudiation | Content changes are not traceable. |
| Information Disclosure | Restricted documents are exposed. |
| Denial of Service | Storage corruption or deletion reduces availability. |
| Elevation of Privilege | Unauthorized users gain write access. |

---

### External LLM Provider

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Requests are redirected to a malicious endpoint. |
| Tampering | Responses are altered in transit. |
| Repudiation | Provider actions are not fully auditable. |
| Information Disclosure | Prompts containing PHI are exposed or retained. |
| Denial of Service | Provider outages interrupt inference. |
| Elevation of Privilege | Provider compromise enables unauthorized access. |

---

### Output Guardrails

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Unauthorized services bypass validation controls. |
| Tampering | Guardrail policies are modified. |
| Repudiation | Blocked responses are not logged. |
| Information Disclosure | Sensitive content is not detected and filtered. |
| Denial of Service | Validation workloads delay responses. |
| Elevation of Privilege | Policy bypass allows unsafe outputs. |

---

### Patient Database

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Attackers access the database using stolen credentials. |
| Tampering | Patient records are altered or deleted. |
| Repudiation | Data changes are not attributable. |
| Information Disclosure | PHI is exposed. |
| Denial of Service | Database outages disrupt system functionality. |
| Elevation of Privilege | Unauthorized accounts gain administrative access. |

---

### Doctor Dashboard

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | Stolen doctor credentials are used to access records. |
| Tampering | Shared reports are modified. |
| Repudiation | Data access is not fully logged. |
| Information Disclosure | Unauthorized viewing of patient summaries. |
| Denial of Service | Dashboard access is disrupted. |
| Elevation of Privilege | Doctors gain unauthorized administrative capabilities. |

---

### Logging and Monitoring

| STRIDE Category | Example Threat |
|------|------|
| Spoofing | False log events are injected. |
| Tampering | Audit logs are altered or deleted. |
| Repudiation | Missing or incomplete logs undermine accountability. |
| Information Disclosure | Logs expose sensitive data. |
| Denial of Service | Log flooding overwhelms storage or detection systems. |
| Elevation of Privilege | Unauthorized users access monitoring systems. |

---

## Highest-Risk Threat Themes

Across all components, the most significant threat themes include:

- Prompt Injection
- Sensitive Data Disclosure
- Knowledge Base Poisoning
- Credential Theft
- Guardrail Bypass
- API Key Exposure
- Audit Log Tampering
- Denial of Service

---

## Security Significance

The STRIDE model provides a systematic and repeatable approach to identifying threats.

By evaluating each component across all six STRIDE categories, the assessment ensures broad coverage of traditional and AI-specific security risks.

---

## Relationship to Subsequent Analysis

The findings from this section are used directly in:

- OWASP Top 10 for LLM Applications Mapping
- MITRE ATLAS Mapping
- Risk Assessment
- Security Controls and Mitigations

---

## Conclusion

The STRIDE analysis reveals a wide range of threats affecting the AI Medical Assistant, from traditional web application risks to advanced AI-specific attacks such as prompt injection and knowledge base poisoning.

This structured threat model provides the analytical foundation for prioritizing risks and designing effective security controls.
