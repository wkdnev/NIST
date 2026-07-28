# Definition of Work (Work Package)
## NIST SP 800-53 SI-04 — System Monitoring
### Application-Specific Delivery Package

**Work package identifier:** SI-04-WP  
**Control:** NIST SP 800-53 SI-04 — System Monitoring  
**Scope:** Internal IT application operating on a large enterprise corporate network  
**Perspective:** Application responsibilities only  
**Language:** UK English  
**Example application:** Engineering Requirements Management System  
**Delivery model:** Standard SDLC and cyber-security artefacts, with minimal creation of standalone documents

---

# 1. Purpose

This work package defines the application-specific work needed to implement and evidence compliance with **SI-04 System Monitoring**.

The application team is responsible for ensuring that the application makes its own security-relevant behaviour visible, understandable and usable by enterprise monitoring and incident-response functions.

This includes:

- defining application-specific monitoring scenarios;
- generating meaningful security telemetry;
- including sufficient investigative context;
- forwarding events to the approved enterprise monitoring service;
- detecting misuse, attack and control failure;
- protecting logging and monitoring configuration;
- detecting failure of application logging or forwarding;
- supporting investigation and containment;
- testing the complete monitoring path; and
- maintaining the monitoring capability through release and operational change.

This work package does **not** require the application team to build or operate:

- an enterprise SOC;
- a SIEM platform;
- enterprise network intrusion detection;
- EDR;
- VPN monitoring;
- firewall telemetry;
- central threat intelligence;
- enterprise identity monitoring;
- shared platform monitoring;
- central time services; or
- corporate incident-management tooling.

These are enterprise responsibilities.

---

# 2. Work package objectives

The work package will deliver an application monitoring capability that:

1. identifies the application behaviours and control failures that require monitoring;
2. creates reliable security-relevant application events;
3. records who did what, to which object, when, where and with what outcome;
4. forwards events to the approved enterprise monitoring service;
5. supports application-specific detection and alerting;
6. detects when monitoring itself is degraded or unavailable;
7. protects monitoring information and configuration;
8. provides operational guidance for support and incident response;
9. demonstrates end-to-end operation through testing; and
10. records compliance evidence in the SSP, SyOps, software design, test evidence and IT support/service documentation.

---

# 3. Scope

## 3.1 In scope

The following application elements are in scope where they form part of the application solution:

- browser or web interface;
- thick client;
- application services;
- APIs;
- scheduled jobs;
- batch processes;
- message consumers and producers;
- application-controlled database logic;
- file import and export;
- reporting;
- workflow and approval logic;
- application-owned service identities;
- privileged administration;
- supplier or support access;
- application security configuration;
- application logging code and configuration;
- application health checks;
- application-to-SIEM forwarding;
- application-specific detection rules;
- application support procedures;
- and application release evidence.

## 3.2 Out of scope

The following remain enterprise responsibilities:

- enterprise network and security infrastructure;
- enterprise hardware;
- end-user compute devices;
- physical and virtual servers;
- enterprise operating systems;
- corporate VPN;
- enterprise EDR;
- central SIEM platform;
- SOC operations;
- enterprise identity monitoring;
- enterprise time synchronisation;
- enterprise log retention platform;
- enterprise incident-management platform;
- and corporate monitoring policy.

The application team must still demonstrate correct integration with those inherited services.

---

# 4. Assumptions

This work package assumes:

- the application is internal-only;
- users connect from hardened, centrally managed corporate Windows EUC;
- remote access is through approved corporate VPN;
- corporate identity and MFA are available;
- an approved enterprise log collector or SIEM ingestion mechanism exists;
- application delivery follows an established SDLC;
- source control, change control and release management already exist;
- and enterprise security operations can receive and act upon application events once the application provides usable telemetry.

Where these assumptions are not valid, the application team must raise an exception or revise the work package estimate.

---

# 5. Deliverable summary

| Deliverable | Purpose | Estimated effort |
|---|---|---:|
| **A. SSP SI-04 implementation content** | Define control implementation, inheritance, monitoring scope, responsibilities and evidence | **18–34 hours** |
| **B. SyOps monitoring and response content** | Define operational monitoring, escalation, failure handling, investigation and support | **30–58 hours** |
| **C. Software design and monitoring specification** | Define event model, architecture, fields, rules, health monitoring, protection and integration | **54–112 hours** |
| **D. Code, configuration and software development** | Implement missing telemetry, forwarding, health checks, detection logic and protection | **80–260 hours** |
| **E. Test documentation and evidence** | Prove generation, delivery, parsing, alerting, protection, failure detection and supportability | **46–96 hours** |
| **F. IT support and service documentation** | Define operational ownership, investigation, containment, service checks and recurring review | **30–60 hours** |
| **G. Release, acceptance and handover evidence** | Confirm released version is monitored and accepted into service | **18–36 hours** |
| **H. Project management, review and assurance** | Coordinate stakeholders, reviews, decisions, defects and closure | **24–54 hours** |

## Indicative total application-team effort

### **300–710 hours**

The lower end assumes the application already produces good structured logs and only requires documentation, integration, tuning and testing.

The upper end assumes custom development is needed across several components and application-specific alerting must be created.

This estimate excludes:

- enterprise SIEM engineering;
- SOC analyst effort;
- enterprise infrastructure changes;
- penetration-testing fees;
- major redevelopment;
- remediation of unrelated defects;
- and supplier commercial costs.

---

# 6. Deliverable A — SSP SI-04 implementation content

## 6.1 Objective

Create the application-specific SI-04 control implementation statement and evidence references in the SSP or application SSP addendum.

## 6.2 Required SSP content

The SSP should include:

### 6.2.1 Control applicability

- statement that SI-04 applies to the application;
- selected SI-04 enhancements, if any;
- organisation-defined parameters;
- control implementation status;
- inherited, shared and application-implemented elements;
- and any approved exceptions.

### 6.2.2 Application monitoring scope

Identify the components and functions monitored, including:

- browser or thick-client activity;
- application services;
- APIs;
- scheduled jobs;
- batch processing;
- file handling;
- integrations;
- application-controlled database activity;
- privileged functions;
- security configuration;
- service identities;
- and application monitoring health.

### 6.2.3 Application-specific monitoring scenarios

The SSP should summarise the application’s key monitoring scenarios, for example:

- repeated attempts to access another project’s requirements;
- unauthorised administrative function use;
- bulk export of restricted information;
- unusual search or download volume;
- security-role or permission change;
- approval or workflow bypass;
- privileged or supplier activity;
- manipulated or malformed requests;
- unexpected service identity use;
- logging configuration change;
- loss of event forwarding;
- and failure of an application security control.

### 6.2.4 Event generation and context

The SSP should state that security-relevant events include, as applicable:

- actor identity;
- service identity;
- application role;
- event time;
- action;
- target object or function;
- outcome;
- reason;
- component;
- session identifier;
- transaction or correlation identifier;
- application and environment;
- and source context.

It should also state that passwords, private keys, complete tokens, recovery codes and unnecessary restricted business content are excluded.

### 6.2.5 Enterprise integration

Record:

- the approved enterprise collection or SIEM service;
- the application forwarding method;
- relevant inherited controls;
- enterprise time service;
- central retention;
- central monitoring ownership;
- and the application team’s responsibility to maintain the feed.

### 6.2.6 Monitoring failure

Describe how the application detects and responds to:

- disabled logging;
- full local buffer;
- forwarding failure;
- malformed or rejected events;
- collector unavailability;
- time failure;
- and loss of expected event flow.

### 6.2.7 Protection

Describe:

- who can change logging configuration;
- who can view application audit data;
- protection of local buffers;
- prevention of ordinary-user alteration;
- and separation between application administration and audit administration where proportionate.

### 6.2.8 Review and maintenance

Define:

- review frequency;
- review participants;
- change triggers;
- incident-driven review;
- false-positive tuning;
- and linkage to CA-07 continuous monitoring.

## 6.3 SSP evidence references

The SSP should reference, rather than duplicate:

- monitoring design;
- event catalogue;
- event schema;
- interface specifications;
- SyOps;
- test reports;
- SIEM onboarding evidence;
- operational acceptance;
- risk records;
- and review minutes.

## 6.4 SSP work items and effort

| Work item | Output | Estimated effort |
|---|---|---:|
| Review enterprise SI-04 policy and inherited services | Applicable requirements and inheritance notes | **3–5 hours** |
| Define monitoring boundary and applicability | SSP scope and status | **3–5 hours** |
| Define application monitoring scenarios | SSP summary of use cases | **4–8 hours** |
| Draft SI-04 implementation statement | Complete SSP control narrative | **5–10 hours** |
| Map evidence and dependencies | Evidence-reference matrix | **2–4 hours** |
| Review and approve | Approved SSP update | **1–2 hours** |

**Deliverable A total:** **18–34 hours**

---

# 7. Deliverable B — SyOps monitoring and response content

## 7.1 Objective

Define how the monitoring capability is operated, supported, investigated and recovered in day-to-day service.

## 7.2 Required SyOps content

### 7.2.1 Operational ownership

Define:

- application owner;
- service owner;
- application support;
- security operations;
- incident response;
- enterprise logging service;
- supplier support;
- and escalation responsibilities.

### 7.2.2 Monitoring checks

Document routine checks for:

- event-flow health;
- collector connectivity;
- queue or buffer status;
- logging configuration;
- application component coverage;
- certificate or credential expiry;
- parser errors;
- rejected events;
- alert operation;
- and monitoring dashboards.

### 7.2.3 Alert handling

For each important application alert define:

- alert name;
- trigger;
- severity;
- likely meaning;
- initial triage;
- evidence to collect;
- business impact;
- escalation route;
- containment options;
- false-positive conditions;
- and closure requirements.

### 7.2.4 Investigation support

Provide guidance on:

- interpreting event names and reason codes;
- locating affected records;
- correlating user, session and transaction identifiers;
- identifying affected projects or business units;
- querying the application;
- obtaining additional logs;
- preserving evidence;
- involving suppliers;
- and determining whether data was viewed, changed or exported.

### 7.2.5 Containment actions

Document authorised containment options such as:

- disabling an application identity;
- removing an application role;
- terminating a session;
- disabling an integration;
- stopping a batch job;
- disabling an export function;
- switching an interface to read-only;
- revoking a service credential;
- or taking a component out of service.

Each containment action should identify:

- approving authority;
- technical steps;
- business impact;
- rollback;
- and evidence to retain.

### 7.2.6 Monitoring failure response

Define actions for:

- no events received;
- forwarding outage;
- full buffer;
- rejected event schema;
- expired forwarding credential;
- disabled logging;
- time synchronisation issue;
- or unexpected reduction in event volume.

The SyOps should identify when sensitive functions must be restricted because monitoring is unavailable.

### 7.2.7 Enhanced or diagnostic logging

Define:

- who may enable it;
- approved duration;
- data minimisation;
- storage location;
- access restrictions;
- monitoring of its use;
- and mandatory disablement after investigation.

### 7.2.8 Recurring review

Define periodic review of:

- monitoring coverage;
- noisy or ineffective alerts;
- missing events;
- unresolved parser issues;
- repeated monitoring failures;
- new application functions;
- supplier changes;
- incidents;
- penetration-test findings;
- and risk exceptions.

## 7.3 SyOps work items and effort

| Work item | Output | Estimated effort |
|---|---|---:|
| Define operational roles and hand-offs | Monitoring and support RACI | **4–8 hours** |
| Define routine monitoring health checks | Operational checklist | **4–8 hours** |
| Define alert triage and escalation | Alert response procedures | **8–16 hours** |
| Define investigation and evidence handling | Investigation support procedure | **5–10 hours** |
| Define containment options | Application containment runbook | **4–8 hours** |
| Define monitoring failure procedure | Failure and recovery steps | **3–6 hours** |
| Define review and tuning process | Periodic service review procedure | **2–4 hours** |

**Deliverable B total:** **30–58 hours**

---

# 8. Deliverable C — Software design and monitoring specification

## 8.1 Objective

Define the technical design required to generate, protect, forward and use application monitoring information.

## 8.2 Required design content

### 8.2.1 Monitoring architecture

The design should identify:

- event-producing components;
- local buffers;
- logging libraries or frameworks;
- event transport;
- enterprise collectors;
- SIEM destination;
- trust boundaries;
- authentication used for forwarding;
- encryption;
- failure paths;
- alternate paths;
- and monitoring health signals.

### 8.2.2 Application event catalogue

For each event define:

- unique event name or ID;
- business/security purpose;
- generating component;
- trigger;
- success/failure treatment;
- severity;
- expected frequency;
- required fields;
- sensitive-data restrictions;
- destination;
- alert/use-case mapping;
- retention category;
- owner;
- and associated test case.

The event catalogue should cover, where applicable:

- authentication;
- session activity;
- denied access;
- role and permission changes;
- privileged access;
- support and emergency activity;
- security configuration;
- high-value record changes;
- workflow approvals;
- separation-of-duties violations;
- bulk view/search/export;
- file import/export;
- API misuse;
- batch failure;
- service identity misuse;
- input-validation and integrity failures;
- logging changes;
- and monitoring failure.

### 8.2.3 Event schema

Define standard fields including:

- event ID;
- event time;
- application;
- environment;
- component;
- actor identity;
- service identity;
- affected identity;
- role;
- session ID;
- transaction/correlation ID;
- target object;
- project or information scope;
- action;
- outcome;
- reason;
- source context;
- destination;
- privilege/supplier/emergency indicator;
- and schema version.

### 8.2.4 Correlation design

Define how correlation works across:

- thick client;
- web tier;
- application service;
- API;
- database;
- queue;
- batch process;
- file processor;
- and external integration.

### 8.2.5 Detection use cases

Define detection logic for the highest-value application scenarios.

For each use case record:

- threat or misuse scenario;
- required events;
- threshold or condition;
- time window;
- severity;
- enrichment;
- expected false positives;
- response;
- and test method.

### 8.2.6 Monitoring health

Define technical health signals for:

- logging initialisation;
- event-generation failure;
- local write failure;
- queue backlog;
- forwarding failure;
- authentication failure to collector;
- expired certificate;
- malformed event;
- parser rejection;
- full local storage;
- time failure;
- and loss of expected heartbeat.

### 8.2.7 Protection

Define:

- logging configuration permissions;
- event access permissions;
- local storage protection;
- append-only or tamper-evident behaviour where applicable;
- secrets used by log forwarders;
- prevention of log injection;
- secure error handling;
- and prevention of sensitive data leakage.

### 8.2.8 Performance and resilience

Define:

- expected event rate;
- peak event rate;
- buffer size;
- retry behaviour;
- duplicate handling;
- back-pressure;
- impact on application availability;
- and maximum acceptable event loss.

## 8.3 Design work items and effort

| Work item | Output | Estimated effort |
|---|---|---:|
| Create monitoring architecture | Diagram and technical description | **8–16 hours** |
| Create event catalogue | Controlled event specification | **12–28 hours** |
| Define event schema and field dictionary | Standard structured event model | **8–16 hours** |
| Define correlation approach | Cross-tier correlation design | **4–10 hours** |
| Define detection use cases | Rules, thresholds and response mapping | **8–18 hours** |
| Define monitoring health and resilience | Failure, buffer and recovery design | **6–14 hours** |
| Define protection and access | Security design and role restrictions | **4–10 hours** |
| Design review and approval | Approved design baseline | **4–8 hours** |

**Deliverable C total:** **54–112 hours**

---

# 9. Deliverable D — Code, configuration and software development

## 9.1 Objective

Implement any missing capability required for SI-04 compliance.

## 9.2 Potential development scope

The exact development scope should be determined by a gap analysis against the design.

### 9.2.1 Structured event generation

Develop or configure application events for:

- authentication and session handling;
- access denials;
- privileged actions;
- role and permission changes;
- sensitive record activity;
- workflow approvals;
- bulk export;
- API or batch misuse;
- service identity activity;
- security configuration;
- and control failure.

### 9.2.2 Common logging component

Where multiple components produce inconsistent events, create or configure a reusable logging component that:

- applies the approved event schema;
- includes correlation identifiers;
- standardises outcome and reason codes;
- redacts prohibited data;
- prevents log injection;
- and handles transmission failure consistently.

### 9.2.3 Correlation support

Implement:

- request IDs;
- session IDs;
- transaction IDs;
- propagation across APIs;
- queue message correlation;
- and batch-job correlation.

### 9.2.4 Event forwarding

Configure or develop:

- enterprise logging agent integration;
- API-based forwarding;
- message-based forwarding;
- authenticated and encrypted transport;
- environment and component tagging;
- retry;
- queueing;
- and duplicate management.

### 9.2.5 Monitoring-health capability

Implement:

- logging health endpoint or metric;
- event-flow heartbeat;
- queue-depth monitoring;
- forwarding error counter;
- certificate-expiry monitoring;
- local-storage threshold;
- parser rejection indicator;
- and operational alert.

### 9.2.6 Detection and alert logic

Implement, jointly with the enterprise monitoring team where necessary:

- saved searches;
- correlation rules;
- thresholds;
- dashboards;
- reports;
- or alert definitions.

Application development may be needed to emit additional fields or explicit misuse events that the SIEM cannot infer reliably.

### 9.2.7 Monitoring protection

Implement:

- restricted administration;
- protected configuration;
- local event access control;
- secrets-vault integration;
- safe diagnostic logging;
- and audit of monitoring configuration changes.

### 9.2.8 Failure behaviour

Implement controlled behaviour when logging or forwarding fails, such as:

- local protected buffering;
- retry;
- operational escalation;
- restriction of particularly sensitive functions;
- or fail-safe shutdown of a specific process.

## 9.3 Development acceptance criteria

All developed capability should satisfy:

- server-side event generation for authoritative actions;
- consistent structured fields;
- stable identity attribution;
- correlation across tiers;
- no passwords, private keys or complete tokens;
- correct application and environment tagging;
- protected transport;
- visible monitoring failure;
- acceptable performance impact;
- repeatable deployment;
- source control;
- peer review;
- static and dependency scanning where applicable;
- and test traceability.

## 9.4 Development work items and effort

| Work item | Output | Estimated effort |
|---|---|---:|
| Detailed gap analysis | Confirmed code/configuration backlog | **8–16 hours** |
| Common logging/schema implementation | Reusable logging capability | **16–50 hours** |
| Security event implementation | Missing application events | **24–90 hours** |
| Correlation implementation | Cross-tier/request correlation | **8–30 hours** |
| Forwarding integration | Collector/SIEM feed configuration or code | **8–30 hours** |
| Monitoring-health implementation | Health checks, metrics and failure alerts | **8–24 hours** |
| Detection-rule implementation support | Application-specific rules and enrichment | **4–12 hours** |
| Protection and secret integration | Access, vault and configuration controls | **4–12 hours** |
| Peer review, build and defect correction | Reviewed implementation | **8–24 hours** |

**Deliverable D total:** **80–260 hours**

---

# 10. Deliverable E — Test documentation and evidence

## 10.1 Objective

Produce repeatable evidence that the monitoring capability operates end to end.

## 10.2 Required test coverage

### 10.2.1 Event-generation tests

For each selected event verify:

- correct trigger;
- success and failure behaviour;
- actor identity;
- target;
- timestamp;
- action;
- outcome;
- reason;
- component;
- application;
- environment;
- and correlation.

### 10.2.2 Client and interface coverage

Test:

- browser;
- thick client;
- API;
- batch;
- queue;
- file import/export;
- administrative function;
- service identity;
- and integration paths.

### 10.2.3 End-to-end delivery

Verify:

- event created;
- event forwarded;
- transport protected;
- event received;
- event parsed;
- fields mapped;
- event searchable;
- detection logic invoked;
- and alert or report understandable.

### 10.2.4 Negative and bypass tests

Test:

- direct URL or API bypass attempt;
- manipulated client request;
- incorrect role;
- cross-project access;
- invalid service identity;
- disabled account;
- malformed input;
- bulk export;
- and attempted monitoring configuration change.

### 10.2.5 Sensitive-data tests

Verify that events do not contain:

- passwords;
- private keys;
- complete tokens;
- recovery codes;
- secret values;
- excessive personal information;
- or unnecessary restricted business content.

### 10.2.6 Failure tests

Test:

- collector unavailable;
- forwarding credential invalid;
- certificate expired;
- buffer full;
- event malformed;
- parser rejects event;
- logging disabled;
- local storage unavailable;
- and time source failure.

### 10.2.7 Protection tests

Verify:

- ordinary users cannot change logging configuration;
- unauthorised support users cannot view protected events;
- local buffers cannot be modified without detection;
- monitoring secrets are protected;
- and diagnostic logging is controlled.

### 10.2.8 Performance tests

Confirm:

- acceptable response-time impact;
- acceptable throughput;
- event generation under peak load;
- no uncontrolled queue growth;
- and no unacceptable loss.

### 10.2.9 Operational interpretation test

Conduct a short exercise in which application support and/or security operations:

- receive a representative alert;
- identify the user and affected object;
- determine business impact;
- locate supporting evidence;
- select a containment action;
- and record the outcome.

## 10.3 Test evidence required

The test report should include:

- test environment;
- application version;
- test data;
- test identities and roles;
- test steps;
- expected results;
- actual results;
- event extracts;
- SIEM screenshots or query output;
- alert evidence;
- defects;
- retest;
- and approval.

## 10.4 Test work items and effort

| Work item | Output | Estimated effort |
|---|---|---:|
| Create SI-04 test plan and traceability | Test scope and requirements mapping | **8–16 hours** |
| Create event and field validation tests | Detailed test cases | **8–18 hours** |
| Execute end-to-end event tests | Generation-to-SIEM evidence | **12–24 hours** |
| Execute negative/protection tests | Bypass, access and redaction evidence | **8–18 hours** |
| Execute failure/resilience tests | Forwarding, buffer and health evidence | **6–14 hours** |
| Execute operational interpretation exercise | Support/SOC usability evidence | **2–6 hours** |
| Produce test report and retest | Approved evidence pack | **2–8 hours** |

**Deliverable E total:** **46–96 hours**

---

# 11. Deliverable F — IT support and service documentation

## 11.1 Objective

Ensure that application support and service-management teams can operate, maintain and support the monitoring capability.

## 11.2 Required support documentation

### 11.2.1 Service monitoring description

Include:

- monitored components;
- event-flow dependencies;
- enterprise collector dependency;
- dashboards;
- health checks;
- alert ownership;
- and expected normal event patterns.

### 11.2.2 Support responsibilities

Define first-, second- and third-line responsibilities for:

- monitoring-health failure;
- missing events;
- parser problems;
- alert investigation;
- application defects;
- supplier escalation;
- certificate or secret failure;
- and release verification.

### 11.2.3 Troubleshooting procedures

Provide procedures for:

- no events arriving;
- only some components producing events;
- duplicate events;
- incorrect timestamps;
- missing user identity;
- parser rejection;
- unexpected sensitive data;
- queue backlog;
- excessive event volume;
- noisy alerts;
- and certificate expiry.

### 11.2.4 Service restoration

Define:

- restart or reconnection procedure;
- queue recovery;
- event reconciliation;
- duplicate handling;
- confirmation of restored monitoring;
- and service closure evidence.

### 11.2.5 Incident support

Define:

- application contacts;
- data-owner contacts;
- event interpretation;
- queries;
- affected-object lookup;
- containment;
- evidence preservation;
- and supplier involvement.

### 11.2.6 Maintenance and review schedule

Include recurring tasks for:

- event coverage review;
- alert tuning;
- service account review;
- forwarding certificate review;
- parser/schema review;
- diagnostic logging review;
- SIEM onboarding review;
- risk review;
- and evidence refresh.

### 11.2.7 Known errors and limitations

Record:

- unsupported events;
- supplier product constraints;
- ambiguous fields;
- local-only logs;
- unmonitored paths;
- excessive false positives;
- and compensating controls.

## 11.3 Support work items and effort

| Work item | Output | Estimated effort |
|---|---|---:|
| Create service monitoring description | Service-design/support content | **6–12 hours** |
| Define support and escalation model | Support RACI and hand-offs | **4–8 hours** |
| Create troubleshooting runbook | Fault diagnosis and restoration procedures | **8–16 hours** |
| Create incident support guide | Queries, containment and evidence steps | **6–12 hours** |
| Define maintenance schedule | Recurring checks and reviews | **3–6 hours** |
| Record known errors and limitations | Knowledge records and risk references | **3–6 hours** |

**Deliverable F total:** **30–60 hours**

---

# 12. Deliverable G — Release, acceptance and handover evidence

## 12.1 Objective

Demonstrate that the released application version has its required monitoring enabled and operational.

## 12.2 Required release evidence

The release or operational acceptance pack should include:

- application version;
- event catalogue version;
- schema version;
- deployment configuration;
- SIEM source/collector reference;
- forwarding certificate or credential status;
- successful test evidence;
- alert validation;
- open defects;
- accepted risks;
- support readiness;
- monitoring owner;
- and approval to enter service.

## 12.3 Production verification

After deployment verify:

- all expected components are producing events;
- application and environment tags are correct;
- timestamps are correct;
- correlation works;
- no debug logging is unintentionally enabled;
- no secrets appear in events;
- event rates are plausible;
- SIEM parsing works;
- alert rules are enabled;
- health monitoring works;
- and support teams have access to required dashboards or queries.

## 12.4 Handover work items and effort

| Work item | Output | Estimated effort |
|---|---|---:|
| Build monitoring acceptance checklist | Release and operational acceptance criteria | **4–8 hours** |
| Prepare release evidence | Configuration, tests, risks and ownership | **6–12 hours** |
| Execute production verification | Post-deployment monitoring checks | **4–8 hours** |
| Conduct support handover | Walkthrough and acceptance | **2–4 hours** |
| Close residual evidence actions | Final SSP/evidence updates | **2–4 hours** |

**Deliverable G total:** **18–36 hours**

---

# 13. Deliverable H — Project management, review and assurance

## 13.1 Objective

Coordinate the work package and obtain timely technical, security, operational and business approval.

## 13.2 Required activities

- work package planning;
- stakeholder identification;
- design workshops;
- application/SOC integration meetings;
- backlog management;
- evidence tracking;
- review coordination;
- defect triage;
- risk and exception management;
- supplier coordination;
- and final closure review.

## 13.3 Work items and effort

| Work item | Output | Estimated effort |
|---|---|---:|
| Work package planning and scheduling | Delivery plan and milestones | **4–8 hours** |
| Technical/security workshops | Agreed scope and decisions | **8–18 hours** |
| Progress, backlog and evidence management | Updated actions and evidence tracker | **6–14 hours** |
| Review and approval coordination | Approved deliverables | **4–8 hours** |
| Final compliance readiness review | Closure decision and residual actions | **2–6 hours** |

**Deliverable H total:** **24–54 hours**

---

# 14. Detailed work breakdown structure

| WBS | Activity | Primary deliverable | Estimated effort |
|---|---|---|---:|
| 1.1 | Confirm application boundary and components | SSP / design | **4–8 hours** |
| 1.2 | Confirm inherited enterprise monitoring services | SSP | **3–5 hours** |
| 1.3 | Identify application threats and misuse scenarios | SSP / design | **6–12 hours** |
| 1.4 | Identify required security events | Design | **8–16 hours** |
| 1.5 | Define event schema and correlation | Design | **8–16 hours** |
| 1.6 | Define SIEM forwarding and failure behaviour | Design / SyOps | **8–16 hours** |
| 1.7 | Define monitoring protection | Design / SSP | **4–10 hours** |
| 1.8 | Define alerting and investigation use cases | Design / SyOps | **8–18 hours** |
| 2.1 | Implement structured logging | Code/configuration | **16–50 hours** |
| 2.2 | Implement missing security events | Code/configuration | **24–90 hours** |
| 2.3 | Implement correlation propagation | Code/configuration | **8–30 hours** |
| 2.4 | Implement central forwarding | Code/configuration | **8–30 hours** |
| 2.5 | Implement monitoring-health detection | Code/configuration | **8–24 hours** |
| 2.6 | Implement protection and secrets integration | Code/configuration | **4–12 hours** |
| 2.7 | Support SIEM rule and dashboard creation | Configuration | **4–12 hours** |
| 3.1 | Update SSP | SSP | **18–34 hours** |
| 3.2 | Update SyOps | SyOps | **30–58 hours** |
| 3.3 | Update software design | Design | **54–112 hours** |
| 3.4 | Update support/service documents | Support docs | **30–60 hours** |
| 4.1 | Create test plan | Test docs | **8–16 hours** |
| 4.2 | Execute functional/event tests | Test evidence | **12–24 hours** |
| 4.3 | Execute negative/protection tests | Test evidence | **8–18 hours** |
| 4.4 | Execute failure/resilience tests | Test evidence | **6–14 hours** |
| 4.5 | Execute operational interpretation exercise | Test evidence | **2–6 hours** |
| 4.6 | Produce report and retest | Test evidence | **2–8 hours** |
| 5.1 | Prepare operational acceptance | Release evidence | **10–20 hours** |
| 5.2 | Complete production verification | Release evidence | **4–8 hours** |
| 5.3 | Handover to support | Service handover | **4–8 hours** |
| 6.1 | Project and assurance management | Work package governance | **24–54 hours** |

---

# 15. Roles and responsibilities

| Role | Application responsibility |
|---|---|
| **Application owner** | Accountable for SI-04 implementation and residual risk |
| **Product/service owner** | Prioritises monitoring requirements and accepts service impacts |
| **Security architect** | Defines monitoring scope, events, architecture, controls and evidence |
| **Software architect/designer** | Defines event schema, correlation, forwarding, failure and protection design |
| **Development team** | Implements structured events, health checks and required control logic |
| **Test team** | Creates and executes end-to-end, negative, failure and protection tests |
| **Application support** | Operates health checks, investigates faults and supports incidents |
| **Service manager** | Maintains service review, support readiness and operational evidence |
| **Business/data owner** | Defines high-value actions, records and business impact |
| **Enterprise logging/SIEM team** | Provides ingestion service, parser/rule support and central platform |
| **SOC/incident response** | Monitors central alerts and leads enterprise incident response |
| **Supplier** | Provides product logging details, defect correction and support where applicable |

---

# 16. Dependencies

The work package depends on:

- approved enterprise logging/SIEM onboarding process;
- availability of an enterprise collector or ingestion mechanism;
- enterprise time synchronisation;
- access to source code or supplier configuration;
- representative test environments;
- representative user roles;
- application architecture and data-flow information;
- business-owner input on high-value actions;
- security operations input on alert usefulness;
- and release/change windows.

A dependency that cannot be met should be recorded as a risk and may require re-planning or exception approval.

---

# 17. Risks and common failure modes

| Risk | Required treatment |
|---|---|
| Product logs do not identify the acting user | Add application event, enrich at service layer or raise formal exception |
| Thick client logs only locally | Generate authoritative server-side events and minimise reliance on local logs |
| Logs contain passwords or tokens | Implement redaction and regression tests immediately |
| SIEM receives events but cannot parse them | Correct schema/parser and retest end to end |
| Events lack business-object context | Add record/project/workflow identifiers |
| High event volume causes noise | Tune event selection and detection thresholds |
| Monitoring fails silently | Implement health indicators and operational alerts |
| Supplier cannot change product logging | Record limitation, compensating monitoring and remediation roadmap |
| Correlation is absent across tiers | Implement request/session/transaction identifiers |
| Debug logging remains enabled | Add controlled activation, expiry and review |
| Monitoring is documented but never tested | Add release-gated end-to-end testing |
| SOC cannot interpret alerts | Provide event catalogue, triage and application support contacts |

---

# 18. Acceptance criteria

The work package is complete when:

1. the SSP contains an approved SI-04 application implementation statement;
2. the SyOps defines operational monitoring, failure response, investigation and containment;
3. the software design includes the monitoring architecture, event catalogue, schema, correlation, protection and health design;
4. required application code and configuration are implemented and released;
5. security-relevant events cover all material application paths;
6. events include sufficient investigative context;
7. events reach the approved enterprise monitoring service;
8. parsing and field mapping are correct;
9. high-value application misuse scenarios have usable detection or investigation logic;
10. monitoring failure is detectable;
11. logging configuration and local event data are protected;
12. end-to-end, negative, failure and protection tests pass;
13. application support can investigate a representative event;
14. operational acceptance confirms monitoring is active in production;
15. open limitations are recorded in the risk register or POA&M;
16. evidence is linked from the SSP;
17. recurring review and tuning are scheduled; and
18. the application owner approves residual risk.

---

# 19. Evidence completion checklist

## SSP

- [ ] SI-04 applicability and status recorded
- [ ] inherited enterprise services identified
- [ ] application monitoring boundary recorded
- [ ] key scenarios and event types summarised
- [ ] monitoring failure described
- [ ] protection described
- [ ] review frequency recorded
- [ ] evidence references complete
- [ ] exceptions recorded

## SyOps

- [ ] monitoring ownership defined
- [ ] health checks defined
- [ ] alert triage documented
- [ ] investigation steps documented
- [ ] containment options documented
- [ ] monitoring failure response documented
- [ ] diagnostic logging controlled
- [ ] recurring review defined

## Software design

- [ ] monitoring architecture complete
- [ ] event catalogue complete
- [ ] event schema complete
- [ ] correlation design complete
- [ ] detection use cases defined
- [ ] failure behaviour defined
- [ ] protection defined
- [ ] performance and buffering defined

## Code/configuration

- [ ] required events implemented
- [ ] common schema used
- [ ] correlation implemented
- [ ] forwarding configured
- [ ] health checks implemented
- [ ] sensitive data redacted
- [ ] configuration protected
- [ ] peer review complete

## Test evidence

- [ ] event generation tested
- [ ] end-to-end delivery tested
- [ ] field mapping tested
- [ ] alert/use case tested
- [ ] negative paths tested
- [ ] monitoring failure tested
- [ ] access protection tested
- [ ] sensitive-data leakage tested
- [ ] performance tested
- [ ] defects retested

## IT support/service

- [ ] support roles agreed
- [ ] troubleshooting runbook complete
- [ ] restoration procedure complete
- [ ] incident support guide complete
- [ ] maintenance schedule complete
- [ ] known limitations recorded
- [ ] support handover accepted

---

# 20. Final dividing line

> **The enterprise operates the shared SOC, SIEM, network, endpoint and platform monitoring services. The application team remains accountable for making the application’s own security-relevant behaviour visible, understandable, protected, testable and operationally supportable.**
