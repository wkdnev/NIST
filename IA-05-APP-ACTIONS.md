# IA-05 Authenticator Management — Application Actions

## Purpose

For an IT application, IA-05 means the application must ensure that every **application-specific authenticator, authentication secret, certificate, key, token, recovery mechanism and trust credential** is securely issued, bound, stored, used, changed, revoked, monitored and retired throughout its lifecycle.

In the stated corporate environment, the enterprise normally provides:

- workforce identity proofing and enrolment;
- corporate user accounts;
- enterprise multi-factor authentication;
- corporate password and authenticator policy;
- corporate identity-provider and federation services;
- managed Microsoft Windows EUC authenticators;
- VPN authentication;
- privileged-access management;
- public key infrastructure;
- enterprise secrets-management services;
- certificate issuance and renewal;
- device-compliance services;
- central account recovery;
- joiner–mover–leaver processes; and
- central identity monitoring.

Those capabilities are inherited.

The application remains responsible for the authenticators and trust material that exist **because of the application**, including:

- application-local passwords where unavoidable;
- service-account secrets;
- API client secrets;
- certificates used by application components;
- private keys;
- database credentials;
- integration credentials;
- signing keys;
- encryption keys under application control;
- recovery and emergency credentials;
- bootstrap and installation credentials;
- session and refresh tokens;
- thick-client trust material;
- supplier support credentials;
- one-time activation or enrolment codes;
- authenticator references and bindings;
- hard-coded or embedded credentials;
- secret-bearing configuration; and
- any fallback authenticator that could bypass enterprise identity.

NIST IA-05 requires authenticators to be managed by verifying the identity of the individual, group, role, service or device receiving the authenticator; establishing initial authenticator content; ensuring sufficient authenticator strength; establishing administrative procedures; changing default authenticators before first use; protecting authenticator content; changing or refreshing authenticators at defined intervals or on specified events; protecting authenticators against unauthorised disclosure and modification; requiring users and devices to protect authenticators; and changing authenticators when membership changes for group or role accounts.

NIST SP 800-63B-4 provides current technical guidance for authentication and authenticator management, including authenticator binding, replacement, recovery, revocation, verifier protections and authenticator assurance levels. NIST SP 800-57 provides key-management guidance for cryptographic keying material.

> **Core principle:** the enterprise manages the corporate user authenticator; the application securely manages every authenticator, secret, key, certificate and token that it creates, stores, consumes or relies upon.

---

## 1. Define the application authenticator inventory

The application should identify every authenticator and secret-bearing mechanism in scope.

This normally includes:

- enterprise federation trust;
- application registrations;
- client secrets;
- private keys;
- service-account passwords;
- database passwords;
- API keys;
- API client certificates;
- mutual-TLS certificates;
- signing certificates;
- encryption keys;
- symmetric integration keys;
- SSH keys;
- secure file-transfer credentials;
- message-broker credentials;
- directory bind credentials;
- thick-client bootstrap material;
- local application passwords;
- emergency or break-glass credentials;
- supplier support credentials;
- installation or initial administrator credentials;
- one-time enrolment codes;
- password-reset tokens;
- session tokens;
- refresh tokens;
- bearer tokens;
- device or workload certificates;
- webhook secrets;
- software-signing keys;
- package-signing certificates;
- recovery codes;
- shared technical-account credentials where unavoidable; and
- credentials embedded in scripts, configuration or deployment tooling.

The inventory should identify:

- authenticator type;
- unique identifier or reference;
- owner;
- consuming component;
- environment;
- purpose;
- privilege;
- storage location;
- issuing authority;
- creation date;
- expiry;
- rotation or renewal method;
- revocation method;
- monitoring;
- last review date; and
- retirement trigger.

The secret value itself should not be recorded in the inventory.

## 2. Distinguish enterprise and application ownership

For each authenticator type, the application should define who owns:

- identity verification;
- issuance;
- binding;
- delivery;
- activation;
- storage;
- use;
- rotation;
- renewal;
- recovery;
- revocation;
- monitoring;
- compromise response; and
- retirement.

Typical division:

| Authenticator | Typical enterprise responsibility | Typical application responsibility |
|---|---|---|
| Corporate user MFA | Identity proofing, enrolment, issuance, recovery and revocation | Correct federation configuration and enforcement of required authentication context |
| Corporate password | Enterprise directory and policy | Avoid collecting or storing it; consume enterprise authentication securely |
| Application-local password | Enterprise may define policy | Full lifecycle management within the application |
| Service-account secret | Enterprise secrets platform | Purpose, ownership, minimum privilege, use, rotation trigger and removal |
| Application certificate | Enterprise PKI or certificate platform | Correct subject, endpoint binding, deployment, trust configuration, renewal testing and revocation response |
| API client credential | Enterprise may provide vaulting | Registration, scope, ownership, expiry, use, monitoring and revocation |
| Database credential | Enterprise database and vault platforms | Application-specific account, privilege, secret reference, rotation testing and removal |
| Signing key | Enterprise key-management or signing service | Authorised use, release integration, verification, separation of duties and compromise response |
| Session token | Enterprise identity service may issue it | Secure validation, storage, expiry, revocation handling and replay protection |

## 3. Prefer enterprise authentication and avoid local authenticators

The application should use approved enterprise federation or integrated authentication wherever technically supported.

It should:

- avoid maintaining a second password store;
- avoid collecting the user’s corporate password;
- avoid passing corporate passwords through the application;
- avoid password synchronisation;
- avoid local fallback unless formally approved;
- map stable enterprise identities correctly;
- validate identity-provider assertions;
- enforce the approved authentication strength;
- remove obsolete local accounts after federation;
- monitor remaining local authenticators; and
- document product limitations.

An application that uses enterprise single sign-on may still have many non-person authenticators requiring IA-05 control.

## 4. Assign an accountable owner to every application authenticator

Every application-specific authenticator should have:

- a named human owner or accountable service owner;
- a consuming component;
- a defined business or technical purpose;
- an approved environment;
- an approved privilege level;
- a support contact;
- a renewal or rotation owner;
- a compromise-response contact;
- a review date; and
- a retirement trigger.

Avoid ownership labels such as “IT”, “the supplier” or “the application” unless the accountable service and responsible role are unambiguous.

## 5. Verify the recipient before issuing or binding an authenticator

Before an application-specific authenticator is issued or bound, verify the receiving:

- person;
- service;
- workload;
- device;
- integration;
- supplier;
- component; or
- administrative role.

The process should confirm:

- approved request;
- identity or service identifier;
- ownership;
- intended use;
- environment;
- privilege;
- consuming endpoint;
- required lifetime;
- approval;
- separation-of-duties conditions;
- delivery method; and
- whether another approved authenticator already exists.

An API key should not be issued merely because someone knows the integration name.

## 6. Use unique authenticators

Authenticators should be unique to the person, service, component, client or environment they represent.

The application should avoid:

- one password shared across several service accounts;
- one API key shared by unrelated clients;
- the same secret in development, test and production;
- a shared supplier credential;
- cloned certificates;
- a common database password across applications;
- a generic signing key used for unrelated purposes;
- reuse of a former component’s credential;
- common default administrator credentials; and
- copying production credentials into recovery or test environments.

Unique authenticators improve attribution, revocation and incident scoping.

## 7. Change default authenticators before first use

The application should identify and replace:

- vendor-default passwords;
- sample API keys;
- default certificates;
- default administrator secrets;
- installation passwords;
- bootstrap tokens;
- default database credentials;
- default keystore passwords;
- demonstration accounts;
- example signing keys;
- shared installer credentials; and
- default secrets in images or templates.

Default authenticators should be changed before the component is connected to production information or networks.

Where a default account is not required, disable or remove it rather than merely change its password.

## 8. Establish secure initial authenticator content

Where the application generates a secret, it should use an approved cryptographically secure random source and sufficient entropy.

The application should not generate secrets from:

- usernames;
- application names;
- dates;
- serial numbers;
- predictable sequences;
- hostnames;
- environment names;
- repeated templates;
- weak pseudo-random functions;
- hard-coded constants; or
- user-supplied low-entropy values.

Generated secrets should be appropriate to their type and accepted only by the intended verifier.

## 9. Protect authenticators during delivery

Application authenticators should be delivered through approved secure channels.

The application should:

- avoid ordinary email for passwords or secrets;
- avoid chat messages;
- avoid service tickets containing secret values;
- avoid including secrets in deployment instructions;
- use approved secrets-management or certificate platforms;
- separate delivery of identity and activation information where required;
- use one-time activation links or codes where appropriate;
- expire unused activation material;
- authenticate the recipient;
- prevent delivery to personal accounts;
- record issuance without recording the secret;
- prevent help-desk staff from reading reusable secrets where possible; and
- require change on first use where the authenticator type warrants it.

## 10. Store secrets only in approved secret-management services

Application secrets should normally be stored in:

- enterprise vaults;
- managed secrets services;
- approved hardware-backed key stores;
- certificate stores;
- protected operating-system credential stores;
- managed key-management services; or
- equivalent approved enterprise mechanisms.

The application should not store secrets in:

- source code;
- public or shared repositories;
- ordinary configuration files;
- spreadsheets;
- architecture documents;
- test scripts;
- wiki pages;
- service tickets;
- email;
- chat;
- container images;
- database tables in clear text;
- registry entries accessible to ordinary users;
- command-line arguments;
- logs;
- crash dumps; or
- support bundles.

Where environment variables are used through an approved platform, the application should understand and mitigate exposure through process inspection, diagnostics, dumps and inherited child processes.

## 11. Avoid hard-coded and embedded credentials

The application should detect and remove:

- passwords in source code;
- API keys in scripts;
- certificates packaged with private keys;
- secrets in thick-client binaries;
- passwords in connection strings committed to repositories;
- secrets in container layers;
- credentials in installer files;
- secrets in sample configuration;
- shared tokens in test utilities;
- hidden supplier credentials;
- default recovery passwords; and
- keys copied into documentation.

Controls should include:

- secret scanning;
- code review;
- repository history review;
- build-pipeline checks;
- package inspection;
- binary inspection where appropriate;
- credential rotation after discovery; and
- removal from all history and artefacts where practical.

Removing the text from the current branch is not enough if the secret remains valid or retrievable from history.

## 12. Limit authenticator access

Access to authenticator material should be granted only to:

- the consuming service or process;
- authorised secrets administrators;
- approved deployment automation;
- approved certificate or key-management services;
- designated emergency operators; and
- authorised support staff under controlled conditions.

The application should prevent developers, testers, ordinary administrators and suppliers from reading production secrets merely because they support the application.

“Use” permission should be separated from “read/export” permission where the enterprise platform supports it.

## 13. Separate environments

Development, test, training, pre-production, production and recovery should use separate authenticators.

The application should:

- prohibit production secrets in lower environments;
- prohibit lower-environment certificates in production;
- use separate API clients;
- use separate database accounts;
- use separate signing contexts;
- use separate service identities;
- use separate trust registrations;
- restrict cross-environment vault access;
- clearly label environment ownership;
- prevent recovery secrets from becoming standing production bypasses; and
- rotate any credential exposed to a lower-assurance environment.

## 14. Apply least privilege to authenticator-backed identities

The strength of a secret does not compensate for excessive privilege.

Each authenticator-backed identity should have:

- minimum required permissions;
- minimum data scope;
- minimum endpoint scope;
- minimum environment scope;
- restricted interactive use;
- restricted delegation;
- defined transaction limits where appropriate;
- restricted administration;
- no unnecessary schema ownership;
- no unnecessary operating-system privilege;
- no broad wildcard scopes;
- no standing privilege where just-in-time access is feasible; and
- a review date.

## 15. Manage application-local passwords carefully

Where local password authentication is unavoidable, the application should:

- justify the exception;
- uniquely identify each user;
- enforce the approved password standard;
- use approved salted password hashing;
- use an approved password-hashing function and parameters;
- prevent storage of reversible passwords;
- protect password-verifier data;
- prevent default and common passwords according to enterprise policy;
- permit password managers and paste where policy allows;
- avoid arbitrary composition rules that conflict with current enterprise standards;
- implement secure reset and recovery;
- rate-limit failed attempts;
- log authentication events;
- prevent administrator viewing of passwords;
- prevent reuse where enterprise policy requires it;
- change compromised passwords promptly;
- disable leaver and dormant accounts;
- test the implementation; and
- maintain a plan to federate, upgrade or replace.

Application-local password stores create significant ongoing application responsibility.

## 16. Protect password-verifier data

Where the application stores password verifiers, it should:

- use unique salts;
- use an approved memory-hard or otherwise approved password-hashing function;
- use current enterprise-approved work factors;
- protect any server-side secret or pepper through approved key management;
- restrict database access;
- prevent verifier export;
- monitor access;
- protect backups;
- ensure secure migration when parameters change;
- avoid using ordinary fast cryptographic hashes alone;
- avoid reversible encryption as the primary storage method; and
- plan emergency reset if verifier data is compromised.

## 17. Manage password reset and account recovery

Recovery is an alternate authentication path and must not be weaker than ordinary authentication.

The application should:

- use enterprise recovery where federation is used;
- avoid knowledge-based questions;
- verify the user through an approved method;
- use short-lived, single-use reset tokens;
- bind tokens to the correct account and purpose;
- protect tokens in storage and transit;
- avoid exposing account existence unnecessarily;
- invalidate prior reset tokens after use;
- notify the user of material recovery activity;
- log initiation and completion;
- require reauthentication after recovery where appropriate;
- revoke existing sessions when risk warrants;
- prevent support personnel from choosing or viewing the new password; and
- monitor repeated recovery attempts.

## 18. Manage one-time activation and enrolment codes

Activation and enrolment codes should be:

- unpredictable;
- single-use;
- short-lived;
- bound to a specific identity, account, service or device;
- delivered securely;
- invalidated after success;
- invalidated after excessive failed attempts;
- excluded from logs;
- protected from replay;
- unusable for unrelated functions; and
- revocable.

## 19. Manage service-account secrets

Each service account should have:

- a unique credential;
- named owner;
- consuming component;
- approved environment;
- documented purpose;
- minimum privilege;
- non-interactive status unless required;
- approved storage;
- automated retrieval where possible;
- rotation method;
- compromise procedure;
- monitoring;
- dependency record;
- expiry or review;
- and removal trigger.

The application should avoid service accounts that cannot be rotated without widespread outage.

## 20. Manage API keys and client secrets

API credentials should be:

- unique per client;
- restricted to approved endpoints;
- restricted by scope;
- restricted by environment;
- assigned to a named owner;
- issued through an approved process;
- stored in an approved secrets platform;
- never embedded in public or thick-client code;
- time-limited where supported;
- rotated;
- revocable;
- monitored;
- rate-limited;
- protected against disclosure in logs; and
- removed when the client is retired.

A secret embedded in a distributed thick client should be assumed recoverable and should not be used as the sole proof of client identity.

## 21. Manage database credentials

Application database credentials should:

- be unique to the application and environment;
- distinguish runtime, migration, reporting and administrative use;
- have minimum database privileges;
- avoid shared DBA credentials;
- be stored in approved secrets services;
- be retrieved securely;
- be protected from connection-string disclosure;
- support rotation without source-code change;
- prevent ordinary developers from reading production values;
- be monitored;
- be revoked when components are retired; and
- be tested during rotation.

## 22. Manage certificates

For each application certificate, the application should define:

- purpose;
- subject and subject alternative names;
- consuming component;
- environment;
- issuing authority;
- trust chain;
- private-key location;
- key usage;
- extended key usage;
- owner;
- issue date;
- expiry;
- renewal method;
- deployment method;
- rollover method;
- revocation method;
- monitoring;
- and dependency impact.

The application should reject:

- expired certificates;
- untrusted issuers;
- incorrect names;
- weak or unapproved algorithms;
- inappropriate key usage;
- revoked certificates where revocation information is required and available; and
- self-signed certificates unless specifically approved.

## 23. Protect private keys

Private keys should:

- be generated in approved cryptographic modules or services where possible;
- remain non-exportable where operationally feasible;
- be access-restricted;
- be separated by environment and purpose;
- be protected at rest;
- not be copied into source code or packages;
- not be sent through email or tickets;
- not be included in support bundles;
- be backed up only where required and securely protected;
- have controlled recovery;
- have defined rotation and revocation;
- and be destroyed securely at retirement.

## 24. Manage trust anchors and federation keys

The application should control:

- identity-provider signing certificates;
- federation metadata;
- trust stores;
- certificate-authority trust;
- API trust anchors;
- mutual-TLS trust;
- package-signing trust;
- software-update trust; and
- supplier trust material.

Controls should include:

- approved source;
- integrity validation;
- version control;
- restricted modification;
- overlap during planned rollover;
- removal of obsolete trust;
- monitoring for expiry;
- emergency revocation;
- test and production separation;
- and testing before activation.

The application should never disable signature or certificate validation as an operational workaround.

## 25. Manage signing keys

Signing keys used for software, packages, documents, assertions or transactions should have:

- defined signing purpose;
- authorised signing process;
- controlled key custody;
- separation of duties;
- restricted use;
- approved algorithms;
- non-exportable storage where practical;
- audit logging;
- release or transaction traceability;
- renewal;
- revocation;
- compromise response;
- and verification by consuming components.

A developer should not be able to sign arbitrary production artefacts outside the approved release process.

## 26. Manage encryption keys under application control

Where the application controls encryption keys, define:

- information protected;
- algorithm and key type;
- generating authority;
- key owner;
- storage;
- authorised consumers;
- activation date;
- cryptoperiod;
- rotation;
- backup or escrow requirements;
- recovery;
- revocation;
- destruction;
- versioning;
- data re-encryption approach;
- and incident response.

The application should use enterprise key-management services rather than invent its own key store.

## 27. Manage session tokens

Session identifiers and tokens should be:

- generated or validated using approved mechanisms;
- unpredictable;
- bound to the authenticated identity;
- bound to the correct audience and application;
- protected in transit;
- stored securely;
- inaccessible to scripts where appropriate;
- scoped;
- time-limited;
- rotated after authentication and privilege change;
- invalidated on sign-out;
- revocable where risk requires;
- protected against replay;
- excluded from URLs and logs;
- and invalidated when compromise is suspected.

Session tokens are authenticators and should be treated as secrets.

## 28. Manage refresh tokens

Refresh tokens require stronger protection than short-lived access tokens.

The application should:

- use them only where necessary;
- store them in approved secure locations;
- restrict them to the intended client;
- bind them to the appropriate identity and scope;
- rotate them where supported;
- detect reuse where supported;
- revoke them on account disablement, client compromise or sign-out where appropriate;
- apply maximum lifetime;
- prevent disclosure to browser scripts or logs;
- avoid issuing them to untrusted distributed clients unless the design supports it;
- and test theft and replay scenarios.

## 29. Manage bearer tokens carefully

Because possession of a bearer token may be sufficient to use it, the application should:

- minimise lifetime;
- minimise scope;
- validate issuer, audience, signature and time;
- protect transmission;
- prevent logging;
- prevent URL placement;
- prevent unnecessary browser storage;
- avoid sending to multiple services;
- use sender-constrained mechanisms where risk and platform capability justify it;
- monitor unusual use;
- and revoke or invalidate on compromise.

## 30. Manage shared and group authenticators

Shared user authenticators should normally be prohibited.

Where an unavoidable shared technical account exists, the application should:

- document why named identities cannot be used;
- identify every authorised operator;
- use enterprise PAM where available;
- ensure the operator is individually authenticated first;
- restrict scope and privilege;
- restrict duration;
- log checkout and use;
- rotate after membership change or compromise;
- review membership frequently;
- prohibit uncontrolled copying;
- and maintain a replacement plan.

IA-05 explicitly requires group or role account authenticators to change when membership changes.

## 31. Manage supplier authenticators

Supplier credentials should be:

- assigned to named supplier personnel or unique supplier services;
- sponsored internally;
- approved for a specific purpose;
- limited in privilege and component scope;
- time-limited;
- protected through approved supplier-access or PAM services;
- prohibited from ordinary sharing;
- rotated when supplier personnel change where shared technical credentials remain;
- revoked when the support case or contract ends;
- monitored;
- and reviewed after use.

Permanent vendor-default or generic support credentials should not remain enabled.

## 32. Manage emergency and break-glass authenticators

Emergency credentials should:

- exist only where justified;
- be unique;
- have a named accountable owner;
- be stored in an approved protected facility;
- be inaccessible during ordinary operation;
- be checked periodically without exposing the secret;
- have defined activation conditions;
- require approval where feasible;
- be time-limited;
- be logged and alerted on use;
- be reviewed after use;
- be rotated immediately after use or suspected exposure;
- and be disabled or returned to secure custody afterwards.

Emergency authenticators should not become routine administrator credentials.

## 33. Manage bootstrap and installation authenticators

Temporary credentials used during installation, onboarding, initial configuration or migration should:

- be unique;
- be time-limited;
- be delivered securely;
- be restricted to the installation function;
- be changed or revoked before production acceptance;
- be removed from scripts and runbooks;
- be excluded from images and templates;
- be logged;
- and be checked during operational acceptance.

## 34. Rotate and renew authenticators

The application should define event-based and, where required, time-based rotation or renewal.

Triggers may include:

- suspected or confirmed compromise;
- unauthorised disclosure;
- change of owner;
- change of group or role membership;
- supplier personnel change;
- administrator departure;
- application transfer;
- certificate expiry;
- algorithm deprecation;
- privilege change;
- component replacement;
- environment migration;
- backup exposure;
- repository leak;
- support-bundle exposure;
- incident;
- failed integrity check;
- known vulnerable secret-generation process;
- and enterprise policy.

Rotation should be automated where practical and tested before production use.

## 35. Avoid unnecessary periodic password changes

For user passwords, the application should follow current enterprise and NIST-aligned policy rather than forcing arbitrary periodic changes that are not required by policy.

The application should prioritise:

- long passwords or passphrases;
- blocklist checks;
- secure storage;
- rate limiting;
- MFA;
- password-manager support;
- compromise-driven change;
- and secure recovery.

Where enterprise policy mandates a specific rule, the application should implement or inherit it consistently.

## 36. Design for rotation without outage

Applications should avoid architectures where credential rotation requires:

- source-code change;
- prolonged outage;
- coordinated manual editing across many servers;
- distribution of the new secret to many people;
- simultaneous uncontrolled cutover;
- or rollback to an exposed secret.

Where supported, use:

- versioned secrets;
- dual credentials during controlled overlap;
- automated retrieval;
- certificate rollover;
- staged deployment;
- health verification;
- and automatic retirement of the old credential.

## 37. Monitor authenticator expiry

The application should monitor expiry for:

- certificates;
- API credentials;
- client secrets;
- signing certificates;
- encryption keys;
- SSH keys;
- supplier access;
- recovery credentials;
- temporary tokens;
- and service-account credentials where expiry applies.

Alerts should occur early enough to:

- obtain approval;
- generate or issue replacement material;
- test rollover;
- deploy;
- verify;
- and recover from failure.

Expiry monitoring should not rely on one individual’s calendar reminder.

## 38. Revoke authenticators promptly

The application should support prompt revocation when:

- an account is disabled;
- a component is retired;
- an integration ends;
- a supplier contract ends;
- a secret is exposed;
- a certificate is compromised;
- a device or workload is lost;
- a privileged role is removed;
- an API client is decommissioned;
- a user signs out where token revocation is required;
- an emergency account is used;
- or an incident requires containment.

Revocation should address active sessions, refresh tokens, cached credentials and alternate copies where applicable.

## 39. Verify revocation effectiveness

The application should test that revoked authenticators:

- cannot authenticate;
- cannot refresh;
- cannot call alternate endpoints;
- cannot use cached sessions beyond the approved risk window;
- cannot use another environment;
- cannot use old client versions;
- cannot access recovery systems;
- and cannot be restored through an old configuration or backup.

A revoked vault entry is not enough if the consuming application continues using a cached secret indefinitely.

## 40. Destroy retired authenticator material securely

When authenticators are retired, the application should:

- revoke them;
- remove them from active configuration;
- remove them from vault paths no longer required;
- remove them from packages and images;
- remove them from scripts;
- remove obsolete trust anchors;
- prevent use from recovery media;
- update inventory and baseline;
- preserve only non-secret audit metadata;
- and use approved secure-destruction methods for exported or backed-up material.

## 41. Protect authenticator metadata

Even where secret values are protected, metadata can be sensitive.

The application should control access to:

- certificate subjects;
- secret names;
- vault paths;
- key identifiers;
- token audiences;
- API client identifiers;
- expiry dates;
- service-account names;
- trust relationships;
- emergency credential locations;
- and dependency mappings.

Metadata should be available to authorised operators and monitoring services without exposing more than necessary.

## 42. Prevent authenticator disclosure in logs and errors

The application should mask or exclude:

- passwords;
- API keys;
- bearer tokens;
- refresh tokens;
- session identifiers;
- private keys;
- certificate private material;
- connection strings;
- signed URLs;
- recovery codes;
- activation links;
- reset tokens;
- secret-bearing headers;
- and full authentication assertions.

Logging controls should be tested against:

- application logs;
- proxy logs;
- debug logs;
- audit logs;
- traces;
- crash dumps;
- support bundles;
- analytics;
- and error responses.

## 43. Prevent authenticator disclosure through client applications

Thick clients and browser applications should not expose reusable secrets through:

- local files;
- registry;
- browser storage;
- source maps;
- embedded code;
- configuration;
- memory dumps;
- command-line arguments;
- clipboard;
- insecure inter-process communication;
- update packages;
- installer logs;
- or diagnostics.

Distributed applications should assume that embedded static secrets can be recovered.

## 44. Prevent authenticator disclosure through support and diagnostics

Support processes should prohibit:

- asking users for passwords;
- copying secrets into tickets;
- emailing configuration with credentials;
- uploading unredacted support bundles;
- sharing private keys with suppliers;
- taking screenshots containing tokens;
- using personal messaging for credentials;
- and retaining emergency credentials in support notes.

Diagnostic bundles should be automatically redacted where practical and manually reviewed before external transfer.

## 45. Protect against forged, copied and replayed authenticators

The application should use proportionate protections such as:

- digital signatures;
- nonce and state;
- token audience validation;
- expiry;
- one-time use;
- replay caches;
- certificate validation;
- mutual authentication;
- sender-constrained tokens;
- secure challenge-response;
- token rotation;
- device or workload binding;
- unique identifiers;
- and anomaly monitoring.

NIST IA-05 enhancements address protection against forged or copied authenticators.

## 46. Restrict authenticator-management functions

Functions that issue, view, rotate, replace, revoke, export or recover authenticators are privileged.

The application should:

- limit them to approved roles and services;
- require named identities;
- use MFA or privileged authentication;
- prevent self-approval where appropriate;
- prohibit ordinary support users from exporting secrets;
- separate signing authority from development;
- restrict vault administration;
- restrict trust-store changes;
- restrict emergency access;
- log all material actions;
- and test direct API and administrative bypass attempts.

## 47. Separate duties for high-risk authenticator management

Where proportionate, separate:

- requester from approver;
- secret administrator from application operator;
- signing-key custodian from developer;
- key-generation authority from key user;
- certificate requester from certificate approver;
- API client owner from scope approver;
- emergency credential user from post-use reviewer;
- vault administrator from audit reviewer;
- and database credential administrator from business-data operator.

## 48. Log authenticator lifecycle events

The application should generate or retain useful events for:

- authenticator issuance;
- binding;
- activation;
- first use;
- failed use;
- rotation;
- renewal;
- replacement;
- revocation;
- expiry;
- recovery;
- emergency use;
- supplier use;
- secret retrieval where available;
- key signing;
- certificate trust change;
- reset initiation and completion;
- reset failure;
- local password change;
- export attempt;
- unauthorised access;
- and deletion or retirement.

Events should include:

- acting identity or service;
- affected authenticator reference;
- affected component or account;
- environment;
- time;
- outcome;
- reason or trigger;
- approval or change reference;
- privileged, emergency or supplier status;
- and source component.

Secret values should never be logged.

## 49. Monitor authenticator anomalies

The application should support detection of:

- repeated secret retrieval;
- use from an unexpected component;
- API key use outside expected patterns;
- service account used interactively;
- expired certificate use;
- failed certificate validation;
- repeated reset attempts;
- use after revocation;
- old secret use after rotation;
- emergency credential use;
- supplier credential use outside approved windows;
- unusual signing activity;
- access to production secrets from non-production;
- secret export attempts;
- trust-store changes;
- hard-coded secret findings;
- and dormant authenticator use.

## 50. Respond to authenticator compromise

The application should define a compromise response covering:

- identification of the affected authenticator;
- immediate revocation or disablement;
- session and token invalidation;
- replacement;
- dependency analysis;
- affected component and environment;
- search for copies;
- repository and history review;
- support-bundle review;
- log review;
- assessment of unauthorised use;
- data and transaction impact;
- supplier notification where applicable;
- incident-response coordination;
- emergency change;
- reissue;
- verification;
- and lessons learned.

Rotating the secret is necessary but may not be sufficient if the compromised authenticator was already used.

## 51. Test authenticator lifecycle controls

Testing should include, where relevant:

- issuance to the correct identity or service;
- denial of unauthorised issuance;
- default authenticator removal;
- secure storage;
- secret retrieval;
- local password storage;
- reset and recovery;
- one-time code expiry;
- API key scope;
- service account interactive-use restriction;
- certificate validation;
- key rollover;
- secret rotation;
- dual-secret cutover;
- revocation;
- cached-secret behaviour;
- session and refresh-token revocation;
- supplier expiry;
- emergency credential use;
- logging;
- monitoring;
- and removal during decommissioning.

## 52. Test rollover before production

Certificate, key and secret rollover should be tested for:

- overlap;
- consumer compatibility;
- cache refresh;
- deployment order;
- rollback;
- expiry behaviour;
- trust-store updates;
- standby and recovery components;
- thick clients;
- scheduled jobs;
- integration clients;
- monitoring;
- and removal of the old material.

A theoretically automated renewal process is not sufficient until successful end-to-end rollover has been demonstrated.

## 53. Review authenticators periodically

At a defined frequency, review:

- ownership;
- continued need;
- privilege;
- environment;
- storage location;
- last use;
- expiry;
- rotation status;
- support status;
- supplier involvement;
- interactive-use status;
- duplicates;
- shared credentials;
- hard-coded secrets;
- obsolete certificates;
- unused API clients;
- emergency credentials;
- local accounts;
- unowned vault entries;
- and authenticators linked to retired components.

## 54. Reconcile authenticator inventory with component inventory

The application should compare the authenticator inventory with:

- CM-08 component inventory;
- architecture;
- APIs and integrations;
- service-account register;
- certificate platform;
- secrets platform;
- database accounts;
- deployment manifests;
- build pipelines;
- supplier records;
- and recovery plans.

The reconciliation should identify:

- secrets with no consuming component;
- components with undocumented secrets;
- certificates with no owner;
- retired components with active credentials;
- duplicate credentials;
- shared credentials;
- test credentials in production;
- production credentials in lower environments;
- and stale trust relationships.

## 55. Update authenticator records through change and release

Authenticator lifecycle updates should be part of:

- new component introduction;
- new integration;
- release;
- migration;
- certificate replacement;
- service-account creation;
- privilege change;
- supplier onboarding;
- supplier offboarding;
- emergency change;
- key rotation;
- product upgrade;
- identity-provider migration;
- recovery change;
- and decommissioning.

A change should not be considered complete until relevant authenticator records and dependencies are updated.

## 56. Manage authenticator limitations and exceptions

Where a legacy or commercial product cannot meet the expected model, record:

- affected authenticator;
- expected control;
- actual implementation;
- users or components affected;
- privilege and information exposure;
- reason;
- risk;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, federation, upgrade, isolation or replacement plan;
- and review or expiry date.

Examples include:

- local password store;
- reversible password storage;
- hard-coded service credential;
- no secret rotation;
- shared supplier credential;
- inability to revoke sessions;
- certificate renewal requiring outage;
- private key that must be exportable;
- secret in a configuration file;
- no audit of secret retrieval;
- weak reset mechanism;
- or one credential shared across environments.

The exception should be recorded in the application addendum or risk process, not buried in an administrator’s notes.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate identity, MFA, PKI, PAM, secrets management, managed Windows EUC and central monitoring. They exclude enterprise platform engineering, large-scale secret migration and major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify all application-specific authenticators** | Inventory local passwords, service and API secrets, database credentials, certificates, keys, tokens, supplier and emergency credentials and trust material. | Summarise in the **SSP IA-05 statement** and maintain detail in the existing **service-account register**, **certificate register**, **secrets platform**, **CM-08 inventory** or **security architecture**. | **8–16 hours** |
| **2. Define ownership and lifecycle responsibility** | Assign an accountable owner, purpose, component, environment, privilege, rotation, revocation and retirement trigger to every authenticator. | Record in the **RACI**, **support model**, **service-account register**, **certificate record**, **interface document**, **SyOps** and **SSP**. | **6–14 hours** |
| **3. Remove default, shared and hard-coded authenticators** | Change or disable defaults, prohibit shared user credentials, scan source and artefacts for secrets and rotate anything exposed. | Evidence remains in the normal **code repository**, **secret-scan results**, **CM-06 configuration**, **security test report**, **change record** and **risk register**. | **12–32 hours initially** |
| **4. Store secrets in approved enterprise services** | Move service, API, database and integration secrets to approved vault, certificate or key-management services and restrict read/export access. | Use the existing **secrets platform records**, **certificate platform**, **deployment design**, **CM-06 configuration**, **PAM evidence** and **SSP**. | **12–40 hours initially** |
| **5. Separate authenticators by identity, purpose and environment** | Use unique credentials per service, client and environment and prohibit production credentials in lower environments. | Record in the **service-account register**, **interface specifications**, **deployment manifests**, **secrets platform** and **CM-08 inventory**. | **8–20 hours** |
| **6. Apply least privilege to authenticator-backed identities** | Restrict API scopes, database roles, service permissions, signing authority and interactive use to the minimum required. | Record in the **role/access matrix**, **interface design**, **database design**, **AC-06 evidence**, **service-account register** and **security test report**. | **8–24 hours** |
| **7. Manage application-local passwords and recovery where unavoidable** | Use approved salted password hashing, secure reset tokens, rate limiting, compromise-driven change, secure recovery and stronger review. | Capture controls in the **authentication design**, **SSP IA-05/IA-02 sections**, **CM-06 settings**, **SyOps** and **security test report**. | **16–48 hours** |
| **8. Manage certificates and trust material** | Define subject, usage, owner, trust, expiry, renewal, rollover, revocation and monitoring and reject invalid certificates. | Evidence sits in the **certificate platform**, **PKI request**, **security design**, **CM-06 configuration**, **renewal test** and **release record**. | **8–24 hours** |
| **9. Manage service, API and database credential rotation** | Use approved storage, automate retrieval where practical, rotate on defined events, test cutover and revoke old values. | Record in the **secrets platform**, **service-account register**, **interface documents**, **database design**, **SyOps**, **change records** and **test evidence**. | **12–32 hours initially** |
| **10. Protect session, refresh and bearer tokens** | Apply secure storage, scope, expiry, rotation, revocation, replay protection and safe logout and prevent token exposure in logs and URLs. | Capture requirements in the **session-management design**, **identity integration specification**, **CM-06 configuration**, **SSP** and **security test report**. | **12–32 hours** |
| **11. Control supplier, emergency and bootstrap credentials** | Use named or attributable access, secure custody, minimum scope, time limits, post-use rotation and removal after use or installation. | Use the existing **supplier record**, **PAM record**, **incident-response annex**, **installation checklist**, **SyOps** and **SSP**. | **8–20 hours** |
| **12. Monitor expiry and compromise events** | Alert before certificate and secret expiry and define rapid revocation, replacement, dependency review and incident response for suspected compromise. | Record arrangements in the **monitoring design**, **certificate/secrets platform**, **SyOps**, **IR plan**, **SI-04 evidence** and **SSP**. | **6–16 hours** |
| **13. Log authenticator lifecycle activity** | Record issuance, binding, rotation, renewal, reset, revocation, emergency use, supplier use, trust changes and unauthorised attempts without logging secret values. | Define events in the **SSP AU-02/SI-04/IA-05 sections** and existing **event specification**. Verify through **SIEM onboarding** and the **security test report**. | **6–16 hours** |
| **14. Test issuance, rotation, rollover and revocation** | Test default removal, secure retrieval, password recovery, API scope, certificate rollover, secret rotation, token revocation, expiry and cached use. | Add cases to the normal **security test plan**, **integration test**, **operational acceptance test**, **release test** and **penetration test**. | **20–48 hours per major test cycle** |
| **15. Review and reconcile authenticators periodically** | Review owners, need, privilege, expiry, use, shared values, environment separation and links to current components and suppliers. | Retain outcomes in established **access reviews**, **service reviews**, **certificate reviews**, **PAM reviews**, **CM-08 reconciliation** or **CA-07 reports**. | **8–20 hours per review** |
| **16. Document and manage authenticator limitations** | Record local password stores, non-rotatable secrets, shared supplier credentials, exportable keys, weak revocation or other product constraints with compensating controls. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP IA-05 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application with enterprise single sign-on and a manageable number of service identities, integrations and certificates, initial application effort is commonly around **130–300 hours**.

Ongoing application effort is commonly around **6–20 hours per month**, plus planned rotations, certificate renewals, access reviews, incidents and material releases.

A simple commercial application with no local accounts and few non-person credentials may require less. A legacy, integration-heavy, thick-client or supplier-supported application with local passwords, embedded secrets, shared credentials or manual certificate management may require substantially more.

The estimates should not be added mechanically where work overlaps. IA-05 commonly shares implementation and evidence with:

- IA-02 identification and authentication;
- AC-02 account management;
- AC-06 least privilege;
- AC-17 remote access;
- CM-05 access restrictions for change;
- CM-06 configuration settings;
- CM-08 component inventory;
- SC-12 cryptographic key establishment and management;
- SC-13 cryptographic protection;
- AU-02 event logging;
- SI-04 system monitoring; and
- IR controls.

---

## Suggested document placement

To avoid creating disconnected evidence, authenticator-management information should normally be distributed across established application and SDLC artefacts:

- **SSP:** IA-05 implementation approach, inherited corporate authenticator services, application-specific authenticator types, lifecycle, monitoring and exceptions.
- **ConOps or SyOps:** operational issuance, rotation, renewal, revocation, recovery, supplier access, emergency use and compromise response.
- **Security architecture:** identity provider, trust anchors, secrets services, certificate flows, service identities, token flows and key dependencies.
- **Identity integration specification:** application registration, issuer, audience, authentication context, signing trust and token lifecycle.
- **Service-account register:** purpose, owner, environment, privilege, authenticator reference, review and retirement.
- **Certificate and key records:** subject, usage, owner, expiry, renewal, rollover, revocation and consuming component.
- **Secrets platform:** authoritative secret value and controlled access; reference it rather than copying secret values into documents.
- **Role/access matrix:** authenticator administrators, secret users, signing authority, recovery roles and separation of duties.
- **Interface control documents:** API clients, credentials, certificates, scopes, token behaviour and revocation.
- **Database design:** runtime, migration and reporting identities, privileges and credential references.
- **Thick-client design and packaging specification:** token storage, certificate trust, no embedded reusable secrets and client-version handling.
- **CM-06 configuration:** secret references, certificate settings, trust stores, expiry thresholds and token settings.
- **CM-08 inventory:** components linked to service identities, certificates, keys and integrations.
- **Source and artefact repositories:** secret scanning, signed artefacts and absence of embedded credentials.
- **Build and deployment pipelines:** controlled secret retrieval, signing, environment separation and rotation support.
- **AU-02 and SI-04 evidence:** lifecycle events, expiry, emergency use, anomalous retrieval and compromise indicators.
- **Test plans and reports:** password storage, reset, token handling, certificate validation, rollover, rotation and revocation.
- **Incident records:** compromise, revocation, replacement, impact assessment and lessons learned.
- **Change and release records:** new credentials, rotation, trust changes, certificate rollover and retirement.
- **Access and service reviews:** continuing need, ownership, privilege, expiry and environment separation.
- **Risk register or application addendum:** local authenticators, shared credentials, non-rotatable secrets, weak revocation and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- workforce identity proofing;
- corporate user enrolment;
- enterprise MFA issuance and recovery;
- corporate password policy;
- corporate identity-provider and federation platform;
- managed Windows EUC authentication;
- VPN authentication;
- enterprise privileged-access management platform;
- enterprise PKI and certificate policy;
- enterprise secrets-management platform;
- enterprise key-management platform;
- organisation-wide cryptographic standards;
- central joiner–mover–leaver processes;
- enterprise account recovery;
- central identity monitoring;
- corporate supplier-access platform;
- organisation-wide authenticator policy; and
- enterprise risk and exception governance.

The application team must still:

- inventory application-specific authenticators;
- assign owners and lifecycle responsibility;
- remove defaults and embedded secrets;
- use approved vault, certificate and key services correctly;
- restrict authenticator-backed privileges;
- manage service, API, database and supplier credentials;
- protect tokens;
- test rotation, rollover and revocation;
- monitor expiry and compromise;
- reconcile authenticators with current components; and
- formally manage application-specific limitations.

> **Key dividing line:** the enterprise issues and manages the corporate user’s authenticator and shared credential platforms; the application manages every application-specific secret, key, certificate, token and trust relationship placed on those platforms or consumed by the application.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, IA-05 Authenticator Management.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, IA-05 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-63-4, Digital Identity Guidelines**.
4. National Institute of Standards and Technology, **NIST SP 800-63B-4, Digital Identity Guidelines: Authentication and Authenticator Management**.
5. National Institute of Standards and Technology, **NIST SP 800-57 Part 1 Rev. 5, Recommendation for Key Management: Part 1 — General**.
6. National Institute of Standards and Technology, **NIST SP 800-57 Part 2 Rev. 1, Recommendation for Key Management: Part 2 — Best Practices for Key Management Organizations**.
7. National Institute of Standards and Technology, **NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems**.
