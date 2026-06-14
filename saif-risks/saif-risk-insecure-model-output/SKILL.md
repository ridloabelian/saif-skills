---
name: saif-risk-insecure-model-output
description: |
  SAIF Risk: Insecure Model Output (IMO). Model output that is not appropriately validated,
  rewritten, or formatted before being passed to downstream systems or the user. Covers harmful
  content generation, malicious links, phishing content, and unsafe formatting. Use this skill
  when implementing output filtering, designing content safety systems, or securing model
  rendering pipelines.
trigger: |
  - When implementing output filtering and safety
  - When designing content safety systems
  - When securing model rendering pipelines
  - When validating model outputs for harmful content
  - When preventing model-generated phishing or malware
---

# SAIF Risk: Insecure Model Output (IMO)

## Risk Overview

**Who can mitigate:** Model Consumers

**Description:** Model output that is not appropriately validated, rewritten, or formatted before being passed to downstream systems or the user.

Whether accidentally triggered or actively exploited, Insecure Model Output poses risks to organizational reputation, security, and user safety.

## Examples of Insecure Output

### 1. Malicious Links
- User asks LLM to generate email for business promotion
- Model produces text including link to URL that delivers malware
- User harmed by clicking model-generated malicious link

### 2. Phishing Content
- Malicious actor intentionally triggers insecure content
- Requests LLM to produce phishing email based on specific target details
- Model generates convincing phishing content

### 3. Unsafe Formatting
- Markdown output interpreted by client applications
- Cross-site scripting (XSS) via model-generated content
- Data exfiltration through rendered output

### 4. Harmful Content
- Toxic or abusive content generation
- Discriminatory or biased outputs
- Dangerous instructions or advice

## When Risk is Introduced

The risk is inherent to AI models due to their non-deterministic nature, which can lead to unexpected and potentially harmful outputs.

## When Risk is Exposed

This risk is exposed within the model itself during usage, either through:
- **Accidental triggers:** Model spontaneously generates harmful content
- **Deliberate exploitation:** Attacker crafts inputs to trigger harmful outputs

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Output Validation and Sanitization** | Block, nullify, or sanitize insecure output before passing to applications, extensions, or users |

### Implementation Strategies

1. **Content Filtering**
   - Block toxic, harmful, or inappropriate content
   - Detect and remove malicious links
   - Filter phishing content patterns
   - Implement safety classifiers

2. **Output Sanitization**
   - Sanitize Markdown and HTML output
   - Remove executable content
   - Validate URLs in output
   - Encode special characters

3. **Format Validation**
   - Validate output matches expected format
   - Reject malformed outputs
   - Ensure proper encoding
   - Check for injection attempts in output

4. **User Warnings**
   - Warn users about model-generated content
   - Flag potentially unsafe outputs
   - Provide verification mechanisms
   - Implement user reporting for harmful content

## Real-World Examples

- **Malicious packages:** Attackers can compromise users by creating fake malicious packages with names inspired by LLM hallucinations

## Testing Checklist

- [ ] Test for malicious link generation
- [ ] Verify phishing content detection
- [ ] Test XSS via model output
- [ ] Validate output format enforcement
- [ ] Test content safety classifiers
- [ ] Verify URL validation in outputs
- [ ] Test for dangerous instruction generation
- [ ] Monitor for novel output-based attacks

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
