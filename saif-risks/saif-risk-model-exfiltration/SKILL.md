---
name: saif-risk-model-exfiltration
description: |
  SAIF Risk: Model Exfiltration (MXF). Unauthorized appropriation of an AI model for
  replicating functionality or extracting intellectual property. Covers model theft from
  cloud, on-device, and insider threats. Use this skill when protecting model IP,
  securing model serving infrastructure, or implementing access controls.
trigger: |
  - When protecting model intellectual property
  - When securing model serving infrastructure
  - When implementing model access controls
  - When evaluating insider threat risks
  - When protecting on-device models
---

# SAIF Risk: Model Exfiltration (MXF)

## Risk Overview

**Who can mitigate:** Model Creators, Model Consumers

**Description:** Unauthorized appropriation of an AI model, for replicating functionality or to extract intellectual property.

Similar to stealing code, this threat has intellectual property, security, and privacy implications.

## Attack Vectors

### 1. Cloud Environment Theft
- Hacking into cloud environment to steal generative AI model
- Model size when serialized is fairly modest and not a major obstacle
- Attackers can exfiltrate model weights and architecture

### 2. Insider Threats
- Models at risk of theft in internal development, build, deployment, and production environments
- External attackers taking over privileged insider accounts
- Compromised employees with access to model artifacts

### 3. On-Device Models
- Attackers with hardware access can extract model weights
- Mobile and edge device models are particularly vulnerable
- Physical security becomes critical

## Distinction from Model Reverse Engineering

**Model Exfiltration** = Stealing the actual model files/weights
**Model Reverse Engineering** = Recreating model by analyzing inputs/outputs

These are related but distinct risks requiring different mitigations.

## When Risk is Introduced

Model Exfiltration is introduced when:
- Storage or serving infrastructure lacks adequate security
- Access controls are insufficient
- Model serialization exposes weights in accessible locations

## When Risk is Exposed

This risk is exposed if attackers:
- Target vulnerabilities in serving or storage systems
- Gain unauthorized access to model code or weights
- Extract models from compromised environments

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Model and Data Inventory Management** | Track all models and their locations |
| **Model and Data Access Control** | Minimize access to model weights and code |
| **Secure-by-Default ML Tooling** | Use secure frameworks that protect model confidentiality |

### Implementation Strategies

1. **Storage Security**
   - Encrypt model weights at rest
   - Implement strict access controls
   - Monitor for unauthorized access attempts
   - Use secure enclaves where available

2. **Serving Security**
   - Authenticate all model access requests
   - Implement rate limiting
   - Monitor for anomalous access patterns
   - Use private endpoints

3. **On-Device Protection**
   - Obfuscate model weights
   - Implement hardware-backed security
   - Use model encryption
   - Detect tampering attempts

## Real-World Examples

- **Meta Llama leak:** Meta's Llama model was leaked online, bypassing Meta's license acceptance review process

## Testing Checklist

- [ ] Test access controls on model storage
- [ ] Verify encryption of model weights at rest
- [ ] Monitor for unauthorized model downloads
- [ ] Test insider threat scenarios
- [ ] Validate on-device model protection
- [ ] Check serving infrastructure security
- [ ] Implement model access logging
- [ ] Test incident response for model theft

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
