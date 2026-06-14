---
name: saif-risk-model-evasion
description: |
  SAIF Risk: Model Evasion (MEV). Causing a model to produce incorrect inferences by
  slightly perturbing the prompt input. Covers adversarial examples, homoglyph attacks,
  steganography, and input perturbations. Use this skill when hardening models against
  adversarial inputs, implementing input validation, or testing model robustness.
trigger: |
  - When hardening models against adversarial inputs
  - When implementing input validation for AI systems
  - When testing model robustness
  - When evaluating adversarial example defenses
  - When securing multi-modal inputs
---

# SAIF Risk: Model Evasion (MEV)

## Risk Overview

**Who can mitigate:** Model Creators, Model Consumers

**Description:** Causing a model to produce incorrect inferences by slightly perturbing the prompt input.

Model Evasion can result in reputational or legal challenges and trigger other downstream risks, such as to security or privacy systems.

## Attack Types

### 1. Visual Adversarial Examples
- Placing stickers on stop sign to obscure visual inputs
- Self-driving car fails to identify stop sign
- Normal wear and tear on signs can lead to misidentification
- Model not trained on images of signs in varying degrees of disrepair

### 2. Foundation Model Discovery
- Attacker discovers underlying foundation model family
- Gains clues about how to perturb inputs
- Uses knowledge of architecture and evolution to craft evasion

### 3. Iterative Probing
- Attacker repeatedly probes model (see Model Reverse Engineering)
- Figures out inference patterns
- Constructs examples that evade inferences
- Adversarial examples provide output attacker wants while looking unaltered

### 4. Invisible Perturbations
- Inputs perturbed to appear unaltered but produce attacker-desired output
- **Homoglyph attack:** Slight changes to typefaces human eye doesn't perceive as different letter, but triggers unexpected inferences
- **Steganography:** Encode text within image pixels. Text is part of prompt for LLM but user won't see it

## When Risk is Introduced

Model Evasion is an inherent risk in AI models, as their core functionality relies on distinguishing between inputs to trigger specific inferences.

## When Risk is Exposed

This risk is exposed within the model component itself during its usage.

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **Adversarial Training and Testing** | Make models robust to adversarial inputs through training techniques |

### Implementation Strategies

1. **Adversarial Training**
   - Include adversarial examples in training data
   - Train model to be robust to small perturbations
   - Use techniques like FGSM, PGD
   - Regular retraining with new adversarial examples

2. **Input Preprocessing**
   - Detect and remove adversarial perturbations
   - Normalize inputs before processing
   - Implement input transformation pipelines
   - Use ensemble methods for prediction

3. **Multi-Modal Validation**
   - Validate all modalities for hidden content
   - OCR to detect embedded text in images
   - Audio analysis for hidden commands
   - Document scanning for hidden layers

4. **Robustness Testing**
   - Regular adversarial testing
   - Red team exercises with evasion focus
   - Automated robustness benchmarks
   - Monitor for novel attack techniques

## Real-World Examples

- **Self-driving car attacks:** Adversarial images have been used to modify street signs to confuse self-driving cars

## Testing Checklist

- [ ] Test with adversarial examples
- [ ] Verify homoglyph attack resistance
- [ ] Test steganography detection
- [ ] Evaluate model robustness to perturbations
- [ ] Test multi-modal evasion attacks
- [ ] Verify adversarial training effectiveness
- [ ] Test input preprocessing defenses
- [ ] Monitor for novel evasion techniques

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
