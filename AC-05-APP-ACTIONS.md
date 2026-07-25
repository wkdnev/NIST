# AC-05 Separation of Duties — Application Actions

## Purpose

For an IT application, AC-05 means the application must ensure that **no single user, administrator, developer, service or process can complete a sensitive or high-risk activity end to end without appropriate independent involvement, approval or review**.

The enterprise may provide:

- corporate identity and access governance;
- joiner–mover–leaver processes;
- privileged-access management;
- organisational role definitions;
- service-management and change-control workflows;
- managed Microsoft Windows EUC devices;
- source-code and deployment platforms;
- central logging and monitoring;
- enterprise database and infrastructure administration; and
- corporate fraud, compliance and risk-management processes.

Those capabilities are inherited.

The application remains responsible for identifying and enforcing separation within its own business processes, technical administration, access model, software lifecycle and data-management functions. This includes deciding which combinations of duties are incompatible and preventing one identity from improperly controlling all stages of a sensitive transaction.

NIST AC-05 requires organisations to identify and document duties that require separation and to define application access authorisations that support that separation. NIST describes separation of duty as preventing a single user from receiving enough privilege to misuse a system alone, and recognises both:

- **static separation of duties** — conflicting roles cannot be assigned to the same identity; and
- **dynamic separation of duties** — the application checks the conflict when the action or transaction is performed.

> **Core principle:** a person may have authority to initiate, prepare or administer an activity, but should not also be able to independently approve, release, conceal and verify the same activity where that combination would create unacceptable risk.

---

## 1. Identify sensitive application processes

The application should identify business and technical processes where one person controlling the whole process could cause unacceptable harm.

Examples include:

- creating and approving a requirement;
- raising and approving a change;
- creating and releasing a controlled record;
- requesting and approving application access;
- assigning and using privileged access;
- modifying and approving security configuration;
- developing and deploying production code;
- creating and approving a database migration;
- preparing and releasing a payment or financial transaction;
- importing and validating authoritative data;
- creating and approving a supplier;
- submitting and approving an exception;
- changing and reviewing audit configuration;
- deleting and authorising deletion of records;
- restoring and validating recovered data;
- initiating and approving bulk export;
- creating and signing a controlled report; and
- investigating an incident while being the subject of the investigation.

The analysis should be risk-based. Not every routine activity requires two people.

## 2. Define incompatible duties

For each sensitive process, the application should define the duties that should not be performed by the same identity.

Common incompatible combinations include:

- requester and approver;
- author and final approver;
- originator and independent reviewer;
- access requester and access approver;
- access approver and access fulfiller;
- privileged-access administrator and privileged-access reviewer;
- developer and production deployer;
- developer and final security tester;
- change implementer and change approver;
- database migration developer and production migration executor;
- transaction creator and transaction releaser;
- data importer and data-quality approver;
- administrator and audit-log administrator;
- evidence producer and independent assessor;
- backup operator and recovery validator;
- supplier administrator and supplier payment approver;
- incident subject and incident investigator; and
- exception requester and risk acceptor.

The duties should be defined in language that maps directly to application roles, functions and workflow steps.

## 3. Determine whether separation is static or dynamic

The application should decide how each conflict will be enforced.

### Static separation

Static separation prevents conflicting roles from being assigned to the same identity.

Use it where:

- the roles are inherently incompatible;
- the conflict applies continuously;
- the organisation has enough staff to maintain the separation;
- the application can evaluate effective role membership; and
- exceptional dual-role use is not normally required.

Example:

> A user assigned the **Application Access Approver** role cannot also hold the **Application Access Administrator** role.

### Dynamic separation

Dynamic separation allows a user to hold several roles but prevents conflicting actions on the same transaction, record, case or change.

Use it where:

- users legitimately perform different duties on different records;
- smaller teams require flexible role assignment;
- conflict depends on who initiated a particular transaction;
- a user may approve another person’s work but not their own; or
- the restriction depends on workflow state or business context.

Example:

> A user may hold both **Requirements Author** and **Requirements Approver**, but cannot approve a requirement they created or materially amended.

The design should state clearly which type applies.

## 4. Maintain an approved separation-of-duties matrix

The application should maintain an authoritative matrix or equivalent rule set showing:

- business or technical process;
- protected action;
- originating duty;
- reviewing or approving duty;
- conflicting roles;
- transaction-level restrictions;
- information or project scope;
- permitted exceptions;
- approving owner;
- enforcement method;
- monitoring;
- review frequency; and
- related application functions.

The SSP should summarise the approach and reference the authoritative matrix rather than duplicate every rule.

## 5. Consider effective access, not only named roles

Conflicts may arise through several access mechanisms at once.

The application should assess effective access derived from:

- application roles;
- enterprise directory groups;
- nested groups;
- project membership;
- record ownership;
- delegated authority;
- temporary elevation;
- support roles;
- privileged-access assignments;
- API scopes;
- service identities;
- database roles;
- workflow configuration; and
- emergency access.

A user may appear compliant when individual role assignments are viewed separately but still possess an incompatible combination through inheritance.

## 6. Enforce separation when roles are assigned

When a user is assigned a role, the application or access workflow should check for incompatible access.

The application should:

- identify existing roles and memberships;
- evaluate inherited and nested access;
- check privileged and temporary assignments;
- identify project-specific conflicts;
- prevent or flag incompatible combinations;
- require independent approval for authorised exceptions;
- record the decision;
- apply an expiry date where the conflict is temporary;
- notify the appropriate role owner; and
- re-evaluate conflicts when roles change.

A warning that administrators can ignore without justification is weak enforcement.

## 7. Enforce separation at transaction time

Role-assignment controls alone may not prevent self-approval or self-review.

For sensitive transactions, the application should validate:

- who created the record;
- who last materially changed it;
- who submitted it;
- who reviewed it;
- who approved it;
- who released it;
- whether the user is acting under delegation;
- whether the user has an ownership or reporting relationship that creates a conflict;
- whether the required number of independent approvals has been met; and
- whether an emergency override is active.

The application should deny the action if the separation rule is not satisfied.

## 8. Prevent self-approval

The application should prevent users from approving, releasing, certifying or independently reviewing their own work where independence is required.

This should include actions performed through:

- browser interfaces;
- thick clients;
- APIs;
- batch processing;
- administrative tools;
- direct workflow transitions;
- mobile interfaces where approved;
- bulk operations; and
- delegated authority.

The application should consider who made the **material change**, not merely who originally created the record.

## 9. Prevent approval loops and collusion-enabling patterns

The application should identify weak workflow patterns such as:

- two users routinely approving each other’s transactions;
- approval by a subordinate where independence is required;
- repeated use of the same small approval pair;
- an approver delegating back to the requester;
- circular delegation;
- chained impersonation;
- a support administrator altering a record and then approving through another role;
- bulk reassignment immediately before approval; and
- use of generic or shared accounts that conceal the actual operator.

Not every pattern is necessarily malicious, but the application should log enough context to support review.

## 10. Separate access request, approval and fulfilment

For higher-risk access, the application should distinguish:

1. the person requesting access;
2. the manager or information owner approving business need;
3. the security or role owner confirming appropriateness;
4. the administrator or automated service implementing access; and
5. the reviewer confirming continued need.

The exact number of people should be proportionate. The requester should not approve their own access, and a person granting their own privilege should normally be prohibited.

## 11. Separate privileged-access administration and use

Where proportionate, the application should distinguish:

- who defines privileged roles;
- who approves privileged access;
- who assigns privileged access;
- who uses privileged access;
- who reviews privileged activity; and
- who manages privileged audit records.

The application should avoid allowing one administrator to:

- grant themselves privilege;
- use the privilege;
- modify the logging configuration;
- delete or suppress evidence; and
- approve their own activity review.

Enterprise PAM may enforce part of this chain, but the application must still separate application-specific role assignment, use and review.

## 12. Separate business administration from technical administration

The application should distinguish between:

- business administration — projects, workflows, reference data and business membership;
- security administration — roles, permissions, authentication and policy;
- technical administration — configuration, deployment, service operation and integration;
- database administration — schema, maintenance and direct data access; and
- audit administration — event configuration, retention and review.

These duties should not automatically be combined into one unrestricted “application administrator” role.

Where a commercial product offers only one administrator role, the resulting risk should be assessed and mitigated.

## 13. Separate development, testing and production deployment

For applications developed or configured internally, the SDLC should prevent one person from independently writing, approving, testing and deploying a production change.

The application should use proportionate controls such as:

- protected branches;
- peer review;
- independent approval;
- automated testing;
- security testing;
- controlled artefact promotion;
- separation between development and production credentials;
- deployment through approved pipelines;
- restriction of direct production changes;
- independent post-deployment verification; and
- attributable emergency change.

For a small team, automation, immutable artefacts and independent release approval may provide practical separation even when staffing is limited.

## 14. Separate source change from release artefact approval

The application should ensure that production artefacts are derived from approved source and cannot be silently substituted by the developer or deployer.

Controls may include:

- protected release tags;
- build pipelines using controlled inputs;
- artefact hashes or signatures;
- restricted artefact repositories;
- separation of build and promotion permissions;
- release manifest approval;
- deployment only from the approved repository; and
- post-deployment baseline verification.

This aligns AC-05 with CM-02, CM-03, CM-05, SI-07 and SA-11.

## 15. Separate database migration duties

Database migrations can bypass application controls and materially change data or security.

The application should consider separating:

- migration design;
- migration review;
- approval;
- execution;
- validation;
- rollback approval; and
- direct production data repair.

Runtime application identities should not normally possess schema-modification rights.

A developer who wrote a high-impact migration should not be the sole person approving its production execution and validating its outcome.

## 16. Separate security configuration change and review

Changes to security-relevant configuration should require appropriate independent involvement.

Examples include:

- identity-provider trust;
- role definitions;
- permission mappings;
- session settings;
- logging configuration;
- export settings;
- encryption settings;
- certificate trust;
- destination allow-lists;
- malware-scanning behaviour;
- retention and deletion rules; and
- emergency-access settings.

The person making a material change should not be the only person confirming that the resulting state is correct.

## 17. Separate audit generation, administration and review

The application should prevent users from being able to perform sensitive activity and then suppress the evidence of that activity.

Where proportionate, distinguish:

- event generation;
- logging configuration;
- access to raw logs;
- log export;
- retention management;
- alert configuration;
- investigation;
- audit review; and
- finding closure.

Application administrators should not automatically be able to delete or rewrite audit records.

## 18. Separate data creation, validation and release

For authoritative or safety-, engineering-, financial- or contract-relevant data, the application should distinguish:

- data entry;
- data validation;
- technical review;
- business approval;
- release or publication; and
- later amendment.

The application should preserve who performed each duty and prevent later edits from making an earlier approval appear valid.

## 19. Separate import and reconciliation

For bulk data import, the application should consider separating:

- file preparation;
- import execution;
- validation;
- exception handling;
- reconciliation;
- acceptance; and
- correction.

The user who imports a high-impact data set should not necessarily be able to mark all import exceptions as acceptable without independent review.

## 20. Separate export request and high-risk release

For sensitive or bulk exports, the application may need to distinguish:

- export requester;
- data owner;
- approving authority;
- export operator;
- recipient validator; and
- post-export reviewer.

This is particularly important for:

- unrestricted extracts;
- cross-project data;
- supplier disclosure;
- controlled technical information;
- personal data;
- incident evidence;
- source code;
- audit records; and
- production-to-non-production transfer.

## 21. Separate backup operation and recovery validation

The application should distinguish, where proportionate:

- backup administration;
- restoration request;
- restoration execution;
- data-integrity validation;
- security validation;
- business acceptance; and
- return-to-service approval.

The person restoring data should not be the sole authority confirming that the recovered application is trustworthy.

## 22. Separate incident handling where conflicts exist

During an incident, the application should prevent individuals from controlling investigations where they are:

- the subject of the investigation;
- responsible for the affected change;
- owner of the disputed activity;
- responsible for the relevant audit evidence;
- able to modify the evidence under review; or
- in another material conflict of interest.

The enterprise incident process owns investigation governance, but the application should expose conflicts and provide independent technical support.

## 23. Apply separation to service and machine identities

Non-person identities can also create conflicting authority.

The application should avoid allowing one service identity to:

- create and approve a transaction;
- modify data and certify its integrity;
- deploy code and approve deployment;
- administer security policy and suppress logs;
- produce and consume the same control message without independent validation;
- create and release an export;
- prepare and accept an import; or
- modify and verify a backup.

Where automation legitimately performs several steps, the application should use:

- distinct service identities;
- independent policy checks;
- signed approvals;
- immutable logs;
- controlled pipeline gates;
- independent validation jobs; and
- human approval at the appropriate risk point.

Automation does not remove the need for separation; it changes how separation is implemented.

## 24. Protect delegation

Delegation should not undermine separation-of-duties rules.

The application should:

- record the delegator and delegate;
- define the delegated role or action;
- restrict start and end dates;
- prevent circular delegation;
- prevent delegation back to the originator;
- re-evaluate conflicts;
- distinguish acting identity from delegated authority;
- prevent onward delegation unless approved;
- log use; and
- terminate delegation automatically.

A user should not be able to delegate approval to themselves through an alternate account or role.

## 25. Control emergency override

Emergency override may temporarily relax normal separation rules, but it should be exceptional.

The application should require:

- defined emergency conditions;
- named accountable operator;
- reason;
- approval before use where possible;
- limited scope;
- time limitation;
- enhanced logging;
- notification;
- post-use independent review;
- evidence preservation;
- correction of resulting records;
- credential or role reset; and
- documented risk acceptance where separation could not be maintained.

“Operational urgency” should not become a routine bypass.

## 26. Design for small teams

Small teams may not have enough people to maintain ideal static separation.

Proportionate alternatives may include:

- dynamic self-approval prevention;
- independent business-owner approval;
- peer review from another team;
- controlled deployment pipeline;
- immutable build artefacts;
- automated policy checks;
- enterprise change approval;
- post-action independent review;
- shorter privilege duration;
- enhanced monitoring;
- transaction limits;
- delayed release;
- periodic retrospective review; and
- rotation of duties.

The application should document why the arrangement provides reasonable independence and where residual risk remains.

## 27. Protect role and workflow configuration

The following are security-critical:

- incompatible-role definitions;
- workflow stages;
- approval thresholds;
- project and record ownership;
- delegation rules;
- emergency override;
- approval counts;
- role-to-function mappings;
- material-change definitions;
- service identity assignments;
- release gates; and
- audit-review permissions.

Changes should be:

- restricted;
- attributable;
- approved;
- tested;
- logged;
- reversible; and
- included within configuration and baseline control.

A user should not be able to weaken the separation rule and then use the newly combined privilege.

## 28. Fail safely

The application should deny or hold the action when:

- the originator cannot be identified;
- the reviewer identity is ambiguous;
- role information is missing;
- the workflow history is incomplete;
- delegation status cannot be validated;
- required approval is absent;
- the same identity performed conflicting stages;
- a service identity conflict is detected;
- policy evaluation fails;
- the audit record is unavailable; or
- the separation configuration is inconsistent.

The application should not default to approving the action because the policy service or workflow data is unavailable.

## 29. Log separation-of-duties activity

The application should generate events for:

- role-conflict detection;
- denied conflicting role assignment;
- denied self-approval;
- approval and release;
- delegation creation and use;
- emergency override;
- privilege assignment;
- workflow-rule change;
- incompatible-role exception;
- administrator self-assignment attempt;
- deployment approval and execution;
- database migration approval and execution;
- audit-configuration change;
- high-risk export approval;
- post-action review; and
- changes to separation policy.

Events should include:

- acting identity;
- affected identity or record;
- action;
- role;
- workflow stage;
- previous and new state;
- time;
- outcome;
- policy reason;
- approval or change reference; and
- application component.

## 30. Monitor for separation-of-duties anomalies

The application should support detection of:

- repeated self-approval attempts;
- role combinations approaching a prohibited conflict;
- temporary exceptions that do not expire;
- repeated emergency override;
- users approving each other’s transactions unusually often;
- administrator self-assignment;
- approval shortly after reassignment;
- broad delegation;
- approval using a shared or generic account;
- one service identity performing incompatible stages;
- privileged users modifying audit settings before sensitive activity;
- deployment outside the approved pipeline;
- direct production data changes; and
- conflicts created by nested group membership.

## 31. Test separation of duties

Testing should include:

- valid independent approval;
- denied self-approval;
- conflicting static role assignment;
- dynamic conflict on the same transaction;
- legitimate dual roles on different transactions;
- nested-group conflict;
- delegated approval;
- circular delegation;
- emergency override;
- expired exception;
- privileged self-assignment;
- direct API bypass;
- thick-client request manipulation;
- workflow replay;
- material amendment after approval;
- database migration separation;
- developer-to-production deployment controls;
- audit administration separation;
- service identity conflicts;
- failure of policy or workflow services; and
- event generation and alerting.

Testing should validate effective end-to-end behaviour, not merely that the user interface hides an approval button.

## 32. Review incompatible duties periodically

The application owner, business owners and security representatives should periodically review:

- sensitive processes;
- incompatible roles;
- current role assignments;
- effective access;
- project-specific conflicts;
- service identities;
- delegated authority;
- emergency access;
- temporary exceptions;
- workflow changes;
- product upgrades;
- supplier roles;
- development and deployment permissions;
- database privileges; and
- audit-administration access.

Reviews should also occur after incidents, audit findings, organisational change and material application change.

## 33. Remove obsolete duties and conflicts

When a workflow, role, feature, supplier or integration is retired, the application should:

- remove obsolete role definitions;
- remove workflow permissions;
- remove delegations;
- revoke service identities;
- update the conflict matrix;
- update tests;
- update monitoring;
- update the SSP and SyOps;
- remove associated exceptions; and
- verify that the obsolete path cannot still be used.

## 34. Manage separation-of-duties exceptions

Where the application or organisational structure cannot provide the intended separation, record:

- affected process;
- conflicting duties;
- identities or roles involved;
- required control;
- actual arrangement;
- business need;
- duration;
- risk;
- compensating controls;
- monitoring;
- independent review;
- owner;
- approval;
- remediation or organisational change plan; and
- review or expiry date.

Examples include:

- a commercial product with one administrator role;
- a small support team;
- an emergency migration;
- a supplier who both develops and deploys;
- inability to prevent self-approval technically;
- shared database administration;
- one service identity performing several workflow stages; or
- insufficient audit separation.

The exception should be visible in the application addendum or risk process, not buried in an operating instruction.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate identity, change control, source repositories, deployment pipelines, service management and central logging. They exclude enterprise IAM/PAM engineering, organisational restructuring and major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify sensitive business and technical processes** | Review application workflows, access administration, configuration, deployment, data movement, recovery and audit activities to find processes requiring independent involvement. | Summarise the scope in the **SSP AC-05 statement** and maintain detail in the existing **business-process design**, **threat/risk assessment**, **ConOps** or **SyOps**. | **6–12 hours** |
| **2. Define incompatible duties and roles** | Identify requester, author, reviewer, approver, fulfiller, releaser, deployer, administrator and auditor combinations that should not be held or exercised together. | Record the rules in the existing **role/access matrix**, **separation-of-duties matrix**, **business requirements**, **security design** or **SyOps**, referenced from the SSP. | **8–20 hours** |
| **3. Decide which conflicts require static or dynamic enforcement** | Prevent inherently conflicting role assignments and apply transaction-level rules where users may perform different duties on different records. | Capture the enforcement choice in the **security design**, **workflow specification**, **role matrix** and **SSP AC-05/AC-03 sections**. | **6–12 hours** |
| **4. Prevent self-approval and self-review** | Store originator and material-editor identity and deny approval, release or independent review by the same identity where required. | Record requirements in the **business-process specification**, **workflow design**, **SDLC backlog** and **SSP**. Retain evidence in the normal **functional/security test report**. | **12–32 hours** |
| **5. Check role conflicts during provisioning and change** | Evaluate direct, inherited, nested, temporary, project and privileged access before assigning a role or group membership. | Use the existing **IAM/access-request workflow**, **role matrix**, **AC-02 account process** and **access-review evidence**. | **8–24 hours** |
| **6. Separate access request, approval and fulfilment for higher-risk access** | Require independent approval before privileged or sensitive access is implemented and prevent self-granting. | Evidence remains in the normal **IAM**, **service-management**, **PAM** or **access-request records**, referenced from the **SSP** and **SyOps**. | **6–16 hours** |
| **7. Separate privileged administration, use and review** | Distinguish role assignment, privileged operation, audit administration and independent review and integrate with enterprise PAM where available. | Record the model in the **privileged-access design**, **role matrix**, **SyOps**, **support model** and **SSP AC-05/AC-06 sections**. | **8–24 hours** |
| **8. Separate development, approval and production deployment** | Use peer review, protected branches, controlled build artefacts, independent release approval and deployment through the approved pipeline. | Evidence sits in the normal **SDLC**, **source repository**, **pipeline history**, **change record**, **release approval** and **release evidence pack**. | **12–32 hours initially** |
| **9. Separate database migration and direct data-change duties** | Restrict migration development, production execution, validation and rollback authority and use separate runtime and migration identities. | Record the design in the **database design**, **deployment plan**, **role matrix**, **SyOps**, **change record** and **operational acceptance evidence**. | **8–24 hours** |
| **10. Protect and independently review security configuration changes** | Restrict changes to roles, identity trust, logging, exports, retention and other security settings and require an independent verification step. | Use the existing **CM-06 configuration record**, **change process**, **release checklist**, **security design** and **post-deployment verification**. | **6–16 hours** |
| **11. Control delegation and emergency override** | Require named delegator and delegate, defined scope and expiry, conflict checks, enhanced logging and post-use independent review. | Record arrangements in the **SyOps**, **workflow specification**, **incident-response annex**, **PAM record**, **SSP** and normal **access/change records**. | **8–20 hours** |
| **12. Apply proportionate separation to automated services** | Use distinct service identities, independent pipeline gates, signed approvals, validation jobs or human approval for incompatible automated stages. | Capture controls in the **service design**, **interface control documents**, **pipeline design**, **service-account register** and **SSP**. | **8–24 hours** |
| **13. Log and monitor conflicts, overrides and sensitive approvals** | Generate events for denied self-approval, role conflicts, delegation, emergency override, privileged assignment, release and policy change. | Define events in the **SSP AU-02/SI-04/AC-05 sections** and existing **event specification**. Verify through **SIEM onboarding** and the normal **security test report**. | **6–16 hours** |
| **14. Test static, dynamic and bypass scenarios** | Test role conflicts, self-approval, nested groups, delegation, direct APIs, workflow replay, service identities, deployment and failure conditions. | Add cases to the normal **security test plan**, **functional test plan**, **integration test**, **operational acceptance test** or **penetration test** and retain results in established reports. | **20–48 hours per major test cycle** |
| **15. Review effective duty combinations periodically** | Review current users, roles, project scope, privileged access, service identities, delegations, pipeline permissions and exceptions. | Retain outcomes in established **access reviews**, **service reviews**, **PAM reviews**, **SDLC governance reviews**, **risk records** or **application governance minutes**. | **8–20 hours per review** |
| **16. Document and manage unavoidable conflicts** | Record small-team limitations, coarse product roles, supplier constraints or emergency combinations with compensating controls and expiry. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP AC-05 statement**. | **4–10 hours per exception** |

### Indicative total

For a typical internal application with several approval workflows and a standard corporate SDLC, initial application effort is commonly around **110–260 hours**.

A small commercial application with no sensitive approval or deployment functionality may require less. A complex engineering, financial, records or safety-relevant application with many workflows, project segregation, privileged functions, supplier development and direct database activity may require substantially more.

The estimates should not be added mechanically where work overlaps. AC-05 activities commonly share requirements, implementation and evidence with AC-02, AC-03, AC-06, CM-03, CM-05, CM-06, SI-07, SA-11, AU-02, SI-04 and CA-07.

---

## Suggested document placement

To avoid creating disconnected evidence, separation-of-duties information should normally be distributed across established application and SDLC artefacts:

- **SSP:** AC-05 implementation approach, sensitive processes, static and dynamic separation, inherited enterprise controls, review arrangements and exceptions.
- **ConOps or SyOps:** operational duties, approval, administration, delegation, emergency override, support and recovery responsibilities.
- **Business-process design:** workflow stages, originator, reviewer, approver, releaser and exceptional paths.
- **Role/access matrix:** functions, project scope, privileged access, incompatible roles, owners and approvers.
- **Separation-of-duties matrix:** concise mapping of incompatible duties and enforcement method; this may be a tab within the existing role matrix rather than a separate document.
- **Security architecture and design:** trusted enforcement points, workflow state, service identities, privileged paths and audit separation.
- **IAM and access-request workflow:** conflict checks, independent approval, fulfilment and review.
- **Privileged-access design:** approval, assignment, use, monitoring and independent review.
- **SDLC and source-control configuration:** peer review, branch protection, build, artefact promotion and deployment separation.
- **Database design and release plan:** runtime, migration, execution, validation and rollback duties.
- **CM-06 configuration records:** workflow rules, role conflicts, approval thresholds, delegation and emergency override.
- **Service-account register and interface design:** automated duties, identities and independent validation.
- **AU-02 and SI-04 evidence:** conflicts, approvals, overrides, policy changes and privileged activity.
- **Test plans and reports:** static, dynamic, transaction, delegation, API, pipeline and failure-path tests.
- **Release and operational acceptance records:** confirmation that approved separation rules operate in the released version.
- **Access reviews and service reviews:** continuing review of effective duty combinations and exceptions.
- **Risk register or application addendum:** small-team constraints, supplier conflicts, coarse roles, emergency arrangements and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate separation-of-duties policy;
- organisational role and line-management structures;
- enterprise IAM and access-governance platforms;
- corporate privileged-access management;
- enterprise joiner–mover–leaver processes;
- organisation-wide change and release governance;
- enterprise source-code and pipeline platforms where centrally operated;
- infrastructure and operating-system administrative separation;
- enterprise database-platform administration;
- corporate procurement, finance and HR approval processes;
- central SIEM and SOC operations;
- enterprise incident investigation governance;
- corporate audit and assurance functions; and
- organisation-wide risk and exception approval.

The application team must still:

- identify the application-specific sensitive duties;
- define incompatible role and transaction combinations;
- implement static or dynamic enforcement;
- prevent self-approval and self-granting;
- separate privileged, SDLC, database and audit functions;
- control delegation and emergency override;
- log and test the rules;
- review effective access; and
- formally manage product and staffing limitations.

> **Key dividing line:** the enterprise defines organisation-wide governance and provides shared workflow, IAM, PAM and SDLC platforms; the application defines and enforces which application-specific duties must remain independent within its business and technical processes.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, AC-05 Separation of Duties.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, AC-05 assessment procedures.
3. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool Glossary — Separation of Duty**.
4. National Institute of Standards and Technology, **NIST SP 800-162, Guide to Attribute Based Access Control Definition and Considerations**.
5. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1**.
