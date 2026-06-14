---
name: saif-control-agent-user-control
description: |
  SAIF Control: Agent User Control. Ensure user approval for any actions performed by
  agents/plugins that alter user data or act on the user's behalf. Covers confirmation
  dialogs, action review, and user override mechanisms. Use this skill when designing
  agent interaction flows, implementing user confirmation systems, or securing agent
  actions.
trigger: |
  - When designing agent interaction flows
  - When implementing user confirmation systems
  - When securing agent actions with user oversight
  - When building agent approval workflows
  - When creating agent safety mechanisms
---

# SAIF Control: Agent User Control

## Control Overview

**Who can implement:** Model Consumers

**Risk mapping:** Sensitive Data Disclosure, Rogue Actions

**Description:** Ensure user approval for any actions performed by agents/plugins that alter user data or act on the user's behalf.

## Implementation Strategies

### 1. Action Classification

| Action Type | Risk Level | User Control |
|-------------|-----------|-------------|
| **Read** | Low | No confirmation needed |
| **Search** | Low | No confirmation needed |
| **Create draft** | Medium | Optional confirmation |
| **Send message** | High | Required confirmation |
| **Delete data** | High | Required confirmation |
| **Financial transaction** | Critical | Multi-factor confirmation |
| **Access external system** | High | Required confirmation |
| **Execute code** | Critical | Explicit approval + sandbox |

### 2. Confirmation Design

| Element | Implementation |
|---------|---------------|
| **Clarity** | Clear description of action |
| **Context** | Show what data will be affected |
| **Reversibility** | Indicate if action can be undone |
| **Timing** | Allow sufficient time for review |
| **Accessibility** | Support for all users |

### 3. User Override

| Scenario | Override Mechanism |
|----------|-------------------|
| **Emergency** | Break-glass procedures |
| **Batch actions** | Bulk approval with review |
| **Trusted agents** | Pre-approved actions with audit |
| **Learning** | Agent learns preferences over time |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Agent Permissions | Permissions define what CAN be done; user control confirms what SHOULD be done |
| Agent Observability | Log user approvals and rejections |
| Output Validation | Validate actions before user confirmation |
| Application Access Management | Authenticate user before confirmation |

## Testing Checklist

- [ ] Test confirmation for all high-risk actions
- [ ] Verify clarity of action descriptions
- [ ] Test override mechanisms
- [ ] Validate accessibility of confirmation UI
- [ ] Test batch approval workflows
- [ ] Monitor user approval patterns
- [ ] Verify audit logging of decisions
- [ ] Test emergency override procedures

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://saif.google/focus-on-agents
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
