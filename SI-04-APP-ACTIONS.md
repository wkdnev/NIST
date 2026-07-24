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

At a practical minimum, an application should have:

1. A documented list of security-relevant events and monitoring scenarios.
2. Reliable logging of authentication, authorisation, privilege, security changes and high-impact business actions.
3. Consistent user, service, time, target, outcome and correlation context.
4. Forwarding of relevant events to the approved central monitoring service.
5. Detection of a small set of application-specific misuse or attack conditions.
6. Visible failure of logging or forwarding.
7. Protected logging configuration and event data.
8. Tested event generation, delivery and alerting.
9. Application support procedures for investigation and response.
10. Periodic review and tuning.

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
