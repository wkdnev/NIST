# CM-06 Configuration Settings — Application Actions

## Purpose

For an IT application, CM-06 means the application must define, implement and maintain secure configuration settings for the software, services, interfaces and application-controlled components that make up the business solution.

It does **not** mean the application team must manage corporate Windows baselines, network-device settings, hypervisors, enterprise databases, central identity platforms or other shared infrastructure. Those settings are inherited from enterprise owners.

The application’s responsibility is to decide which of its own settings are security-relevant, establish approved values, deploy them consistently, prevent unauthorised or accidental weakening, and verify that the running application continues to match the approved configuration.

## 1. Identify the application-controlled configuration

The application should identify the settings it owns or materially controls.

This normally includes:

- application feature settings;
- authentication and identity-integration settings;
- application roles and permission models;
- session and timeout settings;
- API and interface configuration;
- service identities and permissions;
- file-upload and input restrictions;
- application logging and monitoring settings;
- encryption and certificate settings;
- data-retention and clean-up settings;
- security headers and protocol options;
- thick-client configuration;
- database schemas, roles and application-owned parameters;
- scheduled jobs and batch-processing settings;
- integration endpoints;
- error-handling and diagnostic settings; and
- product-specific administrative settings.

The application does not need to repeat every enterprise operating-system, database or network setting. It should identify those as inherited and focus on the configuration necessary to secure the application itself.

## 2. Establish an approved secure configuration

For each security-relevant setting, define the approved value or permitted range.

The selected settings should be based on:

- corporate security requirements;
- supplier hardening guidance;
- NIST or other recognised security checklists;
- architecture and threat assessment;
- information sensitivity;
- business and operational requirements;
- vulnerability and penetration-test findings; and
- lessons from incidents or previous configuration failures.

The approved configuration should be clear enough that two suitably skilled people would configure the application in materially the same way.

## 3. Use secure defaults

The initial application configuration should be secure before production use.

This normally means:

- disabling unused features, modules and interfaces;
- changing or disabling vendor-default accounts and credentials;
- removing sample applications, demonstration data and test functions;
- disabling anonymous or guest access unless explicitly required;
- using restrictive permissions by default;
- disabling unnecessary diagnostic and debugging functions;
- rejecting insecure protocols and weak cryptographic options;
- limiting file types, sizes and processing behaviour;
- disabling unnecessary API methods;
- setting appropriate session timeouts;
- restricting administrative interfaces; and
- ensuring logging is enabled at the required level.

A default installation should not be promoted into production and then hardened later.

## 4. Document security-relevant settings

The application should maintain a controlled configuration record showing:

- setting name;
- component or product;
- approved value;
- security purpose;
- environment applicability;
- source or rationale;
- responsible owner;
- implementation method;
- verification method; and
- any approved deviation.

This information does not need to sit in a separate document. It can be included in:

- the SSP;
- the SyOps or ConOps;
- the application security design;
- deployment configuration;
- infrastructure-as-code or configuration-as-code;
- build and release records;
- product configuration workbooks; or
- controlled operational runbooks.

The SSP should normally summarise the approach and point to the authoritative technical configuration source.

## 5. Separate configuration by environment

Development, test and production should use controlled, distinguishable configurations.

The application should avoid:

- production credentials in test;
- test endpoints in production;
- development debugging in production;
- shared secrets across environments;
- unrestricted test accounts in production;
- production data paths from lower environments; and
- manual configuration copying without review.

Where settings genuinely need to differ, the differences should be documented and justified.

## 6. Protect secrets and sensitive values

Passwords, API keys, private keys, tokens and other secrets are configuration values, but they should not be stored as ordinary configuration text.

The application should:

- reference approved secrets-management services;
- avoid embedding secrets in source code or packages;
- restrict who and what can retrieve secrets;
- use separate secrets for different environments and services;
- rotate or revoke them when required;
- prevent them from appearing in logs or error messages; and
- avoid including actual secret values in configuration documents or evidence.

The configuration record should identify the secret reference and purpose, not the secret itself.

## 7. Apply least functionality and least privilege

Application configuration should enable only the functions and permissions needed for the approved business use.

Examples include:

- disabling unused plugins and connectors;
- limiting service-account permissions;
- restricting database access to required schemas and operations;
- limiting administrative functions to approved roles;
- disabling unnecessary export or bulk-processing functions;
- restricting integration endpoints;
- preventing direct user access to application service accounts; and
- limiting thick-client permissions on the Windows EUC device.

This should align with CM-07, AC-06 and the application’s role model.

## 8. Automate configuration where proportionate

Where practical, the approved application configuration should be deployed using repeatable mechanisms such as:

- deployment pipelines;
- configuration-as-code;
- infrastructure-as-code;
- product configuration packages;
- scripted installation;
- automated database migrations;
- controlled policy files; or
- enterprise software-distribution packages.

Automation reduces manual variation and provides traceability, but the automated configuration itself must be reviewed, protected and tested.

A small application may reasonably use a controlled configuration checklist and manual verification. A large or frequently changed application should normally use automation.

## 9. Prevent unauthorised configuration change

Access to security-relevant configuration should be limited to authorised application administrators, developers or deployment services.

The application should:

- enforce role-based administrative access;
- separate ordinary user and administrative functions;
- use privileged accounts where appropriate;
- protect deployment and configuration repositories;
- require approval for production configuration changes;
- record who made the change;
- retain the previous approved state; and
- prevent users or support personnel from bypassing the normal process.

A production configuration should not be modifiable through an undocumented local file, hidden interface or shared administrator account.

## 10. Integrate configuration changes with the SDLC

Security-relevant setting changes should follow the same controlled process as code and release changes.

The change should normally include:

- reason for change;
- security and operational impact assessment;
- review and approval;
- testing;
- rollback arrangements;
- release traceability;
- updated documentation; and
- post-deployment verification.

Configuration-only changes can create as much risk as code changes and should not be treated as informal operational tweaks.

## 11. Test the configuration

Before production release, verify that the intended security settings are actually effective.

Testing should confirm, where applicable, that:

- disabled functions cannot be used;
- unauthorised roles cannot alter settings;
- sessions expire as designed;
- logging and monitoring are active;
- debugging is disabled;
- insecure protocols are rejected;
- certificates and trust settings are correct;
- file and input limits are enforced;
- integrations use the approved endpoints;
- service identities have only required access;
- production secrets are retrieved securely; and
- the application starts and fails safely with the approved configuration.

Testing should examine behaviour, not merely confirm that a value exists in a file.

## 12. Verify the deployed configuration

After release, confirm that the production application matches the approved configuration.

This may be achieved through:

- automated configuration checks;
- scripted queries;
- deployment-pipeline validation;
- application administration reports;
- API-based configuration extraction;
- database queries;
- file-integrity or checksum checks;
- screenshots for limited manual settings; or
- periodic configuration reviews.

The verification should cover all relevant application nodes and tiers, not just one representative server where configurations can differ.

## 13. Detect configuration drift

The application should identify when the deployed configuration moves away from the approved state.

Examples include:

- logging disabled;
- an unused interface enabled;
- a timeout increased;
- a new administrator added;
- debugging switched on;
- a certificate replaced incorrectly;
- an endpoint changed;
- a service account given additional permissions;
- a security header removed; or
- a manual hotfix altering a configuration file.

For a small application, periodic review may be sufficient. For a higher-risk or frequently changed application, automated drift detection should normally be used.

## 14. Manage configuration deviations

A required setting may occasionally be unsuitable or technically impossible.

Where the application cannot use the standard setting, it should record:

- the affected setting;
- the approved standard value;
- the implemented value;
- the reason;
- the security impact;
- compensating controls;
- accountable owner;
- approval;
- review date; and
- planned correction, upgrade or retirement.

The deviation should be recorded in the application addendum or risk process rather than hidden in an operational configuration file.

## 15. Review settings when circumstances change

Security settings should be reviewed following:

- product or version upgrades;
- new interfaces or integrations;
- architecture changes;
- changes in data sensitivity;
- new vulnerability information;
- penetration-test findings;
- security incidents;
- supplier guidance changes;
- changes to authentication or roles;
- major business-process changes; and
- changes to enterprise standards.

A configuration that was appropriate for one version or operating model may not remain appropriate indefinitely.

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses the standard corporate SDLC, identity, deployment, secrets and monitoring services. They exclude enterprise engineering, procurement and major product redevelopment.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify security-relevant application settings** | Review the application architecture, product administration options, interfaces and business functions to identify settings that affect security. | Summarise the scope in the **SSP CM-06 statement** and record the detailed settings in the existing **security design**, **SyOps**, configuration workbook or deployment definition. | **4–8 hours** |
| **2. Define an approved secure configuration** | Select approved values using corporate requirements, supplier guidance, recognised checklists and application risk. | Record the approved values and rationale in the **application configuration specification**, **security design**, controlled deployment files or product configuration section of the **SyOps**. | **8–20 hours** |
| **3. Apply secure defaults and disable unnecessary features** | Harden the product before production by removing defaults, disabling unused services and interfaces, and applying restrictive initial settings. | Include the requirements in the **build specification** or **SDLC backlog** and retain verification in the normal **system or security test report**. | **8–24 hours** |
| **4. Separate production and non-production settings** | Use separate configuration, endpoints, identities and secrets for each environment, with documented permitted differences. | Capture the environment model in the **solution design**, **ConOps/SyOps** and controlled **deployment configuration**; verify it in the **release or integration test report**. | **4–12 hours** |
| **5. Protect secrets and sensitive configuration** | Store secrets in approved vaults or managed credential services and reference them securely at run time. | Describe the approach in the **SSP IA-05 and CM-06 sections** and **security design**; retain implementation evidence within the normal **deployment and test records**. | **4–16 hours** |
| **6. Restrict who can change configuration** | Limit production configuration access to approved roles and deployment services, with attributable administrative actions. | Record roles in the existing **access-control matrix**, **SSP**, **SyOps** or support model; verify through the normal **access-control test report**. | **4–10 hours** |
| **7. Deploy configuration through a controlled process** | Use the approved release pipeline, scripted deployment, package or controlled manual procedure, with review and rollback. | Capture the method in the **SDLC**, **release plan**, **deployment design** or **operational runbook** and retain the normal **change and release record**. | **8–24 hours** |
| **8. Test security settings before release** | Test that approved values produce the intended security behaviour and that prohibited functions remain unavailable. | Add cases to the normal **system**, **security**, **integration** or **operational acceptance test plan** and retain results in the established **test report**. | **8–20 hours** |
| **9. Verify the production configuration** | Compare the deployed state with the approved configuration after release and periodically thereafter. | Record verification as part of the **release evidence pack**, **operational acceptance record**, **service review** or **continuous-monitoring evidence** referenced by the SSP. | **4–12 hours initially; 2–6 hours per review** |
| **10. Detect and manage drift or deviations** | Use automated checks or periodic review to identify unauthorised differences, then correct them or formally approve the exception. | Record findings in normal **service review records**, **change tickets**, **risk register** or the **application addendum**; update the SSP where the implementation materially changes. | **6–16 hours initially; 2–6 hours per review** |

## Suggested document placement

To avoid creating disconnected evidence, the information should normally be distributed across existing application and SDLC artefacts:

- **SSP:** CM-06 implementation approach, inherited enterprise controls, application-owned settings, deviations, ownership and review frequency.
- **ConOps or SyOps:** operational configuration behaviour, environment differences, administrative responsibilities, failure handling and support procedures.
- **Security architecture or design:** security-relevant settings, trust boundaries, identities, endpoints, protocols, encryption and protected configuration paths.
- **Requirements and backlog:** individual hardening, access, deployment and verification requirements with acceptance criteria.
- **Build and deployment definitions:** the authoritative technical values, scripts, packages, templates or configuration-as-code.
- **Test plans and reports:** evidence that approved values are effective and prohibited functions remain unavailable.
- **Release and operational acceptance records:** confirmation that the deployed configuration matches the approved state.
- **Risk register or addendum:** deviations, unsupported settings, legacy constraints, compensating controls and review dates.

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- Microsoft Windows EUC security baselines;
- server operating-system hardening;
- network-device and firewall configuration;
- hypervisor and virtualisation settings;
- enterprise database-platform baselines;
- identity, MFA and directory configuration;
- corporate VPN configuration;
- endpoint security and EDR settings;
- enterprise PKI and cryptographic policy;
- central secrets-management platforms;
- corporate security configuration standards;
- shared vulnerability and compliance scanning;
- infrastructure configuration monitoring; and
- enterprise change and release governance.

The application team should still reference these inherited controls and ensure that its own configuration does not undermine them.

> **Key dividing line:** the enterprise secures and maintains the shared platforms; the application defines, applies and verifies the security settings needed for its own products, integrations, roles, information and business functions.
