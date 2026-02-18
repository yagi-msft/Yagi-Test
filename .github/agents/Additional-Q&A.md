---
name: Additional Q&A
description: This is the additional Q&A to be used with the Playbook
---

✅ Category A — License Validation & Enforcement (Phase 1 / Phase 2)
1. When do customers start seeing license enforcement banners?
They appear 30 days before the anniversary/renewal date and apply only to unlicensed users (those with no D365 license).
Users with no license 15 days after anniversary will not be able to log into D365. 
Under‑licensed users (wrong license type assigned) will NOT get banners in current enforcement (Phase 1).
2. Do under‑licensed users get blocked?
Not in Phase 1. Only users with no license assigned get blocked at T+15 days after renewal. But customers are required to follow contractual obligations and purchase the licenses they need. 
3. Does enforcement check for correct base/attach combinations?
No — not until late 2026. Phase 1 only checks whether a license exists, not whether it's the correct SKU.
4. How fast does access restore after assigning a license?
Access returns immediately upon next authentication once the correct license is assigned (allow a few minutes for M365 sync).

✅ Category B — PPAC (Power Platform Admin Center) Reporting Issues
6. Why don’t PPAC and USG (User Security Governance) numbers match?
They operate on different refresh cycles and data models. PPAC may take 4–12 hours to update, whereas in system reports are 2 – 8 hour cycles. This is due to the data pipeline. If after enough time both reports are still unmatched, please reach out to the CoE team. 
7. Why are PPAC reports requiring Global Admin or D365 Admin?
Customers often resist giving broad tenant‑level rights, and PG is evaluating alternatives.
9. Why does PPAC show inconsistent license requirements for users with the same role?
Because license requirements depend on all combined roles, not the single role viewed in isolation.

✅ Category C — USG / Security Role & Privilege Licensing Questions
11. How do we see if a standard role was modified?
Use the audit trail on the role to see changes. You can compare versions and see who made the changes. 
13. Why does a privilege appear under Finance in one version and non-entitled in the next?
Because of AOT metadata updates included in product releases or PQUs.
14. Why do some privileges map to HR (Payroll) unexpectedly?
Some Finance/SCM duties reference Payroll tables. If customers don’t run HR, they may still inherit Payroll-linked privileges.

✅ Category D — Device Licensing & Shared Logins
16. Can 20 workers share a single login on a shop‑floor device?
Yes — if configured as a device user with one of the three predefined roles (Production Floor Worker, Retail Store Manager, Warehouse Worker).
17. Do packing slip updates work under device licenses?
No — packing slip updates exceed the device license scope and require SCM full license.
18. Customers are using browser UI instead of Store Commerce app with device licenses. Is that allowed?
No — device licenses are intended for Store Commerce app scenarios; direct F&O web client access may require full licensing.
19. Will device license enforcement start immediately?
Not yet — device-license validation will come later than user-license validation.
20. Does using WMS scanners require a full user license?
If only using warehouse mobile device (WMDP/WHSMobile) and not F&O web UI, no.
If using F&O UI, yes. Reference device section in Licensing Guide

✅ Category E — Storage & Analytics Hub Questions

23. Has the extra Microsoft storage entitlement (upgraded in December) landed for all customers?
Yes, it’s rolled out. The increase entitlements will show in overall entitlement. 
24. Does storage for Dataverse and F&O combine now?
Yes — combined entitlements apply, and customers may buy Dataverse SKUs for additional capacity.
25. Why do Analytics Hub entitlements appear wrong?
Multiple escalation threads show this is an ongoing issue requiring ICM tickets.

✅ Category F — PQU (Proactive Quality Update) & Versioning Issues
26. Why is the license warning banner showing wrong dates (e.g., Aug 30, 2025)?
Known bug → fixed via PQU.
27. Why doesn’t the banner go away after updating PQU?
Requires both correct PQU and correct license assignment to all users.
28. Where to confirm the latest version for 10.0.45?
Latest build referenced in chat: 10.0.2345.131.
29. Customer applied November PQU but still sees old banner — why?
Latest PQU may not have been applied, or platform build mismatch.
30. Why are some license reports blank in sandbox?
Reports run only on Microsoft‑managed environments. Confirm customer is looking in sandbox and has the USG feature enabled. 
31. What about overages in sandbox?
Sandbox data is only for reporting purpose. This is where customer should test and validate. The final counts don’t include sandbox users. 


✅ Category G — Exceptions, Extensions & Licensing Scenarios
32. Can partners get direct CoE support?
Only via Microsoft internal request. Partners must go through PDM.
33. Customer wants to keep an F&O instance alive with minimal licenses — what’s allowed?
Minimum set: 20 named users with a full license.
34. Can an ISV “bundle” functionality with D365 into a custom SKU?
No — customers must acquire D365 licenses via Microsoft agreements, and ISVs sell separate licenses.
35. Can customers reduce to 20 Finance Premium users for inquiry-only scenarios?
Yes

✅ Category H — Role Cleanup, Security Governance & Optimization
36. How to duplicate roles filtered by license type?
Use the new “Duplicate with license filter” feature released Dec 2025.
37. How do customers prepare for enforcement?
Workflow:

Review licensing guide
Review role-to-license mapping
Remove inactive users
Use USG License Summary
Assign correct licenses in M365

38. Should customers remove unused permissions before enforcement?
Yes — unnecessary entitlements increase cost and trigger higher license types.
39. How to “right-size” roles?
Use USG + Duplicate Role Feature to drop entitlements outside expected license. You can also change write to read to reduce functionalities. 
40. Do personalized roles cause incorrect license triggers?
Yes — especially when sub‑roles include privileges from other workloads (Finance, HR).
41. Why is PPAC recommending SCM base + Finance attach vs Finance base + SCM attach?”
SCM Base with Finance Attach is same as Finance Base with SCM Attach.
✅ Category I — Banner Notifications & Customer Communication
41. Who gets banner notifications?
Only users without any license assigned.
42. Do we tell customers that under‑licensed users won’t be blocked?
No — internal only. Customer messaging must remain:
“Assign the correct license based on usage.” The customers are required to have the license they need. We also don’t want them to have to go through this process multiple times. 

43. Can banners show for customers who should not see them yet?
Yes — documented known issues in December.
44. If customer sees banner early, what should we tell them?
Have them apply PQUs and confirm version; submit a COE request if needed. 
45. Where is the official customer guidance?
MS Learn: “Prepare for user validation”, FAQ, licensing guide.

✅ Category J — Miscellaneous Questions Seen Frequently
46. Are Team Member licenses universal across Sales and F&O?
Team Member grants read access across all D365 products. Please reference the licensing guide. 
48. How to check exact assigned vs required licenses per user?
Use PPAC → License Detail export → pivot by user + roles.	
49. Why does a Finance privilege require SCM or vice versa?
Out of box roles only map to one license. 
50. Why does a certain object require x, y or z licening? 
The D365 reports show exactly which objects are requiring a role to be x, y or z. Removing those objects or making them read-only will remove that requirement. 
