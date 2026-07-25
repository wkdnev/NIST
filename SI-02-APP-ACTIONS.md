# SI-02 Flaw Remediation — Application Actions

## Purpose

For an IT application, SI-02 means the application must **identify, assess, correct, test, deploy and verify fixes for security flaws affecting the application within risk-based timescales**.

A flaw is broader than a missing operating-system patch. It may exist in:

- custom source code;
- commercial application software;
- thick-client packages;
- third-party libraries;
- runtime frameworks;
- APIs;
- database logic;
- plugins and extensions;
- application configuration;
- file-processing components;
- build and deployment artefacts;
- supplier-delivered modules;
- authentication or authorisation logic;
- business workflows; or
- unsupported and end-of-life technology.

The enterprise may provide:

- enterprise vulnerability intelligence;
- infrastructure patching;
- endpoint and server patch-management platforms;
- vulnerability-scanning services;
- central remediation deadlines;
- enterprise change and release management;
- service-management tooling;
- managed Microsoft Windows EUC;
- shared database and platform patching;
- central risk and exception governance; and
- organisation-wide reporting.

Those capabilities are inherited.

The application remains responsible for determining whether a flaw applies to the application, prioritising it using application context, developing or obtaining the correction, testing the correction, deploying it safely, confirming complete deployment, verifying that the flaw is no longer exploitable, maintaining the application baseline and managing any delay or residual risk.

NIST SI-02 requires organisations to identify, report and correct system flaws; test software and firmware updates before installation; install security-relevant updates within organisation-defined timescales; and incorporate flaw remediation into configuration management. NIST SP 800-40 Rev. 4 frames patching as preventive maintenance that includes identifying, prioritising, acquiring, installing and verifying patches, updates and upgrades. The 2025 NIST SP 800-53 Release 5.2.0 also added SI-02(07), addressing root-cause analysis for flaws.

> **Core principle:** the enterprise provides common patching, intelligence and governance; the application team owns the complete remediation lifecycle for flaws in the application’s code, products, dependencies, configuration and business behaviour.

---

## 1. Define the application flaw-remediation scope

The application should identify all components for which it has remediation responsibility.

This normally includes:

- custom-developed code;
- configured or customised commercial software;
- thick-client packages;
- web and application services;
- APIs;
- application-owned database schemas and logic;
- runtime frameworks;
- third-party packages and transitive dependencies;
- container and application images;
- plugins, extensions and scripts;
- report engines and templates;
- file parsers and converters;
- integration adapters;
- scheduled jobs;
- application configuration;
- service identities and associated permissions;
- build and deployment definitions;
- supplier-delivered modules;
- recovery artefacts; and
- obsolete versions still deployed.

The scope should align with:

- CM-02 baseline configuration;
- CM-08 component inventory;
- RA-05 vulnerability-monitoring scope;
- SBOM or dependency records;
- architecture;
- release manifests;
- deployed environments; and
- supplier support records.

## 2. Distinguish enterprise and application remediation ownership

For each component or flaw class, the application should establish who owns:

- vulnerability identification;
- applicability assessment;
- patch acquisition;
- code correction;
- configuration mitigation;
- testing;
- change approval;
- deployment;
- verification;
- rollback;
- risk acceptance;
- supplier escalation; and
- closure.

Typical division:

| Area | Typical enterprise responsibility | Typical application responsibility |
|---|---|---|
| Windows EUC operating system | Enterprise endpoint management | Confirm application compatibility with required enterprise updates |
| Server operating system | Enterprise infrastructure team | Confirm application compatibility and perform application validation |
| Shared database platform | Enterprise database-platform team | Test application schemas, drivers and behaviour against the update |
| Shared middleware/platform | Enterprise platform owner | Assess application dependency and validate the application after change |
| Custom application code | None beyond shared SDLC tooling | Full correction, testing, deployment and verification |
| Commercial application product | Enterprise may support procurement/change tooling | Assess applicability, obtain supplier fix, test, deploy and verify |
| Thick-client package | Enterprise distributes package | Application team builds, approves, tests and versions the package |
| Third-party library | Enterprise may provide SCA tooling | Application team updates, tests and deploys the dependency |
| Application configuration | Enterprise may provide hosting controls | Application team corrects and verifies application-specific settings |

Ownership should be explicit enough that a flaw cannot remain unresolved because each team assumes another team owns it.

## 3. Maintain authoritative sources of flaw information

The application should monitor and receive flaw information from relevant sources, including:

- RA-05 scan results;
- static application security testing;
- dynamic application security testing;
- software-composition analysis;
- penetration tests;
- code review;
- supplier security advisories;
- product release notes;
- enterprise threat intelligence;
- national vulnerability databases;
- national and sector advisories;
- incidents;
- bug reports;
- support cases;
- configuration assessments;
- red-team or purple-team findings;
- security architecture review;
- user reports;
- responsible disclosure; and
- internal defect testing.

All legitimate findings should enter an authoritative application remediation workflow.

## 4. Record each flaw consistently

Each flaw record should normally include:

- unique identifier;
- source;
- date identified;
- affected application;
- affected component;
- affected version;
- affected environment;
- description;
- weakness or vulnerability identifier;
- supplier advisory or CVE where applicable;
- severity;
- exploitability;
- business and information impact;
- known exploitation status;
- owner;
- treatment decision;
- target date;
- planned release;
- interim controls;
- test requirements;
- supplier case;
- dependencies;
- risk or exception reference;
- current status;
- deployment coverage;
- retest evidence; and
- closure approval.

The normal vulnerability tracker, defect system, service-management platform, risk register or POA&M should be used rather than a detached spreadsheet.

## 5. Confirm applicability

Before remediation planning, the application should determine whether the flaw affects the actual deployed solution.

Applicability assessment should consider:

- exact product and version;
- enabled module;
- vulnerable dependency version;
- affected code path;
- configuration;
- architecture;
- exposed interface;
- required privilege;
- user interaction;
- operating mode;
- deployment environment;
- compensating controls;
- supplier statement;
- thick-client version;
- affected database driver;
- vulnerable build artefact;
- recovery copies; and
- retired versions that may still be usable.

The outcome should be one of:

- applicable;
- not applicable;
- potentially applicable;
- awaiting evidence; or
- accepted as an unverified risk.

A scanner false positive should be closed only with evidence.

## 6. Prioritise using application risk

Enterprise severity and remediation deadlines should be treated as minimum governance inputs. The application should add business context.

Prioritisation should consider:

- technical severity;
- active exploitation;
- exploit availability;
- remote or local access;
- authentication required;
- privilege required;
- user interaction;
- data sensitivity;
- effect on confidentiality, integrity or availability;
- approval, engineering, financial or safety impact;
- attack-path reachability;
- number of affected instances;
- supplier access;
- recovery impact;
- ability to detect exploitation;
- available mitigation;
- patch maturity;
- operational criticality; and
- residual exposure after enterprise controls.

An internally reachable authentication bypass may deserve greater urgency than a numerically higher-rated flaw in an unused component.

## 7. Define remediation timeframes

The application should apply organisation-defined timeframes for:

- critical flaws;
- high flaws;
- medium flaws;
- low flaws;
- actively exploited vulnerabilities;
- emergency directives;
- unsupported components;
- supplier-dependent flaws;
- flaws requiring architecture change; and
- flaws with effective temporary mitigation.

Where the enterprise defines fixed service levels, the application should follow them.

The application should also define:

- when the clock begins;
- conditions for pausing it;
- required escalation;
- approval for extension;
- retest deadline;
- treatment of partial deployment;
- treatment of unavailable supplier fixes; and
- treatment of flaws found immediately before release.

## 8. Assess emergency treatment triggers

An accelerated process should be available for flaws involving:

- active exploitation;
- remote code execution;
- authentication bypass;
- privilege escalation;
- exposed credentials or secrets;
- application signing or build compromise;
- unauthorised access to restricted information;
- destructive integrity impact;
- widespread malware exploitation;
- exposed supplier access;
- critical unsupported components;
- high-impact business logic;
- known exploitation within the organisation; or
- direction from enterprise security leadership.

Emergency treatment may include:

- immediate feature disablement;
- access restriction;
- integration isolation;
- credential rotation;
- increased logging;
- emergency patching;
- emergency configuration change;
- threat hunting;
- user communication; and
- incident activation.

## 9. Determine the appropriate treatment

Treatment options include:

- custom code correction;
- supplier patch;
- product upgrade;
- dependency update;
- configuration change;
- disabling a feature;
- restricting access;
- isolation;
- removal of a plugin;
- credential or certificate rotation;
- changing permissions;
- replacing a component;
- virtual patch;
- compensating monitoring;
- temporary read-only mode;
- data correction;
- migration; or
- retirement.

The treatment should address the exploitable condition, not merely suppress the scanner finding.

## 10. Obtain fixes from trusted sources

Patches, updates and replacement packages should be obtained from:

- approved supplier portals;
- enterprise software repositories;
- approved package repositories;
- controlled source repositories;
- authorised artefact repositories;
- approved support channels; or
- controlled internal build pipelines.

The application should verify, where available:

- supplier or publisher;
- digital signature;
- checksum;
- version;
- release notes;
- security advisory;
- package integrity;
- provenance;
- dependencies;
- prerequisites;
- superseded updates; and
- support entitlement.

Patches should not be obtained from informal file-sharing locations or unverified third parties.

## 11. Preserve the original flaw evidence

Before correction, the application should retain enough evidence to support:

- reproducibility;
- testing;
- root-cause analysis;
- incident investigation;
- audit;
- supplier escalation;
- regression testing; and
- closure.

Evidence may include:

- scan output;
- test steps;
- affected request;
- stack trace;
- vulnerable package version;
- screenshot;
- code location;
- supplier advisory;
- proof-of-concept details;
- relevant configuration;
- logs;
- affected record type; and
- environmental conditions.

Sensitive exploit information should be access-restricted.

## 12. Develop custom code corrections securely

For custom code, remediation should follow the approved SDLC.

The correction should include, as appropriate:

- root-cause understanding;
- secure design;
- code change;
- peer review;
- static analysis;
- dependency review;
- unit tests;
- negative security tests;
- regression tests;
- updated threat or misuse case;
- updated documentation;
- build from controlled source;
- approved artefact;
- release note;
- rollback plan; and
- retest against the original flaw.

A narrow patch that blocks one payload but leaves the underlying unsafe design may be insufficient.

## 13. Update third-party dependencies

Dependency remediation should consider:

- direct and transitive dependencies;
- compatible fixed version;
- breaking changes;
- package provenance;
- package integrity;
- licence impact;
- support status;
- removed or renamed package;
- dependency confusion;
- build reproducibility;
- runtime compatibility;
- thick-client package impact;
- container-image impact;
- SBOM update; and
- removal of the vulnerable version.

The application should confirm that the fixed dependency is actually present in the deployed artefact.

## 14. Patch or upgrade commercial products

For commercial products, the application should:

- confirm affected modules and versions;
- review supplier advisory and release notes;
- obtain the approved package;
- identify prerequisites;
- identify incompatible customisation;
- review configuration changes;
- assess data migration;
- assess licence or infrastructure impact;
- assess rollback;
- test supplier claims;
- track supplier case references;
- identify unsupported modules;
- plan outage where required;
- update the approved baseline; and
- confirm all instances are updated.

Supplier release notes are inputs to testing, not a substitute for testing.

## 15. Correct configuration flaws

Where a flaw results from configuration, the application should:

- identify the authoritative setting;
- define the secure value;
- assess dependencies;
- change the controlled configuration source;
- prevent local override;
- test the change;
- deploy through the approved path;
- compare the resulting state with the baseline;
- monitor for drift;
- update CM-06 evidence; and
- remove insecure fallback settings.

Examples include:

- anonymous access;
- permissive roles;
- weak session settings;
- unsafe file types;
- debug mode;
- insecure certificate validation;
- excessive error detail;
- obsolete APIs;
- broad export;
- unrestricted callbacks;
- disabled logging; and
- excessive service permissions.

## 16. Correct database and data-layer flaws

Application-owned database remediation may include:

- schema change;
- stored procedure correction;
- safer query construction;
- role or privilege reduction;
- trigger correction;
- index or constraint change;
- migration script;
- data repair;
- audit correction;
- removal of obsolete objects; and
- driver update.

The application should distinguish:

- database platform patching, normally enterprise-owned; and
- application schema, logic, role and data correction, application-owned.

Direct production data repair should follow controlled and attributable procedures.

## 17. Correct thick-client flaws

For thick-client applications, remediation may require changes to:

- application binaries;
- bundled libraries;
- installer;
- updater;
- protocol handler;
- local service;
- configuration;
- server validation;
- local storage;
- file associations;
- privilege requirements;
- plugins;
- package signing; and
- removal of obsolete versions.

The application team should create and approve the corrected package.

The enterprise software-distribution service may deploy it, but the application should verify deployment coverage and ensure obsolete versions cannot continue to connect where this creates risk.

## 18. Correct API and integration flaws

Remediation may include:

- token validation;
- authorisation;
- schema validation;
- object-level access;
- rate limits;
- version retirement;
- endpoint restriction;
- caller scope;
- callback allow-listing;
- replay protection;
- message validation;
- file-transfer controls;
- destination restriction;
- error handling;
- service identity permissions; and
- removal of obsolete clients.

Connected-system owners should be involved where a correction changes the interface contract.

## 19. Correct file-processing flaws

File-processing remediation may include:

- parser upgrade;
- file-type restriction;
- archive limits;
- path handling;
- temporary-file controls;
- malicious-code scanning;
- sandboxing;
- conversion isolation;
- resource limits;
- active-content restriction;
- output sanitisation; and
- removal of vulnerable formats.

Where no timely parser fix exists, disabling the affected file type may be the safest treatment.

## 20. Correct build and deployment flaws

A flaw may exist in the software-production process rather than the runtime application.

Treatment may include:

- rotating pipeline credentials;
- removing a vulnerable plugin;
- updating build tools;
- protecting branches;
- correcting package sources;
- changing runner images;
- restoring security gates;
- protecting signing;
- restricting artefact promotion;
- regenerating releases;
- revoking compromised artefacts;
- improving provenance; and
- rebuilding from trusted source.

The application should assess whether previously produced artefacts may be affected.

## 21. Test fixes before production installation

NIST SI-02 explicitly requires software and firmware updates related to flaw remediation to be tested for effectiveness and potential side effects before installation.

Testing should consider:

- original exploit or failure condition;
- vulnerable code path;
- functional regression;
- performance;
- compatibility;
- database migration;
- thick-client compatibility;
- integrations;
- security controls;
- logging;
- monitoring;
- backup and recovery;
- data integrity;
- high-availability behaviour;
- installation;
- rollback;
- removal of temporary mitigation; and
- unsupported combinations.

Testing should occur in a representative non-production environment where practical.

## 22. Use a risk-based test depth

The depth of testing should reflect:

- flaw severity;
- component criticality;
- complexity of the change;
- supplier confidence;
- size of the update;
- scope of affected functions;
- data migration;
- operational outage;
- rollback difficulty;
- active exploitation;
- available test time;
- change in dependencies; and
- consequences of failure.

An emergency fix may use an abbreviated pre-production test, but should receive enhanced monitoring and follow-up testing.

## 23. Verify that the fix addresses the original flaw

The application should rerun the original detection method or equivalent.

This may involve:

- rescan;
- code-analysis rerun;
- dependency scan;
- penetration retest;
- manual exploit test;
- configuration comparison;
- supplier verification;
- API test;
- file-parser test;
- business-workflow test; or
- version and package verification.

Closure should demonstrate that the exploitable condition has been removed or acceptably constrained.

## 24. Test for side effects and regression

The application should confirm that remediation has not introduced:

- broken authentication;
- weaker authorisation;
- data loss;
- incorrect business logic;
- failed integration;
- performance collapse;
- logging failure;
- broken monitoring;
- incompatible client versions;
- unsafe fallback;
- new dependency vulnerability;
- failed recovery;
- unexpected privilege;
- workflow bypass; or
- disabled security function.

Security fixes are still changes and require controlled regression testing.

## 25. Define rollback and recovery

Before deployment, the application should define:

- rollback trigger;
- previous trusted version;
- rollback artefact;
- database rollback or forward-fix plan;
- backup requirements;
- configuration restoration;
- client rollback;
- integration compatibility;
- data created under the new version;
- decision authority;
- maximum tolerable outage;
- monitoring; and
- post-rollback security risk.

A rollback may reintroduce the flaw. That decision should be explicit and accompanied by alternative containment.

## 26. Deploy fixes through controlled change

Flaw remediation should use:

- approved change record;
- approved release;
- controlled artefact;
- authorised deployment identity;
- maintenance window where required;
- stakeholder notification;
- verified backup or rollback;
- versioned configuration;
- deployment logs;
- post-deployment checks;
- baseline update; and
- inventory update.

Emergency procedures may shorten approval steps but should not eliminate attribution, evidence, rollback and review.

## 27. Verify deployment coverage

The application should confirm correction across all affected:

- production nodes;
- standby nodes;
- thick-client installations;
- database instances;
- containers;
- images;
- scheduled jobs;
- APIs;
- integrations;
- recovery environments;
- offline packages;
- test environments that could reintroduce vulnerable artefacts;
- supplier-maintained components; and
- superseded versions still accessible.

Partial deployment means the flaw remains open unless the remaining exposure is separately treated and approved.

## 28. Prevent vulnerable-version reintroduction

The application should prevent older vulnerable versions from returning through:

- rollback;
- recovery media;
- stale container tags;
- old installation packages;
- developer branches;
- cached dependencies;
- supplier packages;
- lower environments;
- build images;
- disconnected thick clients;
- manual copying;
- old artefact repositories; or
- disaster recovery.

Controls may include:

- blocked versions;
- approved repository policy;
- package supersedence;
- minimum client version;
- image digest controls;
- dependency lock files;
- release gates;
- removal of obsolete packages;
- updated recovery artefacts; and
- scanning of rebuilt components.

## 29. Update the application baseline and inventory

After remediation, update:

- CM-02 baseline;
- CM-06 configuration;
- CM-08 inventory;
- SBOM;
- release manifest;
- deployment records;
- thick-client package records;
- supplier records;
- vulnerability record;
- recovery plan;
- architecture where changed;
- test evidence; and
- SSP implementation status where material.

The documented approved state should match the deployed corrected state.

## 30. Remove temporary mitigations when appropriate

Temporary controls should not remain indefinitely without review.

After the permanent fix, determine whether to remove or retain:

- access restrictions;
- disabled features;
- virtual patches;
- additional monitoring;
- temporary firewall rules;
- emergency roles;
- shortened timeouts;
- export restrictions;
- blocked file types;
- supplier access restrictions; and
- manual review steps.

Some temporary controls may provide continuing value and can be formally adopted into the baseline.

## 31. Maintain interim protection when no fix exists

Where no correction is available, the application should identify and implement the safest feasible treatment.

Options may include:

- disable the function;
- isolate the component;
- restrict users;
- remove supplier access;
- block the interface;
- use read-only mode;
- restrict file types;
- reduce service privilege;
- rotate credentials;
- apply a vendor workaround;
- use a virtual patch;
- increase monitoring;
- add alerting;
- shorten sessions;
- limit transaction volume;
- add independent approval;
- migrate data;
- accelerate replacement; or
- take the application out of service.

The interim state should be tested, monitored and risk-approved.

## 32. Manage supplier-dependent remediation

Where remediation depends on a supplier, the application should:

- open and track a supplier case;
- provide reproducible evidence;
- obtain an affected-version statement;
- obtain mitigation advice;
- obtain target-fix timing;
- assess confidentiality restrictions;
- escalate through contract or service management;
- test supplier workarounds;
- track missed commitments;
- assess support status;
- identify replacement options;
- communicate residual risk; and
- verify the eventual supplier fix.

Supplier dependency does not suspend application accountability.

## 33. Manage remediation exceptions

Where the application cannot meet the required deadline, record:

- flaw;
- affected components and versions;
- risk;
- business impact;
- active exploitation status;
- reason for delay;
- planned permanent treatment;
- interim controls;
- monitoring;
- owner;
- approving authority;
- supplier dependency;
- target date;
- review date;
- expiry date; and
- conditions requiring immediate escalation.

Exceptions should be time-limited and reviewed. Repeated renewal without progress indicates an unresolved risk.

## 34. Escalate overdue remediation

The application should escalate flaws that:

- exceed enterprise deadlines;
- lack an owner;
- lack a credible treatment;
- depend on an unresponsive supplier;
- affect unsupported components;
- have ineffective mitigation;
- have failed retest;
- are only partly deployed;
- are actively exploited;
- have an expired exception; or
- recur after previous closure.

Escalation routes may include:

- application owner;
- information owner;
- security governance;
- risk committee;
- supplier management;
- service management;
- incident response; and
- senior accountable owner.

## 35. Verify closure independently where proportionate

High-risk flaws should receive independent confirmation by:

- security tester;
- code reviewer;
- penetration tester;
- vulnerability-management team;
- product owner;
- database reviewer;
- service owner; or
- other competent person not solely responsible for implementing the fix.

The level of independence should reflect risk and team size.

## 36. Reopen ineffective or incomplete remediation

A flaw should be reopened where:

- the original exploit still works;
- an alternate path remains;
- only some instances are fixed;
- a vulnerable dependency remains in the artefact;
- a thick-client old version remains usable;
- the configuration drifts back;
- the supplier fix is incomplete;
- the workaround fails;
- recovery reintroduces the flaw;
- a regression reopens the condition; or
- evidence does not support closure.

## 37. Perform root-cause analysis

For significant or recurring flaws, the application should determine why the flaw arose and why existing controls did not prevent or detect it earlier.

Root-cause analysis should consider:

- insecure design;
- missing requirement;
- unsafe coding pattern;
- weak code review;
- inadequate testing;
- missing threat model;
- poor dependency management;
- supplier failure;
- configuration drift;
- unclear ownership;
- incomplete inventory;
- weak release gate;
- emergency change;
- inadequate training;
- unsupported component;
- copied vulnerable code;
- poor monitoring; and
- repeated failure to implement previous lessons.

The 2025 NIST SP 800-53 Release 5.2.0 added SI-02(07), Root Cause Analysis, with corresponding assessment procedures.

## 38. Turn root causes into preventive improvements

Root-cause analysis should produce controlled improvements such as:

- secure design pattern;
- reusable library;
- coding-standard update;
- new validation rule;
- new automated test;
- new SAST or SCA rule;
- new release gate;
- improved dependency policy;
- improved supplier requirement;
- better inventory;
- improved configuration baseline;
- training;
- architecture change;
- monitoring enhancement;
- revised remediation deadline;
- product replacement; or
- wider search for the same weakness.

The corrective action should be owned, tracked and verified.

## 39. Search for related flaws

When one significant flaw is found, the application should determine whether similar weaknesses exist elsewhere.

Search may include:

- same code pattern;
- same dependency;
- same product version;
- same configuration;
- same API pattern;
- same parser;
- same supplier module;
- same workflow;
- same thick-client package;
- same deployment image;
- same service-account privilege; and
- same flaw across related applications.

Fixing only the initially reported occurrence may leave the broader weakness intact.

## 40. Monitor remediation metrics

Useful application measures include:

- open flaws by severity;
- overdue flaws;
- mean time to applicability assessment;
- mean time to remediate;
- mean time to retest;
- partial deployments;
- failed remediations;
- reopened flaws;
- supplier-delayed flaws;
- flaws with temporary mitigation;
- unsupported components;
- exception age;
- recurring weakness classes;
- emergency fixes;
- percentage of fixes verified;
- release-blocking flaws; and
- vulnerable versions still deployed.

Metrics should support risk decisions and improvement, not encourage unsupported closure.

## 41. Report application remediation posture

The application should report, at an appropriate frequency:

- critical and high flaws;
- active exploitation;
- overdue remediation;
- unsupported components;
- exceptions;
- supplier dependencies;
- deployment coverage;
- failed retests;
- upcoming patches or upgrades;
- material operational risk;
- root-cause themes; and
- decisions required.

Reporting should use the enterprise vulnerability, service, risk or CA-07 processes.

## 42. Protect flaw and remediation information

Flaw records may contain exploitable detail.

The application should:

- restrict access;
- use approved systems;
- protect proof-of-concept material;
- avoid credentials in reports;
- minimise restricted business data;
- control supplier sharing;
- preserve integrity;
- retain decision history;
- prevent unauthorised deletion;
- log material changes; and
- apply approved retention.

## 43. Integrate remediation with incident response

Where exploitation is suspected or confirmed, the application should:

- link the flaw record to the incident;
- preserve evidence;
- assess affected versions;
- support scoping;
- identify vulnerable periods;
- identify accounts and records at risk;
- deploy containment;
- coordinate emergency correction;
- verify recovery;
- retain heightened monitoring; and
- update lessons learned.

Installing a patch does not establish whether exploitation occurred before installation.

## 44. Integrate remediation with continuous monitoring

CA-07 monitoring should confirm that:

- open flaws remain visible;
- deadlines are tracked;
- exceptions remain current;
- supplier actions progress;
- deployed versions remain corrected;
- temporary controls remain effective;
- no vulnerable versions reappear;
- unsupported components remain visible;
- recurring weaknesses are addressed; and
- remediation metrics drive decisions.

## 45. Review flaw-remediation arrangements periodically

The application should review its process after:

- a significant flaw;
- an actively exploited vulnerability;
- failed deployment;
- failed rollback;
- recurring vulnerability;
- missed deadline;
- supplier delay;
- incident;
- audit finding;
- new application technology;
- new build or deployment process;
- platform migration;
- change in enterprise policy; or
- release of new NIST guidance.

## 46. Test the remediation process itself

The application should periodically verify that:

- findings enter the authoritative tracker;
- owners are assigned;
- applicability is assessed;
- deadlines are calculated;
- emergency routes work;
- supplier escalation works;
- fixes are tested;
- deployment coverage is confirmed;
- retest evidence is retained;
- baselines and inventories update;
- exceptions expire;
- overdue items escalate;
- recovery artefacts are updated; and
- root-cause actions are completed.

## 47. Decommission rather than perpetually patch where appropriate

Where a component is:

- unsupported;
- repeatedly vulnerable;
- impossible to test;
- supplier-abandoned;
- incompatible with enterprise security controls;
- dependent on obsolete libraries;
- unable to receive timely fixes; or
- disproportionately expensive to maintain securely,

the application should evaluate:

- feature removal;
- isolation;
- migration;
- replacement;
- retirement; or
- service redesign.

Continued exception renewal is not a sustainable remediation strategy.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses enterprise vulnerability management, patch-management, source-control, CI/CD, service-management and change processes. They exclude enterprise platform engineering and the engineering effort needed to implement individual fixes.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define remediation scope and ownership** | Map custom code, commercial products, thick clients, dependencies, schemas, integrations and configuration to named remediation owners and inherited enterprise responsibilities. | Summarise in the **SSP SI-02 statement** and maintain detail in the existing **CM-08 inventory**, **RACI**, **support model**, **ConOps** or **SyOps**. | **6–12 hours** |
| **2. Establish an authoritative flaw workflow** | Ensure scan, test, supplier, incident and code findings enter one controlled vulnerability, defect, risk or POA&M process. | Use the existing **vulnerability tracker**, **defect system**, **service-management platform**, **risk register** or **POA&M**, referenced from the SSP. | **6–16 hours** |
| **3. Define triage, severity and remediation deadlines** | Assess applicability, exploitability, business impact, active exploitation and enterprise deadlines and define escalation and exception rules. | Record the method in the **SSP**, **vulnerability-management approach**, **SyOps**, **security test strategy** or **service-management procedure**. | **8–16 hours** |
| **4. Monitor supplier and dependency fixes** | Subscribe to advisories, assess affected versions, track supplier cases, monitor dependency releases and record support status. | Use the existing **supplier record**, **SBOM**, **dependency alerts**, **CM-08 inventory**, **service review** and **risk register**. | **3–8 hours per month or review cycle** |
| **5. Develop or obtain trusted fixes** | Correct custom code through the SDLC or obtain signed, verified supplier patches, updates and packages from approved sources. | Evidence remains in the normal **source repository**, **supplier case**, **artefact repository**, **release manifest**, **change record** and **release pack**. | **2–8 hours per ordinary fix for coordination, excluding engineering** |
| **6. Test effectiveness and side effects before production** | Reproduce the flaw, test the correction, perform regression, integration, security, installation and rollback checks in a representative environment. | Add evidence to the existing **security test plan**, **regression test report**, **integration test**, **operational acceptance test** and **release evidence pack**. | **6–24 hours per remediation group, excluding extensive test engineering** |
| **7. Use controlled deployment and emergency change** | Deploy approved artefacts and configuration through authorised identities with rollback, deployment evidence and enhanced controls for urgent fixes. | Use the normal **change record**, **release approval**, **deployment history**, **PAM record**, **emergency-change record** and **operational acceptance evidence**. | **4–12 hours per release, excluding deployment engineering** |
| **8. Verify deployment across all affected components** | Confirm production, standby, thick-client, database, integration, image and recovery coverage and identify residual vulnerable versions. | Record coverage in the **deployment report**, **software-distribution record**, **CM-08 inventory**, **scan results**, **release record** and **vulnerability record**. | **4–12 hours per remediation group** |
| **9. Retest and verify closure** | Rerun the original scan, test or exploit; confirm the vulnerable version or condition is absent and preserve evidence. | Retain evidence in the **retest report**, **vulnerability record**, **security test report**, **supplier verification** and **closure approval**. | **2–8 hours per finding or related group** |
| **10. Update baseline, inventory and SBOM** | Record the corrected version, artefact, configuration and dependencies and remove or mark obsolete versions. | Update the existing **CM-02 baseline**, **CM-06 configuration**, **CM-08 inventory**, **SBOM**, **release manifest** and **recovery records**. | **2–6 hours per release** |
| **11. Apply and monitor interim controls where fixes are delayed** | Disable, restrict, isolate, virtually patch or increase monitoring and define expiry and permanent treatment. | Record in the **risk record**, **change ticket**, **SyOps**, **incident record**, **application addendum** and **SSP** where material. | **4–16 hours per issue, excluding implementation** |
| **12. Manage remediation exceptions formally** | Record reason, risk, interim controls, owner, approval, supplier dependency, target date, review and expiry. | Use the existing **risk register**, **POA&M**, **exception workflow**, **problem record** or **application addendum**. | **3–8 hours per exception** |
| **13. Escalate overdue, unsupported and failed remediation** | Report missed deadlines, failed retests, partial deployment, unsupported technology and supplier delay to accountable owners. | Evidence sits in the normal **service review**, **risk report**, **CA-07 posture report**, **supplier escalation** or **governance minutes**. | **2–6 hours per escalation** |
| **14. Perform root-cause analysis for significant or recurring flaws** | Determine why the flaw arose and escaped prevention and convert the result into owned SDLC, design, test, supplier or monitoring improvements. | Record outcomes in the existing **problem record**, **lessons-learned record**, **SDLC backlog**, **risk register**, **test strategy** and **SSP change history**. | **8–24 hours per analysis** |
| **15. Report remediation posture and trends** | Summarise critical flaws, overdue items, exceptions, deployment coverage, supplier delays, unsupported components and recurring causes. | Include in the normal **service review**, **security review**, **risk committee pack**, **CA-07 report** or **SSP status review**. | **4–8 hours per report** |
| **16. Test and review the remediation process** | Verify intake, ownership, deadlines, emergency process, testing, deployment, retest, baseline update, exception expiry and root-cause follow-through. | Capture outcomes in the normal **control assessment**, **annual security review**, **service-improvement plan** or **CA-07 review**. | **8–16 hours per annual review** |

### Indicative total

For a typical internal application with mature enterprise vulnerability and release services, initial application setup is commonly around **80–180 hours**.

Ongoing application coordination, triage, testing, verification and reporting is commonly around **15–50 hours per month**, excluding the engineering effort required to develop fixes and excluding exceptional major upgrades.

A simple commercial application with reliable supplier patching may require less. A custom, legacy, thick-client or supplier-constrained application with many dependencies and manual deployments may require substantially more.

The estimates should not be added mechanically where activities overlap. SI-02 commonly shares evidence and effort with:

- RA-05 vulnerability monitoring and scanning;
- CM-02 baseline configuration;
- CM-05 access restrictions for change;
- CM-06 configuration settings;
- CM-08 component inventory;
- SI-07 software and information integrity;
- SA-11 developer testing;
- CA-07 continuous monitoring;
- IR-05 incident monitoring; and
- CP controls for recovery.

---

## Suggested document placement

To avoid creating disconnected evidence, flaw-remediation information should normally be distributed across established application and SDLC artefacts:

- **SSP:** SI-02 implementation approach, application scope, inherited enterprise patching, ownership, deadlines, testing, deployment, verification, reporting and limitations.
- **ConOps or SyOps:** operational patch windows, emergency treatment, supplier escalation, rollback, user impact and support responsibilities.
- **CM-08 inventory:** components, versions, owners, support status and affected deployments.
- **CM-02 baseline:** approved corrected versions, artefacts and configuration.
- **CM-06 configuration specification:** secure configuration corrections and removal of unsafe defaults.
- **SBOM and dependency records:** vulnerable and corrected package versions.
- **Vulnerability or defect tracker:** flaw, applicability, owner, risk, target date, treatment, deployment and retest.
- **Risk register or POA&M:** delayed remediation, unsupported components, interim controls and accepted residual risk.
- **Supplier records:** advisories, affected versions, support cases, mitigations, target fixes and commitments.
- **Source repository and code review:** custom fixes, peer review and traceability.
- **CI/CD and artefact repository:** automated tests, security gates, approved builds, signatures and provenance.
- **Security test plans and reports:** original reproduction, effectiveness testing, regression and retest.
- **Change and release records:** approval, implementation, rollback, deployment and post-change verification.
- **Software-distribution records:** thick-client package version and deployment coverage.
- **Recovery plan and artefacts:** corrected recovery images, packages, versions and configuration.
- **Incident records:** exploitation assessment, containment and emergency correction where relevant.
- **CA-07 service or posture reviews:** overdue flaws, exceptions, trends, unsupported components and root-cause actions.
- **Problem and lessons-learned records:** root cause and preventive improvements.
- **Application addendum:** supplier restrictions, unsupported components, delayed fixes and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide flaw-remediation and patch policy;
- enterprise vulnerability intelligence;
- enterprise vulnerability-management platforms;
- endpoint and server patching platforms;
- managed Windows EUC operating-system and enterprise-software patching;
- shared server operating-system patching;
- shared database-platform patching;
- shared middleware and infrastructure patching;
- network-device and firewall patching;
- hypervisor and virtualisation patching;
- enterprise change and release platforms;
- corporate emergency-change governance;
- central risk, exception and POA&M tooling;
- enterprise SIEM and SOC operations;
- organisation-wide remediation deadlines;
- corporate supplier and contract escalation; and
- executive-level remediation reporting.

The application team must still:

- identify application-specific affected components;
- assess applicability and business risk;
- obtain or develop corrections;
- test fixes and side effects;
- deploy application changes safely;
- verify full deployment;
- retest the original flaw;
- update baselines, inventories and recovery artefacts;
- manage supplier delays and exceptions;
- conduct root-cause analysis; and
- report application remediation posture.

> **Key dividing line:** the enterprise operates shared patching, intelligence and governance services; the application owns the effective correction and verification of flaws in the business application and every application-specific component on which it depends.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, SI-02 Flaw Remediation.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, SI-02 assessment procedures.
3. National Institute of Standards and Technology, **Summary of Changes: NIST SP 800-53 Release 5.2.0**, including SI-02(07) Root Cause Analysis.
4. National Institute of Standards and Technology, **NIST SP 800-40 Rev. 4, Guide to Enterprise Patch Management Planning: Preventive Maintenance for Technology**.
5. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1**.
6. National Institute of Standards and Technology, **NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems**.
