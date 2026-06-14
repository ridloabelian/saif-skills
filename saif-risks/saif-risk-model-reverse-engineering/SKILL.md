---
name: saif-risk-model-reverse-engineering
description: |
  SAIF Risk: Model Reverse Engineering (MRE). Cloning or recreating a model by analyzing
  inputs, outputs, and behaviors. Covers API-based distillation, on-device extraction, and
  imitation attacks. Use this skill when protecting model IP, implementing rate limiting,
  or defending against model stealing.
trigger: |
  - When protecting model architecture secrets
  - When implementing API rate limiting
  - When defending against model stealing
  - When evaluating output perturbation strategies
  - When securing on-device model weights
---

# SAIF Risk: Model Reverse Engineering (MRE)

## Risk Overview

**Who can mitigate:** Model Consumers

**Description:** Cloning or recreating a model by analyzing a model's inputs, outputs, and behaviors.

The stolen or cloned model can be used for:
- Building imitation products
- Developing adversarial attacks on the original model

## Attack Methods

### 1. API-Based Distillation
- Repeatedly calling model API to gather responses
- Creating dataset of thousands of input/output pairs
- Using dataset to reconstruct copycat or distilled model
- Much cheaper than developing original foundation model
- Requires no rate limits on API

### 2. On-Device Extraction
- Attacker has access to hardware
- Extract model weights directly from device
- Reverse engineer model architecture
- See also Model Exfiltration

### 3. Architecture Discovery
- Attacker discovers underlying foundation model family
- Gains clues about how to perturb inputs
- Uses knowledge of architecture to craft evasion attacks

## When Risk is Introduced

The risk arises within:
- Application component when excessive access granted for queries
- No rate limiting or access controls on model API

## When Risk is Exposed

This risk is exposed if attackers:
- Send excessive queries to model
- Leverage responses to reverse engineer weights
- Use distilled model to develop adversarial attacks
- Build competing products using stolen IP

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Application Access Management** | Rate limiting, query throttling, output perturbation |

### Implementation Strategies

1. **Rate Limiting**
   - Strict per-user query limits
   - Detect unusual query patterns
   - Block automated querying
   - Implement CAPTCHA for suspicious behavior

2. **Output Perturbation**
   - Add noise to model outputs
   - Vary responses slightly for same inputs
   - Prevent consistent input/output mapping
   - Watermark outputs for tracking

3. **Query Monitoring**
   - Detect systematic probing patterns
   - Alert on coverage-based querying
   - Block queries designed to map decision boundaries
   - Monitor for distillation attempts

4. **Legal Protections**
   - Terms of service prohibiting reverse engineering
   - Watermarking for attribution
   - Monitoring for derivative models

## Real-World Examples

- **Stanford Alpaca:** Stanford University research team created Alpaca 7B, a model fine-tuned from LLaMA 7B based on 52,000 instruction-following examples generated from OpenAI's text-davinci-003

## Testing Checklist

- [ ] Test rate limiting against systematic querying
- [ ] Verify output perturbation effectiveness
- [ ] Monitor for distillation attack patterns
- [ ] Test query anomaly detection
- [ ] Validate watermarking if implemented
- [ ] Check terms of service enforcement
- [ ] Test for decision boundary mapping attempts
- [ ] Verify response consistency controls

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
