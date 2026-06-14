---
name: saif-control-training-data-management
description: |
  SAIF Control: Training Data Management. Ensure all data used to train and evaluate
  models is authorized for the intended purposes. Use this skill when implementing data
  governance, auditing training data provenance, or ensuring compliance with data
  licensing and consent requirements.
trigger: |
  - When implementing data governance for AI training
  - When auditing training data provenance
  - When ensuring data licensing compliance
  - When managing user consent for training data
  - When documenting data rights and restrictions
---

# SAIF Control: Training Data Management

## Control Overview

**Who can implement:** Model Creators

**Risk mapping:** Inferred Sensitive Data, Unauthorized Training Data

**Description:** Ensure that all data used to train and evaluate models is authorized for the intended purposes.

## Implementation Strategies

### 1. Data Provenance Tracking

| Element | Tracking Requirement |
|---------|-------------------|
| **Source** | Where data originated |
| **License** | Legal terms for data use |
| **Consent** | User consent for personal data |
| **Restrictions** | Any limitations on use |
| **Transformations** | All processing applied to data |
| **Lineage** | Complete chain from source to model |

### 2. Authorization Workflow

```
Data Source → License Review → Consent Verification → Approval → Ingestion → Training
```

| Step | Action | Verification |
|------|--------|-------------|
| License Review | Verify data license permits training use | Legal team sign-off |
| Consent Check | Confirm user consent for personal data | Consent database check |
| Restriction Check | Verify no usage restrictions violated | Automated policy check |
| Approval | Document authorization for training | Audit trail |
| Ingestion | Import approved data only | Gate on approval status |
| Training | Use only authorized data | Pre-training validation |

### 3. Data Cataloging

- Maintain inventory of all training data
- Document authorization status for each dataset
- Track data versions and updates
- Monitor for authorization changes
- Implement data retirement for expired authorizations

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Training Data Sanitization | Remove unauthorized data before training |
| User Data Management | Track consent for user data |
| Privacy Enhancing Technologies | Minimize PII in authorized data |
| Model and Data Inventory | Catalog all authorized data sources |

## Testing Checklist

- [ ] Verify all training data has documented authorization
- [ ] Test license compliance checking
- [ ] Validate consent tracking for user data
- [ ] Audit data provenance records
- [ ] Test unauthorized data detection
- [ ] Verify authorization workflow enforcement
- [ ] Test data retirement for expired licenses
- [ ] Monitor for authorization changes

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
