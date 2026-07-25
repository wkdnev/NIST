# AC-20 Use of External Systems — Application Actions

## Purpose

For an internal corporate-network application, AC-20 means the application must ensure that **organisational information is not accessed, processed, stored, transmitted or administered through external systems unless that use is explicitly authorised and the required safeguards are in place**.

In this guide, an **external system** means a system that is not owned, operated or controlled to the required level by the organisation. Depending on corporate policy, this may include:

- personally owned computers, tablets or phones;
- supplier-owned laptops;
- partner systems;
- customer systems;
- unmanaged virtual desktops;
- public or consumer cloud services;
- personal email or file-sharing accounts;
- external collaboration platforms;
- unmanaged removable media;
- supplier support platforms;
- third-party remote-control tools;
- external code repositories;
- public AI or generative-AI services;
- public paste sites;
- external software build or scanning services; and
- any other system outside the organisation’s approved management, security and monitoring boundary.

The enterprise may provide:

- policy defining authorised and prohibited external systems;
- managed Microsoft Windows corporate EUC;
- VPN and remote-access controls;
- corporate identity and MFA;
- device-compliance enforcement;
- network egress controls;
- web and email gateways;
- data loss prevention;
- approved collaboration, file-transfer and supplier-access services;
- removable-media controls;
- procurement and supplier governance;
- central SIEM and SOC monitoring; and
- enterprise exception and risk-acceptance processes.

Those capabilities are inherited.

The application remains responsible for ensuring that its own design, interfaces and business functions do not permit users, administrators, suppliers or integrations to move application information to, or operate the application through, unapproved external systems.

NIST AC-20 requires organisations to define terms and conditions for use of external systems, prohibit use unless the external system meets defined security requirements or an approved connection or processing agreement is in place, and restrict the use of organisation-controlled portable storage devices on external systems. Its enhancements cover limits on organisationally controlled portable storage, restricted use of non-organisationally owned systems, prohibited use of portable storage and restrictions on network-accessible storage devices.

> **Core principle:** the enterprise decides which external systems and services are approved; the application must ensure that application information and functions can reach only those approved systems, through approved interfaces, for approved purposes.

---

## 1. Define what counts as an external system for the application

The application should adopt the enterprise definition and identify the external-system categories that are relevant to its functions.

Examples include:

- personal devices;
- unmanaged endpoints;
- supplier devices;
- partner workstations;
- external virtual desktop services;
- public cloud storage;
- consumer file-sharing;
- personal email;
- external collaboration platforms;
- public issue trackers;
- public source-code repositories;
- public package repositories not approved by the organisation;
- public AI services;
- external translation or document-conversion services;
- public malware-analysis or file-scanning sites;
- supplier ticketing portals;
- supplier diagnostic upload portals;
- external remote-control services;
- external printing or fulfilment services;
- network-attached storage outside the corporate boundary;
- removable media used on non-corporate systems; and
- systems accessed through unapproved remote routes.

The application’s SSP should reference the enterprise definition and list the external-system classes that its users, administrators or integrations could realistically encounter.

## 2. Define the approved application-use model

For the stated architecture, the normal approved use model should be:

- users access the application only from hardened, centrally managed corporate Windows EUC;
- remote use occurs only through the approved corporate VPN;
- corporate identity, MFA and device compliance are required;
- split tunnelling is prohibited;
- application endpoints remain internal;
- application information is stored in approved corporate repositories;
- supplier access uses approved enterprise supplier-access mechanisms;
- application exports use approved organisational destinations; and
- no public, personal, consumer or unmanaged system is required for normal operation.

The application should explicitly state that external-system use is prohibited unless separately authorised through the enterprise process.

## 3. Identify all ways application information could reach an external system

The application should map potential external-system paths, including:

- browser download;
- thick-client download;
- export;
- print;
- clipboard;
- copy and paste;
- screen capture;
- email;
- notifications;
- report distribution;
- API output;
- file transfer;
- integration;
- webhook or callback;
- URL or endpoint configuration;
- cloud or network storage;
- removable media;
- support bundle;
- crash dump;
- diagnostic logs;
- supplier upload;
- backup export;
- database extract;
- source-code repository;
- package repository;
- build pipeline;
- vulnerability-scanning service;
- document conversion;
- malware submission;
- public AI service;
- remote desktop;
- remote-control tool;
- shared link;
- user-configured destination; and
- mobile or offline synchronisation.

This flow inventory should align with AC-04 and SC-07.

## 4. Identify all ways external systems could access the application

The application should identify possible access from:

- personal endpoints;
- supplier laptops;
- external VDI;
- unmanaged browsers;
- mobile devices;
- partner networks;
- direct Internet routes;
- external VPNs;
- supplier remote-control tools;
- direct database clients;
- public APIs;
- cloud-hosted scripts;
- external automation platforms;
- browser extensions;
- unmanaged thick clients; and
- externally hosted service identities.

The application should design and test controls so these routes do not work unless explicitly authorised.

## 5. Prohibit direct Internet exposure

For an internal-only application, the application should:

- have no public application endpoint;
- have no public administrative endpoint;
- have no public API endpoint;
- have no public database listener;
- have no public thick-client service endpoint;
- have no supplier backdoor;
- have no unapproved cloud relay;
- have no public callback path;
- have no direct public software-update dependency at runtime; and
- have no public file-upload or download portal.

The enterprise implements network controls. The application defines its authorised endpoints and verifies that no external route is needed or exposed.

## 6. Require corporate-managed endpoints

The application should be designed for use from approved corporate-managed Windows EUC.

The application should:

- avoid supporting personal devices;
- avoid browser or client features that assume unmanaged storage;
- avoid local administrator requirements where possible;
- use enterprise authentication;
- use approved internal endpoints;
- avoid accepting untrusted client assertions;
- enforce security controls server-side;
- protect local cache;
- support corporate software distribution;
- prevent obsolete or unofficial thick clients where feasible; and
- document any unavoidable endpoint dependency.

The enterprise owns device hardening and compliance. The application owns the data and functionality it makes available to the endpoint.

## 7. Do not rely solely on device or network ownership

A corporate IP address, VPN address or managed-device signal is useful context, but does not replace application controls.

The application should still enforce:

- authentication;
- account status;
- role;
- project or tenant scope;
- least privilege;
- information-flow restrictions;
- input validation;
- transaction controls;
- export restrictions;
- session security; and
- audit logging.

Conversely, where enterprise policy requires managed-device or VPN context, the application should not silently ignore missing or invalid authoritative context.

## 8. Restrict browser access from external systems

Where technically supported, the application should use enterprise controls or application-integrated policy to prevent access from unmanaged browsers or devices.

The application may:

- require the approved identity provider;
- require an approved authentication context;
- consume authoritative device-compliance claims;
- deny missing or stale device context where required;
- restrict download or export for lower-assurance sessions;
- prohibit access from external identity tenants;
- prohibit unapproved browser origins;
- reject public redirect URIs;
- use internal DNS and routing only; and
- log device- or access-context denials.

The application should not create its own unmanaged-device detection system where the enterprise provides an authoritative service.

## 9. Restrict thick-client use on external systems

A thick client should:

- be distributed only through approved corporate software management;
- be signed;
- have a controlled package identity;
- use approved internal endpoints;
- validate server identity;
- use enterprise authentication;
- avoid embedded credentials;
- protect tokens and local cache;
- prevent configuration redirection;
- avoid direct database access;
- enforce server-side authorisation;
- support minimum client versions;
- prevent unofficial portable copies where feasible; and
- be removed through corporate endpoint management.

The application should not publish installers to public websites or supplier portals unless formally authorised.

## 10. Restrict use of non-organisationally owned systems

Where the enterprise prohibits non-organisationally owned systems, the application should not support or enable them.

Where an exception is permitted, the application should require evidence that the external system or connection meets enterprise-defined conditions, such as:

- approved ownership or sponsorship;
- security requirements;
- managed configuration;
- supported operating system;
- endpoint protection;
- encryption;
- identity and MFA;
- logging;
- data-storage restrictions;
- incident reporting;
- inspection or assessment rights;
- approved connection path;
- approved agreement;
- defined retention and deletion;
- no onward sharing; and
- expiry of authorisation.

The application team should not approve personal or supplier devices independently of enterprise policy.

## 11. Control supplier-owned systems

Where supplier personnel need access, the application should ensure that access occurs only through the approved supplier-access model.

Controls should include:

- named supplier users;
- enterprise-approved access route;
- MFA;
- internal sponsor;
- contract or engagement reference;
- approved device conditions;
- minimum application role;
- limited project and data scope;
- defined start and expiry;
- support case or change reference;
- no direct Internet-facing maintenance interface;
- no unapproved remote-control tool;
- controlled file transfer;
- monitoring;
- prompt removal; and
- post-use review.

If supplier-owned devices are not permitted, the supplier should use an approved corporate-managed device or enterprise-provided controlled workspace.

## 12. Control external partner and customer systems

If the application exchanges information with partners or customers, it should define:

- whether the external organisation is an approved recipient;
- authorised business purpose;
- information types;
- direction of flow;
- interface;
- identity;
- authentication;
- encryption;
- data scope;
- format;
- validation;
- logging;
- retention;
- onward-use restrictions;
- agreement reference;
- incident contacts;
- review date; and
- termination process.

For the current internal-only application scope, partner or customer access should normally be treated as out of scope and prohibited unless the architecture and authorisation are formally changed.

## 13. Restrict exports to approved organisational destinations

The application should prevent users from choosing arbitrary external destinations.

Exports should normally be limited to:

- approved internal repositories;
- approved corporate file shares;
- approved records systems;
- approved enterprise collaboration services;
- approved managed file transfer;
- approved internal email recipients;
- approved downstream applications; and
- approved corporate EUC local storage where policy permits.

Controls may include:

- destination allow-lists;
- recipient validation;
- internal-domain restrictions;
- project or information-owner approval;
- export role restrictions;
- quantity limits;
- expiry;
- watermarking or markings;
- logging;
- protected packaging; and
- post-export review for high-risk data.

## 14. Restrict email and notification destinations

The application should:

- use approved enterprise email services;
- restrict recipient domains where required;
- prevent arbitrary SMTP configuration;
- prevent users from changing mail relays;
- prevent sensitive information in subject lines;
- minimise sensitive content in notifications;
- require authentication for linked content;
- avoid full-record attachments where unnecessary;
- validate distribution lists;
- prevent auto-forwarding to external domains where within application control;
- log report and notification distribution; and
- fail safely when recipient validation fails.

Enterprise email gateway controls remain inherited.

## 15. Restrict report distribution

Reports should not be distributable to personal or unapproved external systems.

The application should control:

- who may generate reports;
- which information may be included;
- project and record scope;
- output format;
- recipient;
- storage location;
- scheduling;
- expiry;
- attachment handling;
- bulk volume;
- marking;
- download;
- printing;
- audit logging; and
- revocation where supported.

Scheduled reports should be reviewed when recipients, roles or supplier engagements change.

## 16. Restrict clipboard, print and screen-capture-related exposure where required

The application should determine whether information sensitivity requires restrictions on:

- clipboard copy;
- copy and paste;
- print;
- export to office formats;
- drag and drop;
- screen capture;
- local browser cache;
- preview;
- offline reading; and
- report generation.

Technical enforcement may rely partly on enterprise EUC, VDI, DLP or information-protection controls.

Where the application cannot technically prevent a prohibited action, it should:

- minimise exposed information;
- apply role and scope controls;
- display handling markings;
- log high-risk exports;
- document inherited controls;
- train users through enterprise processes;
- record the limitation; and
- obtain information-owner risk acceptance where required.

## 17. Control local storage on corporate EUC

Corporate ownership does not mean all local storage is automatically appropriate.

The application should define:

- whether local download is allowed;
- which data types may be stored locally;
- approved locations;
- encryption reliance;
- cache duration;
- temporary-file handling;
- automatic deletion;
- offline availability;
- file naming and markings;
- behaviour after account disablement;
- behaviour after device loss;
- synchronisation;
- backup implications; and
- user responsibilities.

The enterprise owns endpoint encryption and management. The application owns what it writes locally and whether that is necessary.

## 18. Prohibit storage on personal or consumer services

The application should not provide direct integration with:

- personal cloud drives;
- consumer file-sharing services;
- personal email;
- public note-taking services;
- public paste sites;
- personal source repositories;
- consumer messaging platforms;
- personal backup services; or
- public document-sharing links.

Where a product includes built-in connectors to such services, the application should disable or remove them under CM-07 and CM-06.

## 19. Control removable media use

The enterprise normally controls removable media and portable storage.

The application should still:

- avoid requiring removable media;
- avoid export workflows designed around USB devices;
- restrict or disable removable-media destinations where the application can;
- not provide portable standalone copies of the application or database;
- not store secrets on removable media;
- define approved recovery-media handling;
- ensure exports retain markings;
- log high-risk export activity;
- use approved managed transfer services instead; and
- document any operational dependency on removable media.

AC-20 enhancements specifically address restrictions and prohibitions on portable storage used with external systems.

## 20. Control network-accessible storage devices

The application should prevent or restrict storage to:

- personal network-attached storage;
- home file servers;
- unapproved shared drives;
- supplier file shares;
- public object storage;
- unmanaged network shares; and
- user-defined UNC paths.

Where the application accepts a storage destination, it should use:

- fixed approved locations;
- allow-listed hosts;
- approved protocols;
- service identities;
- server-side storage;
- access checks;
- path validation;
- logging; and
- configuration controlled under CM-05 and CM-06.

## 21. Control public cloud and SaaS integrations

For an internal-only application, public cloud or SaaS integrations should normally be absent.

The application should:

- disable built-in cloud connectors;
- remove public telemetry where not approved;
- disable public update checks at runtime;
- disable public sharing;
- block public callback destinations;
- avoid cloud-hosted analytics;
- avoid external crash-reporting services;
- avoid external content-delivery dependencies;
- avoid public authentication tenants;
- avoid external storage;
- use approved internal repositories and services; and
- formally assess any proposed exception.

A corporate subscription does not automatically make a service approved for every information type or application.

## 22. Control use of public AI and generative-AI systems

Where the application handles sensitive organisational information, it should not enable users or administrators to submit that information to unapproved public AI services.

The application should consider:

- disabling AI connectors;
- preventing configurable public AI endpoints;
- prohibiting automatic prompt submission;
- preventing source code, logs or records being sent externally;
- restricting support staff from using public AI for diagnostics;
- using approved internal AI services only where authorised;
- minimising data;
- validating outputs;
- logging approved integrations;
- defining retention and model-training restrictions;
- ensuring contractual controls; and
- documenting any approved use case.

Enterprise policy determines approved AI services. The application controls whether its own information and functions connect to them.

## 23. Control public code and issue-tracking services

Application source code, configuration and security findings should not be placed in unapproved external systems.

The application should use approved enterprise:

- source repositories;
- issue trackers;
- build systems;
- artefact repositories;
- package repositories;
- vulnerability trackers;
- documentation platforms; and
- collaboration tools.

The application should prevent or formally prohibit:

- public repositories;
- personal developer accounts;
- public snippets;
- external paste sites;
- unapproved supplier repositories;
- public CI/CD;
- external issue trackers containing restricted details; and
- public sharing of logs, configurations or exploit evidence.

## 24. Control external package and update sources

The application should not retrieve production software directly from arbitrary external sources.

It should:

- use approved enterprise or supplier repositories;
- verify publisher, signature and integrity;
- pin or control versions;
- prevent direct runtime downloads where possible;
- use internal package mirrors where provided;
- control public repository access through the build process;
- record provenance;
- scan dependencies;
- prevent dependency confusion;
- retain release artefacts internally; and
- ensure recovery does not depend on an unavailable public site.

The enterprise may control egress and repository services. The application defines its approved dependencies and build inputs.

## 25. Control external scanning and analysis services

Application information should not be uploaded to unapproved:

- public malware-analysis sites;
- public source-code scanners;
- public document converters;
- public vulnerability scanners;
- public debugging services;
- public crash-analysis services;
- public translation tools; or
- public AI assistants.

This includes:

- production files;
- source code;
- executables;
- configuration;
- support bundles;
- logs;
- packet captures;
- tokens;
- certificates;
- vulnerability evidence; and
- screenshots.

Approved enterprise or contracted analysis services should be used instead.

## 26. Control supplier diagnostic uploads

Where a supplier requires logs, support bundles, database extracts or files, the application should require:

- approved support case;
- approved transfer service;
- minimum necessary data;
- redaction;
- information-owner or support-owner approval where required;
- supplier identity validation;
- encryption;
- retention and deletion commitment;
- contract or confidentiality coverage;
- named recipient;
- logging;
- evidence of transfer;
- no personal email or public portal unless approved;
- no embedded credentials; and
- confirmation of disposal where required.

The application should prefer reproduction with synthetic data over sending production information.

## 27. Control external remote-control and screen-sharing tools

The application should not require or enable unapproved remote-control tools.

Supplier or support access should use:

- approved enterprise remote-support tooling;
- named identities;
- monitored sessions;
- approved devices;
- restricted functions;
- controlled file transfer;
- time limitation;
- case reference;
- session termination; and
- post-use review.

Built-in vendor “phone home” or remote-support features should be disabled unless explicitly authorised.

## 28. Control externally hosted service identities

The application should not trust an external automation or service merely because it possesses a token.

Where an approved external system calls the application, define:

- approved external organisation or service;
- agreement;
- client identity;
- authentication method;
- certificate or key ownership;
- scopes;
- endpoints;
- information permitted;
- rate limits;
- source restrictions;
- expiry;
- monitoring;
- incident contacts;
- credential revocation;
- data retention; and
- termination.

For the current internal-only architecture, externally hosted callers should normally be prohibited.

## 29. Control callbacks, webhooks and user-supplied URLs

The application should not permit data or events to be sent to arbitrary Internet or external destinations.

It should:

- disable callbacks where not required;
- use approved destination allow-lists;
- validate scheme, host, port and path;
- prohibit user-supplied arbitrary destinations;
- block public, loopback and link-local destinations as appropriate;
- prevent redirection;
- authenticate recipients;
- minimise data;
- sign messages where required;
- log delivery;
- use approved internal brokers; and
- manage exceptions through formal design and risk approval.

## 30. Control data import from external systems

Information received from approved external systems should be:

- sourced through an approved connection or transfer method;
- linked to an authorised agreement;
- attributable to the source;
- authenticated;
- integrity-protected;
- malware-scanned where relevant;
- schema-validated;
- input-validated;
- reconciled;
- quarantined on failure;
- logged;
- subject to information-handling rules;
- checked for malicious active content; and
- limited to the approved business purpose.

Approval of the external system does not make every input trustworthy.

## 31. Control data export to external systems

Where an external transfer is formally authorised, the application should enforce:

- approved recipient;
- approved purpose;
- information-owner approval;
- minimum necessary data;
- correct project and record scope;
- destination allow-list;
- secure transfer;
- authentication;
- encryption;
- integrity;
- file and format controls;
- markings;
- retention and deletion conditions;
- logging;
- expiry;
- reconciliation;
- incident contacts; and
- agreement reference.

The application should prevent users from changing the destination or data scope outside the approved transfer definition.

## 32. Require agreements or defined security requirements

Where external-system use is allowed, the application should reference the relevant:

- interconnection agreement;
- data-sharing agreement;
- supplier contract;
- security schedule;
- support agreement;
- processing agreement;
- information-handling agreement;
- acceptable-use approval;
- risk acceptance; or
- equivalent enterprise authorisation.

The application should record:

- external system;
- owner;
- purpose;
- information;
- access method;
- security requirements;
- restrictions;
- review date;
- expiry;
- incident obligations; and
- termination process.

The application team should not draft a separate agreement where the enterprise already maintains the authoritative contract or connection record.

## 33. Apply data minimisation

Where approved external-system use is necessary, the application should minimise:

- records;
- fields;
- attachments;
- time period;
- user population;
- recipient population;
- frequency;
- export volume;
- diagnostic detail;
- identifiers;
- personal data;
- source code;
- security configuration; and
- retention.

The smallest necessary transfer is easier to protect, monitor and terminate.

## 34. Apply markings and handling metadata

Where organisational information is exported to an approved external system, the application should preserve or apply:

- classification;
- sensitivity;
- project;
- caveat;
- handling instruction;
- owner;
- origin;
- retention;
- recipient restriction;
- export date;
- record identifier; and
- version.

Markings do not replace access control, but they reduce the risk of accidental misuse after transfer.

## 35. Prevent external-system use through error and diagnostic functions

The application should prevent:

- automatic public crash reporting;
- external telemetry;
- public diagnostics;
- copying full stack traces into external tickets;
- uploading memory dumps without review;
- exposing database content through support bundles;
- including secrets in logs;
- sending screenshots to personal email;
- automatic external performance monitoring;
- and unapproved supplier analytics.

Diagnostic outputs should be minimised and routed through approved enterprise systems.

## 36. Prevent use of external systems through configuration

Security-relevant configuration should prevent users or administrators from enabling:

- public storage connectors;
- external mail relays;
- arbitrary webhooks;
- external AI endpoints;
- public telemetry;
- public update services;
- external repository paths;
- supplier remote-control;
- arbitrary file shares;
- public authentication providers;
- external logging destinations; and
- public analytics.

Changes should be restricted, approved, tested, logged and included in CM-05 and CM-06.

## 37. Fail safely when an external destination is not approved

The application should deny or hold an action when:

- destination validation fails;
- the recipient is unapproved;
- the agreement is expired;
- the external system is not on the approved list;
- device or access conditions are missing;
- required encryption is unavailable;
- recipient authentication fails;
- transfer integrity fails;
- the supplier account is expired;
- the external service is unavailable;
- a callback redirects;
- policy evaluation fails; or
- the data scope exceeds approval.

The application should not fall back to personal email, public file sharing or a generic external route.

## 38. Protect credentials used with approved external systems

Where an approved external interface exists, the application should:

- use application-specific credentials;
- avoid personal user credentials;
- use named service ownership;
- store secrets in approved enterprise services;
- restrict access;
- use minimum scopes;
- separate environments;
- rotate or renew;
- monitor expiry;
- revoke promptly;
- prevent disclosure in logs;
- document dependencies; and
- remove credentials when the agreement ends.

## 39. Log external-system-related activity

The application should generate or retain useful events for:

- export to an approved external system;
- denied external destination;
- supplier access;
- supplier file transfer;
- external API call;
- callback or webhook delivery;
- change to destination allow-list;
- enablement of an external connector;
- use of local download;
- bulk report distribution;
- public or personal destination attempt;
- external identity denial;
- unmanaged-device denial where authoritative context is used;
- external diagnostic upload;
- emergency exception;
- external credential change; and
- agreement expiry or disabled connection.

Events should include:

- acting identity or service;
- application and environment;
- destination;
- information type or scope;
- time;
- outcome;
- quantity where appropriate;
- approval or agreement reference;
- supplier status;
- correlation identifier; and
- component.

Sensitive data, passwords and full tokens should not be logged.

## 40. Monitor for external-system misuse

The application should support detection of:

- repeated attempts to send data to unapproved domains;
- use of personal email addresses;
- arbitrary callback configuration;
- unexpected external DNS destinations;
- large remote downloads;
- supplier access outside approved windows;
- external connector enablement;
- external logging destinations;
- public repository references;
- obsolete supplier credentials;
- attempts from unmanaged identities or clients;
- repeated denied exports;
- diagnostic uploads with excessive data;
- unusual local storage activity where visible;
- changes to cloud or telemetry settings; and
- external transfer after agreement expiry.

The enterprise SOC may operate the monitoring service. The application must generate meaningful events and destination context.

## 41. Review approved external-system use periodically

The application should review:

- each approved external system;
- business purpose;
- owner;
- information transferred;
- user population;
- supplier access;
- credentials;
- connection path;
- destination allow-list;
- security requirements;
- agreement status;
- retention;
- incident history;
- exceptions;
- monitoring;
- continuing need; and
- termination date.

Approval should not continue automatically after the business relationship or technical need ends.

## 42. Review product features that enable external use

After product upgrades or configuration changes, the application should check for newly introduced:

- cloud connectors;
- telemetry;
- AI features;
- public sharing;
- external update services;
- supplier support tunnels;
- analytics;
- external storage;
- social or messaging integration;
- public authentication providers;
- external crash reporting;
- webhooks;
- marketplace plugins; and
- mobile synchronisation.

Unneeded features should be disabled under CM-07.

## 43. Test external-system restrictions

Testing should include, where relevant:

- access from approved corporate EUC;
- access from an unmanaged or unapproved system through an authorised test method;
- direct Internet route;
- personal email destination;
- external domain recipient;
- arbitrary webhook;
- public storage connector;
- public AI endpoint;
- public file-sharing link;
- supplier access outside the approved window;
- expired external credential;
- unapproved thick client;
- direct database access;
- upload to an unapproved diagnostic destination;
- export beyond approved data scope;
- callback redirection;
- missing agreement or approval;
- failure of recipient authentication;
- safe failure;
- logging and alerting; and
- removal of an obsolete external connection.

Testing should validate the application-layer control, not only enterprise egress filtering.

## 44. Exercise an external-system incident scenario

The application should consider scenarios such as:

- a user uploads a restricted file to a personal service;
- a supplier copies support data to an unapproved portal;
- an external service credential is compromised;
- an approved external system is breached;
- a public connector is enabled after an upgrade;
- a report is emailed to an external address;
- application data is submitted to a public AI service;
- a user accesses from an unmanaged device;
- a callback is redirected to an attacker-controlled destination; or
- an agreement expires while integration continues.

The exercise should confirm:

- logs identify the user, data and destination;
- the connection or credential can be disabled;
- affected records can be scoped;
- information owners can be notified;
- enterprise incident response receives useful evidence;
- supplier and legal contacts are known; and
- residual copies and retention obligations can be addressed.

## 45. Terminate external-system connections completely

When an approved external-system use ends, the application should:

- disable the connector;
- revoke credentials;
- remove certificates;
- remove allow-list entries;
- remove user and supplier roles;
- stop scheduled transfers;
- remove callbacks;
- remove report distribution;
- archive required evidence;
- confirm data return or deletion where required;
- update architecture;
- update CM-02 and CM-08;
- update monitoring;
- close agreements;
- remove support access; and
- test that the connection no longer works.

## 46. Manage exceptions

Where external-system use cannot meet the expected model, record:

- external system;
- owner;
- purpose;
- affected users;
- information involved;
- access or transfer method;
- expected control;
- actual capability;
- risk;
- compensating controls;
- monitoring;
- agreement or contract status;
- approving authority;
- remediation or replacement plan;
- review date; and
- expiry date.

Examples include:

- supplier portal that cannot use enterprise identity;
- supplier-owned device;
- external file transfer with limited audit detail;
- product requiring public licence activation;
- public package source;
- unapproved telemetry that cannot be fully disabled;
- inability to block local download;
- external document converter;
- shared supplier account;
- external support platform;
- or legacy integration with weak encryption.

The exception should be visible in the application addendum or risk process, not buried in a supplier email or configuration note.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses managed corporate EUC, VPN, enterprise identity, egress controls, approved collaboration services, DLP, supplier governance and central monitoring. They exclude enterprise endpoint, gateway, DLP and network engineering.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the approved-use model and prohibited external systems** | State that the application is accessed only through managed corporate EUC and approved VPN and that personal devices, public services and unmanaged supplier routes are prohibited unless formally authorised. | Summarise in the **SSP AC-20 statement** and maintain detail in the existing **ConOps**, **SyOps**, **security architecture** or **acceptable-use section of the support model**. | **4–8 hours** |
| **2. Map external access and information-transfer paths** | Identify browser, thick-client, API, export, email, file, supplier, diagnostic, repository, cloud, AI and callback paths that could reach external systems. | Record the map in the existing **AC-04 flow inventory**, **SC-07 communication-flow diagram**, **data-flow diagrams**, **interface register** and **SSP**. | **8–20 hours** |
| **3. Remove or disable public and consumer-service connectors** | Disable public storage, personal email, external AI, telemetry, public sharing, arbitrary webhooks, supplier tunnels and other unapproved external features. | Record settings in the **CM-06 configuration specification**, **CM-07 functionality review**, **security design**, **release evidence** and **SSP**. | **8–24 hours** |
| **4. Restrict access to approved corporate endpoints and identity context** | Use internal endpoints, corporate identity and server-side authorisation and consume authoritative device or access context where required. | Capture controls in the **identity integration design**, **security architecture**, **SSP IA-02/AC-17/AC-20 sections** and **security test report**. | **8–24 hours** |
| **5. Restrict exports and report distribution to approved destinations** | Apply destination, recipient, role, project, information-scope and volume controls and prohibit arbitrary external addresses and shares. | Record in the **export/report specification**, **AC-04 design**, **role matrix**, **SyOps**, **CM-06 settings** and **test evidence**. | **12–32 hours** |
| **6. Control local storage, print, clipboard and offline use** | Define allowed local data and cache behaviour and rely on approved EUC/DLP controls for actions the application cannot directly prevent. | Record decisions in the **thick-client or browser design**, **data-handling specification**, **SyOps**, **SSP** and any **risk record**. | **8–20 hours** |
| **7. Control supplier access and diagnostic transfer** | Use named supplier identities, approved access paths, support cases, minimum data, approved transfer, redaction, expiry, monitoring and post-use review. | Use the existing **supplier record**, **support model**, **PAM record**, **support ticket**, **data-transfer approval**, **SyOps** and **SSP**. | **8–24 hours** |
| **8. Control approved external interfaces through agreements and allow-lists** | For any authorised external system, record purpose, information, identity, connection, security requirements, agreement, owner, expiry and termination. | Reference the established **interconnection agreement**, **supplier contract**, **data-sharing agreement**, **interface control document**, **risk record** and **SSP**. | **8–20 hours per approved external connection** |
| **9. Restrict external destinations in APIs, callbacks and configuration** | Use fixed or allow-listed destinations, validate URLs and recipients, prohibit arbitrary public endpoints and protect changes under CM-05. | Capture controls in the **API/interface specification**, **security design**, **CM-05 change model**, **CM-06 configuration** and **security test report**. | **12–28 hours** |
| **10. Protect credentials for approved external connections** | Use application-specific identities, approved secrets services, minimum scopes, rotation, monitoring and prompt revocation. | Evidence remains in the existing **service-account register**, **secrets/certificate platform**, **interface document**, **SyOps** and **access review**. | **6–16 hours** |
| **11. Log and monitor external-system-related activity** | Generate events for approved transfers, denied destinations, supplier access, external connector changes, public-service attempts and credential changes. | Define events in the **SSP AU-02/SI-04/AC-20 sections** and existing **event specification**. Verify through **SIEM onboarding** and the **security test report**. | **6–16 hours** |
| **12. Test prohibited and approved external-system scenarios** | Test unmanaged access, public destinations, personal email, arbitrary webhooks, supplier expiry, export scope, external credentials, safe failure and alerting. | Add cases to the normal **security test plan**, **integration test**, **operational acceptance test**, **penetration test** or **data-loss exercise**. | **16–40 hours per major test cycle** |
| **13. Review external connections, features and exceptions periodically** | Review continuing need, agreement, owner, information, recipients, credentials, supplier access, newly introduced product features and expiry. | Retain outcomes in established **service reviews**, **supplier reviews**, **access reviews**, **CA-07 posture reports** or **application governance minutes**. | **6–16 hours per review** |
| **14. Exercise an external-data-loss scenario** | Test evidence, credential revocation, connection disablement, record scoping, supplier/legal contact and incident coordination. | Use the normal **incident exercise**, **tabletop report**, **IR lessons record** or **resilience exercise**, referenced from the SSP. | **8–16 hours per exercise** |
| **15. Terminate obsolete external connections completely** | Revoke identities and credentials, remove destinations, stop transfers, remove supplier roles, update architecture and confirm the connection no longer works. | Record completion in the **decommissioning record**, **change ticket**, **CM-02 baseline**, **CM-08 inventory**, **supplier record** and **test evidence**. | **6–20 hours per connection** |
| **16. Document and manage external-system limitations** | Record unavoidable public activation, weak supplier portals, unmanaged endpoints, external telemetry or inability to restrict local handling with compensating controls and expiry. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP AC-20 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application with no authorised external integrations and mature enterprise endpoint and egress controls, initial application effort is commonly around **90–210 hours**.

An application with one or more approved supplier, partner or external processing connections may require an additional **40–120 hours per connection**, excluding enterprise network engineering, legal negotiation, supplier remediation and major application development.

Ongoing effort is commonly around **4–15 hours per month**, plus supplier reviews, access reviews, incident exercises, connection changes and exception management.

The estimates should not be added mechanically where work overlaps. AC-20 commonly shares implementation and evidence with:

- AC-04 information-flow enforcement;
- AC-17 remote access;
- AC-19 access control for mobile devices;
- MP controls for media protection;
- SC-07 boundary protection;
- SC-08 transmission confidentiality and integrity;
- CA-03 information exchange;
- SA-09 external system services;
- CM-06 configuration settings;
- CM-07 least functionality;
- AU-02 event logging;
- SI-04 system monitoring; and
- IR controls.

---

## Suggested document placement

To avoid creating disconnected evidence, external-system information should normally be distributed across established application and SDLC artefacts:

- **SSP:** AC-20 implementation approach, external-system definition, approved-use model, inherited controls, authorised connections, monitoring and exceptions.
- **ConOps or SyOps:** user restrictions, supplier support, diagnostic transfer, local storage, removable media, incident handling and termination procedures.
- **Security architecture:** internal-only endpoints, corporate EUC and VPN assumptions, external trust boundaries, supplier paths and prohibited routes.
- **AC-04 information-flow inventory:** approved and prohibited destinations, recipients, exports, integrations and transfers.
- **SC-07 communication-flow diagrams:** internal endpoints, external connection points, egress dependencies and network restrictions.
- **Interface control documents:** approved external systems, identities, data, protocols, validation, agreements and termination.
- **Role/access matrix:** users permitted to export, administer connections, support suppliers or approve external transfers.
- **CM-06 configuration specification:** connector settings, destination allow-lists, telemetry, callbacks, public features and local-storage controls.
- **CM-07 functionality review:** disabled cloud, sharing, telemetry, AI, marketplace, remote-support and external-storage features.
- **Thick-client packaging and design:** distribution, endpoint control, local cache, server addresses and prevention of unofficial use.
- **Supplier records and contracts:** device, access, transfer, confidentiality, retention, incident and deletion requirements.
- **Interconnection or data-sharing agreements:** approved purpose, information, security requirements, owners, expiry and termination.
- **Service-account and certificate records:** identities and trust used for approved external connections.
- **Export, reporting and notification specifications:** recipient and destination controls, data minimisation and markings.
- **AU-02 and SI-04 evidence:** external transfer, destination denial, supplier, connector and anomaly events.
- **Test plans and reports:** public destination, unmanaged access, supplier expiry, callback, export and safe-failure tests.
- **Incident and exercise records:** data loss, supplier breach, external credential compromise and public-service misuse.
- **Service, supplier and CA-07 reviews:** continued need, agreement status, credentials, features and exceptions.
- **Risk register or application addendum:** supplier portal limitations, public activation, external telemetry, unmanaged systems and compensating controls.
- **Decommissioning records:** credential revocation, connection removal, data disposition and closure verification.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide policy for external systems, BYOD and acceptable use;
- approval of personal, supplier and partner devices;
- managed corporate Windows EUC;
- VPN and remote-access infrastructure;
- corporate identity and MFA;
- device-compliance and endpoint-management controls;
- network egress filtering;
- web, email and DNS security gateways;
- enterprise DLP and information-protection platforms;
- removable-media policy and technical enforcement;
- approved collaboration and file-sharing services;
- approved managed file-transfer services;
- enterprise supplier-access platform;
- corporate procurement, contracting, privacy and legal review;
- enterprise cloud and SaaS approval;
- corporate AI-use policy and approved AI platforms;
- central SIEM and SOC operations;
- organisation-wide incident response;
- enterprise interconnection and data-sharing governance; and
- organisation-wide exception and risk acceptance.

The application team must still:

- identify every application path to or from an external system;
- keep the application internal-only unless formally changed;
- disable unapproved external connectors and features;
- restrict exports and destinations;
- control supplier access and diagnostic transfers;
- define approved interfaces and agreements;
- protect connection credentials;
- log and test external-system restrictions;
- terminate connections completely; and
- formally manage application-specific limitations.

> **Key dividing line:** the enterprise defines and operates the approved external-system ecosystem; the application ensures that its information, users, functions and interfaces cannot use anything outside that ecosystem without explicit authorisation and enforceable safeguards.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, AC-20 Use of External Systems.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, AC-20 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-46 Rev. 2, Guide to Enterprise Telework, Remote Access, and Bring Your Own Device (BYOD) Security**.
4. National Institute of Standards and Technology, **NIST SP 800-207, Zero Trust Architecture**.
5. National Institute of Standards and Technology, **NIST SP 800-207A, A Zero Trust Architecture Model for Access Control in Cloud-Native Applications in Multi-Location Environments**.
6. National Institute of Standards and Technology, **NIST SP 800-161 Rev. 1 Update 1, Cybersecurity Supply Chain Risk Management Practices for Systems and Organizations**.
7. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, current AC-20 control and assessment content.
