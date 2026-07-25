# SA-11 Developer Testing and Evaluation — Application Actions

## Purpose

For an IT application, SA-11 means the application must ensure that **security and privacy requirements are tested throughout development and change, using methods appropriate to the application’s technology, risk and attack surface, and that defects are corrected and verified before release or formally accepted as risk**.

Developer testing and evaluation is broader than ordinary functional testing. It should provide evidence that:

- required controls are implemented correctly;
- controls operate as intended;
- security and privacy requirements are met;
- application components interact securely;
- changes have not introduced regressions;
- known weaknesses are detected early;
- credible misuse and attack paths have been considered;
- findings are tracked to closure;
- and the released artefact is the one that was tested.

The enterprise may provide:

- organisation-wide secure development policy;
- approved SDLC and change processes;
- source-control and CI/CD platforms;
- central static, dependency and container-scanning tools;
- enterprise test environments;
- coding standards;
- vulnerability and defect-management platforms;
- corporate identity, PKI, secrets and logging services;
- independent penetration-testing arrangements;
- central risk and exception governance;
- and organisation-wide assurance reporting.

Those capabilities are inherited.

The application remains responsible for ensuring that testing is sufficient for the application’s:

- custom code;
- configured commercial product;
- thick client;
- browser interface;
- APIs;
- database logic;
- files and parsers;
- workflows;
- integrations;
- dependencies;
- application configuration;
- privileged functions;
- security controls;
- business rules;
- and deployment artefacts.

NIST SA-11 requires developers to create and implement a security and privacy assessment plan, perform unit, integration, system and regression testing, produce evidence of execution and results, implement a verifiable flaw-remediation process, and correct identified flaws. Its enhancements cover static code analysis, threat modelling and vulnerability analyses, independent verification of assessment plans and evidence, manual code review, penetration testing, attack-surface reviews and verification of the scope of testing and evaluation. NIST’s current catalogue is SP 800-53 and SP 800-53A Release 5.2.0. NIST SP 800-218 remains the final Secure Software Development Framework Version 1.1, while Version 1.2 is an initial public draft and should not be treated as the final baseline. citeturn851830search1turn851830search6turn851830search20turn851830search36turn851830search42

> **Core principle:** the enterprise provides common development and testing services; the application team defines, performs and retains evidence for the tests needed to prove that its own security controls, business rules and integrations work correctly.

---

## 1. Define the application testing boundary

The application should identify every component whose security and privacy behaviour must be evaluated.

This normally includes:

- custom source code;
- configured commercial products;
- thick-client packages;
- browser applications;
- web and application services;
- APIs;
- administrative consoles;
- support functions;
- database schemas;
- stored procedures;
- database roles;
- message consumers and publishers;
- integration adapters;
- file parsers and converters;
- batch imports and exports;
- report engines;
- scheduled jobs;
- plugins and extensions;
- application configuration;
- service identities;
- certificates and trust material;
- third-party libraries;
- container images;
- build and deployment definitions;
- migration scripts;
- recovery artefacts;
- and application-specific monitoring and logging.

The scope should align with:

- the SSP boundary;
- architecture;
- CM-08 inventory;
- CM-02 baseline;
- SBOM or dependency records;
- interface register;
- data-flow diagrams;
- threat model;
- and release manifest.

## 2. Maintain a security and privacy assessment plan

The application should maintain an assessment plan for development and material changes.

The plan should identify:

- scope;
- objectives;
- security and privacy requirements;
- controls to be tested;
- components;
- test types;
- test environment;
- test data;
- tools;
- responsible roles;
- independence requirements;
- entry criteria;
- exit criteria;
- severity model;
- defect workflow;
- evidence requirements;
- release gates;
- retest requirements;
- limitations;
- and approval.

The plan may be integrated into the ordinary test strategy or release test plan rather than created as a disconnected document.

## 3. Trace tests to security and privacy requirements

Each material requirement should be traceable to one or more tests.

Sources include:

- SSP controls;
- application security requirements;
- privacy requirements;
- threat model;
- architecture decisions;
- role and access model;
- information-flow rules;
- configuration baseline;
- interface requirements;
- secure coding standards;
- supplier security requirements;
- risk treatments;
- penetration-test findings;
- incident lessons;
- and product limitations.

Traceability should demonstrate:

- requirement;
- implementing component;
- test case;
- execution result;
- defect or exception;
- retest;
- and final status.

## 4. Define risk-based test depth

Testing depth should reflect:

- information sensitivity;
- business impact;
- privilege;
- custom-code volume;
- application complexity;
- externally supplied components;
- number and complexity of integrations;
- thick-client functionality;
- file-processing capability;
- workflow importance;
- rate of change;
- history of flaws;
- unsupported technology;
- supplier maturity;
- recovery importance;
- and credible threat scenarios.

A simple internal catalogue application does not need the same test depth as a privileged engineering system handling complex files and approval workflows.

## 5. Establish security test entry criteria

Security testing should not begin until, as appropriate:

- requirements are approved;
- architecture is sufficiently stable;
- threat model is available;
- code or product build is controlled;
- configuration is defined;
- test environment is ready;
- test accounts exist;
- test data exists;
- interfaces are available;
- known blocking defects are resolved;
- tools are configured;
- and the test scope is agreed.

## 6. Establish security test exit criteria

Release or test completion criteria should include:

- planned tests executed;
- required control coverage achieved;
- no unresolved prohibited-severity defects;
- critical and high findings remediated or formally accepted;
- retesting completed;
- security regressions passed;
- evidence retained;
- deviations documented;
- test environment differences assessed;
- release artefact identified;
- and approval recorded.

A percentage of test cases passed is not sufficient if the failed cases affect critical security controls.

## 7. Test throughout the SDLC

Security testing should occur during:

- requirements;
- architecture and design;
- coding;
- component build;
- integration;
- system testing;
- operational acceptance;
- release;
- deployment;
- maintenance;
- and decommissioning.

The application should not defer all security testing until immediately before production release.

## 8. Test security requirements at the earliest practical stage

Examples include:

- review access-control requirements before coding;
- review trust boundaries during architecture;
- test validators in unit tests;
- scan dependencies during build;
- test APIs during integration;
- test workflows during system testing;
- test monitoring during operational acceptance;
- and penetration-test the complete application at appropriate milestones.

Earlier testing normally reduces remediation cost and schedule disruption.

## 9. Perform unit security testing

Unit tests should cover security-relevant functions such as:

- input validation;
- authorisation decisions;
- object ownership;
- workflow transitions;
- cryptographic wrappers;
- token validation helpers;
- file-name handling;
- path normalisation;
- output encoding;
- audit-event creation;
- retention calculations;
- account-state checks;
- configuration parsing;
- and error handling.

Unit tests should include positive, negative and boundary cases.

## 10. Perform component testing

Component tests should verify:

- security configuration;
- access restrictions;
- dependency behaviour;
- parser limits;
- error handling;
- logging;
- secret retrieval;
- certificate validation;
- session handling;
- and safe failure.

Commercial or supplier components should be tested in the application’s actual configuration rather than assumed secure from supplier documentation alone.

## 11. Perform integration security testing

Integration tests should cover:

- identity provider;
- corporate directory;
- APIs;
- database;
- message broker;
- file transfer;
- email;
- logging;
- SIEM;
- malware scanning;
- secrets service;
- certificate service;
- supplier service;
- backup and recovery;
- and connected applications.

Testing should include failure, timeout, invalid data, expired credentials and partial-service conditions.

## 12. Perform system security testing

System testing should examine the complete application across components.

It should verify:

- authentication;
- authorisation;
- information flow;
- least privilege;
- separation of duties;
- input validation;
- session management;
- logging;
- monitoring;
- encryption;
- storage protection;
- remote-access behaviour;
- external-system restrictions;
- flaw remediation;
- retention;
- and recovery.

## 13. Perform regression security testing

Every corrected flaw and material security requirement should have a repeatable regression test where practical.

Regression tests should prevent reintroduction of:

- authentication bypass;
- authorisation failure;
- injection;
- insecure file handling;
- weak session behaviour;
- logging gaps;
- misconfiguration;
- exposed secrets;
- vulnerable dependency;
- workflow bypass;
- and unsafe export.

Security regression tests should run as part of the normal build or release process.

## 14. Test positive and negative behaviour

Security testing should verify both:

- permitted actions succeed; and
- prohibited, malformed and unauthorised actions fail safely.

Examples include:

- authorised user can view an assigned record;
- unauthorised user cannot view it;
- valid workflow transition succeeds;
- skipped transition fails;
- approved file type is accepted;
- mismatched content is rejected;
- valid API request succeeds;
- unknown field is rejected;
- current certificate succeeds;
- expired certificate fails;
- and audit events are produced for both required outcomes.

## 15. Test boundary and edge conditions

Test cases should include:

- minimum and maximum values;
- values just outside allowed ranges;
- empty and null values;
- long input;
- Unicode;
- control characters;
- time and date boundaries;
- expiry;
- concurrent actions;
- duplicate requests;
- retries;
- partial failure;
- resource limits;
- large files;
- nested structures;
- and unexpected sequence.

## 16. Test authentication

Authentication testing should cover:

- corporate federation;
- assertion or token validation;
- issuer;
- audience;
- signature;
- expiry;
- nonce and state;
- identity mapping;
- duplicate identity;
- disabled account;
- MFA or authentication context;
- local fallback;
- password reset where applicable;
- privileged authentication;
- supplier authentication;
- service authentication;
- and failure of the identity service.

## 17. Test authorisation

Authorisation testing should cover:

- role;
- project or tenant scope;
- record ownership;
- object-level access;
- field-level access;
- workflow state;
- privileged function;
- support impersonation;
- service scope;
- API scope;
- direct-object reference;
- hidden fields;
- direct API invocation;
- and administration paths.

The server-side result should be verified, not merely the visibility of a user-interface button.

## 18. Test separation of duties

Testing should attempt to:

- self-approve;
- self-grant privilege;
- combine incompatible roles;
- exploit delegation;
- modify a record after approval;
- bypass workflow through an API;
- use support impersonation to approve;
- replay an approval;
- and use emergency access without review.

## 19. Test information-flow enforcement

Testing should attempt to:

- cross project or tenant boundaries;
- search across restricted scopes;
- use report functions to bypass access;
- export to prohibited destinations;
- alter recipient fields;
- access production data from non-production;
- use integrations to bypass restrictions;
- and infer restricted information through aggregate or error responses.

## 20. Test input validation

Testing should cover:

- type;
- format;
- length;
- range;
- encoding;
- canonicalisation;
- schema;
- unknown fields;
- duplicate fields;
- invalid identifiers;
- cross-field rules;
- file type;
- archive limits;
- business rules;
- and safe failure.

## 21. Test injection resistance

Relevant tests include:

- SQL injection;
- command injection;
- script injection;
- template injection;
- LDAP injection;
- path traversal;
- log injection;
- spreadsheet formula injection;
- server-side request forgery;
- unsafe deserialisation;
- XML attacks;
- and protocol injection.

Testing should verify parameterisation and context-specific output handling, not only blocklists.

## 22. Test session management

Testing should cover:

- session fixation;
- session-token protection;
- rotation;
- inactivity timeout;
- absolute timeout;
- sign-out;
- account disablement;
- role removal;
- concurrent sessions;
- refresh tokens;
- replay;
- session revocation;
- VPN drop and reconnect where applicable;
- and support-impersonation termination.

## 23. Test thick clients

For thick-client applications, testing should include:

- installer and package integrity;
- signature;
- local libraries;
- local storage;
- token storage;
- endpoint configuration;
- server certificate validation;
- protocol manipulation;
- direct API calls;
- direct database attempts;
- local privilege;
- update mechanism;
- offline behaviour;
- cache expiry;
- and obsolete-client rejection.

## 24. Test browser security

Browser testing should include:

- secure cookies;
- cache controls;
- cross-site scripting;
- cross-site request forgery;
- content security policy where used;
- clickjacking protection;
- open redirects;
- sensitive data in URLs;
- browser storage;
- download links;
- cross-origin behaviour;
- and server-side authorisation.

## 25. Test APIs

API testing should include:

- authentication;
- token validation;
- object-level authorisation;
- function-level authorisation;
- excessive data exposure;
- mass assignment;
- schema validation;
- pagination;
- rate limiting;
- replay;
- idempotency;
- deprecated endpoints;
- undocumented endpoints;
- callback restrictions;
- error disclosure;
- and business-logic abuse.

## 26. Test file processing

File and parser testing should cover:

- content/type mismatch;
- malformed files;
- macros and active content;
- archive traversal;
- archive bombs;
- nested archives;
- parser vulnerabilities;
- temporary-file handling;
- malicious content;
- unsafe preview;
- filename handling;
- content-disposition behaviour;
- and unauthorised download.

## 27. Test business logic

Business-logic testing should examine:

- workflow sequence;
- approvals;
- quantity and value limits;
- ownership changes;
- duplicate processing;
- replay;
- timing;
- expiry;
- delegation;
- status manipulation;
- bulk operations;
- reporting;
- and combinations of legitimate functions that create an unauthorised outcome.

## 28. Test privileged functions

Testing should cover:

- role administration;
- account administration;
- security configuration;
- identity trust;
- logging configuration;
- export controls;
- plugin installation;
- script execution;
- database repair;
- backup and restore;
- retention changes;
- certificate and secret references;
- and emergency access.

## 29. Test service identities and integrations

Testing should confirm:

- caller identity;
- scope;
- endpoint;
- message topic;
- schema;
- replay controls;
- privilege;
- credential rotation;
- unexpected caller denial;
- environment separation;
- and safe behaviour when dependencies fail.

## 30. Test security logging

Tests should verify that significant activity produces:

- correct event;
- correct identity;
- correct object;
- correct outcome;
- correct correlation;
- correct timestamp;
- no secret leakage;
- central receipt;
- and required alerting or monitoring.

## 31. Test protection of information at rest and in transit

Testing should verify:

- approved encrypted protocols;
- certificate validation;
- no clear-text fallback;
- encrypted storage where required;
- protected exports;
- safe local cache;
- backup protection;
- key availability;
- and safe response to cryptographic failure.

## 32. Test retention and disposal

Testing should verify:

- retention triggers;
- held-record exclusion;
- archive;
- purge;
- attachment disposal;
- cache and index removal;
- export expiry;
- audit logging;
- and treatment after backup restore.

## 33. Test secure configuration

Configuration testing should assess:

- approved values;
- missing values;
- defaults;
- environment separation;
- logging;
- session settings;
- file types;
- endpoints;
- certificate trust;
- secret references;
- debug mode;
- and unsafe fallback.

Configuration should fail safely where required.

## 34. Perform static code analysis

Where source code is available, static analysis should be used proportionately to identify:

- injection;
- unsafe API use;
- insecure cryptography;
- hard-coded secrets;
- path traversal;
- deserialisation;
- memory-safety issues;
- error handling;
- race conditions;
- insecure randomness;
- validation gaps;
- and other language-specific weaknesses.

Static analysis should be:

- configured for the technology;
- integrated into the build where practical;
- version controlled;
- tuned;
- triaged;
- linked to defects;
- rerun after correction;
- and periodically reviewed for coverage.

Tool output is not evidence of correction until findings are assessed and treated.

## 35. Scan for secrets

Secret scanning should examine:

- source code;
- repository history;
- configuration;
- scripts;
- build files;
- test fixtures;
- container definitions;
- packages;
- documentation;
- and generated artefacts.

Discovered credentials should be revoked or rotated, not merely deleted from the latest file.

## 36. Perform software-composition analysis

The application should identify and assess:

- direct dependencies;
- transitive dependencies;
- package versions;
- known vulnerabilities;
- package provenance;
- licence concerns;
- support status;
- and malicious or unexpected packages.

Results should link to:

- SBOM;
- CM-08 inventory;
- RA-05;
- SI-02;
- and release decisions.

## 37. Scan container and deployment artefacts

Where used, testing should cover:

- base images;
- installed packages;
- application libraries;
- image configuration;
- embedded secrets;
- unnecessary tools;
- privilege;
- exposed ports;
- user identity;
- health checks;
- immutable identifiers;
- and signature or provenance.

The deployed image digest should match the tested and approved artefact.

## 38. Perform dynamic application security testing

Dynamic testing should exercise the running application to identify:

- injection;
- session issues;
- authentication weaknesses;
- configuration errors;
- information disclosure;
- file handling;
- and protocol problems.

Dynamic tools should be used safely and should not replace manual business-logic and authorisation testing.

## 39. Use interactive testing where appropriate

Interactive application security testing or runtime instrumentation may supplement static and dynamic analysis by identifying:

- executed vulnerable paths;
- data flow;
- unsafe APIs;
- and runtime configuration issues.

The application should treat tool findings as evidence to be triaged, not as automatic proof of exploitability.

## 40. Perform fuzz testing where risk warrants

Fuzzing is particularly useful for:

- file parsers;
- protocol handlers;
- APIs;
- message consumers;
- deserialisation;
- image processing;
- archive extraction;
- document conversion;
- and thick-client protocols.

Fuzzing should be:

- authorised;
- isolated;
- resource bounded;
- reproducible;
- linked to crash triage;
- and followed by correction and regression testing.

## 41. Perform threat modelling and vulnerability analysis

Threat modelling should identify:

- assets;
- actors;
- trust boundaries;
- entry points;
- privileged paths;
- abuse cases;
- data flows;
- external dependencies;
- security assumptions;
- mitigations;
- and residual risks.

It should be reviewed after:

- major design change;
- new integration;
- new privilege;
- new data type;
- incident;
- and significant vulnerability.

SA-11 enhancements explicitly address threat modelling and vulnerability analyses.

## 42. Review the attack surface

Attack-surface review should identify:

- exposed interfaces;
- enabled functions;
- ports and services;
- APIs;
- privileged consoles;
- file types;
- callbacks;
- plugins;
- supplier paths;
- direct database paths;
- local thick-client surfaces;
- and obsolete endpoints.

The application should remove or restrict unnecessary attack surface under CM-07.

## 43. Perform manual code review

Manual review should be used for high-risk or complex areas where automated tools are weak.

Examples include:

- authentication;
- authorisation;
- cryptography;
- session management;
- business logic;
- workflow;
- service identities;
- file parsers;
- unsafe deserialisation;
- privileged functions;
- security configuration;
- and fixes for critical flaws.

Reviewers should use documented criteria and record material findings.

## 44. Use peer review for security-relevant changes

Security-relevant changes should receive review by a competent person other than the author where practical.

The review should consider:

- requirement;
- design;
- code;
- tests;
- error handling;
- logs;
- configuration;
- dependencies;
- and possible bypasses.

## 45. Conduct developer penetration testing where appropriate

Developer or pre-release penetration testing can identify chained and runtime weaknesses before independent CA-08 testing.

It should focus on:

- complete attack paths;
- authentication and authorisation;
- business logic;
- file processing;
- APIs;
- thick clients;
- administration;
- and integration trust.

Developer penetration testing does not normally replace independent CA-08 testing where that control applies.

## 46. Verify the scope of testing and evaluation

The application should confirm that testing actually covered:

- all material components;
- all material roles;
- all material environments;
- all high-risk functions;
- all security controls;
- all critical interfaces;
- all supported client types;
- all relevant file types;
- and all release artefacts.

Scope verification should identify:

- exclusions;
- unavailable components;
- untested roles;
- environment differences;
- unsupported tools;
- and residual risk.

## 47. Independently review assessment plans and evidence where required

For higher-risk applications or where the selected SA-11 enhancement applies, a suitably independent reviewer should assess:

- completeness of the test plan;
- appropriateness of methods;
- coverage;
- evidence quality;
- severity decisions;
- exceptions;
- and closure.

Independence may come from:

- application security;
- assurance;
- independent test team;
- security architect;
- or competent supplier personnel separate from the developers.

## 48. Control test environments

Test environments should:

- be representative;
- be separated from production;
- use approved access;
- use separate credentials;
- use controlled configuration;
- have appropriate logging;
- use safe test data;
- support restoration;
- and be protected from becoming an unmanaged production-like store.

Differences from production should be documented and assessed.

## 49. Control test data

Testing should use:

- synthetic data;
- anonymised data;
- masked data;
- or minimum authorised production-derived data.

Where production data is used:

- obtain approval;
- restrict access;
- protect storage;
- define retention;
- prohibit uncontrolled export;
- and delete after use.

## 50. Test in production only when explicitly authorised

Production testing should have:

- approved scope;
- approved techniques;
- approved window;
- test identities;
- monitoring;
- stop conditions;
- rollback;
- incident coordination;
- data restrictions;
- and clean-up.

Ordinary developer testing should normally use representative non-production environments.

## 51. Protect test tools and evidence

The application should ensure that:

- test tools are approved;
- exploit code is controlled;
- credentials are protected;
- screenshots are minimised;
- findings are stored securely;
- source code is not uploaded to unapproved services;
- production records are not copied unnecessarily;
- and reports are access-restricted.

## 52. Use controlled builds

Testing should be performed against a controlled build with:

- source revision;
- dependency versions;
- configuration;
- build environment;
- build identifier;
- artefact hash or digest;
- and provenance.

The release decision should identify the exact tested artefact.

## 53. Ensure test-to-release traceability

The application should demonstrate:

- tested source revision;
- tested dependencies;
- tested configuration;
- tested database migration;
- tested thick-client package;
- approved artefact;
- deployed artefact;
- and environment.

A rebuilt artefact after testing should trigger proportionate revalidation.

## 54. Protect the build pipeline

Testing and release assurance should consider:

- branch controls;
- pipeline permissions;
- secrets;
- runner images;
- build tools;
- dependency sources;
- security gates;
- signing;
- artefact promotion;
- approval;
- and audit logging.

A secure application cannot be proven if the tested artefact can be replaced after approval.

## 55. Define tool configuration as controlled configuration

Security test tools should have controlled:

- rules;
- versions;
- severity thresholds;
- exclusions;
- suppression lists;
- scan scope;
- credentials;
- and output handling.

Changes should be authorised and reviewed.

## 56. Manage false positives

False-positive decisions should include:

- finding reference;
- affected component;
- technical basis;
- supporting evidence;
- reviewer;
- approval;
- expiry or revalidation trigger;
- and impact if assumptions change.

Suppressions should be narrow and periodically reviewed.

## 57. Manage false negatives and tool limitations

The application should document where tools cannot adequately assess:

- business logic;
- proprietary code;
- thick-client protocols;
- generated code;
- runtime configuration;
- encrypted traffic;
- supplier binaries;
- obfuscated code;
- unsupported languages;
- and complex authorisation.

Alternative testing should be used where risk warrants.

## 58. Record defects consistently

Each security or privacy defect should include:

- unique identifier;
- source;
- affected component;
- affected version;
- requirement or control;
- description;
- severity;
- exploitability;
- business impact;
- owner;
- target date;
- treatment;
- planned release;
- test evidence;
- exception;
- retest;
- and closure.

Use the normal defect, vulnerability, risk or POA&M system.

## 59. Prioritise findings using application context

Prioritisation should consider:

- technical severity;
- exploitability;
- active exploitation;
- privilege;
- data sensitivity;
- business impact;
- attack-path reachability;
- affected user population;
- supplier dependency;
- detectability;
- compensating controls;
- and release timing.

## 60. Establish release gates

Release gates should define when a build cannot proceed.

Examples include:

- unresolved critical flaw;
- unresolved high flaw without approved exception;
- failed authentication test;
- failed authorisation test;
- exposed secret;
- vulnerable unsupported dependency;
- missing security event;
- failed certificate validation;
- incomplete test evidence;
- untested material change;
- or mismatch between tested and release artefact.

## 61. Correct identified flaws

The application should:

- assign an owner;
- correct the root cause;
- update code or configuration;
- update tests;
- review the correction;
- rerun relevant analysis;
- perform regression testing;
- deploy through controlled change;
- and verify closure.

SA-11 requires a verifiable flaw-remediation process and correction of identified flaws.

## 62. Retest corrections

Retesting should verify:

- original weakness is removed;
- alternate paths are addressed;
- all affected components are corrected;
- no security regression exists;
- logging works;
- configuration is correct;
- and the corrected artefact is the release candidate.

## 63. Search for related weaknesses

When a material flaw is found, search for:

- repeated code pattern;
- same dependency;
- same configuration;
- same API pattern;
- same role logic;
- same file parser;
- same supplier component;
- and same weakness in related applications.

## 64. Perform root-cause analysis for significant or recurring defects

Root-cause analysis should consider:

- missing requirement;
- insecure design;
- coding pattern;
- insufficient review;
- missing test;
- tool gap;
- supplier weakness;
- configuration drift;
- incomplete threat model;
- training gap;
- and ineffective previous remediation.

The outcome should create preventive improvements.

## 65. Retain execution evidence

Evidence should include, as appropriate:

- test plan;
- test case;
- date;
- tester;
- environment;
- build identifier;
- configuration;
- tools and versions;
- input;
- expected result;
- actual result;
- logs;
- screenshots where necessary;
- defects;
- retest;
- and approval.

Evidence should be sufficient for assessment without preserving unnecessary sensitive information.

## 66. Retain automated pipeline evidence

Relevant evidence includes:

- pipeline run;
- source revision;
- build identifier;
- SAST result;
- SCA result;
- secret scan;
- container scan;
- unit and integration results;
- security-gate outcome;
- approval;
- signed artefact;
- and release promotion.

## 67. Protect test evidence

Security test records may contain:

- vulnerabilities;
- credentials;
- source code;
- attack payloads;
- architecture;
- restricted records;
- and supplier weaknesses.

They should be:

- access-restricted;
- stored in approved systems;
- encrypted in transit;
- retained according to policy;
- redacted where appropriate;
- and securely disposed of.

## 68. Measure testing effectiveness

Useful measures include:

- security requirements with tests;
- test coverage of critical controls;
- critical and high findings;
- escaped defects;
- reopened findings;
- repeated weakness classes;
- mean time to remediate;
- security-gate failures;
- false-positive rates;
- dependency risk;
- untested changes;
- and percentage of releases with complete evidence.

Metrics should drive improvement rather than encourage superficial closure.

## 69. Review testing effectiveness after incidents and penetration tests

The application should ask:

- should an existing test have detected the issue;
- was the requirement missing;
- was the test too narrow;
- was the environment unrepresentative;
- was a tool misconfigured;
- was evidence ignored;
- did a release gate fail;
- and what regression test should be added.

## 70. Review supplier testing evidence

For commercial or supplier-developed components, the application should obtain and assess proportionate evidence such as:

- supplier test summary;
- secure development description;
- vulnerability-management process;
- code-analysis evidence;
- penetration-test summary;
- dependency management;
- known limitations;
- remediation commitments;
- and release security notes.

Supplier evidence does not eliminate the need to test the product in the application’s own configuration and business context.

## 71. Define acceptance criteria for supplier components

Supplier components should meet defined criteria for:

- supported version;
- known vulnerabilities;
- secure configuration;
- authentication integration;
- logging;
- access control;
- encryption;
- update mechanism;
- file handling;
- test evidence;
- and remediation support.

## 72. Test configured commercial products

Testing should examine:

- enabled modules;
- disabled functionality;
- roles;
- workflows;
- APIs;
- local accounts;
- supplier access;
- file types;
- exports;
- logging;
- certificates;
- and configuration.

A secure base product can become insecure through configuration or customisation.

## 73. Test application upgrades and patches

Upgrades should be tested for:

- changed defaults;
- new features;
- new connectors;
- new APIs;
- changed roles;
- changed logging;
- new telemetry;
- dependency changes;
- schema changes;
- data migration;
- and security regression.

## 74. Test recovery and rollback

Testing should verify:

- restored configuration;
- restored data;
- security controls;
- identities;
- certificates;
- secrets;
- logging;
- supported versions;
- and prevention of vulnerable-version reintroduction.

## 75. Integrate testing with continuous monitoring

CA-07 should track:

- planned testing;
- overdue testing;
- open findings;
- untested material changes;
- supplier evidence;
- release-gate exceptions;
- recurring weaknesses;
- and test-process improvements.

## 76. Review and update the testing approach periodically

The application should review its assessment plan after:

- major release;
- architecture change;
- new technology;
- incident;
- penetration test;
- recurring flaw;
- supplier change;
- policy change;
- tool change;
- and significant threat change.

## 77. Manage testing limitations and exceptions

Where testing cannot achieve the expected scope, record:

- untested component;
- missing test type;
- reason;
- affected requirement;
- risk;
- alternative assurance;
- compensating controls;
- owner;
- approval;
- supplier constraint;
- remediation plan;
- review date;
- and expiry.

Examples include:

- no source code for a commercial product;
- unsupported static-analysis language;
- unavailable representative integration;
- unsafe production test;
- no test account for a privileged function;
- thick-client protocol not supported by tools;
- supplier refusal to provide evidence;
- or legacy code without automated tests.

The limitation should be visible in the application addendum or risk process.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses enterprise source control, CI/CD, defect management, SAST, SCA, test environments and change processes. They exclude ordinary functional test effort, independent penetration-testing fees and the engineering required to correct defects.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated application-team effort |
|---|---|---|---:|
| **1. Define the security and privacy assessment plan** | Identify scope, requirements, test types, environments, tools, roles, evidence, severity, gates, retest and limitations. | Summarise in the **SSP SA-11 statement** and maintain detail in the existing **test strategy**, **security test plan**, **SDLC plan**, **ConOps** or **SyOps**. | **12–24 hours** |
| **2. Establish traceability from requirements to tests** | Link SSP controls, security requirements, threat scenarios, roles, interfaces and risks to test cases and outcomes. | Use the existing **requirements repository**, **traceability matrix**, **test-management system**, **security backlog** and **release evidence pack**. | **12–28 hours** |
| **3. Implement unit and component security tests** | Test validators, authorisation, workflows, token handling, file paths, audit events, configuration and failure behaviour. | Evidence remains in the **source repository**, **unit-test results**, **component-test report**, **CI/CD history** and **defect tracker**. | **24–60 hours initially** |
| **4. Implement integration and system security tests** | Test identity, APIs, database, files, messaging, secrets, certificates, logging, exports and dependency failure across the complete application. | Retain evidence in the **integration test plan**, **system/security test report**, **operational acceptance test** and **release pack**. | **32–80 hours initially** |
| **5. Implement security regression tests** | Turn material security requirements and corrected defects into repeatable automated or controlled regression cases. | Use the existing **test repository**, **CI/CD pipeline**, **defect record**, **release checklist** and **test report**. | **20–50 hours initially** |
| **6. Perform static code and secret analysis** | Run appropriately configured SAST and secret scanning, triage results, correct findings and verify no valid credentials remain exposed. | Evidence sits in the **pipeline results**, **security scan reports**, **defect tracker**, **exception record** and **release gate history**. | **8–24 hours initially; 2–8 hours per release for triage** |
| **7. Perform dependency and artefact analysis** | Run SCA, container or package scans, maintain dependency/SBOM records and link findings to RA-05 and SI-02. | Use the existing **SCA results**, **SBOM**, **CM-08 inventory**, **artefact repository**, **vulnerability tracker** and **release evidence**. | **8–20 hours initially; 2–8 hours per release** |
| **8. Perform threat modelling and attack-surface review** | Identify assets, actors, trust boundaries, abuse cases, mitigations, exposed interfaces and unnecessary functions. | Record in the **threat model**, **security architecture**, **CM-07 review**, **risk assessment**, **security backlog** and **SSP**. | **16–36 hours initially; 4–12 hours per major change** |
| **9. Perform manual review of high-risk code and configuration** | Review authentication, authorisation, cryptography, files, sessions, workflows, privileged functions and critical fixes. | Retain evidence in the **pull request**, **code-review record**, **security design review**, **change record** and **defect tracker**. | **8–24 hours per major release** |
| **10. Perform dynamic, fuzz or developer penetration testing where appropriate** | Exercise running components, parsers, APIs, thick clients and business logic beyond automated unit and static checks. | Capture outcomes in the **DAST report**, **fuzzing results**, **developer penetration-test report**, **defect system** and **retest evidence**. | **16–48 hours per major cycle** |
| **11. Define and enforce release security gates** | Block release for prohibited findings, exposed secrets, failed critical controls, unsupported vulnerable dependencies or incomplete evidence. | Record gates in the **pipeline configuration**, **release policy**, **change approval**, **exception process** and **release evidence pack**. | **8–20 hours initially** |
| **12. Verify test scope and release artefact** | Confirm material components, roles, functions and interfaces were tested and that the approved artefact matches the tested build. | Use the **test completion report**, **release manifest**, **artefact digest/signature**, **scope review**, **CM-02 baseline** and **operational acceptance record**. | **6–14 hours per major release** |
| **13. Track, remediate and retest findings** | Record defects, assign owners and deadlines, correct root causes, rerun tests and retain closure evidence. | Use the normal **defect tracker**, **vulnerability tracker**, **risk register**, **POA&M**, **change record** and **retest report**. | **2–6 hours per finding for coordination and evidence, excluding correction** |
| **14. Retain and protect execution evidence** | Preserve plans, results, tool versions, build IDs, environments, defects, approvals and retests in approved repositories. | Evidence remains in the **test-management system**, **CI/CD history**, **artefact repository**, **release pack**, **defect system** and **SSP references**. | **6–16 hours per major release** |
| **15. Review effectiveness and improve testing** | Analyse escaped and recurring defects, incident and penetration-test lessons, tool gaps, false positives and untested risks. | Record outcomes in the **lessons-learned record**, **problem record**, **SDLC improvement backlog**, **threat model**, **CA-07 report** and **governance review**. | **8–20 hours per review** |
| **16. Document and manage testing limitations** | Record unavailable source, unsupported tools, missing environments, unsafe tests or supplier evidence gaps with alternative assurance and expiry. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP SA-11 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internally developed or materially configured application with mature enterprise development tooling, initial application security-testing setup is commonly around **220–500 hours**.

Ongoing application-team effort is commonly around **25–80 hours per major release**, excluding:

- ordinary functional testing;
- independent penetration-testing fees;
- significant defect remediation;
- large test-environment construction;
- and extensive supplier assurance activity.

A simple commercial application with little customisation may require less. A custom, thick-client, API-heavy, file-processing or workflow-intensive application with many integrations may require substantially more.

The estimates should not be added mechanically where activities overlap. SA-11 commonly shares implementation and evidence with:

- CA-08 penetration testing;
- RA-05 vulnerability monitoring;
- SI-02 flaw remediation;
- SI-10 input validation;
- CM-02 baseline configuration;
- CM-05 access restrictions for change;
- CM-06 configuration settings;
- CM-07 least functionality;
- CM-08 component inventory;
- AU-02 event logging;
- SI-04 system monitoring;
- SA-15 development process, standards and tools;
- and CA-07 continuous monitoring.

---

## Suggested document placement

To avoid creating disconnected evidence, developer-testing information should normally be distributed across established application and SDLC artefacts:

- **SSP:** SA-11 implementation approach, inherited enterprise tools, test scope, methods, gates, findings treatment and limitations.
- **SDLC or development plan:** security activities, roles, tool use, review points and release criteria.
- **Security and privacy assessment plan:** components, controls, methods, environments, evidence, severity and retest.
- **Requirements repository:** traceability from security and privacy requirements to implementation and tests.
- **Threat model:** assets, actors, trust boundaries, abuse cases, mitigations and test implications.
- **Security architecture:** attack surface, control placement, interfaces and high-risk components.
- **Test-management system:** unit, component, integration, system, regression, security and recovery test cases and results.
- **Source repository:** unit tests, peer review, manual security review and traceability.
- **CI/CD platform:** SAST, secret scanning, SCA, container scanning, automated tests, gates and artefact promotion.
- **SBOM and CM-08 inventory:** tested dependency and component versions.
- **Defect and vulnerability systems:** findings, severity, owners, deadlines, treatment, exceptions and closure.
- **Risk register or POA&M:** accepted or delayed findings and test limitations.
- **Release evidence pack:** build ID, source revision, tool outputs, test results, approvals, artefact digest and deployed version.
- **Operational acceptance test:** identity, logging, monitoring, backup, recovery, configuration and production-readiness evidence.
- **Penetration-test and fuzzing records:** scope, findings, remediation and retest.
- **Supplier assurance records:** product testing, known limitations, vulnerability process and remediation commitments.
- **Problem and lessons-learned records:** root cause and preventive improvements.
- **CA-07 reviews:** open findings, testing status, untested changes, recurring weaknesses and process improvements.
- **Application addendum:** supplier, legacy, environment and tooling limitations.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide secure-development policy;
- corporate SDLC and change process;
- enterprise source-control and CI/CD platforms;
- centrally procured SAST, SCA, secret-scanning and container-scanning tools;
- enterprise test-management and defect platforms;
- organisation-wide secure coding standards;
- central vulnerability-management process;
- approved development and test infrastructure;
- enterprise penetration-testing framework;
- corporate risk and exception governance;
- supplier procurement and contractual standards;
- central assurance methodology;
- and organisation-wide security training.

The application team must still:

- define application-specific security test scope;
- trace requirements to tests;
- test custom code, configuration, workflows, files, APIs and integrations;
- configure and triage enterprise tools correctly;
- perform manual and business-logic testing;
- verify all material roles and attack paths;
- enforce release gates;
- correct and retest defects;
- prove that the tested artefact is the released artefact;
- retain evidence;
- and formally manage application-specific test gaps.

> **Key dividing line:** the enterprise provides the development governance, platforms and common security-testing tools; the application team defines and executes the tests needed to prove that its particular design, code, configuration and business behaviour are secure.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, SA-11 Developer Testing and Evaluation.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, SA-11 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1: Recommendations for Mitigating the Risk of Software Vulnerabilities**.
4. National Institute of Standards and Technology, **NIST SP 800-115, Technical Guide to Information Security Testing and Assessment**.
5. National Institute of Standards and Technology, **NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems**.
6. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, current SP 800-53 and SP 800-53A catalogues.
