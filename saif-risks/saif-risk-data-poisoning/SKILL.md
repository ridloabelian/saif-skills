---
name: saif-risk-data-poisoning
description: |
  SAIF Risk: Data Poisoning (DP). Altering data sources used during training or
  retraining to degrade model performance, skew results, or create hidden backdoors.
  Covers direct poisoning, indirect poisoning, and backdoor installation. Use this
  skill when securing training data pipelines, implementing data sanitization, or
  auditing data integrity.
trigger: |
  - When securing training data pipelines
  - When implementing data sanitization controls
  - When auditing data integrity and provenance
  - When evaluating supply chain risks for training data
  - When detecting anomalous model behavior
---

# SAIF Risk: Data Poisoning (DP)

## Risk Overview

**Who can mitigate:** Model Creators

**Description:** Altering data sources used during training or retraining (by deleting or modifying existing data as well as injecting adversarial data) to degrade model performance, skew results towards a specific outcome, or create hidden backdoors.

Data Poisoning can be considered comparable to maliciously modifying the logic of an application to change its behavior.

## Types of Data Poisoning

### 1. Direct Data Poisoning
Modifying existing data points or inserting malicious samples directly into the training dataset.

**Examples:**
- Insider mislabeling images for abuse detection
- Modifying training examples to create specific biases
- Injecting adversarial examples into dataset

### 2. Indirect Data Poisoning
Contaminating data sources before ingestion into the organization.

**Examples:**
- Posting misinformation on web that gets incorporated into datasets
- Poisoning public data sources used for training
- Compromising third-party data providers

### 3. Backdoor Installation
Specific alterations of training data that create hidden triggers.

**Characteristics:**
- Backdoored models continue to function normally
- Alternate behaviors triggered under certain conditions
- Difficult to detect during normal evaluation

**Example:**
- Images with specific watermark trigger misclassification
- Text with specific phrase triggers toxic output

## Attack Vectors

| Vector | Description | When It Occurs |
|--------|-------------|----------------|
| **Pre-ingestion** | Poison public data sources before organization collects them | Before data enters organization |
| **In-storage** | Modify datasets while held in storage | During data storage |
| **During training** | Submit poisoned prompt-response examples for tuning data | During training/tuning process |
| **Via dependencies** | Poison data through compromised third-party data providers | Data sourcing phase |

## Real-World Examples

1. **Indirect Pollution of Public Data Sources:**
   - Researchers showed they could indirectly pollute popular data sources used for training models with minimal cost
   - Poisoned Wikipedia articles, web pages, or forum posts eventually scraped into training datasets

2. **Poisoning During Instruction Tuning:**
   - 2023 research paper demonstrated poisoning models during instruction tuning
   - Malicious or compromised insider submits poisoned prompt-response examples
   - Model learns harmful behaviors embedded in tuning data

3. **Backdoor Installation:**
   - Specific alterations of training data install hidden backdoors
   - Model behaves normally until trigger condition met
   - Trigger could be specific keyword, image pattern, or data combination

## Impact

| Impact Type | Severity | Description |
|-------------|----------|-------------|
| Model degradation | High | Reduced accuracy, biased outputs |
| Backdoor activation | Critical | Malicious behavior triggered by attackers |
| Reputation damage | High | Model produces harmful or incorrect outputs |
| Security bypass | Critical | Backdoor bypasses safety controls |
| Data integrity loss | High | Training data no longer trustworthy |

## Mitigation Controls

### Primary Controls

| Control | Implementation |
|---------|---------------|
| **Training Data Sanitization** | Detect and remove or remediate poisoned data. Automated anomaly detection in training datasets. Statistical analysis for outliers. |
| **Secure-by-Default ML Tooling** | Use secure frameworks and libraries. Verify integrity of ML tooling. Regular security updates. |
| **Model and Data Integrity Management** | Cryptographic signatures for data and models. Verify integrity during development and deployment. |
| **Model and Data Access Control** | Minimize internal access to training data. Role-based access controls. Audit all data access. |
| **Model and Data Inventory Management** | Track all data sources, transformations, and resulting models. Maintain complete lineage and provenance. |

### Data Pipeline Security

1. **Data Sourcing**
   - Verify data source authenticity
   - Check cryptographic signatures where available
   - Document data provenance
   - Assess supplier security posture

2. **Data Ingestion**
   - Validate data format and structure
   - Check for anomalies in new data batches
   - Compare against known good data distributions
   - Implement quarantine for suspicious data

3. **Data Processing**
   - Monitor for unusual patterns during cleaning/augmentation
   - Validate labeling accuracy
   - Check for duplicate or near-duplicate injection
   - Audit all transformations

4. **Data Storage**
   - Encrypt data at rest
   - Implement access controls
   - Monitor for unauthorized access
   - Regular integrity checks

5. **Training**
   - Monitor training metrics for anomalies
   - Compare model behavior against baseline
   - Implement checkpoint validation
   - Alert on unexpected training dynamics

## Detection Strategies

| Detection Method | Description |
|-----------------|-------------|
| Statistical anomaly detection | Identify outliers in training data distributions |
| Behavioral analysis | Compare model outputs against expected behavior |
| Backdoor scanning | Test for trigger-activated anomalous behavior |
| Provenance tracking | Verify data source integrity through supply chain |
| Insider threat monitoring | Detect unusual access patterns to training data |

## Testing Checklist

- [ ] Test with known poisoned data samples
- [ ] Test backdoor activation with trigger inputs
- [ ] Verify data sanitization effectiveness
- [ ] Test integrity verification mechanisms
- [ ] Test access control enforcement
- [ ] Verify provenance tracking completeness
- [ ] Test anomaly detection on poisoned batches
- [ ] Verify model behavior consistency across checkpoints

## References

- https://saif.google/secure-ai-framework
- https://saif.google/ai-development-primer
- https://arxiv.org/abs/2302.10149 (Poisoning training data)
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
