# Risk Assessment

## Overview

After identifying threats and mapping them to STRIDE, OWASP Top 10 for LLM Applications and MITRE ATLAS, the next step is to evaluate their relative severity.

This section applies a qualitative risk assessment methodology based on two factors:

- Likelihood
- Impact

The combination of these two factors determines the overall risk level and helps prioritize mitigation efforts.

---

## Purpose of the Risk Assessment

The purpose of this section is to answer the following question:

> Which threats represent the highest priority for remediation?

This assessment helps:

- Prioritize security findings
- Focus mitigation efforts
- Communicate risk to stakeholders
- Support security decision-making

---

## Risk Rating Methodology

### Likelihood

Likelihood estimates how probable it is that a threat will occur.

| Rating | Description |
|------|------|
| Low | Unlikely to occur under normal conditions. |
| Medium | Possible with moderate effort or favorable circumstances. |
| High | Likely to occur and technically feasible for motivated attackers. |
| Critical | Highly probable and expected to occur without strong controls. |

### Impact

Impact estimates the severity of consequences if the threat occurs.

| Rating | Description |
|------|------|
| Low | Minimal operational or security consequences. |
| Medium | Moderate disruption or limited data exposure. |
| High | Significant privacy, safety or operational consequences. |
| Critical | Severe patient harm, major regulatory exposure or prolonged operational disruption. |

### Overall Risk Level

The overall risk is determined by combining Likelihood and Impact.

---

## Risk Assessment Table

| Threat | Likelihood | Impact | Overall Risk | Rationale |
|------|------|------|------|------|
| Prompt Injection | Critical | Critical | Critical | Directly targets model behavior and may lead to unsafe outputs or data disclosure. |
| Sensitive Data Disclosure | High | Critical | Critical | Exposure of PHI may trigger severe privacy and regulatory consequences. |
| Medical Knowledge Base Poisoning | High | Critical | Critical | Corrupted references may produce dangerous medical guidance. |
| Unsafe Output Generation | High | Critical | Critical | Inaccurate or harmful advice may directly affect patient safety. |
| Data Exfiltration via LLM Provider | Medium | Critical | High | Sensitive data may be retained or exposed outside organizational control. |
| Credential Theft | High | High | High | Stolen credentials may lead to account takeover and unauthorized access. |
| API Key Exposure | Medium | High | High | Secrets may be abused to access third-party services and data. |
| Model Denial of Service | High | Medium | High | Excessive requests may degrade performance and increase cost. |
| Audit Log Tampering | Medium | High | High | Reduces visibility and hinders incident investigations. |
| Ransomware Deployment | Medium | Critical | High | May disrupt operations and make critical data unavailable. |
| Session Hijacking | Medium | High | High | Allows attackers to reuse authenticated sessions. |
| Unauthorized Doctor Access | Medium | High | High | Leads to privacy violations and unauthorized PHI disclosure. |
| Supply Chain Compromise | Medium | Critical | High | Compromised dependencies may affect multiple components. |
| Overreliance on AI Output | High | High | High | Patients may act on incorrect recommendations without professional oversight. |

---

## Critical Risks

The following threats are assessed as Critical:

- Prompt Injection
- Sensitive Data Disclosure
- Medical Knowledge Base Poisoning
- Unsafe Output Generation

These threats pose the greatest risk to patient privacy and patient safety.

---

## High Risks

The following threats are assessed as High:

- Data Exfiltration via LLM Provider
- Credential Theft
- API Key Exposure
- Model Denial of Service
- Audit Log Tampering
- Ransomware Deployment
- Session Hijacking
- Unauthorized Doctor Access
- Supply Chain Compromise
- Overreliance on AI Output

These risks require strong preventive and detective controls.

---

## Key Risk Themes

Several recurring themes emerge from the assessment:

### Patient Safety Risk

Unsafe or misleading medical guidance may cause inappropriate health decisions.

### Privacy and Compliance Risk

Exposure of Personal Health Information (PHI) may result in regulatory penalties and reputational damage.

### Data Integrity Risk

Poisoned documents and tampered prompts may corrupt model behavior.

### Third-Party Dependency Risk

The external LLM provider introduces privacy, availability and compliance concerns.

### Operational Resilience Risk

Denial of Service and ransomware may disrupt critical healthcare workflows.

---

## Security Significance

The risk assessment transforms a large set of identified threats into a prioritized remediation plan.

Rather than treating all threats equally, this approach focuses attention on the issues most likely to affect:

- Patient safety
- Confidentiality
- System integrity
- Operational continuity

---

## Relationship to Other Sections

This section builds on:

- STRIDE Threat Model
- OWASP Top 10 for LLM Applications Mapping
- MITRE ATLAS Mapping

It directly informs:

- Security Controls and Mitigations
- Executive Summary

---

## Conclusion

The risk assessment identifies Prompt Injection, Sensitive Data Disclosure, Medical Knowledge Base Poisoning and Unsafe Output Generation as the most critical threats affecting the AI Medical Assistant.

These findings highlight the need for strong prompt security, rigorous output validation, data protection controls and human oversight to ensure both privacy and patient safety.
