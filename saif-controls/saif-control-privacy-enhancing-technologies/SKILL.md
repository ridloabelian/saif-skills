---
name: saif-control-privacy-enhancing-technologies
description: |
  SAIF Control: Privacy Enhancing Technologies. Use technologies that minimize,
  de-identify, or restrict use of PII data in training or evaluating models.
  Covers differential privacy, federated learning, secure multi-party computation,
  and data anonymization. Use this skill when implementing privacy-preserving ML,
  designing data minimization strategies, or complying with privacy regulations.
trigger: |
  - When implementing privacy-preserving machine learning
  - When designing data minimization strategies
  - When complying with GDPR, CCPA, or other privacy regulations
  - When evaluating differential privacy implementations
  - When securing sensitive training data
---

# SAIF Control: Privacy Enhancing Technologies

## Control Overview

**Who can implement:** Model Creators

**Risk mapping:** Sensitive Data Disclosure

**Description:** Use technologies that minimize, de-identify, or restrict use of PII data in training or evaluating models.

## Technologies

### 1. Differential Privacy

**Principle:** Add calibrated noise to data or model outputs to prevent individual data identification.

| Aspect | Implementation |
|--------|---------------|
| **Epsilon budget** | Define privacy budget for training |
| **Noise addition** | Add Gaussian or Laplace noise to gradients |
| **Privacy accounting** | Track cumulative privacy loss |
| **Composition** | Manage privacy across multiple queries |

**Use cases:**
- Training on sensitive datasets (medical, financial)
- Publishing aggregate statistics
- Model release with privacy guarantees

### 2. Federated Learning

**Principle:** Train models across decentralized devices without centralizing raw data.

| Component | Function |
|-----------|----------|
| **Local training** | Each device trains on local data |
| **Gradient aggregation** | Server aggregates model updates |
| **Secure aggregation** | Encrypt updates during transmission |
| **Differential privacy** | Add noise to aggregated updates |

**Use cases:**
- Mobile keyboard prediction
- Health data on user devices
- Cross-organizational collaboration

### 3. Secure Multi-Party Computation (SMPC)

**Principle:** Multiple parties jointly compute on encrypted data without revealing inputs.

| Technique | Description |
|-----------|-------------|
| **Secret sharing** | Split data across multiple parties |
| **Homomorphic encryption** | Compute on encrypted data |
| **Garbled circuits** | Secure two-party computation |
| **Oblivious transfer** | Secure data retrieval |

**Use cases:**
- Cross-border data analysis
- Private set intersection
- Secure model inference

### 4. Data Anonymization

**Principle:** Remove or generalize identifying information.

| Technique | Implementation |
|-----------|---------------|
| **K-anonymity** | Ensure each record indistinguishable from k-1 others |
| **L-diversity** | Ensure sensitive attributes have l distinct values |
| **T-closeness** | Ensure distribution of sensitive attributes close to overall |
| **Generalization** | Replace specific values with broader categories |
| **Suppression** | Remove identifying attributes entirely |

**Use cases:**
- Publishing training datasets
- Sharing data for research
- Regulatory compliance

## Implementation Checklist

- [ ] Identify privacy requirements for training data
- [ ] Select appropriate PETs for data type and use case
- [ ] Implement differential privacy with proper epsilon budget
- [ ] Configure federated learning with secure aggregation
- [ ] Evaluate anonymization effectiveness against re-identification attacks
- [ ] Document privacy guarantees and limitations
- [ ] Test privacy-utility tradeoff
- [ ] Monitor for privacy attacks (membership inference, model inversion)

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Training Data Management | Apply PETs to authorized data |
| User Data Management | Implement consent for privacy-preserving techniques |
| Output Validation | Verify privacy guarantees hold in outputs |

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
