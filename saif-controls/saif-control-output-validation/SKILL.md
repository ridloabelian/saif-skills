---
name: saif-control-output-validation
description: |
  SAIF Control: Output Validation and Sanitization. Block, nullify, or sanitize insecure
  output from AI models before passing it to applications, extensions or users. Covers
  content filtering, format validation, and safety checking. Use this skill when
  implementing output safety systems, designing content filters, or securing model
  rendering pipelines.
trigger: |
  - When implementing output safety systems
  - When designing content filters for AI outputs
  - When securing model rendering pipelines
  - When validating model output formats
  - When preventing harmful content generation
---

# SAIF Control: Output Validation and Sanitization

## Control Overview

**Who can implement:** Model Creators, Model Consumers

**Risk mapping:** Prompt Injection, Rogue Actions, Sensitive Data Disclosure, Inferred Sensitive Data, Insecure Model Output

**Description:** Block, nullify, or sanitize insecure output from AI models before passing it to applications, extensions or users.

## Implementation Strategies

### 1. Content Filtering

| Filter Type | Purpose | Implementation |
|-------------|---------|---------------|
| **Toxicity** | Block harmful content | Classifier-based detection |
| **PII** | Prevent data leakage | Pattern matching for sensitive data |
| **Malicious code** | Block code injection | Static analysis of generated code |
| **Phishing** | Detect phishing content | URL analysis, content patterns |
| **Bias** | Reduce discriminatory output | Fairness metrics and constraints |

### 2. Format Validation

| Format | Validation |
|--------|-----------|
| **JSON** | Schema validation |
| **HTML** | Sanitize tags, prevent XSS |
| **Markdown** | Escape dangerous elements |
| **SQL** | Prevent injection |
| **Code** | Syntax validation, linting |

### 3. Safety Checking

| Check | Implementation |
|-------|---------------|
| **Factuality** | Grounding against knowledge base |
| **Consistency** | Internal logic verification |
| **Appropriateness** | Context-appropriate content |
| **Safety policy** | Organization-specific rules |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Input Validation | Defense in depth - output catches what input misses |
| Adversarial Training | Model trained to produce safer outputs |
| Agent User Control | Output validation before user confirmation |
| Agent Observability | Log output validation decisions |

## Testing Checklist

- [ ] Test content filters with adversarial examples
- [ ] Verify PII detection in outputs
- [ ] Test format validation for all output types
- [ ] Validate safety policy enforcement
- [ ] Test false positive rate
- [ ] Monitor for novel output-based attacks
- [ ] Verify integration with rendering pipeline
- [ ] Test output validation under load

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
