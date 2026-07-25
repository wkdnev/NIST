# CM-02 Baseline Configuration — Application Actions

## Purpose

For an IT application, CM-02 means the application must establish, approve, maintain and use an **authoritative baseline configuration** for the application and its application-controlled components.

A baseline configuration is the agreed description of what an approved release consists of at a particular point in time. It is the reference used to build, deploy, operate, test, recover, compare and change the application. It should show what software, versions, components, configuration, interfaces and deployment artefacts are authorised.

This does **not** mean the application team must create baselines for corporate Microsoft Windows EUC devices, server operating systems, network devices, hypervisors, enterprise databases, identity services or other shared platforms. Those baselines remain the responsibility of the relevant enterprise service owners.

The application’s responsibility is to maintain the baseline for the **business application as a solution**, including the software products, custom code, thick-client packages, services, dependencies, schemas, integrations, application configuration and release artefacts that the application team owns, selects, packages or materially controls.

NIST defines a baseline configuration as a set of specifications for a system or configuration item that has been formally reviewed and agreed at a point in time and may thereafter be changed only through change control. NIST CM-02 requires the baseline to be developed, documented and maintained under configuration control and reviewed and updated at defined lifecycle points.

---

## 1. Define the application baseline boundary

The application should identify exactly what the baseline covers.

For a typical internal business application, this may include:

- one or more commercial software products;
- internally developed code;
- thick-client packages installed on corporate Windows EUC devices;
- browser-based presentation components;
- application and service tiers;
- APIs and integration services;
- scheduled jobs and batch processes;
- database schemas, stored procedures and application-owned database objects;
- reports and reporting definitions;
- message definitions and interface contracts;
- approved runtime and framework versions;
- major libraries and third-party dependencies;
- application configuration and feature settings;
- deployment scripts and manifests;
- certificates, secret references and service-identity references;
- application-specific firewall or network-flow requirements;
- monitoring and logging configuration;
- data-retention and clean-up configuration;
- build and release pipeline definitions;
- rollback packages and recovery artefacts; and
- supplier components or appliances that form part of the application service.

The application baseline should distinguish:

- **application-owned components** — fully described and controlled by the application;
- **dedicated enterprise components** — referenced using their enterprise asset or service identifiers;
- **shared inherited services** — referenced, but not duplicated in detail; and
- **external or interconnected systems** — identified as dependencies outside the application boundary.

## 2. Identify configuration items

The application should divide the solution into configuration items that can be meaningfully versioned, approved, changed and verified.

A configuration item may be:

- a complete commercial product;
- a thick-client installation package;
- a deployable service;
- a web application;
- an API;
- a database schema release;
- an integration package;
- a report bundle;
- a configuration bundle;
- a set of infrastructure or deployment definitions;
- a software library or dependency set;
- a signed artefact;
- a scheduled job;
- a controlled document needed to operate the release; or
- another component whose unauthorised or incorrect change could affect security or operation.

The level of granularity should be practical. A baseline should not become an unmaintainable list of every individual source file, but it must be detailed enough to identify what is approved and to detect material substitution or drift.

## 3. Establish an authoritative baseline record

The application should have one authoritative source that identifies the approved baseline for each environment and release.

The baseline record should normally include:

- application name and unique identifier;
- release or baseline identifier;
- release status;
- approval date;
- applicable environment;
- component and configuration-item names;
- approved versions;
- artefact identifiers, checksums or signatures where appropriate;
- repository or package locations;
- major dependency versions;
- approved configuration reference;
- database schema or migration version;
- interface and API version;
- deployment manifest or package reference;
- thick-client package reference;
- installation or deployment procedure;
- rollback or recovery reference;
- known approved deviations;
- accountable owner;
- approver; and
- relationship to the change or release record.

The baseline may be implemented through a controlled configuration-management database, artefact repository, release manifest, deployment pipeline, signed package catalogue, infrastructure-as-code repository or another approved tool. The SSP should summarise the method and point to the authoritative source rather than copying every technical value.

## 4. Baseline all application environments appropriately

Development, test, training, staging, recovery and production environments should have controlled baselines appropriate to their purpose.

The application should identify:

- which components and versions are intended to be the same;
- which settings are permitted to differ;
- which credentials, endpoints and data sources must differ;
- which diagnostic or test capabilities are prohibited in production;
- which lower environments may use synthetic or masked information;
- how changes are promoted between environments; and
- how the production baseline is distinguished from an interim test build.

A lower environment does not need to be identical to production, but any difference that could invalidate security, operational or recovery testing should be understood and recorded.

## 5. Include the application’s secure configuration

CM-02 and CM-06 are closely related but distinct:

- **CM-02** identifies the approved combination of components, versions and configuration that forms the application release.
- **CM-06** defines the approved security values for individual configuration settings.

The application baseline should therefore reference the applicable secure configuration specification, configuration-as-code, product workbook or deployment configuration. It should not merely state that “version 5.2” is approved if version 5.2 can be deployed with materially different security settings.

## 6. Include dependencies and supporting software

The baseline should identify dependencies that can materially affect the application’s security or operation.

This may include:

- application runtimes;
- frameworks;
- major libraries;
- plugins;
- database drivers;
- thick-client runtime prerequisites;
- browser extensions, where approved and required;
- vendor agents;
- report engines;
- messaging clients;
- integration adapters;
- cryptographic libraries;
- third-party packages; and
- supplier components.

A detailed software bill of materials may be referenced rather than duplicated. The baseline should identify the dependency record or lock file that applies to the approved release.

Unmanaged dependency change is still baseline change, even where the application’s own code has not changed.

## 7. Include database and data-model changes

Database structure and application-controlled database logic should form part of the baseline.

The application should identify:

- schema version;
- migration package;
- stored procedures and functions;
- triggers;
- application database roles;
- reference-data packages where security or operation depends on them;
- data-conversion scripts;
- rollback or restore procedure; and
- compatibility requirements between application and schema versions.

Manual production database changes that are not represented in the approved baseline should be prohibited or treated as emergency deviations requiring prompt reconciliation.

## 8. Include thick-client packages

Where the application uses a locally installed thick client, the baseline should identify:

- package name and version;
- package or software-distribution identifier;
- publisher or signing information;
- installation scope;
- required runtime;
- approved configuration;
- internal service endpoints;
- update and rollback method;
- local storage behaviour;
- prerequisites; and
- supported server-side versions.

The baseline does not need to list every corporate EUC device on which the package is installed. Device inventory and Windows build baselines remain enterprise responsibilities. The application baseline identifies the **approved package**, not the complete EUC estate.

## 9. Use reproducible and controlled builds

The application should be able to recreate the approved release from controlled inputs.

Where proportionate, this should include:

- source-code commit or tag;
- dependency lock file;
- approved compiler or build-tool version;
- build pipeline definition;
- build parameters;
- packaging scripts;
- database migration package;
- configuration references;
- signing process;
- artefact checksum;
- software bill of materials; and
- retained release artefacts.

A baseline that exists only as the current contents of a server or a developer workstation is weak because it cannot be reliably rebuilt, verified or recovered.

For commercial products, reproducibility may instead mean retaining the approved vendor installation media, patches, licences, product version, configuration export, deployment procedure and supplier evidence.

## 10. Formally approve the baseline

A release should become the authorised baseline only after appropriate review and approval.

The approval should confirm that:

- required components are included;
- versions and dependencies are known;
- security configuration has been applied;
- testing has completed;
- vulnerabilities and known defects have been treated;
- interfaces and data flows are approved;
- rollback and recovery are viable;
- evidence is complete;
- deviations are recorded; and
- the release is authorised for the intended environment.

The approver should have sufficient application and operational authority. A successful build alone does not make an artefact an approved production baseline.

## 11. Protect the baseline and its artefacts

The baseline record and release artefacts should be protected from unauthorised change, replacement and deletion.

The application should:

- restrict write access to repositories and package stores;
- use protected branches and release tags;
- separate build and approval permissions where proportionate;
- prevent ordinary administrators from silently replacing release artefacts;
- use checksums, signatures or repository integrity controls;
- retain change history;
- protect configuration and deployment definitions;
- retain prior approved releases as required for rollback and investigation; and
- log changes to baseline records and artefacts.

Where cryptographic signing is used, signing keys and signing authority should be managed through approved enterprise processes.

## 12. Change the baseline only through controlled change

Any material change to the approved application baseline should follow the standard SDLC and change process.

Examples include:

- product upgrades;
- patches;
- code changes;
- dependency changes;
- configuration changes;
- database migrations;
- integration changes;
- new reports or export functions;
- certificate or trust changes;
- addition or removal of application components;
- thick-client package changes;
- emergency fixes; and
- supplier component changes.

The change should identify:

- the previous baseline;
- the proposed change;
- security and operational impact;
- test scope;
- approval;
- deployment method;
- rollback method;
- updated baseline identifier; and
- post-deployment verification.

Configuration-only or dependency-only changes must not bypass baseline control.

## 13. Update the baseline at defined lifecycle points

The baseline should be reviewed and updated:

- when a release is approved;
- after an emergency change;
- after patching or flaw remediation that changes the release;
- after a material configuration change;
- after architecture or interface change;
- after dependency or runtime change;
- after recovery or rebuild where the deployed state may have changed;
- when a component is retired or replaced;
- when unsupported software is removed;
- when a supplier changes its supported configuration; and
- periodically to confirm continued accuracy.

The baseline should be current enough to support recovery, incident response, vulnerability assessment and change impact analysis.

## 14. Verify the deployed state against the baseline

The application should confirm that each deployed environment matches its approved baseline.

Verification may use:

- deployment-pipeline records;
- package-management queries;
- application version endpoints;
- checksums or digital signatures;
- configuration comparison;
- database schema-version queries;
- software-composition or dependency reports;
- product administration exports;
- script-based checks;
- artefact repository comparison; or
- controlled manual review for small or legacy applications.

Verification should cover all relevant nodes and tiers. Checking only one server is insufficient where multiple instances could differ.

## 15. Detect and reconcile baseline drift

The application should identify unapproved differences between the baseline and the actual deployed state.

Examples include:

- a server running an older application build;
- a thick-client package not matching the approved release;
- a manually replaced library;
- an unrecorded database change;
- an unexpected plugin;
- a different configuration bundle on one node;
- an integration endpoint changed outside release control;
- debugging components left installed;
- a retired package still deployed; or
- an emergency fix not incorporated into the baseline.

The application should investigate the difference, determine whether it is authorised, correct it or update the baseline through change control, and record the outcome.

## 16. Maintain rollback and recovery baselines

The application should retain enough information to restore a known, approved and secure state.

This should include, where applicable:

- previous approved release artefacts;
- database rollback or restoration procedures;
- configuration backups;
- required certificates and key references;
- compatible dependency versions;
- installation media;
- deployment scripts;
- recovery order across tiers;
- verification checks; and
- recovery test evidence.

Recovery should not result in an obsolete, unsupported or insecure application state without an explicit risk decision and follow-on remediation plan.

## 17. Retire obsolete baseline components

When a component or release is retired, the application should ensure that it is:

- removed from active deployment;
- removed from normal distribution channels;
- no longer presented as approved;
- removed from active integration and scanning scope only after verified removal;
- retained only where required for evidence, recovery or records purposes;
- protected from accidental redeployment; and
- reflected accurately in the component inventory and support documentation.

Old thick-client packages should not remain available in software-distribution catalogues as selectable alternatives unless their continued use is approved.

## 18. Link the baseline to other application controls

The application baseline should support and remain consistent with:

- **CM-06** — approved configuration settings;
- **CM-08** — system component inventory;
- **CM-03/CM-05** — controlled changes and access to make changes;
- **CM-07** — least functionality;
- **RA-05** — vulnerability and dependency scanning scope;
- **SI-02** — flaw remediation;
- **SI-07** — software and information integrity;
- **SA-11** — developer testing and evaluation;
- **CA-07** — continuous monitoring;
- **CP controls** — recovery and restoration; and
- **AU-02/SI-04** — logging and monitoring of baseline-related events.

The baseline should not conflict with the component inventory, architecture, release record or actual deployed state.

## 19. Manage baseline limitations and deviations

Where a legacy, commercial or supplier-controlled product cannot support a complete or reproducible baseline, the application should record:

- what cannot be identified or reproduced;
- the affected component or environment;
- the expected standard;
- the available evidence;
- the resulting risk;
- compensating controls;
- monitoring;
- owner;
- approval;
- upgrade, replacement or retirement plan; and
- review or expiry date.

A screenshot of an administration screen or a statement that “the supplier manages it” is rarely sufficient on its own.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses an established corporate SDLC, source or artefact repositories, change control and deployment services. They exclude enterprise infrastructure engineering, procurement and major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the application baseline boundary** | Identify the software products, custom components, thick clients, services, schemas, integrations, dependencies and application configuration that form the business application. Distinguish inherited enterprise services. | Summarise the boundary in the **SSP CM-02 statement** and align it with the existing **architecture**, **system context diagram**, **ConOps** or **SyOps**. | **4–8 hours** |
| **2. Identify and version the configuration items** | Divide the application into practical deployable or controllable items and assign each an authoritative name and version or identifier. | Record configuration items in the existing **component inventory**, **release manifest**, **configuration-management record** or **solution design** referenced by the SSP. | **6–16 hours** |
| **3. Establish the authoritative baseline record** | Create one controlled release record showing approved components, versions, dependencies, configuration references, schema version, artefacts, environment and approval. | Use the established **release record**, **artefact repository**, **deployment manifest**, **CMDB/application register** or **release evidence pack**. The **SSP** points to this source. | **8–20 hours** |
| **4. Link the baseline to secure configuration** | Reference the approved CM-06 settings, configuration-as-code, deployment configuration or product hardening workbook that applies to the release. | Record the link in the **release manifest**, **security design**, **SyOps** and **SSP CM-02/CM-06 statements** rather than duplicating the settings. | **3–8 hours** |
| **5. Include dependencies and database changes** | Capture material libraries, runtimes, plugins, database schema and migration versions through lock files, SBOMs, manifests or controlled release records. | Retain these in the normal **repository**, **SBOM**, **dependency report**, **database release package** and **release evidence pack**. | **8–20 hours** |
| **6. Baseline thick-client packages where applicable** | Record the approved package, version, signing/publisher information, prerequisites, configuration, update path and compatible server release. | Use the existing **software-distribution package record**, **release manifest**, **deployment design** and **test report**. Reference it from the SSP. | **4–12 hours** |
| **7. Build or package from controlled inputs** | Use controlled source, dependencies, build definitions and packaging scripts, or retain approved supplier media and configuration exports for commercial products. | Evidence sits in the normal **source repository**, **pipeline history**, **artefact repository**, **supplier release evidence** and **release pack**. | **12–40 hours** |
| **8. Formally review and approve the production baseline** | Confirm testing, security configuration, known findings, interfaces, rollback and deployment readiness before designating the release as approved. | Record approval in the established **release approval**, **change record**, **operational acceptance record** or **release evidence pack**. | **4–10 hours per release** |
| **9. Protect baseline records and artefacts** | Restrict repository and package-store modification, use protected release tags, retain history and use checksums or signatures where proportionate. | Describe the control in the **SSP**, **SDLC**, **repository configuration** or **release process**; retain access and integrity evidence in normal platform records. | **6–16 hours initially** |
| **10. Verify deployment against the approved baseline** | Check application, package, dependency, configuration and schema versions after deployment across all relevant tiers and nodes. | Add checks to the normal **deployment plan**, **release checklist**, **operational acceptance test** or **post-implementation review**. | **4–12 hours per release** |
| **11. Detect and reconcile drift** | Compare the deployed state with the approved release periodically or through automation, investigate differences and correct or approve them. | Record results in existing **service reviews**, **configuration reports**, **change tickets**, **continuous-monitoring evidence** or the **risk register**. | **6–20 hours initially; 2–8 hours per review** |
| **12. Maintain rollback and recovery information** | Retain previous approved artefacts, compatible schemas, configuration and deployment instructions and confirm that a known secure state can be restored. | Integrate evidence into the existing **rollback plan**, **recovery plan**, **SyOps**, **release pack** and **recovery test report**. | **8–20 hours initially; 4–12 hours per recovery test** |
| **13. Retire superseded components and releases** | Remove obsolete packages from active deployment and distribution, prevent accidental reuse and update inventory and support records. | Record within normal **decommissioning**, **change**, **software-distribution**, **component inventory** and **service-management records**. | **3–8 hours per retirement** |
| **14. Review and update the baseline after material change** | Reissue or update the baseline after releases, emergency fixes, dependency changes, patches, schema changes or material configuration changes. | Use the normal **change and release process**, with the updated **release manifest**, **baseline identifier** and **SSP/addendum update** where material. | **3–8 hours per update** |

### Indicative total

For a typical internal application with established repositories and release processes, initial application effort is commonly around **90–220 hours**. A simple commercial application with a single server component may require less. A multi-product engineering application, thick-client estate, complex integrations, poorly controlled legacy build or extensive supplier constraints may require substantially more.

The estimates should not be added mechanically where activities overlap. Component inventory, secure configuration, build engineering, release management and recovery planning often produce shared evidence.

---

## Suggested document placement

To avoid creating disconnected evidence, baseline information should normally be distributed across existing application and SDLC artefacts:

- **SSP:** CM-02 implementation approach, application baseline boundary, inherited enterprise baselines, authoritative evidence source, review frequency and limitations.
- **ConOps or SyOps:** operational component relationships, environment use, deployment, recovery, rollback and support responsibilities.
- **Security or solution architecture:** application boundary, tiers, components, trust relationships and inherited services.
- **Component inventory:** authoritative list of application components, ownership, versions and lifecycle status.
- **Release manifest or release evidence pack:** approved release identifier, component versions, artefacts, dependencies, configuration references and approvals.
- **Source and artefact repositories:** controlled source, release tags, build outputs, packages, checksums, signatures and retained previous versions.
- **SBOM or dependency record:** approved dependency set for the release.
- **Database release package:** schema version, migrations, stored logic, reference data and rollback instructions.
- **Build and deployment definitions:** repeatable build, packaging, configuration and deployment method.
- **Test plans and reports:** evidence that the baseline was tested as an integrated release.
- **Change and release records:** approval to move from one baseline to the next.
- **Operational acceptance and post-implementation review:** confirmation that the deployed state matches the approved baseline.
- **Recovery plan and test report:** evidence that a known approved state can be restored.
- **Risk register or application addendum:** incomplete, non-reproducible, supplier-controlled or otherwise non-standard baseline arrangements.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- corporate Microsoft Windows EUC baseline builds;
- server operating-system baselines;
- network-device and firewall baselines;
- hypervisor and virtualisation baselines;
- enterprise database-platform baselines;
- corporate identity, MFA and directory baselines;
- VPN gateway and remote-access baselines;
- endpoint protection and EDR baselines;
- shared middleware and managed-platform baselines;
- enterprise PKI, key-management and secrets-platform baselines;
- corporate backup-platform configuration;
- enterprise configuration-management policy and tooling;
- infrastructure asset inventory;
- enterprise vulnerability and compliance scanning; and
- corporate change, release and service-management governance.

The application team must still identify which inherited platforms and services its baseline depends upon, record compatible versions or service references where necessary, and ensure that the application baseline does not undermine the inherited controls.

> **Key dividing line:** the enterprise maintains the approved baseline for the shared platforms; the application maintains the approved baseline for the complete business application release that runs on and connects to those platforms.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, CM-02 Baseline Configuration.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, CM-02 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems**.
4. National Institute of Standards and Technology, **NIST SP 800-70 Rev. 5, National Checklist Program for IT Products: Guidelines for Checklist Users and Developers**.
5. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool — baseline configuration glossary definition**.
