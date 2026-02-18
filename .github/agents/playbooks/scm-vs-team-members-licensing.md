---
name: SCM vs Team Members Licensing Diagnostic Playbook
description: Diagnose why a security role requires SCM license instead of Team Members
audience: seller
agent_role: licensing_diagnostic
intent: scm_team_members_license_confusion
scope: D365 Finance & Operations / Supply Chain Management
confidence_model: required
version: 1.0
last_updated: 2026-02-18
---

# Licensing Diagnostic Playbook  
## Scenario: Security Role Requires SCM Instead of Team Members

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

- Customer expected a security role to require Team Members license
- The role is showing as requiring SCM (or Finance) full license instead
- Customer is confused about why this upgrade is needed

Do NOT use this playbook if:
- Question is about device licensing
- Question is about enforcement timing or banners
- Customer is asking about a specific AOT object mapping (use object verification mode instead)

---

## 2. Diagnostic Objective

Determine why a security role requires SCM full license instead of Team Members, and identify the specific privileges, duties, or objects driving the higher license requirement.

---

## 3. Diagnostic Dimensions

Every diagnosis must reason across these dimensions:

1. **Role Composition** - Is this a standard out-of-box role or a customized role?
2. **Duty & Privilege Assignment** - What duties and privileges are assigned to the role?
3. **Object Access Level** - Are there write/update permissions that exceed read-only access?
4. **Role Combinations** - Does the user have multiple roles that combine to require higher licensing?
5. **Legacy Assumptions** - Is the customer's expectation based on old licensing models?

---

## 4. Guided Diagnostic Flow

### Step 1 – Identify Role Type

Ask the customer:

> Is this a standard out-of-box security role, or has it been customized/duplicated?

Accepted answers:
- Standard out-of-box role
- Customized or duplicated role
- Not sure

Why this matters:
- Out-of-box roles map to a single license type by design
- Customized roles may have added duties/privileges that trigger higher licensing
- Understanding customization helps pinpoint the root cause

---

### Step 2 – Check Role Assignment

Ask the customer:

> Does the user have this role assigned by itself, or are there multiple roles combined?

Accepted answers:
- Single role only
- Multiple roles combined
- Not sure

Why this matters:
- License requirements are based on ALL combined roles assigned to a user
- Multiple roles can combine to require higher licensing even if individual roles seem lower
- PPAC and USG show cumulative license requirements, not per-role requirements

---

### Step 3 – Verify Access Level

Ask the customer:

> Does this role need to CREATE, UPDATE, or DELETE records, or is it primarily for READ-ONLY access?

Accepted answers:
- Read-only access
- Create/Update/Delete records
- Mixed - some read-only, some write
- Not sure

Why this matters:
- Team Members licenses provide read-only access across D365 products
- Any write operations (create, update, delete) typically require full licenses
- Changing write permissions to read-only can reduce license requirements

---

## 5. Root Cause Modules

### Root Cause A: Out-of-Box Role Design

Applies when:
- Customer is using a standard out-of-box role
- The role has not been customized
- Single role assigned to user

Why this happens:
- Out-of-box roles are pre-configured to map to specific license types
- SCM roles are designed to provide operational capabilities that exceed Team Members scope
- Team Members is limited to read-only access; operational roles require full licenses

How to validate:
- Check USG or PPAC License Detail report
- Review the role definition in D365 to confirm it's unmodified
- Verify the role name matches standard SCM operational roles (e.g., Production Manager, Warehouse Worker)

Resolution options:
- If user needs operational capabilities: Assign correct SCM license
- If user only needs read access: Assign Team Members license and create a custom read-only role
- Use the "Duplicate with license filter" feature (released Dec 2025) to create a Team Members version

Confidence Level: High

---

### Root Cause B: Customized Role with Write Permissions

Applies when:
- Role has been customized or duplicated
- Role includes duties/privileges with create, update, or delete permissions
- Customer expected read-only behavior

Why this happens:
- Custom roles may inadvertently include write permissions
- Write operations on SCM objects (inventory, production, warehouse) require full SCM license
- Even a single write privilege can elevate the entire role's license requirement

How to validate:
- Use USG License Summary to see which objects are driving the license requirement
- Review the role's assigned duties and privileges
- Check for any non-read-only permissions

Resolution options:
- Remove unnecessary write permissions from the role
- Change write permissions to read-only where appropriate
- Use the "Duplicate with license filter" feature to create a Team Members-compliant version
- Split the role into separate read-only and operational roles

Confidence Level: High

---

### Root Cause C: Multiple Role Combination

Applies when:
- User has multiple security roles assigned
- Individual roles may seem appropriate, but combination triggers higher licensing
- License requirement shown in PPAC is cumulative

Why this happens:
- D365 evaluates license requirements based on ALL roles assigned to a user
- Combining roles from different workloads can trigger higher licensing
- Some duties span multiple modules (e.g., Finance duties that reference SCM tables)

How to validate:
- Review all security roles assigned to the user
- Use PPAC License Detail export and pivot by user + roles
- Check if removing one role changes the license requirement

Resolution options:
- Remove unnecessary role assignments
- Consolidate roles into a single custom role with only needed permissions
- Ensure role separation aligns with actual job functions
- Assign correct license based on cumulative requirements

Confidence Level: High

---

### Root Cause D: Legacy Licensing Model Assumption

Applies when:
- Customer references "old licensing" or "previous version" behavior
- Expectation is based on pre-enforcement licensing model
- Customer believes role should work with Team Members based on past experience

Why this happens:
- Licensing enforcement and mapping has evolved significantly
- Previous versions may not have enforced license requirements
- AOT metadata updates in PQUs can change object-to-license mappings
- Team Members scope has been clarified to be read-only access

How to validate:
- Ask when the customer last reviewed licensing requirements
- Check if customer is referencing old documentation or assumptions
- Verify customer is on latest PQU with current AOT metadata

Resolution options:
- Reference current licensing guide and documentation
- Explain that licensing enforcement now matches entitlement policy
- Review role requirements against current licensing model
- Update customer expectations to align with current policy

Confidence Level: Medium

---

## 6. Alternative / Edge Case Checks

If no primary root cause applies, check:

- **AOT Object Metadata Update**: Some privileges may have changed license mapping due to product updates
- **Payroll/HR Cross-References**: SCM duties may reference HR/Payroll tables unexpectedly
- **Sandbox vs Production Differences**: Sandbox licensing reports may show different results
- **Device License Confusion**: Customer may be conflating device licenses with user licenses

---

## 7. Resolution Summary (Agent Must Generate)

The agent must summarize:
- Identified root cause (from modules above)
- Why the role requires SCM license instead of Team Members
- Whether behavior is expected or due to misconfiguration
- Specific objects/privileges driving the requirement (if available)
- Recommended next action
- Confidence level

---

## 8. Escalation Criteria

Recommend escalation when **all** of the following are true:

- Root cause cannot be identified using this playbook
- USG/PPAC reports show inconsistent license requirements
- Behavior conflicts with official licensing documentation

Escalation packet must include:
- Environment name and type (Production/Sandbox)
- User email and assigned roles
- Security role names (all roles assigned to user)
- License SKU currently assigned
- USG License Summary screenshot showing license requirement
- Specific object/privilege causing SCM requirement (if known)

---

## 9. Seller-Ready Customer Explanation Template

Provide a short explanation that sellers can share verbatim:

> "Your security role requires an SCM license because it includes permissions to create, update, or delete operational data in Supply Chain Management. Team Members licenses provide read-only access across D365 products. To reduce the license requirement, you can either: (1) use the 'Duplicate with license filter' feature to create a Team Members-compliant read-only version of the role, or (2) remove the write permissions and specific duties that are triggering the SCM requirement. I can help identify which specific objects are driving this requirement by reviewing your User Security Governance report."

---

## 10. Confidence Declaration

The final response must explicitly state one of:
- High confidence – expected behavior based on role design
- Medium confidence – likely configuration-related, needs validation
- Low confidence – escalation recommended
