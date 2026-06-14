---
name: saif-control-model-data-integrity
description: |
  SAIF Control: Model and Data Integrity Management. Ensure all data, models, and code
  used to produce AI models are verifiably integrity-protected during development and
  deployment. Covers cryptographic signatures, checksums, and supply chain integrity.
  Use this skill when implementing integrity verification, securing build pipelines,
  or protecting model artifacts.
trigger: |
  - When implementing integrity verification for AI assets
  - When securing model build pipelines
  - When protecting model artifacts from tampering
  - When implementing cryptographic signatures
  - When auditing supply chain integrity
---

# SAIF Control: Model and Data Integrity Management

## Control Overview

**Who can implement:** Model Creators, Model Consumers (if storing models)

**Risk mapping:** Data Poisoning, Model Source Tampering

**Description:** Ensure that all data, models, and code used to produce AI models are verifiably integrity-protected during development and deployment.

## Implementation Strategies

### 1. Cryptographic Signatures

| Asset | Signature Method |
|-------|-----------------|
| **Model weights** | Sign with private key, verify with public key |
| **Training data** | Hash and sign dataset manifests |
| **Code** | Sign commits and build artifacts |
| **Dependencies** | Verify package signatures |
| **Configuration** | Sign deployment configurations |

### 2. Checksum Verification

```
Build → Hash → Sign → Store → Verify → Deploy
```

| Stage | Action |
|-------|--------|
| Build | Generate artifact |
| Hash | Compute SHA-256 checksum |
| Sign | Cryptographically sign hash |
| Store | Store artifact with signature |
| Verify | Validate signature before use |
| Deploy | Deploy verified artifact |

### 3. Supply Chain Integrity

| Component | Protection |
|-----------|-----------|
| **Source code** | Signed commits, code review |
| **Build pipeline** | Hardened build environment |
| **Dependencies** | Verified packages, SBOM |
| **Artifacts** | Signed and checksum-verified |
| **Deployment** | Verified deployment pipeline |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Model and Data Inventory | Track integrity status of all assets |
| Model and Data Access Control | Integrity verification before access |
| Secure-by-Default ML Tooling | Tool integrity verification |
| Training Data Sanitization | Verify sanitized data integrity |

## Testing Checklist

- [ ] Verify signature on all model artifacts
- [ ] Test checksum validation pipeline
- [ ] Validate supply chain integrity
- [ ] Test tamper detection mechanisms
- [ ] Audit integrity verification logs
- [ ] Verify key management security
- [ ] Test rollback to last known good version
- [ ] Validate SBOM accuracy

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
