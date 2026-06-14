---
name: saif-control-threat-detection
description: |
  SAIF Control: Threat Detection. Detect and alert on internal or external attacks on AI
  assets, infrastructure, and products. Covers monitoring, alerting, and anomaly detection.
  Use this skill when implementing security monitoring, designing alert systems, or building
  AI-specific threat detection.
trigger: |
  - When implementing security monitoring for AI systems
  - When designing alert systems for AI threats
  - When building AI-specific threat detection
  - When monitoring for anomalous AI behavior
  - When investigating AI security incidents
---

# SAIF Control: Threat Detection

## Control Overview

**Who can implement:** Model Creators, Model Consumers

**Risk mapping:** All risks

**Description:** Detect and alert on internal or external attacks on AI assets, infrastructure, and products.

## Implementation Strategies

### 1. Monitoring

| Monitor Type | Data Source | Detection Target |
|-------------|-------------|-----------------|
| **Model API monitoring** | API logs | Anomalous queries, extraction attempts |
| **Infrastructure monitoring** | System logs | Unauthorized access, resource abuse |
| **Data access monitoring** | Access logs | Unauthorized data access |
| **Model behavior monitoring** | Model outputs | Output drift, quality degradation |
| **User behavior monitoring** | User activity | Account compromise, insider threats |

### 2. Alerting

| Alert Type | Trigger | Response |
|-----------|---------|----------|
| **Rate limit exceeded** | API calls above threshold | Block and investigate |
| **Anomalous query pattern** | Unusual input patterns | Flag for review |
| **Model output anomaly** | Unexpected output quality | Pause and evaluate |
| **Unauthorized access** | Access from unknown source | Block and alert |
| **Data exfiltration** | Large data transfers | Block and investigate |

### 3. Anomaly Detection

| Technique | Application | Implementation |
|-----------|-------------|---------------|
| **Statistical** | Baseline deviation | Z-score, IQR |
| **Machine learning** | Pattern-based | Isolation forest, autoencoders |
| **Rule-based** | Known attack patterns | Signature detection |
| **Behavioral** | User/agent behavior | Baseline profiling |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Incident Response | Trigger response on detection |
| Vulnerability Management | Detect exploitation of known vulnerabilities |
| Red Teaming | Validate detection effectiveness |
| Application Access Management | Monitor access anomalies |

## Testing Checklist

- [ ] Test detection of known attack patterns
- [ ] Validate alert accuracy and timeliness
- [ ] Test false positive rate
- [ ] Verify incident response integration
- [ ] Test anomaly detection with synthetic data
- [ ] Monitor detection coverage gaps
- [ ] Validate alert escalation procedures
- [ ] Test detection of novel attacks

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
