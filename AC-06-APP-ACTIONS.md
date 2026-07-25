# AC-06 Least Privilege — Application Actions

## Purpose

For an IT application, AC-06 means the application must ensure that every user, administrator, service, process and software component receives **only the minimum permissions and capabilities needed to perform its approved function**.

Least privilege is not achieved merely by using corporate authentication or placing the application on an internal network. The enterprise may provide identity lifecycle, MFA, managed Microsoft Windows EUC devices, network segmentation, privileged-access management, enterprise databases and central monitoring. Those services establish and protect the operating environment, but they do not determine the minimum business permissions required within a specific application.

The application must therefore design, implement, test and maintain a least-privilege model for its own:

- business roles;
- information and record access;
- privileged functions;
- service identities;
- APIs and integrations;
- database access;
- support activities;
- background processing;
- local thick-client behaviour; and
- application-controlled administration.

NIST defines least privilege as restricting users and processes to the minimum resources and authorisations necessary to perform assigned tasks. AC-06 also addresses privileged functions, non-privileged use, privileged accounts, auditing of privileged functions, and preventing non-privileged users from executing privileged capabilities.

> **Core principle:** access should be sufficient to perform the approved task, but no broader, longer-lived or more powerful than necessary.

---

## 1. Define the application’s privilege model

The application should identify all privileges that can materially affect:

- restricted information;
- business transactions;
- workflow outcomes;
- security configuration;
- identities and access;
- audit records;
- interfaces;
- integrations;
- application availability; or
- system integrity.

Privileges should be expressed as distinct actions rather than vague access levels.

Examples include:

- view;
- create;
- amend;
- approve;
- release;
- sign;
- cancel;
- delete;
- restore;
- export;
- print;
- administer;
- configure;
- assign roles;
- impersonate;
- run batch jobs;
- access diagnostics;
- manage integrations; and
- view or manage audit information.

A role called “power user” or “administrator” is not sufficiently clear unless its exact permissions and limitations are documented.

## 2. Grant only the privileges needed for the business task

Each application role should be designed around a legitimate business responsibility.

The application should:

- avoid broad permissions provided merely for convenience;
- distinguish normal use from administration;
- separate viewing from changing;
- separate changing from approving;
- restrict deletion, override, export and bulk actions;
- scope access to the relevant project, business unit, case or information set;
- prevent routine users from receiving technical support permissions;
- avoid assigning full administrative access to business owners;
- limit temporary access to the approved task and period; and
- remove permissions that are not actively required.

The question should not be “Could this user benefit from the permission?” but “Is the permission necessary for their assigned function?”

## 3. Separate ordinary and privileged functions

Privileged functions should not be exposed through ordinary user roles.

The application should separate, where applicable:

- user administration;
- role and permission management;
- security configuration;
- logging configuration;
- certificate and key settings;
- integration administration;
- bulk data management;
- database maintenance;
- workflow override;
- emergency access;
- support impersonation;
- diagnostic functions;
- system-wide export; and
- audit administration.

Ordinary users should not be able to invoke these functions by manipulating a URL, API request, thick-client command, hidden parameter or direct object reference.

## 4. Use dedicated privileged roles and identities

Where corporate policy requires it, privileged application activity should use a dedicated privileged identity or clearly separated privileged role.

The application should:

- avoid shared administrator accounts;
- require named, attributable privileged access;
- prevent privileged identities from being used for routine activity where practicable;
- distinguish business administration from technical administration;
- separate application administration from database, platform and infrastructure administration;
- integrate with enterprise PAM where supported;
- limit privileged sessions to the required function and period;
- revoke or disable dormant privileged access; and
- ensure emergency credentials are tightly controlled and reviewed.

A user who requires occasional administration should not necessarily remain permanently privileged.

## 5. Limit privileges by information scope

Least privilege applies not only to functions but also to the information those functions can affect.

The application should restrict privileges by:

- project;
- programme;
- contract;
- customer;
- business unit;
- case;
- product;
- geography;
- classification;
- sensitivity;
- nationality or handling restriction;
- record ownership;
- workflow state; or
- another approved business relationship.

For example, permission to approve requirements should not automatically permit approval across every engineering programme.

Search, reporting, export, attachment access and metadata should respect the same scope.

## 6. Restrict high-impact capabilities

Certain capabilities should normally require stronger restriction because their misuse can create disproportionate harm.

These include:

- bulk export;
- mass update;
- mass deletion;
- workflow override;
- access-control administration;
- security configuration;
- audit-log administration;
- support impersonation;
- unrestricted search;
- direct database update;
- reclassification of information;
- release or publication;
- restoration of deleted records;
- disabling monitoring;
- changing retention rules; and
- managing service credentials or integration trust.

The application should consider additional approval, reauthentication, time limitation, transaction limits or enhanced logging for these actions.

## 7. Apply least privilege to service identities

Service accounts, workload identities, scheduled jobs, APIs and integration services must receive only the permissions needed for their specific technical function.

The application should:

- use a distinct identity for each material service or integration;
- avoid sharing one highly privileged service account across multiple applications;
- separate development, test and production identities;
- restrict API scopes and operations;
- restrict database access to required schemas, tables, views and procedures;
- avoid giving background jobs interactive access;
- prevent service identities from administering the application unless explicitly required;
- limit file-system and message-queue permissions;
- restrict outbound and inbound integration permissions;
- review privileges when interfaces change; and
- revoke identities when components or integrations are retired.

A service identity should not receive broad access simply because it is non-human.

## 8. Apply least privilege to database access

The application should avoid connecting to its database using a database owner, system administrator or similarly unrestricted identity for routine operation.

Where supported, use separate database roles or identities for:

- read-only access;
- transactional updates;
- reporting;
- schema migration;
- maintenance;
- batch processing;
- backup or recovery integration; and
- administration.

The application should:

- restrict access to required schemas and objects;
- use approved views or stored procedures where appropriate;
- prevent direct table access when business rules require controlled operations;
- restrict schema modification to controlled deployment identities;
- separate runtime and migration privileges;
- avoid embedding highly privileged database credentials;
- record direct or exceptional database access; and
- remove obsolete permissions after migration or support work.

Database platform administration remains an enterprise responsibility; the application remains responsible for its application-owned database roles and access patterns.

## 9. Apply least privilege to thick clients

A thick-client application installed on a managed Microsoft Windows EUC device should operate with ordinary user privileges wherever possible.

The application should:

- avoid requiring local administrator rights for normal use;
- use approved installation and update mechanisms;
- store configuration and local data in appropriate protected locations;
- avoid writing to privileged operating-system locations during normal operation;
- avoid installing unnecessary services, drivers or browser extensions;
- limit local service privileges;
- prevent the client from embedding privileged server or database credentials;
- use the authenticated user or an appropriately scoped service identity;
- keep local administrative functions separate; and
- rely on server-side enforcement for business privileges.

Where installation requires elevation, that elevation should be performed through the corporate software-distribution or approved support process, not granted permanently to the user.

## 10. Prevent privilege escalation

The application must prevent users and services from obtaining higher privileges through manipulation or unintended paths.

Testing and design should consider:

- changing role identifiers in requests;
- direct calls to privileged APIs;
- hidden administrative routes;
- client-side modification;
- workflow replay;
- parameter manipulation;
- mass-assignment vulnerabilities;
- insecure object references;
- privilege inheritance;
- misconfigured group-to-role mapping;
- token or scope substitution;
- support functions that allow impersonation;
- plugin or extension mechanisms;
- database procedures with excessive execution rights; and
- error paths that fall back to elevated access.

The application should fail closed where privilege information is missing, invalid or ambiguous.

## 11. Prevent non-privileged users from executing privileged functions

The application should enforce privileged-function checks in trusted server-side or service-side code.

It must not rely solely on:

- hidden menus;
- disabled buttons;
- client-side checks;
- thick-client logic;
- obscure URLs;
- internal network location;
- possession of a corporate account;
- user instructions; or
- the absence of a documented API.

Every privileged request should be authorised at the point of use.

## 12. Limit privilege duration

Privileges that are temporary, exceptional or task-specific should expire automatically where practical.

Examples include:

- project access;
- supplier support access;
- emergency administration;
- elevated troubleshooting rights;
- temporary data migration access;
- release support;
- privileged testing;
- delegated approval; and
- access during a defined incident.

The application should record:

- the approved purpose;
- start and end time;
- approving owner;
- granted permissions;
- affected information or function; and
- review outcome.

Permanent assignment should not be used merely because time-limited access is inconvenient.

## 13. Control support and impersonation

Support personnel may need to diagnose user issues, but this should not result in unrestricted access.

The application should:

- avoid routine access to restricted business data;
- provide diagnostic views with limited content where possible;
- mask sensitive fields unless required;
- require a support reason or ticket reference;
- identify when support is acting as or viewing on behalf of a user;
- prevent silent impersonation;
- limit the scope and duration of delegated access;
- record affected records and actions;
- prevent support staff from approving or completing business actions as the user unless explicitly authorised; and
- review exceptional support access.

“Support” should not be treated as an unlimited superuser role.

## 14. Separate privilege administration from privilege use

Where proportionate, the ability to assign privileges should be separated from the ability to exercise the most sensitive privileges.

Examples include:

- access requester versus approver;
- role administrator versus business approver;
- privileged-account custodian versus privileged user;
- application administrator versus audit administrator;
- developer versus production deployer;
- database migration operator versus approver; and
- emergency-access issuer versus reviewer.

Where full technical separation is not possible, enhanced approval, logging and independent review should be applied.

## 15. Review privilege inheritance and role composition

Applications often grant privileges through several mechanisms at once, such as:

- corporate directory groups;
- application roles;
- project membership;
- delegated authority;
- record ownership;
- workflow state;
- support roles;
- API scopes; and
- temporary elevation.

The application should evaluate the **effective privilege**, not merely each individual assignment.

The review should identify:

- overlapping roles;
- hidden inherited privileges;
- combinations that create excessive access;
- nested group effects;
- users with multiple incompatible roles;
- dormant privileges;
- broad default memberships; and
- service identities inheriting human-user permissions.

## 16. Log and monitor privileged activity

The application should generate security-relevant events for:

- privileged sign-in and session activity;
- assignment or removal of privileged roles;
- execution of privileged functions;
- changes to access-control policy;
- security configuration changes;
- emergency or temporary privilege use;
- support impersonation;
- bulk export, update or deletion;
- direct or exceptional database activity;
- failed attempts to use privileged functions;
- disabling or changing logging; and
- use of privileged service identities.

Events should include the acting identity, privilege or role used, action, target, outcome, time and relevant reason without exposing credentials or unnecessary restricted information.

## 17. Test least privilege

Testing should demonstrate that each role and service can perform required tasks but cannot perform unauthorised ones.

Testing should include:

- positive role tests;
- negative role tests;
- horizontal access between users or projects;
- vertical escalation into administrative functions;
- direct privileged API calls;
- thick-client manipulation;
- database privilege checks;
- service-identity scope tests;
- temporary access expiry;
- support and impersonation controls;
- workflow and separation-of-duties bypass;
- bulk-function restrictions;
- stale sessions after privilege removal;
- missing or malformed privilege information; and
- cross-interface consistency.

A test that confirms an administrator can administer is not sufficient. It must also confirm that ordinary users, support users and service identities cannot administer.

## 18. Periodically review and recertify privileges

The application owner and relevant business or information owners should periodically review:

- privileged users;
- business roles;
- project and information scope;
- service identities;
- support access;
- temporary and supplier access;
- emergency credentials;
- database privileges;
- API scopes;
- dormant assignments;
- incompatible role combinations;
- users with unusually broad access; and
- privileges associated with retired functions or integrations.

Reviews should also occur after:

- role redesign;
- major releases;
- organisational changes;
- supplier changes;
- incidents;
- audit findings;
- penetration tests; and
- changes in information sensitivity.

## 19. Remove privilege promptly

Privilege should be removed when:

- a user changes role;
- project participation ends;
- a supplier engagement ends;
- temporary access expires;
- a service is retired;
- an integration is removed;
- emergency work is complete;
- an administrator no longer needs elevated access;
- a credential is compromised;
- an account is disabled; or
- a privilege is no longer justified.

The application should ensure that cached permissions, tokens and active sessions do not allow removed privileges to continue indefinitely.

## 20. Manage unavoidable excess privilege

Some commercial, legacy or supplier-controlled products may offer only coarse roles or require excessive service privileges.

Where this cannot be corrected immediately, the application should record:

- the affected identity, role or component;
- the minimum required privilege;
- the actual privilege granted;
- the reason;
- information and functions exposed;
- risk;
- compensating controls;
- monitoring;
- review frequency;
- owner;
- approval;
- remediation, upgrade, isolation or replacement plan; and
- review or expiry date.

Compensating controls may include tighter network paths, transaction limits, enhanced monitoring, dual approval, restricted operating windows, protected jump paths or independent review. They do not make the excess privilege disappear; they reduce and expose the resulting risk.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate identity, standard SDLC processes and established testing and logging services. They exclude enterprise IAM or PAM engineering, major supplier changes and extensive legacy redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the application privilege model** | Identify business, support, administrative and service roles and list the exact functions and information each requires. | Summarise the approach in the **SSP AC-06 statement** and maintain the detail in the existing **role/access matrix**, **security design**, **ConOps** or **SyOps**. | **8–20 hours** |
| **2. Separate ordinary, privileged and high-impact functions** | Create distinct permissions for routine use, administration, role management, support, export, override and security configuration. | Record the separation in the **role matrix**, **business/security requirements** and **application design**. Verify through the normal **access-control test report**. | **8–24 hours** |
| **3. Scope privilege to the required information and business area** | Limit roles by project, case, business unit, product, contract, classification or another approved relationship. | Define the scope rules in the **data model**, **business requirements**, **security design**, **SyOps** and the **SSP AC-03/AC-06 statements**. | **12–32 hours** |
| **4. Apply least privilege to service identities and APIs** | Use unique identities and restrict each service to required endpoints, operations, scopes, queues, files and data. | Record identities and permissions in the existing **interface control document**, **service-account register**, **security design** or **SyOps**. Verify in the **integration/API test report**. | **8–24 hours** |
| **5. Apply least privilege to application database access** | Separate runtime, reporting, migration and administrative database roles and restrict them to required schemas and operations. | Capture the design in the **database design**, **deployment specification**, **security design** and **SSP**. Retain permission tests in the normal **system or security test report**. | **8–24 hours** |
| **6. Ensure thick clients operate without unnecessary local privilege** | Design normal operation for standard Windows user rights and use approved elevated installation or update mechanisms. | Record requirements in the **thick-client design**, **packaging specification**, **SyOps** and **SSP**. Verify through the normal **installation and security test report**. | **6–20 hours** |
| **7. Prevent privilege escalation and privileged-function bypass** | Enforce trusted server-side checks and test request manipulation, hidden routes, direct APIs, role changes and stale sessions. | Capture implementation requirements in the **SDLC backlog** and **security design**. Retain positive and negative results in the standard **security test report**. | **16–40 hours** |
| **8. Control temporary, emergency, support and impersonation access** | Require approval, purpose, defined scope, expiry, attribution and review for exceptional privilege. | Record the operating process in the **SyOps**, **support model**, **incident-response annex**, **SSP** or existing **privileged-access procedure**. | **8–20 hours** |
| **9. Log privileged use and privilege changes** | Generate events for role assignment, privileged actions, emergency use, support impersonation, bulk activity and failed privileged access. | Define the events in the **SSP AU-02/SI-04 sections** and existing **event-logging specification**. Verify through the **system/security test report**. | **6–16 hours** |
| **10. Test least privilege across roles, services and interfaces** | Test required tasks and prohibited actions for every material role, service identity, API, thick client and workflow. | Add cases to the normal **security test plan** and retain outcomes, defects and retests in the established **test report** and **release evidence pack**. | **16–40 hours** |
| **11. Periodically review effective privilege** | Review role combinations, project scope, privileged users, service accounts, API scopes, database roles, temporary access and dormant privileges. | Record decisions in existing **access reviews**, **service reviews**, **risk reviews**, **change records** or the **application addendum**. | **6–16 hours per review** |
| **12. Remove or formally manage excessive privilege** | Revoke unnecessary privilege promptly; where the product cannot support the required granularity, document and approve compensating controls and a remediation plan. | Use normal **access-change records**, **risk register**, **problem record** or **application addendum**, with the SSP referencing any material deviation. | **4–12 hours per issue** |

### Indicative total

For a typical internal application with a usable role model and reasonable product support, initial application effort is commonly around **100–250 hours**.

A simple commercial application with a few well-designed roles may require less. A complex engineering or records application with project segregation, granular data rules, thick clients, many integrations, supplier limitations or coarse legacy roles may require substantially more.

The estimates should not be added mechanically where activities overlap. Role design, access enforcement, separation of duties and testing are commonly delivered through the same SDLC work packages.

---

## Suggested document placement

To avoid disconnected evidence, least-privilege information should normally be distributed across existing application and SDLC artefacts:

- **SSP:** AC-06 implementation approach, inherited enterprise services, role model summary, privileged functions, service identities, review arrangements and deviations.
- **ConOps or SyOps:** operational roles, support access, emergency access, privileged activities, responsibilities and escalation.
- **Security architecture or design:** privilege boundaries, trusted enforcement points, service identities, database roles, client/server responsibilities and privileged paths.
- **Business and security requirements:** the minimum actions each role or service must perform and the prohibited actions.
- **Role/access matrix:** role membership, permissions, information scope, privileged capabilities, incompatible roles and approval owner.
- **Data model:** ownership, project, classification and other attributes used to restrict privilege.
- **Interface control document:** service identities, API scopes, delegated authority and allowed operations.
- **Database design:** runtime, reporting, migration and administration roles and object permissions.
- **Thick-client design and packaging specification:** local privilege requirements, installation elevation and server-side enforcement.
- **SDLC backlog and technical specifications:** implementation stories and acceptance criteria for least privilege.
- **Test plans and reports:** positive and negative role tests, escalation attempts, service scopes, local privilege and exceptional-access tests.
- **Release and operational acceptance records:** confirmation that the released role and privilege configuration is approved and working.
- **Access and service reviews:** periodic review of users, roles, service identities, privileged access and temporary assignments.
- **Risk register or application addendum:** coarse product roles, excessive service privileges, unsupported separation and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate identity proofing and account lifecycle;
- enterprise directory and authentication services;
- MFA;
- corporate Windows EUC account and operating-system privilege management;
- enterprise PAM platform and infrastructure privileged-session controls;
- network-device, firewall, server, hypervisor and shared-platform privileges;
- enterprise database-platform administration;
- corporate joiner, mover and leaver processes;
- enterprise privileged-access policy;
- corporate role-governance and access-review tooling;
- central SIEM and SOC operations;
- enterprise service-account and secrets-management platforms;
- corporate software-distribution elevation mechanisms; and
- enterprise incident, disciplinary and access-violation processes.

The application team must still:

- define its own minimum business and technical privileges;
- map corporate identities to application roles;
- restrict application-owned service and database identities;
- prevent privileged-function bypass;
- provide application-specific context for approval and review; and
- ensure that inherited enterprise privileges do not automatically grant unrestricted application access.

> **Key dividing line:** the enterprise manages privilege for the shared corporate environment; the application ensures that users, services and components receive only the minimum authority needed within the business application itself.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, AC-06 Least Privilege.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, AC-06 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-162, Guide to Attribute Based Access Control Definition and Considerations**.
4. National Institute of Standards and Technology, **NIST SP 800-207, Zero Trust Architecture**.
5. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool glossary — Least Privilege**.
