---
name: saif-risk-assessment
description: |
  SAIF Risk Self-Assessment methodology. Guide organizations through identifying
  which of the 15 SAIF risks are most relevant to their AI systems, based on
  their role (Model Creator vs Model Consumer) and use cases. Use this skill
  when evaluating AI security posture, preparing for audits, or prioritizing
  security investments.
trigger: |
  - When conducting AI security risk assessment
  - When prioritizing which AI risks to address first
  - When preparing for NIST AI RMF or ISO 42001 compliance
  - When onboarding new AI systems or vendors
---

# SAIF Risk Self Assessment

## Purpose

Answer a few questions and discover which risks affect your organization and which controls to implement. The assessment is designed for any organization size, sector, or security posture.

## Assessment Framework

### Step 1: Determine Your Role

| Role | Definition | Primary Risks |
|------|-----------|-------------|
| **Model Creator** | Train or develop AI models for use by yourself or others | DP, UTD, MST, EDH, MXF, MDT, DMS, MEV, SDD, ISD |
| **Model Consumer** | Use AI models to build AI-powered products and applications | MXF, MDT, DMS, MRE, IIC, PIJ, MEV, SDD, ISD, IMO, RA |
| **Both** | Train models AND use them in products | All 15 risks |

### Step 2: Identify Your Components

Which components of the AI development lifecycle do you touch?

| Component | Examples | Relevant Risks |
|-----------|----------|---------------|
| **Data Sources** | Web scraping, APIs, databases, sensor data | DP, UTD |
| **Data Filtering/Processing** | Cleaning, labeling, augmentation | DP, UTD, EDH |
| **Training Data** | Final curated dataset for training | DP, UTD, EDH, SDD |
| **Model Frameworks/Code** | PyTorch, TensorFlow, JAX, custom code | MST |
| **Training/Tuning/Evaluation** | GPU clusters, training pipelines | MST, MXF, MEV |
| **Data/Model Storage** | Model hubs, cloud storage, on-prem | MXF, MST, EDH |
| **Model Serving** | APIs, edge deployment, on-device | MDT, MXF, DMS |
| **Model (Weights)** | The trained model itself | MXF, MRE, MEV |
| **Input Handling** | Prompt preprocessing, filtering | PIJ, MEV |
| **Output Handling** | Response filtering, sanitization | IMO, SDD, ISD, RA |
| **Application** | Chatbot, recommendation engine, agent | IIC, PIJ, DMS, RA |
| **Agent/Plugin** | External tool calls, autonomous actions | IIC, RA, SDD |

### Step 3: Map Risks to Your Context

For each risk, ask:
1. Do we have exposure to this risk? (Yes/No/Maybe)
2. What is the potential impact? (Low/Medium/High/Critical)
3. What controls are currently in place?
4. What controls should we implement?

## Risk Priority Matrix

| Risk | Model Creator | Model Consumer | Impact | Difficulty to Mitigate |
|------|--------------|----------------|--------|----------------------|
| Data Poisoning (DP) | High | Low | Critical | Medium |
| Unauthorized Training Data (UTD) | High | N/A | High | Medium |
| Model Source Tampering (MST) | High | Low | Critical | Medium |
| Excessive Data Handling (EDH) | High | Medium | High | Low |
| Model Exfiltration (MXF) | High | High | Critical | Medium |
| Model Deployment Tampering (MDT) | Medium | High | Critical | Medium |
| Denial of ML Service (DMS) | Low | High | High | Low |
| Model Reverse Engineering (MRE) | Low | High | Medium | Medium |
| Insecure Integrated Component (IIC) | Low | High | High | Medium |
| Prompt Injection (PIJ) | Medium | High | Critical | High |
| Model Evasion (MEV) | High | High | High | High |
| Sensitive Data Disclosure (SDD) | High | High | Critical | Medium |
| Inferred Sensitive Data (ISD) | High | High | Medium | Medium |
| Insecure Model Output (IMO) | Low | High | High | Medium |
| Rogue Actions (RA) | Low | High | Critical | High |

## Assessment Output Template

```
Organization: [Name]
Date: [Date]
Assessor: [Name/Role]

ROLE DETERMINATION:
- Primary Role: [Model Creator / Model Consumer / Both]
- Components Involved: [List]

RISK REGISTER:
| Risk | Exposure | Impact | Current Controls | Gap | Priority |
|------|----------|--------|-----------------|-----|----------|
| DP   | [Y/N/M]  | [L/M/H/C] | [List] | [Desc] | [P1-P5] |
| ...  |          |          |        |        |          |

CONTROL ROADMAP:
| Control | Target Date | Owner | Status |
|---------|------------|-------|--------|
| ...     |            |       |        |

GOVERNANCE ACTIONS:
- [List executive/board-level actions]
```

## Quick Start Questions

1. Do you train or fine-tune AI models? → If yes, focus on Model Creator risks
2. Do you use AI models in products/services? → If yes, focus on Model Consumer risks
3. Do you handle user data in AI systems? → If yes, prioritize SDD, EDH, ISD
4. Do you use agents or plugins? → If yes, prioritize RA, IIC, Agent controls
5. Do you expose models via API? → If yes, prioritize MXF, MRE, DMS, PIJ

## References

- https://saif.google
- https://saif.google/secure-ai-framework
- https://saif.google/ai-development-primer
