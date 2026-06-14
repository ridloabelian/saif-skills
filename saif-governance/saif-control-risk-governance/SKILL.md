---
name: saif-control-risk-governance
description: |
  SAIF Control: Risk Governance. Inventory, measure, and monitor residual risk to AI in
  your organization. Covers risk assessment, risk metrics, and risk monitoring. Use this
  skill when assessing AI risks, establishing risk metrics, or implementing risk
  monitoring programs.
trigger: |
  - When assessing AI risks in your organization
  - When establishing risk metrics and KPIs
  - When implementing risk monitoring programs
  - When conducting risk assessments
  - When reporting AI risk to leadership
---

# SAIF Control: Risk Governance

## Control Overview

**Who can implement:** Model Creators, Model Consumers

**Risk mapping:** All risks

**Description:** Inventory, measure, and monitor residual risk to AI in your organization.

## Implementation Strategies

### 1. Risk Inventory

| Risk Category | Examples | Owner |
|--------------|----------|-------|
| **Technical** | Model evasion, prompt injection | Engineering |
| **Operational** | Data poisoning, deployment tampering | Operations |
| **Legal** | Unauthorized training data, excessive data handling | Legal |
| **Reputational** | Insecure model output, sensitive data disclosure | Communications |
| **Financial** | Model exfiltration, denial of service | Finance |

### 2. Risk Metrics

| Metric | Calculation | Target |
|--------|-------------|--------|
| **Risk score** | Likelihood × Impact | < High |
| **Control coverage** | Controls implemented / Total needed | > 90% |
| **Mean time to remediate** | Time from detection to fix | < 30 days |
| **Vulnerability density** | Vulnerabilities / Model | Decreasing |
| **Incident frequency** | Incidents / Quarter | Decreasing |

### 3. Risk Monitoring

| Activity | Frequency | Output |
|----------|-----------|--------|
| **Risk assessment** | Quarterly | Updated risk register |
| **Control testing** | Monthly | Control effectiveness report |
| **Incident analysis** | Per incident | Lessons learned |
| **Threat intelligence** | Continuous | Threat landscape update |
| **Benchmarking** | Annually | Industry comparison |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Product Governance | Risk assessment informs product requirements |
| Internal Policies | Policies define risk appetite |
| Incident Response | Incidents update risk register |
| Vulnerability Management | Vulnerabilities feed risk metrics |

## Testing Checklist

- [ ] Verify completeness of risk inventory
- [ ] Validate risk scoring methodology
- [ ] Test risk monitoring automation
- [ ] Audit risk metric accuracy
- [ ] Test risk reporting to leadership
- [ ] Verify risk assessment coverage
- [ ] Validate control effectiveness measurement
- [ ] Test risk response procedures

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
