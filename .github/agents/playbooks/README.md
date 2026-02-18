# Diagnostic Playbooks

This directory contains diagnostic playbooks for the Licensing Diagnostic Agent to help sellers diagnose licensing issues for D365 Finance & Operations and Supply Chain Management.

## Available Playbooks

### 1. SCM vs Team Members Licensing (`scm-vs-team-members-licensing.md`)

**Purpose**: Diagnose why a security role requires SCM license instead of Team Members

**Use when**:
- Customer expected a security role to require Team Members license
- The role is showing as requiring SCM (or Finance) full license instead
- Customer is confused about why this upgrade is needed

**Key Diagnostic Areas**:
- Role composition (standard vs customized)
- Duty & privilege assignments
- Object access levels (read-only vs write)
- Role combinations
- Legacy licensing model assumptions

**Common Root Causes**:
1. Out-of-box role design (operational roles require full licenses)
2. Customized role with write permissions
3. Multiple role combination triggering higher licensing
4. Legacy licensing model assumptions

## Playbook Structure

Each playbook follows this standard structure:

1. **Situation Classifier** - When to use this playbook
2. **Diagnostic Objective** - What the playbook is trying to determine
3. **Diagnostic Dimensions** - Key areas to consider
4. **Guided Diagnostic Flow** - Step-by-step diagnostic questions
5. **Root Cause Modules** - Possible root causes with validation steps
6. **Alternative/Edge Case Checks** - Additional scenarios to consider
7. **Resolution Summary** - What the agent must provide
8. **Escalation Criteria** - When to escalate
9. **Seller-Ready Customer Explanation** - Template for customer communication
10. **Confidence Declaration** - Required confidence level statement

## How the Agent Uses Playbooks

The Licensing Diagnostic Agent:
1. Determines the appropriate operating mode (Verification vs Diagnostic)
2. Selects the most relevant diagnostic playbook based on the issue
3. Follows the guided diagnostic flow
4. Asks minimum clarifying questions
5. Identifies the probable root cause
6. Provides seller-ready explanations
7. Recommends next actions
8. States confidence level
9. Escalates only when behavior conflicts with official licensing guidance

## Adding New Playbooks

When adding a new playbook:
1. Follow the template structure in `licensing-diagnostic-playbook-template.md`
2. Include proper YAML frontmatter with required fields
3. Ensure the playbook addresses a specific, common diagnostic scenario
4. Add corresponding Q&A entries to `Additional-Q&A`
5. Reference the playbook in `Licensing-Diagnosis.md` if needed
6. Update this README with the new playbook details

## Related Files

- `../Licensing-Diagnosis.md` - Main agent instructions
- `../Additional-Q&A` - Quick reference Q&A for common questions
- `../licensing-diagnostic-playbook-template.md` - Template for creating new playbooks
