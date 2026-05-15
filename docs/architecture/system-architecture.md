# System Architecture Diagram

![System Architecture Diagram](../../diagrams/system-architecture.png)

## Overview

Before a security team can identify threats, it must first understand how the proposed application is designed.

The System Architecture Diagram provides a high-level blueprint of the AI Medical Assistant and shows all major components involved in processing patient requests and generating AI-assisted medical guidance.

This diagram answers one of the most important questions in any threat modeling engagement:

> What does the system look like and which components are responsible for handling sensitive data?

Without this architectural view, it would be difficult to determine where sensitive information is stored, which components communicate with external services and where security controls need to be enforced.

In this project, the diagram serves as the foundation for all subsequent analyses including the Data Flow Diagram, Trust Boundary Diagram, STRIDE Threat Model and Risk Assessment.

## Architectural Objective

The healthcare organization plans to deploy an AI-powered Medical Assistant that allows patients to submit symptoms and receive preliminary medical guidance.

At a high level, the application performs the following tasks:

1. Accepts symptoms and medical questions from patients.
2. Authenticates the user.
3. Retrieves relevant clinical references from a trusted Medical Knowledge Base.
4. Builds a prompt containing both the patient's input and retrieved context.
5. Sends the prompt to an external Large Language Model (LLM).
6. Validates the generated response using safety guardrails.
7. Stores the result in a secure database.
8. Optionally shares the generated summary with authorized doctors.

The purpose of the architecture diagram is to show which components are responsible for each of these tasks.

## Why This Diagram Matters

Threat modeling is highly dependent on system context.

Before asking questions such as:

- Where could Prompt Injection occur?
- Which components process Personal Health Information (PHI)?
- What happens if the Medical Knowledge Base is poisoned?
- Which systems communicate with third-party providers?

the security team must first understand how the application is structured.

The System Architecture Diagram provides this structural context.

It identifies:

- All major components
- External dependencies
- Sensitive data stores
- Security enforcement points
- Monitoring and logging systems

## Architectural Layers

To make the design easier to understand, the architecture is organized into five logical layers.

### 1. User Layer

The User Layer contains the people who interact directly with the system.

#### Patient

Patients submit symptoms, ask medical questions and receive AI-generated guidance.

#### Doctor

Doctors can review summaries that patients choose to share.

This layer is important because it represents the primary source of untrusted input entering the application.

### 2. Application Layer

The Application Layer contains the traditional web application components that manage access and route requests.

#### Patient Web Interface

The front-end application used by patients.

#### Doctor Dashboard

A secure interface used by healthcare professionals.

#### Authentication Service

Verifies user identities and enforces access control.

#### API Gateway

Acts as the central entry point and routes requests to internal services.

This layer is responsible for identity, authorization and secure request handling.

### 3. AI Processing Layer

This layer contains the components responsible for Retrieval-Augmented Generation (RAG) and model interaction.

#### LLM Orchestrator

Coordinates the end-to-end AI workflow.

#### Retrieval Engine

Searches the Medical Knowledge Base for relevant documents.

#### Output Guardrails

Checks generated responses for privacy, safety and policy compliance.

#### External LLM Provider

A third-party API that generates natural language responses.

This is the most security-sensitive layer because it handles prompt construction, model invocation and response validation.

### 4. Data Layer

The Data Layer stores both structured and unstructured information.

#### Patient Database

Stores PHI, generated summaries and application metadata.

#### Medical Knowledge Base

Contains trusted medical documents used by the RAG pipeline.

The confidentiality of the Patient Database and the integrity of the Medical Knowledge Base are especially important.

### 5. Monitoring Layer

The Monitoring Layer provides visibility into system activity.

#### Logging and Monitoring

Collects audit logs, application telemetry and security events.

This component is essential for detecting attacks and supporting investigations.

## Core Components and Their Responsibilities

| Component | Primary Responsibility |
|------|------|
| Patient Web Interface | Collects symptoms and displays AI-generated guidance. |
| Doctor Dashboard | Allows doctors to review shared summaries. |
| Authentication Service | Verifies identities and issues tokens. |
| API Gateway | Routes and filters application requests. |
| LLM Orchestrator | Coordinates retrieval, prompting and storage. |
| Retrieval Engine | Searches the Medical Knowledge Base. |
| Output Guardrails | Validates model responses. |
| External LLM Provider | Generates natural language output. |
| Patient Database | Stores PHI and generated summaries. |
| Medical Knowledge Base | Provides trusted clinical context. |
| Logging and Monitoring | Records audit and security events. |

## High-Level Request Flow

The following simplified workflow describes how the application processes a patient request.

1. A patient signs in and submits symptoms.
2. The Authentication Service verifies identity.
3. The API Gateway routes the request.
4. The LLM Orchestrator asks the Retrieval Engine for relevant clinical references.
5. The Retrieval Engine searches the Medical Knowledge Base.
6. The LLM Orchestrator constructs the final prompt.
7. The prompt is sent to the External LLM Provider.
8. The generated response is checked by Output Guardrails.
9. The validated result is stored in the Patient Database.
10. The response is returned to the patient.
11. All relevant events are recorded by Logging and Monitoring.
12. The patient may share the summary with a doctor.

## Security-Critical Components

Although every component matters, several have particularly high security significance.

### Patient Database

Contains highly sensitive medical data.

### Medical Knowledge Base

Its integrity directly influences model outputs.

### LLM Orchestrator

Controls prompt construction and model interaction.

### Output Guardrails

Serve as the final safety and privacy checkpoint.

### External LLM Provider

Represents a third-party dependency outside organizational control.

## External Dependencies

The architecture relies on an external LLM provider for inference.

This introduces several important security considerations:

- Sensitive prompts may leave the organization.
- Third-party outages can disrupt availability.
- Provider retention policies may affect privacy.
- Network communications must be encrypted.

This dependency is one of the most significant trust relationships in the entire system.

## Architectural Insights

By modeling the system architecture, several important observations emerge.

- PHI is processed by multiple components.
- The Medical Knowledge Base is a critical integrity dependency.
- Prompt data crosses organizational boundaries.
- Output Guardrails provide a final defense against unsafe responses.
- Logging and Monitoring are essential for detection and accountability.

These insights guide all subsequent security analyses.

## Security Questions Answered by This Diagram

This diagram helps answer the following questions:

- What components make up the system?
- Which services process sensitive medical data?
- Which components interact with external providers?
- Where are critical assets stored?
- Which systems enforce security controls?
- Which components should receive the most scrutiny?

## Conclusion

The System Architecture Diagram establishes the structural blueprint of the AI Medical Assistant.

It defines the scope of the security assessment, identifies the components responsible for handling sensitive data and highlights the most important dependencies and trust relationships.

Every subsequent artifact in this repository builds on the understanding established by this diagram.
