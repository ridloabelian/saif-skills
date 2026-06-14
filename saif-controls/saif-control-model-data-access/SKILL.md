---
name: saif-control-model-data-access
description: |
  SAIF Control: Model and Data Access Controls. Minimize internal access to models,
  weights, datasets, etc. in storage and in production use. Covers RBAC, least-privilege
  access, and production access controls. Use this skill when implementing access
  controls for AI assets, designing production security, or managing model access.
trigger: |
  - When implementing access controls for AI assets
  - When designing production security for models
  - When managing model access permissions
  - When evaluating insider threat risks
  - When securing model weights and checkpoints
---

# SAIF Control: Model and Data Access Controls

## Control Overview

**Who can implement:** Model Creators, Model Consumers (if storing models)

**Risk mapping:** Data Poisoning, Model Source Tampering, Model Exfiltration

**Description:** Minimize internal access to models, weights, datasets, etc. in storage and in production use.

## Implementation Strategies

### 1. Role-Based Access Control (RBAC)

| Role | Model Access | Data Access | Production Access |
|------|-------------|-------------|-------------------|
| **Data Scientist** | Read model metadata | Read training data | No production access |
| **ML Engineer** | Read/Write model weights | Read/Write datasets | Limited production access |
| **Security Engineer** | Audit access | Audit access | Read-only monitoring |
| **DevOps** | Deploy models | No data access | Full production access |
| **Auditor** | Read all | Read all | Read all |

### 2. Least-Privilege Principles

| Principle | Implementation |
|-----------|---------------|
| **Need-to-know** | Access granted only for specific job function |
| **Just-in-time** | Temporary elevation for specific tasks |
| **Segregation** | Separate access for development and production |
| **Monitoring** | Log and audit all access |
| **Revocation** | Immediate access removal on role change |

### 3. Production Access Controls

| Control | Implementation |
|---------|---------------|
| **Authentication** | Multi-factor authentication for all access |
| **Authorization** | Policy-based access control |
| **Encryption** | Encrypt data at rest and in transit |
| **Network segmentation** | Isolate production from development |
| **API keys** | Scoped, rotated, audited API credentials |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Model and Data Inventory | Access controls based on inventory |
| Model and Data Integrity | Access for integrity verification |
| Secure-by-Default ML Tooling | Tool access controls |
| Application Access Management | Extend to model APIs |

## Testing Checklist

- [ ] Verify RBAC enforcement for all AI assets
- [ ] Test least-privilege access
- [ ] Validate just-in-time elevation
- [ ] Test access revocation procedures
- [ ] Audit access logs for anomalies
- [ ] Verify production isolation
- [ ] Test insider threat scenarios
- [ ] Validate encryption of stored assets

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
