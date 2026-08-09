# AC-05 Separation of Duties — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **AC-05-specific content**, implementing targeted separation-of-duties improvements where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already has an established role model, access-request process and identifiable business and technical workflows;
- enterprise IAM, PAM, joiner–mover–leaver processes, change control, source-code and deployment platforms, central logging and corporate risk governance are inherited;
- existing role matrices, workflow specifications, SDLC controls, approval routes and test processes will be reused;
- privileged, database, release and support responsibilities are already identifiable within the existing operating model;
- no major organisational restructuring or extensive product redevelopment is required; and
- enterprise separation-of-duties policy, infrastructure administration and organisation-wide governance remain outside the application work package.

---

## A. SSP AC-05 Content

Update the existing SSP with a concise AC-05 implementation statement describing how the application identifies and enforces duties that must remain independent. Document the sensitive business and technical processes in scope, static and dynamic separation approaches, inherited enterprise controls, privileged and administrative separation, SDLC and deployment separation, delegation and emergency override, review arrangements, monitoring and any approved limitations or exceptions.

**Estimated effort: 6–10 hours**

---

## B. SyOps Separation-of-Duties Content

Update the existing SyOps with operational procedures for maintaining required separation in day-to-day operation. Include access request, approval and fulfilment responsibilities; privileged administration and review; business, security, technical, database and audit administration; delegation; emergency override; supplier and support activity; recovery responsibilities; handling of detected conflicts; post-action review; and escalation where staffing or product limitations prevent the intended separation.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Separation-of-Duties Specification

Extend the existing software or security design to define the application's separation-of-duties model. Document sensitive workflows, incompatible roles and duties, static and dynamic conflict rules, originator and material-editor tracking, transaction-level checks, project or information scope, role-conflict evaluation, delegation rules, emergency override, privileged and service identities, workflow and approval thresholds, database migration responsibilities, release gates, audit-administration separation and protection of the configuration that enforces these rules.

**Estimated effort: 14–28 hours**

---

## D. Separation-of-Duties Analysis, Implementation and Enforcement

Review the application against AC-05 requirements and implement any required improvements. Activities may include identifying sensitive business and technical processes, defining incompatible duty combinations, choosing static or dynamic enforcement, preventing self-approval and self-review, checking effective access during provisioning and role change, separating access request, approval and fulfilment, separating privileged administration, use and review, distinguishing business, security, technical, database and audit administration, strengthening development-to-production separation, controlling release artefact approval, database migration and security-configuration changes, applying separation to service identities and automation, protecting delegation and emergency override, and ensuring conflicting actions fail safely when required independence cannot be established.

**Estimated effort: 36–96 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to demonstrate that separation-of-duties controls operate correctly and cannot be bypassed. Testing should cover valid independent approval, denied self-approval, incompatible static role assignment, dynamic conflict on the same transaction, legitimate dual roles on different transactions, inherited or nested-group conflicts, delegated approval, circular delegation, emergency override, expired exceptions, privileged self-assignment, direct API and thick-client bypass attempts, workflow replay, material amendment after approval, database migration separation, development-to-production controls, audit-administration separation, service-identity conflicts, policy or workflow failure, logging and alerting.

**Estimated effort: 20–40 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for administering and troubleshooting separation-of-duties controls. Include investigation of role conflicts and denied approvals, delegated and emergency access, privileged administration, support and supplier conflicts, workflow and approval issues, database and release responsibilities, service-identity conflicts, temporary exceptions, post-use review, escalation of small-team constraints and removal of obsolete roles, delegations and conflicting access.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release and operational acceptance process with AC-05-specific checks. Confirm that approved static and dynamic separation rules are deployed, self-approval and self-granting are prevented, privileged and administrative responsibilities remain separated, development and production controls operate as designed, database migration and security-configuration approvals are independent where required, delegation and emergency override are constrained, service identities do not combine incompatible duties, required events are generated, and any accepted conflicts or exceptions have been documented.

**Estimated effort: 8–16 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the AC-05 activities through the existing governance process. Activities include separation-of-duties gap analysis, workshops with business owners, application support, security, database and release stakeholders, agreement of incompatible duties, review of staffing and supplier constraints, design assurance, evidence tracking, periodic review planning, alignment with AC-02, AC-03, AC-06, CM-03, CM-05, CM-06, SI-07, SA-11, AU-02, SI-04 and CA-07 activities, risk and exception management, approval coordination and final compliance review. Existing governance forums and artefacts should be reused rather than creating additional project documentation.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP AC-05 content | **6–10 hours** |
| SyOps separation-of-duties content | **8–16 hours** |
| Software design and separation-of-duties specification | **14–28 hours** |
| Separation-of-duties analysis, implementation and enforcement | **36–96 hours** |
| Test documentation and evidence | **20–40 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **8–16 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **108–238 hours** |

## Planning interpretation

A mature application with a clear approval model, effective role-conflict checks, established privileged-access controls, protected SDLC and deployment pipelines, controlled database change and existing security testing is likely to fall near the lower end of the estimate.

Applications with complex approval workflows, project-specific conflicts, broad administrator roles, manual or weakly controlled deployment, direct production database activity, extensive delegation, supplier-developed components, service identities performing multiple workflow stages or small-team staffing constraints are more likely to fall toward the upper end.

The estimate excludes enterprise separation-of-duties policy, organisation-wide role and line-management structures, IAM and PAM platform engineering, corporate joiner–mover–leaver processes, enterprise change and release governance, centrally operated source-code and deployment platforms, infrastructure and database-platform administration, central SIEM and SOC operations, corporate audit functions and other inherited enterprise responsibilities.
