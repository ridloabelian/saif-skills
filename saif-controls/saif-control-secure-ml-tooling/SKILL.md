---
name: saif-control-secure-ml-tooling
description: |
  SAIF Control: Secure-by-Default ML Tooling. Use secure-by-default frameworks,
  libraries, software systems, and hardware components for AI development or deployment
  to protect confidentiality and integrity of AI assets and outputs. Use this skill
  when selecting ML tools, evaluating framework security, or hardening ML infrastructure.
trigger: |
  - When selecting ML frameworks and libraries
  - When evaluating framework security posture
  - When hardening ML development infrastructure
  - When implementing secure model serving
  - When securing ML hardware components
---

# SAIF Control: Secure-by-Default ML Tooling

## Control Overview

**Who can implement:** Model Creators, Model Consumers (if storing models)

**Risk mapping:** Data Poisoning, Model Source Tampering, Model Exfiltration, Model Deployment Tampering

**Description:** Use secure-by-default frameworks, libraries, software systems, and hardware components for AI development or deployment to protect confidentiality and integrity of AI assets and outputs.

## Implementation Strategies

### 1. Framework Selection

| Criteria | Evaluation |
|----------|-----------|
| **Security history** | Track record of vulnerability handling |
| **Update frequency** | Regular security patches |
| **Community** | Active security community |
| **Audits** | Third-party security audits |
| **Defaults** | Secure-by-default configurations |

### 2. Secure Configuration

| Component | Secure Default |
|-----------|---------------|
| **Training frameworks** | Disable unnecessary features, enable logging |
| **Model serving** | Authentication required, rate limiting enabled |
| **Data pipelines** | Encryption at rest and in transit |
| **Development environments** | Isolated, monitored, minimal privileges |
| **Hardware accelerators** | Secure boot, encrypted memory |

### 3. Dependency Management

| Practice | Implementation |
|----------|---------------|
| **SBOM** | Maintain software bill of materials |
| **Vulnerability scanning** | Automated scanning of dependencies |
| **Pin versions** | Use exact versions, not ranges |
| **Private registry** | Internal registry for approved packages |
| **Regular updates** | Scheduled security updates |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Model and Data Integrity | Verify tool integrity |
| Model and Data Access Control | Tool access permissions |
| Training Data Sanitization | Use secure tools for data processing |
| Application Access Management | Secure serving tools |

## Testing Checklist

- [ ] Audit framework security configuration
- [ ] Verify dependency vulnerability scanning
- [ ] Test secure default settings
- [ ] Validate SBOM completeness
- [ ] Test tool access controls
- [ ] Monitor for tool security advisories
- [ ] Verify secure update process
- [ ] Test tool isolation in development

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
