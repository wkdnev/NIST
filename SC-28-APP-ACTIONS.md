# SC-28 Protection of Information at Rest — Application Actions

## Purpose

For an IT application, SC-28 means the application must protect the **confidentiality and integrity of organisational information while it is stored**, using safeguards proportionate to the information, the application architecture and the credible threats.

“Information at rest” includes more than the main production database. It can exist in:

- database tables and files;
- application file stores;
- document repositories;
- search indexes;
- message queues;
- object stores;
- thick-client caches;
- browser storage;
- temporary files;
- exports and reports;
- application logs;
- audit records;
- configuration;
- backups and recovery media;
- snapshots and replicas;
- test data;
- support bundles;
- crash dumps;
- staging areas;
- archive locations;
- build artefacts;
- removable media;
- and decommissioned storage.

The enterprise may provide:

- encrypted corporate Windows EUC devices;
- encrypted server and storage platforms;
- database encryption services;
- enterprise key-management and secrets-management platforms;
- backup encryption;
- storage access controls;
- removable-media controls;
- data-classification and handling policy;
- central monitoring;
- secure disposal services;
- infrastructure administration;
- and organisation-wide cryptographic standards.

Those capabilities are inherited.

The application remains responsible for:

- identifying every place its information is stored;
- determining which information requires confidentiality and integrity protection;
- using enterprise storage and cryptographic services correctly;
- preventing unnecessary copies;
- protecting application-specific caches, files, indexes, exports, logs and temporary data;
- controlling access to stored information;
- configuring encryption correctly;
- associating keys with the correct data and component;
- handling backup, recovery, test and supplier copies;
- proving that protection remains effective after change and recovery;
- and documenting limitations.

NIST SC-28 requires protection of the confidentiality and integrity of specified information at rest. Its enhancement SC-28(1) addresses cryptographic protection, and SC-28(2) addresses protection of information at rest on removable media. NIST SP 800-111 explains storage-encryption concepts for end-user devices, while NIST SP 800-57 provides key-management guidance. Encryption is important, but SC-28 compliance also depends on access control, integrity, copy control, retention, backup, recovery and secure disposal.

> **Core principle:** the enterprise secures shared storage platforms; the application ensures that every application-owned copy of information is stored only where authorised and is protected throughout its complete lifecycle.

---

## 1. Define the information-at-rest boundary

The application should identify all locations where its information may persist.

This normally includes:

- production databases;
- database transaction and temporary files;
- application file shares;
- document stores;
- object stores;
- search indexes;
- caches;
- queue persistence;
- batch staging areas;
- upload directories;
- quarantine;
- report stores;
- export directories;
- local thick-client storage;
- browser cache and storage;
- temporary files;
- operating-system paging or dump exposure relevant to the application;
- application logs;
- audit history;
- configuration repositories;
- secrets references;
- backup repositories;
- snapshots;
- replicas;
- disaster-recovery copies;
- test and training environments;
- supplier diagnostic copies;
- migration staging;
- archived records;
- deleted-but-recoverable data;
- software artefacts containing data;
- and decommissioned media.

The scope should align with:

- architecture;
- data-flow diagrams;
- CM-08 component inventory;
- CM-02 baseline;
- backup design;
- interface inventory;
- records-retention requirements;
- and the application data model.

## 2. Classify stored information

The application should identify the sensitivity and integrity requirements of stored information.

Relevant categories may include:

- ordinary business information;
- restricted engineering information;
- security configuration;
- credentials and authenticator material;
- personal information;
- audit records;
- incident evidence;
- vulnerability findings;
- source code;
- signing material;
- privileged access records;
- export packages;
- supplier information;
- operational logs;
- system configuration;
- recovery information;
- and cryptographic metadata.

For each category, determine:

- confidentiality requirement;
- integrity requirement;
- availability and recovery requirement;
- retention;
- authorised users and services;
- approved storage locations;
- encryption requirement;
- integrity-verification requirement;
- export restrictions;
- and disposal method.

## 3. Maintain a data-at-rest register or storage map

The application should maintain a coherent view of:

- information type;
- authoritative store;
- secondary copies;
- environment;
- component;
- owner;
- access roles;
- encryption method;
- key reference;
- integrity mechanism;
- retention;
- backup;
- recovery;
- export path;
- supplier access;
- monitoring;
- and disposal.

This may be embedded in the existing data-flow diagrams, data inventory, architecture and retention schedule rather than maintained as a separate spreadsheet.

## 4. Minimise stored information

The application should avoid storing information that is not required.

It should consider:

- whether the field is necessary;
- whether the value can be derived;
- whether a token or reference can replace the full value;
- whether duplicate copies are needed;
- whether a cache is justified;
- whether logs need the content;
- whether exports need every field;
- whether test data needs production values;
- whether attachments need indefinite retention;
- whether temporary data can be deleted immediately;
- and whether old versions remain necessary.

Data that is not stored cannot be stolen, altered or mishandled.

## 5. Use approved storage locations only

Application information should be stored only in approved:

- enterprise database platforms;
- managed file services;
- approved object stores;
- corporate document repositories;
- managed application storage;
- approved backup services;
- approved log platforms;
- managed EUC locations where explicitly permitted;
- and authorised archival repositories.

The application should prohibit or disable storage in:

- personal drives;
- consumer cloud storage;
- unmanaged network shares;
- supplier devices;
- arbitrary local directories;
- public repositories;
- email mailboxes used as record stores;
- chat systems;
- temporary developer locations;
- and unsupported product storage.

## 6. Use enterprise encryption services correctly

Where the enterprise storage platform provides encryption, the application should confirm:

- encryption is enabled;
- the correct storage class or database service is used;
- the relevant volumes, files or columns are covered;
- snapshots and replicas are covered;
- backups are covered;
- recovery copies are covered;
- keys are enterprise-managed or appropriately application-bound;
- encryption is not disabled by application configuration;
- and operational procedures do not create unencrypted copies.

“Hosted on an encrypted platform” should be supported by configuration and service evidence, not assumed.

## 7. Determine when application-layer encryption is needed

Platform encryption may be sufficient for many ordinary internal applications.

Application-layer or field-level encryption may be required where:

- privileged platform administrators should not see the information;
- several data populations share one database but require stronger separation;
- particularly sensitive fields require separate key control;
- exports leave the protected platform;
- backups are handled outside the primary platform;
- supplier access creates additional risk;
- information is cached on clients;
- application-specific integrity is required;
- or the information owner mandates it.

The application should avoid unnecessary custom cryptography. Use approved enterprise cryptographic services and libraries.

## 8. Protect confidentiality at rest

Confidentiality controls may include:

- platform encryption;
- database encryption;
- file or object encryption;
- field-level encryption;
- encrypted thick-client cache;
- encrypted export packages;
- restricted storage permissions;
- role-based access;
- row or project-level access;
- secret separation;
- controlled privileged access;
- secure backup;
- and minimised duplication.

Encryption should complement, not replace, access control.

## 9. Protect integrity at rest

Integrity safeguards may include:

- database constraints;
- transaction controls;
- immutable or append-only audit records;
- digital signatures;
- message authentication codes;
- checksums used with appropriate trust controls;
- file-integrity monitoring;
- signed artefacts;
- version control;
- write restrictions;
- controlled change;
- reconciliation;
- approval workflows;
- tamper-evident history;
- and verified recovery.

An ordinary unkeyed checksum can detect accidental change but may not protect against a capable attacker who can replace both the data and checksum.

## 10. Protect authoritative databases

For application databases, the application should:

- identify authoritative schemas and tables;
- use approved database platforms;
- restrict access by role and service identity;
- separate runtime, migration, reporting and administration;
- avoid shared credentials;
- prevent ordinary users from direct database access;
- encrypt storage where required;
- protect database backups;
- protect transaction logs;
- control exports;
- protect temporary database files;
- monitor privileged access;
- audit material changes;
- validate restored data;
- and document inherited platform controls.

The enterprise database team may own platform hardening and storage encryption. The application owns its schemas, roles, data use and direct-access model.

## 11. Protect application file stores

The application should:

- use approved managed file or object storage;
- restrict read, write and delete permissions;
- segregate environments;
- prevent directory traversal;
- generate server-side identifiers;
- validate content;
- prevent executable use;
- protect metadata;
- encrypt where required;
- monitor access;
- retain version or history where required;
- protect against unauthorised overwrite;
- and securely delete expired content.

## 12. Protect attachments and uploaded files

Attachments should be protected through:

- access controls inherited from the parent record;
- server-side storage;
- non-guessable identifiers;
- malware scanning;
- file-type restrictions;
- encryption;
- secure preview;
- no direct public links;
- controlled download;
- retention;
- quarantine;
- integrity verification;
- and deletion when the parent record or retention rule requires it.

A file should not become broadly accessible merely because its URL is known.

## 13. Protect search indexes

Search indexes may contain complete or partial copies of sensitive information.

The application should:

- classify indexed content;
- restrict index access;
- encrypt index storage where required;
- enforce record and project scope at query time;
- prevent cross-project results;
- control index administration;
- protect snapshots;
- remove deleted or reclassified content promptly;
- monitor bulk queries;
- prevent index exports;
- and reconcile the index with the authoritative store.

## 14. Protect message queues and persistent messaging

Where messages persist, the application should:

- minimise message content;
- restrict queue and topic access;
- use approved encryption;
- protect dead-letter queues;
- apply retention and expiry;
- avoid secrets in messages;
- separate environments;
- validate consumers;
- prevent arbitrary browsing;
- protect broker backups;
- delete messages after successful processing where appropriate;
- and monitor unusual access.

## 15. Protect temporary files and staging areas

Temporary storage should be:

- necessary;
- located in an approved directory or service;
- access-restricted;
- encrypted where required;
- created with safe permissions;
- protected from predictable filenames;
- cleaned after success and failure;
- bounded by retention;
- excluded from unauthorised backup where appropriate;
- monitored for accumulation;
- and included in incident and disposal procedures.

Temporary does not mean harmless. Temporary files are famous for becoming permanent residents with no rent agreement.

## 16. Protect thick-client local storage

Where a thick client stores information on corporate Windows EUC, the application should define:

- what may be cached;
- why caching is required;
- storage location;
- encryption;
- access permissions;
- user binding;
- cache lifetime;
- session binding;
- deletion on sign-out;
- behaviour after account disablement;
- behaviour after VPN loss;
- offline use;
- synchronisation;
- conflict handling;
- backup implications;
- device-loss response;
- and support access.

The enterprise provides disk encryption and endpoint management. The application determines whether and how its information is written locally.

## 17. Avoid unnecessary browser storage

The application should avoid placing sensitive information in:

- local storage;
- session storage beyond necessity;
- IndexedDB;
- browser cache;
- URL history;
- autofill fields;
- service-worker caches;
- downloaded temporary files;
- and persistent cookies.

Where browser storage is necessary:

- minimise content;
- protect tokens appropriately;
- define expiry;
- clear on sign-out where feasible;
- use cache-control headers;
- avoid secrets;
- and test shared-device and session scenarios.

## 18. Protect reports and generated documents

Generated reports should be protected through:

- role and project scope;
- approved templates;
- minimised fields;
- controlled generation;
- approved storage;
- encryption where required;
- expiry;
- download controls;
- recipient validation;
- markings;
- audit logging;
- secure deletion;
- and prevention of unauthenticated links.

Scheduled reports should not remain indefinitely in shared locations.

## 19. Protect exports

Exports should:

- contain the minimum necessary information;
- be generated only by authorised roles;
- be scoped to approved projects or records;
- use approved destinations;
- be encrypted where required;
- have integrity protection where required;
- carry appropriate markings;
- have expiry or deletion rules;
- avoid secrets;
- use controlled filenames;
- be logged;
- and be removed from staging after delivery.

## 20. Protect application logs and audit records

Logs may contain sensitive information and should be protected by:

- data minimisation;
- secret redaction;
- restricted access;
- encryption at rest through the central logging platform;
- integrity protection;
- append-only or immutable controls where proportionate;
- retention;
- secure transport;
- controlled export;
- and monitoring of access and deletion.

The application should not solve a data-at-rest problem by creating a more sensitive log copy.

## 21. Protect configuration data

Configuration may reveal or control:

- endpoints;
- trust relationships;
- feature flags;
- logging;
- session settings;
- file paths;
- access models;
- export destinations;
- and secret references.

The application should:

- store configuration in approved repositories;
- restrict modification;
- encrypt sensitive configuration;
- keep secret values in approved vaults;
- version changes;
- protect integrity;
- separate environments;
- back up securely;
- and remove obsolete copies.

## 22. Protect credentials and secret material

Passwords, private keys, API secrets, tokens and connection strings should not be stored as ordinary application data.

They should use:

- enterprise secrets management;
- certificate stores;
- key-management services;
- protected operating-system credential stores;
- or equivalent approved facilities.

The application should prevent secret leakage into:

- databases;
- logs;
- exports;
- backups;
- support bundles;
- source code;
- thick-client packages;
- and test data.

## 23. Protect cryptographic keys separately from encrypted data

Keys should be:

- stored separately from the data where feasible;
- access-restricted;
- associated with the correct purpose and environment;
- managed through approved services;
- rotated or renewed;
- backed up only where required;
- recoverable under controlled conditions;
- revoked on compromise;
- monitored;
- and destroyed at retirement.

Encrypting data while storing the key beside it in an ordinary configuration file provides limited protection.

## 24. Associate keys with data and components

The application should know:

- which key protects which data;
- which environment;
- which component uses it;
- key version;
- algorithm;
- activation date;
- expiry or cryptoperiod;
- rotation method;
- recovery method;
- owner;
- and consequences of loss or compromise.

This relationship should be recorded by reference, without copying key material into documents.

## 25. Design key rotation safely

The application should support:

- versioned keys;
- controlled overlap;
- staged activation;
- decryption of existing information;
- encryption of new information;
- re-encryption where required;
- rollback;
- recovery;
- standby and DR compatibility;
- monitoring;
- and retirement of old keys.

Rotation should be tested before production use.

## 26. Define consequences of key loss

The application should determine:

- whether information becomes permanently unavailable;
- whether escrow or backup is required;
- who may recover keys;
- how recovery is authorised;
- how recovery is logged;
- whether recovery copies are separated;
- how compromised keys are replaced;
- and whether affected information must be re-encrypted.

Key loss is an availability and records-management risk, not only a cryptographic issue.

## 27. Protect database backups

The application should ensure its database backups are:

- included in the approved backup service;
- encrypted;
- access-restricted;
- associated with the correct application and environment;
- retained according to policy;
- protected from unauthorised restore;
- monitored;
- tested;
- and securely deleted when expired.

The enterprise operates the backup service. The application confirms its data is included and validates recovery.

## 28. Protect file and object backups

Backups of files, attachments and object storage should preserve:

- confidentiality;
- integrity;
- access restrictions;
- retention;
- environment separation;
- version;
- and recoverability.

The application should know whether deletion from the live store remains recoverable from backup and for how long.

## 29. Protect snapshots, replicas and standby copies

The application should account for:

- storage snapshots;
- database replicas;
- read replicas;
- standby databases;
- search-index snapshots;
- container volumes;
- recovery replicas;
- and platform clones.

These copies should have:

- equivalent or stronger protection;
- separate environment controls;
- restricted access;
- encryption;
- retention;
- monitoring;
- and secure disposal.

## 30. Protect recovery environments

Recovery environments should not become weaker copies of production.

The application should ensure:

- equivalent storage protection;
- correct key availability;
- controlled recovery credentials;
- approved administrators;
- protected recovery packages;
- no permanent insecure fallback;
- logging;
- validation after restoration;
- removal of temporary copies;
- and reconciliation with the baseline.

## 31. Validate restored information

After restore, the application should verify:

- correct backup;
- expected point in time;
- integrity;
- record counts or reconciliation;
- database constraints;
- file accessibility;
- project and role restrictions;
- encryption state;
- key compatibility;
- audit continuity;
- malware status where relevant;
- and absence of unexpected older data.

A successful technical restore is not sufficient if the restored information is incomplete, corrupted or accessible too broadly.

## 32. Protect test and development data

Non-production environments should use:

- synthetic data;
- anonymised or de-identified data;
- masked data;
- or the minimum authorised production-derived data.

Where production data is permitted:

- obtain approval;
- restrict users;
- apply equivalent storage protection;
- prevent supplier access unless approved;
- prevent export;
- define retention;
- delete after use;
- log access;
- and document the need.

Production encryption should not be weakened merely to make test data convenient.

## 33. Protect migration and conversion data

Migration staging areas should use:

- approved storage;
- encryption;
- restricted identities;
- minimum retention;
- reconciliation;
- integrity checks;
- controlled scripts;
- logging;
- secure transfer;
- no uncontrolled local copies;
- and verified deletion after acceptance.

Legacy extracts often become forgotten permanent copies unless deletion is explicitly owned.

## 34. Protect supplier support copies

Where data is provided to a supplier:

- minimise and redact it;
- prefer synthetic reproduction;
- use approved transfer;
- encrypt;
- identify the recipient;
- link to a support case;
- require contractual protection;
- define retention and deletion;
- prohibit onward sharing;
- record the transfer;
- and obtain disposal confirmation where required.

Supplier handling remains an application risk even when the enterprise manages the contract.

## 35. Protect support bundles and crash dumps

Support bundles may contain:

- records;
- credentials;
- tokens;
- memory content;
- file paths;
- configuration;
- database fragments;
- and user information.

The application should:

- minimise collection;
- automatically redact where possible;
- encrypt;
- restrict access;
- use approved storage;
- set short retention;
- review before external transfer;
- log generation;
- delete after resolution;
- and prohibit public upload.

## 36. Protect archived information

Archive controls should include:

- approved archive format;
- approved location;
- encryption;
- integrity protection;
- index or catalogue;
- owner;
- retention;
- legal hold;
- access review;
- key availability;
- format readability;
- migration when technology becomes obsolete;
- and secure disposal.

## 37. Protect deleted information until disposal completes

The application should understand that deletion may leave data in:

- database free space;
- snapshots;
- backups;
- replicas;
- caches;
- search indexes;
- logs;
- export stores;
- client caches;
- and recovery media.

The deletion design should define:

- logical deletion;
- purge;
- index removal;
- cache removal;
- backup expiry;
- cryptographic erasure where supported;
- legal hold;
- and evidence of disposal.

## 38. Use cryptographic erasure where appropriate

Where supported and approved, cryptographic erasure may be used by securely destroying the key that protects the information.

The application should confirm:

- the key is unique enough for the intended data scope;
- no unencrypted copy exists;
- no alternate key copy remains;
- backup and escrow implications are understood;
- destruction is authorised;
- evidence is retained;
- and recovery is no longer required.

## 39. Control removable-media copies

For SC-28(2), where removable media is used, the application should:

- avoid requiring it;
- use only enterprise-approved media;
- encrypt the data;
- apply integrity protection where required;
- restrict authorised users;
- record transfer;
- label or mark appropriately;
- prohibit use on external systems unless authorised;
- define custody;
- define return and disposal;
- and use approved alternatives where possible.

Enterprise media controls are inherited, but the application owns the decision to create the copy.

## 40. Prevent unauthorised local and portable copies

The application should restrict or minimise:

- local download;
- offline cache;
- export to arbitrary paths;
- copying to personal network storage;
- standalone database copies;
- portable thick-client data;
- report packages;
- removable-media exports;
- and user-created application backups.

Where technical prevention is unavailable, use:

- least privilege;
- enterprise DLP;
- markings;
- logging;
- user obligations;
- monitoring;
- and formal risk treatment.

## 41. Protect information from privileged misuse

Storage encryption does not prevent access by an authorised process or administrator using valid credentials.

The application should also use:

- separation of duties;
- least privilege;
- named administrative accounts;
- PAM;
- row and project restrictions;
- database role separation;
- approval for extracts;
- logging;
- monitoring;
- break-glass controls;
- and independent review.

## 42. Protect integrity against privileged change

For high-value records, the application should consider:

- immutable history;
- digital signatures;
- independent approval;
- versioning;
- append-only audit;
- dual control;
- reconciliations;
- signed exports;
- protected timestamps;
- and independent verification.

The mechanism should be proportionate to the risk of malicious or accidental alteration.

## 43. Protect against storage configuration drift

The application should monitor or review:

- encryption enabled state;
- key reference;
- storage permissions;
- public or broad access;
- anonymous access;
- snapshot settings;
- backup inclusion;
- retention;
- object versioning;
- database role grants;
- local cache settings;
- debug dump settings;
- and export staging locations.

Configuration changes should be controlled under CM-05 and CM-06.

## 44. Protect against unauthorised storage destinations

The application should prevent configurable storage from being redirected to:

- arbitrary file paths;
- personal shares;
- supplier storage;
- public object stores;
- external databases;
- unmanaged network-attached storage;
- unapproved log destinations;
- and public cloud services.

Use fixed approved destinations or allow-lists.

## 45. Log access to high-risk stored information

Where justified, the application should log:

- privileged database access;
- sensitive record view;
- bulk read;
- export;
- backup restore;
- archive access;
- support-bundle generation;
- key recovery;
- emergency access;
- supplier access;
- direct data correction;
- and deletion or purge.

The application should avoid logging the sensitive content itself.

## 46. Log storage-protection changes

The application should log:

- encryption enabled or disabled;
- key reference change;
- key rotation;
- certificate or trust change;
- storage location change;
- access-permission change;
- backup inclusion change;
- retention change;
- snapshot creation;
- recovery;
- archive creation;
- export;
- purge;
- and failure of encryption or integrity checks.

## 47. Monitor storage-protection failures

The application should support detection of:

- encryption failure;
- key retrieval failure;
- expired or unavailable key;
- decryption anomaly;
- integrity-check failure;
- unexpected permission change;
- unapproved storage destination;
- backup failure;
- restore failure;
- snapshot exposure;
- abnormal bulk access;
- unauthorised export;
- local cache growth;
- temporary-file accumulation;
- support-bundle exposure;
- and storage exhaustion.

## 48. Fail safely when protection is unavailable

The application should define behaviour when:

- encryption service is unavailable;
- key management is unavailable;
- key retrieval fails;
- integrity verification fails;
- approved storage is unavailable;
- the backup service fails;
- storage permissions cannot be confirmed;
- or the application detects an unapproved location.

For sensitive operations, the application should normally deny storage or processing rather than fall back to clear-text or an unmanaged location.

## 49. Test encryption configuration

Testing should confirm:

- information is encrypted where required;
- the intended data and copies are covered;
- backups and snapshots are covered;
- keys are separate;
- unauthorised identities cannot decrypt;
- recovery identities work only as approved;
- encryption remains enabled after upgrade;
- and no clear-text temporary copy is produced.

## 50. Test access control around stored information

The application should test:

- ordinary user access;
- cross-project denial;
- privileged access;
- supplier access;
- service identity access;
- direct database denial;
- export permissions;
- backup restore permissions;
- archive access;
- local cache permissions;
- and access after role or account removal.

## 51. Test integrity controls

Testing should cover:

- unauthorised modification;
- corrupted data;
- tampered file;
- altered audit history;
- invalid signature;
- wrong checksum or MAC;
- unexpected database change;
- restoration of modified backup;
- and reconciliation failure.

The application should demonstrate detection and safe response.

## 52. Test key rotation and recovery

Testing should verify:

- new key activation;
- old and new data access;
- re-encryption where required;
- old key retirement;
- rollback;
- recovery from key-management outage;
- DR access;
- backup restore;
- and logging.

## 53. Test secure deletion

Where deletion is a material requirement, verify:

- live-store deletion;
- search-index removal;
- cache removal;
- temporary-file deletion;
- export expiry;
- archive treatment;
- backup expiry or cryptographic erasure;
- and evidence of disposal.

## 54. Test recovery without weakening protection

Recovery testing should confirm that:

- encrypted data remains encrypted;
- keys are available only to authorised recovery roles;
- temporary recovery copies are protected;
- access controls remain correct;
- logging remains available;
- obsolete keys or credentials are not reintroduced;
- and restored information is reconciled.

## 55. Review protection after material change

The application should reassess SC-28 after:

- new data type;
- new storage platform;
- new database;
- new thick client;
- new local cache;
- new export;
- new supplier;
- new backup method;
- new archive;
- migration;
- product upgrade;
- key-management change;
- incident;
- penetration-test finding;
- data-classification change;
- and change to retention requirements.

## 56. Review stored-data locations periodically

At a defined frequency, review:

- authoritative stores;
- duplicate copies;
- local caches;
- exports;
- backups;
- snapshots;
- test data;
- supplier copies;
- archives;
- temporary areas;
- old environments;
- and decommissioned storage.

The review should confirm:

- continuing need;
- ownership;
- encryption;
- permissions;
- integrity;
- retention;
- monitoring;
- and disposal.

## 57. Reconcile storage with component and data inventories

The application should compare storage records with:

- CM-08 inventory;
- architecture;
- data flows;
- database catalogues;
- file stores;
- backup jobs;
- object stores;
- search indexes;
- thick-client design;
- export configuration;
- supplier records;
- and recovery plans.

This should identify unknown, obsolete or unprotected copies.

## 58. Decommission storage completely

When a component or environment is retired, the application should:

- stop writes;
- identify retained information;
- migrate authorised records;
- revoke service identities;
- revoke or retire keys;
- remove application access;
- delete live data;
- address snapshots and replicas;
- remove search indexes;
- remove local caches;
- expire backups according to policy;
- archive required evidence;
- update CM-02 and CM-08;
- update architecture;
- and obtain disposal evidence.

## 59. Manage storage-protection limitations

Where a legacy or commercial application cannot meet the expected protection, record:

- information affected;
- storage location;
- expected protection;
- actual protection;
- users and administrators with access;
- exposure;
- business impact;
- reason;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, migration, isolation or replacement plan;
- and review or expiry date.

Examples include:

- unencrypted application file store;
- local thick-client clear-text cache;
- supplier-controlled backup;
- export files without encryption;
- encryption key stored beside the data;
- no integrity protection for high-value records;
- unprotected temporary files;
- test environment containing production data;
- inability to purge search indexes;
- no secure deletion;
- or database administrators able to bypass all application controls.

The limitation should be recorded in the application addendum or risk process.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses encrypted corporate EUC, managed database and storage platforms, enterprise key management, encrypted backups and central monitoring. They exclude enterprise storage engineering, large-scale data migration and major redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify all application data-at-rest locations** | Map databases, file stores, indexes, queues, caches, exports, logs, temporary areas, backups, test data, supplier copies and archives. | Summarise in the **SSP SC-28 statement** and maintain detail in the existing **architecture**, **data-flow diagrams**, **data inventory**, **CM-08 inventory**, **ConOps** or **SyOps**. | **8–16 hours** |
| **2. Classify stored information and define protection requirements** | Assign confidentiality, integrity, retention, access, encryption, recovery and disposal requirements to material information categories. | Record in the **data-classification assessment**, **data dictionary**, **security requirements**, **records schedule**, **risk assessment** and **SSP**. | **8–20 hours** |
| **3. Confirm approved platform encryption coverage** | Verify encryption for database, file, object, volume, snapshot, replica and backup storage and identify any uncovered copies. | Retain evidence in the **platform/service configuration**, **database design**, **storage design**, **backup record**, **CM-06 configuration** and **SSP inherited-control references**. | **8–20 hours** |
| **4. Protect application-specific files, attachments and indexes** | Apply access restrictions, encryption where required, secure identifiers, retention, deletion and project-level enforcement. | Capture controls in the **file-storage design**, **search design**, **data model**, **AC-03/AC-04 design**, **CM-06 settings** and **security test report**. | **12–32 hours** |
| **5. Protect thick-client and browser-local data** | Minimise cache, use approved protected locations, define expiry and deletion, prevent secrets in browser storage and handle device or account loss. | Record in the **thick-client design**, **browser/session design**, **packaging specification**, **SyOps**, **CM-06 configuration** and **test evidence**. | **8–24 hours** |
| **6. Protect exports, reports and temporary data** | Minimise content, restrict generation and destinations, encrypt where required, apply expiry and delete staging and temporary copies. | Use the existing **export/report specification**, **temporary-file design**, **AC-04 controls**, **SyOps**, **release tests** and **audit evidence**. | **8–24 hours** |
| **7. Protect test, migration and supplier copies** | Prefer synthetic data, approve production-derived data, secure staging, redact supplier bundles and verify deletion after use. | Record in the **test-data plan**, **migration plan**, **supplier support record**, **data-transfer approval**, **risk register** and **test close-out evidence**. | **8–24 hours** |
| **8. Define application key and certificate dependencies** | Link protected data and components to approved key references, owners, versions, rotation, recovery and compromise procedures. | Use the existing **key/certificate records**, **security architecture**, **secrets platform**, **CM-08 inventory**, **SyOps** and **SSP SC-12/SC-28 sections**. | **8–20 hours** |
| **9. Protect and test backup and recovery copies** | Confirm encrypted backups, restricted restore, key availability, representative recovery and post-restore integrity and access validation. | Evidence remains in the **backup configuration**, **recovery plan**, **recovery test report**, **operational acceptance record** and **CM-02 baseline**. | **12–32 hours per major recovery test** |
| **10. Protect logs, configuration and support bundles** | Minimise secrets and business data, use approved encrypted repositories, restrict access and apply retention and disposal. | Record controls in the **AU-02 logging specification**, **CM-06 configuration**, **support procedure**, **SIEM onboarding**, **privacy review** and **SSP**. | **6–16 hours** |
| **11. Log and monitor storage-protection activity** | Generate events for key changes, encryption failures, high-risk access, exports, restores, permission changes and integrity failures. | Define events in the **SSP AU-02/SI-04/SC-28 sections** and existing **event specification**. Verify through **SIEM onboarding** and the **security test report**. | **6–16 hours** |
| **12. Test confidentiality and access controls** | Verify unauthorised users, cross-project users, suppliers and direct database clients cannot access stored information or protected copies. | Add cases to the normal **security test plan**, **access-control test**, **database test**, **thick-client test** and **penetration test**. | **16–36 hours per major test cycle** |
| **13. Test integrity, key rotation and failure behaviour** | Test tampering, corrupted data, signature or MAC failure, key rotation, unavailable keys, encryption failure and safe response. | Retain evidence in the **integrity test**, **key rollover test**, **resilience test**, **release pack** and **operational acceptance report**. | **16–40 hours per major test cycle** |
| **14. Review copies, retention and disposal periodically** | Review caches, exports, test data, supplier copies, snapshots, backups, archives and obsolete environments and remove unnecessary copies. | Retain outcomes in established **service reviews**, **data reviews**, **records reviews**, **CA-07 posture reports** or **application governance minutes**. | **8–20 hours per review** |
| **15. Integrate storage protection into change and decommissioning** | Require assessment and update of encryption, keys, backups, retention, inventories and disposal whenever storage or data use changes. | Add checks to the **change-impact assessment**, **release checklist**, **migration plan**, **operational acceptance** and **decommissioning record**. | **6–16 hours initially** |
| **16. Document and manage storage-protection limitations** | Record unencrypted stores, weak local cache, supplier backup, inadequate integrity, key co-location or disposal constraints with compensating controls. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP SC-28 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application using mature encrypted enterprise storage and backup services, initial application effort is commonly around **120–280 hours**.

Ongoing application effort is commonly around **6–20 hours per month**, plus recovery tests, key rotations, data reviews, migrations and decommissioning activity.

A simple commercial application using one managed database and no local cache may require less. A thick-client, document-heavy, export-heavy, legacy or supplier-supported application with several stores, local files, weak key handling or production data in lower environments may require substantially more.

The estimates should not be added mechanically where activities overlap. SC-28 commonly shares implementation and evidence with:

- AC-03 access enforcement;
- AC-04 information-flow enforcement;
- AC-06 least privilege;
- AC-20 use of external systems;
- AU-02 event logging;
- CM-02 baseline configuration;
- CM-06 configuration settings;
- CM-08 component inventory;
- MP media-protection controls;
- SC-12 cryptographic key establishment and management;
- SC-13 cryptographic protection;
- SI-07 software and information integrity;
- CP backup and recovery controls;
- and CA-07 continuous monitoring.

---

## Suggested document placement

To avoid creating disconnected evidence, information-at-rest protection should normally be distributed across established application and SDLC artefacts:

- **SSP:** SC-28 implementation approach, information categories, inherited encryption services, application-specific stores, integrity, testing and limitations.
- **ConOps or SyOps:** operational storage, exports, local cache, support copies, backup, recovery, key failure and disposal responsibilities.
- **Security architecture:** storage components, trust boundaries, encryption layers, key services, replicas, backups and client storage.
- **Data-flow diagrams and data inventory:** authoritative and secondary stores, temporary locations, exports and external or supplier copies.
- **Data dictionary and classification assessment:** information sensitivity, integrity, retention and handling requirements.
- **CM-08 inventory:** databases, stores, indexes, queues, caches, backup components and key dependencies.
- **CM-02 baseline:** approved storage configuration, encryption state, versions and key references.
- **CM-06 configuration specification:** encryption, permissions, object policies, database settings, local cache, temporary directories and retention settings.
- **Database and storage design:** schemas, roles, encryption, backup, replicas, export and restore.
- **Thick-client design:** local cache, protected storage, expiry, deletion, offline behaviour and device-loss response.
- **Export and report specifications:** minimisation, destination, encryption, expiry, markings and deletion.
- **Key and certificate records:** key purpose, owner, version, rotation, recovery and consuming components.
- **Backup and recovery plan:** encrypted copies, restore authority, key availability, validation and disposal.
- **Test-data and migration plans:** synthetic data, protected staging, retention and deletion.
- **Supplier records:** support-copy minimisation, transfer, encryption, retention and disposal.
- **AU-02 and SI-04 evidence:** privileged storage access, export, restore, key, encryption and integrity events.
- **Test plans and reports:** access, encryption, integrity, key rotation, failure, recovery and deletion tests.
- **Change and release records:** storage change, key rollover, new data use, backup update and post-change verification.
- **Decommissioning records:** migration, key retirement, copy removal and disposal evidence.
- **Risk register or application addendum:** unencrypted data, local cache, supplier copies, weak integrity, key-management or disposal limitations.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide data-classification and handling policy;
- managed Windows EUC full-disk encryption;
- enterprise server and storage encryption;
- enterprise database-platform encryption;
- enterprise backup encryption;
- enterprise key-management services;
- enterprise secrets-management services;
- organisation-wide cryptographic standards;
- central storage administration;
- enterprise removable-media controls;
- corporate DLP and information-protection platforms;
- central records-retention and legal-hold requirements;
- enterprise secure disposal services;
- central SIEM and SOC operations;
- infrastructure backup and recovery platforms;
- and organisation-wide risk and exception governance.

The application team must still:

- identify every application-owned information store and copy;
- classify information and define application-specific protection;
- configure enterprise storage services correctly;
- prevent unnecessary or unapproved copies;
- protect local, temporary, export, test, supplier and recovery data;
- associate keys with the correct information and component;
- test encryption, integrity, recovery and deletion;
- monitor protection failures;
- update storage controls after change;
- and formally manage application-specific limitations.

> **Key dividing line:** the enterprise operates encrypted storage, backup and key-management platforms; the application ensures that every application copy is placed on those platforms correctly, remains access-controlled and tamper-resistant, and is retained and destroyed according to its business and security requirements.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, SC-28 Protection of Information at Rest.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, SC-28 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-111, Guide to Storage Encryption Technologies for End User Devices**.
4. National Institute of Standards and Technology, **NIST SP 800-57 Part 1 Rev. 5, Recommendation for Key Management: Part 1 — General**.
5. National Institute of Standards and Technology, **NIST SP 800-57 Part 2 Rev. 1, Recommendation for Key Management: Part 2 — Best Practices for Key Management Organizations**.
6. National Institute of Standards and Technology, **NIST SP 800-57 Part 3 Rev. 1, Recommendation for Key Management: Part 3 — Application-Specific Key Management Guidance**.
7. National Institute of Standards and Technology, **NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems**.
8. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, current SP 800-53 and SP 800-53A catalogues.
