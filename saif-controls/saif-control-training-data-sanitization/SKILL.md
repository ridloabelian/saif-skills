---
name: saif-control-training-data-sanitization
description: |
  SAIF Control: Training Data Sanitization. Detect and remove or remediate poisoned or
  sensitive data in training and evaluation datasets. Use this skill when implementing
  data cleaning pipelines, detecting anomalous training data, or removing sensitive
  information before model training.
trigger: |
  - When implementing data cleaning pipelines
  - When detecting anomalous training data
  - When removing sensitive information before training
  - When auditing training data quality
  - When implementing automated data filtering
---

# SAIF Control: Training Data Sanitization

## Control Overview

**Who can implement:** Model Creators

**Risk mapping:** Data Poisoning, Unauthorized Training Data

**Description:** Detect and remove or remediate poisoned or sensitive data in training and evaluation.

## Implementation Strategies

### 1. Poisoned Data Detection

| Detection Method | Implementation |
|-----------------|---------------|
| **Statistical anomaly detection** | Identify outliers in data distributions |
| **Label consistency checking** | Verify labels match content |
| **Duplicate detection** | Find near-duplicate injections |
| **Adversarial pattern scanning** | Detect known poisoning patterns |
| **Behavioral analysis** | Compare against expected data characteristics |

### 2. Sensitive Data Removal

| Data Type | Removal Strategy |
|-----------|-----------------|
| **PII** | Automated PII detection and redaction |
| **Credentials** | Pattern matching for passwords, keys, tokens |
| **Proprietary code** | Code similarity detection |
| **Financial data** | Regex and ML-based detection |
| **Health records** | HIPAA pattern detection |

### 3. Data Remediation Pipeline

```
Raw Data → Anomaly Detection → Sensitive Data Scan → Poisoning Check → Clean Data → Training
```

| Stage | Action | Output |
|-------|--------|--------|
| Anomaly Detection | Flag statistical outliers | Anomaly report |
| Sensitive Data Scan | Detect and remove PII/sensitive content | Sanitized data |
| Poisoning Check | Verify data integrity | Poisoning report |
| Quality Validation | Check data quality metrics | Quality score |
| Approval | Human review for flagged items | Approved dataset |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Training Data Management | Only sanitize authorized data |
| Privacy Enhancing Technologies | Apply differential privacy after sanitization |
| Model and Data Integrity | Verify sanitized data integrity |
| User Data Management | Ensure user data properly sanitized |

## Testing Checklist

- [ ] Test anomaly detection with known poisoned samples
- [ ] Verify PII removal effectiveness
- [ ] Test sensitive data detection accuracy
- [ ] Validate poisoned data detection rate
- [ ] Test false positive rate for sanitization
- [ ] Verify data quality after sanitization
- [ ] Test automated vs. manual review balance
- [ ] Monitor for novel poisoning techniques

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
