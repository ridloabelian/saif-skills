---
name: saif-control-application-access
description: |
  SAIF Control: Application Access Management. Ensure that only authorized users and
  endpoints can access specific resources for authorized actions. Covers authentication,
  authorization, rate limiting, and API security. Use this skill when securing model APIs,
  implementing access controls, or designing API protection strategies.
trigger: |
  - When securing model APIs and endpoints
  - When implementing access controls for AI applications
  - When designing API protection strategies
  - When implementing rate limiting
  - When managing API authentication
---

# SAIF Control: Application Access Management

## Control Overview

**Who can implement:** Model Consumers

**Risk mapping:** Denial of ML Service, Model Reverse Engineering

**Description:** Ensure that only authorized users and endpoints can access specific resources for authorized actions.

## Implementation Strategies

### 1. Authentication

| Method | Use Case | Implementation |
|--------|----------|---------------|
| **API keys** | Service-to-service | Scoped, rotated, monitored |
| **OAuth 2.0** | User-facing apps | Token-based with scopes |
| **JWT** | Stateless authentication | Signed tokens with claims |
| **mTLS** | High-security services | Mutual TLS authentication |
| **SAML/SSO** | Enterprise integration | Federated identity |

### 2. Authorization

| Model | Implementation |
|-------|---------------|
| **RBAC** | Role-based permissions |
| **ABAC** | Attribute-based policies |
| **PBAC** | Policy-based access control |
| **ReBAC** | Relationship-based (e.g., Google Zanzibar) |

### 3. Rate Limiting

| Strategy | Purpose |
|----------|---------|
| **Fixed window** | Simple limit per time period |
| **Sliding window** | Smoother rate distribution |
| **Token bucket** | Burst handling |
| **Leaky bucket** | Constant output rate |
| **Adaptive** | Dynamic based on behavior |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Input Validation | Block unauthorized inputs at access layer |
| Output Validation | Restrict access to validated outputs |
| Agent Permissions | Extend access control to agents |
| User Data Management | Control access to user data |

## Testing Checklist

- [ ] Test authentication bypass attempts
- [ ] Verify authorization enforcement
- [ ] Test rate limiting effectiveness
- [ ] Validate token security
- [ ] Test API key rotation
- [ ] Monitor for anomalous access patterns
- [ ] Verify access logging
- [ ] Test access revocation

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
