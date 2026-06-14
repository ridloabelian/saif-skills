---
name: saif-control-red-teaming
description: |
  SAIF Control: Red Teaming. Identify security and privacy improvements through
  self-driven adversarial attacks on AI infrastructure and products. Covers adversarial
  testing, attack simulation, and vulnerability discovery. Use this skill when conducting
  security assessments, testing AI systems, or discovering vulnerabilities.
trigger: |
  - When conducting security assessments of AI systems
  - When testing AI infrastructure for vulnerabilities
  - When discovering AI-specific security flaws
  - When simulating adversarial attacks
  - When evaluating AI system robustness
---

# SAIF Control: Red Teaming

## Control Overview

**Who can implement:** Model Creators, Model Consumers

**Risk mapping:** All risks

**Description:** Identify security and privacy improvements through self-driven adversarial attacks on AI infrastructure and products.

## Implementation Strategies

### 1. Red Team Exercises

| Exercise Type | Focus | Frequency |
|--------------|-------|-----------|
| **Prompt injection** | Bypass input controls | Monthly |
| **Data extraction** | Extract training data | Quarterly |
| **Model evasion** | Cause incorrect outputs | Monthly |
| **Jailbreak testing** | Bypass safety constraints | Weekly |
| **Multi-modal attacks** | Test images, audio, documents | Quarterly |
| **Agent attacks** | Test agent permission boundaries | Monthly |
| **Supply chain** | Test dependency vulnerabilities | Quarterly |

### 2. Attack Simulation

| Phase | Activity | Output |
|-------|----------|--------|
| **Reconnaissance** | Understand target system | Attack surface map |
| **Weaponization** | Develop attack payloads | Attack scripts |
| **Delivery** | Execute attacks | Attack logs |
| **Exploitation** | Attempt to exploit vulnerabilities | Exploitation evidence |
| **Reporting** | Document findings | Vulnerability report |
| **Remediation** | Fix discovered issues | Patched system |

### 3. Automated Testing

| Tool Type | Purpose | Example |
|-----------|---------|---------|
| **Fuzzing** | Random input generation | AFL, libFuzzer |
| **Adversarial example generators** | Crafted inputs | Foolbox, ART |
| **Prompt injection testers** | Injection detection | Custom frameworks |
| **Model scanners** | Model vulnerability scanning | ModelScan |

## Integration with Other Controls

| Control | Integration Point |
|---------|-------------------|
| Adversarial Training | Use red team findings to improve training |
| Input Validation | Test validation effectiveness |
| Output Validation | Test output filtering |
| Vulnerability Management | Feed findings into vulnerability tracking |

## Testing Checklist

- [ ] Conduct regular red team exercises
- [ ] Test with automated adversarial tools
- [ ] Simulate realistic attack scenarios
- [ ] Document all findings and remediation
- [ ] Test remediation effectiveness
- [ ] Share learnings across teams
- [ ] Benchmark against industry standards
- [ ] Continuously update attack techniques

## References

- https://saif.google/secure-ai-framework
- https://saif.google/controls
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
