---
name: saif-control-model-data-inventory
description: |
  SAIF Control: Model and Data Inventory Management. Ensure all data, code, models,
  and transformation tools used in AI applications are inventoried and tracked.
  Covers asset management, lineage tracking, and supply chain visibility. Use this
  skill when implementing ML asset management, tracking model lineage, or auditing
  AI supply chains.
trigger: |
  - When implementing ML asset management
  - When tracking model lineage and provenance
  - When auditing AI supply chains
  - When managing model versions
  - When tracking data transformations
---

# SAIF Control: Model and Data Inventory Management

## Control Overview

**Who can implement:** Model Creators, Model Consumers (if storing models)

**Risk mapping:** Data Poisoning, Model Source Tampering, Model Exfiltration

**Description:** Ensure that all data, code, models, and transformation tools used in AI applications are inventoried and tracked.

## Implementation Strategies

### 1. Asset Inventory

| Asset Type | Inventory Elements |
|-----------|-------------------|
| **Models** | Version, architecture, weights, training data, metrics, deployment status |
| **Datasets** | Source, license, size, schema, transformations, quality metrics |
| **Code** | Repository, version, dependencies, build artifacts, vulnerabilities |
| **Tools** | Name, version, vendor, security status, configuration |
| **Environments** | Infrastructure, platform, security controls, access policies |

### 2. Lineage Tracking

```
Data Source → Ingestion → Processing → Training → Evaluation → Deployment → Monitoring
```

| Stage | Tracking Information |
|-------|---------------------|
| Data Source | Origin, license, consent, timestamp |
| Ingestion | Pipeline version, operator, validation results |
| Processing | Transformations, filters, augmentations |
| Training | Hyperparameters, hardware, duration, checkpoints |
| Evaluation | Metrics, test data, comparison baseline |
| Deployment | Target environment, approval, rollout strategy |
| Monitoring | Performance, drift, incidents, updates |

### 3. Supply Chain Visibility

- Track all dependencies (direct and transitive)
- Monitor for vulnerability disclosures
- Verify integrity of all components
- Document provenance for audit

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Model and Data Access Control | Inventory informs access policies |
| Model and Data Integrity | Inventory verifies integrity status |
| Secure-by-Default ML Tooling | Inventory tracks tool security |
| Training Data Management | Inventory documents data authorization |

## Testing Checklist

- [ ] Verify completeness of asset inventory
- [ ] Test lineage tracking accuracy
- [ ] Validate supply chain visibility
- [ ] Test dependency vulnerability monitoring
- [ ] Verify inventory integration with CI/CD
- [ ] Audit inventory accuracy
- [ ] Test asset discovery for shadow assets
- [ ] Verify inventory-based access control

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
