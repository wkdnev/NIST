# AC-03 Access Enforcement — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **AC-03-specific content**, implementing targeted application access enforcement improvements where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already has an established authentication mechanism and role model;
- enterprise identity, MFA, directory services, PAM and network controls are inherited;
- existing document templates and approval routes will be reused;
- secure development, testing and release processes already exist;
- no major application redesign is required; and
- enterprise identity lifecycle and authentication services remain outside the application work package.

---

## A. SSP AC-03 Content

Update the existing SSP with a concise AC-03 implementation statement describing how the application enforces authorisation decisions. Document the protected resources, application authorisation model, trusted enforcement points, inherited enterprise identity services, privileged access approach, application responsibilities, periodic review arrangements and any approved limitations or exceptions.

**Estimated effort: 6–10 hours**

---

## B. SyOps Access Management Content

Update the existing SyOps with operational procedures for administering and supporting application access controls. Include user provisioning responsibilities, privileged and emergency access procedures, access review activities, investigation of access failures, revocation processes, support responsibilities and ongoing operational maintenance of application-specific permissions.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Authorisation Specification

Extend the existing software design to define the application's authorisation architecture. Document the role model, attribute or relationship rules, server-side enforcement points, object and record-level controls, workflow restrictions, separation-of-duties requirements, service identity authorisation, policy decision logic, access refresh or revocation behaviour, fail-secure behaviour and protection of access-control configuration.

**Estimated effort: 12–24 hours**

---

## D. Access Control Analysis, Implementation and Enforcement

Review the application against AC-03 requirements and implement any required improvements. Activities may include defining protected resources and actions, refining the approved role or authorisation model, implementing or improving server-side authorisation, removing client-side trust assumptions, enforcing deny-by-default behaviour, applying least privilege, protecting object, record and field-level access, enforcing workflow restrictions and separation of duties, securing privileged and support functions, restricting service identities and API scopes, preventing direct-object and parameter manipulation, applying consistent controls across browser, thick-client, API, batch, report, export and administrative paths, implementing fail-closed behaviour, refreshing access when user or business context changes, and protecting the authorisation policy and configuration.

**Estimated effort: 24–72 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to demonstrate that access controls operate correctly. Testing should verify authorised and unauthorised access, role enforcement, horizontal and vertical privilege boundaries, object and record-level security, workflow and separation-of-duties restrictions, privileged access, service identities, API security, direct-object and parameter manipulation, stale or revoked access, fail-secure behaviour and consistency across browser, thick-client, API, batch, reporting, export and administrative interfaces. Evidence should be incorporated into the existing security and operational test documentation.

**Estimated effort: 16–32 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for administering and maintaining application access controls. Include access request handling, troubleshooting, privileged and support activities, emergency or delegated access, periodic access reviews, investigation of denied or unexpected access, access revocation, service identity management, handling of access-control failures, and ongoing maintenance of application-specific permissions and policy configuration.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release process with AC-03-specific acceptance checks. Confirm that the approved role and authorisation model has been deployed, protected resources enforce the correct permissions, object and workflow restrictions operate as designed, service identities are correctly scoped, privileged functions are restricted, access-control configuration is protected, required access-control events are generated, and any approved limitations or exceptions have been documented.

**Estimated effort: 6–12 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the AC-03 activities through the existing governance process. Activities include access-control gap analysis, stakeholder workshops, business-owner confirmation of roles and protected information, design assurance, evidence tracking, approval coordination, risk and exception management, and final compliance review. Existing governance processes should be reused rather than creating additional project artefacts.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP AC-03 content | **6–10 hours** |
| SyOps content | **8–16 hours** |
| Software design and authorisation specification | **12–24 hours** |
| Access control analysis, implementation and enforcement | **24–72 hours** |
| Test documentation and evidence | **16–32 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **6–12 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **88–198 hours** |

## Planning interpretation

A mature application with an established role model, trusted server-side authorisation, existing service-identity controls and comprehensive security testing is likely to fall near the lower end of the estimate.

Applications requiring redesign of their authorisation model, implementation of record or field-level security, stronger workflow and separation-of-duties enforcement, service identity restrictions, access refresh or revocation changes, or remediation of inconsistent enforcement across multiple interfaces are more likely to fall toward the upper end.

The estimate excludes enterprise identity management, authentication services, directory administration, multi-factor authentication, privileged-access-management platform operation, enterprise logging and SOC services, network security controls, managed EUC controls and other inherited enterprise responsibilities.
