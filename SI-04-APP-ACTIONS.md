# SI-04 System Monitoring — Application Actions

## Purpose

For an IT application, SI-04 means the application must provide enough security-relevant visibility to detect misuse, attacks, abnormal behaviour and failure of its own controls, and must make that information usable by the organisation’s monitoring and incident-response functions.

It does **not** mean that every application must operate its own SOC, SIEM, EDR, network sensors or enterprise threat-intelligence service. Those are enterprise capabilities. The application’s responsibility is to generate meaningful telemetry, identify application-specific suspicious behaviour, forward relevant events to the approved monitoring service, and support investigation and response.

## 1. Define what the application needs to monitor

The application should maintain a short monitoring specification or use-case catalogue covering its important components, interfaces, roles, data and business processes.

This should identify:

- the application components and interfaces being monitored;
- the events or conditions that may indicate attack, misuse or control failure;
- the severity or priority of each condition;
- where the monitoring information is produced;
- which team or service receives it; and
- what response is expected.

The monitoring scope should reflect the application’s actual risks. A requirements-management application, for example, should pay particular attention to unauthorised viewing or alteration of restricted requirements, bulk export, privilege escalation, approval bypass, suspicious account use and tampering with audit history.

## 2. Generate security-relevant application telemetry

The application should produce reliable events for significant activity that only the application can properly understand.

At a minimum, this normally includes:

- successful and failed application authentication;
- session creation, termination, expiry and invalid-session use;
- access denied by application roles or record-level permissions;
- changes to roles, permissions, service identities and privileged accounts;
- use of administrative, support or emergency functions;
- changes to security configuration;
- creation, alteration, deletion, approval or release of high-value records;
- bulk viewing, searching, downloading, printing or exporting;
- API, batch, integration and service-processing failures;
- input-validation, file-processing and integrity failures;
- unexpected disabling or failure of application security controls; and
- suspicious or repeated application errors.

AU-02 determines which events are logged; SI-04 is concerned with using monitoring information to recognise attacks, unauthorised activity and control problems. A pile of logs nobody can interpret is not effective monitoring.

## 3. Include enough context for investigation

Each monitoring event should contain sufficient non-secret context to answer the basic investigative questions:

- **Who** performed or attempted the action?
- **What** action occurred?
- **Which** record, function, component or interface was affected?
- **When** did it occur?
- **Where** did it originate?
- **Did it succeed or fail?**
- **Which transaction, session or request did it belong to?**

Useful fields may include:

- corporate user or service identity;
- application role;
- timestamp;
- event type;
- outcome;
- component;
- record identifier;
- session identifier;
- transaction or correlation identifier;
- source endpoint; and
- relevant reason code.

Passwords, private keys, complete tokens, recovery codes and unnecessary restricted business content must not be placed in monitoring records.

## 4. Detect application-specific suspicious behaviour

The application should provide rules, alerts or clearly identifiable events for behaviour that cannot be recognised reliably by enterprise infrastructure alone.

Depending on the application, examples include:

- repeated attempts to access records belonging to another project or business unit;
- an ordinary user invoking an administrative function;
- sudden bulk extraction of restricted information;
- unusual numbers of searches, downloads or failed access attempts;
- changes to sensitive records outside normal workflow;
- approval by the same person who initiated a controlled action;
- repeated rejection of manipulated or malformed requests;
- use of dormant, disabled or unexpected service identities;
- access at an unusual stage of a business process;
- attempts to bypass client-side controls;
- abnormal API or batch volumes;
- unexpected changes to logging or security configuration; and
- failure of an integrity, retention or information-flow control.

This does not require sophisticated behavioural analytics for every application. A small application may use a few well-chosen alerts and reports. A larger or higher-risk application may require automated thresholds, correlation and behavioural baselines.

## 5. Forward monitoring information to the approved enterprise service

Security-relevant application events should be sent to the organisation’s approved central logging or monitoring service in a supported format.

The application should:

- use the approved forwarding mechanism;
- use synchronised enterprise time;
- provide consistent event names and fields;
- identify the application, environment and component;
- support correlation across application tiers;
- protect event transmission;
- avoid duplicate or uncontrolled feeds; and
- document events that cannot be forwarded.

The application team is responsible for ensuring that the feed works and remains useful. The enterprise team is responsible for operating the shared collection, SIEM, SOC and supporting infrastructure.

## 6. Monitor the complete application, not just the user interface

Monitoring should cover all material parts of the application, including:

- thick-client activity;
- browser or presentation components;
- application and service tiers;
- APIs;
- scheduled jobs and batch processes;
- databases and application-controlled stored procedures;
- messaging and integration components;
- file import and export functions;
- application-owned service identities; and
- security-relevant configuration.

For a thick-client application, the server must not assume that requests are legitimate because they came from an approved corporate Windows device. The receiving service should still log and detect manipulated, unauthorised or abnormal requests.

## 7. Monitor privileged and support activity particularly closely

Application administration and support functions should generate enhanced monitoring because they can alter access, configuration or restricted information.

The application should record and, where appropriate, alert on:

- assignment or removal of privileged roles;
- privileged sign-in and sign-out;
- changes to security settings;
- changes to logging or monitoring configuration;
- access to restricted diagnostic or support information;
- emergency-access use;
- bulk administrative changes;
- direct alteration of protected records; and
- failed privileged operations.

Where enterprise PAM is used, application events should be capable of being correlated with the corresponding privileged session.

## 8. Detect failure or degradation of the monitoring itself

The application should make failures in its security monitoring visible.

Examples include:

- logging disabled or reconfigured;
- loss of connection to the central collector;
- repeated event-forwarding failures;
- full or unavailable local log storage;
- malformed or rejected event records;
- time synchronisation failure;
- application components no longer producing expected events; and
- monitoring rules unexpectedly removed or disabled.

The application should not silently continue as though monitoring were healthy. The response may be an alert, controlled buffering, operational escalation or, where the risk justifies it, restriction of particularly sensitive functions.

## 9. Protect monitoring information

Application monitoring information must be protected from unauthorised access, alteration and deletion.

The application should:

- restrict who can view or change logging configuration;
- prevent ordinary users from deleting or altering events;
- avoid exposing restricted event data through the user interface;
- use approved central retention rather than unmanaged local logs;
- protect any temporary local buffers;
- ensure diagnostic logging is not left permanently enabled; and
- separate application administration from audit-log administration where proportionate.

## 10. Support investigation and incident response

The application team must be able to help interpret application events. Enterprise monitoring staff may see that something unusual occurred, but they may not understand what a particular record, workflow or function means.

The application should therefore provide:

- event descriptions and field definitions;
- severity and escalation guidance;
- known benign conditions;
- application support contacts;
- investigation queries or reports;
- information about affected records and business impact;
- procedures for obtaining additional evidence;
- containment options, such as disabling a feature, identity or integration; and
- guidance on preserving relevant application information.

## 11. Test monitoring and alerting

Monitoring should be tested before production use and after material change.

Testing should confirm that:

- the expected application event is generated;
- the correct user, action, target, time and outcome are recorded;
- the event reaches the central monitoring service;
- parsing and field mapping are correct;
- correlation identifiers work across tiers;
- the expected alert or investigation use case activates;
- sensitive information is not unnecessarily exposed;
- monitoring failure is detectable; and
- relevant support and incident teams can interpret the event.

A successful test should demonstrate the full path from application action to an understandable monitoring result, not merely that a log file exists.

## 12. Review and tune the monitoring

The application owner should periodically review monitoring coverage with security operations, application support and relevant business owners.

The review should consider:

- new application functions and interfaces;
- new information types or higher-impact business processes;
- architecture or identity changes;
- incidents and near misses;
- penetration-test and vulnerability findings;
- alerts that are too noisy or never useful;
- suspicious behaviour that is not currently visible;
- event fields that are missing or ambiguous; and
- changes in enterprise monitoring requirements.

Monitoring should be tuned carefully. Excessive noise can hide genuine incidents, while insufficient telemetry leaves investigators guessing.

## Sensible minimum for an ordinary internal application

The estimates below are indicative effort for a typical internal application with an established SDLC, existing enterprise logging services and no major legacy constraints. They represent application-team effort only and exclude enterprise SIEM engineering, procurement or major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Documented security-relevant events and monitoring scenarios** | Identify the important users, roles, components, interfaces, restricted information and business actions, then define the events or conditions that should be monitored. | Record the monitoring scope and event list in the **SSP SI-04 implementation statement**. Reference relevant trust boundaries and information flows already described in the **security architecture**, **ConOps** or **SyOps**. | **4–8 hours** |
| **2. Reliable logging of key security and business events** | Configure or develop logging for authentication, access denial, privilege use, security changes and high-impact business actions. Include both successful and failed outcomes where relevant. | Describe the required event types in the **SSP** and implement them as acceptance criteria or security requirements in the normal **SDLC backlog**, **requirements specification** or **system design**. Retain representative execution results in the standard **test report**. | **12–32 hours** |
| **3. Consistent investigative context** | Standardise event fields so relevant records include the user or service identity, timestamp, action, target, outcome, component and session or correlation identifier. | Define the event-field standard in the **application design specification**, **interface specification** or logging section of the **SyOps**. Confirm implementation in the normal **system/integration test report**. | **6–16 hours** |
| **4. Forwarding to the approved central monitoring service** | Configure the approved logging agent, API, connector or platform integration and verify that events arrive in the central monitoring service with correct application, environment and component identifiers. | Record the inherited enterprise service and application forwarding method in the **SSP**. Include configuration references in the **deployment design**, **build record** or **release documentation**, and retain successful delivery evidence in the **integration or operational acceptance test report**. | **8–20 hours** |
| **5. Detection of application-specific misuse or attacks** | Select a small number of high-value misuse scenarios and implement alerts, thresholds, reports or clearly identifiable events for them. | Document the scenarios and expected response in the **SSP**, **threat assessment**, **risk assessment** or security section of the **ConOps/SyOps**. Record rule implementation and test results within the normal **security test report** or **operational acceptance report**. | **8–24 hours** |
| **6. Visible failure of logging or forwarding** | Detect logging disablement, collector unavailability, rejected events, full local buffers or loss of expected event flow, then raise an operational or security notification. | Describe the expected failure behaviour in the **SSP** and **SyOps/ConOps**. Capture the implemented health check in the **application design** and verify it through the normal **resilience**, **failure-mode** or **operational acceptance test report**. | **6–16 hours** |
| **7. Protected logging configuration and event data** | Restrict access to logging settings and records, prevent ordinary users from changing or deleting events, and protect any temporary local log storage. | Record the roles and protections in the **SSP access-control and SI-04 sections**, supported by the existing **role matrix**, **security design** or **SyOps**. Confirm through the standard **access-control test report** or **configuration review evidence**. | **4–12 hours** |
| **8. Tested event generation, delivery and alerting** | Execute end-to-end tests from a representative application action through event creation, forwarding, parsing and alerting. Repeat after material changes. | Add test cases to the normal **system test plan**, **security test plan** or **operational acceptance test plan**. Retain results, defects and retest outcomes in the established **test report** and **release evidence pack**. | **8–20 hours** |
| **9. Application support for investigation and response** | Define event meanings, support contacts, investigation steps, business impact, containment options and evidence-preservation actions. | Include this material in the existing **SyOps**, **support model**, **incident-response annex**, **operational runbook** or relevant **SSP procedures**. Avoid creating a separate monitoring document unless the application is unusually complex. | **6–12 hours** |
| **10. Periodic review and tuning** | Review coverage, false positives, missing context, alert usefulness, application changes and incident lessons with application support and security operations. | Record the review requirement in the **SSP continuous-monitoring section** and capture decisions in normal **service review minutes**, **security review records**, **change records** or updates to the **risk register** and **backlog**. | **3–6 hours per review** |

### Suggested document placement

To avoid creating disconnected evidence, the information should normally be distributed across existing application and SDLC artefacts:

- **SSP:** control implementation, inherited enterprise services, monitoring scope, key events, ownership, review frequency and control limitations.
- **ConOps or SyOps:** operational monitoring behaviour, support responsibilities, escalation, failure handling and investigation support.
- **Security architecture or design:** event sources, trust boundaries, correlation approach, protected log paths and integration with enterprise monitoring.
- **Requirements and backlog:** individual logging, alerting and protection requirements with acceptance criteria.
- **Test plans and reports:** evidence that events are generated, forwarded, parsed, protected and used in alerts.
- **Release or operational acceptance records:** confirmation that monitoring is enabled and working for the released version.
- **Risk register or addendum:** accepted gaps, unavailable events, legacy constraints and compensating controls.
## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- the enterprise SOC;
- the central SIEM or monitoring platform;
- network intrusion-detection systems;
- EDR on Windows EUC devices and servers;
- VPN monitoring;
- firewall and network telemetry;
- enterprise identity monitoring;
- central threat intelligence;
- shared platform and operating-system monitoring;
- central time services;
- enterprise incident-management tooling; and
- corporate monitoring governance and retention standards.

> **Key dividing line:** the enterprise monitors the shared environment; the application must make its own security-relevant behaviour visible and understandable.
