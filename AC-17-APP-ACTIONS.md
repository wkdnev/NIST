# AC-17 Remote Access — Application Actions

## Purpose

For an internal corporate-network application, AC-17 means the application must ensure that **remote use of the application occurs only through authorised enterprise remote-access services and remains subject to the same—or stronger—application security controls as access from an office location**.

In the stated environment:

- the application is not Internet-facing;
- users connect remotely only from hardened, centrally managed corporate Microsoft Windows EUC devices;
- remote connectivity is provided through an approved corporate VPN;
- corporate identity, multi-factor authentication and device-compliance checks are required;
- split tunnelling is prohibited; and
- the enterprise operates the remote-access infrastructure.

Those enterprise controls are inherited. The application should not reproduce the VPN, corporate MFA, endpoint-compliance, firewall or remote-access gateway.

The application remains responsible for ensuring that remote access does not create an application-layer bypass. It must determine:

- whether each application function is permitted remotely;
- whether remote users and administrators receive the correct roles and information scope;
- whether the application accepts access only through approved internal routes;
- whether thick clients and browser sessions behave securely over remote connections;
- whether privileged and supplier access is more tightly controlled;
- whether remote sessions, exports, downloads and local storage are appropriately constrained;
- whether application logs provide useful remote-access context;
- whether loss or change of VPN, identity, device or session trust is handled safely; and
- whether remote-access limitations and exceptions are documented.

NIST AC-17 requires organisations to establish usage restrictions, configuration and connection requirements, and implementation guidance for each permitted type of remote access; authorise remote access before allowing it; route remote access through authorised and managed access-control points; protect remote-access confidentiality and integrity; control privileged commands and access to security-relevant information; and monitor and control remote sessions. NIST SP 800-46 Rev. 2 provides supporting guidance for enterprise telework and remote-access technologies, while NIST SP 800-207 reinforces that network location alone should not create implicit trust.

> **Core principle:** the enterprise establishes the secure remote connection; the application decides what the remotely connected identity may do and must continue to authenticate, authorise, constrain, monitor and protect every application action.

---

## 1. Define the application’s permitted remote-access model

The application should explicitly state the approved remote-access model.

For the stated corporate architecture, the normal model is:

1. the user operates an approved corporate Windows EUC device;
2. the user establishes the approved corporate VPN;
3. the enterprise validates corporate identity, MFA and device compliance;
4. all relevant traffic is routed through corporate controls, with split tunnelling prohibited;
5. the user accesses the application through its approved internal endpoint; and
6. the application independently authenticates or consumes the approved corporate identity and enforces application authorisation.

The application should explicitly prohibit, unless separately approved:

- direct Internet access;
- public application endpoints;
- access from personal or unmanaged devices;
- access from consumer VPN services;
- access from unapproved remote-desktop services;
- direct supplier connections;
- direct database access from remote devices;
- external identity providers;
- remote access that bypasses corporate MFA;
- local or cached credentials that bypass enterprise identity;
- alternate external URLs;
- unauthorised cloud relays;
- split-tunnel application paths; and
- unmanaged browser or mobile access.

The SSP should state the approved model and identify inherited enterprise controls.

## 2. Identify remotely accessible application functions

The application should identify which functions are:

- permitted remotely;
- permitted remotely only for specified roles;
- permitted only with stronger authentication or approval;
- permitted only during an authorised support window;
- restricted to corporate premises or approved management networks;
- prohibited remotely; or
- unavailable by design.

Functions requiring particular consideration include:

- ordinary record viewing and editing;
- bulk download and export;
- print and report generation;
- privileged administration;
- role and account management;
- security configuration;
- support impersonation;
- database administration;
- direct data correction;
- release and deployment;
- certificate and secret management;
- audit-log access;
- incident evidence access;
- backup and recovery;
- supplier maintenance;
- emergency functions; and
- high-impact approval or signing.

The application should not assume that all functions permitted internally are automatically suitable for remote use.

## 3. Define remote-access usage restrictions

Application-specific restrictions should be based on:

- information sensitivity;
- business impact;
- privilege;
- operational need;
- device capability;
- local storage;
- export capability;
- support model;
- supplier involvement;
- transaction risk;
- user role;
- project or information community;
- incident status; and
- enterprise remote-access policy.

Restrictions may include:

- remote access permitted only to specified roles;
- privileged functions prohibited remotely;
- bulk export disabled remotely;
- local download restricted;
- printing prohibited or limited;
- support impersonation requiring additional approval;
- supplier access limited to approved windows;
- emergency access requiring enhanced monitoring;
- direct production data changes prohibited;
- application administration limited to PAM-controlled sessions;
- sensitive projects requiring an approved location or management path; and
- remote access suspended during a security incident.

## 4. Use only authorised remote-access entry points

The application should be reachable remotely only through the enterprise-approved path.

The application team should:

- identify the approved internal application endpoints;
- identify the relevant VPN or access-control path by enterprise service reference;
- ensure no separate public listener exists;
- ensure alternate hostnames do not expose a weaker route;
- ensure APIs and thick-client services use approved internal endpoints;
- ensure supplier support uses the authorised enterprise path;
- ensure administrative interfaces are not exposed through ordinary remote-user routes unless approved;
- restrict direct server and database connectivity;
- remove obsolete remote endpoints;
- verify firewall and routing requests against the application architecture; and
- test that prohibited paths do not work.

The enterprise configures network routes and gateways. The application defines and verifies which endpoints are legitimate.

## 5. Do not treat VPN presence as application authentication

A VPN connection establishes a protected network path and enterprise access context. It does not by itself prove that an application request is authorised.

The application should still:

- authenticate the user through the approved corporate identity mechanism;
- validate federation assertions or integrated authentication;
- map the identity uniquely to the application account;
- check account status;
- enforce application roles;
- enforce project and information scope;
- enforce least privilege;
- enforce separation of duties;
- validate every request;
- protect sessions; and
- deny unauthenticated direct API calls.

The application should not grant access solely because a request originates from:

- a corporate IP range;
- a VPN address;
- a managed network segment;
- a known proxy;
- a corporate device subnet; or
- an internal hostname.

## 6. Consume enterprise remote-access context only when authoritative

Where the enterprise makes trusted remote-access or device context available to the application, the application may use it in access decisions.

Potential context includes:

- remote versus on-premises session;
- managed-device status;
- device-compliance result;
- VPN assurance;
- authentication method;
- authentication time;
- user risk;
- privileged-access session;
- approved supplier session;
- source access zone; and
- incident-driven restrictions.

The application should:

- accept context only from an approved authoritative source;
- validate integrity and freshness;
- define the consequence of missing context;
- avoid trusting user-supplied headers or parameters;
- document which decisions rely on the context;
- log material decisions;
- fail safely when required context is unavailable; and
- avoid replicating enterprise device-compliance logic.

## 7. Require appropriate authentication strength

The application should rely on the enterprise-approved authentication and MFA service and require the appropriate authentication context for the function being used.

The application should:

- validate the approved identity provider;
- verify issuer, audience, signature and expiry;
- verify required MFA or assurance claims where available;
- reject weaker or unknown authentication contexts;
- require recent authentication or step-up for high-impact functions where approved;
- prohibit local password fallback unless formally authorised;
- prevent silent downgrade during VPN or identity-service failure;
- require named privileged identities for administration; and
- distinguish user authentication from service authentication.

Sensitive remote functions may require reauthentication even where the VPN session remains active.

## 8. Bind the application session to the authenticated user

Remote application sessions should remain securely bound to the authenticated identity.

The application should:

- use unpredictable session identifiers;
- protect cookies or tokens;
- rotate session identifiers after authentication and privilege change;
- prevent session fixation;
- prevent replay;
- enforce inactivity and absolute session limits;
- invalidate sessions on sign-out;
- handle account disablement;
- handle role or project removal;
- handle token expiry;
- prevent session tokens in URLs and logs;
- limit concurrent sessions where justified;
- terminate support impersonation cleanly; and
- require reauthentication for defined sensitive actions.

The application should not assume that the VPN closing will always terminate the application session immediately.

## 9. Define behaviour when the VPN connection changes or drops

Applications—especially thick clients—should handle remote network interruption safely.

The application should define:

- transaction behaviour after loss of connectivity;
- whether in-progress changes are committed or rolled back;
- retry limits;
- duplicate-submission prevention;
- offline caching;
- session expiry;
- reconnection;
- token refresh;
- record locking;
- file-transfer recovery;
- message replay;
- user notification;
- audit-event continuity; and
- prevention of insecure fallback.

The application should avoid:

- silently switching to an external endpoint;
- continuing indefinitely with stale authorisation;
- duplicating high-impact transactions;
- leaving records in ambiguous states;
- exposing sensitive cached information; and
- reconnecting without revalidating the session where necessary.

## 10. Protect thick-client remote access

For a thick client on corporate EUC, the application should:

- use approved internal server endpoints;
- validate server identity;
- use approved encrypted protocols;
- avoid embedded shared credentials;
- protect cached tokens and configuration;
- prevent user redirection to an unapproved server;
- enforce all security decisions server-side;
- support approved proxy and VPN routing;
- prevent direct database access where possible;
- define supported client versions;
- prevent obsolete vulnerable clients from connecting where risk warrants;
- handle intermittent connectivity safely;
- protect local cached records;
- clear temporary sensitive data;
- log relevant connection and authentication failures; and
- distribute changes through the corporate software-management process.

The enterprise owns EUC hardening and VPN. The application owns the thick client’s secure behaviour.

## 11. Protect browser-based remote access

For internal browser applications, the application should:

- expose only approved internal URLs;
- require enterprise authentication;
- use approved TLS;
- protect session cookies;
- enforce server-side authorisation;
- prevent direct unauthenticated deep links;
- prevent sensitive data in URLs;
- control browser caching;
- set appropriate security headers;
- prevent open redirects;
- protect downloads;
- prevent cross-origin access from unapproved origins;
- provide non-sensitive errors;
- terminate sessions predictably; and
- avoid depending solely on the VPN address for trust.

## 12. Protect remote API access

Where interactive clients or remote-support tools call application APIs, the application should:

- authenticate the caller;
- validate token issuer, audience, scope and expiry;
- authorise each operation;
- restrict approved clients;
- validate request schema and content;
- enforce object and project scope;
- rate-limit;
- prevent replay;
- restrict bulk extraction;
- protect callback destinations;
- reject direct calls that bypass user authentication;
- log caller and end-user identity where delegated access is used; and
- retire obsolete API versions and clients.

## 13. Restrict privileged remote access

Remote privileged access should receive stronger controls than ordinary user access.

The application should:

- use named privileged identities;
- integrate with enterprise PAM where available;
- require the approved MFA or authentication context;
- limit privileged access to authorised management paths;
- prohibit direct privileged access from ordinary user interfaces where practical;
- apply just-in-time or time-limited privilege;
- require a business reason or change/support reference;
- restrict duration;
- record the real operator;
- log all material actions;
- prevent silent impersonation;
- prevent the administrator from disabling their own audit trail;
- terminate dormant privileged sessions;
- review activity after use; and
- remove temporary privilege promptly.

Where a privileged function is not appropriate remotely, the application should prohibit it even when the enterprise VPN technically permits the connection.

## 14. Restrict remote access to security-relevant information

The application should identify security-relevant information that needs additional restriction, such as:

- audit logs;
- vulnerability findings;
- authentication configuration;
- role and permission models;
- security architecture;
- incident evidence;
- secrets or certificate metadata;
- supplier diagnostic packages;
- database administration information;
- monitoring configuration;
- recovery information; and
- security-test reports.

Remote access to such information should be limited to authorised roles and protected against unnecessary download, export or local retention.

## 15. Control remote administrative commands

Where remote administration is permitted, the application should define which commands or functions may be executed remotely.

Controls should include:

- function-level authorisation;
- least privilege;
- approved management path;
- command or operation allow-listing where practical;
- change or support reference;
- data-scope restriction;
- prevention of arbitrary command execution;
- safe input validation;
- approval for destructive or high-impact actions;
- session recording or enhanced logging where provided;
- time limitation;
- output protection;
- post-action verification; and
- emergency handling.

Remote access to a server does not automatically authorise all application administration.

## 16. Control supplier remote access

Supplier personnel should use the approved enterprise remote-support mechanism.

The application should require:

- named supplier identities;
- internal sponsor;
- approved support case;
- approved access window;
- minimum role and component scope;
- approved corporate or managed support endpoint as required by enterprise policy;
- MFA;
- PAM or monitored support path where available;
- no direct Internet-facing maintenance interface;
- no unapproved remote-control tools;
- controlled file transfer;
- restricted information export;
- logging and monitoring;
- change approval before production modification;
- prompt revocation;
- post-session review; and
- confirmation of supplier file and package integrity.

Supplier support should not rely on permanent generic credentials.

## 17. Control emergency remote access

Emergency remote access should be defined rather than improvised.

The application should specify:

- qualifying emergency conditions;
- accountable owner;
- approving authority;
- permitted identities;
- permitted functions;
- remote path;
- authentication strength;
- duration;
- logging;
- notification;
- evidence preservation;
- post-use review;
- credential or privilege reset;
- return-to-normal conditions; and
- risk acceptance where normal restrictions could not be maintained.

Emergency remote access should not become a routine support route.

## 18. Restrict remote database access

Ordinary users and thick clients should not connect directly to application databases over the VPN.

Where remote database access is required for administration or support, it should be:

- explicitly authorised;
- restricted to named privileged identities;
- routed through the approved management or PAM path;
- limited to required database roles;
- time-limited;
- associated with a change, incident or support record;
- monitored;
- prohibited from personal database tools where enterprise policy requires managed tooling;
- restricted from direct business-data changes unless separately approved;
- protected by encrypted transport; and
- independently reviewed for high-impact activity.

## 19. Restrict remote deployment and change

Remote connectivity should not permit developers or support users to bypass CM-05 controls.

The application should ensure that:

- production deployment uses the approved pipeline or privileged path;
- deployment requires approved artefacts;
- direct copying from a remote user device is prohibited;
- developers do not receive routine production write access;
- configuration changes are controlled;
- database migrations use approved identities and scripts;
- supplier changes are internally approved;
- emergency change is attributable;
- temporary access expires;
- deployment and configuration events are logged; and
- post-change verification is completed.

## 20. Protect information in transit

Application traffic over remote access should use approved cryptographic protection even though the VPN also protects network transport.

The application should:

- use approved TLS or other enterprise protocols;
- validate server certificates;
- reject expired or untrusted certificates;
- prevent protocol downgrade;
- protect credentials and session tokens;
- use mutual authentication for service-to-service connections where required;
- protect file transfer;
- manage certificate rollover;
- avoid clear-text legacy protocols;
- document unavoidable exceptions; and
- test transport configuration.

Layered protection ensures that data remains protected across internal segments beyond the VPN termination point.

## 21. Control remote downloads and exports

The application should assess whether remote access changes the risk of portable copies.

Controls may include:

- permit download only to managed EUC;
- restrict bulk export;
- restrict specified information types;
- restrict supplier downloads;
- require additional approval;
- apply project or record scope;
- apply markings;
- generate protected files;
- use expiring download links;
- limit quantity;
- log the user, scope and outcome;
- prevent unauthenticated direct links;
- avoid exposing file shares directly; and
- support incident-driven suspension.

The application should rely on enterprise endpoint and DLP controls where provided, but still enforce application-specific export authorisation.

## 22. Control printing and clipboard use where justified

Where information sensitivity warrants it, the application should determine whether remote sessions may:

- print;
- copy to clipboard;
- export to office formats;
- copy attachments;
- use screen-capture-sensitive views;
- save locally; or
- use offline mode.

Technical restriction may not always be feasible, particularly in ordinary browser applications. Where restriction is required but unavailable, the application should document:

- the limitation;
- enterprise endpoint controls relied upon;
- user obligations;
- monitoring;
- information-owner approval; and
- longer-term remediation.

## 23. Protect local and offline data

Where the application or thick client stores data locally, it should define:

- permitted data;
- storage location;
- encryption;
- access permissions;
- cache duration;
- deletion;
- session binding;
- behaviour after account disablement;
- behaviour after VPN loss;
- synchronisation;
- conflict handling;
- audit-event upload;
- device replacement;
- incident response; and
- whether offline use is permitted.

Offline access should be disabled unless there is a documented business need and an approved security design.

The enterprise owns device encryption and endpoint controls; the application owns what it places on the device and how long it remains.

## 24. Prevent remote-access information-flow bypass

Remote users should remain subject to AC-04 information-flow rules.

The application should continue to enforce:

- project boundaries;
- record ownership;
- classification and handling;
- export restrictions;
- supplier restrictions;
- lower-environment restrictions;
- report distribution;
- approved recipients;
- integration destinations;
- notification content; and
- production data controls.

VPN access should not create a broader information community.

## 25. Prevent remote-access boundary bypass

Remote access should remain aligned with SC-07.

The application should ensure that:

- only approved endpoints are exposed;
- administrative interfaces are separated;
- direct tier and database access is restricted;
- outbound destinations remain controlled;
- no external callback or update path is introduced;
- unapproved supplier tunnels are prohibited;
- remote users cannot turn the application into a proxy;
- production and non-production remain separated; and
- recovery routes do not bypass normal controls.

## 26. Handle device-compliance failure safely

Where the application receives authoritative device-compliance context, it should define behaviour when:

- the device becomes non-compliant;
- the compliance claim is stale;
- the claim is missing;
- the device identity changes;
- the enterprise access session is revoked;
- the device is reported lost;
- the device is under incident response; or
- the corporate EUC is no longer managed.

Possible application actions include:

- deny new session;
- require reauthentication;
- restrict sensitive functions;
- terminate or shorten the session;
- prevent download;
- alert support;
- suspend privileged activity; and
- preserve relevant evidence.

The application should not attempt to perform its own endpoint health inspection unless explicitly designed and approved.

## 27. Handle identity and account changes during remote sessions

The application should define how active sessions respond when:

- the enterprise identity is disabled;
- the application account is disabled;
- project membership is removed;
- privilege is revoked;
- the user changes role;
- supplier access expires;
- a session is identified as compromised;
- MFA status changes;
- emergency restrictions are imposed; or
- an incident requires widespread revocation.

The application should support timely session invalidation or revalidation proportionate to risk.

## 28. Protect remote authentication and session errors

Error messages should not reveal:

- whether a named account exists;
- internal VPN addressing;
- identity-provider configuration;
- token details;
- certificate internals;
- server names beyond what is operationally necessary;
- privileged routes;
- stack traces;
- database information; or
- security-control states.

Detailed diagnostics should be available only through protected logs and authorised support processes.

## 29. Log remote application access

The application should generate useful events for:

- successful and failed authentication;
- remote versus on-premises context where authoritative and available;
- privileged remote access;
- supplier access;
- emergency access;
- session creation and termination;
- account-disabled denial;
- insufficient authentication strength;
- non-compliant device denial where the application consumes that context;
- restricted function denial;
- bulk export or download;
- remote administrative actions;
- support impersonation;
- direct API denial;
- unusual thick-client version;
- attempted use of obsolete endpoint;
- session-revocation failure; and
- changes to remote-access policy or configuration.

Events should include:

- stable user identity;
- application and environment;
- session or correlation identifier;
- time;
- outcome;
- role;
- source-access context where trustworthy;
- privileged, supplier or emergency status;
- affected function;
- relevant change, support or incident reference; and
- application component.

The application should not log passwords, full tokens or unnecessary sensitive information.

## 30. Monitor remote-access anomalies

The application should support detection of:

- repeated authentication failure;
- remote use of disabled accounts;
- privileged access outside approved windows;
- supplier access without a current support case;
- bulk download from a remote session;
- unusual export volume;
- emergency access;
- attempts to reach prohibited administrative functions;
- remote direct database attempts;
- obsolete thick-client use;
- many concurrent sessions;
- rapid session switching;
- repeated device-compliance denial;
- remote access after role removal;
- session use after revocation;
- attempts to use alternate endpoints; and
- changes to remote-access restrictions.

The enterprise SOC may operate the alerting platform. The application must provide meaningful events and application context.

## 31. Monitor and control remote sessions

Application-level session controls should include, where proportionate:

- inactivity timeout;
- absolute lifetime;
- sign-out;
- reauthentication;
- concurrent-session rules;
- privileged-session timeout;
- session revocation;
- supplier-session expiry;
- emergency-session expiry;
- impersonation timeout;
- transaction integrity after disconnect;
- visibility of current sessions to authorised support;
- termination of suspicious sessions; and
- recording or enhanced audit of privileged sessions where provided through enterprise PAM.

The application should not depend solely on the VPN session timeout.

## 32. Protect remote support tools and diagnostics

Application support tools should:

- require named authenticated users;
- use approved enterprise remote paths;
- restrict functions by role;
- avoid full production data where unnecessary;
- mask sensitive content;
- prevent arbitrary command execution;
- require a case reference;
- log diagnostics;
- protect support bundles;
- restrict file upload and download;
- expire diagnostic access;
- prevent support impersonation from approving business actions; and
- remove temporary access.

## 33. Protect remote file transfer

Any file transfer used during remote support or application use should:

- use approved application or enterprise transfer paths;
- authenticate sender and recipient;
- restrict source and destination;
- validate file type and content;
- scan for malicious code;
- limit size and quantity;
- prevent direct execution;
- log transfer;
- protect restricted information;
- avoid personal file-sharing services;
- avoid unmanaged removable media;
- expire temporary staging; and
- support incident investigation.

## 34. Test remote access end to end

Testing should cover both permitted and prohibited scenarios.

Tests should include, where relevant:

- approved VPN and corporate EUC access;
- no-VPN access;
- unapproved external route;
- unmanaged-device context where testable through enterprise facilities;
- valid user with no application role;
- disabled account;
- insufficient MFA or authentication context;
- direct API bypass;
- direct database access;
- thick-client endpoint manipulation;
- obsolete client version;
- session expiry;
- VPN drop and reconnection;
- duplicate transaction prevention;
- role removal during session;
- privileged remote access;
- supplier session;
- emergency access;
- bulk export restriction;
- unauthorised administrative function;
- local or offline cache behaviour;
- logging and alerting;
- endpoint or certificate failure; and
- fail-closed behaviour when identity or policy context is unavailable.

Testing should validate application behaviour, not merely that the VPN connects.

## 35. Exercise remote-access incident scenarios

The application should periodically consider scenarios such as:

- compromised remote user account;
- lost corporate device;
- stolen application session;
- compromised supplier account;
- malicious privileged remote action;
- vulnerable thick-client version;
- remote bulk export;
- VPN session still active after account disablement;
- unapproved endpoint discovered;
- malware on a remote device interacting with the application;
- direct API abuse over VPN;
- split-tunnel policy violation detected by enterprise controls; and
- remote access during identity-service outage.

The exercise should confirm:

- relevant application evidence exists;
- sessions can be revoked;
- exports can be scoped;
- privileged access can be suspended;
- supplier access can be removed;
- affected records can be identified; and
- enterprise incident response receives useful application context.

## 36. Review remote access after material change

The application should reassess remote-access controls after:

- new thick client;
- new browser interface;
- new API;
- new privileged function;
- new supplier;
- new support model;
- new identity integration;
- VPN or enterprise remote-access change;
- device-compliance change;
- product upgrade;
- new download or export function;
- new offline capability;
- architecture migration;
- incident;
- penetration-test finding; or
- change to information sensitivity.

## 37. Review remote-access authorisations

At a defined frequency, the application should review:

- users permitted remote access where application-specific approval exists;
- privileged remote roles;
- supplier remote accounts;
- emergency access;
- local fallback accounts;
- support impersonation;
- direct database roles;
- remote deployment roles;
- application-specific remote restrictions;
- exceptions;
- dormant access;
- expired access; and
- functions newly exposed remotely.

Where the enterprise authorises general VPN use centrally, the application should not duplicate the enterprise VPN user review. It should review application-specific remote roles and exceptions.

## 38. Remove obsolete remote-access paths

When a route, client, supplier, function or support method is retired, the application should:

- disable endpoints;
- remove DNS or service registrations;
- remove callback addresses;
- revoke clients and credentials;
- remove supplier roles;
- remove direct database access;
- remove firewall or proxy requirements;
- withdraw thick-client packages;
- block obsolete client versions where needed;
- update architecture;
- update configuration and baseline;
- update monitoring; and
- test that the retired path no longer works.

## 39. Manage remote-access exceptions

Where a legacy or commercial application cannot meet the expected model, record:

- affected access path;
- expected control;
- actual implementation;
- users or roles affected;
- information and privilege exposure;
- reason;
- risk;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, isolation, upgrade or replacement plan; and
- review or expiry date.

Examples include:

- local application authentication;
- inability to consume MFA context;
- direct database access from VPN-connected EUC;
- shared supplier account;
- thick client storing sensitive data locally;
- inability to revoke sessions;
- unsupported encrypted protocol;
- privileged functions exposed through ordinary remote access;
- no application distinction between remote and on-premises sessions; or
- product dependence on a broad network route.

The exception should be recorded in the application addendum or risk process, not only in a firewall or support ticket.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses the approved corporate VPN, managed Windows EUC, corporate identity, MFA, device compliance, PAM and central monitoring. They exclude enterprise VPN, endpoint, identity and firewall engineering.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the approved application remote-access model** | State that access is internal only and permitted remotely solely through approved VPN, managed corporate EUC, corporate identity, MFA and device compliance, with no split tunnelling. | Summarise in the **SSP AC-17 statement** and maintain operational detail in the existing **ConOps**, **SyOps**, **security architecture** or **remote-access section of the support model**. | **4–8 hours** |
| **2. Identify remotely permitted and prohibited functions** | Classify ordinary, export, privileged, support, supplier, deployment, database and recovery functions by whether and under what conditions they may be used remotely. | Record the decisions in the **role/access matrix**, **business and security requirements**, **SyOps**, **privileged-access design** and **SSP**. | **6–16 hours** |
| **3. Verify use of authorised internal endpoints only** | Confirm browser, thick-client, API, support and administrative paths use approved internal routes and that no public, alternate or obsolete endpoint provides access. | Maintain evidence in the **security architecture**, **interface specifications**, **SC-07 flow inventory**, **firewall/change records** and **security test report**. | **8–20 hours** |
| **4. Enforce enterprise identity and application authorisation** | Authenticate through the approved corporate identity service, validate assertions and apply application roles, project scope and least privilege independently of VPN location. | Capture controls in the **identity integration design**, **SSP IA-02/AC-03/AC-17 sections**, **role matrix** and normal **authentication/access test report**. | **12–32 hours** |
| **5. Protect application sessions** | Apply secure session binding, inactivity and absolute limits, sign-out, reauthentication, role-change handling and revocation independent of VPN timeout. | Record requirements in the **session-management design**, **CM-06 configuration**, **SyOps**, **SSP** and **security test report**. | **8–24 hours** |
| **6. Protect thick-client remote behaviour where applicable** | Use approved endpoints and encryption, validate servers, protect tokens and caches, prevent direct database access and handle connection loss safely. | Use the existing **thick-client design**, **packaging specification**, **SyOps**, **CM-06 configuration** and **installation/security test report**. | **12–28 hours** |
| **7. Restrict privileged, supplier and emergency remote access** | Use named identities, PAM or approved management paths, stronger authentication, minimum scope, time limits, case/change references, logging and post-use review. | Record arrangements in the **privileged-access design**, **supplier record**, **support model**, **incident-response annex**, **PAM evidence** and **SSP**. | **8–24 hours** |
| **8. Control remote downloads, exports and local storage** | Apply application-specific export authorisation, volume and information-scope restrictions, protected downloads and explicit controls over offline or cached data. | Record requirements in the **AC-04 design**, **report/export specification**, **thick-client design**, **SyOps**, **data-handling design** and **SSP**. | **8–24 hours** |
| **9. Define safe VPN-drop, reconnect and dependency-failure behaviour** | Preserve transaction integrity, prevent duplicate actions, expire stale sessions and fail closed when required identity, device or policy context is unavailable. | Capture behaviour in the **resilience design**, **transaction design**, **SyOps**, **error-handling specification** and **resilience/security test report**. | **8–20 hours** |
| **10. Log and monitor remote application activity** | Generate useful events for remote authentication, privileged and supplier use, session activity, export, restricted-function denial, obsolete clients and remote-access policy changes. | Define events in the **SSP AU-02/SI-04/AC-17 sections** and existing **event specification**. Verify through **SIEM onboarding** and the **security test report**. | **6–16 hours** |
| **11. Test permitted, prohibited and failure scenarios** | Test approved VPN access, no-VPN access, alternate routes, disabled users, API bypass, session behaviour, privileged and supplier use, exports and VPN interruption. | Add cases to the normal **security test plan**, **integration test**, **operational acceptance test**, **penetration test** or **remote-working exercise**. | **16–40 hours per major test cycle** |
| **12. Review remote roles, paths and exceptions periodically** | Review application-specific privileged, supplier, emergency, support and direct-access permissions and confirm obsolete routes are removed. | Retain outcomes in established **access reviews**, **service reviews**, **PAM reviews**, **supplier reviews**, **CA-07 reports** or **application governance minutes**. | **6–16 hours per review** |
| **13. Exercise a remote-access incident scenario** | Test session revocation, account disablement, supplier removal, export scoping, evidence availability and coordination with enterprise incident response. | Use the normal **incident exercise**, **tabletop report**, **resilience exercise** or **IR-05 lessons record**, referenced from the SSP. | **8–16 hours per exercise** |
| **14. Document and manage application remote-access limitations** | Record local credentials, session-revocation gaps, direct database use, local cache, shared supplier access or other product constraints with compensating controls and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP AC-17 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application using mature corporate VPN, identity and endpoint services, initial application effort is commonly around **90–210 hours**.

A straightforward browser application with no privileged remote functions, local storage or supplier access may require less. A thick-client, legacy, highly privileged or supplier-supported application with local caching, direct database access or weak session revocation may require substantially more.

Ongoing application effort is commonly around **4–15 hours per month**, plus access reviews, exercises, incidents and material changes.

The estimates should not be added mechanically where activities overlap. AC-17 commonly shares implementation and evidence with:

- AC-02 account management;
- AC-03 access enforcement;
- AC-04 information-flow enforcement;
- AC-06 least privilege;
- IA-02 identification and authentication;
- SC-07 boundary protection;
- SC-08 transmission confidentiality and integrity;
- AU-02 event logging;
- SI-04 system monitoring;
- IR-05 incident monitoring; and
- CA-07 continuous monitoring.

---

## Suggested document placement

To avoid creating disconnected evidence, remote-access information should normally be distributed across established application and SDLC artefacts:

- **SSP:** AC-17 implementation approach, inherited enterprise VPN/MFA/device controls, permitted access model, application restrictions, monitoring and exceptions.
- **ConOps or SyOps:** remote user operation, connection-loss behaviour, support, privileged access, supplier access, emergency access and escalation.
- **Security architecture:** approved remote path, VPN termination dependency, internal endpoints, administrative paths, thick-client communication and trust boundaries.
- **SC-07 communication-flow inventory:** authorised browser, client, API, management and supplier routes.
- **Identity integration design:** identity provider, authentication context, device or remote-session claims, failure behaviour and session revocation.
- **Role/access matrix:** remotely permitted roles, privileged functions, supplier roles and prohibited functions.
- **Privileged-access design:** PAM integration, just-in-time access, remote administration, session monitoring and review.
- **Thick-client design and packaging specification:** approved endpoints, token handling, local cache, offline restrictions and supported versions.
- **API and interface specifications:** approved remote clients, authentication, scopes, direct-call restrictions and endpoint controls.
- **AC-04 data-handling and export design:** remote download, report, print, transfer and supplier-disclosure restrictions.
- **CM-06 configuration:** internal endpoints, session timeouts, certificate trust, remote feature flags and client-version settings.
- **Supplier support records:** named identities, access windows, support cases, approved paths and session review.
- **AU-02 and SI-04 evidence:** remote session, privileged, supplier, denial, export and anomaly events.
- **Test plans and reports:** no-VPN, alternate route, authentication, authorisation, disconnect, session, privileged and export scenarios.
- **Incident and exercise records:** lost device, compromised account, supplier misuse, session revocation and remote bulk-export scenarios.
- **Access and service reviews:** continuing validity of remote roles, supplier access, emergency access and exceptions.
- **Risk register or application addendum:** local authentication, direct database access, offline data, weak revocation and other limitations.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate remote-access and telework policy;
- VPN gateway and client;
- VPN authentication;
- enterprise MFA;
- device-compliance assessment;
- managed Windows EUC configuration;
- endpoint protection and EDR;
- corporate disk encryption;
- prohibition and enforcement of split tunnelling;
- enterprise network routing and firewall controls;
- remote-access gateway monitoring;
- enterprise proxy and DNS controls;
- corporate certificate and PKI services;
- enterprise privileged-access management platform;
- supplier remote-access platform;
- central SIEM and SOC monitoring;
- organisation-wide account and device revocation;
- enterprise incident response;
- corporate DLP and endpoint restrictions where provided; and
- organisation-wide remote-access risk and exception governance.

The application team must still:

- define which application functions may be used remotely;
- expose only approved internal endpoints;
- authenticate and authorise users at the application layer;
- protect sessions and thick clients;
- restrict privileged, supplier and emergency access;
- control exports and local storage;
- handle VPN and identity changes safely;
- log and test remote application activity;
- remove obsolete paths; and
- formally manage application-specific limitations.

> **Key dividing line:** the enterprise secures and operates the remote connection and managed endpoint; the application controls the user’s identity, privileges, information access, session and actions after that connection reaches the application.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, AC-17 Remote Access.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, AC-17 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-46 Rev. 2, Guide to Enterprise Telework, Remote Access, and Bring Your Own Device (BYOD) Security**.
4. National Institute of Standards and Technology, **NIST SP 800-207, Zero Trust Architecture**.
5. National Institute of Standards and Technology, **NIST SP 800-207A, A Zero Trust Architecture Model for Access Control in Cloud-Native Applications in Multi-Location Environments**.
