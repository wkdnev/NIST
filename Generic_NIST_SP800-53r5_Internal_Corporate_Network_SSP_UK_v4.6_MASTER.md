# NIST SP 800-53 Release 5.2.0 — Access Control (AC) Family  
## Application Actions, Deliverables, Evidence and Effort

**Scope:** Internal IT applications operating on a large enterprise corporate network  
**Perspective:** Application-specific responsibilities only  
**Language:** UK English  
**Catalogue:** NIST SP 800-53 Release 5.2.0 and corresponding SP 800-53A Release 5.2.0 assessment procedures

---

## 1. Executive summary

This report translates the complete NIST SP 800-53 Release 5.2.0 Access Control family, **AC-01 through AC-25**, into actions that belong to an individual IT application.

The assumed enterprise provides and operates:

- corporate networks and network-security infrastructure;
- physical and virtual servers;
- enterprise server operating systems;
- managed Microsoft Windows end-user compute devices;
- corporate identity and directory services;
- enterprise multi-factor authentication;
- VPN and remote-access services;
- device-compliance services;
- privileged-access-management platforms;
- central logging, SIEM and security operations;
- enterprise configuration, patching and vulnerability services;
- approved collaboration and data-transfer services;
- organisation-wide policies, standards and governance; and
- enterprise risk, exception and assurance processes.

The application is the complete collection of software, configuration, databases, clients, interfaces, integrations and application-specific services that delivers a business function. An example is an Engineering Requirements Management System consisting of a thick client, browser interface, application services, database schemas, file-processing services, integrations, reporting and application-specific administration.

This report deliberately excludes implementation work owned wholly by enterprise infrastructure teams. It concentrates on what the application owner, product team, supplier, developer, integrator and application support team must do.

### 1.1 Controls covered

The Access Control family contains 25 numbered base-control positions:

1. AC-01 — Policy and Procedures  
2. AC-02 — Account Management  
3. AC-03 — Access Enforcement  
4. AC-04 — Information Flow Enforcement  
5. AC-05 — Separation of Duties  
6. AC-06 — Least Privilege  
7. AC-07 — Unsuccessful Logon Attempts  
8. AC-08 — System Use Notification  
9. AC-09 — Previous Logon Notification  
10. AC-10 — Concurrent Session Control  
11. AC-11 — Device Lock  
12. AC-12 — Session Termination  
13. AC-13 — Supervision and Review — Access Control *(withdrawn)*  
14. AC-14 — Permitted Actions Without Identification or Authentication  
15. AC-15 — Automated Marking *(withdrawn)*  
16. AC-16 — Security and Privacy Attributes  
17. AC-17 — Remote Access  
18. AC-18 — Wireless Access  
19. AC-19 — Access Control for Mobile Devices  
20. AC-20 — Use of External Systems  
21. AC-21 — Information Sharing  
22. AC-22 — Publicly Accessible Content  
23. AC-23 — Data Mining Protection  
24. AC-24 — Access Control Decisions  
25. AC-25 — Reference Monitor  

AC-13 and AC-15 are retained as withdrawn placeholders. They do not require separate implementation statements beyond recording their withdrawn status and mapping relevant intent to successor controls.

### 1.2 Base controls versus enhancements

This report addresses the **base controls** AC-01 to AC-25. Control enhancements must be added where selected by the organisation’s baseline, tailoring decision, risk assessment, contractual requirement or application-specific threat model.

The application SSP should identify:

- selected base controls;
- selected enhancements;
- organisation-defined parameters;
- inherited controls;
- application-implemented controls;
- shared controls;
- non-applicable controls;
- and approved deviations.

---

## 2. Recommended evidence model

To avoid creating a large set of disconnected compliance documents, the application should use a small, coherent evidence set.

### 2.1 Core application artefacts

| Artefact | Primary Access Control content |
|---|---|
| **Application SSP and application-specific addendum** | Control implementation statements, inherited controls, applicability, parameters, exceptions and evidence references |
| **Security architecture and data-flow diagrams** | Trust boundaries, access paths, tiers, interfaces, remote paths, information flows and enforcement points |
| **Identity, account and access-management design** | Identity sources, account lifecycle, role model, authentication context, local accounts and service identities |
| **Role and permission matrix** | Roles, permissions, information scope, privileged functions, conflicts and approval authorities |
| **Information-flow and sharing specification** | Project, tenant, record, classification, recipient, destination, export and integration rules |
| **ConOps / SyOps / support model** | Operational account administration, privileged access, supplier support, remote access, exception and incident procedures |
| **Application configuration specification** | Session, lockout, timeout, banner, endpoint, feature, export and security-attribute settings |
| **Interface and API specifications** | Caller identities, scopes, object access, data flows, callback restrictions and service permissions |
| **Security test plan and report** | Positive, negative, bypass, role, information-flow, remote, session and failure tests |
| **Access-review and governance records** | Periodic account, role, supplier, privilege, sharing and exception reviews |
| **Risk register / POA&M / problem records** | Deviations, limitations, compensating controls, owners, expiry and remediation |
| **Logging and monitoring specification** | Authentication, authorisation, privilege, session, sharing and control-failure events |
| **Change and release records** | Access-impact assessment, configuration changes, role changes and post-change verification |

### 2.2 Evidence quality rules

Evidence should be:

- attributable;
- dated;
- version controlled;
- tied to the deployed application version;
- approved by an accountable owner;
- stored in an approved repository;
- sufficiently detailed to reproduce the result;
- protected according to sensitivity;
- and referenced from the SSP rather than copied repeatedly.

---

# 3. Detailed control actions

---

## AC-01 — Policy and Procedures

### Application intent

The application must translate enterprise Access Control policy into application-specific operating rules, responsibilities, configuration and evidence.

### Application actions

1. Identify the enterprise Access Control policies, standards and procedures that apply.
2. Define the application-specific interpretation of those requirements.
3. Identify which controls are inherited, shared, application implemented, non-applicable or subject to exception.
4. Assign application roles for:
   - account ownership;
   - access approval;
   - role design;
   - privileged access;
   - supplier access;
   - access review;
   - security monitoring;
   - exception approval; and
   - control evidence maintenance.
5. Define application-specific procedures for:
   - account provisioning;
   - access modification;
   - account disablement;
   - privileged access;
   - emergency access;
   - supplier access;
   - remote access;
   - sharing;
   - access review;
   - access incidents; and
   - control changes.
6. Review application procedures after material change, incident, audit finding or policy update.
7. Record justified deviations from enterprise standards through the formal exception process.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| AC-family SSP implementation statements | Approved SSP sections showing inherited and application controls | 12–24 hours |
| Application Access Control RACI | Named accountable and responsible roles | 4–8 hours |
| Application access procedures | Procedures embedded in SyOps, support model and IAM runbooks | 12–28 hours |
| Annual or change-driven review | Review record, approval and tracked updates | 4–10 hours per review |
| Exception records | Approved risk record with compensating controls and expiry | 4–10 hours per exception |

### Enterprise responsibilities excluded

Enterprise policy ownership, enterprise identity governance, corporate access standards, organisation-wide training and enterprise exception governance.

**Indicative application effort:** **32–70 hours initially**, then **4–12 hours per review cycle**.

---

## AC-02 — Account Management

### Application intent

The application must manage every account and identity mapping needed to use or operate the application.

### Application actions

1. Inventory application accounts:
   - federated user accounts;
   - local accounts;
   - privileged accounts;
   - service accounts;
   - API clients;
   - supplier accounts;
   - temporary accounts;
   - emergency accounts; and
   - test accounts.
2. Define account types permitted and prohibited.
3. Assign an owner and business purpose to each non-person account.
4. Use enterprise identity as the authoritative source for workforce users.
5. Define account approval and role-assignment workflows.
6. Ensure joiner, mover and leaver events produce timely application changes.
7. Disable dormant, expired, orphaned and unowned accounts.
8. Restrict and periodically review privileged, supplier and emergency accounts.
9. Prevent duplicate or ambiguous mappings from enterprise identities.
10. Reconcile application accounts with enterprise identity, HR, supplier and service inventories.
11. Protect account-management functions through least privilege and separation of duties.
12. Log account creation, change, disablement, deletion and reactivation.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Account-type and lifecycle specification | Approved identity and account design | 12–24 hours |
| Account inventory and ownership records | Current account/service-account register | 12–28 hours |
| Provisioning and deprovisioning workflow | Tested workflow and service-management evidence | 16–36 hours |
| Periodic account reconciliation | Reconciliation report and closure actions | 8–20 hours per review |
| Privileged and supplier account review | Approved review evidence | 6–16 hours per review |
| Account-management security tests | Positive, negative and lifecycle test results | 16–36 hours |

### Enterprise responsibilities excluded

Corporate identity proofing, HR joiner–mover–leaver source data, enterprise directory operation, enterprise MFA and central PAM platform operation.

**Indicative application effort:** **80–180 hours initially**, then **8–25 hours per month or review cycle**.

---

## AC-03 — Access Enforcement

### Application intent

The application must enforce approved access permissions on every application request and object.

### Application actions

1. Define the application role and permission model.
2. Map corporate identities and groups to application roles.
3. Enforce authorisation server-side.
4. Apply object, record, project, tenant, field and function-level checks.
5. Enforce workflow-state restrictions.
6. Protect administrative and support functions.
7. Enforce API and service scopes independently of user-interface restrictions.
8. Deny by default where no explicit permission exists.
9. Revalidate access after role, account, project or workflow changes.
10. Prevent direct URL, API, database or thick-client bypass.
11. Record material access decisions and denials.
12. Test every significant role and prohibited path.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Role and permission model | Approved role matrix and access-control design | 20–50 hours |
| Server-side enforcement implementation | Code/configuration and peer-review evidence | 40–160 hours |
| API/object-level authorisation specification | Interface design and test traceability | 16–40 hours |
| Access-control test suite | Positive, negative, cross-project and bypass tests | 32–80 hours |
| Access-denial logging | Event catalogue and SIEM test evidence | 8–20 hours |
| Periodic permission review | Approved review and remediation record | 8–20 hours per review |

### Enterprise responsibilities excluded

Enterprise directory, network access control, operating-system access control and enterprise identity-provider enforcement.

**Indicative application effort:** **120–350 hours initially**, then **10–30 hours per material release or review**.

---

## AC-04 — Information Flow Enforcement

### Application intent

The application must control where information may flow, independently of whether the user can access the application function.

### Application actions

1. Map information flows between:
   - users;
   - projects;
   - tenants;
   - components;
   - environments;
   - APIs;
   - integrations;
   - reports;
   - exports;
   - email;
   - file stores;
   - suppliers; and
   - external systems.
2. Define approved source, destination, information type and purpose for each flow.
3. Enforce project, tenant, classification, recipient and destination restrictions.
4. Prevent production-to-non-production leakage.
5. Restrict reports, bulk exports, downloads and notifications.
6. Validate message, API, file and integration destinations.
7. Prevent arbitrary callbacks, redirects and user-supplied external destinations.
8. Preserve handling attributes during processing and export.
9. Log denied and high-risk information flows.
10. Test cross-boundary and indirect-flow scenarios.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Information-flow inventory | Architecture and approved flow register | 20–50 hours |
| Flow-enforcement requirements | AC-04 design and interface specifications | 20–50 hours |
| Export/report controls | Tested configuration and role restrictions | 20–60 hours |
| Integration destination controls | Allow-lists, validation and interface tests | 16–48 hours |
| Cross-boundary test suite | Cross-project, report, API and export tests | 24–60 hours |
| Flow exception records | Risk acceptance with monitoring and expiry | 4–10 hours each |

### Enterprise responsibilities excluded

Enterprise firewalls, DLP platforms, network segmentation, email gateways and organisation-wide data-sharing policy.

**Indicative application effort:** **110–280 hours initially**, then **8–25 hours per major change or review**.

---

## AC-05 — Separation of Duties

### Application intent

The application must prevent one identity from controlling incompatible stages of a sensitive process.

### Application actions

1. Identify incompatible application duties.
2. Define role conflicts for:
   - request and approval;
   - creation and release;
   - development and production administration;
   - access request and approval;
   - security configuration and audit review;
   - supplier action and internal approval;
   - data correction and approval; and
   - emergency action and post-use review.
3. Configure role-conflict rules.
4. Prevent self-approval and self-granting.
5. Control delegation and temporary role combinations.
6. Define emergency overrides and independent review.
7. Review users with multiple roles.
8. Test workflow, API and administrative bypass paths.
9. Log conflict denials and overrides.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Separation-of-duties analysis | Approved conflict matrix | 12–28 hours |
| Role/workflow implementation | Configuration or code evidence | 20–60 hours |
| Delegation and emergency procedure | SyOps and tested workflow | 8–20 hours |
| Conflict test suite | Self-approval, API and role-combination tests | 16–40 hours |
| Periodic conflict review | Review evidence and remediation | 6–16 hours per review |

### Enterprise responsibilities excluded

Organisation-wide job-design policy, HR role ownership and enterprise PAM platform operation.

**Indicative application effort:** **60–150 hours initially**, then **6–18 hours per review**.

---

## AC-06 — Least Privilege

### Application intent

Every user, administrator, service and integration should receive only the permissions needed for its approved purpose.

### Application actions

1. Define least-privilege roles.
2. Separate ordinary, privileged, support, reporting, deployment and database functions.
3. Minimise service-account and API scopes.
4. Prohibit routine use of shared or generic privileged accounts.
5. Restrict direct database and server access.
6. Use time-limited or just-in-time privilege where available.
7. Restrict support impersonation.
8. Remove dormant and unused permissions.
9. Review effective permissions, including inherited group membership.
10. Log privileged assignment and use.
11. Test that lower-privileged identities cannot invoke privileged functions.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Least-privilege role design | Role matrix and permission rationale | 16–36 hours |
| Privileged-function inventory | Approved privileged-access design | 8–20 hours |
| Service/API privilege review | Service-account and interface records | 12–28 hours |
| Privilege reduction implementation | Configuration/change evidence | 16–60 hours |
| Privileged-access testing | Negative and escalation tests | 20–48 hours |
| Periodic privilege review | Review and removal evidence | 8–20 hours per review |

### Enterprise responsibilities excluded

Enterprise privileged-access policy, PAM infrastructure, operating-system administrator roles and corporate directory administration.

**Indicative application effort:** **80–190 hours initially**, then **8–25 hours per review**.

---

## AC-07 — Unsuccessful Logon Attempts

### Application intent

The application must limit and respond to repeated failed authentication attempts where the application performs or controls authentication.

### Application actions

1. Prefer enterprise authentication and inherit enterprise lockout or throttling.
2. For application-local authentication, define:
   - threshold;
   - observation window;
   - lockout or delay;
   - recovery;
   - privileged-account treatment;
   - service-account treatment;
   - and denial-of-service safeguards.
3. Rate-limit failed authentication and recovery attempts.
4. Avoid revealing whether an account exists.
5. Log failed attempts and threshold actions.
6. Alert on suspicious patterns where required.
7. Test lockout, delay, recovery and distributed attempts.
8. Ensure service integrations do not cause uncontrolled lockout loops.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Authentication-failure design | IA/AC configuration specification | 4–10 hours |
| Local lockout/rate-limit configuration | Tested application settings | 8–24 hours |
| Failure-event logging | AU-02 specification and SIEM evidence | 4–10 hours |
| Security tests | Threshold, reset and bypass results | 8–20 hours |
| Exception for product limitations | Risk record and compensating controls | 4–10 hours |

### Enterprise responsibilities excluded

Enterprise directory lockout, MFA throttling and identity-provider monitoring.

**Indicative application effort:** **20–55 hours** where local authentication exists; **8–20 hours** where fully inherited.

---

## AC-08 — System Use Notification

### Application intent

The application must display the approved system-use notice before granting access where the enterprise notice is not already sufficient or where application-specific terms are required.

### Application actions

1. Determine whether the enterprise EUC, VPN or identity service notice fully satisfies the requirement.
2. Identify application-specific notice requirements.
3. Display the notice before authentication or before access is granted, as required.
4. Ensure the notice:
   - uses approved wording;
   - does not expose sensitive system information;
   - is consistently presented;
   - cannot be bypassed through alternate clients or interfaces where applicable; and
   - is accessible.
5. Version and control the text.
6. Test browser and thick-client presentation.
7. Record legal or policy approval.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Applicability decision | SSP statement referencing inherited notice | 2–4 hours |
| Application banner text | Approved legal/security wording | 3–8 hours |
| Implementation | Configuration or code evidence | 4–12 hours |
| Test evidence | Screenshots and functional test | 2–6 hours |

### Enterprise responsibilities excluded

Corporate acceptable-use policy and enterprise workstation/VPN banners.

**Indicative application effort:** **6–25 hours**.

---

## AC-09 — Previous Logon Notification

### Application intent

Where selected and applicable, the application should notify users of previous successful or unsuccessful logon information to help identify misuse.

### Application actions

1. Determine applicability based on baseline, risk and enterprise identity capability.
2. Define which previous-logon details are shown:
   - date and time;
   - successful or failed status;
   - client or access context where trustworthy;
   - and number of unsuccessful attempts.
3. Avoid exposing sensitive network or device information.
4. Ensure the information belongs to the authenticated identity.
5. Handle first use and unavailable history safely.
6. Log presentation failures.
7. Test browser, thick-client and accessibility behaviour.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Applicability and design decision | SSP and identity design | 3–8 hours |
| Implementation | Application session/login feature | 8–24 hours |
| Security and privacy review | Approved displayed fields | 3–8 hours |
| Test evidence | Functional and identity-isolation tests | 6–16 hours |

### Enterprise responsibilities excluded

Enterprise identity-provider logon history unless directly presented by the enterprise service.

**Indicative application effort:** **15–45 hours** if required; **2–5 hours** if documented as inherited or not selected.

---

## AC-10 — Concurrent Session Control

### Application intent

The application must limit concurrent sessions where required by risk, licence, privilege or selected control parameters.

### Application actions

1. Define which users and roles require session limits.
2. Distinguish browser, thick-client, API, privileged and supplier sessions.
3. Define:
   - maximum concurrent sessions;
   - session uniqueness;
   - stale-session handling;
   - user notification;
   - administrative termination;
   - and exception handling.
4. Prevent bypass through alternate endpoints or clients.
5. Treat service accounts separately from human sessions.
6. Log limit enforcement and administrative termination.
7. Test race conditions, reconnect and distributed sessions.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Session-limit specification | Session-management design | 4–10 hours |
| Implementation and configuration | Code/configuration evidence | 12–36 hours |
| Session administration procedure | SyOps/support model | 3–8 hours |
| Concurrency test suite | Browser, client, API and race tests | 8–24 hours |

### Enterprise responsibilities excluded

Enterprise VPN session limits and EUC sign-in controls.

**Indicative application effort:** **25–70 hours** if selected.

---

## AC-11 — Device Lock

### Application intent

Device lock is normally inherited from managed corporate EUC. The application must avoid defeating it and should protect application state when the device locks.

### Application actions

1. Record inheritance from corporate Windows EUC lock controls.
2. Ensure the application:
   - does not prevent device lock;
   - does not keep sensitive pop-ups or overlays visible unnecessarily;
   - handles workstation lock and unlock safely;
   - revalidates privileged or sensitive sessions where warranted;
   - protects local cache;
   - and does not expose secrets in notifications.
3. For thick clients, test state after lock, sleep, hibernate and user switch.
4. For privileged functions, consider application reauthentication after device unlock.
5. Document product limitations.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Inherited-control statement | SSP AC-11 section | 2–4 hours |
| Thick-client/session behaviour design | Client and session specification | 4–12 hours |
| Device-lock tests | Lock, unlock, sleep and user-switch evidence | 6–16 hours |
| Limitation record | Risk record if state remains exposed | 4–10 hours |

### Enterprise responsibilities excluded

Windows lock configuration, inactivity period, screen-lock policy and endpoint management.

**Indicative application effort:** **10–30 hours**.

---

## AC-12 — Session Termination

### Application intent

The application must terminate or invalidate sessions after defined conditions.

### Application actions

1. Define termination conditions:
   - inactivity;
   - absolute lifetime;
   - sign-out;
   - account disablement;
   - role removal;
   - supplier expiry;
   - emergency privilege expiry;
   - token expiry;
   - password or authenticator reset where applicable;
   - security incident;
   - and administrative revocation.
2. Terminate browser, thick-client, API and impersonation sessions.
3. Invalidate refresh tokens where appropriate.
4. Prevent stale sessions from retaining removed privilege.
5. Provide administrative session revocation.
6. Log termination and failure.
7. Test disconnect, reconnect, race and cached-token scenarios.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Session-termination specification | Identity/session design | 8–18 hours |
| Implementation and configuration | Code/configuration and review | 16–60 hours |
| Administrative revocation procedure | SyOps and support evidence | 4–10 hours |
| Session test suite | Timeout, disablement, role removal and token tests | 16–40 hours |

### Enterprise responsibilities excluded

VPN termination, enterprise identity token policy and EUC lock.

**Indicative application effort:** **45–120 hours initially**.

---

## AC-13 — Supervision and Review — Access Control *(Withdrawn)*

### Application treatment

AC-13 is withdrawn. No separate application implementation is required.

The application should:

1. Mark AC-13 as withdrawn in the SSP.
2. Avoid creating a duplicate control statement.
3. Map relevant review and supervision evidence to:
   - AC-02 account reviews;
   - AC-05 separation of duties;
   - AC-06 least privilege;
   - AU-06 audit review;
   - CA-07 continuous monitoring; and
   - applicable governance controls.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Withdrawn-control statement | SSP records AC-13 as withdrawn | 1–2 hours |
| Successor-control cross-reference | SSP mapping | 1–2 hours |

**Indicative application effort:** **2–4 hours**.

---

## AC-14 — Permitted Actions Without Identification or Authentication

### Application intent

The application must explicitly identify any functions permitted before authentication and prevent all others.

### Application actions

1. Inventory pre-authentication functions.
2. Default to no unauthenticated business access.
3. Justify each permitted function, such as:
   - health status;
   - static help;
   - approved banner;
   - authentication initiation;
   - password recovery where local;
   - or limited service discovery.
4. Ensure unauthenticated functions expose no restricted data.
5. Prevent enumeration, excessive detail and indirect access.
6. Restrict unauthenticated APIs.
7. Rate-limit abuse-prone functions.
8. Log relevant use and failures.
9. Test direct URLs, API calls, parameters and error paths.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Pre-authentication function inventory | SSP and interface design | 4–10 hours |
| Risk justification | Approved security design | 4–10 hours |
| Enforcement implementation | Code/configuration evidence | 8–30 hours |
| Unauthenticated-access tests | Direct, API and enumeration tests | 12–28 hours |

### Enterprise responsibilities excluded

Public network exposure controls and enterprise identity-provider pre-authentication pages.

**Indicative application effort:** **30–75 hours**.

---

## AC-15 — Automated Marking *(Withdrawn)*

### Application treatment

AC-15 is withdrawn. Relevant marking and attribute functionality is addressed principally through AC-16 and information-handling controls.

The application should:

1. Mark AC-15 as withdrawn in the SSP.
2. Cross-reference application marking and handling requirements to:
   - AC-16 security and privacy attributes;
   - AC-04 information flow;
   - MP controls;
   - SC-16 transmission of attributes; and
   - information-classification requirements.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Withdrawn-control statement | SSP records AC-15 as withdrawn | 1–2 hours |
| Successor-control cross-reference | SSP mapping | 1–2 hours |

**Indicative application effort:** **2–4 hours**.

---

## AC-16 — Security and Privacy Attributes

### Application intent

The application must associate, preserve and use security and privacy attributes needed to make access and information-flow decisions.

### Application actions

1. Identify required attributes, such as:
   - user role;
   - project membership;
   - tenant;
   - organisation;
   - clearance or authorisation;
   - record classification;
   - sensitivity;
   - owner;
   - releasability;
   - purpose;
   - retention category;
   - legal hold;
   - supplier restriction;
   - and privacy handling.
2. Define authoritative sources.
3. Define allowed values and validation.
4. Bind attributes to users, records, files, messages and exports.
5. Protect attribute integrity.
6. Restrict who may assign or change attributes.
7. Preserve attributes through interfaces, exports, copies and archives.
8. Re-evaluate access when attributes change.
9. Log attribute changes.
10. Test missing, forged, stale and conflicting attributes.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Attribute catalogue | Approved data and access design | 16–36 hours |
| Attribute authority and lifecycle model | Identity/data model | 12–28 hours |
| Attribute enforcement implementation | Code/configuration evidence | 24–80 hours |
| Interface/format mapping | API, file and message specifications | 12–36 hours |
| Attribute security tests | Forgery, omission, change and propagation tests | 20–48 hours |

### Enterprise responsibilities excluded

Enterprise classification policy, corporate directory attributes and organisation-wide privacy taxonomy.

**Indicative application effort:** **90–220 hours**.

---

## AC-17 — Remote Access

### Application intent

Remote users must reach the application only through approved enterprise remote-access services and remain subject to full application-layer access control.

### Application actions

1. Define permitted remote functions and prohibited functions.
2. Require approved internal endpoints.
3. Use corporate identity and required authentication context.
4. Do not trust VPN or corporate IP address alone.
5. Protect sessions independently of VPN timeout.
6. Handle VPN loss and reconnect safely.
7. Restrict privileged, supplier and emergency remote access.
8. Protect thick-client caches and tokens.
9. Restrict remote export and download where required.
10. Log remote, privileged and supplier activity.
11. Test no-VPN, alternate-route, session and reconnect scenarios.
12. Document inherited VPN, MFA, device-compliance and no-split-tunnelling controls.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Remote-access application model | SSP, architecture and SyOps | 8–18 hours |
| Remote function restrictions | Role/access matrix | 8–20 hours |
| Session and reconnect design | Client/session specification | 12–32 hours |
| Privileged/supplier remote procedure | PAM/support records | 8–20 hours |
| Remote-access tests | Approved/prohibited route and failure tests | 20–48 hours |

### Enterprise responsibilities excluded

VPN, MFA, device compliance, endpoint hardening, split-tunnel enforcement and remote-access gateway operation.

**Indicative application effort:** **90–210 hours initially**.

---

## AC-18 — Wireless Access

### Application intent

Wireless infrastructure is normally enterprise owned. The application must ensure that wireless connectivity does not create an alternate application access model or weakened control path.

### Application actions

1. Record inheritance from approved enterprise wireless controls.
2. Confirm the application is reached through the same approved internal endpoints and identity controls.
3. Do not create application-specific wireless hotspots, direct device pairing or ad hoc wireless services.
4. Prevent thick clients from discovering or connecting to unapproved local services.
5. Treat wireless network location as untrusted for application authorisation.
6. Define whether sensitive or privileged functions have additional restrictions.
7. Test that guest or unauthorised wireless paths cannot reach the application.
8. Document any product requirement for Bluetooth, Wi-Fi Direct or local wireless communication as an exception.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Inherited-control statement | SSP AC-18 section | 2–4 hours |
| Architecture confirmation | Approved network/access diagram | 3–8 hours |
| Wireless-path test | Guest/unauthorised route results | 4–12 hours |
| Exception record if needed | Approved risk and design | 6–16 hours |

### Enterprise responsibilities excluded

Corporate wireless access points, wireless authentication, RF monitoring and network segmentation.

**Indicative application effort:** **8–25 hours** without special wireless features.

---

## AC-19 — Access Control for Mobile Devices

### Application intent

For an application designed only for managed Windows EUC, mobile-device access should normally be prohibited or unsupported.

### Application actions

1. Define whether mobile access is:
   - prohibited;
   - unsupported;
   - browser-only under enterprise mobile management;
   - or explicitly authorised.
2. Avoid publishing mobile applications or responsive access paths unintentionally.
3. Prevent access from unmanaged mobile clients where enterprise context is available.
4. Restrict mobile download, local storage and offline access.
5. Protect tokens and notifications.
6. Prohibit direct use from personal phones or tablets.
7. Test mobile user agents, alternate clients and direct APIs.
8. Manage any authorised mobile exception through enterprise approval.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Mobile applicability decision | SSP and ConOps | 3–8 hours |
| Technical restriction configuration | Identity/app configuration | 6–20 hours |
| Mobile/API tests | Unmanaged and direct-client results | 8–20 hours |
| Exception design if authorised | Risk, architecture and support model | 20–60 hours |

### Enterprise responsibilities excluded

Mobile-device management, mobile operating systems, device compliance and corporate mobile policy.

**Indicative application effort:** **15–45 hours** where mobile is prohibited; more if authorised.

---

## AC-20 — Use of External Systems

### Application intent

Application information and functions must not use unmanaged, personal, supplier or public systems unless explicitly authorised.

### Application actions

1. Identify ways application information could reach external systems.
2. Prohibit direct Internet and consumer-service integration.
3. Restrict access to managed corporate EUC.
4. Disable public cloud, personal storage, public AI, telemetry and unapproved support connectors.
5. Restrict exports and destinations.
6. Control supplier devices, support platforms and diagnostic transfers.
7. Require approved agreements for any authorised external system.
8. Protect external connection credentials.
9. Log external transfers and denied destinations.
10. Review and terminate external connections.
11. Test personal email, arbitrary callback, public storage and unmanaged-client paths.
12. Record exceptions with expiry.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| External-system flow assessment | AC-04/SC-07 flow inventory | 12–28 hours |
| Prohibited connector review | CM-07 and configuration evidence | 8–24 hours |
| Export/destination controls | Design, configuration and tests | 16–40 hours |
| Supplier/external connection record | Agreement and interface evidence | 12–28 hours each |
| External-system tests | Destination, client and connector tests | 16–40 hours |
| Periodic external-use review | Governance record | 6–16 hours |

### Enterprise responsibilities excluded

Corporate BYOD policy, egress filtering, DLP, supplier contracting and approved SaaS governance.

**Indicative application effort:** **90–210 hours initially**, plus **40–120 hours per authorised external connection**.

---

## AC-21 — Information Sharing

### Application intent

The application must enable authorised sharing while preventing sharing beyond approved recipients, purposes and information scope.

### Application actions

1. Define authorised sharing scenarios.
2. Identify:
   - sender;
   - recipient;
   - information;
   - purpose;
   - authority;
   - destination;
   - duration;
   - and onward-use restrictions.
3. Enforce project, organisation, role and record scope.
4. Validate recipients and distribution lists.
5. Require approval for high-risk or bulk sharing.
6. Apply markings and handling instructions.
7. Prevent unauthorised forwarding, export or public links.
8. Record sharing decisions and outcomes.
9. Review standing shares and scheduled reports.
10. Test cross-project, recipient-manipulation and indirect sharing.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Information-sharing rules | Sharing matrix and business/security requirements | 12–30 hours |
| Recipient and destination controls | Application/interface design | 16–48 hours |
| Sharing approval workflow | Workflow evidence | 12–36 hours |
| Marking/handling implementation | Data/export design | 8–24 hours |
| Sharing test suite | Cross-boundary and recipient tests | 16–40 hours |
| Standing-share review | Review and revocation evidence | 6–16 hours |

### Enterprise responsibilities excluded

Organisation-wide information-sharing policy, approved collaboration platforms and external agreements.

**Indicative application effort:** **75–190 hours**.

---

## AC-22 — Publicly Accessible Content

### Application intent

For an internal-only application, publicly accessible content should normally be absent.

### Application actions

1. Confirm no public application endpoint, public content repository or anonymous publishing feature exists.
2. Identify any function capable of:
   - public link creation;
   - unauthenticated publishing;
   - Internet-facing content;
   - public API output;
   - or search-engine indexing.
3. Disable unneeded public-sharing features.
4. If public content is authorised:
   - assign content owners;
   - establish approval;
   - review content before publication;
   - remove sensitive information;
   - review periodically;
   - correct or remove inappropriate content;
   - and log publication.
5. Test public routes, anonymous links and product defaults.
6. Record the control as not applicable only if the organisation’s tailoring process permits that determination; otherwise describe the implemented prohibition.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Public-content applicability assessment | SSP and architecture | 3–8 hours |
| Product feature review | CM-07 evidence | 4–12 hours |
| External-route test | Security test results | 6–16 hours |
| Publication workflow if applicable | Content approval and review records | 20–60 hours |

### Enterprise responsibilities excluded

Corporate public website governance and Internet perimeter controls.

**Indicative application effort:** **12–35 hours** for an internal-only application.

---

## AC-23 — Data Mining Protection

### Application intent

The application must reduce the risk that users or services can aggregate, correlate or extract information beyond their authorised purpose.

### Application actions

1. Identify data-mining risks:
   - bulk search;
   - unrestricted reports;
   - high-volume API use;
   - exports;
   - inference from counts;
   - cross-project aggregation;
   - metadata correlation;
   - and repeated queries.
2. Define permitted analytical use.
3. Restrict query scope by role, project and purpose.
4. Limit bulk export and high-volume access.
5. Apply rate, row, field, time-range and result limits where appropriate.
6. Prevent users from combining individually permitted outputs into unauthorised datasets.
7. Restrict service and reporting identities.
8. Monitor unusual query and export patterns.
9. Test inference, aggregation and pagination bypass.
10. Document unavoidable analytical capability and residual risk.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Data-mining threat assessment | Threat model and risk assessment | 12–28 hours |
| Query/report restrictions | Design and role matrix | 16–48 hours |
| API and export limits | Interface/configuration evidence | 12–36 hours |
| Monitoring use cases | AU-02/SI-04 specification | 8–20 hours |
| Mining/inference tests | Bulk, pagination and aggregation tests | 16–40 hours |

### Enterprise responsibilities excluded

Enterprise DLP analytics, corporate insider-risk programme and organisation-wide data-science governance.

**Indicative application effort:** **70–170 hours**.

---

## AC-24 — Access Control Decisions

### Application intent

The application must establish and enforce a clear, trustworthy method for making access-control decisions.

### Application actions

1. Define the access decision architecture:
   - policy enforcement points;
   - policy decision points;
   - identity and attribute sources;
   - policy stores;
   - and decision outputs.
2. Ensure decisions use authoritative, current identity and security attributes.
3. Define deny-by-default behaviour.
4. Define behaviour when:
   - identity data is unavailable;
   - attributes are missing;
   - policy service is unavailable;
   - information is conflicting;
   - or cached decisions are stale.
5. Protect policy and decision integrity.
6. Restrict policy administration.
7. Separate policy decision from user-interface presentation.
8. Ensure all clients and interfaces use the same authoritative decision logic.
9. Log material decisions and policy changes.
10. Test policy failure, stale cache, attribute forgery and bypass paths.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Access-decision architecture | Security architecture and design | 16–40 hours |
| Policy and attribute specification | Access model and attribute catalogue | 16–40 hours |
| Failure and cache design | Resilience/security design | 8–24 hours |
| Enforcement integration | Code/configuration evidence | 24–100 hours |
| Decision security tests | Failure, stale, forged and bypass tests | 20–50 hours |

### Enterprise responsibilities excluded

Enterprise policy engines, directory services and identity-provider platform operation, unless the application owns a dedicated instance.

**Indicative application effort:** **90–230 hours**.

---

## AC-25 — Reference Monitor

### Application intent

The application’s access-control enforcement mechanism should be tamper resistant, always invoked and sufficiently small or well-structured to permit analysis and testing.

### Application actions

1. Identify the authoritative application enforcement mechanisms.
2. Ensure every protected request passes through them.
3. Prevent clients, APIs, jobs, integrations or direct database paths from bypassing enforcement.
4. Centralise or consistently reuse authorisation logic.
5. Protect policy, code and configuration from unauthorised change.
6. Minimise trusted enforcement code and complexity.
7. Separate enforcement from untrusted client input.
8. Use server-side checks.
9. Protect decision logs.
10. Review and test:
    - completeness;
    - tamper resistance;
    - fail-closed behaviour;
    - direct-object access;
    - administrative bypass;
    - service identity bypass;
    - batch and queue paths;
    - and database procedures.
11. Record design limitations where commercial products do not expose a verifiable enforcement model.

### Deliverables and evidence

| Deliverable | Evidence of compliance | Effort |
|---|---|---:|
| Reference-monitor design | Security architecture and trust-boundary analysis | 20–48 hours |
| Enforcement-point inventory | Interface and component mapping | 12–28 hours |
| Tamper-resistance controls | CM-05/CM-06 and deployment evidence | 16–48 hours |
| Complete-mediation test suite | Browser, API, batch, service and DB bypass tests | 32–80 hours |
| Independent design review | Security architecture review | 8–20 hours |
| Product limitation assessment | Risk record and compensating controls | 6–16 hours |

### Enterprise responsibilities excluded

Operating-system kernels, hypervisors, enterprise network enforcement and shared identity platform internals.

**Indicative application effort:** **110–260 hours**.

---

# 4. Consolidated application work packages

The 25 controls should not be implemented as 25 unrelated projects. The following work packages efficiently produce evidence across the family.

## Work package 1 — Access Control governance and SSP

Covers:

- AC-01;
- applicability and inheritance for all AC controls;
- withdrawn-control treatment;
- parameters;
- enhancements;
- exceptions;
- evidence mapping.

**Indicative effort:** **40–90 hours**.

## Work package 2 — Identity, accounts and authenticators integration

Covers:

- AC-02;
- parts of AC-03;
- AC-07;
- AC-08;
- AC-09;
- AC-12;
- AC-14;
- integration with IA controls.

**Indicative effort:** **100–240 hours**.

## Work package 3 — Role, privilege and separation model

Covers:

- AC-03;
- AC-05;
- AC-06;
- AC-10;
- AC-24;
- AC-25.

**Indicative effort:** **180–450 hours**.

## Work package 4 — Information flow, attributes and sharing

Covers:

- AC-04;
- AC-16;
- AC-20;
- AC-21;
- AC-22;
- AC-23.

**Indicative effort:** **180–430 hours**.

## Work package 5 — Client, remote, wireless and mobile access

Covers:

- AC-11;
- AC-17;
- AC-18;
- AC-19;
- thick-client and browser access paths.

**Indicative effort:** **80–200 hours**.

## Work package 6 — Logging, monitoring and assurance

Covers:

- access-related AU-02 events;
- access reviews;
- session monitoring;
- supplier monitoring;
- negative testing;
- continuous monitoring;
- incident evidence.

**Indicative effort:** **100–240 hours**.

## Work package 7 — Security testing and operational acceptance

Covers:

- positive and negative role tests;
- information-flow tests;
- session tests;
- remote tests;
- unauthenticated tests;
- data-mining tests;
- decision and reference-monitor tests;
- release evidence.

**Indicative effort:** **140–320 hours per major initial cycle**.

---

# 5. Indicative total effort

For a moderately complex internal enterprise application with:

- corporate SSO and MFA;
- managed Windows EUC;
- browser and/or thick-client access;
- several user roles;
- privileged administration;
- project or information boundaries;
- APIs and integrations;
- exports and reports;
- supplier support;
- and mature enterprise shared services,

a realistic initial application-team effort for the **base AC family** is commonly:

## **700–1,600 application-team hours**

This excludes:

- enterprise network and platform engineering;
- enterprise identity-platform implementation;
- ordinary functional development unrelated to controls;
- large-scale redesign of a legacy product;
- independent penetration-testing fees;
- remediation of major product defects;
- supplier commercial negotiations;
- and control enhancements not included in the base controls.

### 5.1 Lower-complexity application

A simple internal commercial application with:

- enterprise SSO;
- few roles;
- no external connections;
- no local cache;
- no complex sharing;
- and mature product controls

may require approximately:

## **350–750 hours**

### 5.2 Higher-complexity application

A custom or legacy application with:

- thick clients;
- local accounts;
- many roles;
- sensitive engineering data;
- complex workflows;
- cross-project rules;
- several integrations;
- local caches;
- supplier administration;
- weak product logging;
- and substantial deviations

may require:

## **1,500–3,000+ hours**

### 5.3 Ongoing effort

Typical ongoing application effort across the AC family is:

- **20–60 hours per month** for routine administration, reviews, monitoring and evidence;
- **40–140 hours per major release** for access-impact assessment and regression testing;
- additional effort for incidents, supplier changes, new integrations and exceptions.

These figures are planning estimates, not NIST-prescribed values.

---

# 6. Application control evidence matrix

| Control | Primary application evidence |
|---|---|
| AC-01 | SSP, Access Control RACI, SyOps and review records |
| AC-02 | Account design, account inventory, provisioning workflow and access reviews |
| AC-03 | Role matrix, authorisation design, code/configuration and negative tests |
| AC-04 | Information-flow inventory, interface rules, export controls and flow tests |
| AC-05 | Conflict matrix, workflow rules, delegation controls and self-approval tests |
| AC-06 | Least-privilege analysis, privileged inventory, service scopes and reviews |
| AC-07 | Lockout/rate-limit configuration, failure logs and tests |
| AC-08 | Approved notice, configuration and presentation tests |
| AC-09 | Previous-logon design and identity-isolation tests |
| AC-10 | Session-limit settings, session records and concurrency tests |
| AC-11 | Inherited-control statement and thick-client lock/unlock tests |
| AC-12 | Session-termination specification, revocation functions and tests |
| AC-13 | Withdrawn-control statement and successor cross-reference |
| AC-14 | Unauthenticated-function inventory, justification and bypass tests |
| AC-15 | Withdrawn-control statement and AC-16 cross-reference |
| AC-16 | Attribute catalogue, authoritative-source mapping and propagation tests |
| AC-17 | Remote-access model, restrictions, session design and route tests |
| AC-18 | Inheritance statement, architecture and unauthorised-wireless path tests |
| AC-19 | Mobile applicability, restrictions and client/API tests |
| AC-20 | External-system flow map, connector review, agreements and destination tests |
| AC-21 | Sharing rules, recipient controls, approval workflow and sharing reviews |
| AC-22 | Public-content assessment, disabled-feature evidence and external-route tests |
| AC-23 | Data-mining threat analysis, query limits, monitoring and inference tests |
| AC-24 | Decision architecture, policy design, failure handling and decision tests |
| AC-25 | Enforcement-point design, tamper controls and complete-mediation tests |

---

# 7. Enterprise responsibilities explicitly excluded

The following should be referenced as inherited or shared and should not be rebuilt by the application team unless the application has an approved deviation:

- corporate Access Control policy;
- enterprise network segmentation and firewalls;
- VPN infrastructure;
- wireless infrastructure;
- managed Windows EUC;
- mobile-device management;
- server and hypervisor administration;
- enterprise operating-system access control;
- corporate identity proofing;
- enterprise directory;
- enterprise MFA;
- enterprise device compliance;
- central PAM;
- central SIEM and SOC;
- enterprise DLP;
- corporate email gateways;
- approved collaboration platforms;
- enterprise records and legal governance;
- organisation-wide supplier governance;
- enterprise risk and exception approval;
- and corporate security training.

The application must still demonstrate that it uses those services correctly and that its own design does not bypass or weaken them.

---

# 8. Deviation and exception standard

Any deviation from the enterprise standard should include:

- affected AC control;
- affected application component;
- enterprise standard;
- proposed deviation;
- reason;
- business need;
- alternatives considered;
- security impact;
- affected information;
- affected users and roles;
- compensating controls;
- monitoring;
- owner;
- approving authority;
- supplier position;
- remediation or replacement plan;
- review date;
- expiry date;
- and test evidence.

Exceptions should be:

- rare;
- time-bound;
- visible in the SSP and risk register;
- reviewed periodically;
- and closed when the technical constraint is removed.

---

# 9. Recommended implementation sequence

1. Confirm the application boundary and inherited enterprise services.
2. Complete the AC applicability and inheritance matrix.
3. Define identity, account, role and permission models.
4. Map information flows, sharing and security attributes.
5. Identify privileged, remote, supplier, external and unauthenticated paths.
6. Define session, lockout, termination and concurrent-use controls.
7. Implement server-side enforcement and complete mediation.
8. Implement access-related event logging and monitoring.
9. Configure product and client restrictions.
10. Test every role, project, object, interface and bypass path.
11. Complete access, privilege, sharing and supplier reviews.
12. Record deviations and obtain approval.
13. update the SSP, SyOps, architecture, test evidence and risk records.
14. Establish recurring reviews and release-impact testing.

---

# 10. References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0 — Security and Privacy Controls for Information Systems and Organizations**  
   https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final

2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0 — Assessing Security and Privacy Controls in Information Systems and Organizations**  
   https://csrc.nist.gov/pubs/sp/800/53/a/r5/final

3. National Institute of Standards and Technology, **NIST SP 800-53B, Release 5.2.0 — Control Baselines for Information Systems and Organizations**  
   https://csrc.nist.gov/pubs/sp/800/53/b/upd1/final

4. National Institute of Standards and Technology, **Cybersecurity and Privacy Reference Tool**  
   https://csrc.nist.gov/projects/cprt/catalog

5. National Institute of Standards and Technology, **Summary of Changes — NIST SP 800-53 Release 5.2.0**  
   https://csrc.nist.gov/csrc/media/Projects/risk-management/800-53%20Comment%20Site/SP800-53-r5.2.0-changes.pdf

6. National Institute of Standards and Technology, **NIST SP 800-207 — Zero Trust Architecture**  
   https://csrc.nist.gov/pubs/sp/800/207/final

7. National Institute of Standards and Technology, **NIST SP 800-46 Rev. 2 — Guide to Enterprise Telework, Remote Access, and Bring Your Own Device Security**  
   https://csrc.nist.gov/pubs/sp/800/46/r2/final

8. National Institute of Standards and Technology, **NIST SP 800-63-4 — Digital Identity Guidelines**  
   https://csrc.nist.gov/pubs/sp/800/63/4/final

---

## Final dividing line

> **The enterprise supplies and governs the common identity, network, endpoint, infrastructure and monitoring controls. The application team remains accountable for every application account, role, permission, session, information flow, sharing rule, access decision and enforcement point needed to prevent unauthorised use of the business application and its information.**
