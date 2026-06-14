---
name: saif-risk-model-deployment-tampering
description: |
  SAIF Risk: Model Deployment Tampering (MDT). Unauthorized modification of components
  used for deploying a model, whether by tampering with source code supply chain or
  exploiting vulnerabilities in serving tools. Covers candidate model modification and
  serving infrastructure compromise. Use this skill when securing deployment pipelines,
  hardening serving infrastructure, or implementing deployment controls.
trigger: |
  - When securing model deployment pipelines
  - When hardening model serving infrastructure
  - When implementing deployment controls
  - When evaluating serving tool vulnerabilities
  - When protecting production model integrity
---

# SAIF Risk: Model Deployment Tampering (MDT)

## Risk Overview

**Who can mitigate:** Model Creators, Model Consumers

**Description:** Unauthorized modification of components used for deploying a model, whether by tampering with the source code supply chain or exploiting known vulnerabilities in common tools.

Such modifications can result in changes to model behavior.

## Types of Deployment Tampering

### 1. Candidate Model Modification
- Attacker modifies deployment workflow or processes
- Maliciously alters how model operates post-deployment
- Changes model behavior without changing model weights

### 2. Serving Infrastructure Compromise
- Exploiting vulnerabilities in model serving tools
- Example: PyTorch models vulnerable to remote code execution due to critical security flaws in TorchServe
- Attack on serving infrastructure vs. supply chain attack on dependency code

## When Risk is Introduced

The risk is introduced within:
- Model serving components
- Deployment pipelines
- Serving infrastructure when vulnerable to manipulation

## When Risk is Exposed

This risk is exposed if attackers:
- Tamper with production models within model serving component
- Modify deployment workflows
- Exploit serving infrastructure vulnerabilities

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Secure-by-Default ML Tooling** | Harden model serving infrastructure with secure-by-default tooling |

### Implementation Strategies

1. **Deployment Pipeline Security**
   - Sign all deployment artifacts
   - Verify integrity before deployment
   - Implement deployment approval workflows
   - Audit all deployment changes

2. **Serving Infrastructure Hardening**
   - Use latest secure versions of serving tools
   - Implement network segmentation
   - Monitor for anomalous serving behavior
   - Regular vulnerability scanning

3. **Runtime Protection**
   - Detect model behavior drift
   - Implement model versioning and rollback
   - Monitor for unauthorized model modifications
   - Alert on serving anomalies

## Real-World Examples

- **HuggingFace shared infrastructure:** Researchers discovered models on HuggingFace were using shared infrastructure for inference, allowing a malicious model to tamper with any other model

## Testing Checklist

- [ ] Verify deployment artifact signatures
- [ ] Test serving infrastructure for known vulnerabilities
- [ ] Monitor for model behavior drift post-deployment
- [ ] Test deployment rollback procedures
- [ ] Audit deployment pipeline access
- [ ] Verify network segmentation of serving infrastructure
- [ ] Test for candidate model modification attacks
- [ ] Implement serving anomaly detection

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
