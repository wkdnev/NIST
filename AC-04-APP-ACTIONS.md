# AC-04 Information Flow Enforcement — Application Actions

## Purpose

For an IT application, AC-04 means the application must **control where information is allowed to move, how it may move, in what form, and under which conditions**.

This is different from AC-03 Access Enforcement:

- **AC-03** asks whether a user, service or process is authorised to access a resource or perform an action.
- **AC-04** asks whether the resulting information flow is permitted between sources, destinations, projects, environments, components, users or security domains.

A user may be authorised to view information but still not be authorised to export it, copy it to another project, include it in a report, send it to an integration, move it into a lower environment or disclose it to another information community.

The enterprise may provide network segmentation, firewalls, email controls, managed file transfer, data-loss prevention, corporate identity, VPN, endpoint controls and central monitoring. Those services are inherited. They do not understand the application’s detailed information model, project boundaries, record relationships, workflow state, handling markings or the business meaning of an export, report or integration.

The application must therefore define, implement, test and maintain its own information-flow policies across:

- application screens and functions;
- projects, programmes, cases or data partitions;
- reports and dashboards;
- search and autocomplete;
- imports and exports;
- APIs;
- messages and events;
- file transfers;
- integrations;
- thick clients;
- databases;
- lower environments;
- support functions;
- logs;
- notifications;
- generated files; and
- administrative and recovery processes.

NIST AC-04 requires approved authorisations for controlling the flow of information within the system and between connected systems. NIST’s supplemental guidance distinguishes information-flow enforcement from ordinary access control and gives examples such as preventing information from moving between security domains, blocking export of sensitive information and enforcing one-way or policy-governed flows. NIST’s ABAC guidance also supports decisions based on attributes of the subject, object, requested action and environment, while zero-trust guidance rejects implicit trust based solely on network location. citeturn167800search0turn167800search1turn167800search2turn167800search6

> **Core principle:** information should move only to an approved destination, for an approved purpose, in an approved form, through an approved path, and only while the relevant policy conditions remain satisfied.

---

## 1. Define the application’s information-flow policy

The application should define the permitted and prohibited flows for its information.

The policy should identify:

- information types;
- source;
- destination;
- initiating user, service or process;
- permitted operation;
- business purpose;
- permitted environment;
- permitted recipient or information community;
- required attributes;
- transformation or filtering requirements;
- approval requirements;
- handling restrictions;
- logging and monitoring;
- retention or disposal conditions; and
- prohibited onward transfer.

The policy should be understandable to both business owners and technical teams.

A statement such as “access is role-based” is not an information-flow policy.

## 2. Identify information types and handling characteristics

The application should identify the information that requires flow control.

Examples include:

- engineering requirements;
- design records;
- controlled technical information;
- government information;
- contract information;
- personal data;
- commercially sensitive information;
- supplier information;
- security configuration;
- credentials and secrets;
- audit information;
- vulnerability information;
- source code;
- test evidence;
- incident information;
- reports;
- attachments;
- metadata; and
- derived or aggregated information.

For each material type, identify:

- owner;
- sensitivity;
- classification or handling marking;
- project, programme or case;
- permitted recipients;
- permitted environments;
- export restrictions;
- supplier restrictions;
- retention;
- disclosure constraints; and
- whether derived information inherits the same restrictions.

## 3. Identify all information-flow paths

The application should identify every path through which information may move.

This normally includes:

- screen display;
- search results;
- autocomplete;
- dashboards;
- reports;
- print;
- clipboard;
- download;
- export;
- email or notification;
- file attachment;
- API response;
- API submission;
- message queue;
- event stream;
- database replication;
- batch job;
- data warehouse or reporting feed;
- file transfer;
- thick-client cache;
- local working file;
- integration;
- backup;
- recovery;
- log;
- diagnostic output;
- supplier support package;
- archive;
- migration;
- test-data refresh; and
- administrative extraction.

A flow should not be omitted merely because it is indirect or operational rather than user-facing.

## 4. Distinguish access from flow

The application should explicitly identify cases where access is permitted but movement is restricted.

Examples include:

- a user may view a requirement but not export it;
- a reviewer may read a record but not copy it into another project;
- a support user may view masked diagnostic information but not the underlying business content;
- a service may read data for validation but not persist it elsewhere;
- a report may show totals but not individual records;
- a user may download a controlled document only in a protected form;
- production data may be used operationally but not copied to test;
- audit records may be viewed but not included in ordinary reports; and
- a project administrator may manage membership but not transfer records between projects.

This distinction should appear in requirements, design, role matrices and tests.

## 5. Enforce project, programme, case or tenant boundaries

Where one application hosts several information communities, it should prevent information flowing between them unless explicitly approved.

The application should enforce boundaries across:

- record access;
- search;
- reporting;
- export;
- attachment access;
- notifications;
- workflow;
- audit history;
- caches;
- indexes;
- batch jobs;
- data extracts;
- APIs;
- analytics;
- administrative tools; and
- support functions.

The application should prevent:

- changing a project identifier to access another project;
- cross-project search leakage;
- report joins across restricted partitions;
- autocomplete revealing protected names;
- counts revealing the existence of records;
- attachments being accessed outside the parent record’s scope;
- background jobs processing data outside their assigned partition; and
- administrators silently moving records across boundaries.

Logical information segregation must be enforced even where all information is stored in the same database or platform.

## 6. Use data attributes to enforce policy

Where role-based controls alone are insufficient, the application should use trusted attributes such as:

- project;
- programme;
- case;
- contract;
- business unit;
- owner;
- classification;
- handling caveat;
- nationality;
- clearance;
- need-to-know;
- supplier relationship;
- record state;
- legal hold;
- information type;
- creation source;
- retention status; and
- approved destination.

NIST describes ABAC as evaluating subject, object, operation and sometimes environmental attributes against policy rules. NIST SP 800-205 further stresses that confidence in an access decision depends on the accuracy, integrity and timely availability of the attributes used. citeturn167800search1turn167800search17turn167800search30

The application should:

- define each attribute;
- identify its authoritative source;
- restrict who may change it;
- validate allowed values;
- handle missing or conflicting values safely;
- record changes;
- propagate changes consistently;
- prevent user-supplied attribute substitution; and
- re-evaluate flows when attributes change.

## 7. Deny flows by default

The normal policy should be **deny unless an approved rule permits the flow**.

This means:

- new interfaces do not automatically receive data;
- new report fields are not automatically exposed;
- new projects are isolated by default;
- new integrations receive no data until approved;
- new export functions begin disabled;
- missing or invalid markings cause restriction;
- unknown destinations are rejected;
- unsupported transformations are blocked;
- failed policy lookups do not permit unrestricted transfer; and
- temporary flows expire automatically where practical.

“Allow unless specifically prohibited” is unsuitable where information boundaries matter.

## 8. Enforce flow controls at trusted application layers

Information-flow enforcement should occur at the server, service, database policy, API gateway or other trusted component that controls the actual transfer.

The application should not rely solely on:

- hidden buttons;
- disabled menus;
- client-side filtering;
- thick-client logic;
- URL secrecy;
- user instructions;
- internal network location;
- spreadsheet protection;
- report conventions;
- manual data-cleaning expectations; or
- downstream recipients behaving correctly.

Every material flow should be checked before information crosses the relevant boundary.

## 9. Control search and discovery

Search functions can disclose information even when direct record access is blocked.

The application should ensure that:

- indexes are partition-aware;
- results are filtered before display;
- autocomplete respects information boundaries;
- snippets do not reveal restricted text;
- counts do not reveal protected records;
- facets and aggregations are filtered;
- saved searches cannot outlive access;
- search exports enforce the same rules;
- cached results are invalidated after access change; and
- diagnostic or administrative search is separately controlled.

A “no results” response may be safer than confirming that a protected record exists.

## 10. Control reports, dashboards and analytics

Reports and analytics should enforce the same information-flow policy as transactional screens.

The application should:

- restrict report datasets;
- filter by authorised project or information scope;
- prevent cross-boundary joins;
- control drill-down;
- control scheduled report distribution;
- restrict recipients;
- protect generated files;
- remove unauthorised fields;
- prevent formula or template manipulation;
- control report parameters;
- mark or label outputs where required;
- limit aggregate disclosure where small groups reveal individuals or sensitive records;
- expire cached reports; and
- log material report generation and distribution.

A reporting database or warehouse must not become an ungoverned copy of application information.

## 11. Control export, download, print and clipboard paths

High-volume and portable outputs require stronger controls.

The application should:

- restrict export to approved roles;
- enforce information scope at export time;
- permit only required formats;
- limit volume;
- apply row, field and attachment filtering;
- apply markings or metadata;
- prevent unapproved cross-project exports;
- restrict bulk download;
- record purpose or approval where proportionate;
- log the user, scope, format and outcome;
- protect generated files;
- expire download links;
- prevent predictable URLs;
- restrict printing where required;
- disable clipboard functions in high-risk workflows where technically justified; and
- prevent export from support or impersonation sessions unless explicitly authorised.

An export is a new information flow and should not be treated as merely another screen view.

## 12. Control notifications and messaging

Notifications can unintentionally disclose information outside the authorised application context.

The application should:

- minimise sensitive content in email and message notifications;
- avoid including restricted attachments unless approved;
- validate recipients;
- respect project and role changes;
- prevent notification to former members;
- use approved internal messaging channels;
- avoid placing secrets or sensitive information in URLs;
- use expiring or authenticated links;
- suppress protected data from subject lines;
- handle distribution lists carefully;
- prevent lower environments from sending production-style notifications;
- log material distribution; and
- support recall or corrective action where feasible.

A notification should direct an authorised user back to the protected application rather than reproduce the full sensitive record where practical.

## 13. Control APIs and integrations

Every API or integration should have a defined information-flow contract.

The application should document and enforce:

- authorised caller;
- authorised destination;
- permitted records;
- permitted fields;
- permitted operations;
- direction;
- frequency;
- volume;
- purpose;
- authentication;
- authorisation;
- data minimisation;
- validation;
- encryption;
- error handling;
- retention;
- onward-transfer restrictions;
- monitoring; and
- termination process.

The application should prevent:

- over-broad API responses;
- undocumented fields;
- arbitrary query expansion;
- cross-project extraction;
- wildcard access;
- excessive pagination;
- unrestricted bulk endpoints;
- caller-controlled destinations;
- unapproved webhooks;
- insecure fallback; and
- lower-environment access to production data.

## 14. Control message queues and event streams

Applications using message brokers or event streams should restrict both publication and consumption.

The application should:

- define approved producers and consumers;
- restrict topics and queues;
- minimise message content;
- apply project or tenant context;
- validate schemas;
- prevent unauthorised subscriptions;
- control replay;
- control retention;
- protect dead-letter queues;
- avoid secrets in messages;
- restrict administrative browsing;
- log material publication and consumption;
- remove obsolete consumers; and
- prevent one consumer from receiving another information community’s messages.

A trusted broker does not make every message flow permissible.

## 15. Control file transfers

File-based interfaces should enforce:

- approved sender;
- approved recipient;
- approved location;
- approved format;
- content and schema validation;
- malicious-code scanning;
- encryption where required;
- information scope;
- reconciliation;
- duplicate handling;
- partial-transfer handling;
- retention;
- deletion;
- logging; and
- expiry of temporary transfer arrangements.

The application should prevent ordinary users from selecting arbitrary destinations or bypassing the managed transfer route.

## 16. Control movement between production and non-production

Production information should not flow into development, test, training or demonstration environments unless specifically approved.

The application should:

- prohibit default production-to-test copying;
- use synthetic data where practical;
- mask, redact or transform approved extracts;
- remove direct identifiers where required;
- control who can initiate the transfer;
- document the purpose;
- limit the data set;
- restrict the destination;
- protect transfer and storage;
- set a retention period;
- prevent onward transfer;
- verify deletion;
- record approval; and
- reassess whether the lower environment provides adequate protection.

Test systems should not become a quiet side door around production controls.

## 17. Control supplier and support flows

Supplier and support personnel may need diagnostic information, but the application should minimise and control what is shared.

The application should:

- provide the minimum data required;
- mask or redact business information;
- avoid sharing production databases or unrestricted exports;
- use approved transfer paths;
- require a case or purpose;
- identify the recipient;
- apply confidentiality and contractual controls;
- restrict onward transfer;
- set retention and deletion requirements;
- log the disclosure;
- review supplier access;
- use synthetic reproductions where possible; and
- require approval for exceptional disclosure.

Supplier access to the platform should not automatically permit supplier access to all business information.

## 18. Control logs, diagnostics and error messages

Logs and diagnostics can create unintended secondary information flows.

The application should prevent:

- passwords in logs;
- full tokens;
- private keys;
- recovery codes;
- unnecessary personal information;
- complete restricted records;
- sensitive query parameters;
- excessive request or response bodies;
- unredacted database errors;
- stack traces to ordinary users;
- secrets in configuration dumps;
- sensitive content in health endpoints; and
- unrestricted support downloads.

The application should:

- define approved fields;
- mask or redact where appropriate;
- separate security logs from business content;
- restrict log access;
- control forwarding destinations;
- retain only required information; and
- test that error paths do not disclose protected information.

## 19. Control backups, archives and recovery flows

Backup and recovery operations can move large quantities of information outside ordinary application paths.

The application should:

- identify which information is included;
- use approved backup destinations;
- preserve project and handling context where needed;
- restrict restoration destinations;
- prevent restoration into unapproved lower environments;
- protect exports used for recovery;
- control supplier access;
- log restoration;
- verify deletion of temporary recovery copies;
- ensure recovery does not remove access restrictions; and
- confirm that restored information retains appropriate markings and permissions.

## 20. Apply approved transformation, filtering and sanitisation

Where information is permitted to cross a boundary only after transformation, the application should define and test the transformation.

Examples include:

- masking;
- redaction;
- aggregation;
- field removal;
- pseudonymisation;
- tokenisation;
- format conversion;
- removal of metadata;
- image sanitisation;
- document content disarm;
- de-identification;
- truncation;
- one-way summary generation; and
- conversion from detailed to releasable output.

The application should:

- define the intended result;
- protect the transformation rules;
- prevent bypass;
- validate output;
- test edge cases;
- log failures;
- handle unprocessable content safely; and
- confirm that derived information does not reveal the protected source through inference or residual metadata.

## 21. Preserve markings and handling metadata

Where information carries classification, handling, project or ownership attributes, the application should preserve or deliberately transform them when information moves.

The application should prevent:

- loss of classification on export;
- project tags being dropped;
- attachments losing parent-record restrictions;
- reports omitting required markings;
- derived data losing provenance;
- messages being published without partition context;
- copied records defaulting to a less restrictive state; and
- imports overwriting handling attributes without approval.

Markings should support enforcement rather than exist only as visual labels.

## 22. Control copying, cloning, linking and derived records

Applications often create new records from existing information.

The application should define whether users may:

- copy;
- clone;
- duplicate;
- link;
- merge;
- split;
- re-parent;
- move;
- derive;
- quote;
- reference; or
- translate

information across projects or information communities.

The application should:

- re-evaluate authorisation;
- preserve or increase restrictions;
- prevent silent weakening;
- record provenance;
- control attachments;
- control inherited permissions;
- prevent orphaned copies;
- maintain traceability; and
- log high-risk transfers.

## 23. Prevent inference and aggregation leakage

Even where individual records are protected, aggregated or correlated information may reveal sensitive facts.

The application should consider:

- small population counts;
- trend reports;
- cross-project analytics;
- timing information;
- record identifiers;
- status indicators;
- metadata;
- existence checks;
- error differences;
- sequential identifiers;
- search suggestions; and
- combined datasets.

Where risk warrants, the application should apply:

- minimum group sizes;
- suppression;
- rounding;
- delayed publication;
- field minimisation;
- restricted analytics roles;
- query limits; and
- review of derived outputs.

## 24. Enforce one-way or tightly constrained flows where required

Some flows should be one-way or permit only a restricted response.

Examples include:

- publishing approved reports to a wider audience;
- sending events to central monitoring;
- exporting sanitised data from a restricted project;
- transferring release artefacts into production;
- sending backup data to protected storage; and
- receiving approved reference data without allowing reverse extraction.

Where strong one-way enforcement is required, the application should define whether it is achieved through application logic, managed transfer, network architecture or specialised hardware. NIST AC-04 includes enhancements addressing one-way mechanisms and other specialised flow-control techniques. citeturn167800search8turn167800search15

## 25. Re-evaluate flow decisions when context changes

Information-flow permission should be re-evaluated when:

- user role changes;
- project membership changes;
- record classification changes;
- ownership changes;
- workflow state changes;
- recipient status changes;
- contract or supplier relationship ends;
- destination changes;
- token or service scope expires;
- legal hold is applied;
- incident restrictions are imposed;
- data is reclassified;
- the interface is changed; or
- the permitted purpose ends.

Cached permissions and pre-generated reports should not continue to provide access indefinitely after the relevant policy changes.

## 26. Protect flow-policy configuration

The following are security-critical and should be protected:

- project membership;
- classification values;
- export permissions;
- recipient lists;
- transformation rules;
- destination allow-lists;
- API scopes;
- message subscriptions;
- report distribution;
- data-masking rules;
- lower-environment refresh rules;
- supplier disclosure settings;
- workflow transitions;
- service identities; and
- feature flags that enable transfers.

Only approved roles or controlled deployment processes should change them.

Changes should be:

- attributable;
- approved;
- tested;
- logged;
- reversible; and
- included in configuration and baseline control.

## 27. Fail safely when flow controls cannot make a decision

The application should deny or safely hold the flow when:

- the information classification is missing;
- project ownership is unknown;
- recipient validation fails;
- a policy service is unavailable;
- destination identity cannot be verified;
- a transformation fails;
- masking is incomplete;
- message schema is invalid;
- export scope cannot be resolved;
- an attachment’s parent context is missing;
- a lower environment is not recognised;
- a service token is invalid; or
- flow-policy configuration is inconsistent.

The application should not default to the least restrictive classification or broadest destination.

## 28. Log information-flow decisions and violations

The application should record material events such as:

- permitted and denied exports;
- cross-project transfer attempts;
- bulk download;
- report distribution;
- API data extraction;
- message publication;
- file transfer;
- lower-environment data movement;
- supplier disclosure;
- flow-policy changes;
- classification changes;
- masking or transformation failure;
- override;
- exceptional release;
- blocked destination;
- repeated policy violations; and
- administrative movement of records.

Events should include:

- acting identity;
- source;
- destination;
- information type;
- project or partition;
- action;
- volume or scope;
- outcome;
- policy reason;
- time;
- component; and
- approval or incident reference where applicable.

Logs should not themselves create an uncontrolled copy of the transferred information.

## 29. Monitor for anomalous or prohibited flows

The application should support detection of:

- unusual export volume;
- repeated denied transfers;
- unexpected destinations;
- cross-project access patterns;
- supplier access outside approved windows;
- production data in lower environments;
- dormant integration activity;
- excessive report generation;
- unusual API pagination or extraction;
- changes to flow rules;
- loss of classification or project tags;
- unauthorised notification recipients;
- new message consumers;
- unexpected bulk copying; and
- attempts to bypass masking or sanitisation.

## 30. Test information-flow enforcement

Testing should cover both permitted and prohibited flows.

The test set should include, where relevant:

- authorised project-to-project transfer;
- prohibited cross-project transfer;
- export with excessive scope;
- report field suppression;
- search leakage;
- autocomplete leakage;
- attachment access;
- scheduled report recipients;
- API over-fetching;
- message subscription isolation;
- lower-environment transfer;
- supplier disclosure;
- masked output;
- failed sanitisation;
- missing classification;
- changed role or project membership;
- stale cached report;
- copied or cloned record;
- logs and error messages;
- bulk download;
- unauthorised destination;
- flow-control service failure; and
- administrator override.

Testing should validate the actual data received, not merely the visible interface behaviour.

## 31. Review flows after material change

The application should reassess information-flow policy after:

- new interface;
- new report;
- new export;
- new integration;
- new supplier;
- new project type;
- new information type;
- change to classification or handling rules;
- migration;
- new analytics;
- thick-client change;
- new lower environment;
- change to support model;
- security incident;
- penetration-test finding;
- major product upgrade; or
- change to enterprise data-sharing rules.

The SSP, architecture, data-flow diagrams, interface specifications, tests and risk records should remain aligned.

## 32. Remove obsolete flows

When a report, integration, supplier, project, endpoint or business process is retired, the application should:

- remove the transfer configuration;
- remove destination allow-lists;
- revoke service identities and API scopes;
- stop scheduled reports;
- remove message consumers;
- stop file transfers;
- remove obsolete exports;
- delete temporary copies where required;
- update inventories and diagrams;
- withdraw firewall or proxy rules where applicable;
- update monitoring; and
- verify that the flow is no longer possible.

## 33. Manage information-flow exceptions

Where a legacy or commercial product cannot enforce the required flow rule, record:

- the affected information;
- source;
- destination;
- required rule;
- actual behaviour;
- business justification;
- exposure;
- affected users or systems;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, isolation, upgrade or replacement plan; and
- review or expiry date.

Examples include:

- report engine unable to enforce project filtering;
- unavoidable broad export;
- direct database reporting;
- inability to preserve markings;
- shared message topic;
- weak lower-environment separation;
- supplier diagnostic export;
- inability to prevent clipboard use; or
- coarse-grained data masking.

The exception should be visible in the application addendum or risk process, not buried in a support note.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate identity, managed network services, central logging, standard SDLC and established data-handling policy. They exclude enterprise DLP engineering, network implementation and major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define information types, owners and permitted destinations** | Identify the material information handled by the application, its sensitivity, project or business scope, approved recipients and prohibited destinations. | Summarise the approach in the **SSP AC-04 statement** and maintain detail in the existing **information register**, **data model**, **ConOps**, **SyOps** or **data-handling design**. | **6–12 hours** |
| **2. Map all material information-flow paths** | Identify screens, search, reports, notifications, exports, APIs, messages, files, integrations, logs, backups and lower-environment transfers. | Use the existing **data-flow diagrams**, **system context diagram**, **interface control documents**, **architecture** and **release documentation**, referenced from the SSP. | **8–20 hours** |
| **3. Define an approved information-flow policy** | For each material flow, define source, destination, purpose, authorised actor, permitted data, conditions, transformation, monitoring and expiry. | Record the policy in the **security design**, **business/security requirements**, **interface specifications**, **role matrix** and **SSP** rather than creating a disconnected register. | **12–28 hours** |
| **4. Enforce project, case or data-partition boundaries** | Apply trusted server-side filters to records, attachments, search, reports, APIs, indexes, caches and background jobs. | Capture the design in the **security architecture**, **data model**, **AC-03/AC-04 SSP sections** and normal **SDLC requirements**. Verify in the **security test report**. | **20–60 hours** |
| **5. Restrict exports, downloads, reports and bulk movement** | Limit authorised roles, fields, records, volume, format, recipients and destination and log high-impact transfers. | Define requirements in the **business process design**, **role matrix**, **report/export specification**, **SyOps** and **SSP**. Retain test evidence in the normal **functional/security test report**. | **12–32 hours** |
| **6. Control APIs, messages and file transfers** | Enforce approved callers, destinations, fields, schemas, scopes, volume, retention and onward-transfer restrictions. | Record controls in the **interface control document**, **API specification**, **message schema**, **file-transfer design**, **security design** and **integration test report**. | **16–48 hours** |
| **7. Control production-to-non-production movement** | Prohibit uncontrolled copying, use synthetic or masked data, limit scope, record approval, restrict retention and verify deletion. | Record the process in the **environment strategy**, **data-masking design**, **SyOps**, **test-data procedure**, **SSP** and normal **change or refresh records**. | **8–24 hours** |
| **8. Minimise notifications, logs and diagnostic disclosure** | Keep sensitive content out of notifications and errors, mask logs and diagnostics and use authenticated links back to the application. | Capture requirements in the **logging specification**, **notification design**, **error-handling design**, **SyOps** and **SSP AU-02/AC-04 sections**. | **6–16 hours** |
| **9. Preserve classification, project and provenance attributes** | Carry trusted markings and ownership context through copies, exports, reports, messages and derived records and prevent silent weakening. | Record attribute definitions in the **data model**, **security design**, **interface specifications**, **CM-06 configuration** and **SSP**. | **8–24 hours** |
| **10. Apply masking, redaction or other approved transformation** | Remove, aggregate, pseudonymise or sanitise information before it crosses specified boundaries and verify the resulting output. | Define transformation rules in the **data-handling design**, **report specification**, **test-data design**, **SyOps** and **test report**. | **12–40 hours** |
| **11. Fail closed when flow decisions or transformations fail** | Deny or hold transfers when classification, destination, recipient, policy or transformation cannot be validated. | Record failure behaviour in the **security design**, **SyOps**, **interface specification** and **SSP**. Verify through the normal **resilience and security test report**. | **8–20 hours** |
| **12. Protect flow-policy configuration** | Restrict project mappings, export permissions, destination allow-lists, masking rules, report recipients and service scopes to approved roles and change processes. | Use the existing **CM-06 configuration record**, **role matrix**, **deployment design**, **change records** and **SSP**. | **6–16 hours** |
| **13. Log and monitor material information flows** | Generate events for exports, cross-boundary movement, policy denial, lower-environment transfer, supplier disclosure, masking failure and rule changes. | Define events in the **SSP AU-02/SI-04/AC-04 sections** and existing **event specification**. Verify through the **SIEM onboarding** and **security test report**. | **6–16 hours** |
| **14. Test positive, negative and indirect flow paths** | Test permitted and prohibited transfers across screens, search, reports, exports, APIs, messages, files, support and lower environments. | Add cases to the normal **security test plan**, **integration test plan**, **operational acceptance test** or **penetration test**, retaining results in established reports. | **20–48 hours per major test cycle** |
| **15. Review and remove obsolete flows** | Reassess flows following material change and remove retired reports, integrations, recipients, identities, message consumers and transfer jobs. | Record decisions in the **change-impact assessment**, **post-implementation review**, **interface register**, **service review** and **decommissioning records**. | **4–12 hours per review or retired flow** |
| **16. Document and manage information-flow limitations** | Record coarse product controls, broad exports, marking loss, supplier restrictions or unsupported segregation with compensating controls and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP AC-04 statement**. | **4–10 hours per exception** |

### Indicative total

For a typical internal application with several projects, reports and integrations, initial application effort is commonly around **150–360 hours**.

A small application with a single information community and no exports or integrations may require less. A complex engineering, records, analytics or collaboration platform with many projects, granular handling rules, thick clients, broad reporting and supplier interfaces may require substantially more.

The estimates should not be added mechanically where activities overlap. AC-04 work commonly shares requirements, implementation and evidence with AC-03, AC-05, AC-06, AC-20, SC-07, SC-08, SC-28, SI-10, AU-02 and SI-04.

---

## Suggested document placement

To avoid creating disconnected evidence, information-flow evidence should normally be distributed across established application and SDLC artefacts:

- **SSP:** AC-04 implementation approach, information communities, key permitted and prohibited flows, inherited enterprise controls, monitoring and exceptions.
- **ConOps or SyOps:** operational information movement, report distribution, support disclosures, environment refresh, supplier interaction and exception handling.
- **Information register or data catalogue:** information types, owners, sensitivity, handling and approved recipients.
- **Security or solution architecture:** enforcement points, trust boundaries, flows, transformations and inherited services.
- **System context and data-flow diagrams:** source, destination, direction, information and trust transitions.
- **Data model:** project, ownership, classification, provenance and handling attributes.
- **Business and security requirements:** permitted flows, prohibited flows, purpose, recipients, transformations and limits.
- **Role/access matrix:** who may view, export, transfer, distribute, report, administer and approve.
- **Interface control documents:** permitted fields, records, destinations, scopes, schemas, onward transfer and retention.
- **API and message specifications:** caller, consumer, data minimisation, partition context, rate and replay controls.
- **Report and export specifications:** field sets, filters, recipients, markings, file formats and volume restrictions.
- **Notification design:** recipient rules, content minimisation and protected links.
- **Test-data and environment strategy:** production-data restrictions, masking, approval, retention and deletion.
- **CM-06 configuration records:** destination allow-lists, report recipients, export settings, masking rules and feature flags.
- **AU-02 and SI-04 evidence:** information-flow events, policy denials, alerts and monitoring health.
- **SDLC backlog and technical design:** server-side flow-enforcement requirements and acceptance criteria.
- **Test plans and reports:** positive, negative, indirect and failure-path testing.
- **Release and operational acceptance records:** confirmation that released flows match the approved design.
- **Service reviews and access reviews:** continuing validity of recipients, integrations, projects and exceptions.
- **Risk register or application addendum:** coarse controls, broad exports, inability to preserve markings, supplier limitations and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate network segmentation and firewall infrastructure;
- enterprise email and web gateways;
- enterprise data-loss prevention platforms;
- corporate managed file-transfer services;
- enterprise proxy and Internet-egress controls;
- corporate identity, MFA and directory services;
- VPN and remote-access controls;
- Microsoft Windows EUC controls;
- central classification and data-handling policy;
- enterprise encryption and PKI standards;
- central SIEM and SOC operations;
- corporate collaboration and messaging controls;
- enterprise backup infrastructure;
- organisation-wide privacy, legal and records-management policy;
- infrastructure-level cross-domain or one-way mechanisms;
- enterprise supplier-governance processes; and
- corporate exception and risk governance.

The application team must still:

- identify the application’s information types and flow paths;
- define application-specific permitted and prohibited flows;
- enforce project, record, report, export and integration boundaries;
- preserve and validate attributes;
- minimise and transform information where required;
- control production-to-non-production movement;
- prevent application-layer bypass;
- provide logging and monitoring;
- test end-to-end flow behaviour; and
- remove or formally manage obsolete and unsupported flows.

> **Key dividing line:** the enterprise provides shared channels and organisation-wide data-handling controls; the application decides and enforces which information may move through those channels, between which application contexts, for which purpose and in what form.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, AC-04 Information Flow Enforcement.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, AC-04 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-162, Guide to Attribute Based Access Control Definition and Considerations**.
4. National Institute of Standards and Technology, **NIST SP 800-205, Attribute Considerations for Access Control Systems**.
5. National Institute of Standards and Technology, **NIST SP 800-207, Zero Trust Architecture**.
6. National Institute of Standards and Technology, **NIST SP 800-207A, A Zero Trust Architecture Model for Access Control in Cloud-Native Applications in Multi-Location Environments**.
7. National Institute of Standards and Technology, **NIST SP 800-53 Release 5.2.0**, including the current control catalogue and assessment-procedure updates.
