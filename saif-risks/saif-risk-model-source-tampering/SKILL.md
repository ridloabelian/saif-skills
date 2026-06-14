---
name: saif-risk-model-source-tampering
description: |
  SAIF Risk: Model Source Tampering (MST). Tampering with the model's source code,
  dependencies, or weights through supply chain attacks or insider attacks. Covers
  architecture backdoors and dependency confusion. Use this skill when securing model
  supply chains, implementing integrity checks, or hardening development infrastructure.
trigger: |
  - When securing model supply chains
  - When implementing code integrity checks
  - When hardening ML development infrastructure
  - When evaluating third-party ML dependencies
  - When protecting model weights and checkpoints
---

# SAIF Risk: Model Source Tampering (MST)

## Risk Overview

**Who can mitigate:** Model Creators

**Description:** Tampering with the model's source code, dependencies, or weights, either by supply chain attacks or insider attacks.

Similar to tampering with traditional software code, Model Source Tampering can introduce vulnerabilities or unexpected behaviors.

## Attack Vectors

### 1. Supply Chain Attacks
- Attacks on model code dependencies
- Dependency confusion attacks
- Compromised build pipelines

### 2. Architecture Backdoors
- Backdoors embedded within neural network architecture definition
- Can survive full retraining of model
- Difficult to detect through standard evaluation

### 3. Insider Attacks
- Malicious or compromised insiders modifying model code
- Unauthorized access to model weights
- Tampering with training frameworks

## When Risk is Introduced

Model Source Tampering is introduced when:
- Model code, training frameworks, or model weights are not hardened against supply chain attacks
- Dependencies are not verified for integrity
- Access controls are insufficient

## When Risk is Exposed

- **In model frameworks and code components:** If tampering is discovered at the source
- **In the model itself:** Through modified behavior during use if tampering goes undetected

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Secure-by-Default ML Tooling** | Use secure frameworks and libraries with verified integrity |
| **Model and Data Integrity Management** | Cryptographic signatures for model code and weights |
| **Model and Data Access Control** | Minimize internal access to model code and weights |
| **Model and Data Inventory Management** | Track all models, code, and dependencies |

## Real-World Examples

- **PyTorch nightly build attack:** The nightly build of PyTorch package was subjected to a supply chain attack (dependency confusion attack that installed compromised dependency running malicious binary)

## Testing Checklist

- [ ] Verify integrity of all model dependencies
- [ ] Check cryptographic signatures on model weights
- [ ] Audit access to model code repositories
- [ ] Test for architecture backdoors
- [ ] Monitor for unauthorized code changes
- [ ] Validate build pipeline security
- [ ] Implement software bill of materials (SBOM) for models

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
