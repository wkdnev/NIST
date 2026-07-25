# AC-03 Access Enforcement — Application Actions

## Purpose

For an IT application, AC-03 means the application must **enforce approved authorisations whenever a user, service, process or component attempts to access information or perform an action**.

The enterprise may provide corporate identity, multi-factor authentication, managed Microsoft Windows EUC devices, network segmentation, privileged-access management and central logging. Those services help establish identity and provide the approved operating environment, but they do not know whether a particular engineer may amend a specific requirement, whether a reviewer may approve their own change, or whether a support user may export restricted records.

The application must therefore make and enforce the application-specific access decision at the point where the protected function or information is used. A successful sign-in, VPN connection or request from the corporate network is not, by itself, sufficient authorisation.

NIST SP 800-53 defines AC-03 as enforcing approved authorisations for logical access to information and system resources. NIST SP 800-162 describes attribute-based decisions using characteristics of the subject, object, requested operation and, where relevant, environmental conditions. NIST SP 800-207 further reinforces that network location should not create implicit trust.

---

## 1. Define the application’s protected resources and actions

The application should identify what requires access enforcement.

This normally includes:

- application functions and screens;
- business records and individual data fields;
- projects, programmes, cases, contracts or organisational partitions;
- reports, dashboards, searches and saved queries;
- files and attachments;
- APIs and service operations;
- batch jobs and scheduled processes;
- imports, exports and bulk-processing functions;
- approval, release, signing and workflow transitions;
- administration and support functions;
- configuration and security settings;
- audit information;
- database objects and application-controlled stored procedures; and
- application-owned service identities and integration endpoints.

Access rules should cover both **actions** and **information**. It is not enough to control whether a user can open a screen if the underlying API, export, search or direct object reference still allows access.

## 2. Maintain an approved authorisation model

The application should have a clear, approved model showing:

- who or what may request access;
- which roles, groups, attributes or relationships are used;
- what each role or identity may view, create, change, approve, delete, export or administer;
- which records, projects or information sets are in scope;
- any workflow, status, time or contextual restrictions;
- incompatible roles or activities;
- who approves access; and
- who owns each protected information set or business function.

The model may use:

- **role-based access control (RBAC)** — permissions assigned through defined application roles;
- **attribute-based access control (ABAC)** — decisions based on attributes of the user, record, action and context;
- **relationship-based access control** — for example, project membership, case assignment or record ownership;
- **rule-based controls** — for example, only an approver outside the originating team may release a record; or
- a controlled combination of these approaches.

The model should be understandable to the business owner and precise enough to be implemented and tested.

## 3. Enforce authorisation at a trusted application layer

Access enforcement must occur at a trusted server-side or service-side component.

The application should not rely solely on:

- hidden buttons or menu items;
- disabled browser controls;
- thick-client user-interface restrictions;
- client-side JavaScript;
- URL secrecy;
- an internal IP address;
- possession of a corporate account;
- successful VPN connection;
- a user-supplied role or group value; or
- instructions telling users not to access particular information.

Every material request should be authorised by the receiving application service before the requested action or information is provided.

For a thick-client application, the server must assume that client requests can be modified or replayed and must independently revalidate the user, requested operation, target object and relevant context.

## 4. Deny by default

The normal decision should be **deny unless an approved rule explicitly permits the action**.

This means:

- new users receive no application access until approved;
- new roles contain no permissions until deliberately assigned;
- new functions and APIs are not automatically available to existing roles;
- new record types do not inherit broad access accidentally;
- missing, malformed, stale or unrecognised authorisation attributes cause denial;
- failures in the policy or directory lookup do not result in unrestricted access; and
- unsupported or unexpected request methods are rejected.

A permissive “allow unless prohibited” approach is inappropriate for applications holding company, government, personal or otherwise restricted information.

## 5. Enforce least privilege

Each user, service and component should receive only the access necessary for its approved business purpose.

The application should:

- distinguish viewing, creating, updating, approving, deleting, exporting and administering;
- avoid broad “power user” roles that combine unrelated permissions;
- restrict administrative functions to dedicated roles;
- limit service identities to required interfaces and operations;
- scope access to relevant projects, business units, records or data partitions;
- avoid giving support personnel routine access to business information;
- restrict bulk and high-impact functions more tightly than ordinary use; and
- remove permissions that are no longer required.

Access to a function does not automatically justify access to every record processed by that function.

## 6. Enforce record-, object- and field-level access where required

Application roles alone may be too broad for restricted information.

The application should apply finer controls where necessary, such as:

- project or programme membership;
- business-unit ownership;
- case assignment;
- contract or customer relationship;
- nationality, clearance or handling restrictions;
- need-to-know;
- information classification;
- record status;
- field sensitivity;
- legal or investigation hold;
- geographical or contractual restrictions; and
- separation between company, government, personal and other governed information.

Searches, reports, counts, autocomplete, notifications, audit history and metadata must respect the same restrictions as the main record view. The application must not reveal the existence or characteristics of a protected record through side channels.

## 7. Enforce authorisation throughout the business workflow

Authorisation can change as a record moves through its lifecycle.

The application should enforce rules for:

- draft, review, approval, release and closure states;
- who may move a record between states;
- whether the originator may approve their own action;
- whether a released or signed record may be altered;
- who may reopen, cancel or override a process;
- when an action becomes irreversible;
- whether a user retains access after reassignment or project closure; and
- whether historical versions remain accessible.

The current workflow state must be checked by the trusted service at the time of the action. A user should not be able to replay an earlier valid request after the record state or their authority has changed.

## 8. Implement separation of duties

Where one person completing an entire process could create unacceptable risk, the application should enforce separation of duties.

Examples include:

- requester and approver;
- author and independent reviewer;
- developer and production deployer;
- access requester and access approver;
- payment creator and payment releaser;
- record owner and auditor;
- administrator and audit-log administrator; and
- security configuration changer and independent reviewer.

The application should prevent incompatible role assignment or, where that is not technically possible, prevent the conflicting actions at transaction time.

Emergency override should be exceptional, attributable, time-limited and reviewed.

## 9. Control privileged and administrative access

Administrative access should be more tightly controlled than ordinary business access.

The application should:

- provide named administrative roles rather than shared accounts;
- separate application administration from routine user activity;
- use dedicated privileged identities where required by enterprise policy;
- require reauthentication or step-up authentication for particularly sensitive actions where supported;
- limit access to configuration, role assignment, bulk operations and diagnostic functions;
- prevent administrators from silently assuming another user’s identity;
- clearly identify and log support impersonation or delegated access;
- restrict direct database alteration and uncontrolled back-end tools;
- integrate with enterprise PAM where available; and
- record the reason, target and outcome of privileged actions.

Application administrators should not automatically receive unrestricted access to all business records unless that access is genuinely required and approved.

## 10. Enforce access for non-person identities

Service accounts, APIs, scheduled jobs, integration services and application components must also be authorised.

The application should:

- use a unique identity for each material service or integration;
- avoid shared credentials across unrelated applications or environments;
- restrict each identity to required APIs, operations and data;
- validate token issuer, audience, scope and expiry;
- distinguish human and machine activity;
- prevent a service identity from using interactive functions unless explicitly required;
- control delegation and “act on behalf of” behaviour;
- reject calls from unknown or incorrectly scoped services; and
- review service access when integrations change or are retired.

Network reachability between two internal services does not constitute permission to use every available operation.

## 11. Protect against direct-object and parameter manipulation

The application must recheck authorisation whenever a user supplies or changes an object identifier, record key, project code, file reference, tenant or organisational identifier.

It should prevent:

- changing a URL or API identifier to reach another user’s record;
- altering hidden form values;
- changing a project or business-unit identifier;
- requesting an attachment directly without checking access to its parent record;
- guessing sequential identifiers;
- using export parameters to expand scope;
- replaying an authorised request against a different object; and
- accessing deleted, archived or superseded records through an old link.

Possession or knowledge of an identifier is not proof of authorisation.

## 12. Apply the same policy across every access path

The same access rules should apply consistently to:

- browser interfaces;
- thick clients;
- mobile interfaces, where separately approved;
- APIs;
- batch and scheduled processes;
- reports;
- exports;
- search services;
- messaging or integration components;
- administrative tools;
- database-facing services; and
- recovery or support functions.

A restricted action must not become available through a secondary interface merely because the main interface blocks it.

Where multiple products make up the application, the application owner should define which component is authoritative for each access decision and ensure that downstream components cannot bypass it.

## 13. Handle access-control failures safely

The application should fail closed where an access decision cannot be made reliably.

Examples include:

- missing role or group information;
- unavailable identity or policy service;
- stale or invalid session;
- expired token;
- failed attribute lookup;
- conflicting access rules;
- incomplete record ownership information;
- configuration error; and
- unknown service identity.

The application should deny the action, provide a non-sensitive error message, log the reason and trigger operational support where appropriate.

It must not silently grant broad access as a fallback.

## 14. Re-evaluate access when context changes

Access should be re-evaluated when relevant facts change, including:

- account disablement;
- role or group change;
- project reassignment;
- user transfer or departure;
- record ownership change;
- workflow-state change;
- information reclassification;
- service-token expiry;
- termination of supplier access;
- emergency-access expiry; and
- change to a legal, contractual or handling restriction.

Long-lived sessions and cached permissions should not allow access to continue indefinitely after authority is removed. The application should define an appropriate refresh, token lifetime or revocation mechanism.

## 15. Protect the authorisation policy and data

The information used to make access decisions is itself security-critical.

The application should protect:

- role and permission definitions;
- group-to-role mappings;
- project membership;
- record ownership and classification attributes;
- policy rules;
- workflow permissions;
- service scopes;
- configuration controlling enforcement;
- delegated-access records; and
- emergency-access settings.

Only approved administrators or automated processes should be able to alter these values. Changes should be attributable, reviewed and logged.

## 16. Log access decisions and high-risk activity

The application should generate security-relevant events for:

- successful and failed access attempts where material;
- access denied by role, record or policy;
- privileged and administrative actions;
- role and permission changes;
- project or data-partition membership changes;
- use of emergency or delegated access;
- bulk viewing, export or download;
- approval, release, override and deletion;
- direct or exceptional support access;
- access-control configuration changes; and
- repeated attempts to bypass restrictions.

Events should include enough context to identify the acting user or service, action, target, outcome, time and relevant reason without recording passwords, complete tokens or unnecessary restricted content.

## 17. Test access enforcement comprehensively

Access-control testing should prove both what is allowed and what is denied.

Testing should include:

- every defined business and administrative role;
- authorised positive cases;
- unauthorised negative cases;
- horizontal access between users, projects or records;
- vertical escalation into privileged functions;
- direct-object reference manipulation;
- API and thick-client request manipulation;
- workflow and separation-of-duties bypass;
- stale sessions and recently removed access;
- service identities and integration scopes;
- bulk export and search boundaries;
- error and failure conditions; and
- consistency across all interfaces and tiers.

Testing only the visible menu or a small sample of roles is insufficient.

## 18. Review and recertify the authorisation model

The application owner and relevant information owners should periodically review:

- whether roles still reflect current business responsibilities;
- whether permissions remain necessary;
- whether project or record memberships remain accurate;
- whether privileged access is justified;
- whether service identities are still used;
- whether incompatible access exists;
- whether temporary and supplier access has expired;
- whether new functions or interfaces are covered; and
- whether incidents or test findings reveal weaknesses.

The enterprise may operate a general access-review process, but the application must provide the application-specific role, permission and data context needed to make that review meaningful.

## 19. Manage exceptions and unsupported enforcement

Where a legacy or supplier-controlled product cannot enforce the required policy, the application should document:

- the affected role, action, record type or interface;
- the required access rule;
- what the product actually enforces;
- the resulting risk;
- compensating controls;
- monitoring and review;
- accountable owner;
- approval;
- target remediation, upgrade or replacement; and
- review or expiry date.

An instruction to users or a confidentiality agreement is not an adequate substitute where technical enforcement is reasonably possible.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate identity, the standard SDLC and established testing and logging services. They exclude enterprise identity engineering, major supplier product changes and extensive redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define protected functions, information and actions** | Identify the application functions, records, fields, APIs, exports, workflows and administrative actions that require access control. | Summarise the scope in the **SSP AC-03 statement** and link it to the existing **security architecture**, **data-flow description**, **ConOps** or **SyOps**. | **4–8 hours** |
| **2. Maintain an approved role and authorisation model** | Define roles, permitted actions, record scope, approval ownership and any attribute- or relationship-based rules. | Record the model in the existing **role/access matrix**, **business requirements**, **security design** or **SyOps**, with the SSP referencing the authoritative source. | **8–20 hours** |
| **3. Enforce access at the trusted service layer** | Implement authorisation checks in the receiving application service or API for every material request, rather than relying on the client or network location. | Describe the enforcement design in the **solution/security design** and capture implementation requirements in the normal **SDLC backlog** or **technical specification**. Verify it in the **system/security test report**. | **16–40 hours** |
| **4. Deny by default and apply least privilege** | Configure new users, roles, functions and objects with no access until explicitly approved; separate view, change, approve, export and administer permissions. | Record approved defaults and permissions in the **role matrix**, **configuration specification** and **SSP**. Retain positive and negative results in the normal **access-control test report**. | **8–20 hours** |
| **5. Enforce record, project or data-partition boundaries** | Check the user’s approved relationship to each project, case, record or governed data set at the time of access. Apply the same filter to search, reports, exports and attachments. | Define the rule in the **business/security requirements**, **data model**, **security design** or **SyOps**. Evidence through the standard **system, API and security test report**. | **16–48 hours** |
| **6. Enforce workflow and separation of duties** | Restrict state changes, approval, release, override and deletion according to role, record state and incompatible-duty rules. | Record the controlled workflow in the **ConOps**, **business-process design**, **role matrix** and **SSP AC-03/AC-05 statements**. Verify in the normal **functional and security test report**. | **12–32 hours** |
| **7. Control privileged and support functions** | Use named administrative roles, restrict role assignment and security configuration, and tightly control impersonation, emergency and support access. | Describe responsibilities in the **SSP**, **SyOps**, **support model** and existing **privileged-access design**. Retain access and audit tests in the **security or operational acceptance report**. | **8–20 hours** |
| **8. Authorise service identities and integrations** | Give each service or integration a unique identity and only the API scopes, operations and data it requires. Validate tokens and reject unknown or incorrectly scoped callers. | Record identities and scopes in the **interface control document**, **security design**, **service account register** or **SyOps**. Verify through the normal **integration and API test report**. | **8–24 hours** |
| **9. Apply consistent controls across every interface** | Confirm that browser, thick-client, API, batch, report, export and administrative paths use the same authoritative policy and cannot bypass one another. | Describe the enforcement points in the **application architecture** and **interface specifications**. Retain cross-interface results in the established **system/security test report**. | **12–32 hours** |
| **10. Fail closed and refresh access after change** | Deny access when roles, attributes, tokens or policy services are unavailable or invalid, and ensure removed access expires within the approved session or cache period. | Record failure and refresh behaviour in the **security design**, **SyOps** and **SSP**. Verify through the normal **resilience, session and access-control test report**. | **8–20 hours** |
| **11. Log access denials, privilege and policy changes** | Generate events for material denied access, role changes, privileged actions, emergency use, bulk exports and changes to access-control configuration. | Define events in the **SSP AU-02/SI-04 sections** and existing **event-logging specification**. Retain representative events in the **system/security test report** and **operational acceptance evidence**. | **6–16 hours** |
| **12. Test and periodically review access enforcement** | Test positive, negative, horizontal, vertical, direct-object, workflow and service-access cases; review roles and permissions after material change and periodically. | Add cases to the normal **security test plan** and retain outcomes in the **test report**. Record periodic decisions in existing **access reviews**, **service reviews**, **change records** or the **risk register**. | **16–40 hours initially; 4–12 hours per review** |

### Indicative total

For a typical internal application with a usable existing role model and reasonable product support, the initial application effort is commonly around **120–300 hours**. A simple commercial application with a small number of roles may require less. A legacy application, highly granular record-level model, complex engineering segregation rules or extensive supplier constraints may require substantially more.

The estimates should not be added mechanically where work overlaps. For example, access-model design, workflow design and test preparation may be performed together within the same SDLC activities.

---

## Suggested document placement

To avoid creating disconnected evidence, the information should normally be distributed across established application and SDLC artefacts:

- **SSP:** AC-03 implementation approach, inherited controls, enforcement points, role model summary, access-review arrangements, known limitations and addendum references.
- **ConOps or SyOps:** operational roles, business workflows, support and emergency access, user responsibilities and failure behaviour.
- **Security architecture or design:** trusted enforcement points, policy decision inputs, service identities, trust boundaries, session behaviour and cross-tier controls.
- **Business and security requirements:** who may perform each action, against which information, under which conditions.
- **Role or access matrix:** roles, permissions, project or information scope, approval owner and incompatible access.
- **Data model and interface specifications:** object ownership, classification attributes, API scopes and authorisation context.
- **SDLC backlog and technical specifications:** implementation tasks and acceptance criteria for access enforcement.
- **Test plans and reports:** positive and negative role tests, horizontal and vertical escalation, object manipulation, workflow bypass and service-access tests.
- **Release and operational acceptance records:** confirmation that the released version uses the approved access model and enforcement configuration.
- **Access reviews and service reviews:** periodic confirmation that roles, memberships, service identities and privileged access remain appropriate.
- **Risk register or application addendum:** unsupported rules, supplier constraints, temporary exceptions, compensating controls and review dates.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate identity proofing and workforce identity lifecycle;
- enterprise directory and authentication services;
- multi-factor authentication;
- corporate Microsoft Windows EUC access controls;
- VPN authentication and remote-access infrastructure;
- network segmentation and firewall enforcement;
- enterprise privileged-access management platform;
- central joiner, mover and leaver processes;
- corporate access-control policy and role-governance standards;
- enterprise account recertification tooling;
- central logging, SIEM and SOC operations;
- enterprise certificate, token and secrets-management services;
- operating-system, hypervisor and shared-platform permissions; and
- enterprise incident and access-violation processes.

The application team must still consume these services correctly, map enterprise identities to application permissions, provide application-specific context for approvals and reviews, and ensure that no application interface bypasses them.

> **Key dividing line:** the enterprise establishes and authenticates the identity and protects the shared environment; the application decides and enforces what that identity may do with the application’s functions, records and business processes.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, AC-03 Access Enforcement.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, AC-03 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-162, Guide to Attribute Based Access Control (ABAC) Definition and Considerations**.
4. National Institute of Standards and Technology, **NIST SP 800-207, Zero Trust Architecture**.
5. National Institute of Standards and Technology, **NIST SP 800-207A, A Zero Trust Architecture Model for Access Control in Cloud-Native Applications in Multi-Location Environments**.
