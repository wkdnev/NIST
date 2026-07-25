# IR-05 Incident Monitoring — Application Actions

## Purpose

For an IT application, IR-05 means the application must **track, document, maintain and report information about security incidents that affect, involve or originate from the application**.

The enterprise may provide the corporate incident-response policy, Security Operations Centre (SOC), SIEM, incident-management platform, forensic specialists, legal and privacy escalation, communications processes and enterprise reporting. Those capabilities are inherited. They do not, however, know the application’s detailed business processes, information structures, privileged functions, integrations, normal transaction patterns or the practical meaning of a suspicious application event.

The application must therefore be capable of:

- recognising when application activity may represent an incident;
- providing reliable application evidence;
- recording application-specific facts and impact;
- maintaining an accurate incident timeline;
- supporting containment, eradication and recovery;
- tracking affected components, records, users and interfaces;
- reporting status and decisions to the enterprise incident process;
- preserving relevant evidence;
- verifying corrective action; and
- feeding lessons back into the application’s design, controls and SDLC.

NIST IR-05 requires organisations to track and document system security incidents. NIST SP 800-61 Rev. 3 places incident response within wider cybersecurity risk management and emphasises preparation, detection, response, recovery and improvement across the organisation.

> **Core principle:** the enterprise manages the incident process; the application team provides the application-specific facts, evidence, expertise, containment options and corrective action needed to make that process effective.

---

## 1. Define what constitutes an application security incident

The application should identify the types of events and conditions that may constitute an application security incident or require incident triage.

Examples include:

- unauthorised access to restricted information;
- successful or attempted privilege escalation;
- misuse of administrative or support functions;
- unauthorised bulk export, printing or download;
- alteration or deletion of protected business records;
- approval or workflow bypass;
- compromised user or service identities;
- malicious or manipulated API requests;
- exploitation of an application vulnerability;
- tampering with application code, packages or configuration;
- disabling or evading application logging;
- disclosure of credentials, keys, tokens or certificates;
- unauthorised changes to access rules;
- suspicious use of supplier or support access;
- unexpected outbound communication;
- malware or hostile content processed by the application;
- integrity failure affecting data or audit history;
- unauthorised production data in non-production;
- retention or deletion failure with security or privacy impact;
- loss of application availability caused by hostile activity;
- repeated abnormal activity indicating coordinated misuse; and
- evidence that the application was used to attack another system.

The application should distinguish:

- a routine operational fault;
- a security-relevant event;
- a suspected incident;
- a confirmed incident; and
- a major or reportable incident.

The corporate process should define the official incident categories and severity model; the application should map its own scenarios to them.

## 2. Define application incident-monitoring responsibilities

The application should identify named roles for:

- application incident lead;
- technical subject-matter experts;
- business or information owner;
- application support;
- development or supplier support;
- access and identity support;
- database or integration support;
- evidence custodian;
- recovery lead; and
- communications liaison to the enterprise incident team.

Responsibilities should include who can:

- interpret application events;
- approve containment actions;
- disable a user, service or function;
- isolate an integration;
- suspend a workflow;
- take the application offline;
- preserve data or logs;
- authorise recovery;
- communicate business impact; and
- approve return to service.

The application should not create a parallel incident command structure. It should define how its specialists plug into the enterprise process.

## 3. Maintain application incident-monitoring scenarios

The application should maintain a concise set of incident-monitoring scenarios based on:

- threat assessment;
- business impact;
- information sensitivity;
- application roles;
- privileged functions;
- trust boundaries;
- interfaces;
- supplier access;
- previous incidents;
- penetration-test findings;
- vulnerability history; and
- known abuse cases.

Each scenario should identify:

- the suspicious condition;
- likely event sources;
- expected application evidence;
- initial severity;
- triage questions;
- likely affected information or function;
- immediate containment options;
- escalation route; and
- specialist contacts.

This information can sit within the SSP, SyOps, incident-response annex, monitoring use cases or operational runbook rather than in a separate standalone document.

## 4. Generate evidence that supports incident monitoring

The application should produce reliable evidence for security-relevant activity.

This may include:

- authentication and session events;
- access denials;
- privileged actions;
- role and permission changes;
- business-record creation, alteration, approval and deletion;
- export, download and bulk-processing activity;
- API requests and outcomes;
- service-identity use;
- configuration changes;
- security-control failures;
- file-processing activity;
- integrity-validation failures;
- application errors;
- scheduled-job execution;
- integration and message-processing events;
- administrative and support activity; and
- application health and deployment information.

Events should include enough context to determine:

- who or what acted;
- what happened;
- which record, component or interface was affected;
- when it happened;
- where it originated;
- whether it succeeded;
- which session, request or transaction was involved; and
- what policy or control triggered the event.

The application should not log passwords, full authentication tokens, private keys, recovery codes or unnecessary restricted content.

## 5. Ensure evidence can be correlated across the application

Multi-tier and integrated applications should support correlation across:

- thick client;
- browser or presentation tier;
- application service;
- API;
- messaging component;
- scheduled job;
- integration;
- database operation; and
- central identity or VPN event.

The application should use consistent:

- timestamps;
- user and service identifiers;
- application and environment identifiers;
- session identifiers;
- request or transaction identifiers;
- record identifiers;
- component names;
- event categories; and
- outcome codes.

A security analyst should be able to trace a suspicious business action from the initiating identity through the relevant application tiers without relying solely on source IP address.

## 6. Forward relevant evidence to the approved monitoring service

Security-relevant application events should be sent to the approved enterprise monitoring or logging service.

The application should:

- use the approved forwarding mechanism;
- protect event transmission;
- identify the application, environment and component;
- use enterprise time synchronisation;
- avoid duplicate or conflicting event feeds;
- test field parsing and mapping;
- monitor forwarding health;
- buffer safely where supported;
- raise failure notifications; and
- document evidence that cannot be forwarded centrally.

The application team remains responsible for confirming that the events are useful and interpretable after they reach the central platform.

## 7. Define incident triage information

When the enterprise incident team raises an alert, the application should be able to provide concise triage information.

This should normally include:

- application name and environment;
- affected component or function;
- affected user or service identity;
- affected project, record set or information type;
- event and transaction identifiers;
- first observed and last observed time;
- current status;
- relevant application version and configuration;
- whether activity was authorised;
- whether similar activity is normal;
- suspected entry point;
- likely scope;
- business impact;
- operational impact;
- information sensitivity;
- existing containment;
- evidence location;
- known related changes or releases; and
- application contact.

A generic statement such as “suspicious activity detected” is not enough for effective incident monitoring.

## 8. Track the application incident timeline

The application should maintain an accurate timeline of material application events and actions.

This may include:

- initial alert;
- suspicious activity;
- user and service activity;
- relevant configuration changes;
- releases and deployments;
- access changes;
- discovery time;
- escalation time;
- containment decisions;
- evidence collection;
- supplier contact;
- service restriction;
- recovery actions;
- validation;
- return to service; and
- follow-up actions.

The authoritative timeline should be maintained in the enterprise incident record, with application records referenced or attached rather than maintained as an unconnected duplicate.

## 9. Track affected application scope

The application team should identify and update the known or suspected scope of the incident.

This may include:

- application components;
- servers or instances by enterprise identifier;
- thick-client versions;
- user and service identities;
- privileged roles;
- projects or business units;
- records and attachments;
- database objects;
- files and exports;
- integrations;
- message queues;
- API clients;
- scheduled jobs;
- non-production environments;
- suppliers;
- certificates and secrets;
- backups; and
- downstream or upstream systems.

The team should distinguish:

- confirmed affected;
- suspected affected;
- assessed and not affected;
- unknown; and
- awaiting evidence.

Scope should be updated as new evidence becomes available.

## 10. Assess business and information impact

The application team should translate technical activity into application and business impact.

Consider:

- confidentiality of company, government, personal or other governed information;
- unauthorised alteration of business records;
- loss of traceability or audit history;
- impact on engineering, financial, safety or contractual decisions;
- incorrect approval or release;
- loss of availability;
- unreliable data;
- impact on connected systems;
- impact on suppliers or customers;
- records and retention implications;
- privacy consequences;
- legal or contractual notification triggers;
- recovery complexity; and
- reputational impact.

Enterprise incident teams should not be expected to infer the meaning of application records without help from the application and business owners.

## 11. Support containment decisions

The application should identify safe and proportionate containment options before an incident occurs.

Options may include:

- disable a user or service identity;
- revoke a session, token, certificate or API key;
- remove a role or project membership;
- disable an integration;
- block an API client;
- restrict an export or privileged function;
- place a record or workflow on hold;
- disable a scheduled job;
- switch the application to read-only mode;
- isolate an application tier;
- withdraw a thick-client package;
- disable a plugin or feature;
- redirect users to a safe service state;
- suspend supplier access;
- increase logging temporarily;
- preserve volatile or short-lived evidence; and
- take the application offline.

The application should document:

- who may approve each action;
- expected business impact;
- technical dependencies;
- rollback method;
- evidence consequences;
- recovery conditions; and
- emergency contacts.

Containment should not destroy evidence or cause greater harm without a conscious, documented decision.

## 12. Support evidence preservation

The application should help preserve relevant evidence in a trustworthy manner.

Evidence may include:

- application logs;
- audit records;
- configuration exports;
- database records;
- message and queue data;
- files and attachments;
- access-control mappings;
- service-identity records;
- session information;
- deployment artefacts;
- hashes and signatures;
- application memory or process evidence where authorised;
- thick-client package information;
- screenshots;
- reports;
- supplier records; and
- recovery copies.

The application should:

- preserve original evidence where practical;
- record collection time and collector;
- use approved storage;
- restrict access;
- maintain integrity;
- record transformations or exports;
- avoid unnecessary exposure of restricted content;
- apply legal or investigation holds where directed; and
- follow enterprise forensic and chain-of-custody procedures.

The application team should not perform uncontrolled forensic collection if specialist assistance is required.

## 13. Preserve short-lived and volatile application evidence

Some application evidence may disappear quickly.

Examples include:

- in-memory sessions;
- temporary tokens;
- transient queues;
- ephemeral containers or processes;
- temporary files;
- local client caches;
- short-retention debug logs;
- dynamic access mappings;
- failed-message stores;
- rapidly rotating audit files; and
- temporary deployment artefacts.

The application should identify such evidence in advance and define how it can be preserved or exported under incident direction.

## 14. Monitor containment effectiveness

After containment, the application should track whether:

- suspicious activity has stopped;
- alternative access paths remain;
- compromised identities continue to operate;
- queued or scheduled activity continues;
- copied credentials remain valid;
- malicious files or records remain accessible;
- integrations continue to propagate affected data;
- disabled functionality has been re-enabled;
- business users are bypassing restrictions;
- event flow remains operational; and
- containment has introduced data-integrity or availability problems.

Containment should be treated as a monitored state, not a one-off action.

## 15. Support eradication

The application should help identify and remove the incident’s cause and persistence.

Actions may include:

- remove malicious or unauthorised code;
- replace compromised packages;
- correct vulnerable application logic;
- patch or upgrade affected components;
- remove unauthorised accounts or roles;
- revoke credentials, tokens and certificates;
- remove malicious files or configuration;
- correct database changes;
- disable unauthorised plugins;
- rebuild from the approved baseline;
- repair logging and monitoring;
- correct insecure integrations;
- remove persistence from scheduled jobs;
- update detection rules; and
- verify supplier corrective action.

Eradication must be implemented through controlled change and release processes unless emergency procedures are invoked.

## 16. Support secure recovery

Recovery should return the application to a known, trusted and supportable state.

The application should verify:

- approved release and baseline;
- secure configuration;
- component and dependency versions;
- database integrity;
- access-control mappings;
- service identities;
- certificates and secrets;
- logging and monitoring;
- integrations;
- retention and holds;
- backups and restored data;
- privileged access;
- absence of the original exploit path;
- absence of unauthorised persistence; and
- successful business-operation testing.

Recovery should not merely restore availability. It should restore trustworthy operation.

## 17. Define return-to-service criteria

The application should define the evidence required before normal service resumes.

Criteria may include:

- incident scope understood sufficiently;
- immediate threat contained;
- affected credentials revoked;
- vulnerable component corrected or isolated;
- baseline and configuration verified;
- monitoring restored;
- required testing completed;
- data integrity validated;
- business owner accepts residual operational risk;
- enterprise incident lead agrees;
- supplier actions confirmed;
- recovery point approved; and
- follow-up actions assigned.

Where full remediation is not complete, temporary operation should be explicitly risk-approved and monitored.

## 18. Maintain the authoritative incident record

Application-specific incident information should be recorded in the enterprise incident-management system.

The record should include or reference:

- incident category;
- severity;
- application and environment;
- detection source;
- timeline;
- affected scope;
- information impact;
- business impact;
- indicators;
- evidence locations;
- containment actions;
- eradication actions;
- recovery actions;
- decisions and approvals;
- communications;
- supplier involvement;
- legal, privacy or regulatory input;
- open risks;
- corrective actions;
- retest evidence;
- lessons learned; and
- closure approval.

The application should avoid maintaining a separate spreadsheet or document as the primary incident record unless it is formally controlled and linked to the enterprise record.

## 19. Report incident status accurately

The application should provide timely status updates that distinguish:

- known facts;
- working hypotheses;
- unverified reports;
- confirmed scope;
- suspected scope;
- completed actions;
- failed actions;
- decisions required;
- blockers;
- business impact;
- technical impact; and
- next update time.

Status should not be overstated to create reassurance or understated to avoid escalation.

## 20. Coordinate supplier involvement

Where a supplier supports or develops part of the application, the application team should define:

- supplier incident contact;
- support and escalation route;
- contract or service obligations;
- evidence-sharing restrictions;
- approved access method;
- required response times;
- responsibilities for analysis and correction;
- handling of supplier vulnerabilities;
- notification expectations;
- confidentiality requirements;
- approval before supplier access; and
- verification of supplier corrective action.

Supplier case numbers, advice, artefacts and commitments should be referenced from the enterprise incident record.

Supplier involvement does not transfer accountability away from the application owner.

## 21. Track corrective actions after the incident

Incident closure should not end application remediation.

The application should track:

- code corrections;
- configuration changes;
- access changes;
- logging improvements;
- new alerts;
- architectural changes;
- dependency updates;
- supplier actions;
- documentation changes;
- updated tests;
- recovery improvements;
- process changes;
- risk decisions; and
- training or support changes.

Each action should have:

- owner;
- priority;
- target date;
- status;
- evidence;
- dependency;
- risk if delayed; and
- verification requirement.

These actions should be maintained in established defect, risk, POA&M, change or service-improvement records rather than a detached lessons-learned list.

## 22. Verify corrective action

Material corrective actions should be tested to confirm that:

- the original incident path is removed or acceptably constrained;
- the deployed application contains the correction;
- access controls remain effective;
- monitoring detects recurrence;
- no unacceptable regression was introduced;
- data and audit integrity are preserved;
- recovery remains viable; and
- associated documentation and baselines are updated.

A code change or closed supplier ticket is not by itself evidence that the incident risk has been resolved.

## 23. Conduct application-focused lessons learned

After a material incident, the application team should participate in the enterprise lessons-learned process and examine:

- why the activity was possible;
- why it was not prevented;
- how it was detected;
- whether evidence was sufficient;
- whether escalation was timely;
- whether containment options were effective;
- whether recovery was trustworthy;
- whether application documentation was accurate;
- whether supplier response was adequate;
- which assumptions were wrong;
- whether similar paths exist elsewhere; and
- which controls, tests and monitoring should change.

Lessons should be translated into owned actions and updates to the SSP, SyOps, ConOps, architecture, threat assessment, risk register, test plans and operational procedures.

## 24. Exercise incident-monitoring arrangements

The application should periodically test its incident-monitoring and support arrangements.

Exercises may include:

- tabletop scenario;
- simulated compromised user;
- suspicious bulk export;
- service-account misuse;
- unauthorised record alteration;
- vulnerable API exploitation;
- compromised supplier access;
- logging failure;
- malicious file processing;
- thick-client manipulation;
- certificate or secret compromise;
- integrity failure; and
- recovery from a trusted baseline.

The exercise should confirm:

- events are available;
- application specialists can interpret them;
- contacts respond;
- scope can be established;
- containment actions are understood;
- evidence can be preserved;
- business impact can be assessed;
- decisions can be approved; and
- corrective actions are captured.

## 25. Review incident-monitoring arrangements after change

The application should review its incident-monitoring arrangements after:

- major release;
- new interface;
- new information type;
- role or privilege change;
- new supplier;
- new thick-client capability;
- architecture change;
- monitoring change;
- recovery change;
- significant vulnerability;
- penetration-test finding;
- actual incident; and
- change to enterprise incident procedures.

New functions should not enter production without considering how an incident involving them would be detected, scoped, contained and investigated.

## 26. Manage application incident-monitoring limitations

Where the application cannot provide expected evidence, containment or tracking capability, it should record:

- the missing capability;
- affected component or function;
- likely incident impact;
- reason;
- available alternative evidence;
- compensating monitoring;
- containment limitations;
- supplier dependency;
- risk;
- owner;
- approval;
- remediation or replacement plan; and
- review or expiry date.

The limitation should be recorded in the application addendum or risk process and reflected in incident playbooks.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses the corporate incident-management system, SOC, SIEM, identity, service-management and change processes. They exclude enterprise incident operations, forensic investigation and remediation engineering.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define application incident scenarios and escalation criteria** | Identify the most credible application-specific incidents, expected evidence, likely impact, initial severity and escalation route. | Summarise scenarios in the **SSP IR-05 section** and record operational detail in the existing **SyOps**, **incident-response annex**, **threat assessment** or **application runbook**. | **8–16 hours** |
| **2. Define application incident roles and contacts** | Assign application, business, technical, supplier, recovery and evidence responsibilities and identify who can approve containment and return to service. | Record roles in the **SyOps**, **support model**, **ConOps**, **incident-response annex** and the contact section of the **SSP**. | **4–8 hours** |
| **3. Ensure required application evidence is generated and forwarded** | Configure security-relevant events with useful identity, action, target, outcome and correlation context and forward them to the approved monitoring service. | Define requirements in the **SSP AU-02/SI-04/IR-05 sections**, **security design** and **event specification**. Verify through the normal **system/security test report** and **SIEM onboarding evidence**. | **12–32 hours** |
| **4. Define application triage and impact information** | Establish the minimum facts needed to assess affected users, services, records, projects, information types, components and business impact. | Include the triage fields in the **incident-response annex**, **SyOps**, **support runbook** or the enterprise **incident template** used by the application team. | **6–12 hours** |
| **5. Define containment options and approval routes** | Document safe actions such as disabling identities, integrations, exports, jobs, features or service access, including business impact and rollback. | Record options in the **SyOps**, **ConOps**, **incident-response annex**, **recovery plan** and relevant **operational runbook**. | **8–16 hours** |
| **6. Define evidence-preservation requirements** | Identify relevant logs, records, configuration, files, queues, access mappings and short-lived evidence and how they can be preserved through approved processes. | Record this in the **incident-response annex**, **SyOps**, **logging design**, **retention design** or existing **forensic/evidence procedure** referenced by the SSP. | **6–12 hours** |
| **7. Integrate application incident facts into the enterprise incident record** | Use the corporate incident system as the authoritative record and attach or reference application timelines, scope, evidence, decisions and actions. | Evidence is the normal **enterprise incident record**, with linked **change records**, **risk records**, **supplier cases** and **test evidence**. | **2–6 hours per incident, excluding investigation** |
| **8. Support scope and impact assessment** | Use application architecture, inventory, access model, data flows and transaction context to identify confirmed, suspected and unaffected components and information. | Record findings directly in the **enterprise incident record**, supported by the existing **architecture**, **CM-08 inventory**, **role matrix**, **data-flow design** and **business impact assessment**. | **4–16 hours per incident** |
| **9. Support secure containment, eradication and recovery** | Provide application expertise, execute approved actions through change control, verify baseline, configuration, access, integrity and monitoring before return to service. | Evidence sits in the **incident record**, **emergency change**, **release record**, **recovery plan/test report**, **CM-02 baseline** and **operational acceptance record**. | **8–32 hours per incident, excluding engineering remediation** |
| **10. Track corrective actions and verify closure** | Assign owners and dates for application fixes, monitoring changes, access changes, supplier actions and documentation updates and retest material corrections. | Use existing **risk register**, **defect tracker**, **POA&M**, **problem record**, **change record** and **security test report**, referenced from the incident record. | **4–12 hours per material action, excluding remediation** |
| **11. Perform application-focused lessons learned** | Review detection, evidence, escalation, containment, recovery and root cause and convert conclusions into controlled improvement actions. | Capture decisions in the enterprise **lessons-learned record**, **service-improvement plan**, **risk register**, **SSP change history** and normal **SDLC backlog**. | **4–8 hours per material incident** |
| **12. Exercise application incident-monitoring arrangements** | Run a tabletop or technical exercise covering alert interpretation, scope, impact, containment, evidence, contacts and recovery decisions. | Use the normal **exercise plan and report**, **security test report**, **operational resilience exercise** or **annual service review**, referenced from the SSP. | **12–24 hours per exercise** |
| **13. Review incident-monitoring coverage after material change** | Reassess scenarios, event coverage, contacts, containment and evidence whenever application architecture, interfaces, roles or data materially change. | Add the review to the standard **change-impact assessment**, **security design review**, **release checklist** or **post-implementation review**. | **3–8 hours per material change** |
| **14. Document and manage monitoring limitations** | Record unavailable evidence, weak correlation, supplier restrictions or limited containment, with compensating controls and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, with the **SSP IR-05 section** referencing material limitations. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application with established enterprise incident and monitoring services, initial application setup is commonly around **80–170 hours**.

Ongoing effort is event-dependent. A routine false-positive triage may require less than an hour of application support, while a confirmed material application incident may require tens or hundreds of hours across analysis, containment, recovery and remediation. The table estimates cover the application’s monitoring, coordination and evidence contribution, not the full incident cost.

The estimates should not be added mechanically where activities overlap. IR-05 should reuse event definitions, architecture, inventories, role models, recovery procedures, supplier records and test evidence already maintained for AU-02, SI-04, CM-02, CM-08, AC controls and contingency planning.

---

## Suggested document placement

To avoid creating disconnected evidence, application incident-monitoring information should normally be distributed across established application and SDLC artefacts:

- **SSP:** IR-05 implementation approach, inherited enterprise incident services, application scenarios, evidence sources, responsibilities, reporting route and limitations.
- **ConOps or SyOps:** operating roles, escalation, containment, support, supplier involvement, degraded modes and recovery responsibilities.
- **Incident-response annex or operational runbook:** application triage questions, evidence locations, containment options, approval routes and contact details.
- **Security architecture:** components, trust boundaries, event sources, correlation paths and containment points.
- **Data-flow and information register:** affected data types, storage locations, exports, integrations and information owners.
- **CM-08 component inventory:** components, suppliers, environments and accountable owners used for incident scoping.
- **CM-02 baseline and CM-06 configuration:** known trusted state used for comparison, eradication and recovery.
- **Role and access matrix:** user, privileged, support and service access used for scope and misuse analysis.
- **AU-02 and SI-04 evidence:** event definitions, forwarding, parsing, alerting and monitoring health.
- **Recovery plan and recovery test report:** trusted restoration, validation and return-to-service evidence.
- **Enterprise incident record:** authoritative timeline, scope, impact, evidence, actions, decisions and communications.
- **Change and release records:** containment, eradication and recovery changes.
- **Risk register, POA&M, defect tracker or problem record:** corrective actions, accepted risk and overdue treatment.
- **Supplier record:** supplier contacts, case references, obligations, evidence and corrective commitments.
- **Test and exercise reports:** incident exercises, retests and verification of corrective actions.
- **SSP change history and SDLC backlog:** lessons translated into enduring control, design and testing improvements.
- **Application addendum:** unavailable evidence, supplier constraints, limited containment and other non-standard arrangements.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate incident-response policy and severity model;
- enterprise SOC and incident command;
- central SIEM and alert management;
- enterprise incident-management platform;
- enterprise forensic capability and chain-of-custody process;
- corporate legal, privacy, regulatory and communications escalation;
- central threat intelligence;
- enterprise identity, EDR, network, VPN and infrastructure evidence;
- organisation-wide incident reporting;
- executive and external communications;
- enterprise crisis management;
- corporate evidence-retention standards;
- enterprise malware analysis;
- corporate supplier and contract escalation;
- organisation-wide lessons-learned governance; and
- enterprise incident metrics and reporting.

The application team must still:

- define application-specific incident scenarios;
- provide reliable application evidence;
- interpret application events and business meaning;
- establish affected application scope;
- assess information and operational impact;
- identify safe containment options;
- support evidence preservation;
- support eradication and secure recovery;
- track application corrective actions; and
- update the SSP, design, tests and operational procedures after incidents.

> **Key dividing line:** the enterprise owns and coordinates the incident-response process; the application owns the application-specific knowledge, evidence, containment capability and corrective action required to investigate and resolve incidents involving the business application.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, IR-05 Incident Monitoring.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, IR-05 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-61 Rev. 3, Incident Response Recommendations and Considerations for Cybersecurity Risk Management: A CSF 2.0 Community Profile**.
4. National Institute of Standards and Technology, **NIST Cybersecurity Framework 2.0**, Detect, Respond and Recover Functions.
5. National Institute of Standards and Technology, **NIST SP 800-92, Guide to Computer Security Log Management**.
