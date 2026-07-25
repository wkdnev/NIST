# CA-08 Penetration Testing — Application Actions

## Purpose

For an IT application, CA-08 means the application must undergo **authorised, risk-based penetration testing that actively attempts to bypass or defeat application security controls**, with findings analysed, remediated, retested and incorporated into the application’s risk and continuous-monitoring processes.

Penetration testing is not the same as:

- routine vulnerability scanning;
- automated code scanning;
- configuration checking;
- compliance review;
- a functional test;
- a code review;
- a generic infrastructure scan; or
- asking a supplier whether the product is secure.

Those activities are valuable, but penetration testing goes further by using attacker-style techniques to determine whether weaknesses can be combined into a credible compromise of the application, its information, its users or its supporting business processes.

The enterprise may provide:

- organisation-wide penetration-testing policy;
- an approved testing supplier or internal red team;
- tester vetting and contractual arrangements;
- standard rules-of-engagement templates;
- enterprise test governance;
- network and infrastructure testing;
- central vulnerability and risk-management platforms;
- incident-response coordination;
- legal, privacy and supplier governance;
- central SIEM and SOC support; and
- organisation-wide reporting and assurance.

Those capabilities are inherited.

The application remains responsible for ensuring that the test is meaningful for the complete application. This includes:

- defining the application scope and attack surface;
- identifying critical business functions and abuse cases;
- ensuring representative roles, accounts, interfaces and data are available;
- including browser, thick-client, API, file, workflow, database and integration paths as applicable;
- identifying high-risk exclusions;
- preparing the application and support teams;
- agreeing safe but realistic rules of engagement;
- providing architecture and business context;
- ensuring findings are technically and contextually accurate;
- assigning remediation;
- verifying fixes through retesting;
- assessing residual risk;
- updating the SSP, risk records and security backlog; and
- using lessons learned to improve design, testing and monitoring.

NIST CA-08 requires penetration testing at an organisation-defined frequency and on organisation-defined systems or components. The control discussion describes penetration testing as specialised assessment that attempts to circumvent or defeat security features and may include networks, applications, hardware, software and firmware. NIST SP 800-115 provides guidance for planning, conducting, analysing and reporting technical security tests and assessments. NIST currently lists SP 800-53 and SP 800-53A Release 5.2.0 in its Cybersecurity and Privacy Reference Tool. 

> **Core principle:** the enterprise provides the testing governance and independent capability; the application team ensures that the right application is tested in the right way, that the test reflects realistic business and technical attack paths, and that every material finding is treated and verified.

---

## 1. Define the application penetration-testing scope

The application should define the complete system boundary to be tested.

The scope should consider:

- browser application;
- thick client;
- application services;
- APIs;
- administrative interfaces;
- support interfaces;
- databases and application-owned schemas;
- message queues and event consumers;
- file upload and processing;
- batch imports and exports;
- report generation;
- scheduled jobs;
- integrations;
- identity and federation integration;
- role and project boundaries;
- service identities;
- privileged functions;
- supplier modules;
- plugins and extensions;
- application-specific network services;
- recovery interfaces;
- non-production test environment;
- production validation where separately authorised;
- build and deployment paths where included; and
- application-specific dependencies that materially affect security.

The scope should align with:

- the SSP system boundary;
- the architecture;
- CM-08 inventory;
- CM-02 baseline;
- data-flow diagrams;
- interface catalogue;
- role model;
- RA-05 vulnerability scope; and
- current deployment records.

## 2. Define the penetration-testing objective

The application should state what the test is intended to establish.

Objectives may include determining whether an attacker can:

- gain unauthorised access;
- bypass authentication;
- bypass MFA or federation controls;
- escalate privilege;
- cross project, tenant, case or information boundaries;
- approve their own work;
- bypass separation of duties;
- access another user’s records;
- extract restricted information;
- alter authoritative records;
- execute code;
- upload malicious content;
- compromise a thick client;
- abuse an API;
- impersonate another user;
- misuse support functions;
- obtain service credentials;
- alter security configuration;
- evade logging;
- compromise an integration;
- pivot between application tiers;
- cause significant service disruption;
- exploit recovery or fallback functionality;
- use a low-privilege foothold to reach privileged functions; or
- combine several moderate weaknesses into a high-impact compromise.

A test objective such as “perform an OWASP test” is too vague on its own.

## 3. Use a risk-based test frequency

The application should follow organisation-defined testing frequency and request additional testing when risk warrants it.

Factors include:

- information sensitivity;
- business or mission impact;
- privilege;
- external or remote access;
- number of users;
- supplier involvement;
- application complexity;
- rate of change;
- custom code;
- thick-client functionality;
- API exposure;
- history of weaknesses;
- regulatory or contractual requirements;
- major architectural change;
- new authentication or authorisation model;
- new integration;
- new file-processing capability;
- significant product upgrade;
- migration;
- major incident;
- material vulnerability;
- previous high-risk finding; and
- long periods without independent testing.

A common pattern is periodic testing plus event-driven testing after material change. The authoritative frequency should be the enterprise-defined value recorded in the SSP or assurance plan.

## 4. Trigger additional penetration testing after material change

The application should consider additional or targeted testing after:

- major release;
- new browser or thick-client interface;
- new API;
- new privileged function;
- new supplier module;
- identity-provider migration;
- role-model redesign;
- new data segregation model;
- new upload or conversion function;
- new message or integration path;
- major database change;
- product or framework upgrade;
- significant cloud, hosting or platform migration;
- introduction of remote access;
- new support impersonation;
- new export function;
- new offline capability;
- major remediation;
- serious incident; or
- material change to the application threat model.

The application should not wait for the next routine cycle where the changed attack surface is high risk.

## 5. Choose the appropriate assessment style

The application should agree whether the test is:

- **black-box** — little or no internal information is provided;
- **grey-box** — selected architecture, accounts and design information are provided;
- **white-box** — detailed architecture, code, configuration and credentials are available;
- **authenticated** — testers receive one or more user roles;
- **unauthenticated** — testers begin without valid credentials;
- **announced** — operational teams know the timing;
- **partially unannounced** — selected detection or response elements are tested;
- **production** — tightly controlled testing of the live service;
- **non-production** — realistic testing in a representative environment;
- **targeted** — focused on specific functions or previous findings; or
- **broad** — covers the main application attack surface.

For most internal business applications, a well-prepared grey-box authenticated test provides more useful depth than a purely black-box scan-like exercise.

## 6. Ensure tester independence and competence

The tester should be sufficiently independent of the people who designed, built or operate the application.

The application owner should confirm:

- tester competence;
- relevant application-security experience;
- thick-client experience where applicable;
- API testing capability;
- business-logic testing capability;
- knowledge of the relevant technology stack;
- suitable vetting and confidentiality arrangements;
- conflict-of-interest management;
- approved tools and techniques;
- evidence-handling arrangements;
- professional indemnity or contractual protections where applicable; and
- a clear reporting and escalation route.

Developer testing is useful, but it is not normally a substitute for independent CA-08 penetration testing.

## 7. Define tester access and information

The application should provide enough information for a meaningful test while preserving independence.

Useful inputs may include:

- system context;
- architecture;
- data flows;
- trust boundaries;
- component inventory;
- test URLs and endpoints;
- API specifications;
- thick-client package;
- supported client version;
- test accounts;
- role descriptions;
- project or data partitions;
- workflow descriptions;
- file specifications;
- known exclusions;
- privileged functions;
- supplier interfaces;
- authentication flow;
- support model;
- previous findings;
- threat model;
- test-data guide;
- points of contact; and
- stop conditions.

The tester should not need to reverse-engineer basic business context before they can examine the important risks.

## 8. Provide representative accounts and roles

The test should include representative identities such as:

- unauthenticated user;
- ordinary user;
- read-only user;
- author;
- reviewer;
- approver;
- project member;
- user from another project;
- privileged application administrator;
- support user;
- supplier user;
- temporary user;
- service or API client;
- disabled or expired user;
- user with multiple roles; and
- emergency or fallback account where specifically in scope.

The application should provide the minimum safe number of test identities while ensuring that role boundaries can be tested properly.

## 9. Provide representative projects, records and data partitions

Where the application separates information by project, programme, tenant, case, department or classification, the test environment should include:

- at least two distinct information partitions;
- records owned by different users;
- records at different workflow stages;
- records with different sensitivity;
- parent and child relationships;
- attachments;
- restricted records;
- archived or closed records;
- delegated access;
- expired access; and
- cross-partition references where the product supports them.

Without representative segmentation, testers cannot meaningfully test horizontal access control or information-flow enforcement.

## 10. Include authentication testing

The test should assess, where relevant:

- federation flow;
- token and assertion validation;
- issuer;
- audience;
- signature;
- expiry;
- nonce and state;
- redirect and callback handling;
- identity mapping;
- duplicate identity handling;
- local accounts;
- fallback accounts;
- password reset;
- session creation;
- MFA or authentication context;
- step-up authentication;
- privileged authentication;
- disabled accounts;
- session revocation;
- thick-client authentication; and
- direct API calls.

The tester should not attempt to defeat enterprise MFA infrastructure unless that is separately authorised. The application-layer consumption and enforcement of MFA or identity claims should still be tested.

## 11. Include authorisation testing

The test should attempt to bypass:

- role restrictions;
- object-level access;
- project or tenant boundaries;
- record ownership;
- field-level access;
- workflow state;
- privileged functions;
- administrator restrictions;
- support impersonation controls;
- export restrictions;
- direct-object references;
- hidden user-interface restrictions;
- API scopes;
- service identity restrictions; and
- production versus non-production separation.

The application should assume that requests can be created without the official user interface.

## 12. Include separation-of-duties testing

Where AC-05 applies, the test should attempt to:

- approve the tester’s own record;
- use two roles to circumvent a conflict;
- exploit delegation;
- exploit nested group membership;
- replay an earlier approval;
- alter a record after approval;
- use support impersonation to approve;
- modify the approver field;
- bypass workflow stages through APIs;
- self-assign privilege;
- use an alternate identity mapping; and
- exploit emergency override.

## 13. Include information-flow testing

Where AC-04 applies, the test should attempt to:

- access another project’s records;
- search across partitions;
- obtain data through reports;
- exploit export functions;
- manipulate recipient or destination fields;
- obtain restricted data through notifications;
- use APIs to cross information boundaries;
- exploit indirect references;
- infer sensitive information through aggregation;
- obtain data through logs or errors;
- access production data from non-production;
- abuse support functions; and
- redirect integration output.

## 14. Include input-validation and injection testing

Testing should cover, as relevant:

- SQL injection;
- command injection;
- script injection;
- template injection;
- path traversal;
- unsafe deserialisation;
- server-side request forgery;
- XML-related attacks;
- log injection;
- spreadsheet formula injection;
- malformed JSON or XML;
- duplicate parameters;
- mass assignment;
- Unicode and encoding issues;
- oversized input;
- business-rule manipulation;
- file upload; and
- parser abuse.

## 15. Include session-management testing

The test should examine:

- session fixation;
- session token strength;
- cookie or token protection;
- logout;
- inactivity timeout;
- absolute timeout;
- concurrent sessions;
- privilege change during a session;
- role removal;
- account disablement;
- session replay;
- token leakage;
- session tokens in URLs or logs;
- VPN drop and reconnect where relevant;
- thick-client session handling;
- impersonation termination; and
- privileged-session expiry.

## 16. Include file and attachment testing

Where files are accepted or generated, testing should consider:

- file-type validation;
- mismatch between extension and content;
- malicious files;
- macros and active content;
- archive traversal;
- archive bombs;
- nested archives;
- malformed documents;
- parser vulnerabilities;
- unsafe preview;
- temporary storage;
- filename injection;
- path handling;
- content-type confusion;
- generated spreadsheet injection;
- file overwrite;
- unauthorised download; and
- direct file-link access.

## 17. Include API testing

API testing should cover:

- authentication;
- token validation;
- object-level authorisation;
- function-level authorisation;
- mass assignment;
- schema validation;
- rate limiting;
- excessive data exposure;
- bulk extraction;
- pagination;
- deprecated endpoints;
- undocumented endpoints;
- replay;
- idempotency;
- service identities;
- callback handling;
- request size;
- error disclosure;
- business-logic abuse; and
- direct access that bypasses the thick client or browser.

## 18. Include thick-client testing

Where a thick client is used, the test should consider:

- package integrity;
- binary and library versions;
- local storage;
- configuration;
- endpoint manipulation;
- server certificate validation;
- token storage;
- protocol manipulation;
- local privilege requirements;
- local services;
- DLL or library loading;
- update mechanism;
- file associations;
- offline operation;
- cached records;
- direct API or database calls;
- reverse engineering of sensitive logic;
- hard-coded secrets; and
- unsupported client versions.

The managed corporate EUC reduces endpoint risk but does not make the thick client itself trustworthy.

## 19. Include business-logic abuse testing

The test should explore whether legitimate functions can be combined in unintended ways.

Examples include:

- creating and approving the same item;
- bypassing required review;
- manipulating sequencing;
- repeating an action;
- reusing a one-time function;
- changing a record after release;
- exceeding quantity or value limits;
- avoiding project restrictions;
- abusing bulk operations;
- changing an owner before approval;
- using a report to bypass record access;
- obtaining information through search counts;
- abusing delegated authority;
- using support impersonation;
- triggering duplicate processing;
- manipulating time or expiry; and
- combining low-risk features into a high-impact path.

Automated scanners rarely provide adequate coverage of these risks.

## 20. Include administrative-function testing

The test should assess whether an attacker or lower-privileged user can:

- access the admin console;
- change roles;
- create accounts;
- alter identity trust;
- change session configuration;
- modify logging;
- suppress alerts;
- change export controls;
- install plugins;
- execute scripts;
- change integrations;
- alter scheduled jobs;
- access secrets;
- change certificates;
- perform direct data repair;
- initiate backup or restore;
- alter retention; or
- bypass change controls.

## 21. Include service and integration abuse testing

The test should consider whether a compromised service identity or integration can:

- exceed its approved scope;
- call unauthorised endpoints;
- access additional projects;
- replay messages;
- alter message routing;
- submit malformed data;
- redirect file transfer;
- call privileged functions;
- impersonate users;
- extract bulk information;
- suppress errors;
- exploit trust in internal network location; or
- pivot to another component.

## 22. Include logging and detection validation

The test should identify whether material attack activity creates useful events.

Examples include:

- failed authentication;
- privilege escalation;
- object-level access denial;
- injection attempts;
- self-approval attempts;
- role changes;
- support impersonation;
- bulk export;
- direct API misuse;
- administrative configuration change;
- disabled logging;
- suspicious file upload;
- supplier access;
- emergency access;
- token misuse; and
- attempts to access another project.

The purpose is not necessarily to run a full red-team exercise. It is to verify that application activity can support detection and investigation.

## 23. Include application-specific denial-of-service testing carefully

Availability testing should be explicitly authorised because it can disrupt service.

Where included, the scope may cover:

- request-size limits;
- expensive search;
- report generation;
- archive expansion;
- repeated login;
- session creation;
- file conversion;
- queue flooding;
- oversized API batches;
- recursive input;
- malformed documents;
- resource exhaustion; and
- transaction locking.

Testing should use safe limits, representative non-production environments or controlled production methods.

## 24. Include production testing only when justified and authorised

Production testing may reveal issues that a non-production environment cannot reproduce, but it creates operational risk.

Where production testing is approved, define:

- exact targets;
- exact dates and times;
- permitted techniques;
- prohibited techniques;
- test source addresses;
- test identities;
- production data restrictions;
- transaction restrictions;
- notification arrangements;
- real-time monitoring;
- stop conditions;
- rollback;
- incident escalation;
- evidence handling;
- clean-up; and
- confirmation that test records are identifiable.

Production testing should not be inferred from a general annual test approval.

## 25. Make the test environment representative

Where testing occurs outside production, the application should ensure that the environment is sufficiently representative in terms of:

- application version;
- configuration;
- authentication;
- roles;
- data partitions;
- APIs;
- integrations;
- file types;
- security headers;
- session settings;
- logging;
- network paths;
- database logic;
- thick-client version;
- plugins;
- supplier modules; and
- relevant production controls.

Differences should be documented so the tester understands which conclusions may not transfer to production.

## 26. Define the rules of engagement

The rules of engagement should include:

- scope;
- objectives;
- authorised testers;
- targets;
- testing window;
- source systems and addresses;
- accounts and roles;
- permitted techniques;
- prohibited techniques;
- production restrictions;
- social-engineering status;
- physical-testing status;
- denial-of-service status;
- malware or exploit-code restrictions;
- data-handling rules;
- evidence storage;
- communications;
- stop conditions;
- critical-finding escalation;
- incident coordination;
- clean-up;
- report handling;
- retest;
- liability and indemnity where relevant; and
- approval.

The application team should review the rules for technical and business accuracy.

## 27. Define stop conditions

Testing should stop or pause when:

- service availability is materially affected;
- production data integrity is at risk;
- an unsafe chain reaction is possible;
- a real compromise is suspected;
- a critical finding requires immediate containment;
- testing reaches an out-of-scope system;
- sensitive information is exposed beyond the agreed limit;
- a supplier system is unexpectedly affected;
- a safety or financial process may be triggered;
- test accounts behave unexpectedly;
- monitoring cannot distinguish test from attack;
- the authorised window ends; or
- the test lead or application owner invokes the stop procedure.

## 28. Coordinate with operations and incident response

The application should ensure that:

- support contacts are available;
- enterprise security operations know the authorised test where appropriate;
- incident response understands how to distinguish testing from genuine attack;
- logs are retained;
- alert suppression is minimised and documented;
- monitoring remains active;
- critical findings can be escalated immediately;
- a real incident discovered during testing is handled as an incident;
- operational teams understand stop conditions; and
- service recovery arrangements are ready.

An announced test should not require disabling all detection; that would remove valuable evidence.

## 29. Protect test accounts and credentials

Test identities should be:

- uniquely identifiable;
- limited to the agreed roles;
- separate from ordinary user accounts;
- restricted to the test period;
- protected through approved credential handling;
- prohibited from reuse by others;
- monitored;
- removed or disabled after testing; and
- reviewed for residual access.

Privileged test accounts should use the approved PAM or emergency-access process where applicable.

## 30. Use safe and identifiable test data

Test data should be:

- synthetic or minimised where practical;
- representative of required scenarios;
- clearly identifiable;
- separated by project or role;
- free of unnecessary personal or restricted information;
- safe for export and screenshots;
- removable after testing;
- protected while in use; and
- handled according to the agreed rules.

Where production data is unavoidable, the need and handling controls should be explicitly approved.

## 31. Control tester tools and connections

The application should ensure that testing uses:

- approved tester systems;
- approved connection paths;
- approved source addresses;
- approved VPN or internal testing route;
- authorised proxies;
- approved exploit or scanning tools;
- controlled file transfer;
- protected evidence storage;
- malware-safe tooling; and
- no unauthorised persistent agents.

The enterprise owns the tester connectivity platform. The application should verify that test traffic reaches the intended application paths.

## 32. Preserve evidence and chain of custody

Evidence should include, as appropriate:

- request and response;
- affected endpoint;
- user role;
- record identifier;
- screenshot;
- tool output;
- timestamp;
- tester;
- exploit steps;
- affected version;
- data accessed;
- logs;
- business impact;
- test environment; and
- clean-up action.

For high-impact findings, evidence should be sufficient for:

- reproducibility;
- remediation;
- incident assessment;
- supplier escalation;
- retest; and
- audit.

Sensitive evidence should be encrypted, access-restricted and retained in approved systems.

## 33. Require immediate escalation of critical findings

The rules of engagement should define rapid escalation for findings such as:

- remote code execution;
- authentication bypass;
- unrestricted privileged access;
- cross-project or cross-tenant data access;
- exposure of secrets;
- compromise of service identities;
- ability to disable logging;
- unrestricted bulk extraction;
- production data modification;
- build or signing compromise;
- active exploitation;
- severe supplier backdoor;
- destructive action; or
- compromise beyond the authorised scope.

The application should decide whether to:

- contain immediately;
- suspend testing;
- activate incident response;
- revoke credentials;
- disable a function;
- isolate an interface;
- preserve evidence; and
- initiate emergency change.

## 34. Validate findings with application context

The application team should review each finding for:

- reproducibility;
- affected component;
- affected version;
- affected role;
- affected environment;
- business function;
- information impact;
- technical impact;
- exploit prerequisites;
- attack chain;
- existing controls;
- detection;
- likely attacker;
- false-positive possibility;
- duplicate relationship;
- remediation ownership; and
- urgency.

The purpose is to add context, not to pressure the tester into lowering severity.

## 35. Use a consistent severity method

Severity should consider:

- technical exploitability;
- privilege required;
- user interaction;
- attack complexity;
- remote or local access;
- impact on confidentiality;
- impact on integrity;
- impact on availability;
- application criticality;
- information sensitivity;
- safety, engineering or financial consequence;
- scope of affected users or projects;
- detectability;
- active exploitation;
- ease of chaining;
- supplier dependency;
- remediation difficulty; and
- compensating controls.

The application should preserve the tester’s original severity and record any application risk adjustment transparently.

## 36. Distinguish findings from observations

The report should distinguish:

- confirmed exploitable vulnerability;
- control weakness;
- design concern;
- insecure practice;
- information disclosure;
- test limitation;
- unverified suspicion;
- excluded area;
- positive control;
- defence-in-depth recommendation; and
- business-process observation.

This avoids treating every recommendation as equivalent while ensuring that meaningful concerns are not lost.

## 37. Record findings in the authoritative workflow

Each legitimate finding should enter the established:

- vulnerability tracker;
- defect system;
- risk register;
- POA&M;
- service-management platform; or
- application security backlog.

The record should include:

- test reference;
- finding;
- severity;
- affected component;
- owner;
- target date;
- treatment;
- planned release;
- interim control;
- exception;
- retest requirement;
- status; and
- closure evidence.

The penetration-test report should not become the only place where findings are tracked.

## 38. Remediate the root cause

Remediation should address the underlying weakness where practical.

Examples:

- replacing client-side-only checks with server-side enforcement;
- correcting the role model;
- implementing object-level authorisation;
- removing unsafe dynamic queries;
- redesigning workflow;
- correcting token validation;
- updating dependencies;
- reducing service privilege;
- restricting file types;
- isolating conversion services;
- removing a shared account;
- changing support impersonation;
- restricting administrative functions;
- adding audit events;
- fixing insecure defaults; and
- retiring obsolete interfaces.

Blocking the exact payload used by the tester may not resolve the broader vulnerability.

## 39. Apply interim controls where permanent remediation is delayed

Interim measures may include:

- disable the feature;
- restrict roles;
- restrict source or destination;
- remove supplier access;
- block a file type;
- reduce privileges;
- introduce additional approval;
- limit export volume;
- apply a virtual patch;
- increase logging and alerting;
- shorten sessions;
- remove direct access;
- isolate the component;
- restrict to read-only; or
- suspend the affected service.

Interim controls should have:

- an owner;
- implementation evidence;
- monitoring;
- review date;
- expiry;
- residual-risk decision; and
- a permanent remediation plan.

## 40. Retest material findings

The application should arrange retesting for material findings.

Retesting should confirm:

- the original exploit no longer succeeds;
- the corrected component is deployed;
- all affected instances are corrected;
- alternate paths are addressed;
- related roles and projects are covered;
- no regression has been introduced;
- the interim control can be removed or remains necessary;
- logging and detection work;
- the baseline and inventory are updated; and
- evidence supports closure.

Developer screenshots or ticket comments are not a substitute for independent retesting of high-risk findings.

## 41. Manage false positives and disputed findings

Where a finding is disputed, the application should:

- reproduce the test;
- confirm scope and assumptions;
- provide relevant architecture and control evidence;
- involve the tester;
- preserve the original finding;
- record the technical basis for the decision;
- identify any residual concern;
- obtain appropriate security approval; and
- avoid closing solely because exploitation is inconvenient.

A finding that is technically valid but currently unreachable may still warrant monitoring or design correction.

## 42. Manage accepted penetration-test risk

Where remediation is deferred or risk is accepted, record:

- finding;
- affected components;
- exploit path;
- business impact;
- tester severity;
- application risk rating;
- reason for acceptance;
- compensating controls;
- monitoring;
- owner;
- approving authority;
- target remediation;
- review date;
- expiry;
- supplier dependency; and
- conditions requiring reconsideration.

Risk acceptance should not be indefinite.

## 43. Perform root-cause and thematic analysis

After the test, the application should identify themes such as:

- repeated access-control failure;
- client-side trust;
- weak session management;
- insecure defaults;
- weak input validation;
- business-logic gaps;
- poor role design;
- missing logging;
- unsafe supplier components;
- dependency weakness;
- inconsistent API controls;
- thick-client/server trust gaps;
- poor test coverage;
- missing threat model; and
- ineffective remediation of earlier findings.

Themes should result in broader improvements rather than isolated ticket closure.

## 44. Update the threat model and misuse cases

The application should incorporate credible attack paths from the test into:

- threat model;
- misuse cases;
- security requirements;
- design standards;
- role model;
- workflow rules;
- input-validation specification;
- logging design;
- monitoring use cases;
- SDLC tests; and
- supplier requirements.

A penetration test is most valuable when its lessons improve future releases.

## 45. Update automated and regression testing

Where practical, a confirmed penetration-test finding should lead to a repeatable test such as:

- unit test;
- integration test;
- API negative test;
- access-control test;
- security regression test;
- SAST rule;
- SCA gate;
- configuration check;
- pipeline policy;
- monitoring detection; or
- release checklist item.

This reduces the chance of reintroduction.

## 46. Update monitoring and detection

The application should assess whether the penetration-test activity was visible through:

- authentication events;
- access denials;
- API logs;
- input-validation events;
- privilege-change events;
- export logs;
- file-processing logs;
- support impersonation logs;
- configuration-change logs;
- application health;
- SIEM alerts; and
- incident workflows.

Where significant activity was invisible, improve AU-02 and SI-04 coverage.

## 47. Update SSP, risk and continuous-monitoring records

After testing, update as applicable:

- SSP CA-08 implementation statement;
- test date and scope;
- assurance schedule;
- CA-07 continuous-monitoring plan;
- risk assessment;
- risk register;
- POA&M;
- vulnerability tracker;
- security backlog;
- CM-02 baseline;
- CM-08 inventory;
- architecture;
- threat model;
- SyOps;
- support model;
- release plan; and
- supplier remediation records.

The full report need not be embedded in the SSP. The SSP should reference the controlled evidence.

## 48. Track closure to completion

The application owner should track:

- open critical findings;
- overdue findings;
- interim controls;
- retest status;
- exceptions;
- supplier actions;
- recurring issues;
- accepted risks;
- release dependencies;
- root-cause actions; and
- governance decisions.

The test is not complete when the report is delivered. It is complete when findings are treated, verified or formally accepted.

## 49. Protect the penetration-test report

The report may contain:

- exploitable endpoints;
- credentials;
- architecture;
- attack chains;
- restricted screenshots;
- sensitive records;
- source code;
- supplier weaknesses;
- network paths;
- privileged functions; and
- remediation status.

The application should:

- store it in an approved restricted repository;
- limit access;
- encrypt transfer;
- avoid routine email distribution;
- redact unnecessary sensitive content;
- control supplier sharing;
- preserve integrity;
- retain according to policy;
- prevent unauthorised deletion;
- log access where available; and
- use a sanitised summary for broader governance where appropriate.

## 50. Clean up after testing

The application should confirm removal or closure of:

- test accounts;
- privileged roles;
- test records;
- uploaded files;
- test API clients;
- temporary certificates;
- test tokens;
- scheduled jobs;
- test callbacks;
- changed configuration;
- temporary firewall or routing rules;
- test software agents;
- debug settings;
- support access;
- local tester files on application systems; and
- production test artefacts.

Any intentional residual test component should be documented and owned.

## 51. Review tester performance

The application owner and security function should assess whether the test:

- covered the agreed scope;
- used representative roles;
- examined business logic;
- examined APIs;
- examined thick-client behaviour where applicable;
- provided reproducible evidence;
- distinguished severity clearly;
- escalated critical findings appropriately;
- handled data safely;
- complied with the rules of engagement;
- provided useful remediation guidance; and
- identified limitations transparently.

A weak test should not automatically satisfy the next testing cycle merely because a report exists.

## 52. Manage penetration-testing limitations

Where testing cannot cover the full application, record:

- excluded component;
- reason;
- impact;
- associated risk;
- alternative assurance;
- owner;
- approval;
- supplier constraint;
- future test plan; and
- review or expiry date.

Examples include:

- destructive function excluded from production testing;
- supplier appliance inaccessible to testers;
- thick-client binary unavailable;
- no representative integration test environment;
- restricted data preventing workflow testing;
- unavailable privileged account;
- unstable non-production environment;
- unsupported protocol;
- safety-critical function unsuitable for active testing; or
- commercial terms preventing testing.

The limitation should be visible in the SSP, assessment report or risk record.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative **application-team effort**, excluding the tester’s commercial fees or independent testing hours. They assume the enterprise already provides an approved penetration-testing framework, supplier route, risk process and central monitoring.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated application-team effort |
|---|---|---|---:|
| **1. Define the application scope and test objectives** | Map browser, thick-client, API, database, workflow, file, integration, privileged and supplier attack surfaces and define credible compromise objectives. | Summarise in the **SSP CA-08 statement** and maintain detail in the existing **architecture**, **threat model**, **test scope**, **ConOps** or **SyOps**. | **8–16 hours** |
| **2. Agree the test frequency and event-driven triggers** | Apply the enterprise-defined frequency and identify major releases, migrations, incidents and high-risk changes that require additional testing. | Record in the **SSP**, **assurance schedule**, **CA-07 monitoring plan**, **release process** or **security testing strategy**. | **3–6 hours** |
| **3. Prepare representative accounts, roles, projects and test data** | Provide ordinary, cross-project, approver, administrator, support and API identities with safe records covering key workflow and information boundaries. | Evidence remains in the normal **test account record**, **test data plan**, **role matrix**, **test environment plan** and **rules of engagement**. | **12–28 hours** |
| **4. Prepare architecture and business context for the tester** | Supply current diagrams, interfaces, role descriptions, workflows, file types, known exclusions, previous findings and critical functions. | Use the existing **architecture pack**, **interface specifications**, **role matrix**, **threat model**, **CM-08 inventory** and **previous assessment records**. | **8–20 hours** |
| **5. Agree and approve rules of engagement** | Define authorised testers, targets, techniques, windows, test accounts, production limits, stop conditions, data handling, escalation, clean-up and retest. | Retain the approved **rules of engagement**, **assessment plan**, **change record**, **supplier contract/work order** and **security approval**. | **6–12 hours** |
| **6. Prepare and validate the test environment** | Confirm representative version, configuration, authentication, data partitions, integrations, logging and connectivity and document differences from production. | Record in the **test environment plan**, **CM-02 baseline comparison**, **test readiness review**, **change record** and **assessment plan**. | **8–24 hours** |
| **7. Coordinate operations, SOC and incident response** | Ensure contacts, monitoring, escalation, stop procedures, evidence retention and real-incident handling are ready. | Use the existing **SyOps**, **test communication plan**, **SOC notification**, **incident procedure**, **support rota** and **change record**. | **4–10 hours** |
| **8. Support testing without directing the outcome** | Answer business and technical questions, restore test data, resolve environment issues and preserve tester independence. | Record material support activity in the **test log**, **support tickets**, **assessment correspondence** or **daily test status**. | **8–24 hours during the test** |
| **9. Validate and risk-rate findings** | Confirm reproducibility, affected component, exploit path, business impact, duplicate relationship and application context without suppressing tester conclusions. | Record decisions in the **finding workshop notes**, **vulnerability tracker**, **risk register**, **POA&M** or **defect system**. | **1–4 hours per ordinary finding; more for complex chains** |
| **10. Assign remediation, interim controls and deadlines** | Allocate owners, target releases, temporary restrictions, monitoring and exception routes. | Use the normal **vulnerability record**, **security backlog**, **risk register**, **POA&M**, **change plan** and **service review**. | **1–3 hours per finding** |
| **11. Retest critical and high-risk findings** | Arrange independent verification that the exploit and alternate paths are closed and all affected components are corrected. | Retain evidence in the **retest report**, **vulnerability record**, **change/release record** and **closure approval**. | **4–12 hours per remediation group for coordination and evidence** |
| **12. Perform root-cause and thematic analysis** | Identify repeated weaknesses and create broader design, SDLC, role, validation, supplier, test and monitoring improvements. | Record in the existing **problem record**, **lessons-learned report**, **threat model**, **SDLC backlog**, **risk register** and **security improvement plan**. | **8–20 hours** |
| **13. Update SSP, monitoring and security artefacts** | Record test date, scope, limitations, material findings, remediation status, monitoring changes and future assurance requirements. | Update the **SSP**, **CA-07 plan**, **risk assessment**, **threat model**, **security backlog**, **AU-02/SI-04 evidence** and **application addendum**. | **6–14 hours** |
| **14. Clean up test access and artefacts** | Remove accounts, roles, test clients, files, records, callbacks, privileges and temporary configuration and verify completion. | Record in the **test closure checklist**, **access record**, **change ticket**, **CM-02 verification** and **assessment close-out record**. | **4–10 hours** |
| **15. Track findings to verified closure** | Review open items, overdue actions, interim controls, supplier commitments, retests and exceptions until completion. | Retain status in the normal **service review**, **CA-07 posture report**, **risk committee pack**, **POA&M** or **application governance minutes**. | **4–10 hours per review cycle** |
| **16. Document and manage test limitations** | Record excluded functions, unavailable integrations, unsafe production tests, supplier restrictions or environment gaps with alternative assurance and future action. | Use the existing **assessment report**, **risk register**, **problem record** or **application addendum**, referenced from the **SSP CA-08 statement**. | **4–10 hours per material limitation** |

### Indicative total

For a typical internal application, application-team preparation, coordination, triage and close-out commonly require around **100–230 hours per full penetration-testing cycle**, excluding:

- the independent tester’s effort and fees;
- engineering remediation;
- extensive environment construction;
- major incident response; and
- repeated retesting caused by ineffective fixes.

A simple commercial browser application may require less. A custom, thick-client, API-heavy, workflow-intensive or supplier-integrated application with multiple roles and information partitions may require substantially more.

The estimates should not be added mechanically where work overlaps. CA-08 commonly shares evidence and effort with:

- CA-02 control assessments;
- CA-07 continuous monitoring;
- RA-03 risk assessment;
- RA-05 vulnerability monitoring;
- SI-02 flaw remediation;
- SI-10 input validation;
- AC-03 access enforcement;
- AC-04 information-flow enforcement;
- AC-05 separation of duties;
- IA-02 identification and authentication;
- AU-02 event logging;
- SI-04 system monitoring; and
- SA-11 developer testing.

---

## Suggested document placement

To avoid creating disconnected evidence, penetration-testing information should normally be distributed across established application and assurance artefacts:

- **SSP:** CA-08 implementation approach, test frequency, scope principles, inherited enterprise testing services, findings treatment and limitations.
- **CA-07 continuous-monitoring plan:** planned test cycle, trigger events, overdue findings and retest status.
- **Risk assessment and threat model:** important attack paths, business impacts and post-test updates.
- **Security architecture:** trust boundaries, endpoints, privileged paths, test targets and excluded shared services.
- **CM-08 inventory:** components and versions included in scope.
- **CM-02 baseline:** test-environment and production-version comparison.
- **Role/access matrix:** representative accounts, conflicting roles, project boundaries and privileged functions.
- **Interface and API specifications:** endpoints, clients, schemas, service identities and versions.
- **Rules of engagement:** authorised scope, methods, windows, accounts, safety, escalation, evidence and clean-up.
- **Test environment plan:** representative configuration, data, integrations and differences from production.
- **Change record:** testing windows, temporary access, production activity and clean-up.
- **Penetration-test report:** controlled technical evidence, findings, severity, limitations and recommendations.
- **Vulnerability tracker, defect system or POA&M:** authoritative finding ownership, deadlines, treatment, exceptions and closure.
- **Risk register:** accepted risk, delayed remediation and compensating controls.
- **Change and release records:** remediation implementation and deployed version.
- **Retest report:** independent evidence of effective correction.
- **Problem and lessons-learned records:** root causes and thematic improvements.
- **AU-02 and SI-04 evidence:** visibility of test activity and monitoring improvements.
- **Service and governance reviews:** progress, overdue findings, supplier actions and decisions.
- **Application addendum:** test exclusions, supplier restrictions, environment limitations and residual risks.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide penetration-testing policy;
- definition of the enterprise test frequency where centrally mandated;
- approved internal red-team or testing supplier framework;
- tester vetting and contractual terms;
- corporate legal and privacy review;
- enterprise rules-of-engagement templates;
- infrastructure and network penetration testing;
- shared identity, VPN, endpoint and platform testing;
- central vulnerability and POA&M tooling;
- enterprise risk and exception governance;
- central SIEM and SOC operations;
- enterprise incident-response coordination;
- organisation-wide procurement and supplier management;
- corporate handling rules for sensitive test reports; and
- executive assurance reporting.

The application team must still:

- define the application-specific scope and objectives;
- provide representative identities, roles, projects and data;
- ensure the environment is suitable;
- identify business-logic and application-layer attack paths;
- coordinate safe testing;
- validate findings in context;
- own remediation;
- arrange retesting;
- update security artefacts;
- track findings to closure; and
- formally manage limitations.

> **Key dividing line:** the enterprise commissions and governs independent penetration testing; the application team makes the test technically and operationally meaningful and owns the treatment of every application-specific weakness it reveals.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, CA-08 Penetration Testing.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, CA-08 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-115, Technical Guide to Information Security Testing and Assessment**.
4. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1**.
5. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, current SP 800-53 and SP 800-53A catalogues.
6. National Institute of Standards and Technology, **NIST Glossary — Penetration Testing**.
