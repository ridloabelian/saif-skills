---
name: saif-gcp-security-tools
description: |
  Google Cloud security tools supporting SAIF implementation. Covers VPC Service
  Controls, Model Armor, Cloud Armor, reCAPTCHA, and Security AI Workbench.
  Use this skill when implementing SAIF controls on Google Cloud, designing
  cloud-native AI security architectures, or evaluating GCP security services.
trigger: |
  - When implementing SAIF on Google Cloud
  - When designing cloud-native AI security architectures
  - When evaluating GCP security services for AI
  - When configuring model serving security on GCP
  - When implementing network security for AI workloads
---

# Google Cloud Security Tools for SAIF

## Overview

Google Cloud provides a portfolio of security solutions that directly support SAIF implementation. These tools address the infrastructure, application, and governance layers of AI security.

## VPC Service Controls

**Purpose:** Create security perimeters around your AI services and data.

**SAIF Alignment:**
- **Model Exfiltration (MXF):** Prevent unauthorized data transfer out of perimeter
- **Excessive Data Handling (EDH):** Enforce data residency and access boundaries
- **Model Deployment Tampering (MDT):** Restrict which services can access model serving infrastructure

**Key Features:**
| Feature | Security Benefit |
|---------|---------------|
| Service perimeters | Define trust boundaries around AI services |
| Ingress/egress rules | Control data flow to/from AI workloads |
| Access levels | Context-aware access (device, location, time) |
| VPC accessible services | Private connectivity without internet exposure |

**Implementation for AI:**
```
Perimeter: ai-production-perimeter
├── Services: vertex-ai, storage, bigquery
├── Egress: Block all except approved APIs
├── Ingress: Only from approved networks
└── Access Level: Corporate devices + MFA
```

## Model Armor

**Purpose:** Protect AI models from malicious input and output.

**SAIF Alignment:**
- **Prompt Injection (PIJ):** Filter malicious prompts before reaching model
- **Model Evasion (MEV):** Detect adversarial inputs
- **Insecure Model Output (IMO):** Sanitize model outputs

**Key Features:**
| Feature | Security Benefit |
|---------|---------------|
| Input filtering | Block known injection patterns and malicious content |
| Output filtering | Prevent toxic, harmful, or sensitive data in outputs |
| Content moderation | Automated moderation of model inputs and outputs |
| Custom policies | Organization-specific content policies |

## Cloud Armor

**Purpose:** Protect AI APIs and applications from DDoS and web attacks.

**SAIF Alignment:**
- **Denial of ML Service (DMS):** Rate limiting and DDoS protection
- **Model Reverse Engineering (MRE):** Rate limiting to prevent excessive API probing

**Key Features:**
| Feature | Security Benefit |
|---------|---------------|
| DDoS protection | Automatic mitigation of volumetric attacks |
| Rate limiting | Prevent API abuse and reverse engineering |
| WAF rules | Block SQL injection, XSS, and other web attacks |
| Bot management | Detect and block malicious automated traffic |
| Adaptive protection | ML-based detection of emerging threats |

## reCAPTCHA Enterprise

**Purpose:** Distinguish between legitimate users and malicious bots/AI agents.

**SAIF Alignment:**
- **Denial of ML Service (DMS):** Prevent bot abuse of AI APIs
- **Model Reverse Engineering (MRE):** Block automated API probing

**Key Features:**
| Feature | Security Benefit |
|---------|---------------|
| Bot detection | Identify automated vs. human traffic |
| Risk scoring | Score each request for fraud likelihood |
| AI-powered fraud defense | Detect AI-generated attacks |
| Agent-specific capabilities | Identify and manage AI agent traffic |

## Security AI Workbench

**Purpose:** AI-powered security operations and threat detection.

**SAIF Alignment:**
- **Threat Detection:** AI-powered anomaly detection for AI systems
- **Incident Response:** Automated triage and response
- **Vulnerability Management:** Continuous security assessment

**Key Features:**
| Feature | Security Benefit |
|---------|---------------|
| AI-powered threat detection | Identify anomalies in AI system behavior |
| Automated response | Trigger playbooks for security events |
| Natural language queries | Query security data using natural language |
| Integration with Chronicle | Security analytics and investigation |

## Cloud IAM and Workload Identity

**Purpose:** Secure access control for AI workloads and agents.

**SAIF Alignment:**
- **Agent Permissions:** Granular IAM for agent identities
- **Model and Data Access Control:** Least-privilege access to models and data
- **Shadow Agents:** Identify and manage agent identities

**Key Features:**
| Feature | Security Benefit |
|---------|---------------|
| Workload Identity Federation | Secure authentication for AI workloads |
| Granular IAM roles | Fine-grained permissions for AI services |
| Agent IDs | Unique identification for autonomous agents |
| Policy intelligence | Analyze and optimize IAM policies |

## Implementation Architecture

```
User Request
    ↓
[Cloud Armor] → DDoS protection, rate limiting, WAF
    ↓
[reCAPTCHA] → Bot detection, risk scoring
    ↓
[VPC Service Controls] → Perimeter enforcement
    ↓
[Model Armor] → Input/output filtering
    ↓
[Vertex AI / Model Serving] → Model inference
    ↓
[Security AI Workbench] → Monitoring and threat detection
    ↓
[Cloud IAM] → Audit logging and access control
```

## Configuration Checklist

- [ ] VPC Service Controls perimeter around AI services
- [ ] Model Armor policies for input/output filtering
- [ ] Cloud Armor rate limiting for model APIs
- [ ] reCAPTCHA on user-facing AI interfaces
- [ ] Workload Identity for AI services
- [ ] Security AI Workbench for monitoring
- [ ] Cloud IAM least-privilege policies
- [ ] Audit logging for all AI service access

## References

- https://cloud.google.com
- https://cloud.google.com/vpc-service-controls
- https://cloud.google.com/model-armor
- https://cloud.google.com/armor
- https://cloud.google.com/recaptcha-enterprise
- https://cloud.google.com/security-ai-workbench
- https://saif.google
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
