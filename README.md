# Google SAIF Skills Collection

A comprehensive, open-source collection of Agent Skills based on Google's Secure AI Framework (SAIF). These skills enable AI coding agents (Claude Code, Codex, Gemini CLI, Cursor, etc.) to perform AI security assessments, implement controls, and build secure AI systems following Google's industry-standard framework.

## What is SAIF?

Google's Secure AI Framework (SAIF) is a practitioner’s guide to navigating AI security. It addresses AI-specific risks beyond traditional secure coding:
- Model exfiltration
- Data poisoning
- Prompt injection
- Sensitive data disclosure
- Rogue actions (agentic systems)

SAIF was externalized in 2023 from Google's internal AI security framework and is now maintained in collaboration with the Coalition for Secure AI (CoSAI).

## Skill Categories

### 1. Core Framework (`saif-core/`)
- `saif-overview` — Introduction to SAIF, six core elements, and regulatory alignment
- `saif-risk-assessment` — Interactive risk self-assessment methodology
- `saif-development-primer` — Secure AI development lifecycle (data → training → evaluation → deployment)

### 2. Risk Analysis (`saif-risks/`)
- `saif-risk-data-poisoning` — DP: Altering data sources to degrade model performance
- `saif-risk-unauthorized-training-data` — UTD: Using data without authorization
- `saif-risk-model-source-tampering` — MST: Supply chain attacks on model code/weights
- `saif-risk-excessive-data-handling` — EDH: Over-collection/retention of user data
- `saif-risk-model-exfiltration` — MXF: Stealing AI models and weights
- `saif-risk-model-deployment-tampering` — MDT: Compromising model serving infrastructure
- `saif-risk-denial-of-ml-service` — DMS: DoS attacks against ML systems
- `saif-risk-model-reverse-engineering` — MRE: Cloning models via API probing
- `saif-risk-insecure-integrated-component` — IIC: Vulnerabilities in plugins/libraries
- `saif-risk-prompt-injection` — PIJ: Injecting malicious commands into prompts
- `saif-risk-model-evasion` — MEV: Adversarial inputs to cause incorrect inferences
- `saif-risk-sensitive-data-disclosure` — SDD: Leaking private/confidential data
- `saif-risk-inferred-sensitive-data` — ISD: Inferring sensitive info not in training data
- `saif-risk-insecure-model-output` — IMO: Unvalidated harmful model outputs
- `saif-risk-rogue-actions` — RA: Unintended autonomous agent actions

### 3. Security Controls (`saif-controls/`)
- `saif-control-privacy-enhancing-technologies`
- `saif-control-training-data-management`
- `saif-control-training-data-sanitization`
- `saif-control-user-data-management`
- `saif-control-model-data-inventory`
- `saif-control-model-data-access-control`
- `saif-control-model-data-integrity`
- `saif-control-secure-by-default-ml-tooling`
- `saif-control-input-validation`
- `saif-control-output-validation`
- `saif-control-adversarial-training`
- `saif-control-application-access-management`
- `saif-control-user-transparency`
- `saif-control-agent-user-control`
- `saif-control-agent-permissions`
- `saif-control-agent-observability`
- `saif-control-red-teaming`
- `saif-control-vulnerability-management`
- `saif-control-threat-detection`
- `saif-control-incident-response`
- `saif-control-user-policies`
- `saif-control-internal-policies`
- `saif-control-product-governance`
- `saif-control-risk-governance`

### 4. Agent Security (`saif-agents/`)
- `saif-agent-components` — Application, Perception, Reasoning Core, Orchestration, Response Rendering
- `saif-agent-security-guide` — Comprehensive agent security hardening
- `saif-agent-shadow-agents` — Governance for unauthorized autonomous agents

### 5. Google Cloud Integration (`saif-gcp/`)
- `saif-gcp-security-tools` — VPC Service Controls, Model Armor, Cloud Armor, reCAPTCHA
- `saif-gcp-fraud-defense` — AI-powered fraud detection and prevention
- `saif-gcp-executive-protection` — Personal cyberattack defense for executives
- `saif-gcp-board-governance` — CISO/board-level AI security governance

### 6. Content Safety (`saif-safety/`)
- `saif-safety-ai-generated-media` — SynthID, C2PA, content credentials
- `saif-safety-scam-protection` — Scam detection, fraud prevention, user education
- `saif-safety-account-security` — Passkeys, 2SV, recovery contacts, password management

## How to Use

Load any skill with your agent:
```
skill_view(name='saif-risk-prompt-injection')
```

Or reference multiple skills for a comprehensive security assessment:
```
skill_view(name='saif-risk-assessment')
skill_view(name='saif-control-input-validation')
skill_view(name='saif-control-output-validation')
```

## License

These skills are derived from publicly available Google documentation and are provided as open-source educational resources. They do not reflect Google's current technical implementations. Always refer to official Google documentation for the latest guidance.

## Contributing

This is a community-maintained project. Contributions welcome via PR.

## Disclaimer

The content in these skills is intended to provide information and inspiration for industry advancement. It is not a reflection of Google's current technical implementations. Always verify with official sources before implementing security controls in production.
