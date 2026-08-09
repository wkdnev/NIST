# AC-06 Least Privilege — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **AC-06-specific content**, implementing targeted least-privilege improvements where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already has an established authentication mechanism and role model;
- enterprise identity lifecycle, MFA, directory services, PAM, managed Windows EUC and shared-platform privilege controls are inherited;
- existing document templates, access-review processes and approval routes will be reused;
- secure development, testing, logging and release processes already exist;
- no major application redesign or wholesale replacement of the authorisation model is required; and
- enterprise IAM, PAM, infrastructure privilege management and shared-platform administration remain outside the application work package.

---

## A. SSP AC-06 Content

Update the existing SSP with a concise AC-06 implementation statement describing how least privilege is applied within the application. Document the application privilege model, separation of ordinary and privileged functions, scope restrictions, privileged and service identities, database and thick-client privilege arrangements where applicable, temporary and emergency privilege controls, review and revocation arrangements, inherited enterprise controls and any approved limitations or excess privilege.

**Estimated effort: 6–10 hours**

---

## B. SyOps Least-Privilege and Privileged Access Content

Update the existing SyOps with operational procedures for administering and maintaining least privilege. Include role and privilege administration responsibilities, privileged and emergency access, temporary elevation, support and impersonation controls, service identity handling, database privilege administration, periodic access review, prompt privilege removal, investigation of excessive or unexpected privilege, and escalation of exceptions or legacy limitations.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Privilege Model Specification

Extend the existing software design to define the application's least-privilege model. Document business, support, administrative and service roles; the exact actions and information scope permitted to each; separation of privileged functions; high-impact capabilities; service and API scopes; application-owned database roles; thick-client privilege expectations; privilege inheritance and role composition; trusted enforcement points; temporary privilege behaviour; and protection of privilege-management configuration.

**Estimated effort: 12–24 hours**

---

## D. Least-Privilege Analysis, Implementation and Enforcement

Review the application against AC-06 requirements and implement any required improvements. Activities may include refining roles and permissions to remove unnecessary access, separating ordinary and privileged functions, scoping permissions by project or information set, restricting high-impact actions, introducing dedicated privileged roles, tightening service identities and API scopes, reducing database privileges, ensuring thick clients operate without unnecessary local elevation, preventing privilege escalation and privileged-function bypass, controlling support impersonation and temporary privilege, separating privilege administration from privilege use where proportionate, and remediating excessive or inherited privilege combinations.

**Estimated effort: 28–80 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to demonstrate that least privilege is correctly enforced. Testing should confirm that each material role, administrator, support user and service identity can perform its approved tasks but cannot perform prohibited actions; verify horizontal and vertical privilege boundaries, privileged API protection, database permissions, thick-client behaviour, temporary-access expiry, support and impersonation controls, workflow and separation-of-duties restrictions, stale-session behaviour after privilege removal, failure handling when privilege information is missing or invalid, and consistency across all relevant interfaces.

**Estimated effort: 16–32 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for maintaining least privilege in operation. Include role and privilege support responsibilities, privileged troubleshooting, temporary or emergency access, support impersonation, service identity and database privilege maintenance, revocation following role or project change, investigation of dormant or excessive access, periodic privilege reviews, handling of legacy or supplier constraints, and escalation into the risk process where minimum privilege cannot be technically achieved.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release and operational acceptance process with AC-06-specific checks. Confirm that the approved privilege model has been deployed, ordinary and privileged functions remain separated, service and database identities are correctly scoped, thick-client privilege requirements are acceptable, high-impact functions are restricted, temporary and support access controls operate as designed, required privileged events are logged, and any unavoidable excessive privilege or exceptions have been formally documented and approved.

**Estimated effort: 6–12 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the AC-06 activities through the existing governance process. Activities include least-privilege gap analysis, stakeholder workshops, business-owner confirmation of minimum required access, design assurance, coordination with AC-03 and AC-05 activities, evidence tracking, privileged-access and exception review, risk management, approval coordination and final compliance review. Existing governance forums and artefacts should be reused rather than creating additional project documentation.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP AC-06 content | **6–10 hours** |
| SyOps least-privilege and privileged access content | **8–16 hours** |
| Software design and privilege model specification | **12–24 hours** |
| Least-privilege analysis, implementation and enforcement | **28–80 hours** |
| Test documentation and evidence | **16–32 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **6–12 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **92–206 hours** |

## Planning interpretation

A mature application with a well-defined role model, distinct privileged functions, tightly scoped service and database identities, standard-user thick-client operation and established access reviews is likely to fall near the lower end of the estimate.

Applications requiring significant role redesign, granular project or information scoping, reduction of broad administrator or service privileges, database privilege separation, thick-client elevation changes, temporary-access controls, support-impersonation restrictions or remediation of legacy privilege-escalation paths are more likely to fall toward the upper end.

The estimate excludes enterprise identity lifecycle management, authentication and MFA services, PAM platform operation, Windows and infrastructure privilege management, enterprise database-platform administration, corporate role-governance tooling, central SIEM and SOC operations, software-distribution elevation mechanisms and other inherited enterprise responsibilities.
