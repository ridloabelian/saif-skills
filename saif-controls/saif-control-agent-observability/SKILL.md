---
name: saif-control-agent-observability
description: |
  SAIF Control: Agent Observability. Ensure an agent's actions, tool use, and reasoning
  are transparent and auditable through logging, allowing for debugging, security oversight,
  and user insights into agent activity. Covers logging, monitoring, and audit trails.
  Use this skill when implementing agent monitoring, designing audit systems, or building
  agent transparency features.
trigger: |
  - When implementing agent monitoring systems
  1.  When designing audit trails for agent actions
  - When building agent transparency features
  - When debugging agent behavior
  - When investigating agent security incidents
---

# SAIF Control: Agent Observability

## Control Overview

**Who can implement:** Model Consumers

**Risk mapping:** Sensitive Data Disclosure, Rogue Actions

**Description:** Ensure an agent's actions, tool use, and reasoning are transparent and auditable through logging, allowing for debugging, security oversight, and user insights into agent activity.

## Implementation Strategies

### 1. Action Logging

| Log Element | Content | Purpose |
|-------------|---------|---------|
| **Agent identity** | Unique agent ID, version | Attribution |
| **User context** | User ID, session, intent | Context |
| **Action details** | Tool, parameters, result | Accountability |
| **Reasoning** | Plan, decision rationale | Debugging |
| **Timestamp** | When action occurred | Timeline |
| **Outcome** | Success, failure, error | Monitoring |

### 2. Tool Use Monitoring

| Metric | Tracking | Alert |
|--------|----------|-------|
| **Tool frequency** | How often each tool is used | Anomaly detection |
| **Tool sequence** | Order of tool invocations | Pattern analysis |
| **Tool success rate** | Percentage of successful calls | Quality monitoring |
| **Tool errors** | Failed tool invocations | Error tracking |
| **Tool latency** | Response time per tool | Performance |

### 3. Audit Trail

```
User Request → Intent Analysis → Plan Generation → Tool Selection → Execution → Result → User Delivery
```

| Stage | Audit Record |
|-------|-------------|
| User Request | Original query, user identity |
| Intent Analysis | Parsed intent, confidence |
| Plan Generation | Step-by-step plan, reasoning |
| Tool Selection | Selected tools, justification |
| Execution | Tool calls, parameters, results |
| Result | Output, validation status |
| User Delivery | Final response, user feedback |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Agent Permissions | Log permission checks |
| Agent User Control | Log user approvals and rejections |
| Output Validation | Log validation decisions |
| Application Access Management | Log access events |

## Testing Checklist

- [ ] Verify completeness of action logs
- [ ] Test audit trail reconstruction
- [ ] Validate log integrity and tamper protection
- [ ] Test log analysis for anomaly detection
- [ ] Verify user-facing audit views
- [ ] Test log retention policies
- [ ] Validate privacy in logging (no PII in logs)
- [ ] Test incident investigation workflow

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://saif.google/focus-on-agents
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
