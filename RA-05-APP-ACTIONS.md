# RA-05 Vulnerability Monitoring and Scanning — Application Actions

## Purpose

For an IT application, RA-05 means the application must maintain an accurate and continuing understanding of vulnerabilities affecting the application, assess their relevance and risk, ensure that remediation or other treatment is completed, and verify that identified weaknesses are no longer present.

This is broader than running an infrastructure scanner.

The enterprise may provide:

- network and infrastructure vulnerability scanners;
- endpoint and server scanning agents;
- vulnerability-management platforms;
- threat intelligence;
- enterprise patch-management services;
- operating-system and shared-platform remediation;
- central risk and reporting standards;
- penetration-testing services;
- SIEM and SOC monitoring; and
- organisation-wide remediation timeframes.

Those capabilities are inherited.

The application remains responsible for the vulnerabilities created by, contained within or exposed through its own:

- custom source code;
- commercial application products;
- application versions and patches;
- third-party libraries and dependencies;
- thick-client packages;
- APIs and interfaces;
- database schemas and application-owned database logic;
- plugins, extensions and scripts;
- containers and application images;
- configuration;
- authentication and access-control implementation;
- file-processing functions;
- business workflows;
- build and deployment artefacts;
- supplier components;
- unsupported features; and
- application-specific attack paths.

NIST RA-05 requires organisations to monitor and scan for vulnerabilities at defined frequencies and when new vulnerabilities are identified, use appropriate scanning techniques, analyse results, remediate legitimate vulnerabilities, share relevant information and update the vulnerabilities being scanned. NIST SP 800-40 Rev. 4 treats patching as preventive maintenance and stresses risk-based planning rather than ad hoc reaction. NIST SP 800-218 integrates vulnerability identification and remediation into the software development lifecycle.

> **Core principle:** the enterprise supplies common scanning and vulnerability-management capabilities; the application team ensures that the complete application is in scope, interprets findings in business context, treats application-owned weaknesses and proves that remediation is effective.

---

## 1. Define the application vulnerability scope

The application should identify everything that must be considered for vulnerability monitoring.

This normally includes:

- custom code;
- commercial off-the-shelf software;
- thick-client packages;
- web applications;
- application services;
- APIs;
- database schemas and stored logic;
- runtime frameworks;
- third-party libraries;
- open-source packages;
- package lock files;
- plugins and extensions;
- scripts and macros;
- report engines;
- file parsers and converters;
- containers and images;
- application-specific middleware;
- scheduled jobs;
- integration adapters;
- build dependencies;
- deployment artefacts;
- application configuration;
- service identities;
- exposed endpoints;
- supplier-delivered components; and
- retired but still deployed versions.

The scope should align with the:

- CM-02 baseline;
- CM-08 component inventory;
- architecture;
- interface inventory;
- release manifest;
- software bill of materials;
- deployment records; and
- actual production state.

A scanner cannot assess components that the application has failed to identify.

## 2. Maintain an authoritative component and dependency inventory

The application should maintain enough information to determine whether a newly disclosed vulnerability applies.

For each material component, record:

- component name;
- supplier or origin;
- version;
- package identifier;
- environment;
- deployment location or service;
- application function;
- dependency relationship;
- support status;
- end-of-life date where known;
- owner;
- update method;
- supplier advisory source;
- software bill of materials reference;
- current approved baseline; and
- retirement status.

The application should be able to answer:

> “Where is this product, package or vulnerable version used?”

without relying on an informal search through developer workstations.

## 3. Define vulnerability-monitoring sources

Application vulnerability monitoring should use several sources because no single scanner finds every weakness.

Sources may include:

- enterprise infrastructure scans;
- web application scans;
- API security tests;
- static application security testing;
- dynamic application security testing;
- interactive application security testing;
- software-composition analysis;
- container or image scans;
- source-code review;
- secret scanning;
- dependency advisories;
- supplier security notices;
- national vulnerability databases;
- vendor support portals;
- penetration tests;
- configuration assessments;
- code-quality or compiler security checks;
- bug bounty or responsible-disclosure reports where applicable;
- incident findings;
- threat intelligence;
- internal defect reports;
- architecture review;
- security testing; and
- manual business-logic testing.

The application should define which source covers each component and weakness class.

## 4. Establish a vulnerability-monitoring plan

The application should define:

- components and interfaces in scope;
- scanning or assessment method;
- frequency;
- trigger events;
- authenticated or unauthenticated approach;
- environments;
- scan credentials;
- safety constraints;
- excluded functions;
- ownership;
- evidence source;
- triage process;
- severity method;
- remediation targets;
- exception process;
- retest method;
- reporting; and
- review frequency.

This does not need to be a separate document. It can be incorporated into:

- the SSP RA-05 section;
- the security testing strategy;
- the SyOps;
- the SDLC;
- the vulnerability-management plan;
- the continuous-monitoring plan; or
- the application assurance schedule.

## 5. Use risk-based scanning frequencies

The application should set frequencies based on:

- information sensitivity;
- business impact;
- application exposure;
- privilege;
- change rate;
- component volatility;
- supplier dependency;
- history of vulnerabilities;
- ease of automation;
- attack surface;
- active exploitation;
- enterprise policy; and
- regulatory or contractual requirements.

Examples of proportionate frequencies include:

- source and dependency scanning on every material build or merge;
- artefact and container scanning before release;
- authenticated application scanning at defined intervals;
- targeted scanning after major change;
- supplier-advisory review weekly or monthly;
- external or internal attack-surface review periodically;
- penetration testing annually or after material architectural change;
- daily or continuous monitoring of critical dependency advisories;
- immediate assessment when a critical actively exploited vulnerability is announced; and
- periodic review of unsupported or end-of-life components.

The actual frequency should follow corporate requirements where they are more prescriptive.

## 6. Trigger scanning and assessment after material events

The application should not depend only on a calendar.

Additional scans or assessments should occur after:

- major release;
- new API;
- new integration;
- new file type;
- new authentication mechanism;
- privileged-function change;
- application or framework upgrade;
- dependency update;
- container-image change;
- database migration;
- new plugin;
- architecture change;
- supplier patch;
- migration;
- significant configuration change;
- exposure change;
- penetration-test finding;
- incident;
- new vulnerability affecting a known component;
- active exploitation notice;
- new attack technique relevant to the application; and
- restoration from backup or rebuild where the state may have changed.

## 7. Use authenticated scanning where appropriate

Authenticated scanning can identify vulnerabilities and configuration weaknesses that unauthenticated scans cannot see.

The application should:

- identify which scanners require credentials;
- use dedicated scan identities;
- grant the minimum permissions needed;
- separate production and non-production credentials;
- protect credentials through approved secrets services;
- restrict interactive use;
- monitor scan-account activity;
- test that the account cannot alter data;
- rotate or revoke credentials;
- document limitations;
- avoid shared administrator credentials; and
- ensure scanner activity can be distinguished from user or attacker activity.

Where authenticated scanning is unsafe or unsupported, the application should use alternative methods and document the resulting coverage gap.

## 8. Scan application code

For internally developed or materially customised code, the application should use proportionate code-focused vulnerability detection.

This may include:

- static application security testing;
- code review;
- secure compiler settings;
- secret scanning;
- dependency analysis;
- insecure API-use detection;
- data-flow analysis;
- infrastructure-as-code scanning;
- configuration-as-code scanning;
- template scanning;
- mobile or thick-client binary analysis; and
- manual review of sensitive logic.

The application should focus on vulnerabilities such as:

- injection;
- broken access control;
- authentication bypass;
- insecure deserialisation;
- path traversal;
- unsafe file handling;
- command execution;
- server-side request forgery;
- cross-site scripting;
- cross-site request forgery;
- cryptographic misuse;
- sensitive-data exposure;
- race conditions;
- insecure temporary files;
- hard-coded secrets;
- excessive privilege;
- unsafe error handling; and
- business-logic flaws.

Automated results should be reviewed by someone who understands the application.

## 9. Scan third-party dependencies

The application should identify vulnerabilities in:

- direct dependencies;
- transitive dependencies;
- runtime frameworks;
- package-manager components;
- plugins;
- client libraries;
- database drivers;
- cryptographic libraries;
- report engines;
- parser libraries;
- build tools;
- test dependencies that enter production artefacts; and
- supplier-bundled components.

Controls should include, where proportionate:

- software-composition analysis;
- package lock files;
- approved repositories;
- dependency pinning;
- SBOM generation;
- licence and support review;
- detection of abandoned packages;
- monitoring supplier advisories;
- update testing;
- prevention of dependency confusion;
- integrity verification; and
- removal of unused dependencies.

A vulnerability may exist in a transitive package even when the application team did not select it directly.

## 10. Scan commercial and supplier products

For commercial products, the application should:

- identify exact product and module versions;
- subscribe to supplier security advisories;
- review release notes;
- assess applicability;
- obtain patches or mitigations;
- confirm supplier support status;
- review bundled third-party components;
- scan the deployed application where permitted;
- test supplier fixes;
- record supplier case references;
- track supplier remediation commitments;
- assess compensating controls; and
- plan upgrade or replacement where support is inadequate.

A supplier statement that “no action is required” should be assessed against the actual modules, configuration and exposure used by the application.

## 11. Scan thick-client packages

For a thick client installed on corporate Windows EUC devices, the application should assess:

- installer package;
- included binaries;
- libraries;
- embedded runtime;
- updater;
- local services;
- drivers;
- local storage;
- configuration files;
- protocol handlers;
- URL handlers;
- file associations;
- package signing;
- update source;
- server trust validation;
- local privilege requirements;
- bundled plugins; and
- obsolete versions.

The enterprise may scan the endpoint estate, but the application team owns the approved package composition, vulnerability interpretation and update decision.

## 12. Scan web interfaces

Web application scanning should cover more than the landing page.

The application should include:

- authenticated user paths;
- different business roles;
- administrative interfaces;
- APIs used by the browser;
- file upload;
- report generation;
- search;
- export;
- error handling;
- session management;
- workflow transitions;
- project or record boundaries;
- alternate routes;
- legacy endpoints;
- deep links; and
- security headers and protocol behaviour.

Scanner configuration should avoid unsafe actions in production and use suitable test data and accounts.

## 13. Scan APIs

API assessment should include:

- authentication;
- token validation;
- authorisation;
- object-level access;
- function-level access;
- mass assignment;
- schema validation;
- injection;
- rate limits;
- pagination;
- bulk extraction;
- file upload;
- callback and webhook handling;
- server-side request forgery;
- replay;
- error disclosure;
- deprecated versions;
- undocumented routes;
- service identities;
- request-size limits; and
- business-logic abuse.

API definitions and client identities should be supplied to the assessment team so that meaningful authenticated testing is possible.

## 14. Assess database and application-owned data logic

Application vulnerability assessment should cover:

- application-owned schemas;
- stored procedures;
- functions;
- triggers;
- views;
- database roles;
- dynamic SQL;
- database credentials;
- migration scripts;
- direct data-fix methods;
- data validation;
- audit logic; and
- access paths.

Enterprise teams remain responsible for database-platform vulnerabilities, while the application remains responsible for vulnerabilities in its schema, logic, roles and use of the platform.

## 15. Assess configuration vulnerabilities

Many application vulnerabilities arise from configuration rather than code.

The application should assess:

- default accounts;
- debug mode;
- sample modules;
- unused features;
- permissive roles;
- anonymous access;
- session settings;
- weak protocol options;
- insecure headers;
- excessive error detail;
- logging disabled;
- broad file types;
- unrestricted export;
- weak certificate validation;
- unapproved endpoints;
- obsolete API versions;
- excessive service permissions;
- unsafe temporary storage;
- unrestricted plugins;
- insecure callback settings; and
- production/non-production crossover.

This should align with CM-06 and CM-07.

## 16. Assess business-logic vulnerabilities

Automated scanners are often weak at detecting business-logic flaws.

The application should use manual or scenario-based testing for risks such as:

- self-approval;
- workflow bypass;
- project-boundary bypass;
- unauthorised record reassignment;
- bulk export abuse;
- approval replay;
- negative or excessive quantities;
- duplicate processing;
- race conditions;
- inconsistent state transitions;
- support impersonation misuse;
- bypass of separation of duties;
- unauthorised release;
- incorrect retention;
- privilege accumulation; and
- exploitation of trusted integrations.

Threat modelling, misuse cases and penetration testing should inform these scenarios.

## 17. Assess vulnerabilities in file-processing paths

Applications that accept or produce files should assess:

- file-type validation;
- parser vulnerabilities;
- archive expansion;
- macro and active content;
- path traversal;
- malicious filenames;
- content sniffing;
- temporary file handling;
- file preview;
- conversion services;
- malware-scanner bypass;
- generated spreadsheet formula injection;
- embedded object handling;
- resource exhaustion; and
- storage outside executable paths.

## 18. Assess build and software-supply-chain vulnerabilities

The application should monitor vulnerabilities and weaknesses in:

- source repositories;
- build tools;
- CI/CD plugins;
- build images;
- runners;
- package sources;
- artefact repositories;
- signing tools;
- deployment scripts;
- infrastructure-as-code;
- automation tokens;
- supplier packages;
- release provenance; and
- SBOM generation.

The application should distinguish vulnerabilities in the product from vulnerabilities in the process used to produce it.

## 19. Validate scanner safety and authorisation

Before scanning, the application should define:

- approved target;
- environment;
- date and time;
- source addresses;
- scanner identity;
- permitted techniques;
- prohibited destructive tests;
- rate limits;
- data-handling requirements;
- support contacts;
- monitoring suppression or tuning;
- rollback;
- stop conditions;
- incident escalation; and
- approval.

Production scanning should be carefully configured to avoid:

- data corruption;
- unintended workflow execution;
- account lockout;
- bulk email or notification;
- resource exhaustion;
- creation of records;
- triggering financial or safety actions;
- destructive API calls; and
- exposure of restricted information.

## 20. Ensure full coverage

The application should verify that scanning includes:

- all production nodes;
- all application tiers;
- active and standby instances;
- thick-client packages;
- current and supported versions;
- APIs;
- administrative interfaces;
- lower environments where security testing occurs;
- externally supplied modules;
- dependencies;
- database schema;
- scheduled jobs;
- integrations;
- recovery components; and
- newly deployed components.

Coverage should be reconciled with CM-08 and deployment records.

A successful scan of one web server does not prove coverage of the complete application.

## 21. Track scan limitations and blind spots

The application should document where tools cannot assess:

- proprietary protocols;
- thick-client logic;
- encrypted content;
- supplier appliances;
- business workflows;
- privileged functions;
- asynchronous processing;
- message queues;
- offline processing;
- database stored logic;
- unsupported technologies;
- isolated components;
- high-risk production functions; or
- third-party hosted support components.

Alternative assurance methods should be defined, such as:

- manual review;
- code review;
- configuration review;
- supplier evidence;
- targeted testing;
- penetration testing;
- architecture analysis;
- runtime monitoring; or
- compensating controls.

## 22. Triage findings

Every reported vulnerability should be triaged to determine:

- whether it is a true positive;
- affected component;
- affected version;
- affected environment;
- exploitability;
- required access;
- reachable attack path;
- information and business impact;
- privilege implications;
- known exploitation;
- available patch or mitigation;
- compensating controls;
- affected users or records;
- supplier position;
- urgency; and
- owner.

Triage should not dismiss a finding solely because:

- the application is internal;
- VPN is required;
- users have corporate accounts;
- exploitation is technically complex;
- no public exploit is known;
- a firewall blocks one path;
- the vulnerable code is rarely used; or
- the supplier rates it lower.

These factors may affect risk, but they do not make the vulnerability disappear.

## 23. Use application-specific risk prioritisation

Enterprise severity is an important starting point, but the application should apply context.

Risk prioritisation should consider:

- vulnerability severity;
- exploitability;
- active exploitation;
- attack complexity;
- required privilege;
- user interaction;
- application exposure;
- information sensitivity;
- business impact;
- safety or engineering consequences;
- number of affected components;
- availability of exploit code;
- compensating controls;
- detection capability;
- supplier support;
- remediation complexity;
- recovery implications; and
- residual risk.

A medium-rated vulnerability in a privileged approval function may be more important than a high-rated issue in an unreachable optional component.

## 24. Consolidate duplicate findings

The same underlying weakness may be reported by:

- network scanning;
- web scanning;
- code scanning;
- dependency scanning;
- penetration testing;
- supplier advisory;
- incident review; and
- manual assessment.

The application should link or consolidate related findings while preserving:

- each evidence source;
- affected components;
- occurrence count;
- remediation status;
- retest requirements; and
- closure evidence.

Duplicate consolidation should not hide the breadth of exposure.

## 25. Assign ownership and remediation targets

Each legitimate finding should have:

- unique identifier;
- affected component;
- description;
- risk rating;
- owner;
- treatment decision;
- target date;
- planned release;
- interim controls;
- dependency;
- supplier case where relevant;
- test requirement;
- status;
- evidence; and
- escalation route.

Ownership should be assigned to a named team or role capable of completing the action.

## 26. Remediate application-owned vulnerabilities

Remediation may include:

- source-code correction;
- dependency update;
- commercial-product patch;
- configuration change;
- disabling a vulnerable feature;
- restricting an interface;
- removing a plugin;
- changing privileges;
- modifying workflow;
- input validation;
- architecture change;
- stronger isolation;
- package replacement;
- certificate or secret rotation;
- increased logging;
- rate limiting;
- migration;
- upgrade;
- supplier fix; or
- retirement.

Remediation should follow controlled SDLC and change processes.

## 27. Use compensating controls where immediate remediation is not possible

Where a fix cannot be deployed within the target timeframe, the application should consider temporary controls such as:

- disable the function;
- restrict access;
- restrict source or destination;
- remove an integration;
- block a file type;
- reduce privilege;
- enforce read-only operation;
- increase monitoring;
- add detection;
- require additional approval;
- limit transaction volume;
- isolate the component;
- remove external or supplier access;
- shorten session duration;
- revoke credentials;
- apply a virtual patch;
- apply a vendor workaround; or
- take the component out of service.

The control should be documented, tested, monitored and assigned an expiry or review date.

## 28. Manage vulnerability exceptions

Where remediation is deferred or risk is accepted, record:

- vulnerability;
- affected components;
- current version;
- exploitability;
- business impact;
- enterprise and application risk rating;
- reason for delay;
- compensating controls;
- monitoring;
- owner;
- approving authority;
- supplier dependency;
- target remediation;
- review date;
- expiry date; and
- conditions that would require immediate reconsideration.

An exception should not be indefinite or renewed automatically without review.

## 29. Verify remediation through retesting

A finding should not be closed solely because:

- a patch was installed;
- code was changed;
- a ticket was marked complete;
- the supplier said it was fixed;
- a new version was deployed; or
- the vulnerable function was believed to be unused.

The application should verify:

- the correct component was changed;
- the deployed environment contains the change;
- the original test no longer succeeds;
- the vulnerable version is absent;
- configuration is correct;
- no alternate path remains;
- no regression was introduced;
- compensating controls are still needed or can be removed;
- baseline and inventory are updated; and
- evidence is retained.

## 30. Verify patch and update deployment coverage

Where a patch or update applies to several instances, the application should confirm coverage across:

- all production nodes;
- standby nodes;
- thick clients;
- database schema versions;
- container images;
- scheduled jobs;
- integration components;
- test and staging environments;
- recovery images;
- supplier-maintained instances; and
- disconnected or infrequently used components.

Partial deployment should remain an open finding until resolved or formally accepted.

## 31. Address unsupported and end-of-life components

The application should monitor and act on:

- end-of-support products;
- unsupported operating modes;
- abandoned libraries;
- obsolete frameworks;
- unmaintained plugins;
- old thick-client versions;
- unsupported database drivers;
- retired APIs;
- supplier products with no security fixes;
- obsolete build tools; and
- components that cannot be scanned.

Treatment may include:

- upgrade;
- replacement;
- isolation;
- feature removal;
- restricted use;
- increased monitoring;
- supplier agreement;
- accelerated retirement; or
- formal risk acceptance.

Unsupported status should be treated as an active security risk, not merely an asset-management issue.

## 32. Monitor new vulnerability intelligence

The application should maintain awareness of new vulnerabilities affecting its components through:

- supplier notifications;
- enterprise threat intelligence;
- dependency-alerting services;
- vulnerability databases;
- national advisories;
- sector alerts;
- software repository alerts;
- security mailing lists;
- incident information;
- researcher disclosure; and
- internal security teams.

The application should be able to rapidly determine applicability using its component inventory and SBOM.

## 33. Respond to actively exploited vulnerabilities

When exploitation is active or imminent, the application should use an accelerated process.

This may include:

- immediate applicability assessment;
- emergency scan;
- feature restriction;
- credential rotation;
- increased logging;
- targeted threat hunting;
- emergency patching;
- interface isolation;
- user communication;
- supplier escalation;
- incident-response activation;
- expedited testing;
- emergency change; and
- post-action verification.

The application should not wait for the next routine scan cycle.

## 34. Share relevant vulnerability information

The application should provide relevant information to:

- enterprise vulnerability management;
- system owner;
- information owner;
- security operations;
- incident response;
- patch management;
- risk governance;
- connected-system owners;
- supplier management; and
- other application teams using the same component.

Shared information should include enough context to support action without disclosing restricted technical details unnecessarily.

## 35. Protect vulnerability information

Vulnerability findings may reveal exploitable details.

The application should restrict access to:

- scan reports;
- penetration-test reports;
- proof-of-concept details;
- vulnerable endpoints;
- source-code findings;
- credentials accidentally captured;
- architecture weaknesses;
- unpatched component lists;
- exploit paths;
- supplier advisories under confidentiality; and
- risk acceptances.

Reports should be stored in approved systems and shared on a need-to-know basis.

Credentials and complete restricted data should not be included in ordinary evidence records.

## 36. Maintain metrics and trends

Useful application vulnerability measures may include:

- components in scanning scope;
- scan coverage;
- authenticated scan coverage;
- high and critical findings;
- overdue findings;
- mean time to triage;
- mean time to remediate;
- retest backlog;
- reopened findings;
- unsupported components;
- findings by source;
- repeat weaknesses;
- dependency age;
- exceptions approaching expiry;
- supplier-delayed fixes;
- releases with unresolved vulnerabilities;
- false-positive rate; and
- coverage gaps.

Metrics should support decisions rather than reward rapid closure without effective remediation.

## 37. Analyse recurring weaknesses

The application should identify patterns such as:

- repeated injection flaws;
- recurring access-control errors;
- repeated vulnerable dependencies;
- insecure configuration returning after upgrades;
- recurring unsupported components;
- repeated production scan exclusions;
- recurring false positives;
- repeated emergency patching;
- suppliers repeatedly missing remediation commitments; and
- the same vulnerability class across several modules.

Recurring findings should drive root-cause improvement in:

- coding standards;
- architecture;
- developer training;
- design review;
- dependency management;
- test automation;
- release gates;
- supplier requirements;
- configuration baselines; and
- monitoring.

## 38. Integrate vulnerability controls into the SDLC

The application should include vulnerability detection and treatment in normal development and release activities.

This may include:

- threat modelling;
- secure coding;
- code review;
- static analysis;
- dependency analysis;
- secret scanning;
- artefact scanning;
- container scanning;
- security tests;
- release gates;
- vulnerability thresholds;
- exception approval;
- remediation backlog;
- retest;
- release notes;
- baseline update; and
- post-release monitoring.

Security scanning should not be postponed until the end of development where findings become expensive to correct.

## 39. Establish release vulnerability criteria

The application should define when vulnerabilities prevent release.

Criteria may consider:

- critical or high severity;
- active exploitation;
- authentication or access-control bypass;
- remote code execution;
- exposed credentials;
- compromise of restricted information;
- privilege escalation;
- malicious-code execution;
- data-integrity impact;
- unsupported component;
- missing mitigation;
- failed retest;
- expired exception; and
- supplier uncertainty.

Where a release proceeds with a known vulnerability, the decision should be explicit, risk-based and documented.

## 40. Test the vulnerability-management process

The application should periodically verify that:

- all components are included;
- scanner credentials work;
- scanning reaches authenticated paths;
- results enter the authoritative tracker;
- owners are notified;
- severity is assessed consistently;
- remediation targets are applied;
- overdue findings escalate;
- exceptions expire;
- fixes are retested;
- unsupported components are visible;
- supplier advisories are reviewed;
- metrics are accurate; and
- the SSP reflects the current process.

## 41. Review the vulnerability-monitoring approach

The application should review its approach after:

- architecture change;
- new technology;
- new scanner;
- major product upgrade;
- supplier change;
- incident;
- penetration test;
- recurring weakness;
- new enterprise remediation policy;
- material change in exposure;
- failure to detect a known vulnerability; or
- significant false-positive or coverage problem.

## 42. Remove obsolete scanning targets and add new ones

When components change, the application should:

- add new components to scanning scope;
- remove retired components only after verified decommissioning;
- update credentials;
- update endpoint lists;
- update API definitions;
- update dependency manifests;
- update SBOMs;
- update component ownership;
- update scan safety constraints;
- update dashboards; and
- verify coverage.

A retired scanner target should not hide a still-deployed legacy component.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses enterprise vulnerability scanners, source repositories, dependency scanning, service management and change control. They exclude enterprise scanning-platform engineering and the engineering effort required to remediate vulnerabilities.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the application vulnerability scope** | Identify custom code, products, versions, thick clients, dependencies, APIs, schemas, plugins, images, interfaces and supplier components that require monitoring. | Summarise scope in the **SSP RA-05 statement** and align it with the existing **CM-02 baseline**, **CM-08 inventory**, **architecture**, **release manifest** and **SBOM**. | **6–12 hours** |
| **2. Map each component to an assessment method** | Define whether each component is covered by infrastructure scanning, SAST, DAST, SCA, API testing, configuration assessment, supplier review, penetration testing or manual review. | Record the mapping in the **security test strategy**, **assurance plan**, **SDLC**, **SyOps** or **SSP RA-05 section**. | **8–16 hours** |
| **3. Define frequencies and event-driven triggers** | Apply corporate scanning frequencies and add release-, change-, incident- and new-vulnerability-triggered assessments appropriate to the application. | Record frequencies and triggers in the **SSP**, **continuous-monitoring plan**, **release process**, **service calendar** or **SDLC**. | **4–8 hours** |
| **4. Configure safe and authorised application scanning** | Define targets, accounts, source addresses, permitted techniques, rate limits, prohibited destructive actions, stop conditions and support contacts. | Use the existing **scan request**, **test plan**, **operational runbook**, **SyOps**, **change record** and **security assessment plan**. | **6–16 hours** |
| **5. Implement code and dependency scanning** | Run SAST, secret scanning and SCA in the development or build process and generate an SBOM or equivalent dependency record where proportionate. | Evidence remains in the normal **source repository**, **pipeline history**, **SAST/SCA reports**, **SBOM**, **release evidence pack** and **SA-11 test evidence**. | **12–32 hours initially** |
| **6. Assess web, API and business-logic vulnerabilities** | Use authenticated application scanning and targeted manual testing for roles, object access, workflows, exports, file handling, APIs and administrative paths. | Add coverage to the established **security test plan**, **penetration-test scope**, **API test plan** and **security test report**. | **16–48 hours per major assessment cycle** |
| **7. Assess configuration, database and thick-client weaknesses** | Review application settings, schema logic, roles, packages, local storage, client/server trust and included libraries. | Record evidence in the existing **CM-06 review**, **database security test**, **thick-client test**, **configuration assessment** and **release pack**. | **12–32 hours per major assessment cycle** |
| **8. Monitor supplier advisories and support status** | Subscribe to relevant advisories, identify affected versions, track supplier fixes and monitor end-of-support dates. | Use the existing **supplier record**, **component inventory**, **risk register**, **service review**, **support case** and **release plan**. | **3–8 hours per month or review cycle** |
| **9. Triage findings using application context** | Validate true positives, affected components, exploitability, business impact, exposure, active exploitation and compensating controls. | Record the result in the authoritative **vulnerability tracker**, **defect system**, **risk register**, **POA&M** or **service-management record**. | **1–4 hours per ordinary finding; more for complex findings** |
| **10. Assign treatment, ownership and target dates** | Allocate remediation, mitigation, removal or risk treatment and apply enterprise deadlines adjusted for application impact where appropriate. | Maintain owner, target, release and status in the normal **vulnerability record**, **defect backlog**, **risk register**, **POA&M** or **change plan**. | **1–2 hours per finding** |
| **11. Implement compensating controls for delayed fixes** | Restrict or disable affected functions, reduce access, isolate paths, increase monitoring or apply supplier workarounds until permanent remediation. | Record controls in the **risk record**, **change ticket**, **incident record**, **SyOps**, **application addendum** and **SSP** where material. | **4–16 hours per issue, excluding engineering change** |
| **12. Retest and verify remediation** | Confirm the deployed correction, rerun the original test, verify all instances and update the baseline, inventory and exception status. | Retain evidence in the **retest report**, **change record**, **release pack**, **vulnerability record**, **CM-02 baseline** and **CM-08 inventory**. | **2–8 hours per finding or remediation group** |
| **13. Track unsupported components and scanning gaps** | Identify end-of-life products, abandoned dependencies, unscannable components and blind spots and assign treatment or alternative assurance. | Use the existing **component inventory**, **risk register**, **problem record**, **supplier plan** and **application addendum**. | **6–12 hours initially; 3–8 hours per review** |
| **14. Report vulnerability posture and trends** | Summarise coverage, high-risk findings, overdue actions, unsupported components, exceptions, recurring weaknesses and supplier delays. | Include the summary in the normal **service review**, **security review**, **risk committee pack**, **CA-07 posture report** or **SSP status review**. | **4–8 hours per report** |
| **15. Test the vulnerability-management process** | Verify scope, credentials, evidence flow, ownership, escalation, expiry, retesting, metrics and SSP alignment. | Capture outcomes in the normal **control assessment**, **annual security review**, **service-improvement plan** or **CA-07 review**. | **8–16 hours per annual review** |
| **16. Document and manage vulnerability-monitoring limitations** | Record excluded targets, unsafe production tests, supplier restrictions, unsupported tools or incomplete coverage with alternative controls and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP RA-05 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application with established enterprise scanning and mature CI/CD services, initial application setup is commonly around **100–230 hours**.

Ongoing application effort commonly ranges from **15–45 hours per month**, excluding remediation engineering and major penetration-test support.

A simple commercial application with a small footprint may require less. A custom, integration-heavy, thick-client, legacy or supplier-constrained application may require substantially more.

The estimates should not be added mechanically where activities overlap. RA-05 commonly shares evidence and effort with:

- CM-02 baseline configuration;
- CM-06 configuration settings;
- CM-08 component inventory;
- SI-02 flaw remediation;
- SI-07 software integrity;
- SI-10 input validation;
- SA-11 security testing;
- CA-07 continuous monitoring;
- AU-02 event logging; and
- IR-05 incident monitoring.

---

## Suggested document placement

To avoid creating disconnected evidence, vulnerability-monitoring information should normally be distributed across established application and SDLC artefacts:

- **SSP:** RA-05 implementation approach, application scope, inherited enterprise scanning, methods, frequencies, triggers, triage, remediation, reporting and limitations.
- **ConOps or SyOps:** operational scanning windows, scanner accounts, safety constraints, supplier interaction, support responsibilities and emergency response.
- **Security architecture:** components, exposed interfaces, trust boundaries, scanning points and high-risk functions.
- **CM-02 baseline:** approved versions and artefacts against which vulnerability findings are assessed.
- **CM-08 component inventory:** products, versions, ownership, location, support status and scan coverage.
- **SBOM or dependency record:** direct and transitive software dependencies.
- **Security testing strategy:** SAST, DAST, SCA, API testing, penetration testing, configuration review and business-logic assessment.
- **SDLC and pipeline configuration:** automated scanning, thresholds, release gates and evidence retention.
- **Scan authorisation or test plan:** targets, accounts, methods, constraints, timing, support and stop conditions.
- **Supplier records:** advisories, support status, case references, remediation commitments and end-of-life dates.
- **Vulnerability or defect tracker:** finding, owner, risk, target date, planned release, treatment and retest.
- **Risk register or POA&M:** accepted risk, delayed remediation, compensating controls and overdue actions.
- **Change and release records:** implementation of patches, upgrades, configuration changes and mitigations.
- **Security and penetration-test reports:** verified technical findings and business-logic weaknesses.
- **Retest reports:** proof that remediation is effective.
- **CA-07 service or posture reviews:** coverage, trends, overdue findings, unsupported components and recurring weaknesses.
- **Application addendum:** scanning exclusions, supplier restrictions, unsupported technologies and alternative assurance.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- enterprise vulnerability-management policy;
- central vulnerability-scanning platforms;
- endpoint and server scanning agents;
- corporate vulnerability intelligence;
- enterprise severity and remediation-time standards;
- operating-system patching;
- shared database-platform patching;
- network-device and firewall vulnerability management;
- hypervisor and virtualisation patching;
- managed Windows EUC scanning and patching;
- enterprise middleware and shared-platform remediation;
- central vulnerability dashboards;
- organisation-wide penetration-testing governance;
- enterprise threat intelligence;
- central risk, POA&M and exception tooling;
- enterprise SIEM and SOC operations; and
- organisation-wide escalation and reporting.

The application team must still:

- identify all application components and attack paths;
- ensure they are included in appropriate assessments;
- operate code, dependency and application-specific scanning;
- assess commercial and supplier products;
- interpret results using application context;
- assign and track remediation;
- implement temporary controls;
- verify fixes;
- monitor unsupported components;
- report application posture; and
- document limitations.

> **Key dividing line:** the enterprise provides common vulnerability intelligence, scanning platforms and shared-platform remediation; the application ensures that the complete business solution is assessed, interprets the findings and owns treatment of vulnerabilities in its code, products, dependencies, configuration and business logic.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, RA-05 Vulnerability Monitoring and Scanning.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, RA-05 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-40 Rev. 4, Guide to Enterprise Patch Management Planning: Preventive Maintenance for Technology**.
4. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1**.
5. National Institute of Standards and Technology, **NIST SP 1800-31, Improving Enterprise Patching for General IT Systems**.
6. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, current RA-05 control and assessment content.
