# SI-03 Malicious Code Protection — Application Actions

## Purpose

For an IT application, SI-03 means the application must prevent, detect, contain and support the removal of malicious code that could enter, execute within, alter, or be distributed by the application.

The enterprise may provide endpoint protection, EDR, malware scanning platforms, email and web filtering, network controls, hardened Microsoft Windows EUC devices, server operating-system protection, central threat intelligence, SOC monitoring and incident response. Those controls are inherited.

The application remains responsible for the malicious-code risks created by its own design and business functions, including:

- uploaded files and attachments;
- imported datasets and archives;
- thick-client installers and updates;
- application packages and dependencies;
- scripts, macros, plugins and extensions;
- reports and generated files;
- APIs and integrations;
- content preview and conversion;
- supplier software;
- build and release artefacts;
- temporary storage and quarantine;
- application-controlled execution paths; and
- application-specific handling when scanning is unavailable or detects a threat.

NIST SI-03 requires malicious-code protection mechanisms at designated entry and exit points, updates to those mechanisms, periodic and real-time scanning as appropriate, action when malicious code is detected, and controls that prevent users from bypassing protection. NIST SP 800-83 Rev. 1 recommends layered malware prevention, detection, containment and incident-response measures. NIST’s Secure Software Development Framework also supports protecting software from tampering and verifying the integrity and provenance of releases.

> **Core principle:** the enterprise provides common malware-defence capabilities; the application must ensure that its own files, packages, interfaces and processing paths actually use those capabilities and behave safely when malicious content is suspected or found.

---

## 1. Identify application malicious-code entry and exit points

The application should identify every path through which code or active content could enter, execute, persist or leave the application.

This normally includes:

- file and attachment upload;
- bulk import;
- compressed archives;
- document preview;
- image or media processing;
- report templates;
- spreadsheet and macro-enabled content;
- scripts;
- plugins and extensions;
- software packages;
- thick-client installation and update packages;
- APIs;
- message queues;
- integration feeds;
- removable media workflows;
- database imports;
- supplier support packages;
- build dependencies;
- code repositories;
- artefact repositories;
- exported files;
- generated reports;
- downloaded attachments; and
- files transferred to other internal applications.

The application should distinguish:

- user-controlled content;
- supplier-controlled content;
- trusted internal content;
- generated content;
- executable content;
- active content;
- data-only content; and
- content that becomes executable after parsing, conversion or extraction.

## 2. Perform a malicious-code threat assessment

The application should assess how malicious code could affect its architecture and business process.

The assessment should consider:

- whether users upload or exchange files;
- whether files are opened automatically;
- whether the application converts, previews or extracts content;
- whether macros or scripts are permitted;
- whether the application executes user-supplied expressions;
- whether archives are unpacked;
- whether plugins can be installed;
- whether the application generates files used elsewhere;
- whether thick clients update automatically;
- whether supplier packages are introduced;
- whether build tools download dependencies;
- whether service accounts can execute code;
- whether temporary locations are executable;
- whether malware could spread to connected systems;
- whether restricted information could be exfiltrated; and
- whether malicious content could impair availability or data integrity.

The threat assessment should drive the scanning points, allowed content types, quarantine behaviour and operational response.

## 3. Use the approved enterprise malicious-code protection services

The application should integrate with approved enterprise scanning or content-inspection services where malicious content may enter or leave.

This may include:

- endpoint anti-malware;
- EDR;
- server anti-malware;
- file-scanning APIs;
- secure file-transfer scanning;
- email or messaging scanning;
- web or proxy scanning;
- storage scanning;
- software-distribution scanning;
- artefact-repository scanning;
- sandboxing;
- content-disarm and reconstruction;
- malware analysis;
- application allow-listing; and
- supplier package inspection.

The application should not create an unmanaged, application-specific anti-malware service where an approved enterprise capability can meet the requirement.

The application team must still confirm:

- which service is used;
- where it is invoked;
- what content is in scope;
- what file or object size limits apply;
- what result states are returned;
- how failures are handled;
- what evidence is retained; and
- who owns operational support.

## 4. Scan content before trusted use

User- or supplier-controlled content should be scanned before the application:

- opens it;
- renders it;
- parses it deeply;
- extracts it;
- imports it;
- makes it available to another user;
- stores it in a trusted repository;
- sends it to another system;
- executes it; or
- treats it as an approved application artefact.

Where immediate pre-processing is technically unavoidable, the content should remain isolated and untrusted until scanning and validation succeed.

A file being stored on a protected server does not mean it has been scanned safely.

## 5. Scan at relevant entry and exit points

Scanning should occur at the point that best prevents malicious content from entering or propagating.

Depending on the application, this may include:

- upload gateway;
- import service;
- API ingestion point;
- message consumer;
- staging area;
- file share;
- attachment service;
- content-conversion service;
- report generation;
- export or download;
- thick-client packaging;
- build pipeline;
- artefact promotion;
- software-distribution publication; and
- transfer to another application.

Scanning once at an earlier stage may be insufficient if the content is subsequently transformed, extracted, combined or generated into a new potentially active file.

## 6. Restrict accepted file and content types

The application should permit only content types required for the approved business process.

It should:

- use an allow-list of permitted formats;
- validate actual file structure and content, not only the extension;
- compare extension, media type and file signature;
- reject unsupported or ambiguous formats;
- restrict macro-enabled documents;
- restrict executable and script formats;
- restrict password-protected or encrypted archives unless an approved process exists;
- control nested archives;
- limit archive depth and expanded size;
- reject polyglot or malformed files where detectable;
- restrict files containing active external links or embedded objects where appropriate;
- define maximum file size and quantity; and
- review the allow-list after business or threat changes.

General-purpose file upload should not be enabled where only a small number of document formats are required.

## 7. Treat active content as higher risk

The application should treat the following as higher-risk than ordinary data:

- executables;
- scripts;
- macros;
- embedded objects;
- browser-active content;
- document templates;
- code snippets;
- formulas or expressions capable of execution;
- plugins;
- dynamic libraries;
- report extensions;
- notebook files;
- archive-contained executables; and
- files that trigger external fetches.

Where active content is unnecessary, it should be prohibited.

Where it is necessary, the application should apply:

- stronger authorisation;
- approved publishers or signatures;
- sandboxing;
- restricted execution;
- least privilege;
- content inspection;
- logging;
- integrity checking;
- version control;
- approval workflow; and
- periodic review.

## 8. Isolate untrusted content

Untrusted or unscanned content should be stored in a location that prevents ordinary access or execution.

The application should:

- use a dedicated staging or quarantine area;
- prevent execution from upload and temporary directories;
- use restrictive permissions;
- generate server-side object identifiers rather than trusting filenames;
- prevent path traversal;
- separate content from application code and configuration;
- prevent direct web serving before approval;
- restrict access to scanning and processing identities;
- expire abandoned content;
- prevent accidental backup or replication into trusted stores where inappropriate; and
- record the object’s current trust state.

A “pending scan” file should never be available through an ordinary download path.

## 9. Define safe scan-result handling

The application should handle all relevant result states explicitly.

Typical states include:

- clean;
- malicious;
- suspicious;
- potentially unwanted;
- encrypted or unscannable;
- unsupported format;
- scan timeout;
- scanner unavailable;
- scan error;
- incomplete scan; and
- policy blocked.

For each state, the application should define whether to:

- accept;
- quarantine;
- reject;
- delete;
- hold for specialist review;
- notify the user;
- notify security operations;
- restrict distribution;
- retry; or
- stop processing.

The application should not interpret “scanner unavailable” or “unknown” as “clean”.

## 10. Fail safely when scanning is unavailable

Where scanning is required, the application should fail closed or use a documented risk-based degraded mode.

Appropriate behaviour may include:

- reject the upload;
- retain it in inaccessible quarantine;
- queue it securely;
- suspend the import;
- prevent download;
- stop promotion to a trusted repository;
- alert support;
- retry within defined limits; or
- invoke an approved manual review.

The application should define:

- how long content may remain pending;
- retry frequency;
- storage limits;
- user messaging;
- operational escalation;
- recovery;
- disposal of abandoned content; and
- emergency override approval.

Silent bypass of scanning is unacceptable.

## 11. Prevent users and administrators from bypassing protection

The application should prevent bypass through:

- alternate upload routes;
- direct file-share access;
- APIs that omit scanning;
- batch interfaces;
- administrator-only import tools;
- thick-client local copying;
- database insertion;
- message queues;
- support consoles;
- recovery functions;
- disabled feature flags;
- extension changes;
- oversized files;
- encrypted archives; or
- manual movement from quarantine.

Any authorised override should be:

- exceptional;
- attributable;
- time-limited;
- approved;
- logged;
- reviewed; and
- accompanied by alternative controls.

## 12. Protect file preview, conversion and extraction

Preview and conversion services can be attacked even when content is never executed directly by a user.

The application should:

- use supported parsers and converters;
- run them with minimal privileges;
- isolate them from application code and sensitive data;
- restrict network access;
- set CPU, memory and time limits;
- limit archive expansion;
- patch them promptly;
- scan input and, where relevant, output;
- prevent access to local paths and credentials;
- prevent server-side request forgery;
- remove temporary files;
- log failures and suspicious behaviour; and
- treat parser crashes or anomalous resource consumption as security-relevant.

Complex file parsing should not run inside a highly privileged core application process where isolation is practical.

## 13. Protect generated and exported content

Applications can generate malicious or dangerous output unintentionally or after stored data has been manipulated.

The application should consider:

- formula injection in spreadsheets;
- active content in generated documents;
- unsafe hyperlinks;
- embedded scripts;
- malicious filenames;
- path manipulation;
- dangerous archive content;
- executable report templates;
- corrupted exports;
- files containing unauthorised embedded objects; and
- stored content that becomes active when exported.

Generated files should be safely encoded, use controlled templates, receive appropriate scanning where risk warrants it, and preserve access restrictions.

## 14. Protect thick-client installers and updates

For locally installed software, the application should ensure that installation and update packages are:

- obtained from an approved source;
- versioned;
- integrity-checked;
- digitally signed where required;
- scanned before publication;
- stored in an approved artefact or software-distribution repository;
- protected from unauthorised replacement;
- tested before deployment;
- distributed through the corporate software-distribution process;
- associated with the approved baseline;
- removed or superseded when obsolete; and
- capable of safe rollback where required.

The thick client should not download or execute updates from an unapproved external location.

The enterprise owns the Windows EUC and distribution platform; the application owns the integrity and approval of its package.

## 15. Protect application build and release artefacts

Malicious code can enter through the software supply chain.

The application should protect:

- source repositories;
- build scripts;
- pipeline definitions;
- dependencies;
- package managers;
- plugins;
- compilers and build tools;
- artefact repositories;
- signing processes;
- release manifests;
- deployment scripts; and
- supplier-delivered packages.

Controls should include, where proportionate:

- approved repositories;
- protected branches;
- peer review;
- dependency pinning;
- software-composition analysis;
- secret detection;
- malware or artefact scanning;
- integrity hashes;
- signed releases;
- provenance records;
- separation of build and approval;
- controlled promotion; and
- retention of approved artefacts.

An artefact that passed functional testing should not be assumed free of malicious code.

## 16. Assess supplier and commercial software

For supplier-developed software, the application should obtain and assess available evidence such as:

- supplier security-development practices;
- release notes;
- hashes or signatures;
- software bill of materials;
- vulnerability history;
- secure update process;
- malware-scanning attestations;
- incident-notification commitments;
- package provenance;
- support status;
- independent assessment; and
- remediation commitments.

The application should still:

- scan delivered packages;
- verify publisher and integrity;
- test installation;
- inspect unexpected components;
- restrict supplier support access;
- monitor advisories; and
- validate updates before deployment.

Supplier assurance does not remove the need for local verification.

## 17. Control scripts, macros, plugins and extensions

Where the application supports extensibility, it should:

- disable extension mechanisms if not required;
- restrict who can add or change extensions;
- use an approved catalogue;
- require code review;
- scan and integrity-check packages;
- sign approved extensions where supported;
- restrict available APIs;
- prevent unrestricted operating-system command execution;
- restrict network access;
- prevent access to secrets;
- separate development and production;
- log installation and execution;
- version and baseline extensions;
- remove obsolete extensions; and
- provide rollback.

User-contributed code should not move directly into production.

## 18. Control application execution paths

The application should prevent malicious content from becoming executable through configuration or storage mistakes.

It should:

- separate code and data locations;
- prevent execution from upload, cache and temporary directories;
- restrict dynamic loading paths;
- prevent user-controlled library or module search paths;
- avoid executing commands constructed from user input;
- use safe process invocation;
- avoid unsafe deserialisation;
- restrict interpreter access;
- protect scheduled-job definitions;
- restrict writable plugin directories;
- prevent users from changing executable configuration;
- use least-privileged process identities; and
- apply application allow-listing where appropriate.

## 19. Update malicious-code protection dependencies

The application should ensure that application-owned scanning integrations, engines, libraries, policies and signatures remain supported and current.

This may include:

- scanner API versions;
- file-type detection libraries;
- parsing and conversion engines;
- sandbox connectors;
- malware-analysis rules;
- content-disarm policies;
- application allow-lists;
- file-validation libraries; and
- supplier scanning components.

Enterprise security services own their signature and engine updates. The application owns compatibility with the current service and must not remain dependent on an obsolete integration.

## 20. Log malicious-code protection activity

The application should record, as applicable:

- content submission;
- scan request;
- result;
- policy decision;
- object identifier;
- file type and size;
- user or service identity;
- application component;
- timestamp;
- quarantine action;
- release from quarantine;
- override;
- scanner error;
- scanner unavailability;
- repeated suspicious submissions;
- package or artefact rejection;
- administrative configuration changes; and
- notification or incident reference.

Logs should not unnecessarily store malicious payloads, complete file content, credentials or sensitive business information.

## 21. Alert and escalate meaningful detections

The application should define when a detection requires:

- user notification;
- support action;
- security operations alert;
- incident creation;
- supplier escalation;
- temporary feature restriction;
- identity suspension;
- integration isolation;
- package withdrawal; or
- wider search for related content.

Factors may include:

- confirmed malware;
- repeated suspicious submissions;
- privileged or supplier source;
- production package contamination;
- execution evidence;
- spread to other users or systems;
- credential theft;
- restricted information exposure;
- evasion attempts;
- scanner bypass; and
- compromise of the build or release process.

## 22. Preserve evidence safely

When malicious code is detected, the application should support evidence preservation without exposing users or ordinary administrators.

This may include:

- file hash;
- scanner result;
- object metadata;
- source identity;
- transaction context;
- quarantine reference;
- package version;
- build provenance;
- relevant logs;
- affected records;
- integration path; and
- timestamps.

Actual malicious samples should be retained only in approved restricted analysis or quarantine services and handled under enterprise incident and evidence procedures.

## 23. Support containment and remediation

The application should have safe options to:

- quarantine or delete malicious content;
- block the submitting identity;
- disable an upload or import path;
- disable a compromised integration;
- withdraw a thick-client package;
- revoke a package or certificate;
- remove a malicious plugin;
- stop a scheduled job;
- disable a preview or conversion service;
- invalidate generated files;
- restore clean content;
- rebuild from an approved baseline;
- patch the vulnerable parser or dependency;
- increase monitoring; and
- notify affected downstream systems.

Actions should be coordinated through the enterprise incident and change processes.

## 24. Retest after remediation

After correction, the application should verify that:

- the malicious content is no longer accepted or executed;
- all affected copies are removed or controlled;
- scanner integration works;
- bypass paths are closed;
- updated packages are deployed;
- quarantined content remains inaccessible;
- downstream systems are addressed;
- logging and alerting operate;
- no unacceptable regression exists; and
- baseline, inventory and documentation are updated.

Closure should include evidence, not merely a statement that the file was deleted.

## 25. Test malicious-code controls

Testing should include:

- approved harmless anti-malware test files where permitted;
- clean files;
- blocked file types;
- mismatched extensions and signatures;
- encrypted archives;
- nested archives;
- oversized files;
- scanner timeout;
- scanner unavailability;
- quarantine access;
- API and batch bypass attempts;
- thick-client package verification;
- plugin installation controls;
- generated-file safety;
- parser failure;
- event forwarding;
- alerting;
- user messaging; and
- clean-up of temporary content.

Testing must follow enterprise rules and must not introduce live malware into production or corporate environments.

## 26. Review controls after change

The application should reassess malicious-code protection after:

- new file type;
- new upload or import route;
- new export format;
- new API;
- new plugin capability;
- new parser or converter;
- new thick-client package;
- product upgrade;
- new supplier;
- dependency change;
- build-pipeline change;
- scanner-service change;
- security incident;
- penetration-test finding; or
- newly active malware campaign relevant to the application.

## 27. Manage limitations and exceptions

Where the application cannot scan, isolate or safely process particular content, it should record:

- the affected file type, interface or component;
- the required protection;
- the technical limitation;
- the threat and business need;
- alternative controls;
- permitted users;
- volume limits;
- manual review;
- monitoring;
- incident response;
- supplier dependency;
- owner;
- approval;
- remediation or replacement plan; and
- review or expiry date.

The exception should be documented in the application addendum or risk process.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses enterprise endpoint protection, file-scanning, SIEM, software-distribution, artefact repositories and incident-response services. They exclude enterprise platform engineering, supplier redevelopment and major remediation.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify malicious-code entry, processing and exit points** | Review uploads, imports, files, archives, APIs, integrations, thick-client packages, plugins, reports and build artefacts to identify where malicious code could enter or spread. | Summarise the scope in the **SSP SI-03 statement** and link it to the existing **architecture**, **data-flow diagrams**, **interface specifications**, **ConOps** or **SyOps**. | **6–12 hours** |
| **2. Define permitted content and active-content rules** | Establish an allow-list of required file and content types and prohibit or tightly restrict executables, macros, scripts, plugins and encrypted archives. | Record requirements in the **security design**, **business requirements**, **file-handling specification**, **SyOps** and **SSP**. | **6–16 hours** |
| **3. Integrate approved malware-scanning services** | Invoke the enterprise scanner or approved content-inspection service at the relevant upload, import, artefact or transfer point. | Describe the integration in the **security design**, **interface control document**, **deployment design** and **SSP**. Retain implementation evidence in the normal **release pack**. | **12–32 hours** |
| **4. Isolate untrusted and pending content** | Store unscanned or suspicious content in a non-executable, access-restricted staging or quarantine location until a trusted decision is available. | Record the design in the **architecture**, **storage design**, **SyOps** and **SSP SC-28/SI-03 sections**. Verify through the normal **security test report**. | **8–20 hours** |
| **5. Define safe result and failure handling** | Explicitly handle clean, malicious, suspicious, unsupported, encrypted, timeout and scanner-unavailable states; do not treat unknown as clean. | Record decision logic in the **application design**, **SyOps**, **error-handling specification** and **SSP**. Verify it in the **system, resilience and security test report**. | **8–20 hours** |
| **6. Prevent bypass across all interfaces** | Ensure browser, thick-client, API, batch, support and administrative paths use the same required scanning and quarantine controls. | Describe enforcement points in the **architecture** and **interface specifications**. Retain negative bypass tests in the **security test report**. | **12–28 hours** |
| **7. Protect preview, conversion, extraction and generated content** | Run risky parsers with least privilege and resource limits, scan appropriate input/output, use safe templates and clean temporary files. | Capture controls in the **technical design**, **file-processing design**, **CM-06 configuration**, **SyOps** and **test report**. | **8–24 hours** |
| **8. Protect thick-client and release packages** | Verify source, version, signatures and hashes, scan packages, store them in approved repositories and distribute through corporate software management. | Use the existing **CM-02 release baseline**, **artefact repository**, **software-distribution package record**, **release evidence pack** and **installation test report**. | **6–16 hours per package or major release** |
| **9. Protect dependencies, plugins and build artefacts** | Use approved repositories, review changes, scan dependencies and artefacts, detect secrets, verify integrity and control promotion. | Evidence sits in the normal **source repository**, **pipeline history**, **SCA report**, **artefact scan**, **SBOM**, **release manifest** and **SA-11 test evidence**. | **12–32 hours initially** |
| **10. Log and alert on detections, failures and overrides** | Generate events for scan outcomes, quarantine, bypass attempts, scanner failure, overrides and contaminated packages and send relevant events to central monitoring. | Define events in the **SSP AU-02/SI-04/SI-03 sections** and existing **event specification**. Verify through the **SIEM onboarding** and **security test report**. | **6–16 hours** |
| **11. Define containment and incident actions** | Establish how to quarantine, block identities, disable interfaces, withdraw packages, revoke credentials and notify downstream systems. | Record actions in the **SyOps**, **incident-response annex**, **support runbook**, **IR-05 section** and **recovery/change procedures**. | **6–12 hours** |
| **12. Test malicious-code controls safely** | Use approved harmless test artefacts and failure simulations to verify scanning, rejection, quarantine, bypass prevention, event generation and recovery. | Add cases to the normal **security test plan** and retain outcomes, defects and retests in the **test report** and **release evidence pack**. | **12–24 hours per test cycle** |
| **13. Review protection after relevant changes** | Reassess when file types, interfaces, parsers, packages, suppliers, dependencies or scanner services change. | Add the review to the standard **change-impact assessment**, **security design review**, **release checklist** or **post-implementation review**. | **3–8 hours per material change** |
| **14. Formally manage unsupported scanning or other limitations** | Document unscannable content, supplier restrictions, unavailable inspection or required active content with compensating controls and a remediation plan. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP SI-03 section**. | **4–10 hours per exception** |

### Indicative total

For a typical internal application with ordinary file upload and established enterprise scanning services, initial application effort is commonly around **90–210 hours**.

A simple application that accepts no files, scripts, plugins or externally supplied packages may require much less. A document-management, engineering, collaboration or integration-heavy application with complex formats, archives, thick clients, custom plugins or supplier constraints may require substantially more.

The estimates should not be added mechanically where activities overlap. SI-03 should reuse evidence from CM-02, CM-06, CM-07, CM-08, RA-05, SI-02, SI-07, SI-10, SA-11, AU-02, SI-04 and IR-05.

---

## Suggested document placement

To avoid creating disconnected evidence, malicious-code protection information should normally be distributed across established application and SDLC artefacts:

- **SSP:** SI-03 implementation approach, inherited enterprise protection, application entry and exit points, scanner services, failure behaviour, ownership and limitations.
- **ConOps or SyOps:** operational scanning, quarantine, support, user messaging, failure handling, containment and supplier responsibilities.
- **Security architecture:** scanning points, staging and quarantine zones, trust transitions, parser isolation, artefact flows and event forwarding.
- **Data-flow diagrams:** uploaded, imported, generated, exported and transferred content.
- **Business and security requirements:** allowed file types, active-content restrictions, scanning, failure behaviour and user permissions.
- **Interface control documents:** scanning requirements for APIs, messages, batch feeds and downstream transfers.
- **File-processing or content-handling design:** validation, scanning, extraction, conversion, temporary storage and clean-up.
- **CM-06 configuration specification:** enabled file types, size limits, scanner endpoints, timeouts, quarantine and feature settings.
- **CM-02 baseline and release manifest:** approved packages, plugins, scanning integration and release artefacts.
- **CM-08 component inventory:** parsers, converters, plugins, scanning components, libraries and supplier products.
- **Source, build and artefact repositories:** controlled inputs, scans, integrity information, signatures and provenance.
- **SBOM and dependency records:** approved component and dependency set.
- **Thick-client packaging records:** approved package, integrity, malware scan, signing and software-distribution evidence.
- **AU-02 and SI-04 specifications:** detection, failure, quarantine, override and alert events.
- **IR-05 incident procedures:** escalation, evidence, containment and eradication actions.
- **Security test plans and reports:** safe test artefacts, failure simulations, bypass testing and retest evidence.
- **Release and operational acceptance records:** confirmation that scanning and quarantine work for the released version.
- **Risk register or application addendum:** unsupported formats, encrypted content, supplier constraints, active-content exceptions and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- endpoint anti-malware and EDR on corporate Windows EUC devices;
- server anti-malware and EDR;
- enterprise malware signatures and engine updates;
- corporate email and web filtering;
- network security monitoring;
- enterprise file-scanning and sandbox platforms;
- central software-distribution platform protection;
- enterprise artefact-repository protection where provided;
- central threat intelligence;
- SIEM, SOC and malware incident handling;
- enterprise application allow-listing platforms;
- operating-system execution and device-control policies;
- removable-media protection;
- corporate forensic and malware-analysis capability;
- enterprise quarantine and evidence-handling services; and
- organisation-wide malicious-code policy and exception governance.

The application team must still:

- identify its own entry and exit points;
- restrict accepted content;
- invoke approved scanning services;
- isolate untrusted content;
- handle unknown and failure states safely;
- prevent bypass;
- protect thick-client and release packages;
- control plugins, scripts and dependencies;
- provide useful logging and alerting;
- support containment and remediation; and
- maintain evidence that the application-specific protection works.

> **Key dividing line:** the enterprise operates the shared malicious-code defence capabilities; the application ensures that every relevant application path, file, package and processing function actually uses those capabilities and fails safely when malicious content is detected or cannot be assessed.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, SI-03 Malicious Code Protection.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, SI-03 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-83 Rev. 1, Guide to Malware Incident Prevention and Handling for Desktops and Laptops**.
4. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1: Recommendations for Mitigating the Risk of Software Vulnerabilities**.
5. National Institute of Standards and Technology, **NIST SP 800-161 Rev. 1, Cybersecurity Supply Chain Risk Management Practices for Systems and Organizations**.
