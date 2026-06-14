---
name: saif-risk-denial-of-ml-service
description: |
  SAIF Risk: Denial of ML Service (DMS). Reducing availability of ML systems by issuing
  queries that consume excessive resources. Covers traditional DoS, sponge examples, and
  energy-latency attacks. Use this skill when implementing rate limiting, designing API
  protection, or securing model availability.
trigger: |
  - When implementing rate limiting for model APIs
  - When designing API protection strategies
  - When securing model availability
  - When evaluating resource exhaustion risks
  - When protecting on-device models from battery drain
---

# SAIF Risk: Denial of ML Service (DMS)

## Risk Overview

**Who can mitigate:** Model Consumers

**Description:** Reducing the availability of ML systems and denying service by issuing queries that take too many resources.

## Attack Types

### 1. Traditional Denial of Service
- Spamming system with abusive material
- Overloading automated or manual review processes
- Repeated queries without rate limiting
- Taking model offline for other users

### 2. Sponge Examples (Queries of Death)
- Inputs designed to maximize energy consumption and latency
- Push ML systems towards worst-case performance
- Adversaries use tools to accelerate construction of sponge examples
- Especially relevant for on-device models (battery drain)

### 3. Energy-Latency Attacks
- Carefully crafted inputs to maximize resource usage
- Target fundamental functioning of model itself
- Can make model unavailable through resource exhaustion

## When Risk is Introduced

The risk arises in:
- Application component when model exposed to excessive access
- Some types stem from fundamental functioning of model itself

## When Risk is Exposed

This risk is exposed during application use when attackers:
- Overwhelm model with excessive calls
- Use carefully crafted "sponge examples" that take advantage of model weaknesses
- Degrade performance through resource exhaustion

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Application Access Management** | Rate limiting, load balancing, input filtering |

### Implementation Strategies

1. **Rate Limiting**
   - Per-user rate limits
   - Per-IP rate limits
   - Tiered access based on trust level
   - Dynamic rate adjustment based on load

2. **Load Balancing**
   - Distribute queries across multiple instances
   - Auto-scaling based on demand
   - Circuit breakers for failing instances
   - Queue management for peak loads

3. **Input Filtering**
   - Detect and block sponge examples
   - Validate input complexity
   - Reject obviously malicious inputs
   - Monitor for anomalous query patterns

4. **Resource Management**
   - Set query timeout limits
   - Implement query complexity scoring
   - Monitor resource usage per query
   - Alert on resource exhaustion patterns

## Real-World Examples

- **Object detection DoS:** Researchers proved how slight perturbation to images can cause denial of service on object detection models

## Testing Checklist

- [ ] Test rate limiting effectiveness
- [ ] Verify load balancing under stress
- [ ] Test with sponge example inputs
- [ ] Monitor resource usage per query type
- [ ] Verify circuit breaker functionality
- [ ] Test auto-scaling behavior
- [ ] Validate input complexity limits
- [ ] Test DDoS mitigation strategies

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
