---
name: saif-agent-security-guide
description: |
  Comprehensive guide to securing AI agent systems. Covers agent components
  (Application, Perception, Reasoning Core, Orchestration, Response Rendering),
  agent-specific risks, and multi-layered defense strategies. Use this skill when
  designing agent architectures, implementing agent security controls, or reviewing
  agentic system security.
trigger: |
  - When designing AI agent architectures
  - When implementing agent security controls
  - When reviewing agentic system security
  - When securing autonomous AI systems
  - When evaluating agent risks and mitigations
---

# SAIF Agent Security Guide

## Agent Components

Agentic systems differ from other AI systems in their **ability to take autonomous actions**. This guide extends the SAIF Risk Map to address the core operational components of agentic systems.

### 1. Application & Perception

| Component | Function | Security Challenge |
|-----------|----------|------------------|
| **Application** | Interface for collecting explicit user instructions and passively collected contextual data | Distinguishing trusted commands from untrusted information |
| **Perception** | Processing and understanding inputs before sending to reasoning core | Reliable separation of trusted user commands from untrusted data |

**Input types:**
- **Synchronous**: Direct typed commands
- **Asynchronous**: Auto-executed when specific events occur
- **Implicit contextual inputs**: Sensor readings, application state, recently opened documents

**Sub-components:**
- **System instructions**: Define capabilities, permissions, limitations; must be unambiguously separated from user data using special control tokens to prevent prompt injection
- **User queries**: Processed user requests combined with system instructions, memory, and external data into a single structured prompt

### 2. Reasoning Core

The core of an agent's functionality is its ability to reason about a user's goal and create a plan to achieve it.

**Key characteristics:**
- Processes system instructions, user queries, and contextual information
- Generates **tool calls** — actions that affect the real world
- Often iterative **"reasoning loop"** with plan refinement based on new information
- **Vulnerability to indirect prompt injection** through external data ingestion

**Autonomy spectrum:**
- Predefined workflow selection ←→ Dynamic multi-step orchestration

> "The more an agent can do on its own, the greater the risk from manipulation or misalignment, if the agent's actions do not have guardrails."

### 3. Orchestration

Managing and coordinating independent services and data sources to achieve complex tasks.

| Sub-component | Function | Key Security Risk |
|---------------|----------|-----------------|
| **Agent Memory** | Retain context and learn across interactions | Persistent attacks from malicious data; improper user isolation |
| **Tools** | External APIs/services for real-world action | Deceptive third-party descriptions; need least-privilege permissions |
| **Content (RAG)** | Curated knowledge for grounded responses | **Data poisoning** — corrupted knowledge sources |
| **Auxiliary Models** *(Optional)* | Supporting AI models (e.g., safety classifiers) | Supply chain vulnerabilities |

### 4. Response Rendering

This stage is a critical security boundary because it involves taking dynamic content from the agent and displaying it within the trusted context of a user's application.

**Critical vulnerability:** Agents often produce Markdown → interpreted by client applications

> "If this output isn't properly sanitized according to the content type, it can create severe vulnerabilities."

**Attack examples:** Data exfiltration, **cross-site scripting (XSS)**

## Agent-Specific Risks

### Sensitive Data Disclosure (SDD) in Agents

Agentic systems magnify this risk exponentially:
- Granted privileged access to user's email, files, or entire computer
- Potential to exfiltrate vast amounts of personal or corporate data
- Can use tools to leak data: creating documents, writing emails, URL leaks, markdown images

**Mitigation:** Multi-level controls — permissions, safe rendering, application-level confirmation warnings.

### Rogue Actions (RA)

Unintended actions executed by model-based agent:
- **Accidental**: Misalignment, mistakes in task planning/reasoning
- **Malicious**: Indirect prompt injection, poisoning, evasion, multi-agent hijacking

**Mitigation:** Multi-layered defense — input filtering, reasoning core hardening, orchestration governance, output sanitization.

### Insecure Integrated Components (IIC)

Vulnerabilities in software interacting with AI models:
- Manipulation of inputs to integrated components
- Manipulation of outputs from integrated components fed back to model
- Related to but distinct from Prompt Injection

## Multi-Layered Defense Strategy

### Layer 1: Input Protection
- Filter and standardize all inputs before they reach the model
- Define tool limitations in agent's system instructions
- Implement strict input validation and sanitization
- Use explicit delimiters between system instructions and user data

### Layer 2: Model Hardening
- Harden reasoning core with adversarial training
- Train model to recognize prompt injection attempts
- Implement safety classifiers for action validation
- Regular red team exercises targeting agent systems

### Layer 3: Orchestration Controls
- Govern agent capabilities with observability and policy engines
- Implement credentialed tool access (contextual agent security)
- Use reference monitors for dynamic permission adjustment
- Monitor agent memory for persistent attacks

### Layer 4: Output Protection
- Normalize and sanitize outputs during rendering
- Implement user-facing notifications before executing actions
- Require explicit user confirmation for state-changing operations
- Sanitize Markdown and other interpreted content

## Architecture Recommendations

### 1. Permission Model
- **Static permissions**: Define maximum allowed actions at design time
- **Dynamic permissions**: Adjust permissions based on current context and user intent
- **Reference monitors**: Enforce permission checks at runtime

### 2. Action Confirmation Pipeline
```
User Request → Agent Plans Action → Permission Check → User Confirmation → Execution → Audit Log
```

### 3. Multi-Agent Security
- **Authentication between agents**: Verify identity of communicating agents
- **Message integrity**: Cryptographic signatures on inter-agent messages
- **Isolation**: Sandbox agents to prevent lateral movement
- **Monitoring**: Detect anomalous inter-agent communication patterns

## Testing Checklist

- [ ] Test with ambiguous user requests
- [ ] Test indirect prompt injection via external data
- [ ] Test multi-agent hijacking scenarios
- [ ] Test dormant trigger activation
- [ ] Test time-based attack patterns
- [ ] Verify permission enforcement for all tools
- [ ] Verify user confirmation for state-changing actions
- [ ] Test observability and audit logging
- [ ] Test action rollback capabilities
- [ ] Test Markdown/XSS in agent outputs
- [ ] Test memory isolation between users/sessions

## References

- https://saif.google/focus-on-agents
- https://saif.google/secure-ai-framework
- https://storage.googleapis.com/gweb-research2023-media/pubtools/1018686.pdf (Agent Security White Paper)
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
