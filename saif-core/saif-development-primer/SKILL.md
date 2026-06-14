---
name: saif-development-primer
description: |
  Secure AI Development Primer — guide AI development through a security lens.
  Covers data sourcing, training, evaluation, deployment, and monitoring with
  security controls at each stage. Use this skill when building or reviewing
  AI development pipelines, onboarding AI developers to security practices,
  or auditing AI development processes.
trigger: |
  - When building AI development pipelines
  - When onboarding AI developers to security
  - When auditing AI development processes
  - When reviewing data sourcing or training practices
  - When implementing MLOps with security controls
---

# Secure AI Development Primer

## Overview

This primer targets two audiences:
- **Security practitioners**: Understand how data, infrastructure, and applications integrate with AI models to identify risk origins
- **AI developers**: Understand security implications of development choices to select more secure options

**Core thesis**: Risks accumulate throughout development; isolated decisions can have far-reaching consequences. While focused on Generative AI, principles apply broadly to all AI models.

## 1. Data

### 1.1 Data Sourcing and Ingestion

**Key questions developers should ask:**
- What is the intended use case and what questions must be answered?
- What data could train the model to answer these questions?
- Is data high-quality, complete, accurate, and relevant?
- Can data sources be verified as uncompromised (e.g., cryptographic signatures)?
- What are the rights to use the data, and how are they documented?
- Are there ethical concerns, biases, or legal risks?

> **"Using unauthorized training data can cause long-lasting risks."**

**Risks:**
| Risk | Description |
|------|-------------|
| **Unauthorized training data** | Copyrighted material → legal repercussions; user data without consent → regulatory violations; may require model retraining or retirement |
| **Data poisoning (direct)** | Modifying existing data points or inserting malicious samples directly into training dataset (e.g., insider mislabeling images for abuse detection) |
| **Data poisoning (indirect)** | Contaminating data sources before ingestion (e.g., posting misinformation on web that gets incorporated into datasets) |

**Real-world example**: Misinformation in a public help article was surfaced by an LLM that ingested it (iFixit article → ChatGPT output).

### 1.2 Data Cleaning and Augmentation

**Data cleaning addresses:** missing values, duplicates, incorrect labels, dataset corruption, and sensitive data.

**Data augmentation techniques:**
- Transforming data formats/schemata between sources
- Creating synthetic data (via another model or deterministic manipulations like image rotation/mirroring)

> **"Each of the stages of data cleaning and transformation introduces the potential of data poisoning or other types of tampering."**

**Critical concept: Lineage and Provenance**

| Term | Definition |
|------|-----------|
| **Lineage** | Capturing metadata about datasets, transformations, and resulting models |
| **Provenance** | Broader: includes infrastructure metadata and cryptographic signatures for inputs/outputs |

> **"Lineage and provenance contribute to data management and model integrity, and forms the foundation for AI model governance."**

**Risks:**
- **Sensitive data disclosure** if not sanitized during cleaning
- **Data poisoning** via human mislabeling or automated process bugs
- **Excessive data retention** — lineage/provenance support governance for data with limited retention periods

## 2. Training

**Core concept:** Model = collection of weights (parameters determining feature influence), established through iterative adjustment until predictions match desired outcomes.

**Training approaches:**

| Approach | Description | Use Case |
|----------|-------------|----------|
| **From scratch** | Random initial weights, iteratively adjusted | Small models |
| **Transfer learning** | Teach a model trained for one task to perform another | Specialization with less data |
| **Finetuning** | Freeze most weights, update only last few computations | Most efficient for new tasks |

**Example:** General image recognition model → specialized for X-ray diagnostics using smaller medical scan dataset.

**Risks: Model source tampering**
- Pretrained models could contain backdoors or poor performance on certain tasks
- Tampering possible between training and finetuning
- **Provenance critical** to identify compromised models if training environment is breached

## 3. Evaluation

**Goal:** Ensure effective performance without overfitting (exceptional training data performance but failure on new data).

**Evaluation stages:**
1. **Automated testing during training:** Random split into training/test sets; test data evaluates unseen examples periodically
2. **Human evaluation between runs:** RLHF (Reinforcement Learning from Human Feedback) — humans rate responses to create improvement datasets
3. **Post-release evaluation:** Third-party testing similar to integration/acceptance testing

**Privacy evaluation:** Measure memorization (recall of specific training data); mitigate via data generalization.

**Production hygiene:** Continuously monitor model performance and drift; re-evaluate when data distributions shift.

## 4. Deployment

**Security considerations:**
- **Model serving infrastructure hardening** — Secure-by-default ML tooling
- **Input validation** — Filter and sanitize all inputs before model processing
- **Output validation** — Filter and sanitize all outputs before passing to users or downstream systems
- **Access controls** — Rate limiting, authentication, authorization for model APIs
- **Monitoring** — Detect anomalies in inputs, outputs, and usage patterns

## 5. Monitoring and Incident Response

**Continuous monitoring:**
- Input/output anomaly detection
- Usage pattern analysis (detect reverse engineering, DoS)
- Model drift detection
- Security event correlation

**Incident response:**
- Predefined playbooks for AI-specific incidents
- Rapid model rollback capabilities
- Communication templates for stakeholders
- Post-incident analysis and model retraining

## Security Checklist by Stage

### Data Stage
- [ ] Data sources verified and authorized
- [ ] Cryptographic signatures checked where available
- [ ] Sensitive data identified and sanitized
- [ ] Lineage and provenance metadata captured
- [ ] Data poisoning detection in place

### Training Stage
- [ ] Training environment secured (access controls, network isolation)
- [ ] Model code and dependencies integrity-checked
- [ ] Checkpoints encrypted and access-controlled
- [ ] Training logs audited

### Evaluation Stage
- [ ] Test data separated from training data
- [ ] Memorization testing performed
- [ ] Adversarial testing conducted
- [ ] Third-party evaluation scheduled

### Deployment Stage
- [ ] Serving infrastructure hardened
- [ ] Input/output validation implemented
- [ ] Rate limiting and access controls configured
- [ ] Monitoring and alerting enabled

### Operations Stage
- [ ] Continuous monitoring active
- [ ] Incident response playbooks ready
- [ ] Regular red team exercises scheduled
- [ ] Model updates and retraining pipeline secure

## References

- https://saif.google/ai-development-primer
- https://saif.google/secure-ai-framework
- https://saif.google/risks
