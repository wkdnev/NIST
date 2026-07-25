# AU-02 Event Logging — Application Actions

## Purpose

For an IT application, AU-02 means the application must **identify which events need to be logged, generate those events consistently across every relevant application path, provide enough context for accountability and investigation, and ensure that the resulting records can be used by authorised operational, security and assurance teams**.

The enterprise may provide:

- central SIEM and log-management platforms;
- enterprise logging policy and minimum event requirements;
- network, operating-system, database-platform and endpoint logs;
- corporate identity and time-synchronisation services;
- central security monitoring and incident response;
- log transport, storage, retention and backup;
- managed Microsoft Windows EUC logging;
- enterprise vulnerability and threat intelligence;
- privacy, records-management and legal-retention requirements; and
- organisation-wide access controls for central log repositories.

Those capabilities are inherited.

The application remains responsible for defining and producing the events that only the application can understand, such as:

- successful and failed application authentication;
- account and role changes;
- authorisation denials;
- privileged actions;
- sensitive record access;
- workflow approvals and releases;
- project-boundary or information-flow violations;
- data imports and exports;
- configuration changes;
- file-processing decisions;
- supplier and support actions;
- security-control failures;
- service and integration activity;
- session creation and termination;
- business-rule overrides;
- use of emergency or fallback functions;
- and other events needed to reconstruct significant application activity.

NIST AU-02 requires organisations to identify the types of events that systems are capable of logging, coordinate the event-logging function with other organisational entities, specify which event types are to be logged and the frequency or conditions under which they are logged, provide a rationale for the selected events, and review and update the selected event types. NIST SP 800-92 provides supporting guidance for developing, implementing and maintaining effective computer-security log-management practices. The current NIST control and assessment catalogue is SP 800-53 and SP 800-53A Release 5.2.0. citeturn800548search1turn800548search2turn800548search3turn800548search7turn800548search9

> **Core principle:** the enterprise operates the common logging and monitoring platforms; the application must generate the right application events, with the right context, at the right points in the business and security process.

---

## 1. Define the application event-logging scope

The application should identify every component that can generate security-relevant or accountability-relevant events.

This normally includes:

- browser application;
- thick client;
- application services;
- APIs;
- administrative interfaces;
- support consoles;
- authentication and federation components;
- authorisation services;
- databases and application-owned database logic;
- message consumers and publishers;
- file-processing services;
- batch imports and exports;
- report generation;
- scheduled jobs;
- integration adapters;
- plugins and extensions;
- configuration services;
- deployment and migration utilities;
- supplier support functions;
- emergency or fallback mechanisms;
- application-specific service identities;
- local caches and offline functions where applicable; and
- recovery or standby components.

The logging scope should align with:

- the application boundary;
- architecture;
- data-flow diagrams;
- CM-08 inventory;
- CM-02 baseline;
- interface inventory;
- role model;
- threat model;
- risk assessment;
- incident scenarios; and
- CA-07 continuous-monitoring plan.

## 2. Maintain an application event catalogue

The application should maintain an authoritative event catalogue or equivalent specification.

For each event type, record:

- event identifier;
- event name;
- description;
- producing component;
- business or security purpose;
- triggering condition;
- event severity;
- mandatory fields;
- optional fields;
- user or service identity;
- object or record reference;
- outcome;
- correlation identifier;
- environment;
- sensitivity;
- destination;
- retention category;
- monitoring or alert use;
- expected volume;
- test case;
- owner;
- and review date.

The catalogue may be part of the existing logging specification, security design or SSP supporting material rather than a standalone document.

## 3. Define events using application risk

Event selection should be based on:

- credible threats;
- business impact;
- information sensitivity;
- privilege;
- regulatory or contractual requirements;
- incident-response needs;
- fraud and misuse risks;
- accountability requirements;
- separation of duties;
- data export risk;
- supplier access;
- service identities;
- known weaknesses;
- penetration-test findings;
- historical incidents;
- and enterprise logging standards.

The application should be able to explain why each material event is logged and what security, operational or accountability question it helps answer.

## 4. Log successful and failed authentication

The application should log:

- successful authentication;
- failed authentication;
- invalid token or assertion;
- invalid signature;
- wrong issuer or audience;
- expired or not-yet-valid assertion;
- insufficient authentication strength;
- disabled account;
- locked account;
- unknown or unmapped identity;
- ambiguous identity mapping;
- fallback or local-authentication use;
- privileged authentication;
- supplier authentication;
- emergency authentication;
- password reset or recovery where application-owned;
- and authentication-service failure.

Events should distinguish ordinary user, privileged user, supplier, service and emergency access.

## 5. Log session lifecycle events

The application should log, where proportionate:

- session creation;
- session renewal;
- token refresh;
- privilege change within a session;
- session timeout;
- absolute session expiry;
- explicit sign-out;
- administrative session termination;
- session revocation;
- concurrent-session denial;
- session replay detection;
- support-impersonation start and end;
- VPN or access-context change where authoritative context is available;
- and failure to invalidate a session.

Session identifiers should be represented using a safe correlation value rather than logging reusable tokens.

## 6. Log account-management events

Application account events should include:

- account creation;
- activation;
- disablement;
- reactivation;
- deletion;
- expiry;
- identity mapping;
- mapping change;
- duplicate mapping detection;
- account ownership change;
- temporary account creation;
- supplier account creation;
- service identity creation;
- local account creation;
- fallback account use;
- dormant account action;
- and account-reconciliation discrepancy.

These events support AC-02 and IA-02.

## 7. Log role and privilege changes

The application should log:

- role assignment;
- role removal;
- privileged-role assignment;
- temporary privilege;
- privilege expiry;
- project or group membership change;
- permission-definition change;
- role-definition change;
- group-to-role mapping change;
- delegation;
- delegation use;
- delegation expiry;
- emergency privilege;
- self-assignment attempt;
- incompatible-role conflict;
- and separation-of-duties override.

The event should identify both the acting identity and the affected identity.

## 8. Log authorisation decisions and denials

The application should log material authorisation outcomes, especially:

- denied privileged function;
- denied record access;
- denied cross-project access;
- denied object-level access;
- denied field-level access;
- denied export;
- denied workflow action;
- denied administrative action;
- denied direct API access;
- denied support impersonation;
- denied supplier action;
- denied access because account or role information is stale;
- and denied action because required approval is missing.

It is not always necessary to log every successful low-risk read. Denials and high-impact successful actions usually provide more value.

## 9. Log sensitive record access where justified

The application should identify records or functions for which successful access needs logging.

Examples include:

- privileged record views;
- restricted engineering information;
- personnel information;
- security findings;
- audit records;
- incident evidence;
- authentication configuration;
- cryptographic or trust configuration;
- source code;
- bulk data;
- high-value approvals;
- sensitive project records;
- supplier-only information;
- and records subject to legal or contractual obligations.

The event should identify the user, record or object, action, purpose or workflow context where available, time and outcome.

## 10. Log record creation, modification and deletion

For material business records, the application should log:

- creation;
- material amendment;
- status change;
- reassignment;
- classification or sensitivity change;
- ownership change;
- approval;
- rejection;
- release;
- withdrawal;
- deletion;
- restoration;
- archive;
- retention hold;
- and permanent disposal.

Where practical, the event should include the previous and new state or a reliable reference to the change history.

## 11. Log workflow and approval events

Workflow logging should include:

- submission;
- review;
- approval;
- rejection;
- release;
- cancellation;
- return for correction;
- delegation;
- escalation;
- override;
- self-approval denial;
- approval after material change;
- approval replay attempt;
- and workflow-rule change.

The application should preserve the identities that originated, modified, reviewed, approved and released the item.

## 12. Log separation-of-duties events

The application should log:

- prohibited role combination;
- denied self-approval;
- denied self-granting of access;
- delegation conflict;
- emergency override;
- independent review completion;
- post-action review;
- conflicting service identity;
- developer production-access attempt;
- and change implementer attempting to approve their own change.

These events support AC-05 and fraud or misuse investigation.

## 13. Log data import events

Import logging should include:

- source;
- sender or service identity;
- file or message reference;
- schema or format;
- record count;
- validation result;
- rejected record count;
- records created or changed;
- quarantine;
- reconciliation;
- duplicate detection;
- rollback;
- approval;
- and final outcome.

Full imported data should not be copied into the event log.

## 14. Log data export and download events

The application should log high-risk:

- report generation;
- bulk export;
- download;
- attachment download;
- data extract;
- supplier transfer;
- approved external-system transfer;
- scheduled report distribution;
- audit-log export;
- source-code export;
- database extract;
- and support bundle generation.

Useful fields include:

- acting identity;
- project or data scope;
- export type;
- record count or volume;
- destination or recipient;
- approval reference;
- outcome;
- and correlation identifier.

## 15. Log file-processing decisions

The application should log:

- file accepted;
- file rejected;
- malicious-code detection;
- prohibited file type;
- content/type mismatch;
- oversized file;
- archive limit breach;
- encrypted or unscannable file;
- parser failure;
- quarantine;
- sanitisation or conversion;
- release from quarantine;
- and deletion.

Avoid placing full filenames or paths in logs when they contain sensitive personal or project information; use controlled identifiers or sanitised values where appropriate.

## 16. Log input-validation failures

Material validation events include:

- invalid schema;
- unexpected field;
- invalid identifier;
- invalid workflow state;
- cross-project mismatch;
- injection attempt;
- path traversal attempt;
- oversized input;
- malformed API request;
- malformed message;
- invalid callback;
- invalid destination;
- invalid configuration;
- repeated validation failure;
- and validation-service failure.

The log should identify the category without unnecessarily retaining the malicious payload.

## 17. Log API activity

The application should log security-relevant API events such as:

- client authentication;
- failed client authentication;
- token-validation failure;
- unauthorised endpoint call;
- object-level authorisation denial;
- privileged API action;
- bulk extraction;
- deprecated API use;
- unknown API client;
- rate-limit action;
- replay detection;
- invalid callback;
- schema failure;
- service identity use;
- and API configuration change.

## 18. Log service-to-service activity

For material integrations, log:

- calling service identity;
- receiving service;
- operation;
- message or transaction identifier;
- data scope;
- outcome;
- authentication failure;
- authorisation failure;
- replay or duplicate detection;
- schema failure;
- destination change;
- queue or topic change;
- service credential change;
- and unexpected caller.

## 19. Log privileged and administrative activity

Administrative event logging should include:

- security configuration change;
- application configuration change;
- role-definition change;
- identity-provider trust change;
- session setting change;
- export setting change;
- file-type rule change;
- logging setting change;
- monitoring setting change;
- certificate or secret reference change;
- plugin installation;
- scheduled-job change;
- integration change;
- direct data fix;
- database migration;
- support impersonation;
- and emergency administration.

Privileged actions should be attributable to the real operator, not only to a shared technical identity.

## 20. Log change and release activity

Application-relevant change events should include:

- source merge or release tag;
- pipeline change;
- security gate change;
- artefact promotion;
- deployment;
- rollback;
- configuration deployment;
- database migration;
- thick-client package publication;
- emergency change;
- supplier change;
- post-deployment verification;
- and baseline update.

Some events may originate in enterprise repositories or pipelines; the application should ensure they can be linked to the application release.

## 21. Log vulnerability and flaw-remediation events

Where the application directly manages the workflow, useful events include:

- new vulnerability finding;
- severity change;
- owner assignment;
- exception approval;
- interim control;
- remediation deployment;
- failed remediation;
- retest;
- closure;
- reopened finding;
- unsupported component identified;
- supplier delay;
- and expired exception.

The detailed vulnerability content should remain in the authoritative vulnerability system rather than be duplicated into general application logs.

## 22. Log supplier and support activity

The application should log:

- supplier authentication;
- supplier session start and end;
- support case reference;
- support impersonation;
- diagnostic access;
- file upload or download;
- configuration change;
- privileged action;
- direct data correction;
- failed or denied action;
- access outside approved window;
- emergency supplier access;
- and access removal.

## 23. Log emergency and fallback use

The application should generate high-priority events for:

- break-glass authentication;
- emergency role assignment;
- fallback authentication;
- identity-provider bypass;
- emergency change;
- temporary logging reduction;
- recovery-mode operation;
- direct database emergency access;
- and post-use credential rotation or privilege removal.

Emergency events should normally trigger review and may warrant immediate alerting.

## 24. Log security-control failures

The application should log failure or degradation of:

- authentication;
- authorisation;
- identity mapping;
- token validation;
- audit logging;
- event forwarding;
- malware scanning;
- input validation;
- certificate validation;
- secrets retrieval;
- encryption;
- time synchronisation;
- policy evaluation;
- session revocation;
- export control;
- file quarantine;
- and monitoring health checks.

Security-control failure should not disappear into a general application error.

## 25. Log logging-system changes

The application should log:

- logging enabled or disabled;
- log-level change;
- event-category change;
- destination change;
- forwarding change;
- parser or format change;
- retention-related setting change;
- local buffer change;
- audit access change;
- audit deletion attempt;
- alert suppression;
- correlation-field change;
- and logging component failure.

Changes that reduce audit visibility should be treated as privileged and high risk.

## 26. Define mandatory event content

The application should define a minimum event structure.

Typical fields include:

- event identifier;
- event name;
- timestamp;
- application name;
- application version where useful;
- environment;
- producing component;
- host or instance reference;
- stable user identity;
- acting service identity;
- affected identity;
- role;
- session or safe correlation identifier;
- transaction or workflow identifier;
- object or record identifier;
- project or information scope;
- action;
- outcome;
- reason category;
- source context;
- destination or recipient where relevant;
- privileged, supplier or emergency status;
- change, support or incident reference;
- severity;
- and schema version.

Not every event needs every field. The catalogue should define which fields are mandatory for each event type.

## 27. Use stable identities

Event logs should use stable identifiers rather than relying solely on:

- display name;
- email address;
- role label;
- workstation name;
- IP address;
- or free-text username.

Where possible, record:

- authoritative enterprise subject identifier;
- application account identifier;
- service identity;
- and affected account or record owner.

Display names may be included for usability, but stable identifiers preserve attribution after names change.

## 28. Record acting and affected identities separately

For administrative and support events, distinguish:

- the person performing the action;
- the account or user affected;
- the user being impersonated;
- the service identity used;
- the approver;
- the delegator;
- and the supplier organisation.

A log saying “administrator changed role” is inadequate if it does not identify who acted and whose access changed.

## 29. Use correlation identifiers

The application should use identifiers that allow events to be linked across:

- browser;
- thick client;
- API gateway;
- application service;
- database;
- message broker;
- batch job;
- integration;
- SIEM;
- support ticket;
- change record;
- and incident record.

Correlation identifiers should:

- be generated safely;
- not contain secrets;
- not be reusable authenticators;
- remain stable for the relevant transaction;
- be passed through approved interfaces;
- and be included in error and support references where useful.

## 30. Record outcome and reason

Events should clearly distinguish:

- success;
- failure;
- denial;
- partial completion;
- quarantine;
- rollback;
- timeout;
- cancellation;
- override;
- and unknown or indeterminate outcome.

Failure reasons should use controlled categories rather than only free-text messages.

Useful reason categories include:

- invalid identity;
- insufficient role;
- object outside scope;
- invalid state;
- invalid input;
- expired credential;
- policy unavailable;
- supplier window expired;
- prohibited destination;
- service unavailable;
- and internal processing failure.

## 31. Record time accurately

The application should use the approved enterprise time source and include:

- event time;
- timezone or UTC convention;
- sufficient precision;
- and, where relevant, processing or receipt time.

The application should:

- avoid local workstation time as the authoritative timestamp;
- identify delayed or queued events;
- handle clock skew;
- preserve ordering;
- and log time-synchronisation failure where it affects accountability.

The enterprise provides time synchronisation; the application uses it correctly.

## 32. Avoid logging secrets and authenticators

The application should never log:

- passwords;
- full session tokens;
- refresh tokens;
- bearer tokens;
- API keys;
- private keys;
- database passwords;
- full connection strings;
- recovery codes;
- password-reset tokens;
- activation codes;
- complete authentication assertions;
- secret-bearing headers;
- or certificate private material.

Where diagnostic value is needed, use:

- non-sensitive identifiers;
- token fingerprints;
- last few non-secret characters only where approved;
- certificate thumbprints;
- client identifiers;
- or controlled redaction.

## 33. Minimise personal and sensitive information

Application logs should contain only the information needed for:

- accountability;
- detection;
- investigation;
- troubleshooting;
- compliance;
- and evidence.

Avoid unnecessary logging of:

- full record content;
- free-text descriptions;
- personal information;
- medical or personnel data;
- source code;
- document contents;
- full search queries;
- file contents;
- complete exports;
- authentication claims not needed for investigation;
- or sensitive supplier information.

Use object references and controlled categories rather than copying business data.

## 34. Prevent log injection and ambiguity

The application should protect logs from:

- newline injection;
- control-character injection;
- delimiter injection;
- forged prefixes;
- misleading timestamps;
- attacker-controlled severity;
- unescaped JSON or XML;
- spreadsheet formula injection in exported logs;
- and malicious filenames or usernames.

Use structured logging and safe encoders where practical.

## 35. Use structured and versioned event formats

Structured events improve central processing.

The application should define:

- event schema;
- schema version;
- field types;
- controlled enumerations;
- timestamp format;
- identity fields;
- outcome values;
- severity values;
- optional fields;
- redaction rules;
- and compatibility expectations.

Schema changes should be controlled under CM-05 and CM-06 and coordinated with SIEM parsing and monitoring.

## 36. Define event severity consistently

The application should use a controlled severity model aligned with enterprise standards.

Severity should consider:

- security impact;
- business impact;
- privilege;
- likelihood of malicious activity;
- urgency;
- operational effect;
- and whether immediate action is required.

Examples:

- informational — ordinary successful event;
- low — minor invalid input;
- medium — repeated authorisation denial;
- high — privileged configuration change or supplier access outside window;
- critical — logging disabled, break-glass use, authentication bypass or confirmed sensitive bulk extraction.

## 37. Distinguish audit, security, operational and diagnostic events

The application may produce:

- audit events;
- security events;
- operational events;
- performance events;
- diagnostic traces;
- and business-process history.

These categories should be distinguishable.

Diagnostic logging should not be assumed to satisfy audit requirements because it may:

- be temporary;
- be too verbose;
- expose secrets;
- change between releases;
- lack stable identifiers;
- or be disabled in production.

## 38. Define conditions and frequency for logging

AU-02 requires the organisation to specify which events are logged and the frequency or situation requiring logging.

For the application, this means defining whether an event is logged:

- every occurrence;
- on success and failure;
- on failure only;
- for privileged users only;
- for sensitive records only;
- above a volume threshold;
- during an incident;
- during enhanced monitoring;
- in production only;
- in all environments;
- during supplier access;
- or when a control enters a degraded state.

Sampling should not be used for high-value accountability events unless explicitly justified and approved.

## 39. Control verbose and debug logging

Debug logging should be:

- disabled by default in production unless justified;
- time-limited;
- authorised;
- attributable;
- protected;
- monitored;
- automatically returned to the approved level where possible;
- reviewed for secrets and sensitive data;
- and included in post-incident or support clean-up.

The application should log activation and deactivation of verbose logging.

## 40. Ensure logging is consistent across all access paths

Equivalent actions should generate equivalent events whether performed through:

- browser;
- thick client;
- API;
- administrative console;
- batch process;
- message consumer;
- database procedure;
- support console;
- or supplier interface.

A prohibited action blocked through the browser but attempted directly through the API should still create the required event.

## 41. Ensure logging is server-side where accountability matters

Client-side logs may support troubleshooting but should not be the sole evidence for security-relevant actions.

The authoritative event should normally be generated by:

- trusted application service;
- API service;
- workflow engine;
- database procedure;
- integration consumer;
- or other controlled server-side component.

Thick-client and browser logs can be manipulated, suppressed or lost.

## 42. Handle offline and queued events

Where a thick client or component can operate offline or queue activity, the application should define:

- which events are stored locally;
- integrity protection;
- encryption;
- maximum queue size;
- timestamp handling;
- sequence;
- upload on reconnection;
- duplicate detection;
- failure notification;
- local deletion after successful transfer;
- account-disablement handling;
- and incident access.

Offline logs should not become the only record of sensitive activity if the device can be lost or compromised.

## 43. Forward events to approved central logging

The application should integrate with the enterprise log-management or SIEM service where required.

The application team should define:

- event source;
- transport;
- format;
- authentication;
- encryption;
- destination;
- buffering;
- retry;
- failure handling;
- health monitoring;
- parser;
- index or storage category;
- ownership;
- and onboarding evidence.

The enterprise operates the central platform. The application owns correct event generation and integration.

## 44. Protect event transport

Event transport should:

- use approved encrypted protocols;
- authenticate the destination;
- prevent arbitrary destination changes;
- restrict the sending identity;
- preserve event integrity;
- handle network interruption;
- prevent silent event loss;
- avoid clear-text forwarding;
- and log forwarding failure.

Where events traverse message queues or agents, the application should understand the trust and delivery model.

## 45. Buffer safely during temporary failure

If central logging is unavailable, the application should define:

- local buffer;
- capacity;
- protection;
- retention;
- retry;
- back-pressure;
- alerting;
- overflow behaviour;
- recovery;
- and reconciliation.

High-risk events should not be silently dropped.

If safe logging cannot continue, the application should define whether sensitive functions:

- continue;
- are restricted;
- or fail closed.

The decision should be risk-based and documented.

## 46. Detect event-generation and forwarding failure

The application should monitor:

- no events received;
- unexpected volume drop;
- malformed events;
- parser failures;
- schema mismatch;
- forwarding queue growth;
- authentication failure;
- certificate expiry;
- destination failure;
- local storage exhaustion;
- clock skew;
- duplicate events;
- and gaps after release.

Health monitoring should distinguish “the application is quiet” from “the application stopped logging”.

## 47. Protect local application logs

Where local logs exist, the application should:

- restrict read access;
- restrict write and deletion;
- separate application operation from log administration where feasible;
- prevent ordinary users changing logs;
- prevent the application writing outside approved locations;
- rotate safely;
- protect against disk exhaustion;
- secure backups;
- avoid world-readable permissions;
- prevent symbolic-link or path attacks;
- and clear temporary diagnostic logs appropriately.

## 48. Protect audit records from application administrators

Where proportionate, the application should prevent administrators who perform sensitive activity from being able to erase or rewrite the corresponding evidence.

Controls may include:

- immediate central forwarding;
- append-only records;
- restricted deletion;
- separate log-administrator roles;
- immutable storage;
- independent monitoring;
- alert on logging changes;
- and retention controlled outside the application.

The enterprise owns central repository protection. The application should not create an easy local concealment path.

## 49. Define retention and disposal requirements

The application should identify the retention category for each event type based on enterprise:

- security monitoring;
- incident response;
- legal;
- records-management;
- privacy;
- contractual;
- and operational requirements.

The application should:

- avoid inventing conflicting retention periods;
- identify events requiring longer retention;
- identify transient debug logs;
- ensure local copies do not outlive the approved need;
- support legal hold where required;
- and ensure disposal is authorised and traceable.

## 50. Restrict access to logs

Application log access should follow least privilege.

Relevant roles may include:

- application support;
- security operations;
- incident response;
- audit;
- privacy;
- application owner;
- database support;
- supplier support;
- and developers.

Access should be scoped by:

- environment;
- event type;
- project;
- sensitivity;
- operational need;
- and duration.

Supplier and developer access to production logs should be limited and monitored.

## 51. Provide useful search and investigation context

The application should enable authorised investigators to search or correlate by:

- user identity;
- service identity;
- account;
- session;
- transaction;
- record;
- project;
- IP or source context where useful;
- API client;
- supplier;
- change reference;
- support case;
- event type;
- outcome;
- and time range.

The application may rely on enterprise SIEM functionality, but events must contain the necessary fields.

## 52. Link events to incidents, changes and support activity

Where relevant, events should include or support linkage to:

- incident identifier;
- change identifier;
- release identifier;
- support ticket;
- supplier case;
- approval record;
- access request;
- vulnerability finding;
- exception;
- and business transaction.

This reduces the need to reconstruct context manually.

## 53. Define application alerts separately from event logging

Not every event requires an alert, and not every alert should be generated inside the application.

The application should identify events that warrant:

- immediate application response;
- SIEM correlation;
- threshold alert;
- operational notification;
- incident escalation;
- or periodic reporting.

Examples include:

- break-glass use;
- logging disabled;
- repeated privileged denial;
- supplier access outside window;
- bulk export;
- repeated cross-project access;
- use after account disablement;
- certificate validation failure;
- and persistent event-forwarding failure.

## 54. Test event generation

Testing should verify:

- event occurs;
- correct event identifier;
- correct timestamp;
- correct acting identity;
- correct affected identity;
- correct object or record;
- correct project or scope;
- correct outcome;
- correct reason;
- correct severity;
- no secret leakage;
- safe handling of malicious input;
- correct correlation identifier;
- and correct destination.

## 55. Test positive and negative paths

The application should test:

- successful and failed authentication;
- successful and denied authorisation;
- account creation and disablement;
- role assignment and removal;
- privileged action;
- self-approval denial;
- record modification;
- import success and failure;
- export;
- invalid file;
- input-validation failure;
- API misuse;
- supplier access;
- emergency access;
- configuration change;
- logging change;
- and security-control failure.

Testing only ordinary success events is inadequate.

## 56. Test end-to-end event delivery

The application should verify:

- event generation;
- local formatting;
- transport;
- central receipt;
- parser;
- timestamp;
- field mapping;
- searchability;
- retention category;
- alert or use case where required;
- and incident-investigation usability.

A log statement in source code does not prove that the event reaches the monitoring platform.

## 57. Test failure and recovery

Testing should include:

- central log destination unavailable;
- network interruption;
- expired forwarding certificate;
- invalid schema;
- full local buffer;
- parser failure;
- clock skew;
- duplicate delivery;
- application restart;
- release deployment;
- and restoration from backup.

The application should demonstrate that failure is visible and that buffered events are recovered or reconciled.

## 58. Perform privacy and data-minimisation review

The application should periodically review event fields to ensure:

- each field has a legitimate purpose;
- personal data is minimised;
- free text is constrained;
- secrets are excluded;
- sensitive business data is not duplicated;
- retention remains appropriate;
- access remains proportionate;
- and monitoring value justifies the information collected.

## 59. Review event selection periodically

The application should review the event catalogue at the organisation-defined frequency and after:

- material release;
- new feature;
- new role;
- new API;
- new integration;
- new supplier;
- new export;
- architecture change;
- incident;
- penetration-test finding;
- vulnerability finding;
- business-process change;
- regulatory change;
- monitoring failure;
- or change to enterprise logging requirements.

The review should add, remove or refine events based on current risk and operational value.

## 60. Remove obsolete and noisy events carefully

The application may remove or reduce events that:

- no longer relate to active functions;
- duplicate better events;
- are too noisy to be useful;
- expose excessive sensitive data;
- are technically unreliable;
- or create disproportionate cost without security value.

Before removal, assess:

- monitoring dependencies;
- incident needs;
- audit requirements;
- retention;
- legal obligations;
- and whether the event should be improved rather than removed.

## 61. Manage logging limitations and exceptions

Where a legacy or commercial product cannot generate the required events, record:

- missing event;
- affected component;
- expected fields;
- actual capability;
- security and investigation impact;
- product or supplier constraint;
- compensating logs;
- monitoring;
- owner;
- approval;
- remediation, upgrade, wrapper or replacement plan;
- review date;
- and expiry date.

Examples include:

- no stable user identifier;
- no failed-authorisation events;
- no record-level audit trail;
- shared administrator identity;
- logs stored only locally;
- no forwarding health signal;
- proprietary binary logs;
- excessive secret leakage;
- missing API-client identity;
- no distinction between read and export;
- or no audit of supplier actions.

The limitation should be visible in the application addendum or risk process.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate identity, central SIEM, enterprise time synchronisation, managed hosting and established incident processes. They exclude enterprise SIEM engineering, long-term storage costs and major redevelopment of products with poor logging.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the application event catalogue** | Identify authentication, account, role, authorisation, privileged, workflow, record, import, export, file, API, supplier, emergency and control-failure events. | Summarise in the **SSP AU-02 statement** and maintain detail in the existing **event-logging specification**, **security design**, **ConOps** or **SyOps**. | **12–24 hours** |
| **2. Define mandatory event content and schema** | Specify stable identities, timestamp, component, environment, action, object, scope, outcome, reason, correlation and severity and define redaction rules. | Record in the **event schema**, **logging specification**, **API/interface design**, **data dictionary** and **SSP**. | **8–20 hours** |
| **3. Implement authentication, account and session events** | Generate success, failure, mapping, disablement, role, session, recovery and privileged-authentication events. | Evidence remains in the **identity/security design**, **source or product configuration**, **IA-02/AC-02 test report** and **SIEM onboarding records**. | **12–32 hours** |
| **4. Implement authorisation and privileged-action events** | Log denied access, cross-project attempts, privileged functions, administrative changes, support impersonation and emergency use. | Capture requirements in the **AC-03/AC-04/AC-05/AC-06 designs**, **role matrix**, **event catalogue** and **security test report**. | **16–40 hours** |
| **5. Implement business-record and workflow events** | Log creation, material change, approval, rejection, release, deletion, restoration, delegation and override for significant records and workflows. | Record in the **business-process design**, **workflow specification**, **data model**, **audit-history design** and **functional/security test report**. | **16–48 hours** |
| **6. Implement import, export, file and API events** | Log source, validation, counts, outcome, destination, bulk extraction, file decisions, API client and service identity activity. | Use the existing **interface specifications**, **file/import design**, **API design**, **AC-04 export design**, **event catalogue** and **test reports**. | **12–36 hours** |
| **7. Prevent secrets and excessive sensitive data in logs** | Apply structured logging, field allow-lists, redaction, safe identifiers and review of logs, traces, support bundles and errors. | Record controls in the **secure coding standard**, **logging specification**, **privacy review**, **code review**, **SAST/test results** and **SSP**. | **8–20 hours** |
| **8. Integrate events with the enterprise SIEM** | Use approved transport, authentication, encryption, schema, buffering, parser, ownership and health monitoring. | Evidence sits in the **SIEM onboarding record**, **interface design**, **certificate/service-account records**, **SyOps** and **operational acceptance evidence**. | **12–32 hours** |
| **9. Implement forwarding-failure and logging-health monitoring** | Detect event-volume gaps, queue growth, parser failures, expired credentials, local-buffer exhaustion and logging configuration changes. | Record in the **monitoring design**, **SI-04 use cases**, **SyOps**, **SIEM health checks** and **resilience test report**. | **8–20 hours** |
| **10. Protect local logs and audit configuration** | Restrict read, write and deletion, prevent application administrators concealing activity and control changes to logging settings. | Use the existing **CM-05/CM-06 configuration**, **role matrix**, **platform permissions**, **SyOps**, **change records** and **security test evidence**. | **6–16 hours** |
| **11. Define access, retention and handling categories** | Map application events to enterprise retention, privacy, access and legal requirements without duplicating corporate policy. | Record in the **logging specification**, **records schedule reference**, **privacy assessment**, **SSP** and **SIEM onboarding record**. | **4–10 hours** |
| **12. Test positive, negative and privileged events** | Verify event identity, object, outcome, reason, severity, safe content and generation for both successful and denied actions. | Add cases to the normal **unit**, **integration**, **security**, **operational acceptance** and **penetration test plans**. | **20–48 hours per major test cycle** |
| **13. Test end-to-end delivery and recovery** | Confirm generation, transport, parser, search, alerting, buffering, outage recovery, duplicate handling and release continuity. | Retain evidence in the **SIEM acceptance test**, **resilience test**, **release test**, **operational acceptance report** and **CA-07 review**. | **12–28 hours per major integration cycle** |
| **14. Review event selection and usefulness periodically** | Review new functions, incidents, threats, noisy events, monitoring gaps, privacy and continuing investigation needs. | Retain outcomes in established **service reviews**, **security reviews**, **CA-07 posture reports**, **incident lessons** or **application governance minutes**. | **8–16 hours per review** |
| **15. Update logging after material change** | Add or amend events, schemas, parsers, tests and monitoring when roles, workflows, APIs, integrations or privileged functions change. | Add the activity to the standard **change-impact assessment**, **release checklist**, **security design review** and **post-implementation review**. | **3–12 hours per material change** |
| **16. Document and manage logging limitations** | Record missing events, weak attribution, local-only logs, parser constraints or sensitive-data leakage with compensating controls and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP AU-02 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application with established enterprise SIEM services and a reasonable existing audit trail, initial application effort is commonly around **150–340 hours**.

Ongoing application effort is commonly around **6–20 hours per month**, plus release-driven changes, event reviews, incident support and major SIEM integration changes.

A simple commercial application with mature structured logging may require less. A legacy, thick-client, workflow-intensive or integration-heavy application with weak attribution, local-only logs or proprietary formats may require substantially more.

The estimates should not be added mechanically where activities overlap. AU-02 commonly shares implementation and evidence with:

- AU-03 content of audit records;
- AU-05 response to audit logging process failures;
- AU-06 audit record review, analysis and reporting;
- AU-08 time stamps;
- AU-09 protection of audit information;
- AU-12 audit record generation;
- AC-02 account management;
- AC-03 access enforcement;
- AC-04 information-flow enforcement;
- AC-05 separation of duties;
- IA-02 identification and authentication;
- SI-04 system monitoring;
- IR controls;
- CA-07 continuous monitoring; and
- CM-05 access restrictions for change.

---

## Suggested document placement

To avoid creating disconnected evidence, event-logging information should normally be distributed across established application and SDLC artefacts:

- **SSP:** AU-02 implementation approach, inherited enterprise logging, event categories, rationale, review frequency, integration and limitations.
- **ConOps or SyOps:** operational use, support access, verbose logging, forwarding failure, incident access and responsibilities.
- **Security architecture:** event producers, trust boundaries, transport, buffering, central destinations and health monitoring.
- **Event catalogue or logging specification:** event identifier, trigger, fields, severity, sensitivity, destination, alert use, retention category and test.
- **Data dictionary and schema repository:** event field definitions, controlled values, schema version and redaction rules.
- **Identity integration design:** user and service identifiers, authentication events, session references and token-validation outcomes.
- **Role/access matrix:** privileged logging functions, log viewers, audit administrators and separation of duties.
- **Business-process and workflow design:** record, approval, release, delegation and override events.
- **Interface and API specifications:** client, service identity, request, outcome, correlation and error events.
- **File and import specifications:** validation, quarantine, record counts, reconciliation and export events.
- **CM-05 and CM-06 records:** logging configuration, schema, destination, level, health checks and controlled changes.
- **SIEM onboarding records:** source, transport, parser, index, owner, use case, alert, retention category and acceptance evidence.
- **AU-05 and SI-04 evidence:** logging failure, queue, parser, certificate, volume and health monitoring.
- **Test plans and reports:** positive, negative, privilege, injection, forwarding, outage and recovery tests.
- **Incident records:** events used, gaps identified, evidence preservation and monitoring improvements.
- **Release records:** event schema changes, parser updates, SIEM validation and regression results.
- **Service and CA-07 reviews:** event usefulness, coverage, noise, gaps, privacy and outstanding limitations.
- **Risk register or application addendum:** missing events, weak attribution, local-only logs, proprietary formats and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide audit and logging policy;
- central SIEM and log-management platforms;
- enterprise event transport and storage services;
- enterprise retention and records-management requirements;
- central security-monitoring use cases;
- corporate incident-response operations;
- managed Windows EUC logging;
- server operating-system logs;
- shared database-platform logs;
- network, firewall, VPN and proxy logs;
- enterprise identity-provider logs;
- enterprise time synchronisation;
- central access control for log repositories;
- corporate privacy and legal-retention governance;
- enterprise SOC alert handling; and
- organisation-wide logging standards and schemas where defined.

The application team must still:

- define the application event catalogue;
- generate business and security events with reliable attribution;
- include stable identities, outcomes, objects and correlation;
- prevent secret and sensitive-data leakage;
- integrate with central logging;
- monitor event-generation and forwarding health;
- test event content and end-to-end delivery;
- review event usefulness after change and incidents; and
- formally manage application-specific logging gaps.

> **Key dividing line:** the enterprise collects, stores and monitors logs at scale; the application determines and generates the events needed to understand who did what, to which application object, under which authority, with what outcome and in what business context.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, AU-02 Event Logging.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, AU-02 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-92, Guide to Computer Security Log Management**.
4. National Institute of Standards and Technology, **NIST SP 800-92 Rev. 1, Cybersecurity Log Management Planning Guide**, Initial Public Draft.
5. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, current SP 800-53 and SP 800-53A catalogues.
