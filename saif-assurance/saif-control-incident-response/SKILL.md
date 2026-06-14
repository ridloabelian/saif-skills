---
name: saif-control-incident-response
description: |
  SAIF Control: Incident Response Management. Manage response to AI security and privacy
  incidents. Covers preparation, detection, containment, eradication, recovery, and
  lessons learned. Use this skill when preparing for AI security incidents, responding
  to breaches, or improving incident response capabilities.
trigger: |
  - When preparing for AI security incidents
  - When responding to AI security breaches
  - When improving incident response capabilities
  - When conducting incident response drills
  - When documenting AI incident procedures
---

# SAIF Control: Incident Response Management

## Control Overview

**Who can implement:** Model Creators, Model Consumers

**Risk mapping:** All risks

**Description:** Manage response to AI security and privacy incidents.

## Implementation Strategies

### 1. Preparation

| Element | Implementation |
|---------|---------------|
| **Playbooks** | Pre-defined response procedures for common incidents |
| **Team** | Trained incident response team with AI expertise |
| **Tools** | Forensic tools, communication platforms, evidence collection |
| **Contacts** | Stakeholder notification list |
| **Training** | Regular drills and tabletop exercises |

### 2. Response Phases

| Phase | Actions | Timeline |
|-------|---------|----------|
| **Detection** | Identify and validate incident | Minutes |
| **Containment** | Limit impact, preserve evidence | Hours |
| **Eradication** | Remove threat, fix vulnerabilities | Days |
| **Recovery** | Restore systems, verify integrity | Days |
| **Lessons learned** | Document, improve, share | Weeks |

### 3. AI-Specific Considerations

| Consideration | Action |
|-------------|--------|
| **Model rollback** | Restore previous model version |
| **Data contamination** | Identify and remove poisoned data |
| **Output audit** | Review all outputs during incident window |
| **User notification** | Notify affected users |
| **Regulatory reporting** | Report to relevant authorities |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Threat Detection | Trigger incident response |
| Vulnerability Management | Fix vulnerabilities post-incident |
| Red Teaming | Prepare for incident types |
| Agent Observability | Use logs for investigation |

## Testing Checklist

- [ ] Conduct tabletop exercises
- [ ] Test communication channels
- [ ] Validate evidence collection procedures
- [ ] Test model rollback capabilities
- [ ] Verify stakeholder notification
- [ ] Test containment procedures
- [ ] Validate recovery procedures
- [ ] Document lessons learned

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
