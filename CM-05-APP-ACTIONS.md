# CM-05 Access Restrictions for Change — Application Actions

## Purpose

For an IT application, CM-05 means the application must ensure that **only authorised people, services and automated processes can make changes to application code, configuration, data structures, interfaces, deployment artefacts and other security-relevant components**.

This control is not only about approving a change. It is about restricting the technical ability to perform, promote, deploy, execute or conceal a change.

The enterprise may provide:

- corporate identity and multi-factor authentication;
- privileged-access management;
- source-code hosting;
- build and deployment platforms;
- change-management and service-management tooling;
- managed Microsoft Windows EUC devices;
- server, database and network administration;
- central logging and monitoring;
- secrets and certificate services; and
- organisation-wide change and release policy.

Those capabilities are inherited.

The application remains responsible for defining and enforcing who may change its:

- source code;
- commercial-product configuration;
- application security settings;
- role and permission models;
- deployment manifests;
- build and release pipelines;
- dependencies and plugins;
- database schemas and application-owned database objects;
- thick-client packages;
- API and integration configuration;
- workflows and business rules;
- logging and monitoring settings;
- scheduled jobs;
- reports and templates;
- application-controlled data corrections;
- scripts and automation;
- service identities; and
- application baseline and release records.

NIST CM-05 requires physical and logical access restrictions associated with changes to be defined, documented, approved and enforced. Its enhancements address automated enforcement and audit records, review of changes, signed components and controls over production and operational environments. NIST SP 800-128 places these restrictions within security-focused configuration management, while the NIST Secure Software Development Framework supports protecting code, build environments and software artefacts from unauthorised access and tampering.

> **Core principle:** approval to request a change is not the same as technical authority to implement it. Every change path should be restricted to the minimum authorised identities, environments, components and actions.

---

## 1. Identify all application change paths

The application should identify every method by which its behaviour, security or deployed state can be changed.

This normally includes:

- source-code commits and merges;
- repository administration;
- build-pipeline changes;
- dependency and package updates;
- artefact promotion;
- deployment;
- configuration files;
- configuration-as-code;
- infrastructure-as-code used specifically for the application;
- product administration consoles;
- feature flags;
- database migrations;
- stored procedures, triggers and application-owned database roles;
- direct production data fixes;
- thick-client packaging;
- software-distribution package updates;
- API client and integration settings;
- endpoint and destination allow-lists;
- identity-provider and federation configuration;
- role and permission definitions;
- workflow and approval rules;
- logging, alerting and monitoring configuration;
- scheduled jobs and batch definitions;
- report and export templates;
- plugins, extensions and scripts;
- certificates and secret references;
- recovery and rollback packages;
- supplier maintenance tools;
- emergency access;
- local files on application servers;
- thick-client local configuration; and
- manual commands or utilities used by support personnel.

A change path should not be omitted merely because it is informal, rarely used or labelled as support activity.

## 2. Define change roles and authorities

The application should define distinct roles for activities such as:

- change requester;
- developer or configurator;
- code reviewer;
- security reviewer;
- tester;
- build service;
- release approver;
- deployment operator;
- database migration operator;
- application administrator;
- configuration administrator;
- supplier support engineer;
- emergency-change approver;
- post-deployment verifier; and
- audit reviewer.

For each role, define:

- permitted repositories or components;
- permitted environments;
- allowed actions;
- privilege level;
- approval conditions;
- time restrictions;
- whether interactive access is permitted;
- whether production access is permitted;
- whether direct change is permitted;
- required authentication;
- monitoring; and
- review frequency.

The application should avoid broad roles such as “technical administrator” that can modify every layer without distinction.

## 3. Apply least privilege to change access

Change permissions should be limited to the minimum required.

Examples include:

- developers may change source code but not deploy directly to production;
- testers may view builds and record results but not alter approved artefacts;
- build services may compile and package but not approve release;
- deployment services may deploy only approved artefacts;
- application administrators may change defined product settings but not source code;
- database migration identities may alter approved schemas but not perform unrestricted database administration;
- support personnel may execute approved diagnostics but not modify production configuration;
- report designers may change approved templates but not application security settings;
- integration administrators may change defined endpoints but not user roles; and
- role administrators may assign approved roles but not redefine their permissions.

Permission should be scoped by component, environment and action.

## 4. Separate development, test and production change authority

The application should prevent development access from automatically becoming production change authority.

It should normally ensure that:

- development credentials are not accepted in production;
- developers do not have routine direct production write access;
- test environments cannot promote artefacts directly to production without approval;
- production deployment uses a controlled service or privileged role;
- production configuration repositories are separately protected;
- production secrets are inaccessible from development;
- lower-environment administrators cannot administer production;
- production database schema changes use approved migration paths; and
- emergency access is separately controlled.

Where a small team cannot achieve full personnel separation, automated gates, peer approval, immutable artefacts and independent post-deployment verification should provide compensating separation.

## 5. Restrict source-code changes

The application should protect source repositories through controls such as:

- named accounts;
- enterprise authentication;
- MFA where required;
- repository access based on role;
- protected branches;
- pull or merge requests;
- required peer review;
- prevention of direct changes to release branches;
- restricted force-push;
- restricted branch deletion;
- signed commits or tags where proportionate;
- protected repository settings;
- restricted administrator privileges;
- audit logging;
- archived access after team departure;
- control of automation tokens; and
- periodic access review.

The application should identify who can alter repository security settings, not only who can edit code.

## 6. Restrict build-pipeline changes

Build and deployment pipelines are security-critical because they can alter the resulting software without changing ordinary application source files.

The application should restrict changes to:

- pipeline definitions;
- build scripts;
- runner or agent configuration;
- build images;
- compiler and tool versions;
- package sources;
- environment variables;
- signing stages;
- security-testing stages;
- artefact destinations;
- deployment targets;
- approval gates;
- service connections;
- secrets references; and
- retention settings.

Pipeline-administration privileges should be tightly limited and separately reviewed.

A developer who can silently remove security tests or redirect artefacts can effectively bypass source-code controls.

## 7. Restrict build and deployment service identities

Automated identities used for build, packaging, signing and deployment should be:

- unique;
- non-interactive unless explicitly required;
- scoped to the required repository and environment;
- unable to approve their own output;
- unable to retrieve unnecessary secrets;
- restricted to approved artefact repositories;
- restricted to approved deployment targets;
- protected through enterprise secrets management;
- monitored;
- rotated or renewed;
- owned by a named team or individual; and
- removed when the pipeline is retired.

One highly privileged automation account should not be shared across unrelated applications and environments.

## 8. Protect artefact promotion

The application should ensure that only approved artefacts can move into staging or production.

Controls should include, where proportionate:

- immutable or write-protected artefacts;
- unique release identifiers;
- checksums;
- digital signatures;
- software bills of materials;
- release manifests;
- approved repository paths;
- promotion rather than manual rebuilding;
- restricted promotion permissions;
- approval gates;
- verification of test completion;
- vulnerability and policy checks;
- prevention of local file substitution;
- provenance records; and
- post-promotion integrity verification.

The artefact deployed to production should be the artefact that was reviewed and tested.

## 9. Restrict production deployment

Production deployment should occur only through an approved path.

The application should:

- use approved deployment services or named privileged operators;
- require an approved change or release reference;
- restrict production deployment credentials;
- prevent deployment from developer workstations;
- restrict deployment sources to approved artefact repositories;
- validate artefact identity and integrity;
- limit deployment to the approved application and environment;
- record the identity initiating and executing deployment;
- retain deployment output;
- support rollback;
- verify completion; and
- alert on deployment outside the approved process.

Direct copying of binaries or scripts into production should normally be prohibited.

## 10. Restrict application configuration changes

Security-relevant application settings should be changeable only by approved roles or deployment services.

This includes:

- authentication configuration;
- identity-provider trust;
- role and permission definitions;
- session settings;
- feature flags;
- logging settings;
- audit configuration;
- encryption and certificate settings;
- integration endpoints;
- destination allow-lists;
- file handling and upload settings;
- export settings;
- retention and deletion settings;
- privileged functions;
- support and impersonation settings;
- malware-scanning configuration; and
- emergency-access settings.

Where practical, configuration changes should be made through controlled configuration-as-code or repeatable deployment methods rather than ad hoc manual editing.

## 11. Protect configuration files and stores

The application should protect:

- configuration repositories;
- configuration databases;
- product settings;
- environment variables;
- registry values used by thick clients;
- application property files;
- feature-flag stores;
- policy files;
- deployment manifests;
- container definitions;
- scripts;
- certificate trust stores;
- secret references; and
- backup copies of configuration.

Controls should include:

- restrictive permissions;
- named administrative access;
- integrity protection;
- version history;
- secure storage;
- change logging;
- approval;
- backup;
- rollback; and
- prevention of ordinary-user modification.

A configuration file is not controlled merely because it is located on a production server.

## 12. Restrict database changes

The application should distinguish:

- normal runtime data access;
- schema migration;
- stored procedure change;
- reference-data administration;
- direct production data correction;
- database role change;
- performance configuration;
- audit configuration; and
- platform administration.

Application responsibilities should normally include:

- separate runtime and migration identities;
- approved migration scripts;
- restricted schema-change permission;
- controlled execution;
- validation;
- rollback;
- logging;
- prevention of developer direct write access;
- protection of application-owned roles and objects; and
- review of direct data fixes.

Enterprise database teams remain responsible for shared database-platform administration, but application teams remain responsible for their own schemas, roles, migrations and data-change methods.

## 13. Restrict direct production data changes

Direct correction of production data can bypass business rules, validation, audit trails and separation of duties.

The application should:

- prohibit routine direct editing;
- provide controlled business correction functions where practical;
- require an approved support or incident record;
- identify affected records and fields;
- require independent review for high-impact corrections;
- use a controlled script or transaction;
- preserve the previous value;
- record the operator;
- record the reason;
- validate the result;
- protect audit history;
- test the correction outside production where practicable; and
- remove temporary privilege immediately afterwards.

An administrator’s ability to access the database does not automatically authorise them to alter business records.

## 14. Restrict role and permission changes

Changes to the application’s access model should be tightly controlled.

The application should distinguish:

- assigning an existing role;
- changing role membership;
- creating a new role;
- changing role permissions;
- changing group-to-role mappings;
- changing project membership rules;
- changing separation-of-duties rules;
- enabling privileged functions;
- changing support impersonation;
- altering service scopes; and
- changing emergency access.

Redefining a role is usually higher risk than assigning an approved role and should require stronger review, testing and change control.

## 15. Restrict interface and integration changes

Only approved identities should be able to change:

- API clients;
- credentials;
- scopes;
- endpoints;
- callback URLs;
- message topics;
- queue permissions;
- file-transfer destinations;
- schedules;
- data mappings;
- transformation rules;
- retry behaviour;
- encryption settings;
- certificates;
- destination allow-lists; and
- production/non-production routing.

The application should prevent a user from redirecting data to an arbitrary internal or external destination.

## 16. Restrict scheduled jobs and automation changes

The application should control who may create, modify, enable, disable or manually execute:

- scheduled jobs;
- batch processes;
- data imports;
- data exports;
- maintenance jobs;
- reconciliation jobs;
- deletion jobs;
- retention jobs;
- report distribution;
- integration polling;
- synchronisation;
- backup integration;
- recovery automation; and
- monitoring checks.

Job definitions should be versioned where practical, and execution privileges should be separate from design privileges for high-impact jobs.

## 17. Restrict reports, templates and business-rule changes

Reports, templates, calculations and workflow rules can materially alter the information presented or decisions made.

The application should control changes to:

- report queries;
- report data sources;
- report fields;
- approval templates;
- document templates;
- calculation logic;
- scoring rules;
- workflow transitions;
- notification templates;
- export formats;
- data transformations;
- validation rules;
- reference data; and
- publication settings.

These changes should follow proportionate review and testing even where no executable code is modified.

## 18. Restrict thick-client package changes

Where the application includes a thick client, the application should control:

- source package;
- version;
- included binaries;
- libraries;
- configuration;
- endpoints;
- signing;
- installer actions;
- local services;
- drivers;
- prerequisites;
- update behaviour; and
- rollback.

Only approved package maintainers should create or modify the package, and only the approved software-distribution process should publish it to corporate EUC devices.

The application team owns the package content and approval; the enterprise owns the distribution platform and Windows endpoint controls.

## 19. Restrict plugin, script and extension changes

If the product supports plugins, macros, scripts or user extensions, the application should:

- disable them if not required;
- restrict authorship;
- require review;
- restrict installation;
- use approved repositories;
- scan and integrity-check packages;
- version extensions;
- restrict production editing;
- prohibit arbitrary operating-system command execution;
- restrict available APIs;
- log installation and execution changes;
- review obsolete extensions; and
- support rollback.

A product administrator should not automatically have unrestricted code-execution capability.

## 20. Restrict supplier changes

Supplier or vendor support should use the approved enterprise support and privileged-access path.

The application should:

- use named supplier identities;
- require a support case;
- define permitted components and actions;
- restrict duration;
- prohibit unapproved remote tools;
- control file transfer;
- review supplier scripts and packages;
- require approval before production change;
- monitor activity;
- record exact changes;
- require validation;
- remove access after use; and
- retain supplier advice and evidence.

“Vendor recommended” does not replace internal approval and control.

## 21. Restrict changes to logging and monitoring

Changes that reduce visibility are particularly sensitive.

The application should tightly restrict:

- disabling logging;
- changing event categories;
- changing log levels;
- changing log destinations;
- changing retention;
- changing parsing or forwarding;
- suppressing alerts;
- changing correlation identifiers;
- excluding components;
- modifying audit access;
- deleting local buffers; and
- disabling monitoring health checks.

Where practical, the person performing sensitive application administration should not be able to conceal it by changing logging.

## 22. Restrict changes to certificates, keys and secret references

The application should control who may:

- register or replace certificates;
- change trust anchors;
- update client secrets;
- change vault references;
- alter signing configuration;
- change encryption keys;
- change token issuers or audiences;
- revoke trust;
- alter certificate validation; and
- perform emergency rollover.

The actual secrets should remain in approved enterprise services. The application controls its configuration, references and authorised consumers.

## 23. Enforce separation of duties for change

Where proportionate, the application should separate:

- requester from approver;
- developer from reviewer;
- developer from production deployer;
- build administrator from release approver;
- migration author from production executor;
- security-setting changer from verifier;
- role-definition changer from role approver;
- data-fix author from data-fix verifier;
- supplier engineer from internal approver; and
- emergency-change implementer from post-change reviewer.

Small teams may use automated gates and independent post-change review where full personnel separation is not practical.

## 24. Protect emergency change access

Emergency change should be possible without becoming an uncontrolled bypass.

The application should define:

- qualifying emergency conditions;
- approving authority;
- named operator;
- permitted scope;
- temporary privilege;
- start and expiry;
- required evidence;
- logging;
- testing possible before execution;
- rollback;
- notification;
- post-change review;
- retrospective approval;
- baseline reconciliation; and
- removal of temporary access.

Emergency access should not become a standing production-administrator entitlement.

## 25. Use just-in-time and time-limited privilege where proportionate

For rare or high-risk change access, the application should use:

- temporary role assignment;
- PAM checkout;
- just-in-time privilege;
- approved maintenance windows;
- time-limited service tokens;
- expiring supplier access;
- task-specific database permissions;
- temporary feature-administration roles; and
- automatic removal after completion.

The application should record who approved the privilege, why it was needed, what it allowed and when it expired.

## 26. Prevent bypass through alternate paths

Restrictions should apply consistently across:

- source repository;
- product administration console;
- API;
- thick client;
- database;
- server file system;
- message broker;
- file share;
- batch interface;
- software-distribution package;
- deployment pipeline;
- recovery tools;
- support consoles;
- supplier utilities; and
- emergency access.

A change blocked in the user interface must not remain possible through a direct API or database update.

## 27. Prevent unauthorised local changes

Applications should not depend on untracked local edits to remain operational.

The application should:

- restrict server file-system write access;
- prevent changes from ordinary user accounts;
- prevent deployment from personal workspaces;
- control local administrator access;
- prevent thick-client users from changing security-relevant configuration;
- prevent local override files;
- monitor integrity of key files;
- make local settings read-only where practical;
- reconcile emergency edits into the approved repository; and
- rebuild from controlled sources rather than preserve undocumented local state.

## 28. Protect change-management configuration

The mechanisms controlling change are themselves security-critical.

The application should restrict changes to:

- branch protection;
- review requirements;
- pipeline approval gates;
- repository administrators;
- deployment roles;
- service connections;
- protected environments;
- artefact retention;
- signing stages;
- security-test requirements;
- emergency workflows;
- change templates;
- production target definitions; and
- audit settings.

A person able to remove the control gate may have greater practical authority than the person allowed to submit code.

## 29. Define pre-change verification

Before granting or using change access, the application should verify:

- approved request;
- correct person or service;
- correct role;
- correct environment;
- correct component;
- required training or competence;
- separation-of-duties conditions;
- maintenance window;
- backup or rollback readiness;
- current baseline;
- required test evidence;
- supplier authorisation;
- expiry of elevated access; and
- logging availability.

This may be enforced through pipeline gates, service-management workflow, PAM, release checks or controlled manual procedures.

## 30. Verify changes after implementation

After change, the application should confirm:

- only approved components changed;
- deployed version matches the approved artefact;
- configuration matches the approved value;
- database migration completed as intended;
- access controls remain effective;
- logging remains operational;
- integration destinations remain approved;
- no temporary accounts or privileges remain;
- no unexpected files, plugins or endpoints appeared;
- rollback remains possible;
- application health is acceptable; and
- the baseline and inventory are updated.

The person verifying a high-risk change should be independent where proportionate.

## 31. Log change-access activity

The application should generate or retain events for:

- repository permission changes;
- source commits and merges;
- branch-protection changes;
- pipeline changes;
- build and promotion;
- deployment;
- product-configuration changes;
- security-setting changes;
- role-definition changes;
- database migrations;
- direct production data changes;
- job and workflow changes;
- integration changes;
- logging changes;
- certificate and secret-reference changes;
- plugin installation;
- supplier changes;
- emergency access;
- failed change attempts;
- privilege elevation;
- rollback; and
- post-change verification.

Events should include:

- acting identity;
- service identity where applicable;
- target component;
- previous and new state where practical;
- environment;
- time;
- outcome;
- change or release reference;
- artefact or commit identifier;
- approval reference; and
- emergency or supplier status.

## 32. Protect change audit records

Change records and technical audit evidence should be protected from alteration by the same person making the change.

The application should:

- forward relevant events centrally;
- protect repository and pipeline audit logs;
- retain service-management references;
- prevent unauthorised deletion;
- preserve artefact and deployment histories;
- restrict audit administration;
- use immutable or append-only records where proportionate;
- retain emergency evidence;
- link changes to releases and baselines; and
- define retention.

NIST CM-05(1) specifically addresses automated enforcement and creation of audit records for change access restrictions.

## 33. Monitor for unauthorised or unusual change activity

The application should support detection of:

- production change outside an approved window;
- direct deployment from an unapproved source;
- repository administrator changes;
- branch-protection removal;
- security-test bypass;
- unsigned or unexpected artefact;
- direct database update;
- configuration drift;
- logging disabled before change;
- new plugin or script;
- changed integration destination;
- supplier activity outside an approved session;
- repeated failed change attempts;
- unexpected privilege elevation;
- local file replacement;
- production change with no change reference; and
- temporary access not removed.

## 34. Review change access periodically

The application should periodically review:

- repository access;
- repository administrators;
- pipeline administrators;
- build and deployment identities;
- production deployment roles;
- application administrators;
- database migration permissions;
- direct data-fix access;
- supplier access;
- role and workflow administrators;
- logging administrators;
- certificate and secret administrators;
- emergency access;
- local accounts;
- dormant change privileges; and
- permissions associated with retired components.

The review should assess effective access, including inherited groups and automation tokens.

## 35. Remove change access promptly

Change access should be removed when:

- a person leaves the team;
- a supplier engagement ends;
- a deployment is complete;
- an emergency change closes;
- a migration completes;
- a component is retired;
- a service account is replaced;
- a person changes role;
- support access expires;
- a certificate or token is compromised; or
- the access is no longer justified.

Cached credentials, active sessions and automation tokens should also be addressed.

## 36. Test access restrictions for change

Testing should include:

- authorised code commit;
- denied unauthorised commit;
- protected-branch enforcement;
- required peer review;
- denied direct production deployment;
- artefact promotion;
- pipeline-administrator restrictions;
- configuration change by authorised and unauthorised roles;
- direct database-change prevention;
- migration-role separation;
- role-definition change;
- supplier access;
- thick-client package publication;
- emergency privilege expiry;
- logging-change restrictions;
- attempts through APIs and alternate interfaces;
- failed identity or policy service;
- audit-event generation;
- post-change verification; and
- removal of temporary access.

Testing should validate the actual technical restriction, not merely the existence of a change policy.

## 37. Review restrictions after material change

The application should reassess change access after:

- new repository;
- new build pipeline;
- new deployment platform;
- product upgrade;
- new administrative console;
- new database;
- new integration;
- new thick client;
- supplier change;
- new automation;
- cloud or platform migration;
- identity-provider change;
- incident;
- audit finding;
- penetration-test finding; or
- material change to enterprise SDLC or privileged-access tooling.

## 38. Manage unavoidable change-access exceptions

Where a commercial, legacy or supplier-controlled application cannot enforce the expected restrictions, record:

- affected change path;
- required restriction;
- actual capability;
- identities with access;
- affected environments and components;
- business need;
- risk;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, isolation, upgrade or replacement plan; and
- review or expiry date.

Examples include:

- one unrestricted product-administrator role;
- direct production configuration editing;
- no attributable supplier administration;
- inability to separate migration and runtime access;
- editable local thick-client configuration;
- no immutable artefact repository;
- missing audit records;
- shared deployment credential;
- inability to restrict plugin installation; or
- emergency changes that cannot be pre-approved.

The exception should be recorded in the application addendum or risk process, not only in a change ticket.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate source control, identity, PAM, change management, build pipelines, artefact repositories and central logging. They exclude enterprise platform engineering, product redevelopment and implementation of the underlying enterprise tools.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify all application change paths** | Review source, pipelines, configuration, database, thick-client packages, integrations, jobs, reports, plugins, security settings and support methods. | Summarise the scope in the **SSP CM-05 statement** and maintain detail in the existing **security architecture**, **CM-02 baseline**, **CM-08 inventory**, **ConOps** or **SyOps**. | **6–12 hours** |
| **2. Define change roles, permissions and environment scope** | Define who may request, develop, review, build, approve, deploy, configure, migrate, support and verify changes and where each role may act. | Record the model in the existing **RACI**, **role/access matrix**, **SDLC**, **SyOps**, **support model** and **SSP**. | **8–20 hours** |
| **3. Restrict source-code and repository administration** | Use named accounts, protected branches, peer review, restricted repository administration and audited changes. | Evidence remains in the normal **repository permissions**, **branch rules**, **merge history**, **access reviews** and **SDLC documentation**, referenced from the SSP. | **8–20 hours** |
| **4. Restrict build, pipeline and artefact administration** | Limit who can alter pipeline definitions, security gates, package sources, signing, service connections and artefact promotion. | Record controls in the **pipeline design**, **repository settings**, **release process**, **service-account register** and **SSP**. Retain evidence in normal **pipeline audit history**. | **12–28 hours** |
| **5. Restrict production deployment to approved artefacts and identities** | Deploy only from the approved artefact repository through controlled services or named privileged operators with an approved release reference. | Evidence sits in the **release record**, **deployment history**, **artefact manifest**, **change ticket**, **PAM record** and **operational acceptance evidence**. | **12–32 hours** |
| **6. Restrict security-relevant application configuration changes** | Limit changes to identity trust, roles, sessions, logging, integrations, exports, encryption, retention and other security settings to approved roles or deployment services. | Record approved access in the **CM-06 configuration specification**, **role matrix**, **security design**, **SyOps** and **SSP CM-05/CM-06 sections**. | **8–24 hours** |
| **7. Restrict database migrations and direct data fixes** | Separate runtime and migration identities, use approved scripts, prohibit routine direct edits and independently verify high-impact corrections. | Capture controls in the **database design**, **deployment plan**, **change process**, **SyOps**, **role matrix** and **migration/data-fix records**. | **12–32 hours** |
| **8. Restrict integration, job, report and workflow changes** | Control who may alter endpoints, clients, schedules, data mappings, report queries, templates, calculations and approval rules. | Use the existing **interface control documents**, **batch design**, **report specification**, **workflow design**, **CM-06 settings** and **change records**. | **8–24 hours** |
| **9. Restrict thick-client, plugin and extension changes** | Limit package or extension creation and publication, verify integrity and distribute only through approved repositories and corporate software management. | Evidence sits in the **packaging specification**, **release manifest**, **artefact repository**, **software-distribution package record** and **installation test report**. | **8–20 hours** |
| **10. Control supplier and emergency change access** | Require named identities, approved purpose, minimum scope, time limitation, monitoring, post-change review and prompt removal. | Record arrangements in the **SyOps**, **supplier record**, **incident/change procedure**, **PAM record**, **SSP** and normal **support/change tickets**. | **8–20 hours** |
| **11. Protect change-control mechanisms themselves** | Restrict changes to branch rules, approval gates, repository administrators, deployment roles, protected environments and audit settings. | Describe controls in the **SDLC**, **pipeline/repository configuration**, **privileged-access design**, **SSP** and normal **platform audit records**. | **6–16 hours** |
| **12. Log and monitor application change activity** | Record commits, merges, pipeline changes, promotions, deployments, configuration changes, migrations, data fixes, supplier actions and emergency access. | Define evidence in the **SSP AU-02/SI-04/CM-05 sections** and existing **logging specification**. Verify through **SIEM onboarding**, repository history and **security test reports**. | **6–16 hours** |
| **13. Verify the deployed state after change** | Confirm approved artefact, version, configuration, schema, access controls, logging, integrations and removal of temporary access. | Add verification to the normal **deployment plan**, **release checklist**, **operational acceptance test**, **post-implementation review** and **CM-02 baseline update**. | **4–12 hours per release** |
| **14. Review effective change access periodically** | Review repositories, pipelines, deployment identities, administrators, migration roles, supplier access, local accounts and automation tokens. | Retain outcomes in existing **access reviews**, **PAM reviews**, **service reviews**, **SDLC governance reviews** or **risk records**. | **8–20 hours per review** |
| **15. Test authorised, denied and bypass change paths** | Test branch protection, direct deployment, pipeline administration, database changes, configuration changes, alternate interfaces, emergency expiry and audit generation. | Add cases to the normal **security test plan**, **operational acceptance test**, **pipeline test**, **penetration test** or **control assessment report**. | **16–40 hours per major test cycle** |
| **16. Document and manage change-access limitations** | Record broad product-admin roles, shared deployment credentials, direct production edits, missing audit or supplier constraints with compensating controls. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP CM-05 statement**. | **4–10 hours per exception** |

### Indicative total

For a typical internal application using established corporate repositories and deployment pipelines, initial application effort is commonly around **120–280 hours**.

A small commercial application with vendor-managed releases and few local configuration options may require less. A legacy application with direct server changes, manual database fixes, thick-client packaging, supplier access or no mature pipeline may require substantially more.

The estimates should not be added mechanically where activities overlap. CM-05 commonly shares analysis, implementation and evidence with CM-02, CM-03, CM-06, CM-08, AC-05, AC-06, SI-07, SA-11, AU-02 and CA-07.

---

## Suggested document placement

To avoid creating disconnected evidence, change-access information should normally be distributed across established application and SDLC artefacts:

- **SSP:** CM-05 implementation approach, application change paths, inherited enterprise services, role restrictions, monitoring, review and exceptions.
- **ConOps or SyOps:** operational administration, support access, emergency change, supplier activity, rollback and verification responsibilities.
- **Security and solution architecture:** repositories, pipelines, artefact flows, deployment paths, administrative interfaces and privileged trust boundaries.
- **CM-02 baseline:** approved release components, artefacts and configuration used to verify changes.
- **CM-06 configuration specification:** authoritative security settings and authorised methods for changing them.
- **CM-08 inventory:** components, tools, repositories, integrations, plugins and service identities within change scope.
- **Role/access matrix and RACI:** requesters, developers, reviewers, approvers, deployers, administrators and verifiers.
- **SDLC:** source control, peer review, build, testing, artefact promotion, deployment and emergency-change requirements.
- **Repository and pipeline configuration:** protected branches, administrator roles, approval gates, service connections and audit settings.
- **Artefact repository and release manifest:** approved packages, integrity information, provenance and promotion history.
- **Database design and migration plan:** runtime, migration and data-fix roles and execution methods.
- **Interface control documents:** endpoint, client, scope and data-mapping change authority.
- **Thick-client packaging records:** package build, signing, publication and rollback.
- **IAM and PAM records:** privileged and time-limited change access.
- **Change and release records:** business approval, security impact, implementation, rollback and verification.
- **AU-02 and SI-04 evidence:** technical change events, alerts and monitoring health.
- **Test plans and reports:** authorised, denied, bypass, emergency and audit tests.
- **Operational acceptance and post-implementation review:** deployed-state verification and temporary-access removal.
- **Access reviews and service reviews:** continuing review of change privileges and automation tokens.
- **Risk register or application addendum:** broad roles, manual changes, supplier limitations, weak audit and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate change and release policy;
- enterprise service-management tooling;
- enterprise identity and MFA;
- corporate privileged-access management platform;
- centrally operated source-control and pipeline platforms;
- enterprise artefact repositories where provided;
- server and operating-system administrative controls;
- shared database-platform administration;
- network-device and firewall change controls;
- hypervisor and virtualisation change controls;
- enterprise secrets and certificate platforms;
- Microsoft Windows EUC administration;
- corporate software-distribution infrastructure;
- organisation-wide logging, SIEM and SOC operations;
- enterprise supplier-access governance;
- corporate emergency-change governance; and
- organisation-wide risk and exception approval.

The application team must still:

- identify every application-specific change path;
- define who may change each component and environment;
- configure repository, pipeline, deployment and product restrictions;
- control application database and data changes;
- restrict supplier, emergency and local changes;
- protect change-control mechanisms;
- log and test change access;
- verify deployed state; and
- formally manage application-specific limitations.

> **Key dividing line:** the enterprise provides the shared change-control platforms and infrastructure administration; the application restricts and verifies who can alter the application’s code, configuration, data structures, packages, interfaces and business behaviour.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, CM-05 Access Restrictions for Change.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, CM-05 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems**.
4. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1**.
5. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool — Configuration Management terminology**.
