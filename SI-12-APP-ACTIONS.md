# SI-12 Information Management and Retention — Application Actions

## Purpose

For an IT application, SI-12 means the application must ensure that information is **created, collected, stored, used, copied, archived, retained and disposed of in accordance with authorised business, legal, regulatory, privacy, security and records-management requirements**.

The control is not satisfied merely by configuring a database backup period or deleting old records occasionally. Application compliance requires a controlled information lifecycle covering:

- business records;
- attachments and documents;
- personal information;
- security and audit information;
- application logs;
- reports and exports;
- workflow history;
- messages and integration payloads;
- configuration and reference data;
- thick-client and browser caches;
- temporary and staging files;
- test and training data;
- backups, replicas and snapshots;
- archived records;
- supplier-held copies;
- incident and investigation material;
- and data remaining after migration or decommissioning.

The enterprise may provide:

- corporate records-management policy;
- approved retention schedules;
- legal-hold processes;
- privacy policy and data-protection governance;
- data-classification and handling standards;
- enterprise archival services;
- backup and recovery platforms;
- secure media-sanitisation and disposal services;
- corporate email and collaboration retention;
- central logging retention;
- enterprise data-loss prevention;
- procurement and supplier contractual controls;
- and organisation-wide risk and exception processes.

Those capabilities are inherited.

The application remains responsible for translating those requirements into application behaviour, including:

- identifying the information it manages;
- assigning each information type to an approved retention rule;
- preventing indefinite or unauthorised retention;
- retaining records needed for business, security and accountability purposes;
- suspending deletion when a legal or investigation hold applies;
- controlling duplicate, cached, exported, test and supplier copies;
- disposing of information consistently across all application stores;
- ensuring backups and archives do not defeat disposal requirements;
- preserving integrity, provenance and readability during retention;
- verifying deletion and decommissioning;
- and documenting product or supplier limitations.

NIST SI-12 requires organisations to manage and retain information within systems and information output from systems in accordance with applicable laws, executive orders, directives, regulations, policies, standards, guidelines and operational requirements. Relevant enhancements address limiting personally identifiable information elements and information disposal. NIST SP 800-88 Rev. 2, finalised in 2025, provides current guidance for media sanitisation and disposal based on information sensitivity.

> **Core principle:** the enterprise defines the authoritative records, privacy and disposal requirements; the application must implement those requirements across every application-specific copy and prove that retention, hold and disposal actions work as intended.

---

## 1. Define the application information-management scope

The application should identify every category of information that it creates, receives, processes, stores or produces.

This normally includes:

- authoritative business records;
- draft records;
- approvals and decisions;
- engineering or operational records;
- attachments;
- imported files;
- generated reports;
- exports;
- user profiles;
- access and role records;
- service-account records;
- audit history;
- application logs;
- security findings;
- incident evidence;
- configuration;
- reference data;
- workflow state;
- integration messages;
- API payloads;
- message queues;
- notifications;
- search indexes;
- local thick-client data;
- browser storage;
- temporary files;
- quarantine data;
- backups;
- snapshots;
- replicas;
- recovery copies;
- archive copies;
- test and training data;
- migration extracts;
- supplier diagnostic data;
- support bundles;
- and decommissioned-system data.

The scope should align with:

- the system boundary;
- data-flow diagrams;
- data model;
- CM-08 component inventory;
- SC-28 storage map;
- interface inventory;
- backup design;
- privacy assessment;
- and corporate records schedule.

## 2. Identify authoritative information classes

The application should distinguish between:

- authoritative records;
- working copies;
- convenience copies;
- transient processing data;
- caches;
- derived data;
- indexes;
- duplicate exports;
- audit evidence;
- backup copies;
- archive copies;
- and data held by connected systems or suppliers.

This distinction matters because different copies may have different:

- retention rules;
- deletion methods;
- integrity requirements;
- access controls;
- legal-hold treatment;
- and ownership.

A search index may be a derivative copy, but it still needs deletion and hold behaviour aligned with the authoritative record.

## 3. Maintain an information-retention register

The application should maintain a coherent retention view for each material information class.

Relevant attributes include:

- information category;
- business purpose;
- information owner;
- record owner;
- authoritative store;
- secondary stores;
- sensitivity;
- personal-information status;
- retention rule;
- retention trigger;
- minimum retention;
- maximum retention;
- disposal method;
- legal-hold capability;
- archive requirement;
- integrity requirement;
- access roles;
- backup treatment;
- supplier-copy treatment;
- deletion dependencies;
- exception;
- and review date.

The register may be implemented through the existing data inventory, records schedule mapping, architecture and SSP rather than a new standalone spreadsheet.

## 4. Map information to the corporate retention schedule

Every material application information type should be mapped to an approved enterprise records or retention category.

The application should not invent retention periods without appropriate records, legal, privacy or business approval.

The mapping should identify:

- the authoritative schedule item;
- the responsible information owner;
- the retention trigger;
- the retention period;
- whether the period is minimum, maximum or both;
- legal-hold treatment;
- archival requirements;
- disposal authority;
- and application implementation.

Where no suitable schedule item exists, the application should escalate for an authoritative decision rather than retain information indefinitely.

## 5. Define retention triggers precisely

A retention period is not meaningful unless the application knows when the clock begins.

Triggers may include:

- record creation;
- final approval;
- record closure;
- contract termination;
- project completion;
- employee departure;
- account disablement;
- last transaction;
- last use;
- supersedence;
- incident closure;
- vulnerability closure;
- release retirement;
- support-case closure;
- asset disposal;
- or end of a defined reporting period.

The application should avoid ambiguous triggers such as “when no longer needed” unless a controlled decision process defines that point.

## 6. Distinguish minimum and maximum retention

The application should understand whether a rule means:

- information must be retained for at least a period;
- information must be deleted by a maximum point;
- information may be retained within an approved range;
- information must be transferred to an archive;
- or information is retained permanently.

A minimum period should not be interpreted as permission to retain forever.

A maximum period should not cause premature destruction where another approved obligation or hold applies.

## 7. Define disposition actions

At the end of retention, the application should perform the approved action, such as:

- delete;
- purge;
- anonymise;
- de-identify;
- aggregate;
- archive;
- transfer to an authoritative records repository;
- return to the information owner;
- destroy cryptographic keys;
- sanitise media;
- or retain permanently under controlled archival arrangements.

The disposition action should be appropriate to:

- information sensitivity;
- record value;
- technical storage;
- backup model;
- legal requirements;
- and recovery needs.

## 8. Automate retention where practical

Applications should automate retention and disposition where the product and risk permit.

Automation should:

- use approved retention rules;
- calculate the correct trigger date;
- identify eligible records;
- exclude active holds;
- produce a preview or count;
- require approval where appropriate;
- execute consistently;
- record the outcome;
- handle failures;
- reconcile dependent copies;
- and support rollback only where authorised.

Automation reduces forgotten data, but an incorrect automated rule can delete large volumes quickly. Configuration, testing and oversight are essential.

## 9. Protect retention configuration

Retention rules are security- and records-critical configuration.

The application should restrict changes to:

- retention periods;
- trigger definitions;
- archive destinations;
- disposal actions;
- legal-hold flags;
- exclusion rules;
- purge jobs;
- backup expiry;
- search-index deletion;
- log retention;
- export expiry;
- and supplier-copy settings.

Changes should be:

- authorised;
- attributable;
- version-controlled;
- tested;
- logged;
- reviewed for legal and privacy impact;
- reversible where practical;
- and managed through CM-05 and CM-06.

## 10. Prevent unauthorised retention extension

The application should prevent users or administrators from retaining information beyond approved periods merely for convenience.

Examples include:

- changing a closure date;
- repeatedly reopening a record;
- copying records into another module;
- exporting before deletion;
- keeping attachments in a shared folder;
- changing a retention category;
- disabling a purge job;
- moving files into an exception directory;
- or keeping supplier diagnostic copies.

Where a business need requires extension, use the approved exception or hold process.

## 11. Prevent premature deletion

The application should ensure that authorised users cannot delete records before:

- the minimum retention period;
- required approval;
- completion of workflow;
- resolution of legal hold;
- completion of an incident;
- completion of audit or investigation;
- or transfer to the authoritative archive.

Deletion permissions should be distinct from ordinary edit permissions where risk warrants it.

## 12. Support legal, regulatory and investigation holds

The application should support or participate in a controlled hold process.

A hold should:

- identify the affected information;
- identify the authority;
- identify the reason;
- have an owner;
- have an effective date;
- suspend relevant deletion;
- cover dependent copies where required;
- protect information from alteration;
- be access-restricted;
- be logged;
- be reviewable;
- and be released only by authorised instruction.

The application should not expose sensitive legal details broadly merely to enforce the hold.

## 13. Apply holds across related records and copies

A hold may need to cover:

- parent records;
- child records;
- attachments;
- workflow history;
- audit history;
- reports;
- exports;
- messages;
- search indexes;
- backups;
- archived copies;
- supplier copies;
- and relevant account or access records.

The application should define how holds propagate and how gaps are managed.

## 14. Preserve information integrity during retention

Retained information should remain:

- complete;
- accurate;
- attributable;
- protected from unauthorised alteration;
- versioned where required;
- linked to approvals;
- timestamped;
- readable;
- and recoverable.

Controls may include:

- database constraints;
- immutable history;
- digital signatures;
- protected audit records;
- controlled amendments;
- version control;
- hash or integrity checks;
- reconciliation;
- and restricted administrative access.

## 15. Preserve provenance and context

Long-lived information should retain enough context to remain meaningful.

This may include:

- creator;
- owner;
- source;
- version;
- approval;
- project;
- classification;
- date;
- applicable policy;
- schema version;
- relationship to parent records;
- migration history;
- and disposition authority.

A retained record without its metadata may be technically present but operationally useless.

## 16. Preserve readability and usability

The application should ensure that records remain readable for the required retention period.

This may require:

- documented formats;
- supported viewers;
- format migration;
- archive packaging;
- schema documentation;
- character-set preservation;
- version metadata;
- export to durable formats;
- retention of necessary decryption capability;
- and periodic archive testing.

A proprietary format tied to an unsupported application version creates a retention risk.

## 17. Manage record amendments

Where retained records may be corrected or amended, the application should preserve:

- original value where required;
- amended value;
- acting identity;
- reason;
- approval;
- timestamp;
- version;
- and relationship between versions.

The application should not overwrite significant historical evidence without traceability.

## 18. Manage deletion of business records

Deletion should require:

- appropriate role;
- eligible retention state;
- no active hold;
- correct record scope;
- approval where required;
- controlled transaction;
- dependent-copy handling;
- audit logging;
- failure handling;
- and verification.

The user interface should not be the sole enforcement point; deletion rules should be enforced server-side.

## 19. Manage soft deletion

Where the application uses soft deletion, define:

- who can see deleted records;
- how long they remain recoverable;
- who may restore them;
- when final purge occurs;
- whether the retention clock continues;
- how search indexes behave;
- whether exports include them;
- backup treatment;
- and legal-hold treatment.

Soft deletion is a lifecycle state, not final disposal.

## 20. Manage hard deletion and purge

Final purge should address:

- authoritative data;
- child records;
- attachments;
- indexes;
- caches;
- staging areas;
- report copies;
- message persistence;
- and other application-controlled derivatives.

The purge should:

- be authorised;
- be logged;
- handle partial failure;
- produce counts;
- preserve non-sensitive evidence of the action;
- and support reconciliation.

## 21. Manage anonymisation and de-identification

Where information is retained in anonymised or de-identified form, the application should define:

- fields removed or transformed;
- re-identification risk;
- retained linkage;
- key or mapping destruction;
- small-population risks;
- free-text handling;
- attachments;
- audit history;
- data quality;
- approval;
- validation;
- and residual classification.

Removing a name alone is rarely sufficient if other fields can identify the individual or project.

## 22. Limit personally identifiable information

Where SI-12 enhancements or privacy requirements apply, the application should limit personally identifiable information to:

- elements necessary for the authorised purpose;
- the minimum number of records;
- the minimum precision;
- the minimum retention period;
- and the minimum user population.

The application should review:

- optional profile fields;
- copied directory attributes;
- historic identities;
- free-text fields;
- exported user lists;
- audit content;
- test data;
- support bundles;
- and duplicate identity stores.

## 23. Manage application logs

Application logs should have defined:

- purpose;
- event content;
- sensitivity;
- retention category;
- central destination;
- access roles;
- legal-hold treatment;
- archive requirement;
- and disposal.

The application should avoid retaining verbose diagnostic logs longer than needed.

Security and audit logs may require longer retention than ordinary operational logs, but they should still follow an approved schedule.

## 24. Manage audit history

Audit history should be retained long enough to support:

- accountability;
- security monitoring;
- incident investigation;
- fraud or misuse investigation;
- dispute resolution;
- compliance;
- and legal obligations.

The application should preserve audit integrity and avoid disposing of the audit evidence before the related business record where that would prevent meaningful reconstruction.

## 25. Manage authentication and access records

Retention should be defined for:

- account creation;
- role assignments;
- privilege changes;
- access reviews;
- supplier access;
- emergency access;
- authentication events;
- session events;
- service identity records;
- and account disablement.

These records often need to outlast the active account.

## 26. Manage workflow and approval history

The application should retain the evidence needed to show:

- who initiated;
- who edited;
- who reviewed;
- who approved;
- who released;
- what version was approved;
- what exceptions applied;
- and when each action occurred.

Workflow history should remain linked to the authoritative record.

## 27. Manage attachments and documents

Attachments should inherit or map to the parent record’s:

- retention;
- legal hold;
- access;
- classification;
- archive;
- and disposal rules.

The application should prevent orphaned attachments from remaining after parent-record disposal unless there is a separately approved retention need.

## 28. Manage reports and exports

Reports and exports should have shorter, explicit lifecycles where they are convenience copies.

Controls may include:

- automatic expiry;
- deletion from staging;
- expiring links;
- restricted destinations;
- limited regeneration windows;
- user notification;
- no indefinite report repository;
- and scheduled cleanup.

Where a generated report becomes an authoritative business record, it should be assigned the appropriate records category.

## 29. Manage temporary and staging data

Temporary data should have:

- a defined purpose;
- an approved location;
- a maximum lifetime;
- cleanup after success;
- cleanup after failure;
- startup or scheduled cleanup;
- capacity monitoring;
- access restriction;
- and verification.

Examples include:

- upload staging;
- document conversion;
- export packaging;
- migration work areas;
- report generation;
- parser files;
- and reconciliation files.

## 30. Manage search indexes and caches

Indexes and caches should be updated when:

- information is deleted;
- a hold is applied;
- access scope changes;
- classification changes;
- a record is corrected;
- or retention expires.

The application should define:

- refresh delay;
- stale data handling;
- cache expiry;
- purge;
- reconciliation;
- and failure escalation.

## 31. Manage message queues and integration payloads

Persistent messages should have:

- defined retention;
- expiry;
- dead-letter handling;
- retry limits;
- archive requirements;
- purge;
- legal-hold treatment where applicable;
- and minimal content.

The application should avoid treating queues as indefinite data stores.

## 32. Manage notifications and email output

Application-generated email and notifications should:

- minimise copied business information;
- use links rather than full records where appropriate;
- follow enterprise email retention;
- avoid attachments where not required;
- use approved recipients;
- and be considered when legal or investigation holds apply.

The application may not control enterprise mailbox retention, but it controls what information it sends.

## 33. Manage thick-client and browser copies

The application should define retention for:

- thick-client caches;
- offline data;
- downloaded attachments;
- local configuration;
- browser cache;
- local storage;
- session storage;
- temporary downloads;
- and diagnostic files.

Controls should include:

- minimum necessary content;
- expiry;
- deletion on sign-out where appropriate;
- deletion after synchronisation;
- behaviour after account disablement;
- device-loss handling;
- and no indefinite offline copy.

## 34. Manage test and training data

Non-production data should have:

- approved source;
- purpose;
- owner;
- environment;
- retention;
- deletion date;
- access restrictions;
- masking or anonymisation;
- supplier restrictions;
- and review.

Production-derived data should not become a permanent test dataset unless specifically authorised.

## 35. Manage migration data

Migration activities should define:

- source extract;
- staging copies;
- transformation files;
- reconciliation reports;
- failed records;
- rollback copies;
- approval;
- retention after acceptance;
- deletion;
- and evidence.

Legacy extracts should be deleted or archived promptly after migration acceptance according to the approved plan.

## 36. Manage backup retention

The application should confirm that backup retention aligns with:

- business recovery requirements;
- records requirements;
- privacy requirements;
- legal holds;
- information sensitivity;
- and disposal expectations.

The application should understand:

- backup frequency;
- retention period;
- immutable period;
- off-site copies;
- replica treatment;
- restore authority;
- and when deleted records cease to be recoverable.

The enterprise operates the backup platform; the application validates that its information and retention needs are correctly represented.

## 37. Prevent backup retention from defeating disposal

The application should document how disposal applies to backups.

Possible approaches include:

- allow the record to age out through the approved backup cycle;
- prevent ordinary restoration of disposed records;
- reapply application deletion after restore;
- maintain suppression lists;
- use cryptographic erasure where appropriate;
- perform targeted deletion where technically feasible and required;
- or retain under an approved exception.

The chosen approach should be agreed with records, privacy, security and backup owners.

## 38. Manage snapshots and replicas

Snapshots and replicas should have:

- defined purpose;
- owner;
- retention;
- access restrictions;
- legal-hold treatment;
- deletion;
- and decommissioning.

Ad hoc snapshots created for troubleshooting or change should have an expiry and should not become hidden long-term copies.

## 39. Manage archive transfer

Where records are transferred to an archive, the application should ensure:

- completeness;
- approved format;
- metadata;
- integrity;
- chain of custody;
- encryption;
- access controls;
- retention category;
- hold status;
- successful ingestion;
- reconciliation;
- and deletion from the source when authorised.

## 40. Manage supplier-held information

Where suppliers receive or store application information, the application should identify:

- information;
- purpose;
- supplier;
- authoritative agreement;
- storage location;
- access;
- retention;
- legal hold;
- incident notification;
- return;
- deletion;
- disposal evidence;
- subcontractor use;
- and contract termination.

The application team should track supplier copies generated for support, testing, migration or diagnostics.

## 41. Manage external-system copies

Where AC-20 permits an approved external system, the application should ensure that retention and disposal obligations are included in the connection or processing arrangement.

The application should not assume that deletion from the internal application deletes the external copy automatically.

## 42. Manage incident and investigation evidence

Incident evidence may require retention outside ordinary application schedules.

The application should support:

- preservation;
- restricted access;
- integrity;
- chain of custody;
- legal or investigation hold;
- controlled copies;
- documented release;
- and authorised disposal.

Normal purge jobs should not remove held incident evidence.

## 43. Manage vulnerability and penetration-test records

Security findings, penetration-test evidence and remediation records should have defined:

- sensitivity;
- access;
- retention;
- closure evidence;
- legal-hold treatment;
- supplier sharing;
- and disposal.

These records may reveal exploitable details and should not be kept indefinitely without a purpose.

## 44. Manage configuration and release records

The application should retain enough historical information to establish:

- approved configuration;
- deployed release;
- change history;
- release provenance;
- security settings;
- dependency versions;
- rollback state;
- and decommissioned versions.

Retention should support incident investigation and recovery without preserving vulnerable packages indefinitely in active distribution paths.

## 45. Manage source code and build artefacts

The application should define retention for:

- repositories;
- branches;
- tags;
- release artefacts;
- container images;
- SBOMs;
- build logs;
- signing records;
- test evidence;
- and superseded packages.

Old artefacts should be protected from unauthorised reintroduction and disposed of or archived according to approved SDLC and records requirements.

## 46. Manage deleted user and service identities

When a user or service account is removed, the application should preserve necessary historical attribution.

The application should avoid replacing the stable identity in old records with:

- blank;
- “deleted user” only;
- a new user’s identity;
- or an untraceable display name.

Retain the minimum identity metadata needed for accountability, subject to privacy and retention requirements.

## 47. Handle account and record closure consistently

Application closure workflows should trigger relevant lifecycle actions, such as:

- start retention clock;
- stop editing;
- restrict access;
- archive;
- remove temporary access;
- stop scheduled reports;
- remove supplier access;
- expire working copies;
- and schedule disposal.

## 48. Log retention and disposal events

The application should generate useful events for:

- retention-rule change;
- hold applied;
- hold released;
- archive transfer;
- deletion request;
- deletion approval;
- soft deletion;
- restoration;
- purge;
- anonymisation;
- disposal failure;
- backup restore of previously deleted data;
- export expiry;
- supplier deletion confirmation;
- and decommissioning disposal.

Events should include:

- acting identity or process;
- affected information category;
- record or batch reference;
- authority;
- time;
- outcome;
- count;
- exception or hold status;
- and correlation identifier.

The log should not reproduce the deleted information.

## 49. Monitor retention failures

The application should support detection of:

- purge job failure;
- growing backlog;
- hold-processing failure;
- unauthorised retention-rule change;
- deletion before minimum retention;
- records beyond maximum retention;
- orphaned attachments;
- stale search-index copies;
- expired reports still accessible;
- temporary-file accumulation;
- old test data;
- supplier copies past expiry;
- backup-retention mismatch;
- archive-transfer failure;
- and disposal exceptions approaching expiry.

## 50. Reconcile retention across stores

The application should periodically compare:

- authoritative database;
- attachments;
- file stores;
- search indexes;
- caches;
- exports;
- reports;
- messages;
- backups;
- archives;
- non-production;
- supplier copies;
- and local client storage.

The goal is to identify records that have been disposed of in one place but remain unexpectedly available elsewhere.

## 51. Verify disposal

Disposal should be verified through proportionate evidence such as:

- record counts;
- purge job results;
- reconciliation report;
- search result validation;
- file-store check;
- archive receipt;
- supplier confirmation;
- media-sanitisation certificate;
- key-destruction record;
- restore test;
- or independent review.

A closed deletion ticket without technical verification may be insufficient.

## 52. Apply media sanitisation requirements

Where the application controls or initiates disposal of storage media, it should use the enterprise sanitisation process aligned with current NIST SP 800-88 Rev. 2 guidance.

The application should provide:

- information sensitivity;
- media type;
- application and owner;
- disposal authority;
- retention or hold status;
- required sanitisation outcome;
- and verification needs.

The enterprise normally selects and performs the media-specific sanitisation method.

## 53. Use cryptographic erasure where appropriate

Where data is protected with suitably scoped encryption keys and the enterprise approves the method, cryptographic erasure may support disposal.

The application should confirm:

- the relevant information is encrypted;
- the key scope is appropriate;
- no unencrypted copy remains;
- all key copies are identified;
- escrow and backup implications are understood;
- destruction is authorised;
- and evidence is retained.

## 54. Test retention logic

Testing should include:

- trigger calculation;
- minimum and maximum period;
- eligible record selection;
- held-record exclusion;
- archive selection;
- soft deletion;
- restoration;
- purge;
- dependent attachments;
- search-index removal;
- cache expiry;
- report expiry;
- audit event;
- and failure handling.

Use boundary dates and representative record states.

## 55. Test legal-hold behaviour

Testing should verify that:

- held records are not deleted;
- related attachments are protected;
- dependent copies are handled;
- unauthorised users cannot apply or release holds;
- the hold is logged;
- release resumes the correct lifecycle;
- and ordinary purge processes remain operational for non-held records.

## 56. Test disposal across dependent copies

The application should test whether disposal removes or appropriately handles:

- main record;
- child records;
- files;
- indexes;
- caches;
- reports;
- queued messages;
- local copies;
- supplier copies;
- and backup recovery.

Not every backup copy must necessarily be deleted immediately, but the approved treatment should be tested.

## 57. Test archive and long-term readability

Archive tests should confirm:

- successful transfer;
- record counts;
- metadata;
- integrity;
- access control;
- search or retrieval;
- decryption;
- viewer availability;
- hold status;
- and source deletion where authorised.

## 58. Test recovery after disposal

Recovery testing should ensure that restoring an older backup does not silently reactivate disposed information.

The application should define how to:

- identify restored records that should remain deleted;
- reapply retention and hold state;
- rerun purge;
- reconcile with current authoritative state;
- and log the recovery action.

## 59. Review retention after material change

The application should reassess SI-12 after:

- new information type;
- new workflow;
- new report or export;
- new interface;
- new supplier;
- new storage location;
- new thick-client cache;
- migration;
- archive change;
- backup change;
- legal or policy change;
- privacy assessment;
- incident;
- or decommissioning decision.

## 60. Review retained information periodically

At a defined frequency, review:

- information still held;
- retention category;
- records beyond maximum retention;
- records nearing disposal;
- active holds;
- old exports;
- test data;
- supplier copies;
- archive readability;
- purge failures;
- and exceptions.

The review should involve the information or record owner where business judgement is required.

## 61. Integrate retention into change and release

Changes should assess impact on:

- information categories;
- retention triggers;
- holds;
- purge rules;
- archive formats;
- backups;
- indexes;
- exports;
- logs;
- suppliers;
- and disposal.

A release that introduces a new store or copy should not complete until lifecycle requirements are defined.

## 62. Integrate retention into decommissioning

Before application retirement, define:

- which records transfer;
- archive destination;
- format;
- metadata;
- legal holds;
- retention owner;
- access after shutdown;
- remaining backups;
- supplier copies;
- storage sanitisation;
- keys;
- identities;
- and disposal evidence.

The application should not be switched off while leaving unmanaged data behind.

## 63. Manage retention exceptions and limitations

Where a legacy or commercial product cannot meet the required lifecycle, record:

- affected information;
- expected retention or disposal;
- actual product behaviour;
- storage locations;
- business, legal, privacy and security impact;
- reason;
- compensating controls;
- manual process;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, migration, archive or replacement plan;
- review date;
- and expiry.

Examples include:

- no record-level purge;
- inability to apply legal hold;
- attachments retained after record deletion;
- no automated retention;
- proprietary archive format;
- backups retained longer than the application maximum;
- supplier copies with weak deletion evidence;
- deleted records remaining in search indexes;
- no audit of disposal;
- or production data retained indefinitely in test.

The exception should be visible in the application addendum or risk process.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses enterprise records schedules, privacy governance, managed backup, central logging and secure disposal services. They exclude enterprise policy development, legal advice, archive-platform engineering and major historic data cleansing.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify application information classes and copies** | Map business records, attachments, logs, exports, caches, messages, backups, test data, supplier copies and archives. | Summarise in the **SSP SI-12 statement** and maintain detail in the existing **data inventory**, **architecture**, **data-flow diagrams**, **CM-08 inventory**, **ConOps** or **SyOps**. | **8–16 hours** |
| **2. Map each information class to an approved retention rule** | Identify the corporate schedule item, owner, trigger, minimum or maximum period, hold treatment, archive and disposal action. | Record in the existing **data/records inventory**, **retention mapping**, **privacy assessment**, **records schedule reference** and **SSP**. | **12–28 hours** |
| **3. Define authoritative, working, transient and duplicate copies** | Distinguish records from caches, indexes, reports, exports, staging, backups and convenience copies and assign appropriate lifecycles. | Capture in the **data model**, **storage map**, **architecture**, **SC-28 design**, **SyOps** and **retention mapping**. | **8–20 hours** |
| **4. Configure and protect retention rules** | Implement trigger dates, eligible states, minimum and maximum periods, archive destinations, purge actions and restricted administration. | Record in the **CM-06 configuration specification**, **workflow design**, **retention-job configuration**, **CM-05 change model** and **SSP**. | **12–32 hours** |
| **5. Implement legal and investigation hold handling** | Apply, protect, review and release holds and exclude affected records and dependent copies from disposal. | Use the existing **legal-hold process**, **incident/investigation record**, **records-management system**, **SyOps**, **role matrix** and **test evidence**. | **12–28 hours** |
| **6. Implement record, attachment, index and cache disposal** | Dispose of authoritative and dependent application copies, reconcile failures and retain non-sensitive evidence. | Evidence remains in the **data model**, **file-store design**, **search/cache design**, **purge records**, **change records** and **test reports**. | **16–48 hours** |
| **7. Control reports, exports and temporary information** | Apply short lifetimes, expiring links, staging cleanup, approved destinations and disposal after delivery or use. | Record in the **report/export specification**, **temporary-file design**, **SyOps**, **CM-06 settings**, **AU-02 event catalogue** and **test evidence**. | **8–24 hours** |
| **8. Control non-production, migration and supplier copies** | Use synthetic or masked data, approve production-derived copies, set deletion dates, protect migration staging and obtain supplier disposal evidence. | Use the existing **test-data plan**, **migration plan**, **supplier record**, **data-transfer approval**, **risk register** and **close-out evidence**. | **8–24 hours** |
| **9. Align backup and archive behaviour** | Confirm backup retention, legal holds, restored-deletion handling, archive format, integrity, readability and source disposal. | Retain evidence in the **backup design**, **recovery plan**, **archive transfer record**, **recovery test**, **records mapping** and **SSP**. | **12–28 hours** |
| **10. Preserve integrity, provenance and readability** | Retain metadata, versions, approvals, timestamps, durable formats, decryption capability and controlled amendments. | Capture controls in the **data model**, **workflow design**, **archive specification**, **SC-28 design**, **audit-history design** and **test reports**. | **8–24 hours** |
| **11. Log and monitor retention, hold and disposal activity** | Generate events for rule changes, holds, archive, purge, restoration, disposal failure, backlog and unauthorised actions. | Define events in the **SSP AU-02/SI-04/SI-12 sections** and existing **event specification**. Verify through **SIEM onboarding** and the **security test report**. | **6–16 hours** |
| **12. Test retention boundaries and legal holds** | Test trigger dates, minimum and maximum periods, held-record exclusion, release, archive, purge and authorisation. | Add cases to the normal **functional**, **security**, **records**, **operational acceptance** and **release test plans**. | **20–40 hours per major test cycle** |
| **13. Test disposal across dependent copies and recovery** | Verify record, attachment, index, cache, export and staging disposal and confirm an older backup does not silently reactivate disposed data. | Retain evidence in the **disposal test**, **recovery test**, **reconciliation report**, **operational acceptance evidence** and **CA-07 review**. | **16–36 hours per major test cycle** |
| **14. Review retained information and exceptions periodically** | Review overdue disposal, active holds, old exports, test and supplier data, archive readability, failures and continuing business need. | Retain outcomes in established **records reviews**, **privacy reviews**, **service reviews**, **CA-07 reports** or **application governance minutes**. | **8–20 hours per review** |
| **15. Integrate lifecycle requirements into change and decommissioning** | Require retention, hold, archive, backup, migration and disposal assessment for new stores, releases and retirement. | Add checks to the **change-impact assessment**, **release checklist**, **migration plan**, **operational acceptance** and **decommissioning record**. | **6–16 hours initially** |
| **16. Document and manage retention limitations** | Record missing purge, weak hold support, proprietary archive, backup conflict, supplier deletion gap or orphaned copies with compensating controls. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP SI-12 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application with established corporate retention schedules and mature managed storage services, initial application effort is commonly around **150–340 hours**.

Ongoing application effort is commonly around **6–20 hours per month**, plus records reviews, legal holds, archive activity, migrations, recovery tests and decommissioning.

A small commercial application with a simple data model and built-in retention may require less. A document-heavy, workflow-intensive, legacy or supplier-supported application with several stores, weak purge capabilities, complex holds or production data in non-production may require substantially more.

The estimates should not be added mechanically where work overlaps. SI-12 commonly shares implementation and evidence with:

- AC-02 account management;
- AC-04 information-flow enforcement;
- AC-20 use of external systems;
- AU-02 event logging;
- AU-11 audit record retention;
- CM-08 component inventory;
- MP-06 media sanitisation;
- SC-28 protection of information at rest;
- SI-04 system monitoring;
- CP backup and recovery controls;
- privacy controls;
- and CA-07 continuous monitoring.

---

## Suggested document placement

To avoid creating disconnected evidence, information-management and retention requirements should normally be distributed across established application and SDLC artefacts:

- **SSP:** SI-12 implementation approach, inherited corporate records and privacy services, information categories, retention, holds, disposal, testing and limitations.
- **ConOps or SyOps:** operational retention jobs, hold handling, archive, purge, supplier copies, failures and responsibilities.
- **Data inventory and records mapping:** information category, owner, authoritative store, retention rule, trigger, hold, archive and disposal.
- **Security and solution architecture:** authoritative and secondary stores, backup, archive, supplier and client copies.
- **Data-flow diagrams:** creation, transfer, storage, export, archive and disposal paths.
- **Data model and workflow design:** lifecycle state, closure trigger, amendment history, soft deletion, purge and hold status.
- **CM-06 configuration:** retention periods, triggers, archive destinations, purge jobs, cache expiry, report expiry and hold settings.
- **CM-05 change records:** authorised change to retention, hold or disposal rules.
- **SC-28 storage design:** protection of retained, archived, backup, temporary and supplier-held information.
- **Backup and recovery plan:** retention, hold treatment, restore of disposed records and reconciliation.
- **Archive specification:** format, metadata, integrity, readability, transfer, access and source deletion.
- **Test-data plan:** production-data approval, masking, retention and deletion.
- **Migration plan:** extracts, staging, reconciliation, acceptance and disposal.
- **Supplier records and contracts:** support copies, retention, return, deletion, subcontractors and disposal evidence.
- **AU-02 and SI-04 evidence:** hold, purge, archive, restoration, failure, backlog and unauthorised-change events.
- **Test plans and reports:** retention boundary, legal hold, purge, dependent-copy, archive and recovery tests.
- **Records, privacy and service reviews:** overdue disposal, active holds, exceptions, supplier copies and archive readability.
- **Decommissioning records:** archive transfer, residual data, backup expiry, sanitisation and disposal evidence.
- **Risk register or application addendum:** product, supplier, backup, purge, hold and archive limitations.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide records-management policy;
- authoritative corporate retention schedules;
- legal and regulatory interpretation;
- enterprise legal-hold governance;
- privacy and data-protection policy;
- corporate data-classification standards;
- enterprise archival services;
- enterprise backup and recovery platforms;
- corporate email and collaboration retention;
- central SIEM and log retention;
- enterprise media-sanitisation processes;
- secure physical media disposal;
- corporate DLP and information-protection platforms;
- supplier contractual standards;
- organisation-wide records and privacy training;
- and enterprise risk and exception governance.

The application team must still:

- identify each application information class and copy;
- map it to an approved retention requirement;
- implement triggers, holds, archive and disposal;
- control reports, exports, caches, test data and supplier copies;
- align backup and recovery behaviour;
- preserve integrity, provenance and readability;
- log and test lifecycle actions;
- verify disposal across application-controlled stores;
- integrate retention into change and decommissioning;
- and formally manage application-specific limitations.

> **Key dividing line:** the enterprise defines the authoritative retention, hold, privacy and sanitisation requirements; the application implements those requirements in every application record, copy, workflow, store, export, archive and disposal path.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, SI-12 Information Management and Retention.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, SI-12 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-88 Rev. 2, Guidelines for Media Sanitization**.
4. National Institute of Standards and Technology, **NIST Privacy Framework**, current published framework and supporting resources.
5. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, current SP 800-53 and SP 800-53A catalogues.
