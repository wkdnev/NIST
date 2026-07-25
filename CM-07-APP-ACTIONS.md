# CM-07 Least Functionality — Application Actions

## Purpose

For an IT application, CM-07 means the application must provide **only the functions, services, interfaces, protocols, packages, accounts and capabilities required for its approved business purpose**, and must disable, remove or tightly restrict everything else.

The enterprise may provide hardened Microsoft Windows EUC devices, server operating-system baselines, network controls, managed database platforms, endpoint protection, software distribution and shared infrastructure services. Those enterprise controls reduce unnecessary functionality in the common environment, but they do not determine which features, modules, plugins, interfaces or administrative capabilities are genuinely required within a particular business application.

The application must therefore identify what functionality is necessary, remove or disable what is not, restrict any risky function that must remain, prevent unauthorised re-enablement, and periodically verify that the deployed application still reflects the approved functional scope.

NIST CM-07 requires systems to be configured to provide only mission-essential capabilities and to prohibit or restrict unnecessary functions, ports, protocols, software and services. NIST SP 800-128 places this within security-focused configuration management, while NIST SP 800-70 Rev. 5 explains how security configuration checklists can help reduce attack surface, vulnerabilities and undetected change.

> **Core principle:** every enabled function creates operational value, attack surface or both. If the application cannot explain why a capability is needed, it should normally be disabled, removed or separately justified.

---

## 1. Define the application’s essential business functions

The application should clearly identify the functions required to support its approved business purpose.

For a requirements-management application, for example, essential functions might include:

- creating and editing requirements;
- controlled review and approval;
- versioning and traceability;
- project-based access;
- searching and reporting;
- approved import and export;
- integration with selected engineering tools;
- audit history;
- records retention;
- administration of application roles; and
- recovery of authorised records.

The application should distinguish these from optional, convenience, demonstration, legacy, diagnostic or supplier features.

A product feature being available under the licence does not mean it is required.

## 2. Maintain an approved functionality inventory

The application should maintain a concise record of enabled and prohibited functionality.

This should normally cover:

- application modules;
- plugins and extensions;
- APIs;
- web routes;
- reports;
- import and export functions;
- file types;
- protocols;
- administrative interfaces;
- scheduled jobs;
- batch processes;
- integration connectors;
- database-access paths;
- local thick-client components;
- scripting or macro capabilities;
- embedded interpreters;
- remote-support functions;
- sample or demonstration features;
- developer and debug modes;
- supplier telemetry or update functions;
- optional background services; and
- executable or uploaded content.

For each material item, the record should identify:

- whether it is enabled, disabled, removed or restricted;
- the business or technical justification;
- the applicable environment;
- the accountable owner;
- the implementation method;
- the verification method; and
- any approved exception.

This need not be a separate document. It can form part of the CM-06 configuration specification, solution design, SyOps, release manifest or controlled product configuration record.

## 3. Disable or remove non-essential modules and features

The application should disable or remove functionality that is not required for the approved use case.

Examples include:

- unused product modules;
- demonstration applications;
- sample data;
- tutorial content;
- default dashboards;
- obsolete reports;
- unused workflows;
- unused database schemas;
- optional web applications;
- unneeded messaging components;
- inactive integrations;
- legacy compatibility modes;
- embedded web servers not used by the design;
- development consoles;
- debug endpoints;
- shell or command-execution features;
- scripting engines;
- macro support;
- supplier remote-support tools;
- optional telemetry;
- peer-to-peer functions;
- local discovery services;
- unnecessary schedulers; and
- bundled third-party utilities.

Where removal is supported and safe, removal is usually stronger than merely hiding or disabling a feature.

## 4. Disable unused services, listeners and interfaces

Application components should expose only the service endpoints required by the approved architecture.

The application should identify and restrict:

- listening ports;
- web endpoints;
- API routes;
- administrative interfaces;
- health and diagnostic endpoints;
- database listeners under application control;
- message queues and topics;
- file-transfer services;
- local inter-process interfaces;
- thick-client service endpoints;
- management APIs;
- callback URLs;
- webhooks;
- supplier-support channels; and
- discovery or broadcast services.

An endpoint should not remain available merely because a firewall currently blocks it. Defence in depth means disabling the unnecessary service at the application or product layer where possible.

## 5. Restrict protocols and methods

The application should use only approved protocols and methods needed for its intended operation.

It should disable or reject, where not required:

- insecure or obsolete protocol versions;
- clear-text administration;
- anonymous binds;
- unused HTTP methods;
- legacy authentication methods;
- unrestricted database protocols;
- unneeded file-transfer methods;
- unauthorised remote procedure calls;
- open redirects or callbacks;
- insecure serialisation formats;
- broad cross-origin behaviour; and
- unauthorised tunnelling or proxy functions.

Where a legacy protocol must remain, its use should be narrowly restricted by identity, network path, function and monitoring and documented in the application addendum.

## 6. Restrict file, content and executable handling

Applications that accept or generate files should enable only the formats and behaviours required for the business process.

The application should:

- allow only approved file types;
- validate actual content rather than relying only on filename extensions;
- limit file size and quantity;
- prevent executable content unless explicitly required;
- disable unnecessary macro, script or active-content processing;
- control archive extraction and nesting;
- reject unsupported or malformed formats;
- restrict preview and conversion functions;
- scan uploaded or generated content through approved services where applicable;
- store files outside executable application paths; and
- prevent uploaded content from changing application configuration or code.

A general-purpose file upload function should not exist when the business process requires only a small set of document types.

## 7. Restrict import, export and bulk-processing capabilities

Import, export and bulk functions can create significant confidentiality, integrity and availability risk.

The application should:

- enable only business-approved import and export formats;
- restrict who may use bulk functions;
- limit the volume or scope of each operation;
- apply the same access controls as interactive use;
- prevent export of information outside the authorised project, case or business scope;
- validate imported data and instructions;
- prevent imported content from assigning roles or altering security settings unless explicitly designed;
- require approval for unusually high-impact functions where proportionate;
- log use and outcome;
- protect generated files; and
- remove obsolete or duplicate export paths.

An application should not provide an unrestricted “export everything” capability simply because the product supports one.

## 8. Restrict administrative and support functions

Administrative, support and diagnostic features should be limited to the minimum needed to operate the application.

The application should restrict:

- role administration;
- security configuration;
- database maintenance tools;
- support consoles;
- user impersonation;
- diagnostic data access;
- debug logging;
- cache and queue inspection;
- workflow override;
- bulk correction;
- direct record editing;
- system-wide search;
- data repair utilities;
- configuration import and export;
- plugin installation;
- licence administration;
- script execution; and
- emergency recovery functions.

These functions should be available only through approved privileged roles and, where appropriate, approved management paths or PAM.

## 9. Remove default, sample and development functionality before production

Production deployments should not contain unnecessary development or demonstration artefacts.

The application should remove or disable:

- default accounts;
- sample credentials;
- sample applications;
- test endpoints;
- test users;
- demonstration workflows;
- development databases;
- debug symbols where not operationally required;
- source maps that expose sensitive implementation detail;
- verbose stack traces;
- test certificates;
- dummy integrations;
- temporary bypass settings;
- developer backdoors;
- tracing consoles; and
- installation wizards or setup interfaces no longer required.

The release process should verify this before operational acceptance.

## 10. Restrict scripting, macros and user extensibility

User-configurable scripting, macros, plugins and extension mechanisms can turn a business application into a general-purpose execution environment.

Where these features are not essential, they should be disabled.

Where required, the application should:

- restrict who may create or execute scripts or macros;
- limit available commands and libraries;
- prevent operating-system command execution;
- prevent direct access to credentials or restricted files;
- validate and approve extensions;
- sign or integrity-protect approved code;
- separate development and production extension processes;
- restrict external network access;
- log execution and changes;
- provide version control and rollback; and
- regularly review unused or obsolete extensions.

A configurable rules engine should not automatically be assumed safe merely because it is part of the product.

## 11. Restrict plugins, libraries and optional packages

Only approved plugins, libraries, add-ons and optional packages should be installed or loadable.

The application should:

- maintain an approved dependency and extension list;
- prevent ordinary users from adding plugins;
- remove unused packages;
- disable dynamic loading from untrusted locations;
- restrict package repositories;
- verify package source and integrity;
- review supplier support and vulnerability status;
- prevent automatic installation of unapproved dependencies;
- distinguish development-only and production dependencies; and
- update the baseline when an approved package changes.

This should align with CM-02, CM-08, RA-05 and SI-07.

## 12. Limit thick-client functionality

A thick client installed on a corporate Windows EUC device should include only the functions needed for approved use.

The application should:

- package only required binaries and components;
- avoid bundled utilities not needed by users;
- avoid unnecessary local services or drivers;
- disable local database or server functions unless required;
- prevent embedded administrative credentials;
- restrict local configuration editing;
- avoid local scripting or plugin installation unless approved;
- limit local storage and offline capability;
- communicate only with approved internal service endpoints;
- use the corporate software-distribution process;
- remove obsolete versions through normal software management; and
- ensure security is enforced by the receiving service rather than solely by the client.

The application baseline should identify the approved package and capabilities, while the enterprise remains responsible for the Windows device baseline and package deployment infrastructure.

## 13. Limit background jobs and scheduled processing

Scheduled jobs and batch functions should exist only where needed.

The application should:

- inventory active jobs;
- disable obsolete or duplicate jobs;
- define the business purpose and owner;
- restrict the service identity and data scope;
- limit frequency and concurrency;
- prevent arbitrary command or query execution;
- control job parameters;
- set time and resource limits;
- log execution and failure;
- prevent unauthorised ad hoc execution; and
- review jobs when the business process changes.

Dormant jobs can remain exploitable even when their outputs are no longer used.

## 14. Limit error, debug and diagnostic functionality

Diagnostic capability should be sufficient for support but not excessive in normal production operation.

The application should:

- disable debug mode by default;
- avoid detailed stack traces to ordinary users;
- prevent diagnostic pages exposing configuration, paths, secrets or source details;
- limit verbose logging to approved temporary troubleshooting windows;
- restrict diagnostic endpoints;
- remove temporary support artefacts after use;
- protect memory dumps and trace files;
- prevent unauthorised profiling or introspection;
- log changes to diagnostic settings; and
- restore the approved state after troubleshooting.

Where diagnostic functionality is temporarily enabled, it should be time-limited, attributable and reviewed.

## 15. Limit outbound functionality and external connections

An internal application should initiate only the outbound communications required by its approved design.

The application should:

- identify each required destination and purpose;
- use approved internal endpoints;
- prohibit unapproved Internet, cloud, consumer or supplier connections;
- disable vendor telemetry or update checks that require external access unless separately approved;
- prevent user-defined callbacks or arbitrary URLs;
- restrict connector configuration;
- use approved proxies or gateways where applicable;
- reject unexpected redirection;
- log material connection failures and changes; and
- remove obsolete outbound rules when integrations are retired.

This is particularly important for a master standard scoped to internal corporate-network applications.

## 16. Limit data and resource consumption

Least functionality also means preventing features from being used beyond their intended scale or purpose.

The application should apply proportionate limits to:

- file size;
- record count;
- query scope;
- export volume;
- report complexity;
- API request rate;
- batch size;
- concurrent jobs;
- archive depth;
- search range;
- session count;
- local cache size;
- retry behaviour; and
- user-configurable processing.

These limits reduce abuse, accidental exhaustion and denial-of-service risk without requiring the application team to manage enterprise infrastructure capacity.

## 17. Prevent unauthorised re-enablement

Disabled functionality must not be easy to restore outside the approved process.

The application should:

- restrict configuration access;
- protect feature flags;
- control plugin and module installation;
- protect deployment manifests;
- require change approval;
- use controlled build and release pipelines;
- monitor changes to security-relevant functionality;
- avoid hidden local overrides;
- prevent ordinary administrators from enabling unsupported capabilities;
- retain previous approved settings; and
- verify production after release.

A feature is not meaningfully disabled if any support user can re-enable it without approval or audit.

## 18. Test that prohibited functionality is unavailable

Testing should verify both what is enabled and what is absent.

Tests should include, where relevant:

- disabled modules;
- removed sample applications;
- inaccessible administrative routes;
- rejected unused API methods;
- blocked file types;
- disabled scripting and macros;
- restricted plugins;
- unavailable debug endpoints;
- prohibited exports;
- disabled remote support;
- denied outbound connections;
- removed default accounts;
- standard-user thick-client behaviour;
- obsolete scheduled jobs;
- direct invocation of hidden functions; and
- failure behaviour when a required module is unavailable.

Testing only the visible menu is insufficient. Direct API, URL, service, local-client and configuration paths should be considered.

## 19. Monitor for unexpected functionality

The application should identify evidence that unapproved functionality has appeared or been re-enabled.

Potential indicators include:

- a new listening endpoint;
- an unexpected module or plugin;
- a new scheduled job;
- debug mode enabled;
- an unapproved export function;
- a changed feature flag;
- an unexpected outbound destination;
- a new administrative route;
- a thick-client package containing additional binaries;
- a new service identity;
- a new database procedure;
- a previously removed default account; or
- drift from the approved package or configuration.

Monitoring may use deployment checks, package comparisons, configuration review, application self-reporting, vulnerability scans, software-composition analysis or periodic manual review.

## 20. Review functionality after change

Least-functionality decisions should be reviewed after:

- product upgrades;
- licence changes;
- new modules;
- architecture changes;
- new integrations;
- supplier changes;
- business-process changes;
- security incidents;
- penetration-test findings;
- vulnerability findings;
- new data types;
- changes to user roles;
- migration to a new platform; and
- retirement of old functions.

Upgrades often enable new features by default or reinstall sample and diagnostic components, so previous hardening decisions should not be assumed to remain effective.

## 21. Manage required exceptions

Some products may require a component, protocol or privilege that appears unnecessary but cannot be removed without breaking supported operation.

Where a non-essential or risky function must remain, the application should record:

- the function or component;
- why it is not required by the business but remains technically necessary;
- the affected environment;
- the exposure created;
- available restriction;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, upgrade or replacement plan; and
- review or expiry date.

The exception should be documented in the application addendum or risk process rather than hidden in product configuration.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate build, deployment, identity, logging and change-management services. They exclude enterprise platform engineering, procurement and major supplier redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify essential and non-essential application functions** | Review business requirements, architecture, product modules, interfaces, jobs and administrative features and classify each as required, prohibited or restricted. | Summarise the approach in the **SSP CM-07 statement** and maintain the detail in the existing **security design**, **SyOps**, **product configuration record** or **CM-06 settings record**. | **6–12 hours** |
| **2. Disable or remove unused modules, services and interfaces** | Turn off or uninstall unnecessary modules, endpoints, listeners, sample applications, connectors and optional services before production release. | Record the approved state in the **configuration specification**, **deployment definition**, **release manifest** or **product hardening section of the SyOps**. Verify in the normal **system/security test report**. | **8–24 hours** |
| **3. Remove default, sample, test and development functionality** | Remove default accounts, sample data, setup utilities, debug routes, test certificates and temporary bypass settings from the production build. | Include checks in the **build specification**, **release checklist** and **operational acceptance test report**. Reference the result from the SSP. | **4–12 hours** |
| **4. Restrict file, import, export and bulk functions** | Permit only approved formats and operations, apply size and volume limits, and restrict high-impact use to authorised roles. | Define requirements in the **business/security requirements**, **data-flow design**, **SyOps** and **SSP**. Retain results in the **functional and security test report**. | **8–24 hours** |
| **5. Restrict administrative, support and diagnostic capabilities** | Limit privileged functions, disable debug mode by default and control temporary troubleshooting features through approved support and change processes. | Record operating arrangements in the **SyOps**, **support model**, **SSP CM-07/AC-06 sections** and normal **change records**. | **6–16 hours** |
| **6. Restrict scripting, macros, plugins and extensions** | Disable them where not required; otherwise approve, integrity-protect, scope and monitor permitted extensions. | Capture the decision in the **security design**, **product configuration**, **SDLC requirements** and **SSP**. Retain approved extensions in the **component inventory** or **release manifest**. | **8–24 hours** |
| **7. Limit thick-client functionality where applicable** | Package only required binaries and capabilities, avoid unnecessary services or drivers, restrict local configuration and use only approved internal endpoints. | Record this in the **thick-client design**, **packaging specification**, **software-distribution package record**, **SyOps** and **installation test report**. | **8–20 hours** |
| **8. Limit background jobs and service capabilities** | Inventory scheduled jobs and service identities, disable obsolete jobs and restrict each to its required function, frequency, parameters and data. | Use the existing **batch design**, **service-account register**, **SyOps**, **release manifest** and **operational test report**. | **6–16 hours** |
| **9. Restrict outbound connections and supplier functions** | Permit only approved internal destinations and disable unapproved telemetry, update checks, callbacks, remote support and external connectors. | Define approved flows in the **architecture**, **interface control document**, **data-flow diagram**, **SSP** and **firewall/change request** where applicable. | **6–16 hours** |
| **10. Apply operational limits to exposed functions** | Set proportionate file, query, export, API, batch, retry and concurrency limits to prevent accidental or abusive overuse. | Record limits in the **application configuration specification**, **interface specification**, **SyOps** and **performance/security test report**. | **6–20 hours** |
| **11. Protect disabled functionality from re-enablement** | Restrict configuration, feature flags, plugin installation and deployment changes to approved roles and release processes. | Describe access and change controls in the **SSP**, **CM-06 configuration record**, **SDLC/release process** and **role matrix**. | **4–12 hours** |
| **12. Test that unnecessary functionality is unavailable** | Test direct routes, APIs, package contents, local-client behaviour, protocols, exports, debug paths and disabled modules rather than relying only on visible menus. | Add negative cases to the normal **system/security test plan** and retain outcomes, defects and retests in the established **test report** and **release evidence pack**. | **12–32 hours** |
| **13. Verify and review least functionality after release** | Compare the deployed application with the approved functionality set after release and review again following upgrades or material change. | Record checks in the **operational acceptance record**, **post-implementation review**, **service review**, **continuous-monitoring evidence** or **change record**. | **4–10 hours per release or review** |
| **14. Formally manage unavoidable functions and exceptions** | Document any risky or unnecessary function that cannot be removed, apply restriction and monitoring, and establish remediation or replacement actions. | Use the existing **risk register**, **problem record** or **application addendum**, with the **SSP** referencing material deviations. | **4–10 hours per exception** |

### Indicative total

For a typical internal application with reasonable product configurability and established deployment processes, initial application effort is commonly around **80–200 hours**.

A simple commercial application with few optional modules may require less. A large engineering platform, heavily extensible product, thick-client package, legacy application or supplier-controlled solution may require substantially more.

The estimates should not be added mechanically where work overlaps. CM-07 activities commonly share analysis and evidence with CM-02 baseline configuration, CM-06 configuration settings, CM-08 component inventory, AC-06 least privilege and SA-11 testing.

---

## Suggested document placement

To avoid creating disconnected evidence, least-functionality information should normally be distributed across existing application and SDLC artefacts:

- **SSP:** CM-07 implementation approach, inherited controls, high-level enabled/prohibited capability summary, review arrangements and exceptions.
- **ConOps or SyOps:** approved operational functions, administration, support, diagnostics, batch processing and restricted capabilities.
- **Security or solution architecture:** required services, interfaces, protocols, endpoints, trust boundaries and approved outbound connections.
- **Business and security requirements:** essential functions, prohibited functions, limits and role restrictions.
- **CM-06 configuration specification:** authoritative enabled, disabled and restricted settings.
- **CM-02 baseline and release manifest:** approved modules, packages, plugins, jobs and interfaces included in each release.
- **CM-08 component inventory:** installed products, extensions, dependencies and application services.
- **Interface control document:** approved APIs, methods, protocols, endpoints, callbacks and connectors.
- **Thick-client packaging specification:** included binaries, local services, drivers, configuration and approved endpoints.
- **Build and deployment definitions:** removal or disabling of sample, test, debug and optional components.
- **Role/access matrix:** administrative, support, export, scripting and other restricted capabilities.
- **Test plans and reports:** negative tests proving that prohibited functionality is unavailable.
- **Release and operational acceptance records:** confirmation that only approved capabilities are enabled in the deployed version.
- **Service reviews and change records:** periodic or change-triggered confirmation that least functionality remains effective.
- **Risk register or application addendum:** non-removable modules, legacy protocols, supplier constraints and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- Microsoft Windows EUC operating-system features and service baselines;
- server operating-system service and package baselines;
- enterprise firewall and network-port governance;
- network-device protocols and services;
- hypervisor and virtualisation functionality;
- managed database-platform features and services;
- enterprise identity and authentication platform functionality;
- VPN gateway functionality;
- EDR and endpoint application-control platforms;
- shared middleware and enterprise platform baselines;
- corporate software-distribution controls;
- enterprise allow-listing and executable-control tooling;
- central vulnerability and compliance scanning;
- corporate configuration and change governance; and
- infrastructure monitoring for ports, services and unauthorised software.

The application team must still:

- decide which application features are genuinely required;
- disable unnecessary product functionality;
- restrict application-owned interfaces, plugins and jobs;
- package thick clients minimally;
- ensure the application does not undermine inherited platform hardening; and
- provide enough application context for enterprise scanning and monitoring teams to recognise unexpected functionality.

> **Key dividing line:** the enterprise minimises and controls functionality in the shared platforms; the application minimises and controls the features, modules, interfaces and capabilities that make up the business application.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, CM-07 Least Functionality.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, CM-07 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-128, Guide for Security-Focused Configuration Management of Information Systems**.
4. National Institute of Standards and Technology, **NIST SP 800-70 Rev. 5, National Checklist Program for IT Products: Guidelines for Checklist Users and Developers**.
5. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, CM-07 and related configuration-management content.
