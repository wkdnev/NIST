# IA-02 Identification and Authentication (Organisational Users) — Application Actions

## Purpose

For an IT application, IA-02 means the application must **uniquely identify organisational users and verify that the claimed identity has been authenticated before granting access to application functions or information**.

The enterprise may provide:

- workforce identity proofing;
- corporate directory accounts;
- multi-factor authentication;
- federation and single sign-on;
- managed Microsoft Windows end-user computing devices;
- VPN access;
- certificate services;
- privileged-access management;
- authenticator lifecycle management;
- central identity monitoring; and
- joiner–mover–leaver processes.

Those capabilities are inherited.

The application remains responsible for ensuring that:

- every interactive user is represented by a unique, attributable identity;
- only approved enterprise identity providers are trusted;
- authentication results and assertions are validated correctly;
- the authenticated identity is bound to the correct application account;
- anonymous, shared, generic and fallback access is prohibited or tightly controlled;
- privileged, support and sensitive functions invoke the required authentication strength;
- sessions remain bound to the authenticated identity;
- authentication cannot be bypassed through APIs, thick clients, alternate routes or recovery functions;
- failed, stale or ambiguous identity information results in denial;
- authentication events are logged and monitored; and
- application-specific limitations are documented and managed.

NIST IA-02 requires organisational users to be uniquely identified and authenticated before access is granted. The current NIST Digital Identity Guidelines cover identity proofing, authentication, federation and assertions, while NIST zero-trust guidance emphasises that network location or device ownership must not create implicit trust. citeturn989374search0turn989374search4turn989374search6

> **Core principle:** the enterprise proves and authenticates the organisational identity; the application must consume that result securely, bind it to the correct user and require it consistently at every application access path.

---

## 1. Define the application’s organisational-user population

The application should identify who is considered an organisational user.

This may include:

- employees;
- contractors;
- agency or temporary workers;
- approved secondees;
- embedded supplier personnel operating as part of the organisation;
- privileged administrators;
- application support personnel;
- developers with approved non-production access;
- auditors;
- incident responders; and
- other users issued an enterprise-managed organisational identity.

The application should distinguish these from:

- service identities;
- API clients;
- batch jobs;
- devices;
- external customers;
- public users;
- business partners using external identities;
- supplier-managed identities; and
- emergency or recovery identities.

IA-02 concerns organisational users. Non-person identities and external users may be addressed through related identification and authentication controls, but the application must still prevent them from being misrepresented as ordinary organisational users.

## 2. Use unique, attributable user identities

Every organisational user should access the application through a unique identity.

The application should prohibit or tightly control:

- shared user accounts;
- generic team accounts;
- role accounts used by several people;
- anonymous access;
- guest access;
- vendor-default users;
- reused leaver identities;
- local aliases that obscure the enterprise identity;
- administrative accounts without a named owner; and
- support impersonation that hides the real operator.

The identity recorded by the application should be stable enough to preserve attribution when:

- the user’s display name changes;
- their email address changes;
- they move business unit;
- their role changes; or
- their account is later disabled.

Display names and email addresses alone are usually weak primary identifiers because they can change or be reused.

## 3. Use the approved enterprise identity provider

Where technically supported, the application should authenticate organisational users through the approved enterprise identity provider or federation service.

The application should:

- trust only approved issuers;
- use approved authentication protocols;
- use registered application or relying-party identifiers;
- protect client credentials and certificates;
- use approved redirect and callback addresses;
- restrict accepted identity domains or tenants;
- validate the identity provider’s signing keys;
- support key rollover;
- reject unsigned or incorrectly signed assertions;
- reject identities from unapproved identity providers; and
- avoid creating a separate application password where enterprise authentication is available.

Federation should reduce duplicate authentication systems, but it does not remove the application’s responsibility to validate the assertion.

## 4. Map the enterprise identity to the correct application account

The application should map the authenticated enterprise identity to one and only one application account.

The mapping should use a stable, authoritative identifier such as an approved subject or directory identifier.

The application should prevent:

- mapping based only on an editable display name;
- ambiguous matches;
- case or format inconsistencies;
- duplicate application profiles;
- automatic linking to an existing account based solely on email;
- user-controlled changes to the identity identifier;
- one enterprise identity mapping to several unintended users;
- several enterprise identities mapping to one ordinary user account; and
- account takeover during identity migration or renaming.

Where an identity cannot be mapped safely, access should be denied and the issue referred to the approved support process.

## 5. Validate authentication assertions and tokens

Applications that consume federated assertions or tokens should validate all security-relevant properties.

Depending on the protocol, validation should include:

- issuer;
- audience;
- signature;
- signing algorithm;
- expiry;
- not-before time;
- issue time;
- nonce;
- state;
- authorised client;
- redirect address;
- token type;
- subject identifier;
- authentication context;
- authentication time;
- required factors or assurance;
- tenant or domain;
- token binding where supported; and
- replay protections.

The application should not merely decode a token and trust the claims.

A token valid for another application, environment, audience or purpose must be rejected.

## 6. Require authentication before protected access

Authentication should be completed before the application provides:

- protected screens;
- records;
- reports;
- search results;
- file downloads;
- APIs;
- administrative functions;
- diagnostics;
- application configuration;
- audit information;
- workflow actions; or
- any metadata that reveals protected information.

The application should avoid unauthenticated endpoints that disclose:

- usernames;
- project names;
- record identifiers;
- system versions;
- internal paths;
- detailed error information;
- account status;
- role information;
- restricted health data; or
- sensitive application configuration.

Public or unauthenticated health checks should expose only the minimum information required by the approved operational design.

## 7. Apply authentication consistently across all access paths

The same authentication requirement should cover:

- browser access;
- thick clients;
- APIs used by interactive users;
- mobile interfaces where separately approved;
- report portals;
- file-download links;
- administrative consoles;
- support consoles;
- diagnostic interfaces;
- direct deep links;
- alternate hostnames;
- legacy routes;
- embedded application modules;
- recovery interfaces; and
- locally cached or offline functions.

A user should not be able to bypass authentication by calling a back-end service directly or manipulating the thick client.

## 8. Protect thick-client authentication

A thick client installed on a managed corporate Windows device should authenticate to the application through an approved method.

The application should:

- use the current signed-in corporate identity where approved;
- validate the target server;
- protect tokens and session material;
- avoid collecting the corporate password itself where federation or integrated authentication is available;
- avoid embedding shared credentials;
- use approved internal endpoints;
- prevent configuration from redirecting authentication to an unapproved server;
- use server-side authentication and authorisation;
- clear sensitive session material on sign-out;
- handle token expiry;
- prevent offline access unless explicitly designed and authorised; and
- distinguish client authentication from device compliance.

The managed EUC and VPN establish a trusted operating context, but they do not replace application authentication.

## 9. Require the appropriate authentication strength

The application should identify whether ordinary, privileged or particularly sensitive functions require different authentication strength.

Factors to consider include:

- information sensitivity;
- business impact;
- privilege;
- administrative capability;
- export volume;
- approval or signing;
- support impersonation;
- emergency access;
- access from a remote VPN session;
- access to cryptographic or security configuration;
- ability to change roles;
- ability to delete or release records; and
- applicable enterprise assurance requirements.

The enterprise determines the approved authentication mechanisms and assurance policy. The application must:

- request the required authentication context where the identity protocol supports it;
- verify that the required context was satisfied;
- deny access when it was not;
- avoid silently downgrading to weaker authentication; and
- document functions that require stronger or renewed authentication.

NIST defines multi-factor authentication as requiring more than one distinct authentication factor. citeturn989374search39

## 10. Use step-up or reauthentication for sensitive functions where required

A valid session may not be sufficient for every high-impact action.

The application should consider step-up authentication or reauthentication before:

- assigning privileged roles;
- changing security configuration;
- managing authenticators or trust;
- approving high-impact transactions;
- performing bulk export;
- revealing highly restricted information;
- support impersonation;
- emergency override;
- changing critical integration settings;
- deleting large data sets;
- disabling logging;
- signing or releasing controlled records; and
- recovering or resetting another user’s access.

Where step-up is required, the application should validate a recent authentication event or invoke the approved enterprise mechanism.

A password prompt implemented solely by the application should not be introduced casually where the enterprise identity service can provide stronger reauthentication.

## 11. Bind sessions to the authenticated identity

After authentication, the application should establish a session that remains securely bound to the authenticated user.

The application should:

- generate unpredictable session identifiers;
- protect session tokens in transit;
- use secure cookie or token settings;
- prevent user-controlled identity substitution;
- prevent session fixation;
- rotate identifiers after authentication or privilege change;
- validate token audience and scope on each relevant request;
- expire sessions appropriately;
- invalidate sessions on sign-out;
- prevent use after account disablement within the approved risk window;
- revoke or refresh after material role changes;
- protect against replay; and
- avoid placing session tokens in insecure URLs or logs.

The application should not accept a username, role or project identifier supplied by the client as proof of identity.

## 12. Separate authentication from authorisation

Successful authentication proves the claimed identity to the required level; it does not grant unrestricted access.

After authentication, the application should still enforce:

- approved account status;
- role;
- project or data scope;
- least privilege;
- separation of duties;
- workflow rules;
- information-flow policy;
- environment restrictions;
- temporary-access expiry; and
- privileged-function controls.

A corporate account authenticated with MFA may still have no approved access to the application.

## 13. Prevent implicit trust based on network location

The application should not treat a request as authenticated merely because it originates from:

- the corporate network;
- an approved subnet;
- the VPN;
- a managed EUC device;
- a server network;
- a known IP address;
- an internal proxy;
- a trusted integration zone; or
- a privileged support network.

NIST zero-trust guidance focuses on protecting resources and rejects network location as the primary basis for trust. citeturn989374search6turn989374search23

Network and device controls may contribute to the access decision, but the application should still establish and verify identity.

## 14. Control local application authentication

Where a commercial or legacy product cannot use enterprise authentication, local authentication should be treated as an exception or explicitly approved design.

The application should:

- justify why local authentication is required;
- uniquely identify every user;
- apply approved password and authenticator policy;
- prevent default credentials;
- protect stored authentication data;
- restrict password reset;
- rate-limit failed attempts;
- lock or delay repeated failures as required;
- support secure recovery;
- prohibit shared credentials;
- review accounts more frequently;
- log authentication activity;
- disable dormant and leaver accounts;
- test the implementation; and
- maintain a plan to federate, upgrade, isolate or replace where appropriate.

The application should not invent its own password rules where an approved enterprise standard exists.

## 15. Control fallback and emergency authentication

Fallback authentication may be required when the enterprise identity service is unavailable, but it creates a potential bypass.

The application should define:

- approved outage scenarios;
- who may activate fallback access;
- which identities may use it;
- allowed functions;
- authentication method;
- credential custody;
- start and expiry;
- monitoring;
- incident notification;
- post-use review;
- credential rotation;
- return to normal service; and
- evidence retention.

Fallback should normally be disabled and inaccessible during ordinary operation.

## 16. Prevent shared and generic authentication

Shared credentials weaken attribution and accountability.

The application should normally prohibit:

- departmental logins;
- generic administrator usernames used by several people;
- shared support credentials;
- team passwords;
- a common API token used interactively by users;
- kiosk-style access to protected application functions; and
- credentials embedded in shared scripts.

Where a shared technical identity is unavoidable, individual operators should be authenticated and attributable through an approved privileged-access or orchestration service before the technical identity is used.

## 17. Control privileged-user authentication

Privileged users should be strongly identified and authenticated.

The application should:

- require named privileged access;
- use the approved enterprise privileged identity or role;
- integrate with PAM where available;
- prevent ordinary accounts from invoking privileged functions unless authorised;
- require the approved MFA or authentication context;
- avoid persistent shared privileged sessions;
- log the real operator;
- prevent silent impersonation;
- terminate or constrain dormant privileged sessions;
- require reauthentication for high-impact actions where appropriate; and
- prohibit local administrator fallbacks unless approved.

## 18. Control support impersonation and “act as user” functions

Support personnel may need to reproduce a user’s experience, but the application should not erase operator identity.

The application should:

- authenticate the support user first;
- authorise the support function separately;
- identify both the support operator and affected user;
- require a business reason or ticket reference;
- limit scope and duration;
- display a clear indication of impersonation;
- prevent use for approval or signing unless specifically authorised;
- restrict export and sensitive data;
- log every material action;
- prevent nested or chained impersonation; and
- terminate impersonation cleanly.

The application should never require support staff to ask for or use the user’s password.

## 19. Handle authentication failure safely

The application should deny access when:

- the identity provider is unavailable;
- the token is invalid;
- the signature cannot be verified;
- the issuer or audience is wrong;
- the assertion is expired;
- the authentication context is insufficient;
- the user mapping is ambiguous;
- the account is disabled;
- required claims are missing;
- clock skew is outside the permitted tolerance;
- the callback state is invalid;
- the session is stale;
- certificate validation fails; or
- identity synchronisation is incomplete.

The application should:

- provide a non-sensitive error message;
- avoid revealing whether a particular user exists;
- avoid falling back to anonymous access;
- avoid accepting stale cached authentication indefinitely;
- log the failure reason securely;
- alert support for systemic failures; and
- preserve transaction integrity.

## 20. Protect authentication redirects and callbacks

Federated applications should protect the authentication flow itself.

The application should:

- register exact approved callback addresses;
- validate state;
- validate nonce;
- use approved response modes;
- reject arbitrary redirect destinations;
- prevent open redirects;
- use correlation between request and response;
- prevent login cross-site request forgery;
- reject unsolicited responses where the protocol requires;
- protect authorisation codes;
- use secure back-channel exchange where applicable;
- validate proof key mechanisms where required; and
- keep development and production registrations separate.

## 21. Protect authentication secrets and keys

The application may hold credentials used to establish trust with the identity provider, such as:

- client secrets;
- private keys;
- certificates;
- signing keys;
- metadata trust anchors;
- API credentials;
- recovery credentials; and
- fallback authenticators.

The application should:

- use approved secrets-management and certificate services;
- avoid source-code storage;
- restrict access;
- separate environments;
- rotate or renew before expiry;
- monitor expiry;
- support emergency revocation;
- prevent disclosure in logs or diagnostics;
- document ownership; and
- test rollover.

The enterprise owns the shared secrets or PKI platform; the application owns correct use and lifecycle of its application-specific trust material.

## 22. Handle identity-provider and key rollover

The application should be able to handle planned and emergency identity-provider changes without accepting untrusted keys.

It should:

- consume approved metadata or trust configuration;
- support overlapping valid keys during rollover;
- reject removed or revoked keys;
- verify metadata source and integrity;
- separate test and production trust;
- monitor certificate and key expiry;
- test rollover before production where practical;
- document emergency trust updates; and
- avoid disabling signature validation as a workaround.

## 23. Manage session timeout and reauthentication

Session management should reflect the application’s risk and enterprise policy.

The application should define:

- inactivity timeout;
- absolute session lifetime;
- token refresh behaviour;
- reauthentication triggers;
- privileged-session timeout;
- behaviour after device lock or network interruption;
- behaviour after role or account change;
- concurrent-session rules where required;
- sign-out behaviour;
- offline-session behaviour; and
- session invalidation after incident or compromise.

Timeouts should be long enough to support legitimate work but not allow abandoned sessions to remain useful indefinitely.

## 24. Prevent credential and token exposure

The application should avoid exposing authentication material through:

- URLs;
- browser history;
- referrer headers;
- logs;
- error messages;
- screenshots;
- clipboard;
- local configuration;
- crash dumps;
- support bundles;
- temporary files;
- client-side storage;
- analytics;
- source code; or
- report output.

Tokens should contain only necessary claims and should not be treated as harmless merely because they are signed or encoded.

## 25. Control cached and offline authentication

Where a thick client or other component supports cached or offline access, the application should explicitly define:

- business need;
- permitted users;
- permitted information;
- duration;
- local identity verification;
- token and data protection;
- revocation limitations;
- behaviour after account disablement;
- device requirements;
- reauthentication on reconnection;
- audit-event synchronisation;
- data clean-up; and
- incident response.

Offline authentication should not be enabled by default merely because the product supports it.

## 26. Log authentication activity

The application should generate security-relevant events for:

- successful authentication;
- failed authentication;
- rejected issuer or audience;
- invalid signature;
- expired assertion or token;
- insufficient authentication strength;
- account-disabled denial;
- ambiguous identity mapping;
- privileged authentication;
- step-up or reauthentication;
- fallback or emergency authentication;
- support impersonation;
- session creation;
- session termination;
- token refresh or revocation where material;
- trust-configuration changes; and
- authentication-service failures.

Events should include:

- application and environment;
- stable user identifier;
- time;
- outcome;
- authentication method or context where appropriate;
- session or correlation identifier;
- source component;
- failure category;
- privileged or fallback status; and
- relevant request identifier.

The application should not log passwords, complete tokens, private keys, recovery codes or unnecessary sensitive claims.

## 27. Monitor authentication anomalies

The application should support detection of:

- repeated failures;
- failures across many accounts;
- disabled-account attempts;
- use of fallback authentication;
- unexpected local-account use;
- authentication from an unapproved issuer;
- token replay;
- impossible or unusual session patterns where reliable context exists;
- privileged authentication outside expected activity;
- excessive concurrent sessions;
- sudden changes in authentication method;
- repeated identity-mapping failures;
- authentication after termination;
- support impersonation outside approved periods; and
- systemic identity-provider validation failures.

The enterprise SOC may operate the alerts, but the application must supply meaningful events and application context.

## 28. Test identification and authentication

Testing should include:

- valid organisational user;
- user with no application account;
- disabled enterprise user;
- disabled application account;
- wrong issuer;
- wrong audience;
- expired token;
- not-yet-valid token;
- invalid signature;
- altered claim;
- missing subject;
- duplicate or ambiguous mapping;
- insufficient authentication context;
- bypass of browser authentication through direct API calls;
- thick-client request manipulation;
- unauthenticated file download;
- deep-link access;
- callback and redirect manipulation;
- session fixation;
- session replay;
- sign-out and session invalidation;
- role change during an active session;
- key rollover;
- identity-provider outage;
- fallback access;
- privileged reauthentication;
- support impersonation; and
- authentication-event forwarding.

Testing should validate end-to-end behaviour, not merely that the identity-provider login page appears.

## 29. Reconcile application identities

The application should periodically compare its user mappings and account status with the authoritative enterprise identity source.

The reconciliation should identify:

- application users with no active enterprise identity;
- duplicate mappings;
- reused identifiers;
- mismatched subject identifiers;
- disabled enterprise identities still holding application access;
- local accounts;
- fallback accounts;
- users authenticated from an unapproved issuer;
- obsolete privileged identities;
- identities belonging to departed suppliers; and
- accounts that cannot be traced to an approved person.

The reconciliation supports both IA-02 and AC-02.

## 30. Review authentication design after material change

The application should reassess identification and authentication after:

- identity-provider migration;
- federation-protocol change;
- new thick client;
- new API;
- new privileged function;
- new user population;
- merger or directory consolidation;
- new supplier access;
- application migration;
- product upgrade;
- new offline capability;
- introduction of step-up authentication;
- change to enterprise MFA;
- security incident;
- penetration-test finding; or
- new NIST or enterprise identity requirements.

The SSP, design, registration, test evidence and operational procedures should remain aligned.

## 31. Remove obsolete authentication paths

When an interface, local account, protocol, fallback method or identity provider is retired, the application should:

- disable the route;
- remove callback registrations;
- revoke client secrets and certificates;
- remove local accounts;
- remove trust anchors;
- remove obsolete code and libraries;
- update documentation;
- update monitoring;
- remove firewall or proxy requirements where applicable;
- update the baseline and inventory; and
- verify that the old authentication path no longer works.

Obsolete paths should not remain available as an undocumented fallback.

## 32. Manage identification and authentication exceptions

Where a commercial or legacy application cannot meet the expected authentication model, record:

- the affected interface or account population;
- required control;
- actual implementation;
- identity and authentication weakness;
- business need;
- information and privilege exposure;
- risk;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, federation, isolation, upgrade or replacement plan; and
- review or expiry date.

Examples include:

- local password authentication;
- no MFA support;
- shared account;
- inability to validate token audience;
- inability to revoke sessions;
- weak session binding;
- no step-up authentication;
- reliance on network location;
- incomplete authentication logs; or
- unsupported federation library.

The exception should be recorded in the application addendum or risk process, not hidden in a product configuration note.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate identity, MFA, federation, managed EUC, VPN, secrets management and central monitoring. They exclude enterprise identity engineering, tenant-wide identity-provider configuration and major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the organisational-user population and approved authentication path** | Identify employees, contractors, administrators and support users and define the approved corporate identity provider and authentication protocol for each interface. | Summarise in the **SSP IA-02 statement** and maintain detail in the existing **security architecture**, **ConOps**, **SyOps** or **identity integration design**. | **4–8 hours** |
| **2. Use unique enterprise identities and prohibit shared or anonymous access** | Map each user to a unique corporate identifier and disable anonymous, guest, generic and shared user access unless formally excepted. | Record the rule in the **role/account model**, **security requirements**, **SSP IA-02/AC-02 sections** and **application configuration specification**. | **4–10 hours** |
| **3. Register and configure the application with the approved identity provider** | Configure the relying party or client, exact redirects, issuer, audience, keys, claims and environment separation using approved enterprise patterns. | Evidence sits in the existing **identity-provider registration**, **security design**, **CM-06 configuration**, **deployment record** and **release evidence pack**. | **8–24 hours** |
| **4. Validate authentication assertions and tokens correctly** | Verify signature, issuer, audience, expiry, nonce/state, subject, authentication context and other required protocol properties at the trusted server layer. | Capture requirements in the **technical/security design** and **SDLC backlog**. Retain positive and negative results in the normal **security and integration test report**. | **16–40 hours** |
| **5. Bind the authenticated identity to one application account** | Use a stable authoritative identifier, prevent duplicate or ambiguous mappings and fail closed when a safe mapping cannot be made. | Record the mapping in the **identity integration specification**, **data model**, **AC-02 account design** and **SSP**. Verify in the **system/security test report**. | **8–20 hours** |
| **6. Apply authentication to every interactive access path** | Require authentication for browser, thick-client, API, report, file, administrative, support, deep-link and recovery interfaces. | Describe enforcement points in the **security architecture**, **interface specifications**, **SSP** and normal **test coverage matrix**. | **12–32 hours** |
| **7. Protect thick-client authentication where applicable** | Use approved corporate identity integration, validate the server, protect tokens, prevent endpoint redirection and rely on server-side enforcement. | Record controls in the **thick-client design**, **packaging specification**, **SyOps**, **CM-06 settings** and **installation/security test report**. | **8–24 hours** |
| **8. Require the approved authentication strength for privileged or sensitive functions** | Verify the required MFA or authentication context and invoke step-up or recent reauthentication for defined high-impact actions where supported. | Define requirements in the **SSP IA-02/AC-06 sections**, **role matrix**, **security design** and **business-process specification**. Retain evidence in the **security test report**. | **8–24 hours** |
| **9. Implement secure session binding, expiry and sign-out** | Protect session tokens, prevent fixation and replay, rotate identifiers, enforce inactivity and absolute expiry and invalidate sessions on sign-out or material status change. | Capture controls in the **session-management design**, **CM-06 settings**, **SyOps**, **SSP** and **security test report**. | **12–32 hours** |
| **10. Fail closed on invalid, stale or ambiguous authentication** | Deny access for invalid issuer, audience, signature, expiry, insufficient authentication strength, disabled account or ambiguous mapping and provide non-sensitive errors. | Record failure behaviour in the **security design**, **SyOps**, **error-handling specification** and **SSP**. Verify through the **resilience and security test report**. | **8–20 hours** |
| **11. Protect application trust material** | Store client secrets, keys and certificates in approved enterprise services, restrict access, monitor expiry and test rollover and revocation. | Evidence remains in the existing **secrets/certificate records**, **security design**, **CM-06 configuration**, **release records** and **operational acceptance evidence**. | **6–16 hours initially** |
| **12. Log and monitor authentication events** | Generate events for success, failure, invalid tokens, insufficient assurance, privileged authentication, fallback use, impersonation and identity-service failure. | Define events in the **SSP AU-02/SI-04/IA-02 sections** and existing **event specification**. Verify through **SIEM onboarding** and the **security test report**. | **6–16 hours** |
| **13. Test authentication and bypass resistance end to end** | Test valid users, disabled users, wrong issuer/audience, altered and expired tokens, direct APIs, deep links, sessions, logout, rollover, outage and privileged reauthentication. | Add cases to the normal **security test plan**, **integration test plan**, **operational acceptance test** or **penetration test** and retain results in established reports. | **20–48 hours per major test cycle** |
| **14. Reconcile application identities with the enterprise source** | Identify disabled, duplicate, local, orphaned, obsolete or ambiguously mapped application identities and resolve them. | Retain results in the existing **access review**, **identity reconciliation**, **service review**, **risk record** or **AC-02 account-management evidence**. | **6–16 hours initially; 3–8 hours per review** |
| **15. Control fallback, emergency and support impersonation** | Keep fallback disabled in normal operation, require approval and attribution, limit scope and duration, and log both the operator and affected identity. | Record arrangements in the **SyOps**, **support model**, **incident-response annex**, **PAM record**, **SSP** and normal **access/change records**. | **8–20 hours** |
| **16. Document and manage authentication limitations** | Record local passwords, absent MFA, weak token validation, shared identities, poor session revocation or other product constraints with compensating controls and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP IA-02 statement**. | **4–10 hours per exception** |

### Indicative total

For a typical internal application with mature enterprise federation and standard integration patterns, initial application effort is commonly around **120–280 hours**.

A simple commercial application with proven corporate single sign-on support may require less. A legacy application, thick client, custom federation implementation, privileged administration model, offline capability or local account store may require substantially more.

The estimates should not be added mechanically where work overlaps. IA-02 work commonly shares architecture, implementation and evidence with AC-02, AC-03, AC-06, IA-05, AC-17, AU-02, SI-04, SC-07 and CA-07.

---

## Suggested document placement

To avoid creating disconnected evidence, identification and authentication information should normally be distributed across established application and SDLC artefacts:

- **SSP:** IA-02 implementation approach, organisational-user population, inherited enterprise identity services, authentication methods, stronger-authentication triggers, session approach, monitoring and exceptions.
- **ConOps or SyOps:** user sign-in, privileged sign-in, support impersonation, fallback operation, outage handling, sign-out and operational responsibilities.
- **Security architecture:** identity provider, federation flows, trust boundaries, token validation, client/server responsibilities and authentication enforcement points.
- **Identity integration specification:** issuer, audience, subject identifier, required claims, authentication context, redirects, keys, mapping and error handling.
- **Role/account model:** unique identities, account status, privileged users, local accounts and relationship to authorisation.
- **CM-06 configuration:** issuer, audience, redirects, timeout, cookie or token settings, trust material references and feature flags.
- **Secrets and certificate records:** application trust credentials, owners, expiry, rotation and revocation.
- **Thick-client design and packaging specification:** integrated authentication, token handling, server validation, approved endpoints and offline restrictions.
- **Interface and API specifications:** authentication requirement, accepted tokens, scopes, failure responses and direct-call protection.
- **SDLC backlog and technical design:** validation, mapping, session, step-up, failure and logging requirements.
- **Test plans and reports:** positive, negative, bypass, token, mapping, session, rollover, outage, fallback and privileged-authentication cases.
- **AU-02 and SI-04 evidence:** authentication events, anomaly alerts and event-flow health.
- **AC-02 access reviews and reconciliation:** active identities, account mappings, local accounts, privileged identities and disabled users.
- **Release and operational acceptance records:** confirmation that identity integration and monitoring work for the released version.
- **Risk register or application addendum:** local authentication, shared accounts, missing MFA, weak federation support and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- identity proofing and enrolment;
- authoritative workforce identity status;
- corporate directory services;
- corporate credential service provider;
- enterprise MFA;
- enterprise federation and single sign-on platform;
- authenticator issuance, binding, replacement and revocation;
- corporate password and authenticator policy;
- managed Windows sign-in;
- VPN authentication;
- enterprise device-compliance checks;
- privileged-access management platform;
- enterprise PKI and certificate policy;
- central identity threat detection;
- organisation-wide joiner–mover–leaver processes;
- corporate identity assurance decisions; and
- enterprise identity governance and exception policy.

The application team must still:

- trust only approved identity providers;
- configure and validate federation correctly;
- uniquely map identities to application accounts;
- require authentication at every application path;
- enforce the required authentication strength;
- protect sessions and trust material;
- prevent fallback and local-account bypass;
- log and test authentication;
- reconcile application identities; and
- formally manage application-specific limitations.

> **Key dividing line:** the enterprise proves and authenticates the organisational user; the application securely consumes that result, binds it to the correct application identity and refuses access whenever the authentication evidence is invalid, insufficient or absent.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, IA-02 Identification and Authentication (Organisational Users). citeturn989374search0
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, IA-02 assessment procedures. citeturn989374search3
3. National Institute of Standards and Technology, **NIST SP 800-63-4, Digital Identity Guidelines**. citeturn989374search4
4. National Institute of Standards and Technology, **NIST SP 800-207, Zero Trust Architecture**. citeturn989374search6
5. National Institute of Standards and Technology, **NIST SP 800-207A, A Zero Trust Architecture Model for Access Control in Cloud-Native Applications in Multi-Location Environments**. citeturn989374search7
