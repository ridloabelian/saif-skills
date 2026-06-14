---
name: saif-control-agent-permissions
description: |
  SAIF Control: Agent Permissions. Use least-privilege principle as the upper bound
  on agentic system permissions. Minimize tools and actions an agent can access.
  Contextual and dynamic permissions adapting to user query and trusted context.
  Use this skill when designing agent permission models, implementing least-privilege
  for AI agents, or securing agent tool access.
trigger: |
  - When designing agent permission models
  - When implementing least-privilege for AI agents
  - When securing agent tool access
  - When reviewing agent capabilities and blast radius
  - When implementing contextual security for agents
---

# SAIF Control: Agent Permissions

## Control Overview

**Who can implement:** Model Consumers

**Risk mapping:** Insecure Integrated Component, Sensitive Data Disclosure, Rogue Actions

**Description:** Use least-privilege principle as the upper bound on agentic system permissions to minimize the number of tools that an agent is permitted to interact with and the actions it is allowed to take. An agentic system's use of privileges should be contextual and dynamic, adapting to the specific user query and trusted contextual information.

## Core Principles

### 1. Least Privilege

Agents should only have access to the minimum set of tools and data required for their current task.

| Permission Aspect | Implementation |
|------------------|---------------|
| **Tool access** | Only register tools the agent needs for its defined purpose |
| **Data access** | Limit data sources the agent can read from |
| **Action scope** | Restrict state-changing vs. read-only operations |
| **Network access** | Limit external APIs and services the agent can call |

### 2. Contextual Permissions

Permissions should adapt based on current context:

```python
# Example: Contextual permission model
class AgentPermission:
    def __init__(self, base_permissions):
        self.base = base_permissions
        self.contextual = {}
    
    def adjust_for_query(self, user_query, trusted_context):
        # Dynamically adjust permissions based on query and context
        if "email" in user_query and trusted_context.get("email_access"):
            return self.base + ["email_read", "email_send"]
        return self.base
```

| Context Factor | Permission Adjustment |
|----------------|----------------------|
| User identity | Different users get different permission sets |
| Query intent | Permissions adjusted based on what user is asking |
| Data sensitivity | Higher sensitivity = stricter permissions |
| Time/location | Permissions may vary by time or location |
| Historical trust | Established trust patterns may relax permissions |

### 3. Dynamic Permission Adjustment

Permissions should change during execution based on runtime conditions:

| Trigger | Action |
|---------|--------|
| User escalation | User explicitly requests higher permissions |
| Anomaly detected | Permissions reduced when suspicious behavior detected |
| Task completion | Permissions revoked after task completes |
| Session timeout | All permissions expire after time limit |

## Implementation Strategies

### 1. Permission Model Design

```
Permission Hierarchy:
├── System Level (what agent CANNOT do)
│   ├── Blocked tools
│   ├── Blocked APIs
│   └── Blocked data sources
│
├── User Level (what user ALLOWS)
│   ├── Explicitly granted tools
│   ├── Data access approvals
│   └── Action confirmations
│
└── Context Level (what query REQUIRES)
    ├── Tools needed for current task
    ├── Data sources relevant to query
    └── Actions implied by user intent
```

### 2. Reference Monitor Pattern

Implement a reference monitor that enforces permissions at runtime:

```python
class ReferenceMonitor:
    def check_permission(self, agent, action, resource):
        # Check if agent has permission for action on resource
        permissions = agent.get_contextual_permissions()
        
        if action not in permissions.get(resource, []):
            raise PermissionDenied(f"Agent cannot {action} on {resource}")
        
        # Log the access for audit
        self.audit_log.record(agent, action, resource)
        return True
```

### 3. Tool Registration and Validation

| Step | Implementation |
|------|---------------|
| Tool registration | Each tool must be explicitly registered with agent |
| Tool validation | Validate tool integrity before registration |
| Tool sandboxing | Run tools in isolated environments |
| Tool monitoring | Monitor tool usage for anomalies |

## Permission Categories

### Data Access Permissions

| Level | Access | Example |
|-------|--------|---------|
| **None** | No data access | Agent cannot access any user data |
| **Read-only** | Can read but not modify | Agent can read emails but not send |
| **Write-own** | Can modify agent-created data | Agent can update its own notes |
| **Write-limited** | Can modify specific data types | Agent can update calendar events |
| **Full** | Complete access | Agent can read/write all data (rarely appropriate) |

### Action Permissions

| Action Type | Risk Level | Typical Restriction |
|-------------|-----------|-------------------|
| **Read** | Low | Generally allowed with appropriate data access |
| **Search** | Low | Allowed within permitted data sources |
| **Create** | Medium | Requires user confirmation for external-facing content |
| **Update** | Medium | Requires user confirmation for existing data |
| **Delete** | High | Requires explicit user confirmation |
| **Send/Share** | High | Requires explicit user confirmation |
| **Execute code** | Critical | Requires explicit approval, sandboxed environment |
| **Financial** | Critical | Requires multi-factor confirmation |

## Multi-Agent Permission Coordination

When multiple agents interact:

| Challenge | Solution |
|-----------|----------|
| **Permission escalation** | Agent A cannot grant permissions to Agent B that A doesn't have |
| **Transitive permissions** | Track permission flow across agent chains |
| **Conflicting permissions** | Resolve conflicts with most restrictive wins |
| **Permission revocation** | Cascade revocation when parent agent permissions change |

## Testing Checklist

- [ ] Verify agent cannot access unregistered tools
- [ ] Test permission escalation attempts
- [ ] Verify contextual permission adjustment works correctly
- [ ] Test permission revocation on session timeout
- [ ] Verify audit logging captures all permission checks
- [ ] Test multi-agent permission coordination
- [ ] Verify most restrictive permission wins in conflicts
- [ ] Test permission boundaries with adversarial queries

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Agent User Control | Permissions define what agent CAN do; user control confirms what it SHOULD do |
| Agent Observability | Permission checks logged for audit and debugging |
| Output Validation | Permission enforcement prevents unauthorized output actions |
| Application Access Management | Rate limiting and access controls complement permission model |

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://saif.google/focus-on-agents
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
