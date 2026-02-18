---
title: Licensing Diagnostic Playbook – <SCENARIO NAME>
audience: seller
agent_role: licensing_diagnostic
intent: <INTENT_KEYWORD>
scope: <PRODUCT / WORKLOAD>
confidence_model: required
version: 1.0
last_updated: <YYYY-MM-DD>
---

# Licensing Diagnostic Playbook  
## Scenario: <SCENARIO NAME>

---

## 0. Agent Usage Instructions (Agent-Only)

This playbook is designed for **guided diagnosis**, not direct Q&A.

Rules:
- Diagnose before explaining.
- Ask the minimum number of questions required.
- Prefer validation steps over assumptions.
- Stop once confidence is high.
- Explicitly state confidence level.
- Recommend escalation if no root cause applies.

---

## 1. Situation Classifier

Use this playbook when **all** of the following are true:

- <Trigger condition 1>
- <Trigger condition 2>
- <Trigger condition 3>

Do NOT use this playbook if:
- <Exclusion condition>

---

## 2. Diagnostic Objective

Clearly state what this playbook is trying to determine.

Example:
Determine why <observed behavior> is occurring and whether it is expected behavior, misconfiguration, or an anomaly.

---

## 3. Diagnostic Dimensions

Every diagnosis must reason across these dimensions:

1. <Dimension 1>
2. <Dimension 2>
3. <Dimension 3>
4. <Dimension 4>

---

## 4. Guided Diagnostic Flow

### Step 1 – <Step Name>

Ask the customer:

> <Primary diagnostic question>

Accepted answers:
- Yes
- No
- Not sure

Why this matters:
- <Explanation>

---

### Step 2 – <Step Name>

Ask the customer:

> <Follow-up diagnostic question>

Accepted answers:
- <Option A>
- <Option B>

Why this matters:
- <Explanation>

---

## 5. Root Cause Modules

### Root Cause A: <Root Cause Name>

Applies when:
- <Condition>
- <Condition>

Why this happens:
- <Explanation>

How to validate:
- <Validation step>

Resolution options:
- <Option 1>
- <Option 2>

Confidence Level: High | Medium

---

### Root Cause B: <Root Cause Name>

Applies when:
- <Condition>

Why this happens:
- <Explanation>

Resolution options:
- <Option>

Confidence Level: Medium | Low

---

## 6. Alternative / Edge Case Checks

If no primary root cause applies, check:

- <Edge case 1>
- <Edge case 2>

---

## 7. Resolution Summary (Agent Must Generate)

The agent must summarize:
- Identified root cause
- Why the behavior occurs
- Whether behavior is expected
- Recommended next action
- Confidence level

---

## 8. Escalation Criteria

Recommend escalation when **all** of the following are true:

- <Escalation condition 1>
- <Escalation condition 2>
- <Escalation condition 3>

Escalation packet must include:
- Environment
- User
- Security roles
- License SKU
- Evidence collected

---

## 9. Seller-Ready Customer Explanation Template

Provide a short explanation that sellers can share verbatim:

> "<Customer-safe explanation>"

---

## 10. Confidence Declaration

The final response must explicitly state one of:
- High confidence – expected behavior
- Medium confidence – configuration-related
- Low confidence – escalation recommended
