# SC-07 Boundary Protection — Application Actions

## Purpose

For an IT application, SC-07 means the application must ensure that communications crossing its **application trust boundaries** pass only through approved, controlled and monitored interfaces.

The enterprise may provide corporate network segmentation, firewalls, routing, VPN, proxy services, secure DNS, endpoint protection, managed load balancers, intrusion detection, remote-access controls and the hardened Microsoft Windows EUC environment. Those are inherited enterprise capabilities.

The application remains responsible for defining and enforcing the boundaries created by its own:

- presentation, service and data tiers;
- user, administrative and support interfaces;
- thick clients;
- APIs;
- service-to-service calls;
- integration services;
- message queues;
- file-transfer paths;
- database connections;
- privileged management paths;
- supplier connections;
- development, test and production separation;
- application-controlled allow-lists;
- outbound destinations;
- data import and export functions; and
- trust decisions made after network traffic reaches the application.

NIST SC-07 requires communications at external managed interfaces and key internal managed interfaces to be monitored and controlled. It also requires connections to external networks or systems to pass through managed interfaces arranged in accordance with the organisation’s security architecture. NIST guidance on firewalls supports explicit policy, controlled traffic flow and “deny by default”, while NIST zero-trust guidance reinforces that network location alone must not create implicit trust.

> **Core principle:** the enterprise protects the corporate network perimeter and shared network zones; the application protects every point where users, services, components or information cross into a different application trust context.

---

## 1. Define the application boundary

The application should define what is inside and outside the application’s security boundary.

The boundary should identify:

- application components;
- thick-client components;
- presentation tier;
- service or API tier;
- data tier;
- batch and scheduled-processing components;
- message brokers and queues;
- file stores;
- application-owned databases and schemas;
- reporting services;
- management interfaces;
- monitoring and logging interfaces;
- build and deployment interfaces;
- enterprise services relied upon;
- interconnected applications;
- supplier-managed components; and
- users and support teams that interact with the application.

The boundary should distinguish:

- **application-owned components**;
- **dedicated components operated for the application**;
- **shared enterprise services**;
- **interconnected internal systems**;
- **administrative and support systems**; and
- **systems outside the approved application scope**.

An application boundary is not necessarily the same as a network subnet. Several application trust boundaries may exist within one corporate network segment.

## 2. Identify trust boundaries and managed interfaces

The application should identify each point where trust, privilege, identity, data sensitivity or administrative authority changes.

Typical trust boundaries include:

- corporate EUC to application service;
- thick client to server;
- browser to web application;
- web tier to service tier;
- service tier to database;
- application to enterprise identity service;
- application to another internal application;
- user interface to privileged administration;
- production to non-production;
- application to supplier support;
- application to shared file storage;
- application to message broker;
- application to central logging;
- build pipeline to production deployment;
- application to backup or recovery service; and
- ordinary processing to a high-risk file-conversion or execution service.

Each boundary should have an identifiable managed interface or enforcement point.

## 3. Maintain an approved communication-flow inventory

The application should maintain an authoritative description of its permitted communications.

For each material flow, record:

- source component or identity;
- destination component or service;
- environment;
- protocol;
- port or service;
- direction;
- purpose;
- authentication method;
- authorisation or scope;
- encryption requirement;
- data or information type;
- expected volume or frequency;
- logging and monitoring;
- resilience behaviour;
- owner;
- approval; and
- expiry or review date where temporary.

The flow inventory may be maintained through:

- architecture diagrams;
- data-flow diagrams;
- interface control documents;
- service catalogues;
- firewall-request records;
- API specifications;
- deployment definitions;
- configuration-as-code; or
- controlled application connectivity registers.

The SSP should summarise the approach and reference the authoritative technical evidence rather than duplicate every rule.

## 4. Use deny-by-default communication policy

Application communications should be prohibited unless explicitly required and approved.

This means:

- only documented interfaces are enabled;
- only required methods and operations are accepted;
- unknown API clients are rejected;
- unapproved destinations are blocked;
- unused listeners are disabled;
- unnecessary bidirectional communication is avoided;
- temporary access expires;
- new components do not inherit broad connectivity automatically;
- missing or invalid identity information results in denial; and
- failure of an authorisation or policy lookup does not create unrestricted access.

A broad corporate network route does not authorise the application to accept every request available over that route.

## 5. Enforce controls at the application layer

Network firewalls alone are not sufficient for application boundary protection.

The application should enforce, as appropriate:

- authenticated sessions;
- service identity validation;
- API scopes;
- record and project authorisation;
- permitted request methods;
- schema validation;
- message validation;
- file-type and content restrictions;
- rate and size limits;
- workflow rules;
- replay protection;
- tenant or organisational boundaries;
- administrative-role checks; and
- restrictions on sensitive operations.

A request reaching the application from the corporate network should still be treated as untrusted until the application validates identity, authority, target, operation and content.

## 6. Separate presentation, service and data tiers

Where proportionate to the architecture, the application should separate tiers so that users and clients cannot directly access back-end resources.

The application should normally ensure that:

- users access the approved presentation or service interface;
- thick clients call approved application services rather than the database directly;
- presentation components access only required service endpoints;
- services access only required database objects;
- databases do not initiate unnecessary connections to user devices;
- administrative interfaces are separate from normal user interfaces;
- reporting services receive only required data access;
- batch jobs use dedicated identities and paths; and
- support tools do not bypass normal business controls.

For a small or monolithic application, logical controls may provide the separation where physical or network-tier separation is not proportionate.

## 7. Prevent direct database access from ordinary clients

Ordinary users and thick clients should not normally connect directly to the application database.

The preferred pattern is:

1. the user authenticates to the application;
2. the application service authorises the requested action;
3. the service accesses the database using an appropriately scoped identity; and
4. the result is filtered and returned through the trusted application interface.

Where direct database access is genuinely required, it should be:

- explicitly justified;
- limited to approved roles;
- read-only where possible;
- restricted to approved views or procedures;
- protected by strong identity;
- monitored;
- time-limited where appropriate; and
- documented as an application risk or exception.

## 8. Protect thick-client communications

A thick client installed on a corporate Windows EUC device should communicate only with approved internal application endpoints.

The application should:

- define approved server names and service endpoints;
- use authenticated and encrypted communication;
- validate server identity;
- avoid direct database connectivity where possible;
- reject unapproved redirection;
- avoid embedded privileged credentials;
- restrict local proxy or endpoint overrides;
- protect configuration that controls destinations;
- use server-side authorisation;
- handle unavailable services safely;
- log relevant connection failures; and
- maintain compatibility between approved client and server versions.

The enterprise owns the EUC baseline, VPN and network routing. The application owns the client’s approved communication behaviour.

## 9. Authenticate service-to-service communications

Internal service calls should not rely solely on source network location.

The application should use approved mechanisms to establish the identity and authority of:

- APIs;
- integration services;
- batch services;
- message producers and consumers;
- reporting services;
- schedulers;
- file-transfer services;
- deployment services; and
- administrative tools.

Controls may include:

- mutual TLS;
- service accounts;
- workload identities;
- signed tokens;
- scoped API credentials;
- certificate-based authentication;
- broker identities;
- restricted database roles; and
- enterprise-issued machine credentials.

The receiving component should validate issuer, audience, scope, expiry and intended operation where applicable.

## 10. Restrict APIs

The application should expose only approved APIs and operations.

It should:

- maintain an API inventory;
- disable obsolete versions;
- authenticate callers;
- authorise each operation;
- validate input;
- restrict methods;
- limit payload size;
- apply rate and concurrency limits;
- restrict bulk operations;
- prevent object-level access bypass;
- control cross-origin behaviour;
- validate callback and redirect destinations;
- protect API documentation and test consoles where necessary;
- avoid sensitive information in error messages;
- log relevant requests and denials; and
- retire unused keys, clients and routes.

An API being undocumented does not make it protected.

## 11. Protect message and event boundaries

Applications using queues, topics or event buses should control:

- who may publish;
- who may consume;
- permitted topics or queues;
- message schema;
- message size;
- message origin;
- replay;
- duplicate processing;
- dead-letter handling;
- message retention;
- sensitive content;
- administrative operations; and
- failure behaviour.

The application should not trust a message merely because it arrived through an enterprise broker.

Messages should be validated and authorised before they change application state.

## 12. Protect file-transfer boundaries

File exchanges should use approved, managed transfer paths.

The application should:

- identify approved sender and recipient identities;
- restrict source and destination locations;
- use protected transfer protocols;
- validate file type, structure and content;
- apply malicious-code scanning;
- restrict size and frequency;
- protect temporary staging;
- prevent direct execution;
- log receipt and transfer;
- prevent path traversal;
- reconcile expected and received files;
- handle duplicates and partial transfers safely; and
- prevent users from creating arbitrary transfer destinations.

Shared folders should not become an uncontrolled alternative to an approved application interface.

## 13. Separate production and non-production

The application should protect the production boundary from development, test, training and other lower environments.

This should include:

- separate identities and secrets;
- separate endpoints;
- no uncontrolled lower-environment access to production data;
- no test clients calling production unintentionally;
- controlled promotion into production;
- restricted production administration;
- no direct production-to-development data replication unless approved;
- controlled diagnostic access;
- separate logging and monitoring identifiers;
- prohibition of shared service accounts; and
- explicit, time-limited exceptions for support or migration.

The enterprise may provide network separation, but the application must configure and use it correctly.

## 14. Restrict administrative and management interfaces

Administrative interfaces should have stronger boundary controls than ordinary user interfaces.

The application should:

- separate administrative routes or endpoints;
- limit access to approved privileged identities;
- integrate with enterprise PAM where available;
- prohibit ordinary-user access;
- avoid exposing administration through a public or broadly reachable path;
- require reauthentication or stronger confirmation for high-impact actions where supported;
- restrict source management locations where proportionate;
- log all material administrative actions;
- disable unused supplier or maintenance interfaces;
- prevent silent impersonation; and
- close temporary support access promptly.

A hidden administrative URL is not a boundary-control mechanism.

## 15. Restrict outbound connections

An internal application should initiate only outbound communications required by its approved design.

The application should identify and control:

- destination;
- protocol;
- port;
- purpose;
- identity;
- information transferred;
- expected frequency;
- failure behaviour;
- logging;
- ownership; and
- approval.

The application should prohibit or tightly control:

- arbitrary user-supplied URLs;
- vendor telemetry;
- Internet update checks;
- cloud callbacks;
- consumer file-sharing services;
- unapproved webhooks;
- dynamic external redirects;
- unrestricted DNS resolution;
- direct supplier connections;
- unauthorised proxying; and
- generic network-scanning or tunnelling functionality.

Where no Internet or external access is approved, the application design and configuration should reflect that explicitly rather than merely depending on an assumed network block.

## 16. Prevent server-side request forgery and arbitrary destinations

Applications that retrieve URLs, call callbacks, import remote content or test connections should prevent users from turning the application into a network proxy.

Controls should include:

- destination allow-lists;
- approved schemes and ports;
- hostname validation;
- resolution and revalidation of destination addresses;
- rejection of loopback, link-local and unapproved internal addresses;
- redirect limits;
- prevention of credential forwarding;
- request timeouts;
- response-size limits;
- restricted service identity;
- network egress controls; and
- logging of destination and outcome.

User-supplied destination fields should not be passed directly to privileged server-side network functions.

## 17. Control redirects, callbacks and webhooks

Where redirects, callbacks or webhooks are required, the application should:

- pre-register destinations;
- approve destination ownership;
- restrict protocols;
- validate destination identity;
- sign or authenticate messages;
- prevent arbitrary destination changes;
- protect secrets;
- limit payload content;
- apply replay protection;
- monitor failures;
- expire unused registrations; and
- prevent lower environments from calling production destinations.

## 18. Validate communications crossing boundaries

The application should validate incoming and outgoing information for:

- expected schema;
- required fields;
- data type;
- length;
- range;
- encoding;
- file format;
- message sequence;
- record ownership;
- classification or handling marking;
- authorisation;
- integrity;
- freshness;
- duplicate or replay; and
- prohibited content.

Encryption protects data in transit but does not make the content trustworthy.

## 19. Protect confidentiality and integrity in transit

Application communications containing sensitive or security-relevant information should use approved cryptographic protection.

The application should:

- use approved protocol versions and cipher configurations;
- validate certificates and trust chains;
- verify hostname or service identity;
- avoid clear-text credentials;
- protect tokens and session identifiers;
- prevent downgrade;
- manage certificate rollover;
- reject expired or untrusted certificates;
- avoid sensitive data in URLs where inappropriate;
- use message-level integrity where transport protection does not provide sufficient end-to-end assurance; and
- document any trusted internal flow that cannot use the required protection.

Enterprise PKI and cryptographic standards are inherited, but the application must use them correctly.

## 20. Restrict information flow by sensitivity and business rule

Boundary protection also requires controlling what information may cross each interface.

The application should enforce:

- project or case boundaries;
- classification or handling restrictions;
- data-minimisation rules;
- approved field sets;
- export restrictions;
- masking or redaction;
- attachment restrictions;
- recipient restrictions;
- environment restrictions;
- purpose limitation;
- supplier-access limitations; and
- prohibition of production data in unauthorised lower environments.

A technically permitted connection should not imply that every application record may traverse it.

## 21. Protect shared and multi-tenant boundaries

Where the application separates projects, programmes, business units, customers or other information communities within one platform, it should treat those logical partitions as internal boundaries.

The application should:

- enforce project or tenant context;
- prevent identifier manipulation;
- filter search, reporting and export;
- isolate attachments and indexes;
- scope background jobs;
- scope caches;
- scope audit access;
- protect cross-project administration;
- test horizontal access;
- prevent data leakage through counts, metadata or autocomplete; and
- log attempted boundary violations.

Network segmentation does not enforce logical data segregation inside one application.

## 22. Limit and control proxy functionality

An application should not provide generic proxy, relay, port-forwarding or tunnelling capability unless it is an approved business function.

Where such functionality is necessary, it should be:

- limited to approved destinations and protocols;
- authenticated;
- authorised;
- logged;
- rate-limited;
- protected from arbitrary header or credential forwarding;
- isolated;
- reviewed;
- monitored for abuse; and
- disabled when no longer needed.

## 23. Protect supplier and maintenance access

Supplier access should use the approved enterprise remote-support or privileged-access path.

The application should:

- identify approved supplier identities;
- limit access to required components and functions;
- use named accounts;
- require approval;
- restrict time and duration;
- avoid direct Internet-facing maintenance interfaces;
- disable dormant access;
- prohibit unapproved remote-control tools;
- monitor and log activity;
- prevent unrestricted data export;
- require a support case or purpose;
- review transferred files;
- revoke credentials after use where appropriate; and
- verify changes through normal change control.

## 24. Protect recovery and failover boundaries

Recovery, backup and failover paths should not bypass normal boundary protections.

The application should ensure that:

- recovery environments use approved connectivity;
- restored systems do not expose default or obsolete interfaces;
- backup access is restricted;
- replication paths are authenticated and protected;
- failover endpoints are approved;
- lower environments are not used as an uncontrolled recovery route;
- recovered components are checked against the baseline;
- logging and monitoring resume;
- temporary recovery access is removed; and
- business and data segregation remains effective.

## 25. Monitor application boundary activity

The application should generate useful security events for:

- connection acceptance and rejection;
- authentication and authorisation failure;
- unknown service identity;
- blocked destination;
- unexpected protocol or method;
- repeated API denial;
- invalid message or schema;
- file-transfer failure;
- attempted project or tenant crossing;
- administrative-interface access;
- supplier access;
- changes to endpoints or allow-lists;
- new or removed integrations;
- failed certificate validation;
- excessive rate or volume;
- scanner or gateway bypass;
- configuration drift; and
- loss of expected event flow.

The application should forward relevant events to the approved enterprise monitoring service.

## 26. Detect unapproved interfaces and flows

The application should identify when the deployed solution differs from the approved communication-flow inventory.

Indicators may include:

- new listening endpoint;
- new API route;
- changed destination;
- unexpected outbound connection;
- unapproved message topic;
- direct database connection;
- lower environment calling production;
- supplier access outside the approved path;
- newly enabled remote support;
- thick client using an obsolete endpoint;
- unexpected protocol;
- changed certificate trust;
- alternate file-transfer path; or
- firewall rule with no current application justification.

Detection may use:

- deployment validation;
- configuration comparison;
- network-flow reports;
- application self-reporting;
- API gateway inventory;
- service-mesh telemetry;
- firewall review;
- vulnerability scans;
- code review; and
- periodic architecture reconciliation.

## 27. Handle boundary-control failure safely

The application should define safe behaviour when a boundary-control dependency fails.

Examples include:

- identity service unavailable;
- certificate validation failure;
- API gateway unavailable;
- message broker authentication failure;
- DNS failure;
- firewall or routing change;
- proxy unavailable;
- malware scanner unavailable;
- policy-decision service unavailable;
- logging failure; and
- integration timeout.

The application should:

- fail closed for unauthorised access;
- avoid silently rerouting to an insecure path;
- prevent unvalidated processing;
- preserve transaction integrity;
- queue safely where appropriate;
- limit retries;
- alert support;
- avoid duplicate processing;
- provide non-sensitive user messages; and
- define controlled recovery.

## 28. Test boundary protection

Testing should include both authorised and unauthorised flows.

Tests should cover, where relevant:

- approved user access;
- unapproved network path;
- direct service access;
- direct database access;
- unknown API client;
- invalid or expired service token;
- wrong audience or scope;
- blocked API method;
- unauthorised record or project;
- alternate upload or file-transfer route;
- unapproved outbound URL;
- redirect and callback manipulation;
- server-side request forgery attempts;
- production/non-production crossover;
- supplier path;
- administrative interface;
- certificate failure;
- message replay;
- oversized or malformed payload;
- rate limits;
- fail-closed behaviour;
- logging and alerting; and
- recovery and failover.

Testing only that a firewall rule exists is insufficient. The application should demonstrate the resulting end-to-end behaviour.

## 29. Review boundary protection after change

The application should review its boundaries and flows after:

- new interface;
- new integration;
- new application tier;
- migration;
- new thick client;
- new supplier;
- new support model;
- introduction of an API gateway or message broker;
- product upgrade;
- new file-transfer method;
- new outbound requirement;
- production or recovery architecture change;
- change in information sensitivity;
- incident;
- penetration-test finding; and
- enterprise network or identity-service change.

The architecture, flow inventory, firewall justification, test coverage and SSP should be updated together.

## 30. Remove obsolete connectivity

When an interface, supplier, service, endpoint or component is retired, the application should ensure that:

- application configuration is removed;
- credentials and certificates are revoked;
- API clients and scopes are removed;
- message permissions are removed;
- scheduled transfers stop;
- firewall and proxy rules are withdrawn;
- DNS or service-discovery records are updated;
- thick-client configuration is updated;
- monitoring rules are revised;
- documentation and inventories are updated; and
- residual connectivity is tested as unavailable.

Retired connectivity should not remain “just in case”.

## 31. Manage boundary-protection exceptions

Where a legacy or supplier-controlled application cannot meet the expected boundary model, record:

- the affected interface or flow;
- source and destination;
- required control;
- actual implementation;
- business need;
- information involved;
- risk;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, isolation, upgrade or retirement plan; and
- review or expiry date.

Examples include:

- unavoidable direct database access;
- unencrypted legacy protocol;
- shared service identity;
- broad network source range;
- inability to restrict outbound destinations;
- unsupported certificate validation;
- supplier-only remote access method; or
- weak production/non-production separation.

The exception should appear in the application addendum or risk process, not only in a firewall ticket.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate network, identity, PKI, firewall, proxy, monitoring and change-management services. They exclude enterprise network engineering, firewall implementation and major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the application boundary and trust zones** | Identify application components, users, tiers, data stores, administrative paths, integrations, inherited services and where trust or privilege changes. | Summarise the boundary in the **SSP SC-07 statement** and maintain the detail in the existing **security architecture**, **system context diagram**, **ConOps** or **SyOps**. | **6–12 hours** |
| **2. Maintain an approved communication-flow inventory** | Record each material source, destination, protocol, direction, purpose, identity, data type, protection and owner. | Use the existing **data-flow diagrams**, **interface control documents**, **connectivity register**, **firewall requests**, **API specifications** or **deployment design**, referenced by the SSP. | **8–20 hours** |
| **3. Apply deny-by-default at application interfaces** | Expose only required endpoints, methods, clients, topics, transfers and destinations and reject everything not explicitly approved. | Record approved interfaces in the **security design**, **CM-06 configuration**, **API/interface specifications** and **SSP**. Verify through the normal **security test report**. | **8–24 hours** |
| **4. Enforce server-side identity and authorisation** | Authenticate users and services and authorise every material request at the receiving service rather than relying on network location or client controls. | Capture the design in the **security architecture**, **access-control design**, **SSP AC-03/SC-07 sections** and normal **SDLC requirements**. | **16–40 hours** |
| **5. Separate user, service, data and administrative paths** | Prevent ordinary clients from directly accessing databases or privileged interfaces and restrict each tier to required downstream services. | Record the separation in the **solution architecture**, **deployment design**, **database design**, **SyOps** and **role matrix**. | **12–32 hours** |
| **6. Protect thick-client communications where applicable** | Configure approved endpoints, authenticated encrypted transport, server validation, no embedded privileged credentials and server-side access enforcement. | Use the existing **thick-client design**, **packaging specification**, **CM-06 configuration**, **SyOps** and **installation/security test report**. | **8–20 hours** |
| **7. Protect APIs, messages and file transfers** | Authenticate callers, validate operations and content, restrict destinations and scopes, control size and rate, prevent replay and log material outcomes. | Record requirements in the **API specifications**, **interface control documents**, **message schemas**, **file-transfer design**, **security design** and **test reports**. | **16–48 hours** |
| **8. Restrict outbound destinations and callbacks** | Use approved destination allow-lists, prevent arbitrary URLs, disable unapproved telemetry and external connections and protect callback or webhook registration. | Define flows in the **architecture**, **interface specification**, **CM-06 settings**, **SSP**, and corresponding **proxy/firewall/change records**. | **8–24 hours** |
| **9. Separate production and non-production** | Use separate identities, secrets, endpoints and data paths and control promotion and temporary support access. | Record the model in the **environment architecture**, **ConOps/SyOps**, **deployment design**, **secrets configuration** and **release test report**. | **8–20 hours** |
| **10. Protect privileged and supplier access paths** | Restrict administrative and supplier interfaces to named approved identities, approved management paths, limited duration and full logging. | Record arrangements in the **SyOps**, **support model**, **privileged-access design**, **supplier record**, **SSP** and normal **access/change records**. | **8–20 hours** |
| **11. Protect information crossing boundaries** | Apply approved encryption, schema and content validation, project or data-scope controls, masking, export restrictions and safe error handling. | Capture controls in the **security design**, **data-flow design**, **interface specifications**, **data model**, **SSP SC-07/AC-04/SC-08 sections** and **test report**. | **12–32 hours** |
| **12. Log and monitor application boundary activity** | Generate events for rejected connections, unknown clients, invalid tokens, changed destinations, cross-project attempts, privileged paths and flow failures. | Define events in the **SSP AU-02/SI-04/SC-07 sections** and existing **event specification**. Verify in the **SIEM onboarding** and **security test report**. | **6–16 hours** |
| **13. Test approved and prohibited flows end to end** | Test direct tier access, API misuse, database access, outbound manipulation, SSRF, environment crossover, supplier access, certificate failure and fail-closed behaviour. | Add cases to the normal **security test plan**, **integration test plan**, **penetration test** or **operational acceptance test** and retain results in established reports. | **16–40 hours per major test cycle** |
| **14. Verify flows after deployment and material change** | Confirm that deployed endpoints, routes, clients, destinations and settings match the approved architecture and flow inventory. | Record checks in the **release checklist**, **operational acceptance record**, **post-implementation review**, **configuration review** or **service review**. | **4–12 hours per release or review** |
| **15. Remove obsolete interfaces and connectivity** | Withdraw application configuration, credentials, API clients, firewall rules, transfer jobs and monitoring for retired connections and verify they no longer work. | Use the normal **decommissioning record**, **change ticket**, **interface register**, **firewall withdrawal**, **CM-08 update** and **post-change test evidence**. | **4–12 hours per retired interface** |
| **16. Document and manage boundary exceptions** | Record unavoidable direct access, weak protocols, broad routes, supplier restrictions or other gaps with compensating controls and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP SC-07 statement**. | **4–10 hours per exception** |

### Indicative total

For a typical internal multi-tier application with established enterprise network and identity services, initial application effort is commonly around **130–320 hours**.

A simple commercial application with one approved user interface and one database may require less. A complex engineering platform with thick clients, many APIs, project segregation, message flows, supplier support and legacy direct connections may require substantially more.

The estimates should not be added mechanically where activities overlap. SC-07 work commonly shares architecture, implementation and evidence with AC-03, AC-04, AC-06, AC-17, CM-06, CM-07, SI-04, SC-08, SC-12, SC-13 and SI-10.

---

## Suggested document placement

To avoid creating disconnected evidence, boundary-protection information should normally be distributed across existing application and SDLC artefacts:

- **SSP:** SC-07 implementation approach, application boundary, inherited enterprise controls, managed interfaces, key flow restrictions, ownership and exceptions.
- **ConOps or SyOps:** operational communication paths, support and supplier access, failure behaviour, degraded modes, recovery and escalation.
- **Security or solution architecture:** trust boundaries, tiers, enforcement points, zones, interfaces, privileged paths and inherited services.
- **System context and data-flow diagrams:** users, components, information flows, external dependencies and trust transitions.
- **Interface control documents:** source, destination, protocol, port, identity, scope, data, validation and failure behaviour.
- **API specifications:** routes, methods, callers, scopes, schemas, limits and security responses.
- **Message and file-transfer specifications:** producers, consumers, queues, topics, formats, validation, replay and reconciliation.
- **CM-06 configuration specification:** endpoints, allow-lists, certificates, proxy settings, feature flags, timeouts and permitted protocols.
- **CM-02 baseline and CM-08 inventory:** approved components, interfaces, client packages, services and versions.
- **Role and access matrix:** user, privileged, support, supplier and service permissions.
- **Thick-client design and packaging specification:** approved destinations, transport protection, local configuration and client/server compatibility.
- **Firewall, proxy and connectivity requests:** enterprise implementation of approved application flows, linked to architecture and change approval.
- **SDLC backlog and technical design:** application-layer enforcement, validation, SSRF prevention, rate limits and fail-closed requirements.
- **Test plans and reports:** positive and negative communication tests, environment separation, direct-access attempts and failure handling.
- **Release and operational acceptance records:** confirmation that deployed flows match the approved design.
- **SIEM onboarding and monitoring evidence:** boundary-related events, alerts and health checks.
- **Service reviews and post-implementation reviews:** continuing verification of connections and obsolete-flow removal.
- **Risk register or application addendum:** legacy protocols, direct database paths, broad rules, supplier limitations and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate Internet and external network perimeter protection;
- enterprise firewalls and network access-control infrastructure;
- corporate network segmentation and routing;
- VPN gateway and remote-access infrastructure;
- enterprise proxies and secure web gateways;
- central DNS, DHCP and IP-address management;
- network intrusion detection and prevention;
- enterprise DDoS protection;
- corporate wireless and physical network controls;
- managed load balancers and reverse proxies where provided as a service;
- enterprise API gateways or service meshes where operated centrally;
- enterprise PKI and certificate policy;
- corporate network-flow monitoring;
- network-device hardening;
- enterprise supplier remote-access platform;
- central firewall-rule governance;
- shared environment and infrastructure boundary assessments; and
- SOC monitoring of enterprise network events.

The application team must still:

- define its own boundary and trust transitions;
- identify required flows;
- justify enterprise connectivity requests;
- implement application-layer identity, authorisation and validation;
- restrict thick clients, APIs, messages and file transfers;
- control outbound destinations;
- separate production and non-production correctly;
- provide boundary-related logs;
- test end-to-end behaviour; and
- remove connectivity when no longer required.

> **Key dividing line:** the enterprise operates the shared network boundary mechanisms; the application defines, constrains and verifies the communication paths and trust decisions required by the business application.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, SC-07 Boundary Protection.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, SC-07 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-41 Rev. 1, Guidelines on Firewalls and Firewall Policy**.
4. National Institute of Standards and Technology, **NIST SP 800-207, Zero Trust Architecture**.
5. National Institute of Standards and Technology, **NIST SP 800-207A, A Zero Trust Architecture Model for Access Control in Cloud-Native Applications in Multi-Location Environments**.
6. National Institute of Standards and Technology, **NIST SP 800-53 Release 5.2.0**, including the current control catalogue and corresponding assessment-procedure updates.
