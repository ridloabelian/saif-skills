---
name: saif-risk-excessive-data-handling
description: |
  SAIF Risk: Excessive Data Handling (EDH). Collection, retention, processing, or sharing
  of user data beyond what is allowed by relevant policies. Covers data lifecycle management
  and privacy compliance. Use this skill when implementing data retention policies, designing
  privacy controls, or auditing data handling practices.
trigger: |
  - When implementing data retention policies
  - When designing privacy controls for AI systems
  - When auditing data handling practices
  - When evaluating data minimization strategies
  - When ensuring GDPR/CCPA compliance for AI
---

# SAIF Risk: Excessive Data Handling (EDH)

## Risk Overview

**Who can mitigate:** Model Creators

**Description:** Collection, retention, processing, or sharing of user data beyond what is allowed by relevant policies.

Excessive Data Handling can create both policy and legal challenges.

## Types of User Data at Risk

In the context of models, user data might include:
- User queries and text inputs
- User interactions and conversations
- Personalizations and preferences
- Models derived from user data

## When Risk is Introduced

The risk is introduced when:
- Data sources lack proper metadata tagging for effective management
- Model and data storage infrastructure isn't designed to address data lifecycle concerns
- Data handling policies are not enforced

## When Risk is Exposed

This risk is exposed in:
- **Model components:** Leading to data usage beyond permissible limits
- **Storage components:** Leading to data retention beyond allowed periods

## Mitigation Controls

| Control | Implementation |
|---------|---------------|
| **User Data Management** | Store, process, and use all user data in compliance with user consent |

### Data Lifecycle Management

1. **Data Collection**
   - Collect only necessary data
   - Document purpose for each data element
   - Obtain proper consent

2. **Data Retention**
   - Define retention periods per data type
   - Automate archiving and deletion
   - Alert on models trained with outdated data

3. **Data Processing**
   - Process only for stated purposes
   - Implement data minimization
   - Monitor for unauthorized processing

4. **Data Sharing**
   - Limit sharing to authorized parties
   - Document all data transfers
   - Implement sharing agreements

## Real-World Examples

- **Samsung ChatGPT ban:** Samsung banned usage of ChatGPT after discovering private source code had leaked via using it in GenAI prompts

## Testing Checklist

- [ ] Audit data collection practices against policies
- [ ] Verify retention periods are enforced
- [ ] Test automated deletion workflows
- [ ] Monitor for unauthorized data sharing
- [ ] Validate consent mechanisms
- [ ] Check metadata tagging completeness
- [ ] Test data lineage tracking
- [ ] Audit access to stored user data

## References

- https://saif.google/secure-ai-framework
- https://blog.google/innovation-and-ai/technology/safety-security/introducing-googles-secure-ai-framework/
