# AC-02 Account Management — Application Actions

## Purpose

For an IT application, AC-02 means the application must ensure that **every application account, role assignment and non-person identity is explicitly authorised, uniquely attributable, appropriately configured, regularly reviewed and promptly disabled or removed when no longer required**.

The enterprise may provide workforce identity proofing, the corporate directory, multi-factor authentication, joiner–mover–leaver processes, privileged-access management, managed Microsoft Windows EUC devices, VPN access and central identity-governance tooling. Those services are inherited.

The application remains responsible for the account-management decisions and controls that are specific to the application, including:

- which application account types are allowed or prohibited;
- whether local accounts are necessary;
- how corporate identities are mapped to application roles;
- project, programme, case or information-scope membership;
- privileged and support accounts;
- service, API, batch and integration identities;
- temporary, emergency and supplier access;
- approval and account-manager responsibilities;
- activation, modification, review, suspension and removal;
- dormant and unused access;
- role and group conditions;
- account-related audit events;
- reconciliation with enterprise identity sources; and
- exceptions where the product cannot use the standard enterprise model.

NIST AC-02 requires organisations to define permitted and prohibited account types, assign account managers, establish conditions for group and role membership, specify authorised users and access privileges, create and manage accounts through approved processes, monitor account use, notify account managers of relevant personnel or usage changes, authorise access based on valid need, periodically review accounts, and align account management with personnel termination and transfer processes.

> **Core principle:** the enterprise establishes who the person is and whether their corporate identity is active; the application decides whether that identity needs an application account, what it may do, which information it may access, how long that access remains valid and when it must be removed.

---

## 1. Define permitted and prohibited application account types

The application should identify which account types are permitted.

Typical permitted account types may include:

- named business-user accounts;
- named application-administrator accounts;
- named support accounts;
- service or workload identities;
- API client identities;
- scheduled-job identities;
- integration identities;
- read-only reporting identities;
- controlled emergency accounts;
- supplier support accounts;
- test identities in non-production; and
- application-owned database identities.

The application should explicitly prohibit or tightly constrain:

- shared user accounts;
- generic team accounts;
- anonymous access;
- guest accounts;
- vendor-default accounts;
- embedded accounts;
- undocumented local accounts;
- production test accounts;
- developer accounts in production;
- orphaned service accounts;
- accounts without an accountable owner;
- accounts with no expiry where access is temporary;
- interactive use of service identities;
- local accounts that duplicate corporate identities; and
- accounts created outside the approved process.

The permitted account types and constraints should be recorded in the SSP, role model, SyOps or application security design.

## 2. Prefer enterprise identities and minimise local accounts

Where technically supported, the application should use the approved corporate identity service rather than maintaining a separate username and password store.

The application should:

- map enterprise identities to application permissions;
- use stable enterprise identifiers rather than display names;
- avoid creating a second password for the same user;
- prevent duplicate application identities;
- reject identities from unapproved identity providers;
- validate issuer, audience and relevant claims;
- handle renamed users without creating a new account;
- reconcile application access with disabled enterprise identities;
- prevent local fallback from silently bypassing enterprise authentication; and
- document any application-local identity that remains necessary.

Local accounts should be exceptional and subject to stronger ownership, authentication, review, monitoring and removal controls.

## 3. Assign application account managers

Every application account population should have an accountable manager or owner.

Responsibilities should include:

- approving or confirming legitimate need;
- determining the correct role and information scope;
- reviewing current access;
- responding to joiner, mover and leaver notifications;
- reviewing dormant accounts;
- confirming supplier and temporary access;
- resolving orphaned service identities;
- approving exceptions; and
- ensuring removal when access is no longer justified.

The account manager may be:

- an application owner;
- business information owner;
- project manager;
- line manager;
- role owner;
- service owner;
- integration owner;
- supplier manager; or
- privileged-access owner.

The application should avoid ambiguous ownership such as “IT” or “the project team”.

## 4. Establish conditions for role and group membership

The application should define the conditions that must be satisfied before an identity may join each application role, group, project or information community.

Conditions may include:

- active corporate identity;
- employment or contract status;
- approved business need;
- manager approval;
- information-owner approval;
- project membership;
- required training;
- confidentiality or contractual obligations;
- nationality, clearance or handling restrictions;
- separation-of-duties checks;
- privileged-access approval;
- supplier engagement;
- defined start and end date; and
- completion of any required onboarding.

The application should not use group membership merely because it is convenient. Membership should reflect an approved business relationship.

## 5. Maintain an authoritative role and account model

The application should maintain a clear model showing:

- account type;
- role or group;
- permitted functions;
- permitted information scope;
- privileged status;
- incompatible roles;
- approver;
- account manager;
- expected review frequency;
- expiry requirements;
- authentication source;
- account creation method;
- account removal method; and
- logging requirements.

This model should align with:

- AC-03 access enforcement;
- AC-05 separation of duties;
- AC-06 least privilege;
- IA-02 identification and authentication;
- IA-05 authenticator management; and
- AU-02 event logging.

The SSP should summarise the model and point to the authoritative role or access matrix.

## 6. Use an approved account request and approval process

Application access should be created only following an attributable, approved request.

The request should normally identify:

- user or service identity;
- business justification;
- requested role;
- project or information scope;
- privileged functions;
- start date;
- expiry date where applicable;
- line manager;
- information or role owner;
- separation-of-duties assessment;
- supplier or contract reference;
- requester;
- approver; and
- fulfilment evidence.

The application should prevent:

- self-approval;
- informal email-only provisioning without traceability;
- administrators granting access solely on verbal instruction;
- reuse of a former user’s account;
- broad access “just in case”; and
- creation before required approvals are complete.

## 7. Provision the minimum approved access

When access is created, the application should grant only the permissions and information scope approved in the request.

The provisioning process should:

- use named identities;
- assign the approved role;
- assign only approved project or data scope;
- avoid default privileged membership;
- avoid broad inherited groups unless explicitly approved;
- apply expiry where required;
- distinguish production and non-production;
- record the provisioner and time;
- verify that the account works as intended;
- confirm that prohibited functions remain inaccessible; and
- notify the account manager or requester of completion.

The application should not rely on post-provisioning clean-up to remove excessive default access.

## 8. Control account activation

Accounts should become active only when required conditions are satisfied.

Activation controls should consider:

- approved start date;
- active enterprise identity;
- completed approvals;
- required training;
- contract commencement;
- project start;
- successful identity mapping;
- absence of incompatible role assignments;
- valid sponsor or manager; and
- required privileged-access controls.

Pre-created accounts should remain disabled until the authorised start condition is met.

## 9. Manage movers and role changes

A user’s existing access should be reassessed when they:

- change job;
- change manager;
- move project;
- change business unit;
- change contract;
- change supplier;
- gain or lose privileged duties;
- change location or handling eligibility;
- stop supporting the application; or
- assume a conflicting role.

The application should:

- remove obsolete access, not merely add new access;
- reassess project and data scope;
- check separation of duties;
- update the account manager;
- update expiry;
- invalidate stale sessions or cached permissions where appropriate;
- record the change;
- notify relevant owners; and
- verify effective access after modification.

A mover process that only accumulates permissions is not compliant account management.

## 10. Disable and remove leaver access promptly

When a person leaves the organisation, project, contract or supplier engagement, the application should ensure that application access is disabled or removed within the required timeframe.

The application should:

- consume enterprise termination notifications where available;
- disable application-local accounts;
- remove project and role memberships;
- remove privileged access;
- revoke active sessions and application tokens where supported;
- revoke API keys or delegated credentials;
- transfer ownership of records, jobs and integrations;
- protect records and audit history;
- preserve necessary investigation evidence;
- remove support access;
- update contact and ownership records; and
- confirm completion.

Where enterprise account disablement blocks sign-in, the application must still clean up application roles, ownership, local credentials and non-person dependencies.

## 11. Manage temporary accounts

Temporary access should be:

- approved for a specific purpose;
- limited to the minimum role and data scope;
- assigned a start and end time;
- automatically disabled where practical;
- reviewed if extended;
- clearly identifiable;
- monitored;
- prohibited from becoming permanent by default; and
- removed when the task ends.

Examples include:

- short-term project members;
- migration support;
- release support;
- penetration testers;
- auditors;
- incident-response specialists;
- supplier engineers; and
- temporary delegated approvers.

## 12. Manage emergency accounts

Where emergency accounts are required, the application should define:

- permitted emergency scenarios;
- accountable owner;
- approval or break-glass process;
- credential custody;
- allowed functions;
- restrictions on ordinary use;
- activation method;
- duration;
- monitoring;
- immediate notification;
- post-use review;
- credential reset or rotation;
- evidence preservation; and
- conditions for return to the disabled state.

Emergency accounts should not become convenient administrative accounts.

Where the enterprise PAM service provides emergency access, the application should integrate with it and still log the application actions performed.

## 13. Manage privileged application accounts

Privileged accounts should be more tightly controlled than ordinary business accounts.

The application should:

- use named privileged identities or attributable privileged roles;
- avoid shared administrator accounts;
- separate routine and privileged use where required;
- integrate with enterprise PAM where supported;
- limit privileged functions;
- restrict privileged information access;
- require stronger approval;
- assign expiry or review dates;
- review more frequently;
- log material privileged activity;
- prohibit dormant privilege;
- remove privilege when duties change; and
- prevent privileged users from silently bypassing business controls.

Application administration should not automatically provide unrestricted access to all business records unless specifically justified.

## 14. Manage service, workload and integration identities

Non-person identities require the same rigour as human accounts.

Each service identity should have:

- unique identifier;
- clear technical purpose;
- owning application or service;
- named human owner;
- approved environment;
- permitted interfaces;
- permitted operations;
- data scope;
- credential or certificate reference;
- creation date;
- review frequency;
- expiry or rotation requirements;
- dependency information;
- monitoring;
- removal trigger; and
- documented prohibition on interactive use unless required.

The application should avoid:

- one service account shared across unrelated components;
- production and non-production sharing;
- broad database ownership;
- permanent high privilege;
- embedded credentials;
- unused service identities;
- identities with no current owner; and
- credentials that remain active after an integration is retired.

## 15. Manage API client accounts and delegated access

For API clients, applications should record and control:

- client identity;
- owning system;
- authorised endpoints;
- scopes;
- data or project boundaries;
- token audience;
- credential type;
- secret or certificate reference;
- rate and volume limits;
- start and expiry;
- approval;
- contact;
- monitoring; and
- revocation process.

Where a service acts on behalf of a user, the application should distinguish:

- the calling service;
- the end user;
- delegated permissions;
- the permitted duration; and
- whether onward delegation is allowed.

A powerful integration identity should not conceal which user initiated a business action.

## 16. Control shared and generic accounts

Shared accounts should normally be prohibited.

Where a product or operational constraint makes one unavoidable, the application should document:

- why a named identity cannot be used;
- approved users;
- owner;
- permitted functions;
- credential-management method;
- access path;
- session monitoring;
- check-out and check-in controls;
- expiry or rotation;
- logging limitations;
- compensating controls;
- review frequency;
- remediation or replacement plan; and
- risk approval.

Use of enterprise PAM may make a shared technical account attributable, but the application should still minimise its privilege and scope.

## 17. Control local and fallback accounts

Application-local accounts should be:

- explicitly inventoried;
- justified;
- disabled by default where not required;
- protected using approved authentication requirements;
- limited in privilege;
- excluded from ordinary use;
- monitored;
- periodically tested;
- reviewed more frequently;
- assigned an owner;
- prevented from using default credentials; and
- removed when enterprise integration becomes available.

Fallback accounts used for identity-service outages should have documented activation, monitoring and post-use review.

## 18. Control test, training and demonstration accounts

Non-production accounts should be separated from production.

The application should:

- prohibit production credentials in lower environments;
- prevent test identities from accessing production;
- avoid real personal or supplier accounts where unnecessary;
- avoid shared privileged test credentials;
- use synthetic identities where practical;
- define expiry;
- remove stale accounts;
- prevent lower-environment tokens from being accepted by production;
- clearly distinguish environment and purpose;
- control test administrator roles; and
- prevent demonstration accounts from being deployed into production.

## 19. Monitor account use

The application should monitor for:

- use of dormant accounts;
- disabled-account attempts;
- unexpected privileged use;
- service identity used interactively;
- account use outside expected hours or workflow;
- supplier access outside approved periods;
- emergency-account use;
- repeated denied role assignment;
- unusual project membership changes;
- role accumulation;
- shared-account activity;
- local-account use;
- stale API clients;
- accounts with no recent legitimate use;
- activity after termination or role removal; and
- use from an unexpected component or interface.

The application should send relevant events to the approved enterprise monitoring service.

## 20. Define and manage inactivity

Where appropriate, the application should identify inactive accounts and take defined action.

The process should:

- define inactivity by account type;
- distinguish infrequent but legitimate access;
- identify last successful use;
- identify last role or membership use;
- notify the account manager;
- suspend before deletion where appropriate;
- preserve ownership and records;
- avoid disabling essential unattended services without impact assessment;
- require reapproval for reactivation; and
- record the decision.

A service account should not be judged by interactive sign-in activity; its expected technical use should be assessed separately.

## 21. Review application accounts periodically

The application should periodically review:

- all active user accounts;
- role assignments;
- project or data-partition memberships;
- privileged accounts;
- support accounts;
- temporary accounts;
- emergency accounts;
- supplier accounts;
- service identities;
- API clients;
- local accounts;
- inactive accounts;
- accounts without owners;
- incompatible role combinations;
- expired approvals; and
- identities belonging to retired components or integrations.

The reviewer should have enough business context to decide whether access is still necessary.

A list sent to a manager with no description of privileges or information scope is weak evidence.

## 22. Review effective access, not only account existence

Applications often derive access from several sources:

- enterprise groups;
- application roles;
- project membership;
- delegated authority;
- record ownership;
- workflow state;
- nested groups;
- temporary elevation;
- API scopes; and
- support roles.

The review should show the effective result, including:

- what the identity can do;
- which information it can reach;
- whether the access is privileged;
- how it was granted;
- who approved it;
- when it expires; and
- whether incompatible combinations exist.

## 23. Reconcile accounts with authoritative identity sources

The application should periodically compare its account and role data with:

- active corporate identities;
- HR or contractor status where supplied through enterprise processes;
- enterprise directory groups;
- privileged-access records;
- supplier rosters;
- project membership;
- service-account registers;
- approved access requests; and
- application component inventory.

The reconciliation should identify:

- application accounts with no active enterprise identity;
- duplicate identities;
- mismatched identifiers;
- unapproved local accounts;
- users absent from the approved project list;
- service accounts with no owner;
- roles that do not match approved requests;
- expired supplier access; and
- accounts associated with retired components.

## 24. Protect account-management functions

Functions that create, change, enable, disable or delete accounts and roles are privileged.

The application should:

- restrict them to authorised administrators;
- separate request, approval and fulfilment where proportionate;
- prevent self-approval;
- prevent ordinary support users from granting privilege;
- protect group-to-role mappings;
- protect bulk provisioning;
- validate requests;
- use attributable administration;
- require controlled change for role-model changes;
- log all material actions;
- prevent API bypass; and
- test that non-privileged users cannot invoke them.

## 25. Protect account data

The application should protect:

- identity mappings;
- role assignments;
- project membership;
- account status;
- account-manager data;
- supplier status;
- service-account ownership;
- API scopes;
- temporary-access dates;
- privileged status;
- account-review decisions; and
- account-related audit records.

Access to account data should be restricted, and changes should be attributable.

Passwords, full tokens, private keys and other authenticators should not be stored in account registers or evidence records.

## 26. Log account-management events

The application should generate events for:

- account creation;
- account activation;
- account disablement;
- account deletion;
- role assignment and removal;
- project or group membership change;
- privilege assignment and removal;
- account reactivation;
- temporary-access extension;
- emergency-account activation;
- supplier-account use;
- service-account creation and change;
- API client registration and revocation;
- local-account use;
- failed administrative action;
- changes to account policy; and
- bulk provisioning or removal.

Events should include:

- acting administrator or process;
- affected identity;
- action;
- previous and new state where appropriate;
- role or scope;
- time;
- outcome;
- source component;
- request or approval reference; and
- reason where captured.

## 27. Notify relevant owners of account changes

The application should ensure that account managers or owners are informed of relevant changes such as:

- new access;
- privileged access;
- temporary-access expiry;
- dormant access;
- supplier engagement ending;
- user transfer;
- disabled enterprise identity;
- service-owner change;
- credential compromise;
- emergency-account use;
- rejected or failed deprovisioning;
- unresolved orphan account; and
- overdue review.

Notification can be implemented through enterprise workflow, service management or application reporting. The application should avoid creating a disconnected manual notification process where established tooling exists.

## 28. Handle account-management failures safely

The application should define safe behaviour when provisioning or deprovisioning fails.

Examples include:

- corporate identity not found;
- duplicate identity;
- invalid role;
- missing approver;
- role conflict;
- directory synchronisation failure;
- account disablement failure;
- API revocation failure;
- service owner missing;
- expired account remaining active;
- partial project-membership removal; and
- bulk change only partly completed.

The application should:

- fail closed for new access;
- avoid partial privilege assignment;
- alert support;
- record the failed state;
- retry safely;
- prevent duplicate processing;
- verify eventual completion;
- escalate overdue deprovisioning; and
- provide manual recovery under controlled authority.

## 29. Test account-management controls

Testing should include:

- approved user provisioning;
- denied unapproved provisioning;
- duplicate-user handling;
- role and project assignment;
- separation-of-duties conflict;
- temporary-account expiry;
- dormant-account suspension;
- mover access removal;
- leaver disablement;
- active-session behaviour after disablement;
- privileged-account controls;
- supplier-account expiry;
- service-account restrictions;
- API client revocation;
- local fallback account controls;
- account-manager notifications;
- audit-event generation;
- failed identity synchronisation;
- failed deprovisioning; and
- non-privileged attempts to manage accounts.

Testing should validate the resulting effective access, not merely that a workflow ticket completed.

## 30. Verify deprovisioning end to end

Account removal should be verified across:

- application account;
- role assignments;
- project membership;
- privileged roles;
- delegated access;
- API tokens;
- service credentials;
- active sessions;
- scheduled jobs;
- report distribution;
- record ownership;
- integration ownership;
- local thick-client data where relevant;
- support access; and
- downstream application-controlled stores.

A disabled corporate identity can prevent sign-in while residual application permissions and credentials remain. Those residual items still require clean-up.

## 31. Preserve business and audit records when accounts are removed

Account deletion should not destroy required business or audit history.

The application should:

- preserve attribution to the former identity;
- transfer ownership where necessary;
- retain approvals and signatures;
- preserve audit events;
- prevent identifier reuse that confuses historical records;
- distinguish deleted, disabled and anonymised identities;
- support legal and records requirements;
- avoid changing historical actions to the replacement owner; and
- protect former-user records from unauthorised access.

Where personal information must be minimised, the application should follow approved privacy and records processes without undermining audit integrity.

## 32. Review the account model after change

Account management should be reassessed after:

- new role;
- new project type;
- new privileged function;
- new integration;
- new supplier;
- migration;
- identity-provider change;
- product upgrade;
- new non-production environment;
- organisational restructuring;
- incident;
- audit or penetration-test finding;
- change to information sensitivity; or
- change to enterprise joiner–mover–leaver processes.

The role model, provisioning rules, account reviews, tests and SSP should remain aligned.

## 33. Remove obsolete account types and roles

When a role, integration, supplier, project or feature is retired, the application should:

- disable affected accounts;
- remove role definitions;
- revoke service credentials;
- remove API clients;
- remove group mappings;
- stop scheduled processes;
- transfer ownership;
- update the role matrix;
- update monitoring;
- update the component and service-account inventory; and
- verify that the retired access path no longer works.

Obsolete roles should not remain available for convenient reuse.

## 34. Manage account-management exceptions

Where a commercial or legacy product cannot meet the expected account model, record:

- affected account type;
- expected control;
- actual behaviour;
- business need;
- affected users or services;
- privilege and information exposure;
- risk;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, upgrade, isolation or replacement plan; and
- review or expiry date.

Examples include:

- unavoidable shared administrator account;
- inability to federate;
- no automatic expiry;
- no account-use report;
- inability to revoke sessions;
- coarse role membership;
- local password store;
- service account with excessive privilege; or
- incomplete audit events.

The exception should be visible in the application addendum or risk process, not buried in an administrator’s notes.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate identity, MFA, joiner–mover–leaver processes, service management and central logging. They exclude enterprise IAM/PAM engineering, large-scale data clean-up and major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define permitted and prohibited account types** | Identify named users, privileged users, service identities, integrations, temporary and supplier accounts and explicitly prohibit anonymous, default, shared and undocumented accounts unless approved. | Summarise in the **SSP AC-02 statement** and maintain detail in the existing **security design**, **SyOps**, **role model** or **account-management section of the ConOps**. | **4–8 hours** |
| **2. Define application account managers and approvers** | Assign accountable owners for business roles, projects, privileged access, service identities and supplier accounts. | Record responsibilities in the **SSP**, **RACI**, **support model**, **SyOps**, **role matrix** or **service-account register**. | **3–6 hours** |
| **3. Maintain an approved role and account model** | Define each role, permitted function, information scope, privilege level, approver, account manager, review frequency and incompatible access. | Use the existing **role/access matrix**, **business requirements**, **security design** and **SSP AC-02/AC-03/AC-06 sections**. | **8–20 hours** |
| **4. Use approved request, approval and provisioning workflows** | Require attributable requests, business justification, role and scope, approval, start/expiry dates and separation-of-duties checks before access is created. | Evidence remains in the normal **IAM**, **service-management**, **access-request**, **change** or **workflow records**, referenced from the SSP. | **8–20 hours** |
| **5. Integrate or reconcile with corporate identity** | Map stable corporate identities to application accounts, avoid duplicate local credentials and identify accounts whose enterprise identity is disabled or missing. | Describe the design in the **identity integration specification**, **security architecture**, **SyOps** and **SSP IA-02/AC-02 sections**. Retain reconciliation results in normal **access-review evidence**. | **12–32 hours** |
| **6. Provision least-privilege roles and information scope** | Grant only the approved role, project, case or data scope and verify that default or inherited access does not exceed the request. | Record approved access in the **access request** and **role matrix** and retain fulfilment and verification in the normal **IAM/service record** and **access-control test report**. | **6–16 hours** |
| **7. Implement mover and leaver handling** | Remove obsolete roles and project memberships, disable local accounts, revoke sessions or tokens where supported and transfer record or service ownership. | Define the process in the **SyOps**, **support model**, **SSP** and enterprise **joiner–mover–leaver workflow**. Retain completion evidence in normal **IAM/service records**. | **8–24 hours initially** |
| **8. Control temporary, emergency, supplier and support accounts** | Require purpose, approval, minimum scope, named ownership, start and expiry, enhanced monitoring and post-use review. | Record arrangements in the **SyOps**, **support model**, **supplier record**, **incident-response annex**, **PAM record** and **SSP**. | **8–20 hours** |
| **9. Inventory and control service and API identities** | Give each non-person identity a unique purpose, owner, environment, scope, credential reference, review date and removal trigger. | Use the existing **service-account register**, **interface control document**, **CM-08 inventory**, **security design**, **SyOps** and **SSP**. | **8–24 hours** |
| **10. Restrict and audit account-management functions** | Limit creation, modification, privilege assignment and deletion to approved administrators or automated services and prevent self-approval and bypass. | Record controls in the **role matrix**, **security design**, **SSP AC-02/AC-05/AC-06 sections** and normal **administrator access test report**. | **8–20 hours** |
| **11. Log account lifecycle and privilege changes** | Generate events for creation, activation, role change, project membership, privilege, disablement, deletion, emergency use and service-client changes. | Define events in the **SSP AU-02/SI-04/AC-02 sections** and existing **event specification**. Verify through **SIEM onboarding** and the normal **security test report**. | **6–16 hours** |
| **12. Review accounts and effective access periodically** | Review user, privileged, service, API, supplier, temporary, dormant and local accounts, including effective roles and information scope. | Retain outcomes in established **access-review records**, **service reviews**, **PAM reviews**, **role-owner attestations**, **risk records** or **application governance minutes**. | **8–24 hours per review** |
| **13. Detect and resolve dormant, orphaned and expired access** | Identify accounts with no legitimate use, missing owners, inactive identities, expired approvals or retired dependencies and suspend or remove them. | Use existing **reconciliation reports**, **access-review records**, **service-account register**, **problem records** and **risk register**. | **6–16 hours initially; 3–8 hours per review** |
| **14. Test provisioning, modification and deprovisioning end to end** | Test positive and negative provisioning, role conflicts, expiry, mover/leaver removal, session revocation, API-client revocation and audit generation. | Add cases to the normal **security test plan**, **integration test plan** or **operational acceptance test** and retain results in the established **test report**. | **16–40 hours per major test cycle** |
| **15. Verify that account removal preserves records and attribution** | Confirm that disabling or deleting accounts preserves audit history, approvals and record ownership while removing current access. | Capture requirements in the **data model**, **records design**, **SyOps** and **SSP** and retain evidence in the normal **system/security test report**. | **6–16 hours** |
| **16. Document and manage account-management limitations** | Record unavoidable shared accounts, local credentials, missing expiry, weak review reporting or incomplete session revocation with compensating controls. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP AC-02 statement**. | **4–10 hours per exception** |

### Indicative total

For a typical internal application that integrates with the corporate directory and has a manageable role model, initial application effort is commonly around **110–260 hours**.

A simple commercial application with a few roles and mature enterprise provisioning may require less. A legacy, highly privileged or project-segregated application with local accounts, thick clients, many integrations, supplier access or poor lifecycle automation may require substantially more.

The estimates should not be added mechanically where work overlaps. AC-02 activities commonly share design, implementation and evidence with AC-03, AC-05, AC-06, IA-02, IA-05, CM-08, AU-02, SI-04 and CA-07.

---

## Suggested document placement

To avoid creating disconnected evidence, account-management information should normally be distributed across established application and SDLC artefacts:

- **SSP:** AC-02 implementation approach, permitted account types, inherited identity services, account managers, lifecycle process, review frequency, monitoring and exceptions.
- **ConOps or SyOps:** operational provisioning, support, temporary access, emergency access, supplier access, deprovisioning and failure handling.
- **Security architecture:** identity provider, federation, provisioning paths, service identities, privileged paths and trust boundaries.
- **Role/access matrix:** roles, functions, information scope, privilege, incompatible access, approvers and owners.
- **RACI or support model:** application, role, project, service and supplier account-management responsibilities.
- **IAM or service-management workflow:** requests, approvals, fulfilment, modification, suspension and removal.
- **Identity integration specification:** identifiers, claims, group mappings, synchronisation, error handling and reconciliation.
- **Service-account register:** non-person identity, owner, purpose, environment, permissions, credential reference, review and retirement.
- **Interface control documents:** API clients, service identities, scopes, delegation and revocation.
- **CM-08 inventory:** components, integrations and associated non-person identities.
- **SDLC backlog and technical design:** provisioning, expiry, revocation, session invalidation, reconciliation and audit requirements.
- **Test plans and reports:** positive and negative lifecycle tests, mover/leaver, expiry, role conflicts, service identities and preservation of attribution.
- **AU-02 and SI-04 evidence:** account lifecycle, privilege, emergency and anomaly events.
- **Access reviews and service reviews:** effective access, dormant accounts, owners, suppliers and service identities.
- **Risk register or application addendum:** local accounts, shared accounts, incomplete lifecycle automation, weak review evidence and compensating controls.
- **Release and operational acceptance records:** confirmation that identity integration, provisioning and deprovisioning work in the released version.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- workforce identity proofing;
- authoritative HR identity status;
- corporate directory services;
- enterprise MFA;
- enterprise joiner–mover–leaver orchestration;
- corporate identity-governance and administration tooling;
- enterprise privileged-access management platform;
- corporate password and authenticator policy;
- Microsoft Windows EUC account management;
- VPN and remote-access account management;
- enterprise service-account and secrets platforms;
- organisation-wide access-review policy;
- corporate supplier onboarding and offboarding;
- central SIEM and SOC operations;
- enterprise disciplinary and personnel processes; and
- organisation-wide account-management standards and exception governance.

The application team must still:

- define allowed account types;
- appoint application account and role owners;
- map corporate identities correctly;
- approve and enforce application roles and information scope;
- manage application-local and non-person identities;
- respond to movers and leavers;
- review effective application access;
- remove residual permissions and credentials;
- log account lifecycle events;
- test the complete lifecycle; and
- formally manage product limitations.

> **Key dividing line:** the enterprise establishes and maintains the corporate identity; the application manages the identity’s lifecycle, privileges, scope and continued need within the business application.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, AC-02 Account Management.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, AC-02 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-63-4, Digital Identity Guidelines**.
4. National Institute of Standards and Technology, **NIST SP 800-63B-4, Digital Identity Guidelines: Authentication and Authenticator Management**.
5. National Institute of Standards and Technology, **NIST SP 800-207, Zero Trust Architecture**.
