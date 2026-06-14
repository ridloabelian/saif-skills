---
name: saif-risk-insecure-integrated-component
description: |
  SAIF Risk: Insecure Integrated Component (IIC). Vulnerabilities in software interacting
  with AI models (plugins, libraries, applications) that can be leveraged by attackers to
  gain unauthorized access, introduce malicious code, or compromise system operations.
  Covers input/output manipulation and plugin security. Use this skill when securing AI
  integrations, reviewing plugin security, or hardening application interfaces.
trigger: |
  - When securing AI integrations and plugins
  - When reviewing plugin security architecture
  - When hardening application interfaces
  - When evaluating third-party AI components
  - When testing for indirect prompt injection via integrations
---

# SAIF Risk: Insecure Integrated Component (IIC)

## Risk Overview

**Who can mitigate:** Model Consumers

**Description:** Vulnerabilities in software interacting with AI models, such as a plugin, library, or application, that can be leveraged by attackers to gain unauthorized access to models, introduce malicious code, or compromise system operations.

Given the level of autonomy expected to be granted to agents and applications, insecure integrated components represent a broad swath of threats to user trust and safety, privacy and security concerns, and ethical and legal challenges.

## Attack Vectors

### 1. Input Manipulation
- Manipulation of model output to include malicious instructions fed as input to integrated component
- Plugin accepts freeform text instead of structured and validated input
- Plugin accepts input without authentication and authorization
- Trusts input as coming from authorized user

### 2. Output Manipulation
- Manipulation of output from integrated component fed as input to model
- Plugin calls other systems (especially 3rd party services) and uses content to construct input to model
- Opens potential for indirect prompt injection
- Similar case for integrated application calling another service

### 3. Plugin Vulnerabilities
- Malicious plugins uploaded to plugin stores
- Compromised plugins with backdoors
- Insufficient plugin sandboxing
- Overly permissive plugin capabilities

## Relationship to Prompt Injection

**Related but different:**
- Attacks exploiting IIC often involve prompt injection
- Can also be done via Poisoning and Evasion
- Prompt injection is possible even when integrated components are secure
- IIC is about vulnerable software; Prompt Injection is about model behavior

## When Risk is Introduced

The risk is introduced in:
- Application and agent components
- Through integrations that permit manipulation of inputs or outputs
- When plugins lack proper security controls

## When Risk is Exposed

This risk is exposed within:
- Application or agent components
- If attackers exploit security vulnerability to gain unauthorized model access
- Insert malicious code or compromise systems

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Agent Permissions** | Enforce strict permissions for agents and plugins |

### Implementation Strategies

1. **Input Validation**
   - Validate all inputs to integrated components
   - Use structured formats instead of freeform text
   - Implement authentication and authorization
   - Sanitize all data passed to plugins

2. **Output Validation**
   - Validate all outputs from integrated components
   - Filter before passing to model
   - Detect anomalous output patterns
   - Implement content security policies

3. **Plugin Security**
   - Review all plugins before integration
   - Implement plugin sandboxing
   - Limit plugin capabilities
   - Monitor plugin behavior

4. **Access Control**
   - Authenticate all plugin interactions
   - Implement least-privilege for plugins
   - Audit plugin access logs
   - Restrict plugin network access

## Real-World Examples

- **Alexa/Google Home eavesdropping:** Attackers uploaded malicious Alexa skills / Google actions (plugins), enabling eavesdropping on user conversations near devices

## Testing Checklist

- [ ] Test plugin input validation
- [ ] Verify plugin output filtering
- [ ] Test for indirect prompt injection via plugins
- [ ] Verify plugin sandboxing
- [ ] Test plugin permission enforcement
- [ ] Audit plugin access logs
- [ ] Test for malicious plugin behavior
- [ ] Verify plugin authentication

## References

- https://saif.google/secure-ai-framework
- https://saif.google/focus-on-agents
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
