---
name: saif-risk-inferred-sensitive-data
description: |
  SAIF Risk: Inferred Sensitive Data (ISD). Models inferring sensitive information about
  people that is not contained in the model's training data. Covers privacy inference from
  public data, behavioral analysis, and sensitive attribute prediction. Use this skill when
  evaluating privacy risks, implementing inference detection, or protecting user privacy.
trigger: |
  - When evaluating privacy inference risks
  - When implementing inference detection controls
  - When protecting user privacy from model inference
  - When auditing model outputs for sensitive inferences
  - When designing data minimization for training
---

# SAIF Risk: Inferred Sensitive Data (ISD)

## Risk Overview

**Who can mitigate:** Model Creators, Model Consumers

**Description:** Models inferring sensitive information about people that is not contained in the model's training data.

Inferred information that turns out to be true, even if produced as part of a hallucination, can be considered a data privacy incident, whereas the same information when false would be treated as a factuality issue.

## Inference Examples

A model may be able to infer information about people (gender, political affiliation, or sexual orientation) based on:
- Their inputs and responses
- Integrated plugins, such as social media plugin accessing public account's liked pages or followed accounts

## Two Related Risks

1. **User alarmed:** If a model infers sensitive data about them
2. **Privacy violation:** One user may use a model to infer sensitive data about someone else

## Distinction from Sensitive Data Disclosure

**Inferred Sensitive Data** = Model deduces sensitive info not in training data
**Sensitive Data Disclosure** = Model reveals sensitive info from training/tuning/prompt data

These are related but distinct risks.

## When Risk is Introduced

The risk is introduced in several components:
- Inherent to models due to non-deterministic nature
- Amplified by inadequate data handling practices
- Due to training processes that neglect evaluating model's potential for sensitive inferences

## When Risk is Exposed

This risk is exposed within the model when it generates a response containing inferred sensitive data that it shouldn't.

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Training Data Management** | Remove or label data that could lead to sensitive inferences |
| **Output Validation and Sanitization** | Filter model outputs to prevent revealing inferred sensitive data |

### Implementation Strategies

1. **Data Minimization**
   - Remove data that enables sensitive inferences
   - Label data that could lead to inference
   - Evaluate training data for inference risks
   - Document data that could enable inference

2. **Output Filtering**
   - Detect and block inferred sensitive data in outputs
   - Implement privacy classifiers
   - Monitor for inference patterns
   - Alert on sensitive attribute predictions

3. **Model Testing**
   - Test for inference capabilities during evaluation
   - Check for sensitive attribute prediction
   - Evaluate on privacy benchmarks
   - Regular red team exercises for inference

4. **User Controls**
   - Allow users to opt out of inference
   - Provide transparency about inference capabilities
   - Implement data deletion for inference training
   - User-facing controls for sensitive data

## Real-World Examples

- **AI inference from faces:** Papers on AI inferences about sexual orientation or criminal record from faces

## Testing Checklist

- [ ] Test for sensitive attribute inference
- [ ] Verify output filtering for inferred data
- [ ] Evaluate training data for inference risks
- [ ] Test model on privacy benchmarks
- [ ] Verify user controls for inference
- [ ] Monitor for inference attack patterns
- [ ] Test with adversarial inference queries
- [ ] Audit model for inference capabilities

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
