---
name: saif-control-input-validation
description: |
  SAIF Control: Input Validation and Sanitization. Block or restrict adversarial
  queries to AI models. Use this skill when implementing input filtering for LLMs,
  designing prompt preprocessing pipelines, or securing model APIs against injection
  attacks.
trigger: |
  - When implementing input filtering for AI systems
  - When designing prompt preprocessing pipelines
  - When securing model APIs
  - When testing for prompt injection vulnerabilities
  - When reviewing AI application input handling
---

# SAIF Control: Input Validation and Sanitization

## Control Overview

**Who can implement:** Model Creators, Model Consumers

**Risk mapping:** Prompt Injection, Model Evasion

**Description:** Block or restrict adversarial queries to AI models.

## Implementation Strategies

### 1. Pattern-Based Filtering

Block known injection patterns and malicious phrases:

| Pattern Category | Examples |
|-----------------|----------|
| Instruction override | "ignore your previous instructions", "ignore above", "forget everything" |
| Jailbreak triggers | "DAN", "Do Anything Now", "developer mode", "jailbreak" |
| System prompt extraction | "what are your instructions", "output your system prompt", "show your preamble" |
| Delimiter manipulation | Unmatched quotes, brackets, XML tags, markdown code blocks |
| Encoding tricks | Base64, URL encoding, Unicode homoglyphs, zero-width characters |

### 2. Semantic Analysis

Detect when user input contains commands or instructions:

| Technique | Implementation |
|-----------|---------------|
| Intent classification | Classify input as query vs. instruction vs. command |
| Named entity recognition | Detect system-related terms in user input |
| Sentiment analysis | Detect manipulative or coercive language patterns |
| Context analysis | Compare input against expected user query patterns |

### 3. Structural Validation

Validate input structure and format:

| Check | Purpose |
|-------|---------|
| Length limits | Prevent excessively long prompts that could overflow context |
| Character set validation | Restrict to expected character sets |
| Format validation | Ensure input matches expected format (JSON, XML, etc.) |
| Nested structure detection | Detect attempts to embed instructions within instructions |

### 4. Content-Type Separation

Unambiguously separate system instructions from user data:

```
# Best Practice: Use explicit delimiters
SYSTEM_INSTRUCTIONS = """You are a helpful assistant."""

USER_INPUT = """[BEGIN_USER_INPUT]
{user_input}
[END_USER_INPUT]"""

FULL_PROMPT = f"{SYSTEM_INSTRUCTIONS}\n{USER_INPUT}"
```

| Delimiter Type | Example | Use Case |
|---------------|---------|----------|
| XML tags | `<system>`, `<user>`, `<instruction>` | Structured prompts |
| Special tokens | `[SYSTEM]`, `[USER]`, `[ASSISTANT]` | Custom tokenizers |
| JSON structure | `{"role": "system"}`, `{"role": "user"}` | API-based models |
| Markdown fences | `--- system ---`, `--- user ---` | Human-readable separation |

## Multi-Modal Input Validation

For models processing images, audio, or other modalities:

| Modality | Validation Strategy |
|----------|-------------------|
| **Images** | OCR to detect embedded text; steganography detection; metadata validation |
| **Audio** | Transcription analysis; detect hidden commands in audio |
| **Documents** | Extract and validate all embedded content; scan for hidden text layers |
| **URLs** | URL validation; domain reputation check; content preview before fetching |

## Implementation Checklist

- [ ] Define allowed input patterns and character sets
- [ ] Implement length limits appropriate to use case
- [ ] Block known injection phrases and patterns
- [ ] Use explicit delimiters between system and user content
- [ ] Validate multi-modal inputs for hidden content
- [ ] Log and alert on blocked inputs for monitoring
- [ ] Implement rate limiting to prevent brute-force injection attempts
- [ ] Test with adversarial input datasets
- [ ] Regularly update filter patterns based on new attack techniques

## Testing Strategies

| Test Type | Description |
|-----------|-------------|
| Known injection phrases | Test with published jailbreak prompts and injection techniques |
| Obfuscated inputs | Test with encoding, homoglyphs, zero-width characters |
| Multi-modal injection | Test images/audio containing hidden instructions |
| Context window attacks | Test with very long inputs designed to push out system instructions |
| Delimiter attacks | Test with unmatched or nested delimiters |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Output Validation | Input validation is first line; output validation catches what gets through |
| Adversarial Training | Model trained to recognize injection attempts even if filters miss them |
| Application Access Management | Rate limiting prevents brute-force injection attempts |
| Agent Permissions | Limit blast radius if injection bypasses input filters |

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://arxiv.org/abs/2302.12173 (Prompt Injection attacks)
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
