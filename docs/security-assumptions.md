# Security Assumptions

## Overview

Every threat model is built on a set of assumptions.

These assumptions define the architectural, operational, and trust conditions under which the system is designed and analyzed. They establish the boundaries of the assessment and clarify which controls are expected to be in place before evaluating potential threats.

Without explicitly documenting these assumptions, it becomes difficult to interpret risks consistently or understand the context in which identified threats are considered realistic.

---

## Purpose of Security Assumptions

The purpose of this section is to answer the following question:

> What conditions are assumed to be true when performing the security assessment?

By documenting these assumptions, the analysis can:

- Define the scope of the assessment
- Establish baseline security expectations
- Clarify what is considered trusted
- Prevent ambiguity during risk analysis
- Ensure that findings are interpreted consistently

---

## Architectural Assumptions

The following assumptions describe the overall system design.

- The application is deployed in a cloud-hosted environment.
- The Large Language Model (LLM) is accessed through a third-party API provider.
- Retrieval-Augmented Generation (RAG) is used to retrieve trusted medical references.
- The Patient Database stores Personal Health Information (PHI) and AI-generated summaries.
- Doctors access shared patient summaries through a secure dashboard.
- All major components generate audit logs.

---

## Authentication and Authorization Assumptions

The following assumptions apply to identity and access management.

- Each patient, doctor, and administrator has a unique account.
- Role-Based Access Control (RBAC) is enforced.
- Session tokens are securely generated and validated.
- Access to PHI is restricted to authorized users.
- Administrative functions require elevated privileges.
- Patients must explicitly consent before summaries are shared with doctors.

---

## Data Protection Assumptions

The following assumptions apply to data confidentiality and integrity.

- Data in transit is protected using TLS.
- Sensitive data is encrypted at rest.
- API keys and secrets are stored in a secure secrets management solution.
- Audit logs are protected from unauthorized modification.
- Backups are encrypted and stored securely.

---

## AI-Specific Assumptions

The following assumptions are specific to AI and LLM-based processing.

- Prompts may contain sensitive patient information.
- The external LLM provider may process data outside the organization's security boundary.
- Output Guardrails validate responses for privacy and safety issues.
- The Medical Knowledge Base is trusted unless compromised through data poisoning.
- Model outputs are informational and do not replace professional medical diagnosis.

---

## Operational Assumptions

The following assumptions apply to day-to-day system operations.

- Logging and monitoring are enabled across all major components.
- Rate limiting is enforced to reduce abuse.
- Security patches are applied regularly.
- Incident response procedures are available.
- Personnel with privileged access are subject to oversight.

---

## Compliance and Privacy Assumptions

The following assumptions apply to regulatory and privacy obligations.

- Personal Health Information (PHI) is treated as highly sensitive data.
- Access to medical data is auditable.
- Data retention and deletion policies are defined.
- Third-party providers are subject to contractual privacy requirements.

---

## Scope Assumptions

The following assumptions define what is included and excluded from this assessment.

- The analysis focuses on application-layer and AI-specific security risks.
- Physical security is considered out of scope.
- Underlying cloud infrastructure is assumed to be securely managed by the provider.
- End-user devices are assumed to be uncompromised unless otherwise stated.

---

## Security Significance

Security assumptions are essential because they define the baseline conditions that support the threat model.

If any of these assumptions are invalid, the actual risk level may be significantly higher than the assessment indicates.

For example:

- If encryption is not enabled, confidentiality risks increase.
- If RBAC is not enforced, unauthorized access becomes more likely.
- If guardrails are ineffective, unsafe outputs may reach patients.

---

## Key Security Questions

This section helps answer the following questions:

- What controls are assumed to exist?
- Which components are considered trusted?
- What is outside the scope of the assessment?
- What conditions must hold true for the threat model to remain valid?

---

## Relationship to Threat Modeling

Security assumptions influence every stage of the analysis, including:

- Abuse Case Development
- STRIDE Threat Modeling
- Risk Assessment
- Mitigation Prioritization

They provide the baseline context used to interpret all identified threats.

---

## Conclusion

The Security Assumptions section defines the conditions and expectations that underpin the threat model.

By documenting architectural, operational, and trust-related assumptions, the assessment establishes a consistent foundation for evaluating threats and prioritizing security controls.
