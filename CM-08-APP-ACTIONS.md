# CM-08 System Component Inventory — Application Actions

## Purpose

For an IT application, CM-08 means the application must maintain an **accurate, current and sufficiently detailed inventory of the components that make up the application**, including where they are used, who owns them, what version is approved and how they relate to the application’s authorised baseline.

The enterprise may provide:

- a corporate configuration management database (CMDB);
- endpoint, server and network discovery;
- enterprise asset-management tooling;
- cloud, virtualisation or infrastructure inventories;
- corporate software-distribution records;
- vulnerability-management platforms;
- software-licence management;
- enterprise procurement and supplier registers;
- central identity, certificate and secrets inventories; and
- organisation-wide asset and configuration policy.

Those services are inherited.

The application remains responsible for ensuring that the enterprise records are supplemented with the application-specific detail needed to understand and control the complete business solution. This includes:

- custom and commercial application software;
- thick-client packages;
- web, service and data tiers;
- application-owned databases and schemas;
- APIs, integrations, queues and file-transfer components;
- libraries, dependencies, plugins and extensions;
- application containers and images;
- scheduled jobs and automation;
- reports, templates and executable business rules;
- application-specific service identities;
- certificates and secret references;
- build and deployment artefacts;
- supplier-delivered modules;
- non-production and recovery components;
- approved versions, owners, support status and relationships; and
- components that cannot be discovered reliably by enterprise tooling.

NIST CM-08 requires an inventory of system components that accurately reflects the system, includes all components within the system, avoids duplicate accounting, provides an appropriate level of granularity and includes information needed for component accountability. NIST SP 800-128 treats an accurate component inventory as a foundation for security-focused configuration management. NIST supply-chain guidance further supports knowing the provenance, supplier and dependencies of products and services used by the system.

> **Core principle:** the enterprise may operate the authoritative asset platforms, but the application team must ensure that those platforms and linked application records collectively describe the complete application as it is actually designed, built, deployed and supported.

---

## 1. Define the application inventory boundary

The application should define which components belong to the application inventory.

The boundary should include components that are:

- owned by the application;
- dedicated to the application;
- deployed specifically for the application;
- packaged or distributed by the application team;
- necessary for the application’s security or business operation;
- configured specifically for the application;
- supplied as part of the application;
- embedded within the application;
- used to build or release the application where compromise could affect production;
- used for recovery; or
- relied upon through an application-specific integration.

The boundary should distinguish:

- **application-owned components**;
- **dedicated enterprise-hosted components**;
- **shared enterprise services**;
- **interconnected applications**;
- **supplier-controlled components**;
- **user-installed application components**; and
- **out-of-scope infrastructure inherited from the enterprise**.

A component can be inherited operationally while still requiring an application inventory reference because the application depends on a particular service, version, interface or configuration.

## 2. Define the required inventory granularity

The application should inventory components at a level that supports:

- vulnerability assessment;
- baseline verification;
- change control;
- incident scoping;
- support;
- licence and supplier management;
- recovery;
- end-of-life management;
- security impact analysis; and
- accountability.

A single entry called “Engineering Requirements System” is not sufficient if the application consists of:

- a thick client;
- web tier;
- API service;
- database;
- reporting engine;
- message adapter;
- document-conversion service;
- plugins;
- scheduled jobs;
- integration clients;
- third-party libraries; and
- supplier modules.

The inventory should not become so granular that every transient process or ordinary data file is treated as a separate configuration item. Granularity should be based on security, support and change significance.

## 3. Identify component categories

The application should define the categories of component that may need to be inventoried.

Typical categories include:

- application products;
- custom services;
- thick-client packages;
- web applications;
- APIs;
- microservices;
- application servers or dedicated runtime instances;
- databases;
- schemas;
- stored procedures and application-owned database modules;
- message queues and topics;
- integration adapters;
- file-transfer components;
- reporting services;
- scheduled jobs;
- plugins and extensions;
- libraries and dependencies;
- runtimes and frameworks;
- containers and images;
- deployment packages;
- scripts and automation;
- configuration repositories;
- build pipelines;
- artefact repositories;
- application-specific certificates;
- service identities;
- supplier modules;
- recovery images;
- test harnesses that can affect production artefacts; and
- obsolete components still deployed or retained for recovery.

## 4. Define mandatory inventory attributes

Each material inventory record should contain enough information to identify, locate and manage the component.

Relevant attributes may include:

- unique component identifier;
- component name;
- component type;
- description and purpose;
- application or service association;
- environment;
- version or release;
- build or artefact identifier;
- supplier or origin;
- product edition or module;
- deployment location;
- hostname, instance, cluster or service reference where applicable;
- logical tier;
- owner;
- technical custodian;
- business owner;
- support team;
- support contract;
- support status;
- end-of-support date;
- criticality;
- information processed;
- privileged status;
- exposure or interface type;
- baseline reference;
- configuration reference;
- dependency or parent component;
- software bill of materials reference;
- licence reference;
- recovery requirement;
- monitoring status;
- vulnerability-scanning status;
- date added;
- last verified date;
- lifecycle status;
- planned retirement date; and
- authoritative evidence source.

Not every attribute belongs in one tool. The application should define which system is authoritative for each field and link records where necessary.

## 5. Assign unique identifiers

Components should have identifiers that support consistent reference across:

- CMDB records;
- architecture diagrams;
- baselines;
- vulnerability findings;
- incident records;
- change and release records;
- monitoring;
- supplier cases;
- risk records;
- test evidence; and
- recovery plans.

The identifier should not depend solely on a display name that may change.

For replicated or scaled services, the application should distinguish between:

- the logical component;
- deployed instances;
- versioned artefacts; and
- runtime instances created dynamically.

## 6. Identify authoritative inventory sources

The application should avoid maintaining several contradictory inventories.

It should define the authoritative source for each class of information, for example:

- enterprise CMDB for servers and managed services;
- software-distribution platform for thick-client deployment;
- artefact repository for application packages;
- source repository and lock files for dependencies;
- deployment platform for runtime instances;
- database catalogue for schemas;
- API gateway for registered APIs;
- message broker for queues and topics;
- identity platform for service accounts;
- certificate service for certificates;
- secrets platform for secret references;
- supplier register for contracts and support status;
- application role or interface register for logical components; and
- CM-02 baseline for the approved release set.

The SSP should describe the inventory model and reference these sources rather than reproduce all details.

## 7. Maintain an application inventory view

Even where information is distributed across enterprise systems, the application team should be able to produce a coherent application view.

The view should answer:

- what components comprise the application;
- which versions are deployed;
- where they are deployed;
- which environment each belongs to;
- who owns and supports them;
- which components are shared or inherited;
- which interfaces and dependencies exist;
- which supplier products are used;
- which components are unsupported;
- which components are vulnerable;
- which components are approved by the baseline;
- which components are expected in recovery; and
- which components are being retired.

The application view may be generated from linked records rather than maintained as a separate spreadsheet.

## 8. Reconcile the inventory with the application architecture

The application should compare its inventory with:

- system context diagrams;
- logical architecture;
- deployment architecture;
- trust-boundary diagrams;
- data-flow diagrams;
- interface control documents;
- database design;
- thick-client design;
- recovery architecture; and
- supplier solution design.

Every significant component shown in the architecture should have an inventory record or an explicit inherited-service reference.

Every inventory component should have a legitimate place in the approved architecture.

## 9. Reconcile the inventory with the baseline

CM-08 and CM-02 should operate together.

The application should be able to determine:

- whether every deployed component is in the approved baseline;
- whether every baseline component is deployed where expected;
- whether versions match;
- whether unauthorised components exist;
- whether retired components remain;
- whether emergency changes were reconciled;
- whether recovery packages match the baseline; and
- whether thick-client packages in distribution match the approved release.

The inventory describes what exists; the baseline describes what is authorised.

## 10. Inventory custom-developed software

For custom code, record:

- repository;
- product or service name;
- release version;
- commit or tag;
- build identifier;
- artefact;
- deployment environment;
- owner;
- language and runtime;
- deployment method;
- dependency manifest;
- SBOM reference;
- support status;
- security-test evidence;
- recovery source; and
- retirement status.

The application should not treat “custom code” as one undifferentiated component where separate services or packages can change independently.

## 11. Inventory commercial products

For commercial software, record:

- supplier;
- product;
- edition;
- modules enabled;
- deployed version;
- patch or update level;
- licence;
- support entitlement;
- support status;
- end-of-support date;
- supplier advisory source;
- deployment environments;
- customisations;
- plugins;
- interfaces;
- owner;
- supplier contact;
- recovery media or package; and
- replacement or upgrade plan where applicable.

The inventory should describe the modules actually used, not merely the umbrella product name.

## 12. Inventory thick-client components

For a thick client installed on managed corporate Windows EUC devices, record:

- package name;
- product and version;
- approved installer;
- package or artefact identifier;
- signing information;
- included runtime;
- included libraries;
- plugins;
- local services or drivers;
- configuration profile;
- approved server endpoints;
- software-distribution package reference;
- supported Windows versions;
- owner;
- support status;
- current approved version;
- superseded versions;
- removal method; and
- deployment coverage evidence.

The enterprise owns the EUC inventory platform. The application owns the accuracy of the package content, version and support information.

## 13. Inventory application dependencies

The application should identify direct and material transitive dependencies.

Relevant records may include:

- package name;
- version;
- package ecosystem;
- supplier or maintainer;
- direct or transitive relationship;
- component using it;
- licence;
- support status;
- known vulnerability status;
- package source;
- integrity information;
- approved version;
- update owner; and
- SBOM reference.

Dependency information should preferably be generated from controlled build and package manifests rather than manually typed.

## 14. Maintain a software bill of materials where proportionate

For internally developed, packaged or materially customised software, the application should maintain an SBOM or equivalent dependency record where it provides meaningful risk-management value.

The SBOM should be:

- associated with a specific release;
- generated from the actual build;
- stored with release evidence;
- protected from unauthorised alteration;
- sufficiently complete to support vulnerability assessment;
- updated when dependencies change;
- linked to deployed artefacts;
- available to authorised vulnerability and incident teams; and
- handled as security-sensitive information where appropriate.

An SBOM does not replace the wider component inventory. It provides software-composition detail within it.

## 15. Inventory APIs and interfaces

The application should inventory:

- API name;
- version;
- environment;
- owner;
- producing component;
- authorised clients;
- authentication method;
- data exchanged;
- endpoint;
- status;
- support or retirement date;
- interface specification;
- monitoring status; and
- related service identities.

It should also inventory:

- message queues and topics;
- file-transfer jobs;
- scheduled integration jobs;
- callbacks and webhooks;
- database interfaces;
- report feeds; and
- enterprise-service dependencies.

An undocumented integration is an untracked component relationship and a potential security risk.

## 16. Inventory application-owned database components

Where relevant, inventory:

- database service reference;
- database or catalogue;
- schema;
- major application-owned modules;
- stored procedures;
- migration package;
- database role set;
- version;
- environment;
- owner;
- dependency;
- backup and recovery reference;
- support status; and
- baseline reference.

The enterprise may inventory the database platform and host. The application should inventory its logical database components and approved versions.

## 17. Inventory containers and images

For containerised components, record:

- logical service;
- image name;
- image digest;
- version or tag;
- registry;
- base image;
- build pipeline;
- SBOM;
- deployment environment;
- owner;
- support status;
- vulnerability status;
- configuration reference;
- runtime platform reference; and
- retirement status.

Mutable tags alone are insufficient for high-confidence identification. Digests or equivalent immutable identifiers should be retained where supported.

## 18. Inventory plugins, extensions and scripts

Products often acquire untracked functionality through:

- plugins;
- extensions;
- macros;
- scripts;
- report modules;
- workflow packages;
- custom connectors;
- local utilities;
- browser components; and
- supplier add-ons.

The application should record:

- name;
- version;
- source;
- owner;
- purpose;
- approval;
- environment;
- privilege;
- support status;
- integrity or signature;
- dependencies;
- installation method; and
- retirement status.

## 19. Inventory scheduled jobs and automation

Material scheduled or automated components should be inventoried where they can affect:

- business records;
- access;
- data movement;
- retention;
- deletion;
- integration;
- security monitoring;
- backup;
- reconciliation;
- report distribution; or
- production configuration.

Record:

- job name;
- purpose;
- schedule;
- environment;
- executing identity;
- owner;
- script or artefact;
- inputs and outputs;
- dependencies;
- failure notification;
- change-control reference; and
- status.

## 20. Inventory service and machine identities

Application-specific non-person identities should be linked to the components that use them.

Record:

- identity;
- type;
- owning component;
- environment;
- purpose;
- owner;
- privileges;
- authentication method;
- credential or certificate reference;
- interactive-use status;
- review date;
- expiry or rotation;
- dependent services; and
- retirement trigger.

The secret itself should not be stored in the inventory.

## 21. Inventory application certificates and trust material

The application should maintain references for certificates and trust material that are specific to the application.

Relevant details include:

- certificate or trust reference;
- purpose;
- subject or service;
- environment;
- issuing authority;
- owner;
- consuming component;
- expiry;
- renewal method;
- revocation method;
- trust-store location;
- replacement dependency; and
- monitoring status.

The enterprise certificate service remains authoritative for certificate issuance and lifecycle. The application inventory links the certificate to its business component and dependency.

## 22. Inventory build and release components

Where compromise could affect production software, the application should inventory or reference:

- source repositories;
- build pipelines;
- runners or agents;
- build images;
- package repositories;
- artefact repositories;
- signing services;
- deployment pipelines;
- production service connections;
- security-testing tools;
- SBOM generation;
- release manifests; and
- recovery artefacts.

These may be shared enterprise platforms, but the application should record the specific projects, pipelines, credentials, repositories and artefact paths used.

## 23. Inventory supplier-controlled components

For supplier components, record:

- supplier;
- product or service;
- component;
- version;
- module;
- ownership boundary;
- support responsibility;
- support contact;
- contract reference;
- support and end-of-life status;
- maintenance method;
- supplier access path;
- advisory source;
- evidence available;
- dependencies;
- location; and
- exit or replacement plan.

The application should not assume that the supplier’s inventory automatically covers the customer’s deployed configuration.

## 24. Inventory shared and inherited services

The application should reference the shared enterprise services it depends upon, such as:

- corporate identity;
- MFA;
- directory;
- VPN;
- DNS;
- PKI;
- secrets management;
- SIEM;
- malware scanning;
- vulnerability scanning;
- backup;
- message broker;
- database platform;
- software distribution;
- load balancing;
- monitoring; and
- service management.

The application record should identify:

- service name;
- purpose;
- owner;
- dependency;
- interface;
- service reference;
- environment;
- failure impact; and
- any application-specific configuration.

The application should not duplicate the enterprise service’s internal component inventory.

## 25. Inventory non-production environments

Development, test, training and pre-production components should be inventoried sufficiently to manage:

- production connection risk;
- unsupported software;
- production data;
- test identities;
- deployment paths;
- supplier access;
- vulnerability exposure;
- shared credentials;
- obsolete environments; and
- configuration drift.

The inventory should clearly distinguish environment and prevent lower-environment components from being mistaken for production.

## 26. Inventory recovery and standby components

The application should inventory:

- standby services;
- recovery environment components;
- recovery images;
- backup agents or application modules;
- restore utilities;
- recovery scripts;
- replicated databases;
- recovery certificates;
- recovery service identities;
- alternate endpoints;
- offline installation media; and
- dependencies required for restoration.

Recovery components should be included in vulnerability, support and end-of-life review.

## 27. Record component relationships

A useful inventory should show how components depend on one another.

Relationships may include:

- runs on;
- connects to;
- calls;
- consumes;
- publishes to;
- stores in;
- authenticates through;
- deployed by;
- built from;
- includes;
- supplied by;
- monitored by;
- scanned by;
- backed up by;
- restored from; and
- replaced by.

Relationship information supports:

- incident blast-radius analysis;
- vulnerability applicability;
- change impact;
- recovery planning;
- supplier risk;
- decommissioning; and
- architecture assurance.

## 28. Record ownership and accountability

Every material component should have:

- an accountable application or service owner;
- a technical custodian;
- a support route;
- a supplier owner where applicable;
- an update or patch owner;
- a vulnerability-remediation owner;
- a recovery owner; and
- an escalation route.

Ownership should be reviewed when people, suppliers or organisational structures change.

“Platform team” or “supplier” may be too vague unless the accountable service and contact route are clear.

## 29. Record lifecycle and support status

The inventory should distinguish:

- proposed;
- approved;
- in development;
- in test;
- in production;
- temporarily disabled;
- superseded;
- unsupported;
- planned for retirement;
- decommissioning;
- decommissioned; and
- retained for legal, recovery or evidence purposes.

It should also record:

- release date;
- support start;
- end of standard support;
- end of extended support;
- planned upgrade;
- retirement date; and
- residual deployment.

Unsupported status should be visible and linked to risk treatment.

## 30. Prevent duplicate accounting

NIST CM-08 expects components to be accounted for without unnecessary duplication.

The application should:

- use unique identifiers;
- distinguish logical components from deployed instances;
- reference shared enterprise components rather than copy them as application-owned;
- define parent and child relationships;
- identify authoritative records;
- avoid separate unlinked spreadsheets;
- reconcile duplicate names;
- identify aliases;
- merge or link duplicate records; and
- preserve history when records are consolidated.

Avoiding duplicate accounting does not mean omitting a dependency. It means referencing it consistently.

## 31. Discover components through several methods

No single discovery method is sufficient.

The application should combine, where appropriate:

- enterprise discovery;
- deployment-platform inventory;
- source and artefact records;
- software-distribution records;
- package manifests;
- SBOMs;
- API gateway inventory;
- message-broker configuration;
- database catalogues;
- service-account registers;
- certificate records;
- supplier documentation;
- architecture reviews;
- vulnerability scans;
- configuration scans;
- support records;
- network-flow review;
- code and repository searches; and
- interviews with developers and operators.

Automated discovery should be preferred for volatile runtime details, while application knowledge is needed for logical and business components.

## 32. Reconcile discovered and declared components

The application should compare discovered components against:

- approved inventory;
- baseline;
- architecture;
- deployment manifests;
- release records;
- CMDB;
- vulnerability scan targets;
- monitoring targets;
- backup scope; and
- support records.

The reconciliation should identify:

- discovered but unapproved components;
- approved but missing components;
- version mismatches;
- duplicate records;
- retired but active components;
- active but unmonitored components;
- active but unscanned components;
- unknown owners;
- unsupported versions; and
- components absent from recovery planning.

## 33. Update inventory through the change process

Inventory update should be part of:

- component introduction;
- release;
- deployment;
- upgrade;
- patching;
- interface creation;
- supplier change;
- environment creation;
- service-account creation;
- certificate deployment;
- architecture change;
- migration;
- emergency change;
- retirement; and
- decommissioning.

A change should not be considered complete until relevant inventory and baseline records are updated.

## 34. Integrate inventory with vulnerability management

The application inventory should support RA-05 by allowing the team to:

- identify affected products and versions;
- find all deployments of a vulnerable component;
- identify dependency relationships;
- identify owners;
- identify supplier contacts;
- identify unsupported versions;
- track scan coverage;
- link findings to components;
- confirm remediation coverage; and
- verify that vulnerable versions are removed.

A vulnerability scanner’s asset list is not a complete application inventory, but it is an important reconciliation source.

## 35. Integrate inventory with incident response

The inventory should support incident teams in determining:

- affected components;
- component owners;
- versions;
- interfaces;
- service identities;
- dependencies;
- supplier involvement;
- recovery sources;
- monitoring sources;
- related vulnerabilities;
- deployment locations; and
- downstream systems.

The inventory should be accessible to authorised incident personnel without requiring the original developer to reconstruct the architecture from memory.

## 36. Integrate inventory with monitoring and logging

The application should reconcile its inventory with:

- SIEM source lists;
- application monitoring;
- health checks;
- logging endpoints;
- vulnerability-scanning targets;
- backup coverage;
- certificate-expiry monitoring;
- support monitoring; and
- alert ownership.

Every production component should have an explicit monitoring decision, even if the decision is that monitoring is inherited or not technically available.

## 37. Integrate inventory with recovery planning

The application should use the inventory to identify:

- components required for minimum service;
- recovery sequence;
- dependencies;
- required versions;
- installation packages;
- configuration;
- service identities;
- certificates;
- database components;
- recovery locations;
- supplier dependencies; and
- verification requirements.

Recovery testing should confirm that the inventory contains enough information to reconstruct the approved application.

## 38. Protect inventory information

Inventory information can reveal valuable technical detail.

The application should:

- restrict modification to authorised roles or automated processes;
- restrict sensitive views;
- protect supplier and vulnerability details;
- avoid storing passwords or secret values;
- preserve change history;
- log changes;
- back up authoritative records;
- validate imports;
- prevent unauthorised bulk export;
- preserve integrity;
- apply retention; and
- support recovery.

Read access may be broader than write access, but detailed architecture, vulnerabilities and security relationships should remain need-to-know.

## 39. Log inventory changes

Relevant events should include:

- component creation;
- version change;
- owner change;
- environment change;
- support-status change;
- new dependency;
- interface change;
- supplier change;
- service-identity link;
- certificate link;
- component retirement;
- decommissioning;
- duplicate consolidation;
- manual override;
- reconciliation exception; and
- unauthorised update attempt.

The application should preserve:

- acting identity or process;
- time;
- previous and new value where practical;
- component identifier;
- change reference;
- source system; and
- outcome.

## 40. Review inventory accuracy periodically

The application should review the inventory at a defined frequency and after material change.

The review should confirm:

- completeness;
- correct versions;
- correct environments;
- ownership;
- support status;
- dependency accuracy;
- alignment with architecture;
- alignment with baseline;
- vulnerability-scan coverage;
- monitoring coverage;
- recovery coverage;
- supplier accuracy;
- absence of duplicate records;
- retirement status; and
- resolution of previous discrepancies.

High-change applications may require automated or continuous reconciliation. Stable commercial applications may use less frequent formal reviews supported by release checks.

## 41. Define event-driven inventory reviews

Inventory should be reviewed after:

- major release;
- new component;
- new integration;
- product upgrade;
- new thick-client package;
- supplier change;
- new environment;
- migration;
- database change;
- container-platform change;
- service-account creation;
- certificate replacement;
- vulnerability affecting a component;
- incident;
- recovery exercise;
- decommissioning; and
- enterprise CMDB or discovery change.

## 42. Resolve inventory discrepancies

Each discrepancy should be assessed and resolved.

Examples include:

- unknown component;
- unapproved version;
- missing owner;
- duplicate record;
- obsolete package;
- undocumented integration;
- service identity with no component;
- certificate with no owner;
- component not scanned;
- component not monitored;
- recovery component not in baseline; and
- CMDB record that does not match the deployment platform.

The resolution should identify:

- cause;
- risk;
- owner;
- corrective action;
- target date;
- evidence;
- baseline or architecture impact; and
- whether an incident or unauthorised change investigation is required.

## 43. Decommission components completely

When a component is retired, the application should:

- stop service;
- remove deployment;
- remove packages;
- remove integrations;
- revoke service identities;
- revoke certificates and credentials;
- remove scheduled jobs;
- remove monitoring and scan targets when appropriate;
- archive required artefacts;
- preserve required records;
- update architecture;
- update baseline;
- update inventory status;
- remove supplier support where appropriate;
- remove licences;
- validate data disposition; and
- verify that no active instances remain.

The component record should normally be retained with a decommissioned status rather than deleted immediately, so that historical changes and incidents remain traceable.

## 44. Manage inventory limitations

Where the application cannot maintain the expected inventory detail, record:

- affected component class;
- missing information;
- reason;
- impact;
- discovery limitation;
- supplier restriction;
- authoritative alternative;
- compensating review;
- owner;
- approval;
- remediation plan; and
- review or expiry date.

Examples include:

- opaque supplier appliance;
- no reliable dependency list;
- dynamic instances not visible to the CMDB;
- undocumented legacy scripts;
- thick-client versions not reported centrally;
- shared platform with poor component attribution;
- missing end-of-support information; or
- incomplete SBOM.

The limitation should be recorded in the application addendum or risk process.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses an enterprise CMDB, managed hosting, software distribution, source control, vulnerability management and service-management processes. They exclude enterprise discovery-platform engineering and large-scale historic data cleansing.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define the application inventory boundary and component categories** | Identify the application-owned, dedicated, shared, supplier, thick-client, integration, build and recovery components that require inventory treatment. | Summarise in the **SSP CM-08 statement** and maintain the detail in the existing **system context**, **architecture**, **ConOps**, **SyOps** or **CM-08 inventory model**. | **6–12 hours** |
| **2. Define mandatory inventory attributes and authoritative sources** | Specify identifiers, version, environment, owner, supplier, support status, baseline, dependencies and which enterprise or application system is authoritative for each field. | Record the model in the **SSP**, **configuration-management approach**, **CMDB data model**, **SyOps** or **application support model**. | **8–16 hours** |
| **3. Establish a coherent application inventory view** | Link or export relevant CMDB, deployment, artefact, dependency, interface, identity and supplier records so the complete application can be understood. | Use the existing **CMDB**, **component register**, **architecture repository**, **deployment platform**, **artefact repository** and **service catalogue**, referenced from the SSP. | **12–32 hours** |
| **4. Inventory custom and commercial application components** | Record services, products, modules, versions, environments, owners, support and lifecycle status. | Evidence remains in the normal **CMDB/component records**, **CM-02 baseline**, **release manifest**, **supplier register** and **architecture**. | **8–24 hours** |
| **5. Inventory thick-client packages where applicable** | Record package, version, signing, included runtime and libraries, approved endpoints, distribution reference, support status and superseded versions. | Use the existing **software-distribution package record**, **packaging specification**, **release manifest**, **CMDB/software inventory** and **installation evidence**. | **6–16 hours** |
| **6. Inventory software dependencies and maintain an SBOM where proportionate** | Generate dependency manifests or an SBOM from the actual build and link it to the approved release and deployed artefact. | Store evidence in the **source repository**, **build pipeline**, **artefact repository**, **SBOM store**, **release pack** and **RA-05 records**. | **12–28 hours initially** |
| **7. Inventory APIs, integrations, queues, transfers and scheduled jobs** | Record name, owner, version, endpoint, direction, identity, purpose, status and related components. | Use the existing **interface control documents**, **API catalogue**, **message-broker records**, **batch schedule**, **data-flow diagrams** and **service catalogue**. | **8–24 hours** |
| **8. Inventory application-owned database and runtime components** | Record databases, schemas, migration versions, application roles, runtimes, containers, images and relevant logical components. | Evidence sits in the **database design**, **deployment manifest**, **container registry**, **CMDB**, **CM-02 baseline** and **release records**. | **8–20 hours** |
| **9. Link service identities, certificates and secret references to components** | Associate each application-specific identity and certificate with its purpose, owner, environment, consuming component and lifecycle. | Use the existing **service-account register**, **certificate platform**, **secrets platform**, **interface documents**, **CMDB** and **SyOps**. | **6–16 hours** |
| **10. Record supplier, support and lifecycle status** | Track supplier, support entitlement, end-of-support dates, advisory source, owner, upgrade or retirement plan and contract reference. | Maintain evidence in the **supplier register**, **CMDB**, **risk register**, **service review**, **support case system** and **release roadmap**. | **6–14 hours** |
| **11. Reconcile inventory with architecture, baseline and deployment** | Compare records with diagrams, release manifests, runtime platforms, software distribution and vulnerability targets to identify missing or unauthorised components. | Record results in the normal **configuration review**, **release verification**, **CMDB reconciliation**, **post-implementation review** or **CA-07 review**. | **12–28 hours initially; 4–12 hours per review** |
| **12. Integrate inventory updates into change and release** | Require inventory, baseline, interface, owner and support updates before a change, release, migration or retirement is closed. | Add checks to the existing **change template**, **release checklist**, **operational acceptance record**, **migration plan** and **decommissioning process**. | **6–16 hours initially** |
| **13. Review inventory accuracy periodically** | Verify completeness, versions, owners, lifecycle, dependencies, scanning, monitoring, recovery and duplicate accounting. | Retain outcomes in established **service reviews**, **configuration audits**, **CMDB reviews**, **CA-07 posture reports** or **application governance minutes**. | **8–20 hours per review** |
| **14. Resolve discrepancies and unknown components** | Investigate missing, duplicate, unsupported, unapproved or ownerless components and update records, baseline, risk or incident processes. | Use existing **problem records**, **change records**, **risk register**, **incident records**, **CMDB corrections** and **application backlog**. | **2–8 hours per ordinary discrepancy** |
| **15. Decommission and retain historical traceability** | Remove active deployment, identities, certificates, jobs, interfaces and monitoring while retaining a decommissioned inventory record and evidence. | Record completion in the **decommissioning record**, **change ticket**, **CMDB**, **CM-02 baseline**, **architecture**, **supplier record** and **data-disposition evidence**. | **6–20 hours per component group** |
| **16. Document and manage inventory limitations** | Record opaque supplier components, incomplete discovery, missing dependency data or dynamic-runtime gaps with compensating reconciliation and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP CM-08 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application with established enterprise inventory platforms and a manageable number of components, initial application effort is commonly around **110–250 hours**.

Ongoing effort is commonly around **6–20 hours per month**, plus release, migration and decommissioning activity.

A small commercial application with one package and one database may require less. A custom, integration-heavy, containerised or thick-client application with many dependencies, supplier modules and environments may require substantially more.

The estimates should not be added mechanically where work overlaps. CM-08 commonly shares evidence and effort with:

- CM-02 baseline configuration;
- CM-05 access restrictions for change;
- CM-06 configuration settings;
- CM-07 least functionality;
- RA-05 vulnerability monitoring;
- SI-02 flaw remediation;
- SI-07 software integrity;
- CA-07 continuous monitoring;
- IR-05 incident monitoring; and
- CP controls for recovery.

---

## Suggested document placement

To avoid creating disconnected evidence, component-inventory information should normally be distributed across established application and SDLC artefacts:

- **SSP:** CM-08 implementation approach, inventory boundary, authoritative sources, required attributes, review, reconciliation and limitations.
- **System context and architecture:** logical components, shared services, trust boundaries and relationships.
- **Deployment architecture:** environments, instances, tiers, containers, databases and runtime locations.
- **CMDB or enterprise asset platform:** managed hosts, services, software packages, ownership and lifecycle.
- **CM-02 baseline:** authorised release components, versions, artefacts and configuration.
- **CM-06 configuration specification:** component-specific approved settings and configuration references.
- **Source and artefact repositories:** custom software, build identifiers, packages and release provenance.
- **SBOM and dependency manifests:** direct and transitive software composition.
- **Software-distribution records:** thick-client package identity, versions and deployment coverage.
- **Interface control documents and API catalogue:** APIs, messages, files, queues, clients and destinations.
- **Database design and migration records:** schemas, application-owned database modules and versions.
- **Service-account register:** application identities linked to components and owners.
- **Certificate and secrets platforms:** lifecycle records linked by reference, without copying secret values.
- **Supplier register:** product, support, contract, advisory and end-of-life details.
- **Vulnerability-management platform:** findings and coverage linked to component identifiers.
- **Monitoring and SIEM onboarding:** monitored components, event sources and owners.
- **Recovery plan:** required components, artefacts, sequence and dependencies.
- **Change and release records:** component introduction, update, replacement and inventory reconciliation.
- **Decommissioning records:** removal of deployment, identities, interfaces, licences and retained history.
- **Service and CA-07 reviews:** periodic completeness, support, vulnerability and lifecycle review.
- **Risk register or application addendum:** opaque components, unsupported products, discovery gaps and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide asset and configuration-management policy;
- enterprise CMDB and discovery platforms;
- server, endpoint, network and infrastructure inventories;
- managed Windows EUC hardware and software inventory;
- enterprise virtualisation and hosting inventory;
- corporate cloud or platform inventory where applicable;
- network-device and firewall inventory;
- enterprise software-licence management;
- corporate procurement and supplier master data;
- enterprise certificate and secrets platforms;
- organisation-wide identity and service-account platforms;
- central vulnerability-management asset records;
- enterprise backup-platform inventory;
- corporate software-distribution inventory;
- enterprise data-retention and records policy; and
- organisation-wide asset reporting and governance.

The application team must still:

- define the complete application component boundary;
- determine appropriate component granularity;
- maintain application-specific software, dependency and interface detail;
- link shared enterprise services correctly;
- identify owners, versions, suppliers and support status;
- reconcile inventory with the baseline, architecture and deployed state;
- integrate updates into change and release;
- support vulnerability, incident and recovery use;
- decommission components completely; and
- formally manage inventory gaps.

> **Key dividing line:** the enterprise operates the authoritative asset and discovery platforms; the application ensures that those platforms and linked application records collectively identify every component needed to build, operate, secure, support, recover and retire the business application.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, CM-08 System Component Inventory.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, CM-08 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems**.
4. National Institute of Standards and Technology, **NIST SP 800-161 Rev. 1 Update 1, Cybersecurity Supply Chain Risk Management Practices for Systems and Organizations**.
5. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1**.
