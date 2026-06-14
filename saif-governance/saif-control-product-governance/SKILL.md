---
name: saif-control-product-governance
description: |
  SAIF Control: Product Governance. Validate that all AI models and products meet the
  established security and privacy requirements. Covers security reviews, compliance
  checks, and release gates. Use this skill when conducting security reviews, implementing
  release gates, or validating AI product security.
trigger: |
  - When conducting security reviews of AI products
  - When implementing release gates for AI models
  - When validating AI product security
  - When establishing product security requirements
  - When reviewing AI product compliance
---

# SAIF Control: Product Governance

## Control Overview

**Who can implement:** Model Creators, Model Consumers

**Risk mapping:** All risks

**Description:** Validate that all AI models and products meet the established security and privacy requirements.

## Implementation Strategies

### 1. Security Review Process

| Review Stage | Activities | Exit Criteria |
|-------------|----------|--------------|
| **Design review** | Threat modeling, architecture review | Approved threat model |
| **Development review** | Code review, security testing | No critical findings |
| **Pre-release review** | Penetration testing, red teaming | All findings remediated |
| **Post-release review** | Monitoring, incident analysis | No active incidents |

### 2. Release Gates

| Gate | Check | Approval |
|------|-------|----------|
| **Security scan** | No critical vulnerabilities | Security team |
| **Privacy review** | Privacy requirements met | Privacy team |
| **Compliance check** | Regulatory requirements met | Legal team |
| **Performance test** | Model meets performance SLAs | Engineering |
| **Safety test** | Model passes safety benchmarks | Safety team |
| **Documentation** | Security docs complete | Technical writers |

### 3. Continuous Validation

| Activity | Frequency | Owner |
|----------|-----------|-------|
| **Security monitoring** | Continuous | Security operations |
| **Vulnerability scanning** | Weekly | Security engineering |
| **Penetration testing** | Quarterly | Red team |
| **Compliance audit** | Annually | Compliance |
| **Safety evaluation** | Per release | Safety team |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Risk Governance | Product risk assessment |
| Internal Policies | Policies define review requirements |
| User Policies | Product meets user-facing requirements |
| Vulnerability Management | Continuous scanning post-release |

## Testing Checklist

- [ ] Verify security review coverage
- [ ] Test release gate enforcement
- [ ] Validate continuous monitoring
- [ ] Audit review documentation
- [ ] Test emergency release procedures
- [ ] Measure time-to-review metrics
- [ ] Validate gate bypass controls
- [ ] Test cross-functional review coordination

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
