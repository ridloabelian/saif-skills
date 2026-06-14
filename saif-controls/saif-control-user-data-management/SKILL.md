---
name: saif-control-user-data-management
description: |
  SAIF Control: User Data Management. Store, process, and use all user data (e.g.
  prompts and logs) from AI applications in compliance with user consent. Covers
  data retention, consent management, and secure deletion. Use this skill when
  implementing data lifecycle management, designing consent workflows, or ensuring
  regulatory compliance for user data.
trigger: |
  - When implementing data lifecycle management for AI
  - When designing user consent workflows
  - When ensuring GDPR/CCPA compliance for user data
  - When implementing data retention policies
  - When designing secure data deletion
---

# SAIF Control: User Data Management

## Control Overview

**Who can implement:** Model Creators, Model Consumers

**Risk mapping:** Sensitive Data Disclosure, Excessive Data Handling

**Description:** Store, process, and use all user data (e.g. prompts and logs) from AI applications in compliance with user consent.

## Implementation Strategies

### 1. Consent Management

| Consent Element | Implementation |
|----------------|---------------|
| **Collection consent** | Explicit opt-in for data collection |
| **Use consent** | Clear terms for how data will be used |
| **Retention consent** | User controls for data retention periods |
| **Sharing consent** | Approval for third-party data sharing |
| **Withdrawal** | Easy mechanism to revoke consent |

### 2. Data Retention

| Stage | Action | Timeline |
|-------|--------|----------|
| **Active use** | Data available for model inference | Duration of session |
| **Short-term storage** | Retained for quality improvement | 30-90 days |
| **Long-term storage** | Retained for model retraining | Per policy |
| **Archival** | Compressed storage for compliance | Per regulation |
| **Deletion** | Secure removal from all systems | Upon request or expiry |

### 3. Secure Deletion

| Method | Use Case |
|--------|----------|
| **Cryptographic erasure** | Encrypt data, destroy key |
| **Overwriting** | Multiple-pass overwrite for storage media |
| **Secure erase commands** | Use hardware secure erase features |
| **Degaussing** | Magnetic media destruction |
| **Physical destruction** | Storage media shredding |

### 4. Access Logging

- Log all access to user data
- Monitor for unauthorized access
- Audit data usage patterns
- Alert on anomalous access

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Privacy Enhancing Technologies | Minimize PII in stored user data |
| Output Validation | Ensure logs don't capture sensitive outputs |
| Training Data Sanitization | Remove user data from training datasets |
| Application Access Management | Control who can access user data |

## Testing Checklist

- [ ] Verify consent collection for all user data
- [ ] Test consent withdrawal mechanisms
- [ ] Validate data retention period enforcement
- [ ] Test secure deletion procedures
- [ ] Audit access logs for user data
- [ ] Verify compliance with GDPR/CCPA requirements
- [ ] Test data portability (export user data)
- [ ] Monitor for unauthorized data retention

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
