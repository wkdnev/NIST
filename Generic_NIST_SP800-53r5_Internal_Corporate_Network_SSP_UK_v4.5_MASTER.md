<!-- Generated from Generic_NIST_SP800-53r5_Internal_Corporate_Network_SSP_UK_v4.5_MASTER_PROTECTED.docx -->
<!-- Document order, heading hierarchy and tables have been preserved. -->

# Generic Internal Corporate Application System Security Plan

**NIST SP 800-53 Revision 5 / Release 5.2.0 aligned template**

For internally hosted corporate-network applications that may process government, company-confidential, regulated or other restricted information

> **Control statement:** Document status: Controlled corporate security standard - MASTER COPY<br>Standard identifier: GICA-SSP-001<br>Version: 4.5<br>Date: 22 July 2026<br>Classification/handling: Organisation Controlled - Security Documentation<br>Editing status: The normative body of this document must not be altered for individual applications.

> **Template note:** This document describes a defensible standard implementation pattern. It is not an authorisation decision and does not, by itself, establish compliance. Each deployed application must validate applicability, inherited controls, parameter values, evidence, data categories, and legal/contractual obligations.

# Document Control

| **Item** | **Value** |
| --- | --- |
| Document owner | Enterprise Cybersecurity / Governance, Risk and Compliance |
| Approver | Authorizing Official or delegated risk executive |
| Review cycle | At least annually and after significant change, material incident, boundary change, or major control failure |
| Template usage | Mandatory starting point for in-scope applications; deviations are recorded in controlled addenda |
| Normative hierarchy | Applicable law/contract and agency direction; organisational policy; approved system-specific addendum; this generic SSP |

## Record of Changes

| **Version** | **Date** | **Description** | **Owner** |
| --- | --- | --- | --- |
| 1.0 | 22 Jul 2026 | Initial completed generic baseline aligned to NIST SP 800-53 Rev. 5 Release 5.2.0 and current CUI guidance. | Enterprise Security Architecture |
| 1.3 | 22 Jul 2026 | Replaced application-style system identification fields with fixed master-standard scope and applicability statements; application identification remains solely in the Application Addendum. | Enterprise Security Architecture |
| 1.4 | 22 Jul 2026 | Broadened the purpose and business-function wording to make clear that the master applies to all internally hosted corporate application purposes and operating models within the defined network and access scope; examples are illustrative, not limiting. | Enterprise Security Architecture |
| 1.5 | 22 Jul 2026 | Removed the representative application/user-role and scale table from the controlled master because those facts are application-specific and belong in the Application Addendum; renumbered the information-scope section. | Enterprise Security Architecture |
| 1.6 | 22 Jul 2026 | Restored Figure 1 in Section 2 by embedding the generic internal corporate-network application reference architecture in the controlled master. The figure is now presented in both the Word and PDF versions. | Enterprise Security Architecture |
| 1.7 | 22 Jul 2026 | Corrected Figure 1 and the Section 2 topology narrative to show that approved VPN client software is installed on the corporate EUC device. The remote EUC establishes an encrypted tunnel to the corporate VPN gateway and, once authenticated and connected, operates as a corporate-network endpoint using the normal internal application access paths. | Enterprise Security Architecture |
| 1.8 | 22 Jul 2026 | Clarified Section 2 and Figure 1 to state that corporate EUC devices use a hardened, centrally managed Microsoft Windows operating system and may have approved thick-client applications and supporting components installed locally. The corporate EUC security baseline and software-distribution controls apply to both on-site and VPN-connected devices. | Enterprise Security Architecture |
| 1.9 | 22 Jul 2026 | Reworked SI-04 System Monitoring to distinguish inherited enterprise monitoring for network, boundary, EUC, operating system, hosting, identity, SIEM and SOC services from the minimum monitoring duties implemented by each application. Reduced application requirements to security-relevant event generation, contextual logging, central forwarding, a concise monitoring profile, investigation support and proportionate verification. | Enterprise Security Architecture |
| 2.0 | 22 Jul 2026 | Reworked CM-06 Configuration Settings to distinguish enterprise-inherited configuration controls from the minimum application-specific configuration requirements, with proportionate guidance, evidence, monitoring measures and addendum triggers. | Enterprise Security Architecture |
| 2.1 | 22 Jul 2026 | Reworked AC-03 Access Enforcement to distinguish enterprise-inherited device, identity, network, hosting and shared-service controls from the minimum application-specific authorisation requirements. | Enterprise Security Architecture |
| 2.2 | 22 Jul 2026 | Reworked CM-02 Baseline Configuration to distinguish inherited enterprise baselines for EUC, hosting, network and managed services from the minimum application-specific baseline. Added proportionate implementation guidance, evidence, monitoring measures and addendum triggers. | Enterprise Security Architecture |
| 2.3 | 22 Jul 2026 | Reworked AC-06 Least Privilege to distinguish inherited enterprise controls for EUC, identity, PAM, hosting, network and security services from the minimum application-specific requirements. Added proportionate guidance, evidence, monitoring measures and explicit addendum triggers. | Enterprise Security Architecture |
| 2.4 | 22 Jul 2026 | Reworked CM-07 Least Functionality to distinguish inherited enterprise controls for hardened Windows EUC, hosting, network, managed platforms and enterprise software control from the minimum application-specific requirements. Added proportionate guidance, evidence, monitoring measures and explicit addendum triggers. | Enterprise Security Architecture |
| 2.5 | 22 Jul 2026 | Reworked CA-07 Continuous Monitoring to distinguish inherited enterprise monitoring, SOC, vulnerability, configuration, common-control assessment and risk-reporting capabilities from the minimum application-specific monitoring and assurance requirements. Added proportionate guidance, evidence, measures, relationship to SI-04 and addendum triggers. | Enterprise Security Architecture |
| 2.6 | 22 Jul 2026 | Reworked IR-05 Incident Monitoring to distinguish inherited enterprise incident-management, triage, response coordination, evidence handling, external reporting and lessons-learned capabilities from the minimum application-specific incident tracking and documentation requirements. Added proportionate guidance, evidence, measures, adjacent-control relationships and addendum triggers. | Enterprise Security Architecture |
| 2.7 | 22 Jul 2026 | Reworked SI-03 Malicious Code Protection to distinguish inherited enterprise endpoint, server, network, software-distribution and security-response capabilities from the minimum application-specific controls for approved software, file and content handling, active content, quarantine, alerting and testing. Added proportionate guidance, evidence, measures, control relationships and addendum triggers. | Enterprise Security Architecture |
| 2.8 | 23 Jul 2026 | Reworked SC-07 Boundary Protection to distinguish inherited enterprise perimeter, VPN, segmentation, hosting, network-service and boundary-monitoring controls from the minimum application-specific responsibilities. Added proportionate guidance, evidence, monitoring measures, relationships with AC-04 and AC-03, and addendum triggers. | Enterprise Security Architecture |
| 2.9 | 23 Jul 2026 | Reworked AC-04 Information Flow Enforcement to distinguish inherited enterprise network, VPN, gateway, managed-transfer, platform and monitoring controls from the minimum application-specific requirements. Added content-level and destination enforcement, user and service transfer controls, safe failure, evidence, monitoring measures, relationships with SC-07 and AC-03, and explicit addendum triggers. | Enterprise Security Architecture |
| 3.0 | 23 Jul 2026 | Reworked AC-02 Account Management to distinguish inherited enterprise identity, joiner-mover-leaver, authentication, PAM and account-monitoring controls from the minimum application-specific account and entitlement lifecycle requirements. Added proportionate guidance, evidence, monitoring measures, related-control explanation and explicit addendum triggers. | Enterprise Security Architecture |
| 3.1 | 23 Jul 2026 | Reworked SI-07 Software, Firmware, and Information Integrity to distinguish inherited enterprise controls for Windows EUC, hosting, firmware, repositories, code signing, managed platforms and central monitoring from the minimum application-specific integrity requirements. Added proportionate guidance for artefact verification, software provenance, application and information integrity, evidence, monitoring measures, related controls and explicit addendum triggers. | Enterprise Security Architecture |
| 3.2 | 23 Jul 2026 | Reworked IA-02 Identification and Authentication to distinguish inherited enterprise identity, MFA, Windows EUC, VPN, PAM, PKI and machine-identity controls from the minimum application-specific requirements. Added trusted assertion validation, secure session binding, step-up authentication, service authentication, fail-safe behaviour, evidence, monitoring measures, related-control explanation and explicit addendum triggers. | Enterprise Security Architecture |
| 3.3 | 23 Jul 2026 | Reworked AC-05 Separation of Duties to distinguish inherited enterprise controls for identity, PAM, infrastructure administration, release governance, monitoring, backup and key management from the minimum application-specific requirements. Added risk-based conflict identification, maker-checker and release separation guidance, compensating-control principles, evidence, measures, related controls and addendum triggers. | Enterprise Security Architecture |
| 3.4 | 23 Jul 2026 | Reworked CM-05 Access Restrictions for Change to distinguish inherited enterprise controls for EUC, hosting, network, managed platforms, PAM and physical infrastructure from the minimum application-specific controls over source, build, release, configuration, database and production change access. Added proportionate guidance, evidence, monitoring measures, related-control explanation and explicit addendum triggers. | Enterprise Security Architecture |
| 3.5 | 23 Jul 2026 | Reworked RA-05 Vulnerability Monitoring and Scanning to distinguish inherited enterprise assessment of EUC, network, hosting, managed platforms, vulnerability intelligence and patching from the minimum application-specific responsibilities for component inventory, advisory review, dependency and code analysis, authenticated interface testing, configuration assessment, finding prioritisation, remediation and retesting. Added proportionate guidance, evidence, measures, related-control explanation and explicit addendum triggers. | Enterprise Security Architecture |
| 3.6 | 23 Jul 2026 | Reworked CM-08 System Component Inventory to distinguish inherited enterprise inventory for Windows EUC, network, hosting, operating systems, managed platforms and shared services from the minimum application-specific inventory. Added requirements for scope, deployable components, dependencies, stable identifiers, ownership, non-production and supplier components, change-driven updates, reconciliation, lifecycle status, proportionate guidance, evidence, monitoring measures, related controls and explicit addendum triggers. | Enterprise Security Architecture |
| 3.7 | 23 Jul 2026 | Reworked SI-10 Information Input Validation to distinguish inherited enterprise protections from the minimum application-specific validation requirements. Added trust-boundary and input-channel identification, allow-list specifications, authoritative trusted-side validation, contextual business rules, safe parsing and parameterisation, file and structured-content checks, resource limits, safe failure, testing, evidence, measures, related controls and explicit addendum triggers. | Enterprise Security Architecture |
| 3.8 | 23 Jul 2026 | Reworked SI-02 Flaw Remediation to distinguish inherited enterprise patching and update controls for EUC, network, hosting and managed platforms from the minimum application-specific responsibilities. Added requirements for applicability assessment, risk-based prioritisation, treatment, testing, controlled deployment, remediation timescales, verification, end-of-support management, failed or deferred remediation, evidence, measures, related controls and explicit addendum triggers. | Enterprise Security Architecture |
| 3.9 | 23 Jul 2026 | Reworked AC-17 Remote Access to distinguish inherited enterprise controls for the managed Microsoft Windows EUC, approved VPN client and gateway, corporate identity and MFA, network routing, cryptographic protection, privileged access and monitoring from the deliberately minimal application-specific requirements. Clarified that VPN connection extends the corporate network path but does not replace application authentication or authorisation. Added proportionate guidance, evidence, measures, related controls and explicit addendum triggers. | Enterprise Security Architecture |
| 4.0 | 23 Jul 2026 | Reworked CA-08 Penetration Testing to distinguish inherited enterprise governance, authorisation, rules of engagement, infrastructure testing, operational coordination, evidence protection, finding management and retesting from the minimum application-specific requirements. Added risk-based scope and frequency, role and trust-boundary testing, thick-client and multi-tier scenarios, business-logic testing, safety constraints, detection evaluation, proportionate guidance, evidence, measures, related controls and explicit addendum triggers. | Enterprise Security Architecture |
| 4.1 | 23 Jul 2026 | Reworked AC-20 Use of External Systems to distinguish inherited enterprise controls for corporate device ownership, hardened Windows EUC management, identity, VPN, network access, information protection, supplier governance and monitoring from the deliberately concise application-specific requirements. Clarified that a remote, corporately managed EUC device using the approved VPN remains an organisational system, while personal, supplier-owned, public and unmanaged systems are external and prohibited. Added evidence, measures, related-control explanation and explicit addendum triggers. | Enterprise Security Architecture |
| 4.2 | 23 Jul 2026 | Reworked IA-05 Authenticator Management to distinguish inherited enterprise controls for corporate identities, passwords, MFA, Windows EUC, VPN, PAM, PKI and managed secrets from the minimum application-specific management of service credentials, certificates, keys, tokens, emergency authenticators and unavoidable local passwords. Added current password guidance, secure storage, lifecycle events, revocation, recovery, validation, evidence, monitoring measures, related controls and explicit addendum triggers. | Enterprise Security Architecture |
| 4.3 | 23 Jul 2026 | Reworked SC-28 Protection of Information at Rest to distinguish inherited enterprise controls for hardened Windows EUC devices, hosting, storage, managed platforms, backups, key management, physical protection and monitoring from the minimum application-specific requirements. Added data-at-rest location mapping, copy minimisation, application access and segregation, risk-based encryption, thick-client storage, exports and logs, non-production data, integrity, recovery, retention, fail-safe behaviour, evidence, monitoring measures, related-control explanation and explicit addendum triggers. | Enterprise Security Architecture |
| 4.4 | 23 Jul 2026 | Reworked SI-12 Information Management and Retention to distinguish inherited enterprise records, legal, privacy, storage, backup, logging and media-sanitisation controls from the minimum application-specific information-lifecycle requirements. Added authoritative retention mapping, minimisation, duplicate-copy control, event-based retention, holds, active/archive/backup separation, thick-client and non-production copies, disposal, immutable-copy limitations, long-term readability, testing, evidence, monitoring measures, related controls and explicit addendum triggers. Added reference to NIST SP 800-88 Revision 2. | Enterprise Security Architecture |
| 4.5 | 23 Jul 2026 | Reworked SA-11 Developer Testing and Evaluation to distinguish inherited enterprise controls for secure development governance, repositories, build and release services, analysis tooling, test environments, Windows EUC packaging, independent assurance and finding management from the minimum application-specific developer-testing requirements. Added risk-based test strategy, misuse cases, code and dependency analysis, peer review, security-function and interface testing, secure deployment, protected test data, objective release criteria, regression, supplier evaluation, evidence, monitoring measures, related controls and explicit addendum triggers. | Enterprise Security Architecture |

## Approval

| **Role** | **Name / title** | **Decision** | **Date** |
| --- | --- | --- | --- |
| System Owner | [APPLICATION-SPECIFIC] | Approve / Reject | [DATE] |
| Information Owner | [APPLICATION-SPECIFIC] | Approve / Reject | [DATE] |
| System Security Officer | [APPLICATION-SPECIFIC] | Recommend / Do not recommend | [DATE] |
| Authorizing Official | [APPLICATION-SPECIFIC] | Authorize / Authorize with conditions / Deny | [DATE] |

# How to Use This Controlled Master Standard

The generic baseline is intentionally prescriptive: every application is expected to implement the same control outcomes and evidence model as closely as technically and operationally practicable. This version applies only to applications hosted on, and reachable through, the corporate network. It supports managed thick-client, internal thin-client, internal web and multi-tier, physical-server, virtual-machine and approved containerised patterns. It does not cover public-facing, cloud-hosted, cloud-connected, software-as-a-service or hybrid-cloud services.

- Do not populate or edit the master standard. Record application identification, data inventory, actual boundary, interconnections, component inventory, user counts and ownership in the Application Addendum.
- Record inherited enterprise controls and supporting evidence in the Application Addendum; do not modify the corresponding master control statement.
- Apply the generic implementation statements without weakening or editing them. Record product names, actual parameter values and implementation evidence in the Application Addendum.
- Create an Application Addendum for every deployed application. Use it to document conformity as well as all deviations, omissions, non-applicable elements, additional risks, compensating controls, parameter selections and approved exceptions.
- Record control deficiencies in the authoritative POA&M or risk register and cross-reference them from the Application Addendum; never disguise an unimplemented requirement as a harmless architectural variation.
- Assess controls using NIST SP 800-53A procedures and organisation-defined assessment depth and coverage.
## Mandatory master/addendum governance rule

The master standard is not tailored per application. The separately controlled Application Addendum is the only permitted location for application-specific content. It may describe specialised implementation but must not silently reduce a control objective. Every deviation, omission, non-applicable statement or non-standard condition must identify the affected master section or control, the exact difference, business and technical reason, security impact, compensating safeguards, evidence, accountable owner, approving authority, review date and expiry or remediation date. Absence of an addendum entry means the application is asserting full conformity with the master wording.

# 1. Standard Scope and Applicability

**Application identification rule: system name, unique identifier, business owner, information owner, technical owner, security officer, user population, actual categorisation, deployment details and contact information must not be entered into this master. They must be completed in the Application Addendum.**

## 1.1 Purpose of the master standard

This controlled master defines the preferred security architecture, operating model and control implementation for the full range of internally hosted applications used on the corporate network. Its scope is based on where and how an application is hosted, connected, accessed and controlled - not on the business activity that the application performs. It therefore applies to general business, operational, administrative, analytical, engineering, scientific, records and content management, collaboration, communications, security, infrastructure-management, data-processing, integration, reporting and specialist line-of-business applications, together with other internal application functions not specifically named here. These examples are illustrative rather than limiting. The master applies whether an application is organisation-wide, departmental, specialist, high-volume, low-volume, interactive, batch-oriented or primarily machine-to-machine, provided that it remains within the internal corporate-network boundary and the stated access model. It is intentionally application-neutral: it does not identify a particular system, owner, business service, user count or deployment. Those facts are recorded only in the separately controlled Application Addendum. The master is the fixed point of comparison when determining whether an application conforms to the corporate standard.

The master applies to corporate-network applications that are reachable only from corporately managed end-user computing devices connected directly to the corporate network or through the corporate VPN. Permitted patterns include thick-client, internal thin-client, internal web and multi-tier applications hosted on approved physical servers, virtual machines or internally hosted container platforms. Public-facing, cloud-hosted, cloud-connected, software-as-a-service and hybrid-cloud applications are outside scope.

## 1.2 Information scope and handling assumptions

This master assumes that an in-scope application may process government-restricted, company-restricted, personal, regulated, internal or other controlled information. The table below states the preferred generic handling approach; it is not an application data inventory. The Application Addendum identifies the actual information types, owners, markings, legal and contractual obligations, retention periods, authorised disclosures and any categories that are not processed. CUI is permitted only where the application boundary, contract, agency requirements, encryption, incident reporting and authorised user population have been validated.

| **Information class** | **Examples** | **Default handling** |
| --- | --- | --- |
| Government-restricted / CUI | Contract data, controlled technical information, law-enforcement or privacy CUI | Approved CUI environment; access by need-to-know; encryption in transit and at rest; CUI markings and dissemination controls |
| Company restricted | Trade secrets, source code, strategy, security data | Restricted role groups; monitored export; encrypted storage and transmission |
| Personal / regulated | PII, personnel, customer or financial records | Privacy impact review; minimization; retention and disclosure controls |
| Internal | Routine business records | Authenticated access; standard logging and retention |
| Public | Approved public content | May be released only through a separate, approved corporate publication process; the application itself is not publicly accessible |

# 2. System Environment and Boundary

The reference architecture below depicts the broadest permitted deployment for this baseline and is not edited for an individual application. It explicitly shows that corporate EUC devices run a hardened, centrally managed Microsoft Windows operating system and may contain approved locally installed applications, including thick clients. It also distinguishes a corporate EUC device used at a remote location from the corporate network itself. The EUC device contains approved corporate VPN client software, which establishes an encrypted connection to the corporate VPN gateway. After successful corporate-account authentication, multi-factor authentication and device-compliance checks, the device is logically connected to the corporate network and uses the same internal application access paths as an on-site corporate EUC device. A deployment may omit unused tiers or components only where the Application Addendum records the omission and provides the actual architecture, every internal data flow, trust boundary, privileged access path, interconnection and inherited service.

Figure 1. Generic internal corporate-network application reference architecture, including hardened Microsoft Windows EUC devices, locally installed approved thick-client applications and the remote corporate EUC VPN connection path. The dashed outline denotes the corporate network security boundary. A remote EUC device remains outside that physical boundary until its installed VPN client establishes an encrypted tunnel to the corporate VPN gateway; once connected, it operates as a corporate-network endpoint for access to internal applications.

## 2.1 Topology narrative

- Users access applications only from corporately managed end-user computing (EUC) devices running a hardened, centrally managed Microsoft Windows operating system. These devices may have approved thick-client applications and supporting components installed locally through the corporate software-distribution service. They may also use an approved corporate browser or thin-client software to access internal web, presentation and multi-tier services. An EUC device may be connected directly to the corporate network at a corporate location, or it may connect from a remote location using approved VPN client software installed and managed on that device. The Windows build, security configuration, endpoint protection, full-disk encryption, application control, patching, local firewall, logging and device-compliance settings are enforced through the corporate EUC baseline. Users do not receive local administrator rights unless a formally approved exception is recorded. Personally owned, unmanaged, supplier-managed and public-access devices are prohibited.
- Remote user access is permitted only from a corporately managed EUC device using the approved VPN client installed on that device. The client establishes an encrypted tunnel to the corporate VPN gateway and requires a corporate account, multi-factor authentication and device-compliance checks. Once the VPN session is established, the EUC device is logically connected to the corporate network and operates, for application-access purposes, in the same manner as an EUC device connected directly at a corporate location. Application traffic then follows the normal internal corporate-network paths and remains subject to the same application authorisation, segmentation, logging and monitoring controls. Split tunnelling and direct inbound administration are prohibited.
- Internal presentation components may use approved internal reverse proxies and load balancers. Web application firewalls or equivalent application-layer inspection may be used where risk warrants. All listeners use internal addresses and corporate name resolution; no public DNS record, public address, Internet-facing listener or externally routed gateway is permitted.
- Application services run on hardened physical servers, virtual machines or approved internally hosted container platforms. Administrative access is available only through the segregated management network, privileged access management controls and authorised corporate administrator workstations. Serverless and cloud-managed platforms are outside this baseline.
- Data services use approved internal database, file, cache and messaging technologies. Restricted data is encrypted where required, backed up, access-controlled, monitored and retained according to records requirements. Application data is not stored in or synchronised to cloud services under this baseline.
- Interconnections are limited to authorised corporate-network systems and enterprise services. Every interface is documented by source, destination, protocol, purpose, data classification and owner. Connections to partner networks, the Internet, cloud services or externally hosted services are prohibited unless the system is moved to a different approved security baseline.
- Logs and security telemetry are forwarded to centralised security monitoring. Configuration, vulnerability, endpoint, network, and integrity data are correlated in the SIEM and case-management systems.
- Development and deployment use segregated environments, reviewed code, automated security testing, signed artefacts, protected branches, and controlled promotion into production.
## 2.2 Component inventory baseline

| **Component class** | **Minimum inventory attributes** | **Authoritative source** |
| --- | --- | --- |
| Hardware / virtual resources | Owner, hostname, serial/instance ID, location, platform, criticality, support status | CMDB / internal asset inventory |
| Operating systems / firmware | Product, version, patch level, baseline, EOL date | Endpoint/server management and CMDB |
| Application software | Product/build, owner, package source, licence, SBOM reference | Software catalogue / artefact registry |
| Containers / images | Digest, base image, build pipeline, scan status, deployment target | Container registry / orchestration inventory |
| Databases / storage | Engine, version, data class, encryption, backup, owner | Database catalogueue / internal storage inventory |
| Network / security devices | Device, interface, zone, rule set, firmware, owner | Network source of truth / firewall manager |
| Accounts / identities | Identity type, owner, purpose, privilege, credential age | IAM / PAM / directory |
| External services / APIs | Provider, data exchanged, auth method, agreement, owner | Third-party register / API catalogue |

## 2.3 Common-control inheritance

The system may inherit portions of identity, physical protection, personnel security, security awareness, enterprise logging, endpoint protection, vulnerability scanning, network boundary protection, backup, incident response, key management, and configuration management. Inheritance is not assumed: each application records the provider, service scope, control responsibility, service-level commitment, evidence source, and any residual implementation responsibility.

# 3. Security Governance and Operating Model

| **Role** | **Accountability** |
| --- | --- |
| Authorizing Official | Accepts residual risk and issues authorisation decision. |
| System Owner | Funds and operates the system; approves access and risk decisions within delegation. |
| Information Owner / Data Steward | Defines use, sensitivity, sharing, retention, and access criteria. |
| ISSO / Security Manager | Maintains SSP, coordinates assessment, monitors risk, validates evidence. |
| Control Owner | Defines enterprise control implementation and evidence. |
| Application Owner | Implements system-specific responsibilities and produces evidence. |
| Change Advisory Board | Approves significant and emergency changes according to risk. |
| SOC / Incident Response | Monitors, investigates, contains, reports, and learns from incidents. |
| Privacy / Legal / Records | Confirms privacy, legal hold, records, export, and contractual obligations. |

## 3.1 Standard security parameters

| **Parameter** | **Generic baseline** |
| --- | --- |
| MFA | Required for privileged access, remote access, and access to restricted data; phishing-resistant methods preferred and required where policy/agency direction specifies. |
| Session inactivity | 15 minutes for privileged/admin interfaces; 30 minutes for standard restricted-data sessions unless stricter policy applies. |
| Account review | Privileged monthly; standard quarterly; service accounts at least quarterly and on owner/role change. |
| Vulnerability scanning | Authenticated internal infrastructure at least monthly; code, dependency and container scans on build and before release; periodic verification that no unintended external exposure exists. |
| Critical flaw remediation | Emergency/risk-based target, normally 15 calendar days or faster for active exploitation; high within 30 days; exceptions documented. |
| Log retention | At least 90 days readily searchable and one year retained, or longer when contract, investigation, privacy, or records schedules require. |
| Backup testing | At least quarterly for representative restores; annually for full recovery scenario; more frequently for high criticality. |
| Penetration testing | At least annually and after major architectural change for high-risk internal systems; scope includes internal user, VPN, administrative and segmentation attack paths. |
| Configuration compliance | Continuous or daily where tooling supports; formal review at least monthly. |
| SSP review | At least annually and after significant change. |

# 4. Detailed Control Implementations

> **Template note:** MASTER TEXT CONTROL: Do not alter any control statement, architecture-specific application, evidence expectation, measure or addendum trigger below. Record every application-specific difference exclusively in the Application Addendum.

The following sections provide the normative generic implementation baseline for the controls specifically requested. Control titles and identifiers align to NIST SP 800-53 Rev. 5 / Release 5.2.0. These implementation statements are fixed corporate-standard text and must not be edited for an individual application. The Application Addendum records actual implementation, evidence, inherited elements, omissions, deviations and approved exceptions by explicit cross-reference.

## SI-04 - System Monitoring

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

### Control intent and responsibility model

SI-04 requires monitoring that can detect attacks, indicators of potential attacks, unauthorised local, network and remote connections, and unauthorised use; it also requires detected events and anomalies to be analysed and the monitoring level to be adjusted when risk changes. In this corporate model, monitoring is deliberately divided between enterprise-provided capabilities and a small set of application-specific duties. This avoids requiring every application team to recreate network, endpoint, operating-system or security-operations tooling while ensuring that the application supplies the events and context that only the application can reliably provide. This implementation is aligned with the control and assessment objectives in NIST SP 800-53 and SP 800-53A [1][2].

### Inherited enterprise monitoring

The following capabilities are inherited common controls. They are designed, operated and evidenced by the responsible enterprise infrastructure or security service owner, rather than being separately implemented by each application:

- Network and boundary monitoring: corporate firewalls, network intrusion detection or network detection and response, network-flow telemetry, internal segmentation controls, DNS and proxy services where used, and VPN gateway monitoring identify unauthorised connections, suspicious traffic and boundary-policy violations.
- Corporate EUC and server monitoring: centrally managed endpoint detection and response, anti-malware, Microsoft Windows security logging, host firewall telemetry, device-compliance monitoring and approved software-execution controls monitor hardened corporate EUC devices and supported server operating systems.
- Hosting and platform monitoring: enterprise teams monitor physical hosts, virtualisation platforms, storage, backup infrastructure, databases and middleware where these are supplied as managed enterprise services. Platform-native logs are forwarded through approved central collection mechanisms.
- Identity and privileged-access monitoring: the corporate identity service, multi-factor authentication service, directory service, privileged-access tooling and VPN service monitor authentication, account, group, privilege and remote-access activity.
- Central analysis and response: enterprise time synchronisation, protected log transport and storage, the security information and event management service, enterprise detection rules and the Security Operations Centre provide correlation, alerting, triage, escalation and monitoring-health oversight.
### Application-specific minimum requirements

Each application must implement only the monitoring functions that require knowledge of its own users, permissions, transactions, data and business logic. The minimum application-specific set is:

1. Generate security-relevant application events. At minimum, record application authentication outcomes where authentication occurs within the application; authorisation failures; use of administrative or privileged functions; changes to application-managed accounts, roles or permissions; changes to security-relevant configuration; security-validation failures; and significant data export, bulk retrieval or other high-risk actions supported by the application. Events that do not apply to the application need not be manufactured, but the omission must be evident from the application logging matrix.
1. Include sufficient context. Each event must include an accurate timestamp derived from the enterprise time service, the user or service identity, the application/component, the action attempted or completed, the outcome, and a suitable object, record or transaction reference. Logs must not contain passwords, authentication secrets, cryptographic keys or unnecessary restricted data.
1. Send events to the enterprise monitoring service. Security-relevant events must be forwarded using an approved, reliable mechanism to the enterprise log collector or SIEM. Where direct forwarding is not technically possible, an approved intermediary or agent must be used. Loss of logging or repeated forwarding failure must be detectable.
1. Define the application monitoring profile. The application owner must maintain a concise logging and monitoring matrix identifying required event types, event sources, log destinations, responsible owners, retention classification and any application-specific alert conditions. Application-specific alerts should be limited to credible misuse or compromise scenarios that enterprise infrastructure monitoring cannot identify without business context.
1. Support investigation and tuning. The application support team must assist the SOC or incident-response team by interpreting application events, identifying expected behaviour, validating suspicious activity and preserving relevant application evidence. It must also correct excessive, missing or misleading logging through the normal change process.
1. Verify monitoring after material change. Logging and forwarding must be tested when the application is first onboarded, after material changes to authentication, authorisation, interfaces, data flows or logging components, and periodically under the continuous-monitoring schedule.
### Proportionate implementation guidance

An application is not normally required to deploy its own intrusion-detection platform, endpoint agent, network sensor, SIEM, separate monitoring dashboard or duplicate operating-system monitoring. These remain enterprise responsibilities unless the application has a specialised risk or technology that the inherited services cannot monitor. Routine performance and availability monitoring may be integrated with SI-04 evidence where useful, but operational monitoring alone does not satisfy the security-monitoring requirement.

### Expected evidence and assessment artefacts

- Application logging and monitoring matrix showing the minimum event set, sources, destinations and ownership split
- Evidence that required application events are generated with suitable identities, timestamps, outcomes and transaction context
- SIEM or central-log onboarding record, including a sample end-to-end event and confirmation that loss of event flow is detectable
- Application-specific alert or detection rules, where required by the monitoring profile, together with test or tuning evidence
- Cross-reference to the inherited enterprise monitoring services and their common-control evidence
### Continuous monitoring and measures

- Required application event types successfully received by the central monitoring service
- Age and result of the latest end-to-end logging test
- Unresolved application logging failures or material gaps
- Application-specific security alerts reviewed within the agreed service level, where such alerts are defined
### Addendum trigger

> **Template note:** Use an addendum when the application cannot generate or forward one or more applicable minimum events; requires monitoring that is not provided by the inherited enterprise services; contains a specialised protocol, appliance or technology needing additional sensors; cannot provide the required identity or transaction context; or needs logging restrictions because of performance, legal, privacy or data-minimisation constraints. The addendum must identify the gap, rationale, risk, compensating monitoring, owner and approval.

## CM-06 - Configuration Settings

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

### Control objective and allocation

CM-06 requires the organisation to establish and document secure configuration settings for system components, implement those settings, identify and approve deviations, and monitor or control changes to the settings. For this standard, responsibility is deliberately divided between enterprise-managed technology and configuration that only the application team can define because it depends on the application design, business logic or data.

### Enterprise-inherited configuration controls

The following settings and enforcement mechanisms are normally provided as enterprise common controls. The application inherits them when it uses the approved corporate platforms and services:

- Corporate EUC configuration. Hardened Microsoft Windows builds, Group Policy, endpoint-management policies, full-disk encryption, host firewall, endpoint protection, application control, browser configuration, corporate certificate stores, VPN client settings, screen locking and operating-system audit policy are defined and enforced by the enterprise EUC service.
- Server and hosting-platform configuration. Approved Windows or Linux server builds, virtual-machine templates, hypervisor settings, firmware standards, endpoint protection, host firewalls, time synchronisation, operating-system logging, backup agents and infrastructure-management agents are maintained by the enterprise hosting service.
- Network and boundary-device configuration. Routers, switches, firewalls, load balancers, VPN gateways, network access control, segmentation controls and enterprise DNS, DHCP and time services are configured and maintained by the relevant enterprise network teams.
- Enterprise identity and security-service configuration. Directory services, multi-factor authentication, privileged-access management, public key infrastructure, central logging, SIEM, vulnerability scanning, software distribution and other shared security services are configured by their service owners.
- Enterprise database, middleware and platform defaults. Where an approved centrally managed database, web server, application server, messaging service or similar platform is supplied, its secure base settings, patch level and standard administrative controls are maintained by the platform owner.
- Configuration enforcement and drift monitoring. Enterprise tools apply approved baselines, identify unauthorised or accidental changes and raise remediation work. Application teams consume the resulting service and evidence rather than duplicating the same control tooling.
The enterprise service owner remains accountable for the common-control evidence, baseline maintenance and correction of drift for these inherited elements. The application owner must confirm that the application is deployed only on supported enterprise services and must identify any inherited control that is unavailable or not applicable.

### Minimum application-specific configuration requirements

Each application must define and control only the security-relevant settings that are unique to the application or that cannot sensibly be imposed by an enterprise platform. The minimum application-specific set is:

1.  Maintain an application configuration specification. Record the approved security-relevant settings, their permitted values or ranges, the component or environment to which they apply, the setting owner and the method used to enforce them. The specification may be concise and may be held as configuration-as-code, deployment manifests or a controlled configuration register.

2.  Use secure defaults. New installations and new environments must start from the approved secure configuration. Features, demonstration accounts, sample data, debugging functions and interfaces that are not required for the approved business purpose must be disabled or removed.

3.  Protect authentication and session settings owned by the application. Where the application manages them, define suitable session time-outs, lockout behaviour, cookie and token properties, re-authentication conditions, service-account use and other application-level authentication parameters. Where these are wholly provided by the enterprise identity service, they are inherited and need not be duplicated.

4.  Protect application authorisation and administrative settings. Role definitions, privilege mappings, administrative functions, workflow approvals, data-access rules and security-relevant feature flags must be explicitly configured, access-controlled and changed only through the approved change process.

5.  Configure interfaces and data handling securely. Enable only required internal interfaces, protocols and integration endpoints; use approved encryption and certificate validation where applicable; restrict allowed origins, hosts and calling services; and set upload, export, query, message-size and similar limits where they reduce credible misuse or failure risk.

6.  Control secrets and sensitive configuration values. Passwords, API keys, private keys and other secrets must not be stored in source code or ordinary configuration files. They must be obtained from an approved enterprise secret-management or credential service where available, and access must be limited and auditable.

7.  Separate environments and prevent unsafe promotion. Development, test and production settings must be distinguishable and controlled. Debugging, verbose error output, test credentials and non-production integrations must not be enabled in production unless specifically approved.

8.  Validate configuration at deployment and after material change. Automated checks should be used where proportionate. At minimum, the application team must verify that the approved settings are present following initial deployment, significant upgrades, migration, restoration and changes to security-relevant configuration.

### Proportionate implementation guidance

An application is not normally required to create a second operating-system, network-device, EUC or enterprise-service baseline. Nor is it expected to duplicate Group Policy, endpoint-management, vulnerability-management or infrastructure configuration tooling. A small application may satisfy its application-specific responsibility with a short controlled settings register and deployment checklist. A larger or multi-tier application should normally use version-controlled configuration-as-code, deployment pipelines and automated validation. The amount of documentation and automation should reflect the number of components, frequency of change and consequence of misconfiguration.

### Expected evidence and assessment artefacts

- Application configuration specification or configuration-as-code identifying the security-relevant application settings and approved values
- Cross-reference to the applicable enterprise EUC, server, network, identity and platform baselines and their common-control owners
- Evidence that production deployments use the approved settings, such as deployment records, automated policy results, configuration exports or a completed validation checklist
- Change records for material security-configuration changes, including review and approval
- Current application-specific exception or deviation records, including expiry date, risk owner and compensating controls where relevant
- Evidence that secrets and sensitive configuration values are held and accessed through approved mechanisms
### Continuous monitoring and measures

- Percentage of in-scope application components confirmed against the approved application configuration
- Number and age of unresolved application-specific configuration deviations
- Failed or overdue configuration-validation checks following deployment or material change
- Expired application configuration exceptions
- Security incidents or defects attributable to incorrect application configuration
### Addendum trigger

> **Template note:** Use an addendum when the application cannot use an applicable enterprise baseline or service; requires a weaker, different or additional security setting; retains a feature, protocol, account or interface that the standard approach disables; cannot enforce or validate one or more applicable application settings; uses a specialised appliance, legacy component or vendor-controlled configuration; or needs a time-limited exception. The addendum must identify the affected setting, standard value or approach, implemented value or approach, technical and business rationale, security risk, compensating controls, owner, approval and review or expiry date.

## AC-03 - Access Enforcement

### Control objective and responsibility model

AC-03 requires approved logical-access authorisations to be enforced for information and system resources in accordance with the applicable access-control policies. In this corporate model, responsibility is divided between enterprise controls that establish and enforce access to devices, networks, operating systems and shared services, and a small set of application-specific controls that enforce what an authenticated user or service is permitted to see and do within the application. This avoids duplicating enterprise identity and infrastructure controls while retaining clear application accountability for business functions, records, transactions and data. This implementation is aligned with the control and assessment objectives in NIST SP 800-53 and SP 800-53A [1][2].

### Inherited enterprise access-enforcement controls

The following capabilities are inherited common controls when the application uses approved corporate platforms and services. They are designed, operated and evidenced by the relevant enterprise service owner rather than recreated by each application:

- Corporate EUC access. Hardened Microsoft Windows devices, device-management controls, local operating-system permissions, host firewalls, application control and device-compliance checks restrict use of corporate EUC devices and the software installed on them.
- Corporate identity and authentication. Directory services, corporate accounts, multi-factor authentication, account status, group membership, privileged-access management and authentication policy establish verified identities and enterprise-managed access conditions.
- Network and remote-access enforcement. Network access control, segmentation, firewalls, routing, VPN gateways and approved internal access paths restrict which managed devices and network zones can reach application components. Remote access is permitted only through the approved corporate VPN from a compliant corporate EUC device.
- Server, database and platform administration. Enterprise hosting, operating-system and managed-platform services restrict administrative access to authorised support personnel through approved privileged accounts, management networks and tooling.
- Shared-service permissions. Enterprise-managed databases, file services, messaging platforms, secrets services, certificate services and similar shared capabilities enforce their own platform-level permissions and service-access policies.
- Central logging and oversight. Enterprise logging, SIEM, identity monitoring and privileged-session monitoring provide evidence of authentication, platform administration and network access decisions, including denied attempts and changes to enterprise-managed groups or privileges.
The enterprise service owner remains accountable for the design, operation and evidence of these common controls. The application owner must confirm which controls are inherited, use only supported enterprise access paths, and record in the Application Addendum any inherited capability that is unavailable, materially different or insufficient for the application risk.

### Minimum application-specific access-enforcement requirements

Each application must implement only the access decisions that depend on its own business functions, data, records, transactions or application-managed privileges. The minimum application-specific set is:

1.  Define application roles and permissions. Maintain a concise role and permission model that identifies the application functions, information and administrative capabilities available to each role or service identity. Permissions must be based on approved business need and must not be inferred solely from interface visibility.

2.  Enforce authorisation on the trusted side. Every protected function and data request must be checked by the application service, server-side component or authoritative data layer. A hidden button, disabled menu option or other client-side restriction is not sufficient. Thick clients must therefore be treated as untrusted for authorisation purposes.

3.  Deny access unless explicitly permitted. New users, roles, functions, interfaces and data objects must not become accessible by default. Where a user has several roles, the resulting permissions must be predictable, documented and tested so that role combinations do not create unintended access.

4.  Control access to functions and data at the necessary level. The application must enforce access to administrative functions, business operations, records, files, reports, exports and other protected objects. Multi-tier and web applications must prevent function-level and object-level access-control failures, including access obtained by changing a URL, object identifier, request parameter or API call.

5.  Use approved identities for automated activity. Batch processes, scheduled tasks, interfaces and service-to-service calls must use dedicated workload or service identities with only the permissions required for the approved function. Shared human accounts and embedded personal credentials are prohibited.

6.  Protect privileged and high-risk actions. Application administration, role assignment, security-setting changes, bulk export, destructive actions and other high-risk operations must be restricted to specifically authorised roles. Additional approval, re-authentication or separation of duties must be used where required by the business risk or another control.

7.  Fail securely. If identity, group, policy, entitlement or authorisation information is unavailable, invalid or ambiguous, the application must deny the protected action or enter a documented safe state rather than granting access.

8.  Record material access decisions. The application must log authorisation failures and use of application-level privileged or high-risk functions in accordance with the application logging matrix. Routine successful access need only be logged where it supports accountability, investigation, legal requirements or credible misuse detection.

### Proportionate implementation guidance

An application is not normally required to implement a separate identity provider, VPN, network access-control system, privileged-access platform or operating-system permission model. Those capabilities are inherited. A small application may use a simple role-to-function matrix and server-side role checks. A larger or multi-tier application may require centralised policy components, API scopes, record-level rules or attribute-based decisions. The mechanism may vary, but the minimum outcome is the same: an authenticated identity can perform only the approved application functions and access only the approved application information. The application must not rely solely on network location, possession of a corporate device or successful corporate authentication as proof that a particular business action is authorised.

### Expected evidence and assessment artefacts

- Application role and permission matrix, including application administrators, support roles, ordinary users and service identities
- Description of where server-side authorisation is enforced for thick-client, web, thin-client, batch and service interfaces that apply
- Sample approved access assignments or access-request records and a cross-reference to enterprise identity groups where used
- Authorisation test evidence covering permitted access, denied access, direct object or function requests, role changes and relevant role combinations
- Evidence that privileged and high-risk application functions are restricted and logged
- Cross-reference to inherited enterprise identity, EUC, VPN, network, hosting and privileged-access common controls
### Continuous monitoring and measures

- Completion and outcome of scheduled application access reviews
- Unresolved excessive, orphaned or conflicting application permissions
- Authorisation failures or suspected access-control misuse requiring investigation
- Open access-control defects found through testing, vulnerability assessment or incident review
- Age and result of the latest material authorisation test following a significant role, interface or data-access change
### Addendum trigger

> **Template note:** Use an addendum when the application cannot enforce one or more applicable minimum requirements; relies on a legacy or vendor-controlled authorisation mechanism; permits discretionary sharing or delegation not covered by the standard role model; uses unusual role combinations, service identities or record-level rules; must remain available when an authorisation dependency is unavailable; or requires weaker, additional or materially different access enforcement. The addendum must identify the affected access path or function, standard requirement, implemented approach, rationale, risk, compensating controls, owner, approval and review or expiry date. External identity providers, public access and cross-organisation or cross-tenant access remain outside this baseline.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## CM-02 - Baseline Configuration

### Control objective and responsibility model

CM-02 requires an approved, documented and current baseline configuration for the system, maintained under configuration control and reviewed when defined events occur. The baseline describes the agreed state from which components are built, deployed, operated and restored. In this corporate model, the enterprise owns the baselines for shared hardware, networks, operating systems and managed platforms. Each application owns only the baseline information needed to define its application software, application-controlled configuration and deployment. This allocation avoids duplicating enterprise build standards while preserving a reproducible and assessable application state. This implementation is aligned with the control and assessment objectives in NIST SP 800-53 and SP 800-53A [1][2].

### Inherited enterprise baseline configurations

The following baseline configurations are inherited common controls when the application uses approved corporate infrastructure and services. They are established, maintained and evidenced by the relevant enterprise service owner rather than recreated in each application baseline:

- Corporate EUC baseline. The enterprise EUC service maintains the approved hardened Microsoft Windows build, firmware and driver standards, device-management policies, security agents, corporate browser and VPN client, approved supporting software and standard configuration applied to corporate EUC devices. Application-specific thick-client software may be added through the controlled corporate software-distribution process.
- Server and hosting baseline. Enterprise hosting teams maintain approved physical-server, virtual-machine and supported server operating-system images; hypervisor and management settings; firmware; storage, backup and monitoring agents; and standard post-deployment configuration.
- Network baseline. Enterprise network teams maintain approved configurations for routers, switches, firewalls, network segmentation, load balancers, VPN gateways, DNS, DHCP, time services and management networks.
- Managed platform and enterprise-service baseline. Where supplied as managed services, the enterprise owner maintains the baseline for databases, middleware, messaging, file services, identity services, PKI, secrets services, central logging, vulnerability scanning, endpoint protection and software distribution.
- Infrastructure inventory and lifecycle records. Enterprise asset, configuration-management and service-management repositories record the approved infrastructure components, versions, ownership, support status and applicable enterprise baseline.
The application owner must identify the inherited services used by the application and cross-reference their common-control evidence. The application must not reproduce the complete enterprise Windows, server, network or managed-platform baseline in its own documentation.

### Minimum application-specific baseline requirements

Each application must maintain a concise application baseline covering only the software and configuration that the application team owns or controls. The minimum application-specific set is:

1.  Define the approved application composition. Identify the application release, deployable components, locally installed thick-client package where applicable, internal web or service components, application-owned scheduled tasks or services, required runtime and middleware dependencies, database schema or migration level, and approved internal interfaces.

2.  Define application-controlled configuration. Record the approved production values or controlled references for security-relevant application settings, feature states, service endpoints, ports used by the application, identity and role integration, logging destinations, certificate or secret references, data locations and retention-related settings. Secret values themselves must not be placed in the baseline document.

3.  Use controlled and identifiable artefacts. Application binaries, packages, scripts, database migrations, deployment definitions and configuration templates must have an approved version or immutable identifier and be held in an authorised repository. Thick-client packages must be distributed through the corporate software-distribution service; internally hosted virtual machines or containers must use approved enterprise templates and controlled application deployment artefacts.

4.  Keep environments distinct. Production, development and test baselines must be distinguishable. Non-production must not silently become the source of production settings, credentials or restricted data, and production deployment must use the approved production baseline.

5.  Approve and retain baseline changes. Changes to the application baseline must follow the normal change process, include appropriate testing and approval, and update the baseline record at or before release. The current baseline and sufficient prior versions must be retained to support rollback, investigation and reconstruction.

6.  Review the baseline at defined triggers. Review and update it after a material application release, architecture or interface change, significant vulnerability remediation, platform migration, recovery exercise, incident finding, unsupported dependency or other change that affects the approved application state. A periodic review must also confirm that the recorded baseline remains current.

7.  Verify deployed state against the baseline. Confirm during release and periodically thereafter that the deployed application version, components and material application-controlled settings match the approved baseline. Unauthorised drift must be investigated and corrected or formally documented as a deviation.

### Proportionate implementation guidance

A small application may satisfy CM-02 with an approved release record, component list, configuration register and deployment checklist. A larger multi-tier application should normally use version-controlled deployment definitions, automated build and release pipelines, database migration records and automated comparison of deployed versions or configuration. The application is not required to copy enterprise golden-image specifications, Windows Group Policy, firewall standards or hypervisor settings into its baseline. It must, however, record which approved enterprise baseline or managed service it depends upon.

### Expected evidence and assessment artefacts

- Approved application baseline or release manifest identifying application components, versions, dependencies, schema level and applicable deployment artefacts
- Application-controlled configuration specification or register, excluding secret values
- Version-controlled source, package, deployment and database-migration records with release approval
- Evidence of thick-client software distribution or server-side deployment through approved enterprise mechanisms, as applicable
- Deployment or validation evidence showing that the installed application state matches the approved baseline
- Cross-reference to inherited EUC, hosting, network, platform and enterprise-service baselines
### Continuous monitoring and measures

- Production application releases mapped to a current approved baseline
- Age and result of the latest application baseline review
- Unresolved differences between the approved baseline and deployed application state
- Unsupported or unapproved application components and dependencies
- Rollback or reconstruction test outcome where required by the release or recovery process
### Addendum trigger

> **Template note:** Use an addendum when the application cannot maintain one or more applicable minimum baseline elements; contains a legacy, vendor-controlled or specialist component that cannot be versioned, reproduced or compared with the approved state; requires a production configuration that differs from the standard enterprise platform; uses manual deployment where the resulting state cannot otherwise be reliably demonstrated; or must temporarily operate with an unapproved or unsupported component. The addendum must identify the affected component or setting, standard approach, implemented approach, rationale, risk, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## AC-06 - Least Privilege

### Control objective and responsibility model

AC-06 requires privileges to be limited to the minimum necessary for users, administrators, services, processes and devices to perform approved duties. Privileged access must be separately controlled, used only when required, and attributable to an authorised individual or technical identity. In this corporate model, the enterprise provides the common controls that limit operating-system, network, hosting-platform and enterprise-service privileges. Each application remains responsible for limiting application roles, administrative functions, service identities and access to application data. This implementation also supports the related NIST expectations for explicitly authorising security functions, using non-privileged accounts for non-security work, restricting privileged accounts, preventing non-privileged users from performing privileged functions, and recording the execution of privileged functions [1][2].

### Inherited enterprise least-privilege controls

The following capabilities are inherited when the application uses approved corporate EUC, hosting, identity, network and security services. They are implemented and evidenced by the relevant enterprise service owner rather than duplicated by the application team:

- Corporate EUC privilege control. Users normally operate hardened Microsoft Windows EUC devices without local administrator rights. Approved software is installed through managed distribution processes, and temporary or exceptional elevation is controlled, time-limited where supported, logged and reviewed.
- Enterprise identity and privileged access management. Corporate accounts, privileged administration accounts, multi-factor authentication, account lifecycle controls, privileged credential checkout or session brokering, emergency-access procedures and central entitlement reviews are provided through enterprise identity and PAM services where available.
- Server, virtualisation and platform administration. Operating-system, hypervisor, storage, backup, database-platform, middleware and infrastructure administration rights are restricted to approved support roles using dedicated administration paths and accounts. Application users and ordinary application administrators do not receive these infrastructure privileges.
- Network and security-service administration. Firewall, router, switch, VPN, load-balancer, PKI, SIEM, EDR, vulnerability-scanning and other enterprise security-service privileges are assigned and monitored by the owning enterprise teams.
- Central monitoring and accountability. Enterprise logging, identity, PAM and security-monitoring services record privileged sign-in, elevation and administration activity within the services they manage and support investigation of suspected misuse.
The application owner must identify the inherited services and privileged roles on which the application depends. The application must not create local operating-system, database-platform or network privileges merely to avoid the established enterprise administration process.

### Minimum application-specific least-privilege requirements

Each application must implement the following minimum set for the functions, identities and data that it owns or controls:

1.  Define application roles and privilege boundaries. Maintain a concise role-and-permission model that distinguishes ordinary users, business approvers, support users, application administrators, auditors and technical service identities as applicable. Each role must contain only the functions and data access needed for its approved purpose.

2.  Separate ordinary use from administration. Users and support personnel must use standard application roles for routine work and a separate privileged role or account for administration. Administrative functions must not be available merely because a user is connected to the corporate network or has a privileged Windows or infrastructure account.

3.  Restrict privileged application functions. Functions such as role assignment, security-configuration change, bulk export, data correction, retention override, audit-log administration, interface activation and other high-impact actions must be limited to explicitly authorised roles. Where risk warrants it, sensitive actions must require approval, step-up authentication or dual control.

4.  Minimise service and process privileges. Each application service, scheduled task, integration, database connection and background process must use a dedicated technical identity where practicable and receive only the permissions, data access and network access required for that function. A service identity must not normally be shared across unrelated applications, environments or tiers.

5.  Avoid unnecessary platform privilege. Application components must run without local administrator, root, database-owner or equivalent platform-wide rights unless technically necessary and approved. Thick clients must run under the user's standard Windows context; server-side components must use the least privileged supported execution identity; database access must use narrowly scoped roles rather than unrestricted administrative accounts.

6.  Protect privileged credentials and secrets. Application administrative credentials, service-account secrets, keys and tokens must be stored and retrieved through approved enterprise mechanisms, scoped to a single purpose and environment, and not embedded in source code, scripts, packages or user-readable configuration.

7.  Make privilege temporary where practical. Time-bound, just-in-time, checked-out or otherwise controlled privileged access should be used for infrequent support and maintenance activities. Permanent high privilege must be limited to the smallest practicable group and justified by operational need.

8.  Review and remove privilege. Application entitlements, privileged roles and technical identities must have an owner and be reviewed at a frequency proportionate to risk and after relevant joiner, mover, leaver, supplier, role or system changes. Unused, excessive, conflicting or orphaned access must be removed promptly.

9.  Record privileged activity. The application must log successful and failed use of privileged application functions with the acting identity, action, target, outcome and time. Logging must be forwarded to the enterprise monitoring service where technically supported and must not expose credentials or restricted data unnecessarily.

### Proportionate implementation guidance

A small application may satisfy AC-06 through a simple role matrix, separate user and administrator roles, a small number of dedicated service identities and a periodic access review. A complex multi-tier application should normally use centrally managed groups, granular application roles, separate identities per service and environment, automated entitlement provisioning, PAM-supported administration and application-level privileged-event logging. Least privilege does not require a unique role for every individual; it requires roles and technical identities to be no broader than the approved duties they serve.

### Expected evidence and assessment artefacts

- Approved application role and permission matrix, including privileged functions
- List of application administrators, privileged support roles and approving owners
- Service and technical identity inventory showing purpose, owner, environment and permissions
- Evidence that thick clients and server-side components run without unnecessary elevated rights
- Entitlement review results and records of removed or corrected access
- Privileged application activity logs and evidence of forwarding to enterprise monitoring
- Cross-reference to inherited corporate identity, PAM, EUC, hosting and platform controls
### Continuous monitoring and measures

- Number of standing privileged application accounts and roles
- Privileged access reviews completed on time
- Orphaned, dormant or ownerless privileged and service identities
- Service identities shared across applications or environments
- Application components running with local administrator, root, database-owner or equivalent rights
- Privileged functions not represented in the role matrix or not producing audit events
- Excessive privileges identified and removed
### Addendum trigger

> **Template note:** Use an addendum when a legacy or supplier-controlled application requires shared, generic or permanently privileged accounts; a component must run with local administrator, root, database-owner or similarly broad rights; a service identity must be shared across applications or environments; separate administrative and ordinary use cannot be enforced; privileged activity cannot be individually attributed or logged; or the application cannot use the approved corporate identity or PAM service. The addendum must identify the affected role, account, component or function; the standard approach; the implemented approach; rationale; risk; compensating controls; owner; approval; and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## CM-07 - Least Functionality

### Control objective and responsibility model

CM-07 requires the system to provide only the capabilities needed for its approved business purpose and to prohibit or restrict unnecessary functions, ports, protocols, software and services. Reducing functionality reduces the attack surface, limits opportunities for misuse and makes the approved operating state easier to understand and monitor. In this corporate model, enterprise service owners minimise and control the functionality of managed EUC devices, networks, operating systems, hosting platforms and shared security services. Each application remains responsible for limiting the application features, components, interfaces, dependencies and execution paths that it owns or selects. This implementation reflects the CM-07 control and its assessment objectives, together with NIST guidance on security-focused configuration management [1][2][3].

### Inherited enterprise least-functionality controls

The following capabilities are inherited when the application uses approved corporate infrastructure and services. They are implemented and evidenced by the relevant enterprise service owner rather than recreated by each application team:

- Corporate EUC build. Hardened Microsoft Windows EUC devices use an approved operating-system build and centrally managed software catalogue. Unnecessary Windows features, services, legacy protocols, consumer capabilities, local administrator access and unauthorised software are disabled, removed or controlled through enterprise policy. Corporate VPN, browser, endpoint security and other standard agents are installed only where required by the corporate build.
- Server and hosting platforms. Enterprise hosting teams use approved server roles, virtual-machine templates and platform builds that remove or disable unnecessary packages, services, sample content, default accounts, management interfaces and legacy protocols. Infrastructure administration tools are limited to approved management paths and authorised support personnel.
- Network functionality. Enterprise network teams operate deny-by-default network controls and permit only approved internal flows, ports and protocols between corporate zones and application tiers. Internet, public-network, cloud-service and externally initiated paths are outside this standard and are not enabled for covered applications.
- Managed platform and enterprise services. Enterprise owners control enabled features, extensions, administrative interfaces and supported protocols for shared databases, middleware, identity services, PKI, file services, messaging, logging, endpoint protection, vulnerability scanning, backup and other managed services.
- Enterprise software control and detection. Corporate software distribution, application control, endpoint protection, vulnerability management and asset-management services restrict or identify unauthorised executables, packages and installed software on managed components.
The application owner must identify the enterprise platforms and services it uses and must not enable additional operating-system, network or platform functionality outside the normal enterprise service process. Where an enterprise-managed component needs a non-standard feature, service, port or protocol for the application, the application addendum must record the requirement and the relevant enterprise owner must approve and implement it.

### Minimum application-specific least-functionality requirements

Each application must implement the following sensible minimum for the software, features and interfaces that it owns or controls:

1.  Limit the application to approved business capabilities. Enable only the modules, functions, workflows, reports, interfaces and administrative features required for the approved purpose. Optional, demonstration, sample, test, diagnostic and deprecated features must be disabled or removed from production unless there is a documented operational need.

2.  Minimise application components and dependencies. Include only required libraries, runtimes, plugins, browser components, thick-client modules, server packages and supporting tools. Dependencies must have an identifiable purpose and supported version. Development kits, compilers, source-control clients, package managers and debugging tools must not be present in production merely for convenience.

3.  Restrict application-owned services, ports and protocols. Each listener, service endpoint, scheduled task, background process, database connection and integration path must be documented and necessary. Application components must bind only to the required interfaces and use approved internal protocols. Unused listeners and services must be disabled; network access must follow the approved data-flow and firewall rules.

4.  Control executable and interpreted content. Only approved application binaries, scripts, packages, macros, plugins and code modules may execute in production. Where technically feasible, use code signing, package integrity checking, application allow-listing or equivalent controls. User-supplied or dynamically downloaded code must not execute unless explicitly required, validated and confined by design.

5.  Remove or secure default and maintenance functionality. Disable or change vendor default accounts, credentials, sample applications, example data, unrestricted management pages and unused remote-management functions. Maintenance and diagnostic capabilities that remain must be restricted to authorised support roles, disabled when not required where practical, and logged when used.

6.  Keep client installations minimal. A thick client installed on a corporate Windows EUC device must contain only approved application components and supporting dependencies. It must not install unnecessary local services, browser extensions, kernel drivers, auto-loaded plugins or elevated helper processes. Thin-client and browser-based applications must not require unapproved browser plugins or locally installed components.

7.  Keep server-side deployments minimal. Application and service tiers must contain only the application runtime and operational tools needed for reliable support. Administrative consoles must be separated from normal user interfaces and exposed only through approved internal management paths. Container images, where used internally, must be minimal, immutable where practical and free of unnecessary shells, package managers and utilities.

8.  Review functionality and remove what is no longer needed. Review enabled application features, components, dependencies, services, ports, protocols and integrations after material releases or architecture changes and periodically thereafter. Obsolete, unsupported, unused or unauthorised functionality must be removed, disabled or formally documented as a deviation.

### Proportionate implementation guidance

A small application may satisfy CM-07 with a concise component list, feature register, documented ports and interfaces, a production deployment checklist and periodic review. A complex multi-tier application should normally use version-controlled dependency manifests, automated software-composition analysis, hardened deployment templates, network-flow definitions, application allow-listing where supported and automated checks for unexpected services or packages. Least functionality does not require stripping out capabilities needed for availability, support or recovery; it requires those capabilities to be necessary, controlled and no broader than their purpose.

### Expected evidence and assessment artefacts

- Approved list of application modules, features, services, endpoints, ports, protocols and integrations
- Application and thick-client package manifests, dependency lock files or equivalent component records
- Production deployment or hardening checklist showing removal or disabling of non-required functionality
- Network-flow and firewall-rule cross-reference for application-owned communications
- Evidence of code-signing, package integrity, application control or other executable-content restrictions where used
- Review records showing removal, disabling or formal acceptance of obsolete or unnecessary functionality
- Cross-reference to inherited EUC, server, network, platform and enterprise software-control evidence
### Continuous monitoring and measures

- Unexpected or undocumented application listeners, services, scheduled tasks or network flows
- Unauthorised or unapproved application binaries, scripts, packages, plugins or dependencies
- Production components containing development, debugging or package-management tools without approval
- Enabled application features or interfaces with no current business owner or documented use
- Obsolete, unsupported or unused components awaiting removal
- Non-standard ports, protocols or management interfaces recorded in application addenda
### Addendum trigger

> **Template note:** Use an addendum when a legacy, supplier-controlled or specialist application requires an unnecessary-looking but operationally essential service, feature, port, protocol, plugin, runtime, local service, browser component, development or diagnostic tool; cannot support enterprise software-control mechanisms; requires dynamic or user-supplied code execution; must retain default or shared maintenance functionality; or cannot remove an obsolete or unsupported component. The addendum must identify the affected capability or component, standard approach, implemented approach, business and technical rationale, exposure created, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## CA-07 - Continuous Monitoring

### Control objective and responsibility model

CA-07 requires a system-level continuous monitoring strategy and an operating process that provides ongoing awareness of security control effectiveness, system changes, vulnerabilities, threats and resulting risk. In this context, continuous does not mean that every control is tested every moment. It means that monitoring and reassessment occur at frequencies sufficient to support timely, risk-based decisions. The strategy must define what is monitored, how often it is assessed, who receives the results, how findings are analysed and reported, and how corrective action is tracked. In this corporate model, the enterprise provides most infrastructure telemetry, common-control assessment, security operations, vulnerability management and central risk reporting. Each application supplies the minimum application-specific information needed to show that its own controls remain effective and that material changes or findings are acted upon. This implementation reflects NIST SP 800-53, SP 800-53A and the information security continuous monitoring approach described in SP 800-137 [1][2][3].

### Inherited enterprise continuous-monitoring capabilities

The following activities are inherited common controls when the application uses approved corporate infrastructure and services. They are operated and evidenced by the relevant enterprise service owners rather than recreated by each application team:

- Enterprise monitoring strategy and governance. The organisation defines common monitoring objectives, risk-based frequencies, reporting routes, escalation thresholds, assessment methods and ownership for enterprise and shared controls.
- Security operations and event monitoring. The SOC and enterprise security services collect, correlate and analyse network, identity, VPN, endpoint, server, platform and security-tool events; generate alerts; investigate suspected activity; and retain monitoring evidence in accordance with corporate requirements.
- Infrastructure vulnerability and configuration monitoring. Enterprise teams scan and assess corporate EUC devices, servers, network devices, virtualisation platforms and managed services; identify unsupported or vulnerable components; monitor configuration compliance and drift; and track remediation through enterprise processes.
- Common-control assessment. Control owners assess the design and operation of inherited identity, network, hosting, EUC, backup, logging, vulnerability-management and other common controls at defined intervals and after significant change.
- Asset, change and service-health information. Enterprise asset inventories, service-management records, change records, monitoring platforms and availability services provide ongoing information about shared components and material infrastructure changes.
- Enterprise risk and issue reporting. Security findings, incidents, exceptions, overdue remediation and common-control weaknesses are escalated through the corporate risk, governance and assurance processes.
The application owner must identify which enterprise monitoring and common-control services are inherited and must review relevant notifications or service reports. The application is not expected to duplicate the enterprise SOC, SIEM, endpoint monitoring, network monitoring, infrastructure scanning or common-control assessment programme.

### Minimum application-specific continuous-monitoring requirements

Each application must implement the following sensible minimum for the controls, components and risks that the application team owns or can influence:

1.  Maintain an application monitoring plan. Record the application-owned controls and risk indicators that require ongoing review, the evidence source, responsible owner, review frequency, reporting route and action threshold. This may be a concise matrix rather than a separate large document.

2.  Monitor application security events and service health. Review application-generated security events, authorisation failures, privileged actions, interface failures, abnormal processing, security-relevant errors and material availability or integrity issues. Events should be forwarded to the enterprise monitoring service where technically supported.

3.  Monitor application vulnerabilities and dependencies. Track results from application, library, package, runtime and database vulnerability assessment; monitor supplier and security advisories relevant to the application; and ensure findings are risk-assessed and remediated through the agreed process.

4.  Monitor the approved application state. Confirm that deployed application versions, application-owned configuration, interfaces, service identities and material permissions remain consistent with the approved baseline. Investigate unauthorised or unexplained drift.

5.  Reassess after material change. Review affected controls after significant releases, architecture or interface changes, changes to data classification or use, new privileged functionality, major platform migration, security incidents, significant vulnerabilities or relevant changes to inherited services.

6.  Review application access and privileged entitlement. Confirm at the defined frequency that application roles, privileged users, service identities and high-risk permissions remain approved, owned and necessary.

7.  Track findings to closure. Record application security weaknesses, monitoring exceptions and failed control checks in the appropriate remediation, risk or POA&M process. Assign an owner, target date and priority, and retain evidence of correction or formally approved risk treatment.

8.  Report application security status. Provide a periodic, risk-based summary to the system owner or designated governance forum covering significant findings, overdue actions, material changes, incidents, exceptions and the current effectiveness of application-owned controls. Urgent matters must be escalated without waiting for the periodic report.

9.  Review and improve the monitoring approach. At least periodically, and after a significant incident or control failure, confirm that the selected indicators, frequencies and evidence remain appropriate. Add, remove or adjust monitoring where the application, threat, vulnerability or business risk has changed.

### Proportionate implementation guidance

A small, stable application may use a short monitoring matrix supported by central alerts, vulnerability reports, release checks, access reviews and a periodic owner review. A complex multi-tier application should normally use automated health and security telemetry, pipeline and dependency checks, configuration-drift detection, scheduled control testing and a consolidated security-status dashboard. Monitoring frequency must be based on risk, rate of change and available evidence; it need not be identical for every control. Automation should be used where reliable and proportionate, but automated data does not replace accountable review, analysis and corrective action.

### Expected evidence and assessment artefacts

- Application continuous-monitoring plan or matrix identifying controls, indicators, evidence, frequencies, owners, thresholds and reporting routes
- Application security-event and service-health review records, including relevant SOC referrals
- Application vulnerability, dependency and security-advisory review records
- Baseline, configuration, release and drift-validation results
- Application access, privileged-role and service-identity review records
- Risk, exception, remediation or POA&M records showing ownership and progress to closure
- Periodic application security-status reports and evidence of urgent escalation where applicable
- Cross-reference to inherited enterprise monitoring, SOC, vulnerability, configuration, identity and common-control assessment evidence
### Continuous monitoring measures

- Application-owned monitoring activities completed within their defined frequency
- Critical or high application findings that remain overdue
- Material application changes completed without the required control review
- Security-relevant application events not reaching the enterprise monitoring service
- Unresolved differences between approved and deployed application state
- Overdue application access, privileged-role or service-identity reviews
- Age of the latest application security-status report and monitoring-plan review
- Repeat findings or control failures indicating ineffective corrective action
### Relationship with SI-04

SI-04 addresses the operational monitoring mechanisms used to detect attacks, unauthorised use, suspicious activity and relevant system events. CA-07 is broader: it defines the ongoing assurance process that uses SI-04 outputs together with vulnerability results, configuration checks, access reviews, change information, control assessments, incidents and remediation status to determine whether controls continue to operate effectively and whether risk remains acceptable.

### Addendum trigger

> **Template note:** Use an addendum when the application cannot provide one or more applicable monitoring indicators or evidence sources; cannot forward relevant events to the enterprise monitoring service; cannot be included in the standard vulnerability, dependency, access-review or configuration-assurance process; requires a monitoring frequency materially different from the corporate approach; relies on manual monitoring that cannot provide timely risk awareness; or has a supplier-controlled component for which control-effectiveness information is not available. The addendum must identify the affected control or component, standard approach, implemented approach, rationale, risk, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## IR-05 - Incident Monitoring

### Control objective and responsibility model

IR-05 requires security, privacy and supply-chain incidents to be tracked and documented. The record must remain sufficiently complete and current to support coordination, decision-making, reporting, evidence preservation, recovery and lessons learned. IR-05 is principally a case-management and accountability control: it does not require each application to operate a separate incident-response platform or duplicate the enterprise response team. In this corporate model, the enterprise provides the incident-management process, tooling, severity model, response coordination and reporting routes. Each application supplies timely, accurate application-specific information and supports the incident record for matters affecting the application. This implementation is aligned with NIST SP 800-53 Revision 5, the corresponding SP 800-53A assessment procedures and the incident-response lifecycle recommendations in SP 800-61 Revision 3 [1][2][4].

### Inherited enterprise incident-monitoring capabilities

The following capabilities are inherited common controls and are operated and evidenced by the enterprise security, privacy, service-management, legal, compliance and risk functions rather than recreated by each application team:

- Enterprise incident-management process and system. The organisation provides the authoritative case-management mechanism used to assign a unique incident record, record status and severity, maintain a chronology, assign actions and owners, retain supporting evidence, record decisions and track the incident through closure.
- Detection intake and escalation. The SOC, service desk, monitoring teams, users and other authorised reporting channels can raise suspected incidents. Enterprise triage applies common severity, priority, escalation and notification criteria and engages the appropriate technical, business, privacy, legal and management stakeholders.
- Response coordination. The enterprise incident-response function coordinates analysis, containment, eradication, recovery, communications and cross-team activity. It determines when specialist forensic, legal, privacy, human-resources, supplier, law-enforcement or government reporting support is required.
- Evidence handling and record protection. Enterprise procedures define evidence preservation, access restrictions, integrity protection, chain of custody where needed, retention and secure disposal. Access to incident records is restricted according to sensitivity and operational need.
- External and regulatory reporting. Corporate legal, privacy, contractual and regulatory functions determine whether an incident must be reported externally, to whom, by when and with what approved content. Application teams do not make unauthorised external notifications.
- Enterprise metrics and lessons learned. The incident-response function reports incident trends, timeliness, recurring causes and overdue corrective actions, and uses post-incident findings to improve common controls, procedures and monitoring.
The application owner must know how to report an incident, identify the relevant business and technical contacts, and participate when requested. The application must not maintain an informal parallel incident record as a substitute for the authoritative enterprise record.

### Minimum application-specific incident-monitoring requirements

Each application must meet the following minimum requirements for incidents or suspected incidents that affect, originate from, or materially involve the application:

1.  Report promptly through the approved route. Application users, support staff, developers and administrators must raise suspected incidents without waiting for certainty or completing their own investigation. Urgent or high-impact conditions must use the enterprise escalation route rather than routine service-request channels.

2.  Provide sufficient application context. The application team must supply the application name, affected environment and components, detected time and source, observed behaviour, affected users or technical identities, relevant transactions or data, known business impact, recent changes and any immediate actions already taken. Information must be factual, time-stamped where practicable and clearly distinguish confirmed facts from assumptions.

3.  Preserve relevant application evidence. Logs, audit events, configuration snapshots, release information, database records, interface messages, error details and other relevant artefacts must be preserved in accordance with enterprise direction. Application personnel must not alter, delete or unnecessarily access suspected evidence, and must avoid actions that could destroy volatile or time-sensitive information.

4.  Maintain the application contribution to the incident chronology. Material application observations, decisions, containment steps, configuration changes, recovery actions, validation results and communications must be recorded in, or supplied for inclusion in, the authoritative incident record. Separate technical notes may be retained where necessary but must be referenced from the incident record.

5.  Support controlled containment and recovery. Application teams must assist the incident lead in identifying safe containment options, dependencies, business consequences and recovery checks. Emergency changes must follow the approved emergency-change process and be documented in the incident record. Restoration must use approved software, configuration and data sources.

6.  Identify information and reporting considerations. The application owner or data owner must identify whether government information, personal data, company-confidential information, regulated records or contractual data may be affected and provide this information promptly to the authorised enterprise functions. The application team must not independently determine or issue external notifications unless formally authorised.

7.  Track application corrective actions. Application-specific remediation, monitoring improvements, control changes, code fixes, configuration changes and documentation updates arising from the incident must have an owner, priority and target date and be tracked through the approved risk, change, vulnerability or POA&M process until verified and closed.

8.  Participate in closure and lessons learned. Before closure, the application owner must confirm that application recovery and validation are complete, residual risk is understood, required evidence is retained and application actions are recorded. For significant or recurring incidents, the application team must contribute to the post-incident review and update relevant controls, tests, monitoring or operating procedures.

### Proportionate implementation guidance

A small application normally needs no dedicated incident tool or bespoke response team. Its minimum implementation may consist of named contacts, an understood reporting route, accessible application logs, a short evidence checklist and participation in the enterprise incident record. A complex multi-tier application should maintain an application incident-support runbook identifying component owners, critical dependencies, log and evidence locations, safe containment options, recovery validation steps and specialist contacts. The runbook supports the enterprise process; it does not replace it.

### Expected evidence and assessment artefacts

- Cross-reference to the enterprise incident-response policy, process, severity model and authoritative incident-management system
- Application incident contacts and, for complex applications, an incident-support runbook
- Incident records showing application context, chronology, decisions, actions, status and closure
- Preserved application logs and artefacts, with chain-of-custody records where required
- Emergency-change, recovery-validation and service-restoration records
- Application corrective-action records and evidence of verified closure
- Post-incident review outputs for significant or recurring incidents
### Continuous monitoring and measures

- Suspected application incidents reported within the defined escalation time
- Open application incidents without a current owner, status or next action
- Incident records lacking sufficient application context or chronology
- Application corrective actions overdue or repeatedly deferred
- Repeat incidents with the same or materially similar root cause
- Incidents where required evidence was unavailable, incomplete or not retained
- Time from application recovery to owner validation and formal closure
### Relationship with adjacent controls

IR-04 governs the organisation's incident-handling capability and response activities. IR-05 ensures that incidents are tracked and documented throughout that process. SI-04 and AU-02 provide monitoring and event information that may initiate or support an incident record, while CA-07 uses incident trends, findings and corrective-action status as part of ongoing control assurance.

### Addendum trigger

> **Template note:** Use an addendum when the application cannot use the authoritative enterprise incident-management process; cannot preserve or provide necessary logs or evidence; has safety, operational or technical constraints that materially limit standard containment or recovery actions; requires specialised forensic handling; is subject to application-specific contractual or government reporting conditions; or relies on a supplier whose notification, evidence or response arrangements differ from the corporate standard. The addendum must identify the affected process or evidence source, standard approach, implemented approach, rationale, risk, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## SI-03 - Malicious Code Protection

### Control objective and responsibility model

SI-03 requires malicious-code protection mechanisms at appropriate locations, automatic or centrally controlled updates, periodic and real-time scanning where applicable, and defined action when malicious code is detected. Protection should use multiple detection methods where practicable, including signature, reputation, behavioural and other non-signature techniques. In this corporate model, the enterprise provides the principal endpoint, server, network, messaging and security-monitoring capabilities. The application team is responsible only for ensuring that its software, content-handling paths and deployment practices do not bypass those controls and for providing a small number of application-specific safeguards where the application accepts, generates or executes content that could carry malicious code. This implementation is aligned with NIST SP 800-53, SP 800-53A and the malware-prevention principles in SP 800-83 Rev. 1 [1][2][4].

### Inherited enterprise malicious-code protection

The following capabilities are inherited common controls when the application uses approved corporate EUC, hosting, network and security services. They are implemented, maintained and evidenced by the relevant enterprise service owner rather than duplicated by each application:

- Corporate Windows EUC protection. Hardened Microsoft Windows EUC devices use centrally managed endpoint protection and EDR, real-time file and process inspection, reputation and behavioural analysis, scheduled scanning, host firewalling and controlled updates. Users do not disable or reconfigure these protections.
- Server and hosting protection. Supported server operating systems and approved hosting platforms use centrally managed anti-malware or EDR where technically suitable, together with hardened builds, application control, patching, monitoring and restricted administration. Where conventional scanning is unsuitable for a specialist platform, the enterprise service owner documents the alternative protection model.
- Enterprise update and health management. Detection engines, signatures, reputation data and protection agents are updated and monitored centrally. Failures, stale protection data, disabled agents and unhealthy endpoints are identified and escalated through enterprise security operations.
- Network, email and content controls. Enterprise gateways, email services, web filtering, network security controls and approved file-transfer services inspect or block known malicious content and suspicious communications where those services are used.
- Software distribution and application control. Corporate software-distribution, code-signing, allow-listing or application-control processes restrict installation and execution to approved software and provide controlled delivery of thick-client packages and supporting components.
- Central detection and response. The SOC and enterprise incident-response capability receive endpoint, server, network and application alerts; investigate suspected malware; isolate affected devices or accounts; coordinate eradication and recovery; and preserve relevant evidence.
The application owner must identify which inherited protections apply to each application component and must not deploy duplicate anti-malware agents or scanning products without enterprise approval. The application must not require users or administrators to disable endpoint protection, application control, scanning, EDR or other corporate safeguards.

### Minimum application-specific malicious-code protection requirements

Each application must implement the following sensible minimum for the software, files, content and execution paths that it owns or controls:

1.  Use approved software and deployment routes. Application binaries, libraries, scripts, installers, thick-client packages and deployment artefacts must come from controlled repositories and be delivered through approved build and software-distribution processes. Unapproved download, sideloading or direct installation by users is prohibited.

2.  Preserve enterprise protection. The application must operate with the standard corporate endpoint, server and platform protections enabled. Installation, upgrade, troubleshooting and support procedures must not create exclusions, disable scanning or weaken application control except where a documented, narrowly scoped and approved exception is technically necessary.

3.  Validate uploaded, imported or transferred files. Where the application accepts files or other potentially executable content, it must restrict permitted types and sizes, verify the actual content rather than relying only on the file extension, reject malformed or unexpected content, and use an approved malware-scanning service before the content is made available, processed or distributed when technically supported and proportionate to risk.

4.  Store and handle untrusted content safely. Untrusted files must be held in a controlled location with least-privilege access and must not be executed, rendered with active content, or placed in executable directories by default. Quarantine, rejection or restricted handling must be used when scanning fails, is unavailable or produces an uncertain result.

5.  Control active content and extensibility. Macros, scripts, plugins, embedded objects, templates, document automation, user-supplied code and other active-content features must be disabled unless required for an approved business function. Where required, they must be limited to approved sources, signed or otherwise validated where feasible, and executed with the least privilege available.

6.  Protect generated and exported content. The application must not generate packages, documents, scripts or archives containing unauthorised executable content. Where the application creates downloadable files, it must apply the same approved content-handling and scanning controls where the generated content or included attachments could carry malicious code.

7.  Handle detection securely. When malicious or suspicious content is detected, the application must block or quarantine it, avoid disclosing it to users, record the event without storing harmful payloads in ordinary logs, and notify the enterprise monitoring or incident process at the required severity. The application must fail closed when a mandatory scanning decision cannot be obtained.

8.  Keep application components and detection integrations current. Application-owned scanning connectors, content-processing libraries, archive handlers, document converters, parsers and similar components must remain supported and patched. Changes to scanning services, file-handling logic or approved content types must be tested before production use.

9.  Test the protected paths. At implementation and after material changes, verify that file upload, import, transfer, quarantine, blocking, alerting and recovery paths operate as designed. Testing must use safe test artefacts or approved simulations and must not introduce live malicious code into production.

### Proportionate implementation guidance

An application that neither accepts files nor executes user-supplied or externally sourced content may rely almost entirely on inherited enterprise endpoint, server and software-distribution controls, provided its own deployment artefacts remain controlled. An application that accepts ordinary business documents should normally enforce type and size restrictions, inspect actual content, use the approved malware-scanning service and quarantine on failure. Applications that process archives, macros, scripts, plugins, executable packages or complex document formats require stronger validation, isolation and active-content controls. The application does not need to build its own anti-malware engine, EDR platform, quarantine infrastructure or SOC capability where approved enterprise services are available.

### Expected evidence and assessment artefacts

- Application component and data-flow description identifying file, content and execution paths
- Cross-reference to inherited EUC, server, EDR, anti-malware, gateway, software-distribution and SOC controls
- Approved file-type, content-type, size and active-content rules, where applicable
- Configuration or design evidence for approved malware-scanning, quarantine and fail-closed behaviour
- Build, package-signing, repository and software-distribution records for application components
- Records of any protection exclusions, including approval, scope, owner and expiry
- Safe test results showing detection, blocking, quarantine, alerting and recovery behaviour
- Relevant malicious-code alerts, incidents and corrective-action records
### Continuous monitoring and measures

- Application components or devices with disabled, unhealthy or out-of-date inherited protection
- Approved protection exclusions that are overdue for review or broader than required
- File or content-processing paths not covered by the approved scanning decision
- Scanning failures, timeouts or unavailable-service events and the resulting disposition
- Malicious or suspicious content detections by application, source and outcome
- Unsupported content-processing, archive, parser or scanning-integration components
- Material file-handling or active-content changes completed without the required security test
### Relationship with other controls

SI-03 provides prevention, detection and response mechanisms for malicious code. SI-04 uses the resulting alerts and telemetry as part of system monitoring. SI-02 addresses timely correction of flaws in protection agents and application content-processing components. CM-07 reduces attack surface by removing unnecessary interpreters, plugins and active content. SI-10 validates inputs more broadly, while SI-03 focuses specifically on malicious or potentially executable code and content. IR-05 tracks confirmed or suspected malware incidents through the enterprise incident process.

### Addendum trigger

> **Template note:** Use an addendum when an application component cannot run with the standard enterprise endpoint or server protection; requires an anti-malware or EDR exclusion; accepts or distributes files without using the approved scanning service; must allow macros, scripts, plugins, embedded code or other active content outside the standard approach; cannot fail closed when scanning is unavailable; uses a specialist platform for which conventional malware protection is unsupported; or relies on supplier-controlled scanning or quarantine evidence. The addendum must identify the affected component or content path, standard approach, implemented approach, technical rationale, risk, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## SC-07 - Boundary Protection

### Control objective and responsibility model

SC-07 requires communications at the external boundary and at selected internal boundaries to be monitored and controlled. Boundary protection is not limited to the Internet edge: it also applies where network zones, application tiers, management networks, security domains or information of different sensitivity meet. NIST guidance supports a deny-by-default, permit-by-exception policy, managed boundary devices, physically or logically separated public-access components where applicable, controlled external connections, and prevention of unauthorised information transfer. This standard has no public-facing, cloud, hybrid or direct Internet-connected application components. The enterprise therefore owns the corporate network perimeter, VPN termination, routing, segmentation, firewall platforms and central network monitoring. Each application owns only the minimum information and controls needed to define and constrain its approved internal communication paths. This implementation is aligned with NIST SP 800-53, SP 800-53A, SP 800-41 and the resource-focused principles in SP 800-207 [1][2][4][5].

### Inherited enterprise boundary-protection controls

The following controls are inherited when the application uses approved corporate network, EUC, hosting and security services. They are implemented, operated and evidenced by the relevant enterprise service owner rather than reproduced by the application team:

- Corporate external boundary. Enterprise firewalls, secure gateways, routing controls, proxies and monitoring services protect the corporate network from public and other untrusted networks. Applications covered by this standard have no direct inbound or outbound Internet path and must not bypass these controls.
- Remote-access boundary. Approved VPN client software on a hardened corporate Microsoft Windows EUC device establishes an encrypted tunnel to the corporate VPN gateway. Corporate identity, multi-factor authentication, device-compliance checks, central logging and prohibition of split tunnelling are provided by the enterprise remote-access service. Once connected, the EUC uses the normal internal application access paths.
- Internal network segmentation. Enterprise network teams establish and administer corporate user, server, application, database, management, security-service and other network zones. Inter-zone communications are controlled through managed firewalls, access-control lists, routing policy, load balancers or equivalent enforcement points.
- Hosting and platform boundaries. Enterprise hosting teams provide approved virtual networks, host firewalls, hypervisor or container-network controls, management-plane separation and controlled administration paths for physical and virtual server platforms.
- Enterprise network services. DNS, DHCP, time synchronisation, identity, PKI, logging, vulnerability scanning, backup and other approved shared services are provided through defined corporate network paths and managed by their service owners.
- Boundary monitoring and rule governance. Enterprise teams log and monitor traffic at managed enforcement points; investigate anomalous or denied communications; maintain firewall and routing rules under change control; periodically review rules; and remove obsolete or unauthorised paths.
The application owner must identify the enterprise zones and boundary services on which the application depends and must not directly administer enterprise firewalls, routers, VPN gateways or network-monitoring platforms unless separately authorised as an enterprise service role.

### Minimum application-specific boundary-protection requirements

Each application must meet the following sensible minimum for the communication paths and components that it owns or can influence:

1.  Define the application boundary and data flows. Maintain a current diagram or structured flow record showing corporate EUC access, application tiers, data stores, management paths, enterprise services and every approved application interface. For each flow, identify source, destination, direction, purpose, protocol, port or service, authentication method and data classification where relevant.

2.  Permit only required communication paths. Request and use only the network flows needed for an approved business or support purpose. Flows must be specific enough to avoid unrestricted any-to-any access, broad network ranges or unnecessary bidirectional communication. Access must be denied where no approved requirement exists.

3.  Separate application tiers where risk or architecture requires it. Presentation, application or service, data and management functions must use distinct logical zones, host controls or equivalent enforcement where combining them would expose a higher-trust component unnecessarily. A small single-server application may use one server zone where justified, but its user, administrative and enterprise-service paths must still be defined and constrained.

4.  Constrain thick-client communication. Software installed on corporate Windows EUC devices must communicate only with documented internal application endpoints and approved enterprise services. It must not require local listening services, peer-to-peer connectivity, direct database access or unrestricted server access unless specifically necessary, approved and documented.

5.  Protect application interfaces. Internal web, API, messaging, file-transfer and machine-to-machine interfaces must use approved endpoints, authenticated and encrypted protocols where required, narrowly scoped service identities and application-level authorisation. The application must not assume that network location alone authorises a request.

6.  Control application-initiated outbound connections. Server-side components may connect only to documented internal destinations required for enterprise services, dependencies or approved integrations. Direct Internet access, cloud endpoints, public software repositories and unapproved external services are prohibited under this standard. Software and updates must arrive through approved corporate distribution or repository services.

7.  Protect management paths. Administrative interfaces must be separated from ordinary user access where technically practicable, restricted to approved management networks or privileged access workstations, and unavailable from general user networks unless the approved architecture requires and securely controls that path. Direct inbound administration from external networks is prohibited.

8.  Fail safely and avoid bypass routes. Components must not automatically fall back to an unprotected protocol, alternate external endpoint, local peer connection or unrestricted path when the approved route is unavailable. Diagnostic, maintenance and disaster-recovery routes must be controlled to the same standard or documented in an addendum.

9.  Validate and review requested flows. Network-rule requests must be traceable to the approved architecture and tested after implementation. The application owner must periodically confirm that each application-specific flow remains required, correctly scoped and associated with a supported component. Obsolete flows must be removed through the enterprise change process.

### Proportionate implementation guidance

A small internal application may satisfy SC-07 with one controlled user-to-server flow, a limited set of enterprise-service connections and a concise flow register. A multi-tier application should normally separate user-facing, service, data and management traffic and use distinct enforcement points between the relevant zones. Segmentation should reflect actual risk and trust differences rather than creating tiers with no enforceable purpose. The application team is not expected to operate its own firewall or network sensor where enterprise controls exist; it is expected to know and justify every required path and to ensure the application does not create an alternative route around those controls.

### Expected evidence and assessment artefacts

- Current application boundary and data-flow diagram, including remote corporate EUC access where applicable
- Application communication-flow register showing source, destination, direction, purpose, protocol, port or service, owner and approval
- Approved firewall, access-control-list, load-balancer or equivalent rule requests linked to application requirements
- Evidence that thick clients, web tiers, service tiers, data tiers and management paths use only approved endpoints
- Post-implementation connectivity and segmentation test results, including confirmation that prohibited paths are blocked
- Periodic application flow-review or rule-recertification records and evidence of obsolete-rule removal
- Cross-reference to inherited corporate perimeter, VPN, network-segmentation, hosting and boundary-monitoring evidence
### Continuous monitoring and measures

- Application-specific network flows without a current owner, purpose or approval
- Flows broader than the documented source, destination, protocol or direction requires
- Direct Internet, cloud, public-network or unapproved external connections detected
- Application components communicating with undocumented destinations or listening on undocumented ports
- Segmentation or prohibited-path tests that fail
- Application-specific firewall or routing rules not reviewed within the defined period
- Obsolete rules or interfaces awaiting removal
- Denied-traffic or anomalous-connection patterns referred by the enterprise monitoring service
### Relationship with AC-04 and AC-03

SC-07 establishes and protects network and system boundaries and controls which communication paths can exist. AC-04 governs whether information is permitted to flow between sources and destinations in accordance with approved policy, including controls within the application or data layer. AC-03 enforces the user, process and service authorisations that determine who may use an allowed path and what they may do. A permitted network connection therefore does not by itself authorise access to an application function or information.

### Addendum trigger

> **Template note:** Use an addendum when an application requires direct Internet, public-network, cloud or hybrid connectivity; a partner, supplier or government connection that is not provided through the standard corporate boundary; direct EUC-to-database access; peer-to-peer or locally listening thick-client functionality; an unsegmented multi-tier design where the standard separation cannot be applied; broad, dynamic or vendor-controlled network ranges; an application-managed firewall or gateway; a management path from a general user network; an unauthenticated or unencrypted specialist protocol; or a required route that bypasses standard enterprise enforcement or monitoring. The addendum must identify the affected component and flow, standard approach, implemented approach, business and technical rationale, data involved, risk, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## AC-04 - Information Flow Enforcement

### Control objective and responsibility model

AC-04 requires approved information-flow authorisations to be enforced within the system and between connected systems. Information-flow control is concerned with where information may move, in which direction, for what purpose and under what conditions. It is distinct from user access control: a user may be authorised to use an application while the application must still prevent information from being sent to an unapproved destination, transferred between incompatible data domains, exposed through an interface, copied into an unrestricted field or exported in an unauthorised form. In this corporate model, the enterprise provides the common network, platform and security services that constrain communication paths and certain classes of transfer. Each application remains responsible for understanding its information flows and enforcing the business, classification, privacy, contractual and integrity rules that apply to the information it processes. This implementation is aligned with NIST SP 800-53 and the corresponding assessment procedures in SP 800-53A [1][2].

### Inherited enterprise information-flow controls

The following controls are inherited where the application uses approved corporate infrastructure and managed services. They are operated and evidenced by the relevant enterprise service owner rather than recreated by each application team:

- Network routing, segmentation and boundary enforcement. Enterprise network services restrict which corporate network zones, hosts and services may communicate, in which direction and over which approved ports and protocols. Firewall and routing policy is deny-by-default unless an approved business requirement exists.
- Corporate VPN path. Remote corporate EUC devices use the approved VPN client and corporate VPN gateway. Once connected, traffic is routed through the corporate network and is subject to the same internal segmentation, monitoring and application-access controls as traffic from an on-site corporate EUC device. Split tunnelling and direct inbound access to internal applications are prohibited.
- Managed gateway and transfer services. Where provided, enterprise reverse proxies, load balancers, API gateways, messaging services, managed file-transfer services, email gateways, malware-scanning services and data-loss prevention controls enforce approved destinations, protocols, file handling and transfer restrictions.
- Enterprise identity and directory attributes. Corporate identity, group and device information may be used by applications and gateways to apply flow restrictions based on approved role, organisation, device state or other authoritative attributes.
- Shared data-platform controls. Enterprise-managed database, file, messaging and analytics platforms enforce platform permissions, tenant or schema boundaries, approved connection methods and administrative restrictions for the services they own.
- Central monitoring and incident response. Enterprise network, security and logging services detect and investigate blocked or anomalous communications, malware-related transfers and other policy violations within the services they monitor.
The application owner must identify the inherited services used by the application and the information-flow decisions delegated to those services. Network reachability alone does not demonstrate that an information flow is authorised, and an enterprise firewall rule does not remove the application responsibility to control the content and purpose of an allowed connection.

### Minimum application-specific information-flow requirements

Each application must implement the following sensible minimum for the information, interfaces and transfer functions it owns or controls:

1.  Define the approved information flows. Maintain a concise data-flow or interface register identifying the source, destination, direction, business purpose, information type or classification, transfer method, initiating identity or process, frequency and approving owner. Include user-driven exports, thick-client transfers, browser downloads and uploads, service interfaces, database connections, messaging, scheduled jobs and batch transfers as applicable.

2.  Permit only required destinations and directions. Application interfaces, service endpoints, connection strings, queues, file locations and export functions must be restricted to approved internal destinations. The application must not provide a general-purpose forwarding, proxying, arbitrary file-transfer or unrestricted destination capability unless that is an expressly approved business function.

3.  Enforce flow rules at the trusted processing point. Server-side or otherwise trusted application components must enforce the applicable rules; interface controls must not rely solely on hidden buttons, client-side code or user instructions. Thick-client applications must not be able to bypass server-side checks merely because they run on a corporate Windows EUC device.

4.  Control the information content, not only the connection. Validate that records, fields, files and messages sent through an approved path are permitted for the destination and purpose. Apply data minimisation, field or record filtering, classification or handling rules, format restrictions and content validation where relevant. Restricted information must not be placed in logs, error messages, URLs, temporary files, notifications or metadata unless specifically required and protected.

5.  Restrict user-initiated movement. Export, download, print, copy, paste, report generation, bulk extraction and attachment functions must be available only to approved roles and must apply appropriate scope, volume and data-handling restrictions. Where the application cannot technically prevent onward handling on a corporate EUC device, the residual reliance on corporate endpoint controls and user procedures must be explicit.

6.  Control service-to-service and batch flows. Integrations must use approved endpoints, schemas and message types; authenticate the sending and receiving services; reject unexpected destinations or message formats; and use reconciliation, acknowledgements or equivalent checks where failure, duplication or misdirection could affect confidentiality, integrity or business processing.

7.  Prevent unintended cross-domain or cross-context disclosure. The application must keep information separated where required by business unit, case, tenant, project, security classification, legal restriction, personal-data purpose or other approved boundary. Queries, caching, search, reporting, background jobs and shared storage must preserve those restrictions.

8.  Fail safely. If classification, destination, authorisation, filtering or policy information is missing, invalid or unavailable, the application must block or safely hold the transfer rather than defaulting to unrestricted flow. Failed transfers must not leave uncontrolled partial files, messages or duplicate transactions.

9.  Record material flow activity and violations. Log security-relevant transfers, bulk exports, blocked flows, invalid destinations, policy failures and administrative changes to flow rules with sufficient context for investigation. Avoid recording restricted content unnecessarily. Forward relevant events to the enterprise monitoring service where technically supported.

10.  Review and test flows. Review approved flows after material architecture, interface, data-use or classification changes and periodically thereafter. Test that disallowed destinations, directions, fields, records, files and user actions are blocked, while approved flows remain operational.

### Proportionate implementation guidance

A small application with no integrations and no export capability may satisfy AC-04 with a simple diagram, a short list of permitted data stores and a confirmation that users can only view or update information through the controlled application interface. A typical internal web or thick-client application should document its database, file, reporting and service flows and enforce destination and data-scope restrictions in server-side logic. A complex multi-tier application should normally use controlled API or messaging contracts, destination allowlists, schema and content validation, automated flow testing, reconciliation and monitored policy enforcement. Controls should be proportionate to the sensitivity, volume, direction and consequence of the flow; the application does not need to duplicate enterprise firewall, VPN or managed-transfer technology.

### Expected evidence and assessment artefacts

- Approved application data-flow diagram and information-flow or interface register
- Data-owner, business-owner or information-owner approvals for material flows
- Application role and function mapping for export, download, print, bulk extraction and transfer capabilities
- Interface specifications, schemas, destination allowlists and application configuration controlling flows
- Evidence of server-side flow enforcement, content or field filtering, validation and safe failure
- Test results showing approved flows succeed and prohibited destinations, directions or content are blocked
- Transfer, reconciliation, blocked-flow and policy-change logs
- Cross-reference to inherited network, VPN, gateway, managed-transfer, DLP, platform and monitoring controls
### Continuous monitoring and measures

- Approved application flows reviewed within their defined frequency
- Interfaces or destinations operating without a current owner or approval
- Blocked or attempted transfers to unapproved destinations
- Bulk export, download or print activity outside expected patterns
- Failed reconciliation, duplicate delivery, misrouting or partial-transfer events
- Material application changes completed without data-flow review
- Flow-control rules or destination allowlists changed outside the approved process
- Information-flow violations and repeat incidents by cause
### Relationship with SC-07 and AC-03

SC-07 establishes and protects the network and system boundaries through which communications may pass. AC-04 determines whether particular information is allowed to move through an available path, including its direction, destination, content and purpose. AC-03 determines whether the user, service or process is authorised to invoke the function or access the data. Effective implementation normally requires all three: an approved network path, an authorised actor and an authorised information flow.

### Addendum trigger

> **Template note:** Use an addendum when the application requires a flow not represented by the standard internal architecture; cannot restrict an interface to approved destinations, directions or content; permits unrestricted export, copy, print or bulk extraction; relies on manual review instead of technical enforcement for material restricted-data flows; cannot preserve separation between required business, project, tenant, case, classification or privacy contexts; uses a legacy or supplier-controlled interface without adequate validation, reconciliation or logging; or cannot fail safely when flow-policy information is unavailable. The addendum must identify the affected information, source, destination and direction; standard approach; implemented approach; rationale; risk; compensating controls; owner; approval; and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## AC-02 - Account Management

### Control objective and responsibility model

AC-02 requires accounts to be defined, approved, created, enabled, modified, reviewed, disabled and removed through a controlled lifecycle. Account types, authorised users, role membership, access conditions and responsible owners must be established; account activity and status must be monitored; and changes in employment, contract, role, need-to-know or risk must result in timely access changes. In this corporate model, the enterprise provides the authoritative workforce identity, corporate account lifecycle, authentication, directory, privileged-access and joiner-mover-leaver processes. Each application remains responsible for deciding who may hold an application account or role, ensuring application entitlements remain necessary, controlling application-local and technical accounts, and removing access when it is no longer required. This implementation reflects AC-02 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A [1][2].

### Inherited enterprise account-management controls

The following capabilities are inherited when the application uses approved corporate identity, EUC, hosting and privileged-access services. They are operated and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Authoritative identity and joiner-mover-leaver process. Human identities are established from approved employment, contractor or other authoritative records. Corporate accounts are created, changed, suspended and closed through the enterprise identity lifecycle when personnel join, change role, leave, expire or otherwise lose eligibility.
- Corporate account and directory services. Unique corporate user identifiers, account status, organisational attributes, group membership and authentication integration are provided through approved enterprise directory and identity services.
- Authentication and device access. Corporate account authentication, MFA where required, password or authenticator controls, hardened Microsoft Windows EUC sign-in and corporate VPN access are managed by enterprise identity, EUC and remote-access services.
- Privileged and infrastructure accounts. Dedicated administration accounts, privileged-access management, server and platform administration identities, emergency-access arrangements and related monitoring are controlled by the relevant enterprise teams.
- Enterprise service and machine identities. Where centrally provided, managed service accounts, certificate-based identities, secrets services and enterprise integration identities are provisioned and governed by the owning platform or security service.
- Central monitoring and periodic governance. Enterprise identity services monitor account status, dormant or anomalous use, authentication activity and selected entitlement conditions, and support corporate access certification, investigation and reporting.
The application owner must identify which enterprise identity and account services are inherited and must consume account status and lifecycle changes promptly. The application must not create a second unmanaged workforce identity where the approved corporate identity can be used.

### Minimum application-specific account-management requirements

Each application must implement the following sensible minimum for application access, roles and technical identities that it owns or controls:

1.  Define permitted account types. Document which account types the application allows, such as named corporate users, application administrators, support roles, auditors, service identities, scheduled-task identities and emergency accounts. Shared, generic, guest, anonymous, default and local application accounts must be prohibited unless specifically required, approved and documented.

2.  Use the corporate identity by default. Interactive users must normally access the application using their unique corporate account. Application-local user accounts must be avoided and may be used only where the corporate identity service cannot meet a legitimate technical or operational need.

3.  Require authorised access requests and approval. New application access and material role changes must be based on a recorded business need, requested or endorsed by an authorised manager or data owner, and approved by the designated application or information owner. The approver must not simply confirm that the person has a corporate account; the approver must confirm the required application role and data access.

4.  Assign only the approved role and scope. Provision the minimum role, organisational scope, case, project, dataset or other entitlement necessary for the approved duties. Default access must be minimal, and privileged or high-risk permissions must require separate approval.

5.  Process lifecycle changes promptly. The application must respond to enterprise account disablement and to notified joiner, mover, leaver, contract-expiry, extended-absence, disciplinary or role-change events. Application roles and local entitlements must be removed or adjusted within the corporate target timescale; urgent revocation must be acted upon immediately.

6.  Control application-local and emergency accounts. Any unavoidable local, break-glass or emergency account must have a named owner, documented purpose, strong authentication, restricted privileges, protected credentials, monitored use, periodic validation and a defined disablement or expiry condition. Default vendor accounts must be removed, disabled or securely controlled before production use.

7.  Govern service and technical identities. Each service account, API identity, scheduled-task account, database connection identity or other non-person account must have a unique identifier where practicable, documented purpose, accountable owner, approved permissions, credential-management method, environment and review date. It must not be used for interactive human activity unless specifically approved.

8.  Prevent orphaned and duplicate access. Application access must remain linked to an active corporate identity or an explicitly governed technical identity. Duplicate user records, stale local accounts, ownerless service identities and entitlements that survive account disablement must be identified and corrected.

9.  Review accounts and entitlements. Application users, privileged roles, local accounts and technical identities must be reviewed at a frequency proportionate to risk and after significant organisational or application change. Reviewers must confirm the person or process still requires the account, role, scope and privilege; unsupported access must be removed.

10.  Monitor and record account-management activity. The application must record creation, enablement, disablement, deletion, role assignment, privilege change, failed provisioning and use of emergency or local accounts. Relevant events must identify the acting administrator or process, affected account, action, outcome and time, and must be forwarded to enterprise monitoring where technically supported.

### Proportionate implementation guidance

A small application may satisfy AC-02 by using corporate sign-in, a concise role matrix, an approved access-request workflow, a current list of users and service identities, and periodic owner review. A complex or high-volume application should normally integrate with enterprise identity governance for automated provisioning and de-provisioning, use centrally managed groups or attributes, apply expiry to temporary access, reconcile application entitlements with the authoritative identity source, and produce exception reports. Automation is preferable where reliable, but the application owner remains accountable for defining and approving the application access that automation implements.

### Expected evidence and assessment artefacts

- Documented permitted account types and application account-management procedure
- Application role and entitlement model, including approving authorities
- Sample approved access requests, role changes, revocations and urgent disablements
- Current application user, privileged-account, local-account and technical-identity inventory
- Evidence of integration with corporate identity status and joiner-mover-leaver processes
- Periodic account and entitlement review results, including removals and corrections
- Default, emergency and local-account control records where such accounts exist
- Account-management and emergency-account audit events forwarded to enterprise monitoring
- Cross-reference to inherited enterprise identity, authentication, PAM and HR lifecycle controls
### Continuous monitoring and measures

- Application accounts not linked to an active corporate identity or governed technical identity
- Accounts, roles or temporary entitlements retained beyond their approved end date
- Leaver or urgent-revocation actions completed outside the corporate target timescale
- Dormant, duplicate, default, shared, generic or ownerless application accounts
- Privileged, local and service accounts not reviewed within the defined period
- Failed or incomplete automated provisioning and de-provisioning events
- Unapproved changes to application roles or account status
- Emergency-account use not reviewed promptly after the event
### Relationship with related controls

AC-02 governs the lifecycle and status of accounts and their assigned memberships or roles. AC-03 enforces what an approved account may do in the application. AC-06 limits those permissions to the minimum necessary. IA-02 verifies the identity using the account, while IA-05 governs the associated authenticators. AU-02 and SI-04 provide the event logging and monitoring needed to detect unauthorised account changes or misuse.

### Addendum trigger

> **Template note:** Use an addendum when the application cannot use the approved corporate identity; requires application-local, shared, generic, guest, anonymous, default or permanent emergency accounts; cannot consume enterprise account disablement promptly; cannot meet the standard joiner-mover-leaver or access-review timescale; requires a service identity without a named owner or with permissions shared across unrelated applications or environments; cannot individually attribute account-management actions; or cannot produce a reliable account and entitlement inventory. The addendum must identify the affected account type or process, standard approach, implemented approach, rationale, risk, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## SI-07 - Software, Firmware, and Information Integrity

### Control objective and responsibility model

SI-07 requires mechanisms and processes to detect unauthorised changes to software, firmware and information, and to take defined action when an integrity failure is identified. Integrity means that code, configuration and information remain complete, accurate and in the approved state, and have not been altered accidentally or maliciously without detection. NIST permits integrity checking to be applied at appropriate points and frequencies according to risk; it does not require every file or data item to be continuously hashed. In this corporate model, the enterprise provides platform trust, operating-system and firmware protection, approved repositories, signing services, endpoint and server integrity monitoring, and central alerting. Each application remains responsible for the integrity of its application artefacts, application-controlled configuration, dependencies, database structures, interfaces and business information. This implementation reflects SI-07 and its assessment objectives in NIST SP 800-53 and SP 800-53A, supported by NIST secure software development and code-signing guidance [1][2][4][5].

### Inherited enterprise integrity controls

The following capabilities are inherited when the application uses approved corporate EUC, hosting, software-distribution, repository, identity and security services. They are implemented and evidenced by the relevant enterprise service owner rather than duplicated by the application team:

- Corporate EUC and operating-system integrity. Hardened Microsoft Windows builds, secure boot and platform protections where supported, operating-system code-signing enforcement, application control, endpoint protection, EDR, patching and configuration-compliance mechanisms protect corporate EUC devices.
- Server, virtualisation and firmware integrity. Enterprise hosting teams maintain approved server and virtual-machine images, hypervisor and management components, firmware and driver updates, platform attestation or secure-boot capabilities where available, and infrastructure integrity monitoring.
- Approved software distribution and code-signing services. Enterprise packaging, software-distribution, certificate, key-management and code-signing services provide controlled mechanisms for deploying approved thick-client installers, scripts and other signed artefacts.
- Enterprise repositories and build platforms. Where centrally provided, source-code repositories, artefact repositories, package registries and build or release platforms enforce access control, change history, branch or approval rules, protected storage and retention of identifiable artefacts.
- Managed database, middleware and platform integrity. Enterprise service owners protect shared database engines, middleware, messaging, file services and other managed platforms, including their binaries, firmware where relevant, configuration and administrative change records.
- Central detection and response. Enterprise endpoint, server, configuration and security-monitoring services detect selected unauthorised changes, failed signature or policy checks and suspicious modification activity, and route alerts to the SOC or responsible support team.
The application owner must identify the inherited services used by the application and cross-reference their evidence. The application is not expected to implement its own firmware-verification platform, Windows system-file protection, endpoint agent, enterprise signing infrastructure or duplicate file-integrity service where approved enterprise controls already provide that capability.

### Minimum application-specific integrity requirements

Each application must implement the following sensible minimum for software, configuration and information that the application team owns or controls:

1.  Use controlled and identifiable application artefacts. Source code, build definitions, packages, installers, scripts, database migrations, configuration templates and release artefacts must be held in approved repositories and associated with a version, release identifier, cryptographic digest or other reliable immutable reference.

2.  Verify artefacts before deployment. Application releases and updates must be obtained from the approved source and checked for authenticity and integrity before promotion or installation. Thick-client installers and executable code should use the approved corporate code-signing process. Server-side packages, scripts and deployment bundles must be verified by signature, digest, trusted repository metadata or an equivalent controlled mechanism.

3.  Protect the build and release path. Only authorised personnel and service identities may change source, build definitions, dependencies, release approvals or production artefacts. Build and deployment activity must be attributable, and production releases must be promoted from controlled outputs rather than rebuilt or manually substituted outside the approved process.

4.  Control third-party and open-source components. Record material libraries, packages, runtimes and vendor components; obtain them from approved sources; retain version and origin information; and verify available signatures, checksums or repository metadata. A software bill of materials or equivalent dependency record should be maintained where proportionate to application complexity and risk.

5.  Detect unauthorised changes to application components. Apply proportionate integrity checking to production application binaries, scripts, deployment definitions, critical application-controlled configuration, database schema or migration state, and other components whose alteration could affect security or business processing. This may use file-integrity monitoring, signed packages, immutable deployment, version reconciliation, configuration comparison or controlled redeployment from the approved baseline.

6.  Protect the integrity of important business information. Restrict write and update paths, validate authorised state changes, preserve transaction and audit history, and use database constraints, record versioning, reconciliation, checksums, digital signatures or equivalent controls where accidental or malicious alteration would create material harm. The control should be proportionate: not every ordinary record requires a cryptographic signature.

7.  Protect transfers and imports against undetected alteration. Where the application imports, exports, exchanges or batch-processes important information, use trusted transport and, where needed, record counts, control totals, message authentication, signatures, digests, sequence checks or acknowledgements to detect truncation, duplication, substitution or unauthorised modification.

8.  Respond safely to integrity failures. A failed signature, digest, provenance, schema, reconciliation or integrity check must prevent deployment or processing where continuing could create material risk. Otherwise, the application must quarantine or isolate the affected artefact or information, preserve evidence, alert the responsible team and restore from an approved source or known-good state.

9.  Record integrity-relevant activity. Log release promotion, package verification, signature or digest failure, unauthorised component change, critical configuration modification, database schema change, integrity-control override and restoration activity. Relevant events must be forwarded to enterprise monitoring where technically supported.

10.  Test integrity controls. Confirm during initial deployment and after material change that signed or verified artefacts are accepted, altered or unapproved artefacts are rejected or detected, alerts reach the intended recipient, and restoration from an approved source produces the expected application state.

### Proportionate implementation guidance

A small application may satisfy SI-07 through protected source control, versioned release packages, checksums or signatures, controlled deployment, database constraints, audit history and verification of the installed release. A complex multi-tier application should normally add protected build pipelines, dependency and provenance records, signed or digest-pinned artefacts, automated configuration or schema comparison, selected file-integrity monitoring, and reconciliation of high-value information flows. Integrity controls must concentrate on components and information whose unauthorised alteration could change access decisions, security behaviour, financial or operational outcomes, regulatory records or evidence.

### Expected evidence and assessment artefacts

- Approved source, build and artefact repository settings, including access and change history
- Release manifest identifying artefacts, versions, dependencies and cryptographic digests or signatures
- Code-signing, certificate and key-management records for application artefacts where applicable
- Software bill of materials or equivalent dependency and provenance record, proportionate to risk
- Production integrity-check, version-reconciliation, configuration-comparison or file-integrity results
- Database schema and migration records, information-reconciliation controls and relevant audit history
- Integrity failure, quarantine, alert and restoration test evidence
- Cross-reference to inherited EUC, hosting, firmware, repository, signing, EDR and monitoring controls
### Continuous monitoring and measures

- Production deployments not traceable to an approved and identifiable release artefact
- Unsigned, unverified or digest-mismatched application deployment attempts
- Critical application components without an appropriate integrity-verification mechanism
- Unauthorised or unexplained differences between approved and deployed application state
- Third-party components without recorded source, version or integrity information
- Integrity alerts, reconciliation failures or schema differences awaiting resolution
- Use of integrity-control overrides and whether each use was approved and reviewed
- Age and outcome of the latest integrity-control and restoration test
### Relationship with related controls

CM-02 defines the approved application baseline against which integrity can be checked. CM-05 restricts who may make changes, while CM-06 defines approved security-relevant settings. SI-02 governs correction of known flaws, SI-03 addresses malicious code, SI-10 validates information at application entry points, SA-11 tests software during development, and AU-02 and SI-04 provide the logging and monitoring needed to detect and investigate unauthorised changes.

### Addendum trigger

> **Template note:** Use an addendum when an application or supplier component cannot be signed, hashed, versioned or obtained from an approved repository; production artefacts can be changed outside the controlled release path; critical application files, configuration, database structures or information cannot be checked against an approved state; a required vendor package has unverifiable origin or integrity; firmware or specialist hardware falls within the application boundary rather than an inherited enterprise service; integrity failures cannot automatically block, quarantine or alert; or restoration from a known-good state cannot be demonstrated. The addendum must identify the affected artefact, component or information, the standard approach, implemented approach, rationale, risk, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## IA-02 - Identification and Authentication (Organisational Users)

### Control objective and responsibility model

IA-02 requires organisational users to be uniquely identified and their claimed identities authenticated before access is granted. Authentication strength must be appropriate to the access path, privilege and risk, and authentication mechanisms must resist replay and other relevant attacks. Identification and authentication establish who is requesting access; they do not by themselves grant permission to use a function or view information. In this corporate model, the enterprise provides authoritative workforce identities, corporate authentication, multi-factor authentication, hardened Microsoft Windows sign-in, VPN authentication, privileged-access authentication and federation or single sign-on services. Each application remains responsible for integrating correctly with those services, binding the authenticated identity to the correct application account and session, requiring fresh or stronger authentication for sensitive activity where justified, and securely authenticating application-owned services and interfaces. This implementation reflects IA-02 and the associated assessment objectives in NIST SP 800-53 and SP 800-53A, with authentication strength informed by the current NIST Digital Identity Guidelines [1][2][6].

### Inherited enterprise identification and authentication controls

The following capabilities are inherited when the application uses approved corporate identity, EUC, VPN and privileged-access services. They are implemented and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Authoritative corporate identity. Each organisational user is assigned a unique corporate identifier linked to an approved employee, contractor or other authorised identity and governed through the enterprise joiner-mover-leaver process.
- Corporate authentication and single sign-on. Enterprise identity services authenticate users and provide approved directory, federation, token-based or integrated Microsoft Windows authentication mechanisms for internal applications.
- Multi-factor authentication. MFA is enforced by enterprise identity, VPN and privileged-access services for the access paths and account types defined by corporate policy, including remote VPN access and privileged administration. Phishing-resistant methods are preferred where risk and available technology warrant them.
- Hardened Microsoft Windows EUC sign-in. Corporate EUC devices use the managed Windows authentication configuration, device identity, credential-protection and screen-lock controls. Applications installed on the EUC inherit the authenticated user context only through an approved integration.
- Corporate VPN authentication. A remote corporate EUC device uses its approved VPN client, corporate account, MFA and device-compliance checks to establish an encrypted connection to the corporate network. VPN authentication establishes an approved network access path but does not replace application authentication or application authorisation.
- Privileged authentication. Dedicated privileged accounts, PAM controls, stronger authentication, session brokering or controlled credential use are provided for enterprise infrastructure and, where integrated, application administration.
- Enterprise cryptographic and machine-identity services. PKI, certificate issuance, managed service accounts, secrets management and approved token services provide authentication mechanisms for devices, services and machine-to-machine connections where available.
- Central authentication monitoring. Enterprise identity, VPN, Windows, PAM and security-monitoring services record authentication successes, failures, lockouts, MFA events, anomalous sign-in and relevant account activity.
The application owner must identify the inherited identity and authentication services used by the application and must not create a parallel password store or local authentication mechanism where an approved corporate service can meet the requirement.

### Minimum application-specific identification and authentication requirements

Each application must implement the following sensible minimum for identities, sessions and interfaces that the application team owns or controls:

1.  Use unique corporate identities for interactive users. The application must normally accept the approved corporate identity and preserve the unique user identifier supplied by the trusted identity service. Display names, email addresses and other mutable attributes must not be used as the sole identity key where a stable corporate identifier is available.

2.  Validate authentication assertions at a trusted application component. The application must verify the issuer, intended audience, cryptographic signature, validity period, nonce or equivalent replay protection, and other security-relevant properties of tokens or assertions before creating a session. Identity information received from an untrusted client, query parameter or unvalidated header must not be accepted.

3.  Bind the authenticated identity securely to the application session. A session must be associated with the correct corporate identity and protected against substitution, fixation and reuse. It must be terminated or re-established when authentication expires, the corporate account is disabled, privilege materially changes or another defined security condition occurs.

4.  Do not treat network location as proof of identity. Connection from the corporate network, including through the corporate VPN, confirms an approved access path but does not identify the user to the application. The approved user or service authentication mechanism must complete before access is granted.

5.  Apply fresh or stronger authentication to sensitive activity where proportionate. High-risk functions such as privileged administration, security-setting change, emergency access, release of highly restricted information or other material actions should require a recent or step-up authentication event when supported by the enterprise identity service and justified by risk.

6.  Keep authentication separate from authorisation. Successful corporate authentication must map to an application account and role only through the approved account-management and access-enforcement process. Unknown, unassigned, disabled or ineligible identities must be denied even when corporate authentication succeeds.

7.  Authenticate application services and interfaces. APIs, scheduled tasks, integrations, database connections and other machine-to-machine interactions must use dedicated, approved identities and mechanisms such as managed service accounts, certificates, mutually authenticated protocols or protected tokens. Static shared passwords must be avoided.

8.  Prevent shared or anonymous interactive authentication. Shared, generic, anonymous, guest and vendor accounts must not be used for ordinary interactive access. Where an unavoidable emergency or specialist account exists, it must be governed under AC-02 and IA-05 and its use made individually attributable through appropriate compensating controls.

9.  Fail securely when authentication cannot be verified. If the identity service, token validation, certificate validation or required authentication context is unavailable or invalid, the application must deny new access and sensitive actions rather than silently downgrade to weaker or unauthenticated access. Existing sessions must be handled according to a documented, risk-based fail-safe rule.

10.  Record authentication-relevant application events. The application must log successful and failed application authentication, invalid or expired assertions, session creation and termination, step-up authentication, service-authentication failure and use of local or emergency authentication. Logs must not contain passwords, private keys, complete tokens or other reusable secrets.

### Proportionate implementation guidance

A small internal application may satisfy IA-02 through enterprise single sign-on, stable corporate identifiers, secure session handling and central authentication logs. A thick client should normally use approved integrated Windows or enterprise token-based authentication and must not rely solely on the fact that the software is installed on a corporate EUC device. A multi-tier or service-oriented application should validate identity at the trusted application tier and use dedicated service identities between tiers. Applications should not implement their own MFA prompts, password rules or authenticator lifecycle unless the approved enterprise identity service cannot provide the required capability.

### Expected evidence and assessment artefacts

- Application authentication design identifying user, administrator and service authentication paths
- Identity-provider, federation, integrated Windows or token-validation configuration
- Evidence that unique, stable corporate identifiers are preserved and mapped to application accounts
- Session-management and re-authentication settings, including sensitive-function requirements
- Service and machine-identity inventory showing authentication mechanism, owner and purpose
- Test evidence for valid, invalid, expired, replayed, disabled-account and unavailable-identity-service scenarios
- Authentication and session audit events forwarded to enterprise monitoring
- Cross-reference to inherited corporate identity, MFA, Windows EUC, VPN, PAM, PKI and secrets-management controls
### Continuous monitoring and measures

- Interactive application access paths not using the approved corporate identity service
- Application-local, shared, anonymous or generic authentication mechanisms in production
- Authentication assertions accepted without complete issuer, audience, signature or expiry validation
- Service identities using shared or unmanaged static credentials
- Authentication or session failures not producing the required audit events
- Sensitive functions lacking the required recent or step-up authentication
- Disabled or ineligible corporate identities retaining usable application sessions
- Age and result of the latest authentication integration and fail-safe test
### Relationship with related controls

IA-02 identifies and authenticates organisational users and application-relevant services. IA-05 governs the authenticators, credentials, certificates, keys and tokens used in that process. AC-02 governs account lifecycle and eligibility; AC-03 enforces the actions permitted after authentication; AC-06 limits privilege; AC-17 governs the remote-access path; and AU-02 and SI-04 provide logging and monitoring of authentication activity. Successful VPN authentication under AC-17 does not remove the requirement for application identification and authentication under IA-02.

### Addendum trigger

> **Template note:** Use an addendum when the application cannot use the approved corporate identity or single sign-on service; requires a local password store, shared, generic, anonymous, guest or vendor authentication; cannot support MFA or recent authentication for an applicable high-risk function; accepts identities through an untrusted or incompletely validated header or assertion; cannot uniquely identify users; relies only on corporate-network or VPN location as proof of identity; uses unmanaged static service credentials; cannot terminate or restrict sessions following account disablement; or must continue operating when authentication cannot be validated. The addendum must identify the affected access path or identity type, the standard approach, implemented approach, rationale, risk, compensating controls, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## AC-05 - Separation of Duties

### Control objective and responsibility model

AC-05 requires duties that could enable error, fraud, misuse or unauthorised change to be divided so that one individual cannot complete a high-risk activity without independent involvement, oversight or detection. The organisation must identify and document the duties that require separation and define the application roles or access authorisations that enforce that separation. Separation of duties may be preventive, such as requiring different people to request and approve a payment, or detective, such as an independent review of privileged changes where full preventive separation is not proportionate. In this corporate model, the enterprise provides separation for infrastructure administration, corporate identity, privileged access, software release, network change and other shared services. Each application remains responsible for identifying its own conflicting business and administrative duties and enforcing a sensible minimum set of role, approval and review controls. This implementation reflects AC-05 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A [1][2].

### Inherited enterprise separation-of-duties controls

The following controls are inherited when the application uses approved corporate identity, EUC, hosting, network, change, security and software-delivery services. They are implemented and evidenced by the relevant enterprise service owners rather than recreated by each application team:

- Corporate identity lifecycle. Authoritative personnel records, account provisioning and account approval are performed through separate HR, management, identity-administration and service-management responsibilities, with changes attributable to the initiating and approving parties.
- Privileged access administration. Request, approval, assignment, use and review of privileged enterprise accounts are separated through enterprise identity and PAM processes where supported. Privileged users do not normally approve their own access.
- Infrastructure administration. Network, firewall, VPN, Microsoft Windows EUC, server, virtualisation, storage, backup, database-platform and enterprise-security administration are assigned to approved specialist roles. Application users and ordinary application administrators do not receive these infrastructure privileges.
- Enterprise change and release governance. Change request, technical implementation, testing, approval and production deployment are separated to the extent proportionate to risk. Controlled software-distribution and release services record who built, approved and deployed corporate packages and infrastructure changes.
- Security monitoring and investigation. Enterprise SOC, audit, risk or assurance personnel retain independent access to relevant logs, alerts and evidence and are not dependent solely on the administrator or team whose activity is being reviewed.
- Backup, recovery and key-management services. Where centrally provided, responsibilities for backup operation, restoration approval, cryptographic key administration and use are divided among approved service roles and recorded through the enterprise process.
The application owner must identify the inherited enterprise processes on which the application relies. The application must not duplicate these controls, but it must not undermine them by giving an application role the ability to bypass enterprise approval, deployment, logging or privileged-access arrangements.

### Minimum application-specific separation-of-duties requirements

Each application must implement the following sensible minimum for the business processes, administrative functions and technical changes that the application owns or controls:

1.  Identify material conflicts. Document the combinations of application duties that could allow one person to initiate, approve and conceal a material transaction, unauthorised access, data change, security change or production change. Focus on credible high-impact conflicts rather than attempting to separate every routine task.

2.  Separate access request from approval. A person must not approve their own application access, privileged role or material entitlement. Access approval must be performed by an authorised manager, application owner, information owner or delegated approver with sufficient knowledge of the requested duty.

3.  Separate routine use from application administration. Ordinary business processing and privileged application administration must use distinct roles. Where the same individual legitimately performs both, they must use the privileged role only for authorised administration and their privileged activity must be recorded and independently reviewable.

4.  Separate initiation from approval for high-risk business actions. Material payments, releases, records disposal, bulk data disclosure, sensitive case closure, master-data change or equivalent high-impact actions must require an independent approval or verification where the business and information risk warrants it.

5.  Separate development and testing from production release. Application code, packages, scripts, database migrations and security-relevant configuration must not normally be promoted to production solely by the person who created them. Production release must include independent review, approval or an enterprise-controlled pipeline that enforces the approved build, test and deployment stages.

6.  Separate security administration from audit oversight. Users who can assign roles, alter security settings, change retention rules or administer application audit functionality must not be able to suppress or alter the independent evidence used to review their activity. Audit review should be performed by a different role or enterprise monitoring function.

7.  Restrict emergency combinations of duty. Temporary combination of normally separated duties may be permitted only for a documented operational emergency, with explicit approval where practicable, time-limited access, enhanced logging and prompt independent review after use.

8.  Enforce separation through application roles and workflow. Conflicting permissions must be prevented through role design, incompatible-role rules, approval workflow, transaction limits, dual control or another reliable mechanism. A written procedure alone is insufficient where the application can technically enforce the separation.

9.  Review conflicts and exceptions. Application roles and assignments must be checked periodically and after material organisational, workflow or role changes to identify incompatible combinations, self-approval, excessive privilege or unreviewed emergency access. Conflicts must be removed or formally accepted with compensating controls.

10.  Record high-risk actions and approvals. The application must retain sufficient evidence to show who initiated, approved, implemented and reviewed a material business or administrative action, including the outcome and time. Relevant events must be forwarded to enterprise monitoring where technically supported.

### Proportionate implementation guidance

A small application does not need an elaborate segregation-of-duties engine. It may use a concise conflict matrix, separate administrator and user roles, manager approval for access, independent approval for a small number of high-risk actions and periodic review of privileged activity. A complex transaction or records application should normally use workflow-enforced maker-checker controls, incompatible-role rules, transaction thresholds, separate release stages and automated conflict reporting. Where staffing is genuinely too limited to maintain full preventive separation, the preferred compensating approach is narrowly scoped privilege, strong attribution, timely independent review and documented management acceptance - not an undocumented combination of duties.

### Expected evidence and assessment artefacts

- Application separation-of-duties and incompatible-role matrix
- Role and workflow design showing initiator, approver, administrator and reviewer responsibilities
- Sample access requests demonstrating that users did not approve their own access
- Sample high-risk transactions or changes showing independent approval and attributable actions
- Release records showing creation, review, approval and production deployment responsibilities
- Privileged and security-administration activity reviewed by an independent role or enterprise function
- Periodic conflict-review results and records of removed or accepted conflicts
- Emergency-access approvals, time limits, logs and post-use reviews where applicable
- Cross-reference to inherited identity, PAM, change, release, infrastructure and monitoring controls
### Continuous monitoring and measures

- Users holding incompatible application roles without an approved exception
- Self-approved access, role changes, transactions or security changes
- High-risk actions completed without the required independent approval
- Production deployments performed without independent review or controlled-pipeline approval
- Application administrators able to alter or suppress the only evidence of their own activity
- Emergency combinations of duty not reviewed promptly after use
- Age and outcome of the latest application role-conflict review
- Repeat separation-of-duties exceptions indicating that role or workflow design is ineffective
### Relationship with related controls

AC-05 identifies duties that must be divided and the roles or access authorisations used to divide them. AC-02 governs assignment and review of the relevant accounts and roles; AC-03 enforces the approved permissions and workflow decisions; AC-06 limits each role to the minimum privilege needed; CM-05 restricts access to make changes; SA-11 supports independent testing; and AU-02, SI-04 and CA-07 provide the evidence and monitoring needed to detect conflicts, self-approval and misuse.

### Addendum trigger

> **Template note:** Use an addendum when limited staffing, a legacy product or a supplier-controlled design prevents separation of applicable high-risk duties; one person must request and approve their own access; developers must deploy their own production changes without independent review; an administrator can alter or suppress the only audit evidence of their activity; the application cannot prevent incompatible roles or self-approval; or emergency combinations of duty must remain standing rather than time-limited. The addendum must identify the conflicting duties, affected roles or functions, standard approach, implemented approach, rationale, risk, compensating controls, independent review arrangements, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## CM-05 - Access Restrictions for Change

### Control objective and responsibility model

CM-05 requires physical and logical access to make system changes to be defined, documented, approved and enforced. The control is concerned with who or what can alter hardware, software, firmware, configuration, data structures, deployment artefacts and security-relevant settings - not merely whether a change ticket exists. Access to change must be limited to authorised personnel and technical identities, separated from ordinary use, attributable to the individual or process making the change, and reviewed for continued need. In this corporate model, the enterprise controls changes to corporate EUC devices, networks, operating systems, virtualisation, managed platforms and shared security services. Each application remains responsible for restricting access to its source, build and release mechanisms, application configuration, database structures, application administration and production deployment paths. This implementation reflects CM-05 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A, supported by the security-focused configuration-management practices in NIST SP 800-128 [1][2][8].

### Inherited enterprise access restrictions for change

The following controls are inherited when the application uses approved corporate EUC, hosting, network, identity, software-distribution and managed-platform services. They are implemented and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Corporate EUC change restriction. Hardened Microsoft Windows builds, Group Policy, endpoint-security agents, VPN clients, drivers and approved software are changed through centrally managed administration and software-distribution services. Ordinary users do not normally have local administrator rights or the ability to alter protected corporate configuration.
- Server and hosting-platform change restriction. Access to change physical servers, virtual machines, server operating systems, hypervisors, storage, backup platforms and management tooling is restricted to authorised enterprise support roles using dedicated administration accounts and approved management paths.
- Network and boundary change restriction. Router, switch, firewall, segmentation, VPN gateway, DNS, load-balancer and other network changes are limited to authorised network roles and governed through enterprise change, approval, implementation and logging processes.
- Managed database, middleware and enterprise-service change restriction. Where these are centrally provided, platform configuration, engine-level security settings, identity services, PKI, PAM, logging, EDR, scanning, backup and other shared services are changed only by their authorised service owners.
- Enterprise privileged-access controls. Dedicated privileged accounts, multi-factor authentication, PAM or controlled elevation, management-network restrictions, session logging and periodic privilege review protect access to enterprise change functions.
- Physical access to infrastructure. Data-centre, communications-room and infrastructure hardware access is restricted through corporate physical-security controls and authorised maintenance procedures.
The application owner must identify the inherited services and administration boundaries used by the application. Application personnel must not be granted infrastructure-wide privilege simply to perform application support, and the application must not provide a route that bypasses enterprise platform or network change controls.

### Minimum application-specific access restrictions for change

Each application must implement the following sensible minimum for application components and settings that the application team owns or controls:

1.  Identify application change functions and authorised roles. Maintain a concise record of the repositories, build systems, release pipelines, deployment tools, application administration functions, configuration stores, database migration mechanisms and other facilities that can change the production application. Define which roles may request, approve, prepare, deploy, verify and, where necessary, reverse those changes.

2.  Restrict source and artefact modification. Only authorised developers or maintainers may alter application source, build definitions, deployment scripts, database migrations, configuration templates and release artefacts. Access must use named corporate or approved technical identities, be limited to the relevant application or repository, and be removed when duties change.

3.  Protect the production deployment path. Production deployment must occur through the approved release or software-distribution mechanism. Direct copying, manual replacement or alteration of production binaries, thick-client packages, scripts or configuration outside that mechanism must be prevented where technically possible and otherwise tightly restricted, approved and recorded.

4.  Restrict application security and administrative changes. Only explicitly authorised application administrators may change roles, permissions, security settings, authentication integration, logging, retention, interfaces, scheduled jobs, feature controls or other security-relevant application configuration. Ordinary users and support users must not inherit these rights by default.

5.  Restrict database and information-structure changes. Database schema, stored procedure, trigger, migration, reference-data and other structural changes must use controlled migration or administration mechanisms. Application support personnel must not receive unrestricted database-owner or equivalent rights merely to deploy or troubleshoot the application.

6.  Use dedicated, least-privileged change identities. Human administrators must use separate privileged roles or accounts for production change. Build agents, deployment services and configuration-management tools must use dedicated technical identities limited to the specific repositories, environments, components and actions they require. Shared interactive administrator accounts are prohibited.

7.  Separate preparation, approval and production execution where proportionate. The person who creates a material change must not normally be the sole approver and deployer. Independent review, release approval or a controlled pipeline must enforce the required separation, particularly for security-relevant, high-impact and emergency changes.

8.  Prevent bypass and uncontrolled alternative paths. Disable or restrict production consoles, direct database editing, local server logon, removable-media installation, developer back doors, hidden maintenance interfaces and other routes that could alter the application outside the approved process. Any retained emergency path must be explicitly controlled and monitored.

9.  Control emergency change access. Emergency change privilege must be granted only to designated personnel, limited to the affected application and period of need, protected by strong authentication and enhanced logging, and followed by retrospective approval, verification, baseline update and removal of temporary access.

10.  Record and review change-access activity. The application and supporting tools must record material changes and failed change attempts with the acting identity, affected object or setting, previous and new state where practicable, outcome and time. Repository, pipeline, deployment, application-administration and database-change events must be retained and forwarded to enterprise monitoring where technically supported.

11.  Review change privileges periodically. Access to source repositories, build and release services, production administration, deployment tools and database-change mechanisms must be reviewed at a frequency proportionate to risk and after personnel, supplier, role, support-model or architecture changes. Excessive, dormant, duplicate or orphaned privileges must be removed promptly.

### Proportionate implementation guidance

A small application may satisfy CM-05 through protected source control, a limited administrator group, a controlled corporate deployment package, manager or owner approval, separate production credentials and retained change logs. A complex multi-tier application should normally use protected branches, mandatory review, immutable or signed release artefacts, environment-specific deployment identities, automated production gates, privileged session control, database migration tooling and continuous reconciliation of change privileges. The control does not require a large configuration control board for every change; it requires access to change to be no broader than necessary, appropriately approved and reliably enforced.

### Expected evidence and assessment artefacts

- Application change-role and access matrix covering source, build, release, configuration and production
- Repository, branch-protection, build-system and artefact-repository access settings
- Production deployment and software-distribution permissions, including technical identities
- Application administrator and database-change privilege lists with approving owners
- Sample normal and emergency changes showing request, approval, implementation and verification
- Audit records for repository changes, release approvals, deployments and application configuration changes
- Periodic review results for developer, administrator, deployment and database-change access
- Cross-reference to inherited enterprise EUC, hosting, network, PAM, platform and physical-access controls
### Continuous monitoring and measures

- Production change paths or consoles not represented in the approved change-access matrix
- Users or service identities with production-change access but no current owner or approval
- Direct or manual production changes performed outside the approved deployment mechanism
- Shared, generic or interactive technical accounts able to make production changes
- Developers able to approve and deploy their own material changes without an approved control
- Emergency change access not removed or reviewed within the defined period
- Failed or unauthorised change attempts and unexplained changes to security-relevant settings
- Overdue reviews of repository, deployment, administrator or database-change privileges
### Relationship with related controls

CM-05 restricts who and what may make changes. CM-02 defines the approved baseline; CM-03 governs the process for requesting, analysing, approving and recording changes; CM-06 defines required security configuration settings; AC-05 separates conflicting change duties; AC-06 limits change privilege; SI-07 verifies the integrity and provenance of changed artefacts; SA-11 provides testing before release; and AU-02, SI-04 and CA-07 provide logging, monitoring and continuing assurance over change activity.

### Addendum trigger

> **Template note:** Use an addendum when a legacy, specialist or supplier-controlled application requires direct production editing; cannot use the approved repository, software-distribution or deployment process; requires shared or generic administrator credentials; cannot separate development, approval and deployment; requires application personnel to hold infrastructure-wide, local administrator, database-owner or equivalent privilege; retains an undocumented or unmonitored maintenance path; cannot attribute production changes to an individual or controlled technical identity; or cannot periodically review and remove change access. The addendum must identify the affected component, change path or privilege, standard approach, implemented approach, rationale, risk, compensating controls, monitoring, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## RA-05 - Vulnerability Monitoring and Scanning

### Control objective and responsibility model

RA-05 requires the organisation to monitor for vulnerabilities in the system and hosted applications, scan at an organisation-defined frequency and when newly reported vulnerabilities may affect the system, keep the vulnerabilities checked by scanning tools current, analyse results, remediate legitimate findings in accordance with risk, and share relevant information with responsible parties. Vulnerability monitoring is broader than running a periodic network scanner: it includes awareness of vulnerable products and dependencies, appropriate technical testing, validation of findings, prioritisation using threat and business context, and confirmation that corrective action has worked. In this corporate model, the enterprise provides most hardware, network, Microsoft Windows, server operating-system, virtualisation and managed-service scanning. Each application remains responsible for the application code, thick-client package, application dependencies, application-controlled configuration, database objects and internal interfaces that enterprise infrastructure scanning cannot assess adequately. This implementation reflects RA-05 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A, and is supported by NIST enterprise patch-management and secure software-development guidance [1][2][4][7].

### Inherited enterprise vulnerability-monitoring and scanning controls

The following capabilities are inherited when the application uses approved corporate EUC, network, hosting and managed-platform services. They are implemented and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Corporate EUC assessment. Enterprise security and EUC services assess hardened Microsoft Windows devices for operating-system, browser, VPN client, approved software, firmware, driver and security-configuration vulnerabilities, using centrally managed inventory, endpoint, patching and scanning capabilities.
- Network and boundary scanning. Enterprise network and security teams discover and assess approved internal addresses, network devices, firewalls, VPN gateways, load balancers, exposed ports, protocols, services and relevant network configurations. Scanning is authorised, scheduled and tuned to avoid unacceptable disruption.
- Server and hosting-platform scanning. Enterprise hosting teams conduct authenticated or otherwise suitably privileged assessment of physical servers, virtual machines, server operating systems, hypervisors, storage, backup agents and standard platform components, and track infrastructure findings to the responsible service owner.
- Managed database, middleware and enterprise-service assessment. Where centrally provided, database engines, middleware, messaging, file services, identity, PKI, PAM, logging, EDR, backup and other shared services are assessed by their enterprise owners using appropriate product, configuration and vulnerability information.
- Vulnerability intelligence and tool maintenance. Enterprise security services maintain approved scanning tools, plugins, signatures, vulnerability feeds, severity information and relevant threat intelligence, and notify service or application owners when newly identified vulnerabilities may affect their components.
- Central finding, risk and remediation workflow. Enterprise vulnerability-management or service-management processes record findings, ownership, severity, exploitability, remediation targets, exceptions, retest results and overdue items, and provide governance reporting and escalation.
- Enterprise patch and update services. Approved operating-system, platform and corporate software patches are identified, prioritised, tested, deployed and verified through the enterprise patch-management process.
The application owner must identify the inherited scanning and patching services used by the application, ensure that the enterprise inventory and scan scope include its infrastructure, and respond to findings allocated to the application. The application must not deploy duplicate infrastructure scanners or independently scan corporate networks without authorisation.

### Minimum application-specific vulnerability-monitoring and scanning requirements

Each application must implement the following sensible minimum for code, packages, dependencies, configuration and interfaces that the application team owns or controls:

1.  Maintain an assessable application inventory. Record the supported application release, thick-client package where applicable, server-side components, runtimes, frameworks, libraries, third-party products, database technology and schema level, internal interfaces and material build or deployment dependencies. The inventory must be sufficiently current to determine whether a newly reported vulnerability is relevant.

2.  Monitor vulnerability sources relevant to the application. Review supplier advisories, approved vulnerability feeds, dependency and package alerts, enterprise notifications and other authoritative sources for the application and its components. Newly reported vulnerabilities that may affect the application must be assessed without waiting for the next scheduled scan.

3.  Assess application dependencies and release artefacts. Use software-composition analysis, package or artefact scanning, a software bill of materials or an equivalent controlled dependency check to identify known vulnerable libraries, runtimes, installers and third-party components. Checks should occur during build or release and periodically against deployed or supported versions.

4.  Assess application code where the organisation develops or materially maintains it. Apply proportionate static analysis, secure code review or equivalent testing to identify coding weaknesses before production release. Scanning results must be reviewed by personnel able to distinguish genuine issues from tool noise and understand the affected application context.

5.  Assess running application interfaces. Internal web applications, APIs, services and other remotely reachable application interfaces must receive authenticated dynamic vulnerability testing where technically suitable and safe. Thick clients and non-web applications must receive equivalent testing of their exposed services, local privilege boundaries, update mechanisms, data handling and server interactions as applicable.

6.  Include application-controlled configuration. Check security-relevant application settings, enabled features, default or test functions, authentication and session configuration, roles, file permissions, service endpoints, database privileges, logging and cryptographic configuration against the approved baseline. Enterprise operating-system scanning does not replace this application-level review.

7.  Use appropriate scope, credentials and safe methods. Scans must cover all applicable production components and representative non-production environments, use authenticated access where needed for meaningful results, and be configured to avoid data corruption, service interruption or uncontrolled test data. Intrusive exploitation and full penetration testing are governed separately under CA-08.

8.  Analyse and prioritise findings using context. Validate findings, remove confirmed false positives with an auditable rationale, identify affected releases and data, and prioritise action using technical severity, known exploitation, exposure, privilege required, business criticality and potential impact. A scanner severity alone must not be the only risk decision.

9.  Assign and track corrective action. Each legitimate application finding must have an accountable owner, agreed treatment, target date and status in the approved vulnerability, defect, risk or POA&M process. Remediation may include patching, upgrading, configuration change, code correction, feature removal, isolation or a formally approved compensating control.

10.  Verify remediation. Re-scan, re-test or otherwise verify that corrective action removed or acceptably reduced the vulnerability and did not introduce a material regression. Closure must be based on evidence rather than the implementation team's assertion alone.

11.  Protect vulnerability information. Detailed findings, exploitability information, credentials and scan output must be restricted to personnel and services with an operational need. Reports provided more widely should contain only the detail necessary for risk and remediation decisions.

12.  Integrate results with continuous monitoring. Material findings, newly affected components, repeated failures, overdue remediation and accepted exceptions must feed the application security-status reporting under CA-07 and incident processes where evidence suggests exploitation.

### Proportionate implementation guidance

A small commercially supplied thick-client application may rely mainly on enterprise EUC and server scanning, supplier advisories, package-version checks, authenticated assessment of its internal service, and documented tracking of vendor fixes. A small internally developed web application should normally add dependency scanning, static analysis and authenticated dynamic testing. A complex multi-tier application should normally automate software-composition and static checks in its pipeline, maintain an accurate dependency or software-bill-of-materials record, perform authenticated interface testing, assess application configuration, correlate results with deployed versions and retest closure. Tools should be selected for the technology and risk; using every available scanner is neither necessary nor desirable.

### Expected evidence and assessment artefacts

- Current application component, dependency and supported-version inventory
- Documented application vulnerability-monitoring and scanning scope, methods, frequencies and owners
- Supplier-advisory, vulnerability-feed and newly reported vulnerability review records
- Dependency, package, artefact or software-composition analysis results
- Static analysis or secure code-review results for organisation-developed code, where applicable
- Authenticated dynamic, API, service or equivalent application-interface assessment results
- Application security-configuration assessment or baseline-comparison results
- Finding validation, risk prioritisation, false-positive rationale and remediation records
- Retest or other verification evidence supporting closure
- Cross-reference to inherited EUC, network, hosting, managed-platform, patching and enterprise vulnerability-management evidence
### Continuous monitoring and measures

- Production application components or dependencies absent from the assessable inventory
- Supported releases not assessed within their defined application scanning frequency
- Newly reported critical or actively exploited vulnerabilities awaiting applicability assessment
- Critical and high application findings open beyond their target remediation date
- Findings closed without retest or equivalent verification evidence
- Application interfaces excluded from assessment without an approved rationale
- Scanner, package or analysis rules significantly out of date
- Repeated vulnerabilities indicating ineffective root-cause correction
- False-positive or risk-acceptance decisions lacking an owner, rationale or review date
### Relationship with related controls

RA-05 identifies and monitors vulnerabilities and verifies their treatment. SI-02 governs timely correction of system flaws; CM-02 and CM-06 provide the approved baseline and settings against which configuration weaknesses are assessed; CM-08 supplies component inventory; SI-07 addresses software and information integrity; SA-11 provides developer testing; CA-08 provides deeper adversarial penetration testing; and CA-07 tracks continuing control effectiveness and unresolved risk. A penetration test does not replace routine vulnerability monitoring, and routine scanning does not replace a properly scoped penetration test.

### Addendum trigger

> **Template note:** Use an addendum when an application, legacy product or supplier component cannot be included in the approved enterprise or application scanning process; authenticated assessment is not technically possible; scanning could create unacceptable operational or safety risk; source code or dependency information is unavailable; a supported component cannot be patched or upgraded within the corporate target; the supplier prohibits or materially limits testing; a finding must remain open beyond the standard period; or vulnerability information cannot be shared with the normal enterprise process. The addendum must identify the excluded component, test or finding, the standard approach, implemented approach, rationale, risk, compensating controls, alternative monitoring, remediation or retirement plan, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## CM-08 - System Component Inventory

### Control objective and responsibility model

CM-08 requires a documented inventory of the components within the system boundary. The inventory must accurately reflect the system, include the components needed for effective accountability, be recorded at a level of detail appropriate to management and risk, avoid duplicate ownership or accounting, and be reviewed and updated at an organisation-defined frequency and when relevant changes occur. A component inventory is not merely a list of servers. It is the authoritative record used to understand what forms the application service, who is responsible for each part, which version or instance is approved, where it is deployed, and which enterprise service or application team maintains it. In this corporate model, the enterprise owns the authoritative inventory for corporate EUC devices, network equipment, physical and virtual infrastructure, operating systems and centrally managed services. Each application remains responsible for identifying the application software, packages, tiers, application-owned services, dependencies, data stores and interfaces that enterprise infrastructure inventories do not describe at sufficient application detail. This implementation reflects CM-08 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A, supported by the security-focused configuration-management principles in NIST SP 800-128 [1][2][8].

### Inherited enterprise component-inventory controls

The following inventory capabilities are inherited when the application uses approved corporate EUC, network, hosting and managed-platform services. They are maintained and evidenced by the relevant enterprise service owners rather than duplicated in the application inventory:

- Corporate EUC inventory. The enterprise EUC service records corporately managed Microsoft Windows devices, including device identifier, hardware make and model, operating-system version, assigned user or support group, management status, security tooling and relevant lifecycle or support information.
- Network and boundary inventory. Enterprise network teams maintain records for routers, switches, firewalls, VPN gateways, load balancers, wireless infrastructure, network security appliances and other managed communications components, including ownership, location, approved configuration and support status.
- Physical and virtual hosting inventory. Enterprise hosting services maintain records for physical servers, virtual machines, hypervisors, storage, backup infrastructure and management platforms, including unique identifiers, host or cluster relationship, operating-system image, environment, owner and lifecycle status.
- Managed operating-system and platform inventory. Supported server operating systems, database engines, middleware, messaging, file services and other centrally managed platforms are recorded by their enterprise owners with version, instance, responsible team and support information.
- Enterprise security and shared-service inventory. Identity, PKI, PAM, SIEM, EDR, vulnerability scanning, software distribution, backup, time, DNS and other shared services are inventoried and governed by their enterprise service owners.
- Enterprise discovery and reconciliation. Asset-management, endpoint-management, network-discovery, virtualisation and vulnerability-management tools identify managed infrastructure and support reconciliation of authoritative records with observed components.
The application owner must reference the authoritative enterprise records for inherited components and must not create a second competing inventory that assigns different ownership or lifecycle status. Where an enterprise component is dedicated to the application, the application inventory may reference its enterprise identifier and describe its application role without duplicating the full enterprise asset record.

### Minimum application-specific component-inventory requirements

Each application must maintain a concise inventory of the components that define the application service and are owned, selected, configured or deployed by the application team. The sensible minimum is:

1.  Define the inventory scope and system boundary. Identify which application components are inside the application boundary, which are inherited enterprise services, and which are interconnected systems outside the boundary. The inventory must be consistent with the architecture and data-flow description in Section 2.

2.  Record application deployable components. Include each approved thick-client package, internal web application, presentation component, application service, API, scheduled job, batch process, integration service, database schema or application-owned data store, messaging component and other deployable unit that is necessary to operate or secure the application.

3.  Record material software dependencies. Include supported runtimes, frameworks, major libraries, vendor products, plugins, agents and other dependencies whose version, support status or vulnerability could materially affect the application. A detailed software bill of materials may be referenced rather than copied into the main inventory.

4.  Use stable identifiers and sufficient accountability information. Each inventory entry must have a unique or reliably distinguishable identifier and, as applicable, component name, type, purpose, version or release, environment, hosting or installation location, enterprise asset reference, responsible owner or support role, supplier, support status and relationship to the application tier or service.

5.  Distinguish instances from component types. The inventory must make clear whether an entry represents a software product or package, a deployed instance, a server-side service, an EUC installation package, a data store or an inherited platform. Similar components may be grouped only where the grouping preserves accurate version, ownership, environment and lifecycle information.

6.  Prevent duplicate or conflicting accounting. Each component must have one authoritative owner and source record. References to the same component in architecture, vulnerability, baseline, support or service records must use a common identifier or an unambiguous mapping. Duplicate records that could produce conflicting versions, ownership or remediation status must be reconciled.

7.  Include non-production components where they can affect production security. Development, test, build and release components must be included or referenced when they hold restricted information, production secrets, production connectivity, release authority or another capability that could materially affect the production application. Ordinary developer workstations remain part of the enterprise EUC inventory unless specially dedicated or placed within the application boundary.

8.  Record external and supplier-managed dependencies clearly. Although cloud and Internet-connected services are outside the scope of this master standard, an internally connected supplier product, licence service, appliance or specialist component must be identified with its ownership, support arrangement, connectivity and boundary status. Any non-standard external connection must be documented in the Application Addendum.

9.  Update the inventory through change and release processes. New, changed, replaced, retired or removed application components must be reflected in the inventory at or before production release. Emergency changes must update the inventory promptly after implementation. The inventory must not depend solely on an annual manual exercise.

10.  Reconcile documented and observed state. Periodically compare the application inventory with release manifests, software-distribution records, deployment tools, hosting records, vulnerability scan scope and other observed evidence. Unauthorised, unknown, unsupported or missing components must be investigated, removed, brought under management or formally documented as a deviation.

11.  Retain lifecycle and status information. Record whether a component is planned, active, temporarily disabled, end-of-support, under replacement or retired. Retired components must be removed from active deployment and scanning scope only after their removal has been verified and required records have been retained.

### Proportionate implementation guidance

A small application may satisfy CM-08 with a controlled component register linked to its release record and enterprise asset identifiers. A thick-client application should identify the approved package and version, supporting runtime, internal service endpoints and software-distribution reference; it does not need to list every corporate EUC device because those devices are inventoried by the enterprise. A multi-tier application should normally use deployment manifests, configuration-management records, repository metadata and automated discovery or reconciliation to maintain its service, dependency, data-store and interface inventory. The inventory should be detailed enough to support vulnerability assessment, patching, incident response, change control and recovery, but not so granular that it becomes unmaintainable.

### Expected evidence and assessment artefacts

- Approved application component inventory or register with unique identifiers, versions, environments and owners
- Architecture and data-flow documentation reconciled with the component inventory
- Release manifests, software-distribution records, deployment definitions or artefact repository records
- Software bill of materials or equivalent dependency record where proportionate
- Enterprise asset, virtualisation, network or managed-service references for inherited components
- Reconciliation results showing comparison between documented and observed components
- Records for unauthorised, unsupported, duplicate, missing and retired components and their resolution
- Inventory review and approval records, including evidence of updates following material changes
### Continuous monitoring and measures

- Application components discovered without an inventory record or accountable owner
- Inventory entries with missing version, environment, support status or enterprise reference
- Differences between the component inventory, release manifest and deployed state
- Unsupported or end-of-life components still active in production
- Retired components still reachable, installed, scanned or receiving data
- Duplicate records assigning conflicting ownership, version or remediation status
- Production releases completed without the required inventory update
- Age and outcome of the latest inventory reconciliation and owner review
### Relationship with related controls

CM-08 identifies the components that make up the application and assigns accountability for them. CM-02 defines their approved baseline state; CM-06 defines required security settings; CM-03 and CM-05 govern changes and access to make changes; RA-05 uses the inventory to determine scanning scope and vulnerability applicability; SI-02 uses it to identify affected components requiring flaw remediation; SI-07 protects the integrity of software and information; and CA-07 uses inventory accuracy as part of continuing assurance. The organisation-wide system inventory under programme-management controls is distinct from this component-level application inventory.

### Addendum trigger

> **Template note:** Use an addendum when a legacy, specialist or supplier-controlled application cannot provide reliable component identifiers, version or support information; a component is deliberately omitted from enterprise discovery or scanning; multiple teams claim conflicting ownership; the deployed state cannot be reconciled with the documented inventory; an unsupported component must remain in service; a dedicated appliance, firmware-bearing device or supplier-managed component falls within the application boundary; or inventory updates cannot be integrated with the standard change and release process. The addendum must identify the affected component or inventory limitation, the standard approach, implemented approach, rationale, risk, compensating controls, alternative monitoring, accountable owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## SI-10 - Information Input Validation

### Control objective and responsibility model

SI-10 requires information inputs to be checked for validity so that the system accepts only data that conforms to defined formats, ranges, types, lengths, sources and business rules. Validation must occur before the input is trusted or used in security-relevant processing. The control applies to human-entered data, files, messages, API requests, batch feeds, thick-client submissions, configuration values and machine-to-machine inputs. Input validation is not simply a user-interface convenience: it is a security control intended to prevent malformed, unexpected or unauthorised input from causing injection, corruption, incorrect processing, privilege bypass or service failure. In this corporate model, the enterprise provides secure operating platforms, network controls, malware protection, approved development tooling and shared gateways where used. Each application remains responsible for defining and enforcing the validation rules for the information it receives. This implementation reflects SI-10 and its assessment objectives in NIST SP 800-53 and SP 800-53A, supported by the secure software practices in NIST SP 800-218 [1][2][4].

### Inherited enterprise input-protection capabilities

The following capabilities are inherited when the application uses approved corporate EUC, hosting, network and shared security services. They reduce exposure to malformed or malicious input but do not replace application-level validation:

- Hardened Microsoft Windows EUC controls. Corporate EUC devices provide managed browsers, approved thick-client software, endpoint protection, application control and operating-system security features that reduce unauthorised software execution and some unsafe content handling.
- Network and boundary controls. Enterprise firewalls, segmentation, VPN, reverse proxies, load balancers and, where provided, API gateways or managed file-transfer services restrict approved communication paths, sources, protocols and message sizes.
- Malicious-code and content protection. Enterprise EDR, anti-malware, file scanning and approved content-transfer services detect or block known malicious files and active content at designated points.
- Managed platform protections. Corporate web servers, database engines, middleware, messaging platforms and supported runtimes provide platform-level parsing, protocol handling, size limits, encoding functions and security updates when used according to the approved baseline.
- Enterprise identity and access context. Corporate identity, device and service attributes provide trusted context that applications may use when deciding whether a source is authorised to submit particular information.
- Development and testing services. Approved source control, build pipelines, code analysis, dependency scanning and test environments support identification of input-handling defects before production release.
The application owner must identify the inherited services used by the application. Network location, authenticated identity, malware scanning or a trusted corporate device does not make the submitted information valid; the application must still validate the content and permitted business state.

### Minimum application-specific input-validation requirements

Each application must implement the following sensible minimum for every input channel that it owns or controls:

1.  Identify all trust boundaries and input channels. Maintain a concise record of user forms, thick-client fields, files, APIs, messages, batch feeds, command parameters, database imports, configuration values and administrative interfaces through which information enters a component or changes processing state.

2.  Define an allow-list validation specification. For each material input, define the expected data type, structure, syntax, length, range, precision, character set, encoding, mandatory or optional status and permitted values. Prefer explicit allowed formats and values over attempts to identify every possible bad value.

3.  Validate at the trusted processing component. Client-side checks may improve usability, but authoritative validation must be performed by the server-side or otherwise trusted component before the data is processed, stored, executed, used in a query or passed to another trust zone. Thick-client input must be revalidated by the receiving service where one exists.

4.  Apply contextual and business-rule validation. Confirm that the input is permitted for the authenticated identity, role, record state, transaction sequence and business process. A syntactically valid value must still be rejected when it is not authorised or is inconsistent with the current business state.

5.  Use safe parsing and parameter handling. Use supported parsers, parameterised database operations, strongly typed interfaces and safe library functions. Do not construct commands, queries, paths, templates or expressions by directly concatenating untrusted input. Canonicalise or normalise input before comparison where alternate encodings or representations could bypass a rule.

6.  Validate files and structured content. Check approved file type, actual content or signature where practicable, size, name, extension, structure, archive depth, compression ratio and required metadata. Parse structured formats using hardened libraries with unnecessary features such as external entity resolution or embedded active content disabled unless explicitly required.

7.  Constrain quantities and resource use. Apply sensible limits to message size, field length, record count, nesting depth, pagination, query complexity, upload volume, batch size, processing time and request rate so that valid-looking input cannot consume disproportionate resources or cause denial of service.

8.  Validate sources and interfaces. Accept machine-generated input only from approved internal systems, services, queues, files or endpoints and require the expected authenticated service identity, protocol, schema and message context. Source trust does not remove the need to validate the content.

9.  Handle invalid input safely. Reject or quarantine invalid input without partial processing where that could create inconsistency. Return a clear but non-sensitive error to the user or calling service, preserve sufficient diagnostic detail for authorised support personnel, and avoid revealing queries, stack traces, secrets, internal paths or security rules.

10.  Record and monitor material validation failures. Log security-relevant validation failures, repeated malformed requests, rejected files, schema violations, limit breaches and attempted injection with the source identity or service, interface, reason category, outcome and time. Do not record passwords, complete tokens or restricted data unnecessarily.

11.  Test both accepted and rejected input. Tests must cover normal boundary values, missing and extra fields, invalid type and encoding, excessive size and depth, malformed files and messages, unauthorised business states, common injection patterns and failure of dependent validation services. Regression tests must be retained for significant defects.

12.  Review rules when interfaces or risks change. Update validation specifications and tests when a field, schema, file type, integration, business rule, dependency or threat changes. Temporary compatibility logic that accepts broader input must be removed when no longer required or documented as a deviation.

### Proportionate implementation guidance

A small internal forms application may satisfy SI-10 with strongly typed server-side validation, field length and range checks, parameterised database queries, safe error handling and regression tests. A thick client must validate locally for usability and safety, but any receiving server or database procedure must independently validate the request. A multi-tier application should normally use centrally defined schemas, reusable validation libraries, API contract validation, file-processing controls, request and resource limits, and automated negative tests in its release pipeline. Validation should be concentrated at trust boundaries and authoritative processing points rather than duplicated inconsistently in every screen.

### Expected evidence and assessment artefacts

- Application input-channel and trust-boundary inventory
- Input-validation specification, data dictionary, API schema or equivalent rules
- Source-code or configuration evidence of trusted-side validation and parameterised operations
- File-upload, import, structured-content and resource-limit configuration
- Unit, integration, negative, boundary and regression test results
- Sample validation-failure logs and evidence of forwarding to enterprise monitoring
- Defect and remediation records for input-validation weaknesses
- Cross-reference to inherited network, malware-protection, identity, platform and development controls
### Continuous monitoring and measures

- Input channels without a documented validation specification or accountable owner
- Interfaces relying only on client-side validation
- Use of dynamic query, command, path or template construction with untrusted input
- Accepted file or message types without size, structure or content checks
- Repeated validation failures, injection attempts or resource-limit breaches
- Validation defects reopened or repeated after remediation
- Production interfaces whose schemas or rules differ from the approved specification
- Age and outcome of the latest negative and boundary-value test
### Relationship with related controls

SI-10 validates information before it is trusted or processed. AC-03 and AC-04 determine whether the authenticated user or service may perform the action and whether the information may flow to the destination. SI-03 detects malicious code in files and content but does not determine whether otherwise benign data is valid. SI-07 protects integrity after acceptance, SI-11 governs safe error handling, SA-11 tests the implementation during development, and AU-02 and SI-04 provide logging and monitoring of material validation failures.

### Addendum trigger

> **Template note:** Use an addendum when a legacy, specialist or supplier-controlled application cannot perform authoritative server-side validation; relies on client-side checks alone; must accept undocumented, ambiguous or excessively broad formats; cannot safely limit file, message or resource size; uses dynamic commands or queries that cannot be parameterised; cannot validate an internal supplier or machine feed; cannot reject malformed input without disrupting an essential business process; or cannot log and test material validation failures. The addendum must identify the affected input channel or rule, the standard approach, implemented approach, rationale, risk, compensating controls, monitoring, remediation or replacement plan, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## SI-02 - Flaw Remediation

### Control objective and responsibility model

SI-02 requires the organisation to identify, report and correct software and firmware flaws, test updates before installation where appropriate, install security-relevant updates within defined risk-based timescales, and incorporate flaw remediation into configuration management. Flaw remediation includes vendor patches, application code corrections, configuration changes, component upgrades, compensating controls and retirement where no safe correction is available. In this corporate model, the enterprise owns remediation of corporate EUC devices, network equipment, operating systems, virtualisation platforms and centrally managed services. Each application remains responsible for application code, thick-client packages, application-owned dependencies, database objects, application configuration and supplier components selected or managed by the application team. This implementation reflects SI-02 and its assessment objectives in NIST SP 800-53 and SP 800-53A, and follows the enterprise patch-management lifecycle described in NIST SP 800-40 Revision 4 [1][2][7].

### Inherited enterprise flaw-remediation controls

The following capabilities are inherited when the application uses approved corporate EUC, network, hosting and managed-platform services. They are implemented and evidenced by the relevant enterprise service owners rather than repeated by each application team:

- Corporate EUC remediation. The enterprise EUC service identifies, tests, deploys and verifies Microsoft Windows, browser, VPN-client, approved software, driver and firmware updates on corporately managed devices, using central patching and endpoint-management services.
- Network and boundary remediation. Enterprise network teams remediate flaws in routers, switches, firewalls, VPN gateways, load balancers, network appliances and associated firmware or software through controlled maintenance and change processes.
- Server and hosting remediation. Enterprise hosting teams patch and upgrade physical servers, virtual machines, server operating systems, hypervisors, storage, backup agents and standard infrastructure components.
- Managed platform and enterprise-service remediation. Where centrally provided, database engines, middleware, messaging, file services, identity, PKI, PAM, SIEM, EDR, vulnerability-scanning, backup and other shared services are remediated by their enterprise service owners.
- Enterprise vulnerability and patch intelligence. Security and service-management functions monitor vendor advisories, vulnerability intelligence, known exploitation and product support status, and assign relevant remediation actions to responsible owners.
- Enterprise patch governance and reporting. Corporate processes define risk-based remediation targets, emergency treatment, testing expectations, exception and risk-acceptance routes, deployment verification, overdue-item escalation and governance reporting.
The application owner must identify the inherited services used by the application, ensure enterprise owners know which infrastructure supports it, and act on application-relevant notifications. The application team must not independently modify enterprise-owned operating systems, firmware, network devices or managed platforms outside the approved service process.

### Minimum application-specific flaw-remediation requirements

Each application must implement the following sensible minimum for flaws in software, packages, dependencies, configuration and supplier components that the application team owns or controls:

1.  Receive and assess flaw information. Monitor enterprise notifications, supplier advisories, vulnerability findings, dependency alerts, penetration-test findings, code-analysis results and incident lessons relevant to the application. Determine promptly whether each credible flaw affects a supported or deployed application version.

2.  Record affected components and ownership. Link the flaw to the application component, release, dependency, thick-client package, interface, database object or configuration affected. Assign an accountable remediation owner and record the finding in the approved defect, vulnerability, risk or POA&M process.

3.  Prioritise using risk and exploitation context. Set the treatment priority and target date using technical severity, known or likely exploitation, exposure within the corporate network, privileges required, data sensitivity, business criticality, availability impact and available compensating controls. A vendor or scanner score alone must not be the sole decision.

4.  Select an appropriate treatment. Apply a vendor patch, supported upgrade, application code correction, dependency replacement, configuration change, feature disablement, isolation or another effective remediation. When no immediate correction is available, implement time-limited compensating controls and an approved remediation, replacement or retirement plan.

5.  Test before production deployment. Test security updates and code corrections in a representative non-production environment where practicable. Confirm that the flaw is addressed, essential business functions still operate, security controls remain effective, data and interfaces are not damaged, and rollback or recovery arrangements are understood.

6.  Use the controlled change and release process. Promote application fixes through approved source, build, review, approval and deployment mechanisms. Thick-client updates must be packaged and distributed through the corporate software-distribution service. Server-side changes, database migrations and configuration corrections must use the approved production deployment path.

7.  Meet defined remediation timescales. Correct flaws within the corporate risk-based target applicable to their severity and exploitation status. Actively exploited, critical or otherwise urgent flaws must use the emergency change or mitigation process where waiting for the routine release cycle would create unacceptable risk.

8.  Verify installation and effectiveness. Confirm that the intended version or correction reached all applicable production components, that superseded or vulnerable versions are no longer active, and that re-scan, re-test or other evidence demonstrates effective remediation. Deployment success alone is not sufficient proof of closure.

9.  Maintain supported software. Track end-of-support and end-of-life dates for application products, runtimes, libraries and supplier components. Plan upgrades or replacement early enough to avoid unsupported production operation. Unsupported components must not remain without formally approved risk treatment and enhanced monitoring.

10.  Handle failed or deferred remediation safely. Where an update fails, causes unacceptable regression or cannot be installed, restore the approved state where necessary, preserve evidence, reassess risk, apply interim safeguards, notify responsible owners and retain the item as open until correction is verified or risk is formally accepted.

11.  Communicate operationally significant changes. Inform service desk, operations, security monitoring, business owners and affected users where remediation changes expected behaviour, requires downtime, alters support procedures or creates indicators that must be monitored.

12.  Retain traceable evidence. Maintain the advisory or finding, applicability decision, affected component, risk decision, testing, approval, deployment, verification, exception and closure evidence needed to demonstrate the complete remediation lifecycle.

### Proportionate implementation guidance

A small supplier application may rely mainly on enterprise infrastructure patching, vendor advisories, controlled deployment of vendor releases and documented verification. An internally developed application should normally integrate dependency and code findings into its backlog and release pipeline, with risk-based expedited handling for urgent flaws. A complex multi-tier application should normally automate component matching, patch or dependency alerts, testing, deployment status and re-verification across environments. Applications do not need to create a separate patch-management organisation, but they must have an accountable owner, a reliable route from finding to verified correction and a clear process for exceptions.

### Expected evidence and assessment artefacts

- Application flaw-remediation procedure or workflow showing roles, prioritisation and target timescales
- Supplier advisories, vulnerability findings and applicability assessments linked to affected components
- Defect, vulnerability, risk or POA&M records with owner, treatment and target date
- Patch, upgrade, code-change, dependency-change or configuration-remediation records
- Non-production testing, regression, security and rollback evidence
- Approved change, release and deployment records, including thick-client distribution where applicable
- Installation and effectiveness verification, including re-scan or re-test evidence
- Unsupported-component register and approved exception, replacement or retirement plans
- Cross-reference to inherited enterprise EUC, network, hosting, managed-platform and patch-governance evidence
### Continuous monitoring and measures

- Critical, actively exploited or high-risk application flaws awaiting applicability assessment
- Open application flaws beyond the defined remediation target
- Production components running a vulnerable, superseded or unsupported version
- Remediation records closed without installation and effectiveness verification
- Failed or partially deployed application updates not fully resolved
- Temporary compensating controls or exceptions beyond their review or expiry date
- Repeated flaws caused by the same dependency, coding pattern or release weakness
- Age and outcome of the latest supported-component and end-of-life review
### Relationship with related controls

RA-05 identifies and monitors vulnerabilities; SI-02 governs their correction and verification. CM-02 and CM-08 identify the approved baseline and affected components; CM-03 and CM-05 control the change process and access to make changes; SI-07 protects the integrity and provenance of update artefacts; SA-11 provides testing before release; CA-07 tracks continuing effectiveness and overdue risk; and IR-05 is engaged where a flaw is suspected to have been exploited. Applying a patch without verifying its deployment and effectiveness does not complete SI-02.

### Addendum trigger

> **Template note:** Use an addendum when a legacy, specialist or supplier-controlled component cannot be patched, upgraded or replaced within the corporate target; the supplier has not issued a correction; source code or build capability is unavailable; a required update cannot be tested in a representative environment; remediation would create unacceptable operational, safety or regulatory impact; a thick-client or server update cannot use the approved distribution or deployment process; an unsupported component must remain in service; or verification of installation and effectiveness is not technically possible. The addendum must identify the flaw and affected component, standard approach, implemented treatment, rationale, risk, compensating controls, monitoring, remediation or retirement plan, accountable owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## AC-17 - Remote Access

### Control objective and responsibility model

AC-17 requires remote access to be authorised, documented, monitored and controlled. Remote access must use approved methods, pass through managed access-control points, protect the confidentiality and integrity of the session, and apply restrictions appropriate to the type of access and privilege involved. For this controlled master standard, remote access is narrowly defined: an authorised corporate user may use a corporately managed Microsoft Windows EUC device, with the approved corporate VPN client installed, to establish an encrypted VPN connection to the corporate network from a remote location. After successful corporate-account authentication, multi-factor authentication and device-compliance checks, the EUC device is logically connected to the corporate network and uses the same internal application access paths as an on-site corporate EUC device. Remote access from personal, unmanaged, supplier-owned or non-corporate devices is outside this standard. Direct application exposure to the Internet, public networks, cloud services or externally initiated connections is prohibited. This implementation reflects AC-17 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A, supported by NIST SP 800-46 guidance on enterprise remote-access security [1][2][9].

### Inherited enterprise remote-access controls

The following capabilities are inherited when the application uses the approved corporate VPN, identity, EUC, network and security services. They are implemented and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Approved remote-access method. The corporate VPN is the standard remote-access mechanism. Alternative remote-access technologies, direct inbound application access, consumer remote-desktop services and unmanaged tunnels are prohibited unless separately approved and documented in an Application Addendum.
- Managed corporate EUC device. Remote access is permitted only from a corporately owned or corporately managed Microsoft Windows EUC device that meets the hardened build, endpoint-protection, encryption, patching, device-management and compliance requirements. The approved VPN client is installed and maintained through the enterprise EUC service.
- Corporate identity and multi-factor authentication. The enterprise identity service authenticates the user with a unique corporate account and MFA before the VPN session is established. Account status, joiner-mover-leaver events, authenticator management and relevant sign-in risk controls are inherited from enterprise identity services.
- Managed access-control point. All remote network access terminates at an enterprise-managed VPN gateway or equivalent approved remote-access gateway. The gateway enforces authentication, device-compliance, routing, session and security policies before corporate-network access is provided.
- Encrypted tunnel and session protection. The VPN service uses approved cryptographic mechanisms and corporate certificate or key-management services to protect remote-access traffic against disclosure and alteration while traversing untrusted networks.
- Network routing and boundary controls. Remote VPN users are placed into approved corporate network segments and are subject to enterprise routing, firewall, segmentation, DNS, proxy and boundary-monitoring controls. Split tunnelling is prohibited so that corporate application traffic and applicable device traffic follow the controlled corporate path.
- Remote privileged administration. Remote execution of privileged commands and access to security-relevant information are controlled through enterprise PAM, dedicated privileged accounts, approved management paths, strong authentication and session monitoring. Ordinary VPN access does not confer administrative privilege.
- Monitoring, logging and response. Enterprise VPN, identity, Windows EUC, network, EDR, PAM and SIEM services record remote-access authentication, connection, disconnection, device-compliance, routing and suspicious activity and support SOC investigation and incident response.
- Session and service availability controls. The enterprise remote-access service defines permitted session durations, inactivity behaviour, reauthentication conditions, capacity management, maintenance, emergency disablement and service recovery.
The application owner must identify the inherited VPN, identity, EUC, network and monitoring services used by the application. The application team must not create a separate inbound remote-access route, install an independent remote-access gateway or permit a supplier support connection that bypasses the approved enterprise service.

### Minimum application-specific remote-access requirements

Because the remote corporate EUC device operates as a corporate-network endpoint after the VPN connection is established, the application-specific requirements are intentionally limited. Each application must implement the following sensible minimum:

1.  Use the same application access path for on-site and VPN-connected users. The application must be reached through its approved internal hostname, address, load balancer, service endpoint or thick-client service path. It must not expose a separate Internet-facing, externally routed or remote-only application endpoint.

2.  Require normal application identification, authentication and authorisation. A successful VPN connection establishes the network path but does not itself grant application access. The application must continue to use the approved corporate identity integration, account status, application roles, access enforcement and least-privilege controls.

3.  Do not weaken controls for VPN-connected users. Security configuration, session protection, application roles, information-flow rules, logging, data handling and input validation must be equivalent to those applied to an on-site corporate EUC device unless a stricter remote condition is justified.

4.  Restrict privileged remote activity. Application administration performed through VPN must use the approved privileged role, account and management route. Privileged application functions must not be exposed to ordinary users merely because they are connected through the VPN, and direct remote administration of servers, databases or security components must remain under enterprise PAM and management-network controls.

5.  Avoid unmanaged local storage and offline processing. Thick clients and browser-based applications must not create additional remote-working data stores, caches, exports or offline copies beyond those permitted for an on-site corporate EUC device. Where local storage is necessary, it must use approved corporate device encryption, access control, retention and secure-clean-up mechanisms.

6.  Handle loss of VPN connectivity safely. The application must define how active sessions, transactions, file transfers and unsaved changes behave when the VPN connection is interrupted. It must avoid partial, duplicate or unauthorised processing and must require re-establishment of the trusted network and authentication context before sensitive processing resumes.

7.  Log application activity consistently. Application authentication, session, privileged-action, security-relevant transaction and authorisation events must be recorded in the same manner for VPN and on-site access. Where available, the application should preserve sufficient session or source context to support correlation with enterprise VPN and identity logs without relying on a shared VPN address as the user identity.

8.  Test the remote access path. Before production use and after material change to the application, VPN, identity integration or network path, verify that a compliant corporate EUC device can connect through the approved VPN, reach only the authorised internal application paths, authenticate correctly, perform permitted functions, produce the required logs and fail safely when the VPN session is terminated.

9.  Document application-specific restrictions. If the application is not suitable for remote use because of operational, safety, data-handling, performance or licensing constraints, the restriction must be enforced and recorded in the Application Addendum. A user instruction alone is insufficient where technical enforcement is reasonably available.

### Proportionate implementation guidance

A small internal web application normally requires no remote-access component of its own: it uses the existing corporate VPN path, corporate sign-on and ordinary application controls. A thick-client application must be installed through the corporate software-distribution service and must communicate only with its approved internal service endpoints after the VPN is established. A multi-tier application should treat VPN-connected EUC traffic as traffic entering from the approved corporate user-access segment and should apply the same tier separation and server-side authorisation as on-site access. Applications must not attempt to determine trust solely from an IP address associated with the VPN pool.

### Expected evidence and assessment artefacts

- Application architecture and data-flow diagram showing the approved corporate VPN access path
- Cross-reference to enterprise VPN, identity, MFA, EUC compliance, network and monitoring controls
- Application network-flow and firewall records showing no direct Internet or external inbound path
- Application authentication and authorisation design demonstrating that VPN connection alone does not grant access
- Remote-access test results using a compliant corporate Microsoft Windows EUC device
- Evidence that split tunnelling, unmanaged devices and alternative remote-access methods are prohibited by enterprise controls
- Application session and transaction behaviour for VPN interruption and reconnection
- Application and enterprise log-correlation evidence for representative VPN access
- Approved restrictions or Application Addendum entries where remote use is limited or prohibited
### Continuous monitoring and measures

- Application endpoints reachable from public or non-corporate networks
- Remote application sessions originating from unmanaged or non-compliant devices
- Alternative tunnels, remote-desktop paths or supplier connections bypassing the corporate VPN
- VPN-connected users receiving application access without normal application authentication and authorisation
- Privileged remote activity not using the approved privileged account and management path
- Remote application events that cannot be correlated with enterprise VPN and identity records
- Application failures, duplicate processing or data-integrity issues caused by VPN interruption
- Age and outcome of the latest end-to-end remote-access test
### Relationship with related controls

AC-17 governs the approved remote-access method, authorisation, managed access-control point, session protection and monitoring. SC-07 protects the corporate and internal network boundaries; IA-02 and IA-05 govern user and service authentication and authenticators; AC-02 governs account eligibility; AC-03 and AC-06 enforce application permissions and least privilege; SC-08 and related cryptographic controls protect information in transit; AU-02 and SI-04 provide logging and monitoring; and CM-06 defines secure VPN, EUC and application settings. A successful VPN connection does not replace any of these application-level controls.

### Addendum trigger

> **Template note:** Use an addendum when the application requires a remote-access method other than the approved corporate VPN; must be accessed from a non-corporate, unmanaged, supplier-owned or personally owned device; requires split tunnelling; exposes a separate remote or Internet-facing endpoint; permits direct inbound support or administration; cannot use corporate identity and MFA; requires broader remote privileges than on-site use; stores additional restricted information locally for offline operation; cannot fail safely when the VPN connection is interrupted; or cannot produce adequate remote-access and application audit evidence. The addendum must identify the affected access path, user group, device type or function, the standard approach, implemented approach, rationale, risk, compensating controls, monitoring, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## CA-08 - Penetration Testing

### Control objective and responsibility model

CA-08 requires penetration testing to be conducted at an organisation-defined frequency on an organisation-defined scope. Penetration testing uses authorised, controlled attempts to bypass or circumvent security controls and demonstrate the practical effect of exploitable weaknesses. It is distinct from routine vulnerability scanning: scanning identifies potential weaknesses, while penetration testing chains techniques and exercises trust boundaries, identities, roles, workflows and technical controls to determine whether an attacker could achieve a material objective. Testing must be planned, authorised, bounded by documented rules of engagement, performed by suitably skilled and sufficiently independent personnel, and followed by risk-based remediation and verification. In this corporate model, the enterprise provides governance, authorised testers, network and infrastructure testing, test coordination, evidence handling and central finding management. Each application remains responsible for defining its application scope, providing representative access and business context, ensuring application-specific attack paths are tested, supporting safe execution, and correcting findings. This implementation reflects CA-08 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A, together with the planning, execution and rules-of-engagement guidance in NIST SP 800-115 [1][2][10].

### Inherited enterprise penetration-testing controls

The following capabilities are inherited when the application participates in the approved corporate penetration-testing and assurance programme. They are implemented and evidenced by the relevant enterprise security, infrastructure and governance owners rather than recreated by each application team:

- Penetration-testing governance. The enterprise defines risk-based testing frequencies, qualification and independence expectations, authorisation routes, reporting requirements, severity criteria, escalation paths and circumstances requiring additional testing after significant change or threat information.
- Authorised test personnel. Testing is performed by approved internal specialists or contracted testers with appropriate competence, confidentiality obligations, access authorisation and independence from the personnel who designed or implemented the controls being assessed.
- Rules of engagement and legal authority. The enterprise establishes written rules of engagement before testing, including scope, permitted and prohibited techniques, dates and times, source systems, test accounts, data-handling rules, communications, emergency contacts, stop conditions, evidence protection and approval to conduct the defined activities.
- Corporate network and infrastructure assessment. Where included in the authorised scope, enterprise testers assess network segmentation, firewalls, VPN gateways, identity infrastructure, Microsoft Windows EUC controls, server operating systems, virtualisation, management networks and centrally managed platforms. Application teams do not independently test or exploit shared infrastructure without explicit approval.
- Safe test environment and coordination. Enterprise security, SOC, network and service-management teams coordinate allow-listing, monitoring, backups, operational windows, emergency response and restoration arrangements so that testing can be distinguished from hostile activity and stopped if unacceptable impact occurs.
- Central finding and risk management. Test findings are quality-reviewed, risk-rated, assigned to accountable owners and tracked through the approved vulnerability, risk, POA&M or corrective-action process. Significant findings are escalated to the system owner and relevant governance forum.
- Sensitive evidence protection. Credentials, exploit details, screenshots, data extracts, attack paths and reports are stored, transmitted, retained and disposed of through approved restricted-access mechanisms.
- Enterprise retest and closure assurance. The assurance function coordinates or validates retesting of material findings and retains evidence that corrective action is effective before closure.
The application owner must use the approved enterprise penetration-testing process and identify inherited infrastructure and shared services within scope. Application teams must not commission unapproved testing, run intrusive tools against the corporate network, or authorise a supplier to test shared services without the relevant enterprise owners' written approval.

### Minimum application-specific penetration-testing requirements

Each application must implement the following sensible minimum for the application functions, interfaces, identities, data and trust boundaries that it owns or controls:

1.  Define a risk-based application test scope. Identify the production-representative components, thick-client functions, internal web interfaces, APIs, services, authentication paths, role boundaries, privileged functions, data stores, file-processing functions, integrations and application-controlled network flows that require testing. Scope must reflect the actual architecture and the highest-impact information and business processes.

2.  Set an appropriate testing frequency and change trigger. Conduct testing at the corporate risk-based frequency and additionally after material architecture, authentication, authorisation, data-flow, privileged-function or externally supplied component changes where the change could create a new attack path. A routine minor release does not automatically require a full penetration test if proportionate security testing and change analysis demonstrate that the tested attack surface has not materially changed.

3.  Provide representative identities and roles. Supply controlled test accounts or equivalent access for ordinary users, distinct business roles, privileged application administrators, support roles and relevant service interfaces. Testing must examine horizontal and vertical privilege escalation, role confusion, unauthorised cross-record or cross-business access, and attempts to bypass approval or separation-of-duties controls.

4.  Test application trust boundaries and attack paths. Exercise the paths between the corporate Windows EUC device or approved test client, presentation tier, application or service tier, database or messaging tier and connected internal services. Testers should attempt to bypass client-side controls, manipulate requests, abuse internal interfaces, exploit excessive service permissions and combine weaknesses across tiers.

5.  Include thick-client risks where applicable. For locally installed applications, assess package integrity and update behaviour, local data and credential storage, insecure inter-process or local communications, privilege requirements, manipulation of client files or configuration, reverse engineering risk where material, and whether server-side controls revalidate client requests.

6.  Include internal web, API and service risks where applicable. Assess authentication and session handling, access control, input handling, injection, file processing, deserialisation, business-logic abuse, excessive data exposure, service-to-service authentication, error handling, security headers and relevant protocol or configuration weaknesses. Testing must not assume that an internal network source is trustworthy.

7.  Test high-impact business logic and information flows. Where relevant, attempt unauthorised initiation, approval, cancellation, duplication, replay, bulk extraction, record alteration, retention override, workflow bypass and movement of restricted information to an unauthorised role, record set, interface or destination.

8.  Use production-representative conditions without avoidable harm. Testing should use a representative non-production environment when it can faithfully reproduce production controls and data flows. Testing in production requires explicit approval and additional safeguards. Real restricted data must not be copied into test tools or reports unless specifically authorised and necessary; synthetic or sanitised data should be used where practical.

9.  Define and enforce safety constraints. The application owner and tester must agree prohibited actions, transaction limits, test-data rules, target exclusions, service-impact thresholds, stop conditions and recovery arrangements. Denial-of-service, destructive actions, uncontrolled persistence, social engineering and physical testing are excluded unless separately authorised in the rules of engagement.

10.  Support detection and response evaluation. Coordinate with the SOC so that selected test activity can demonstrate whether application and enterprise logging, alerting and investigation processes detect and explain the activity. Unannounced or partially announced testing may be used only where explicitly approved and safely controlled.

11.  Analyse and track findings using business context. Validate findings, identify the affected component, role, data and attack path, and prioritise remediation using exploitability, required access, available compensating controls, information sensitivity and potential business impact. Findings must have an accountable owner, target date and approved treatment.

12.  Verify corrective action. Material findings must be retested by the approved assurance function or suitably independent tester. Closure must show that the exploit path is removed or acceptably constrained and that the correction has not created a new material weakness. Risk acceptance requires documented approval and a review or expiry date.

### Proportionate implementation guidance

A small, low-complexity internal application may use a focused test of corporate sign-on, application roles, server-side authorisation, input handling, sensitive functions and its principal service interface. A thick-client application requires testing of both the installed Windows client and the receiving internal services; testing only the client or only the server is insufficient where security depends on both. A complex multi-tier application should normally receive scenario-based testing across tiers, service identities, business workflows and connected systems. The depth and frequency should reflect risk, complexity, rate of change, information sensitivity and previous findings. Penetration testing should complement - not duplicate or replace - secure development testing, vulnerability scanning and control assessment.

### Expected evidence and assessment artefacts

- Approved penetration-testing plan and application scope
- Signed rules of engagement, testing authority and emergency contact arrangements
- Tester competence, independence and confidentiality evidence
- Architecture, data-flow, role and trust-boundary information supplied to the tester
- Representative user, privileged and service test-account arrangements
- Penetration-test report describing methods, attack paths, evidence, impact and limitations
- SOC coordination and detection-response observations where included in scope
- Finding ownership, remediation, risk-acceptance and target-date records
- Independent retest or equivalent verification evidence supporting closure
- Cross-reference to inherited network, VPN, identity, EUC, hosting and enterprise assurance testing
### Continuous monitoring and measures

- Applications overdue for penetration testing against the approved risk-based frequency
- Material application changes completed without a documented penetration-test decision
- Application tiers, roles, interfaces or high-impact workflows omitted without an approved rationale
- Critical or high penetration-test findings open beyond their target date
- Findings closed without independent retest or adequate verification evidence
- Repeat or recurring attack paths indicating ineffective root-cause correction
- Tests conducted without approved rules of engagement or using unapproved source systems
- Sensitive test evidence stored outside the approved restricted-access location
- Age and outcome of the latest penetration test and remediation retest
### Relationship with related controls

CA-08 provides active, adversarial validation of whether controls can be bypassed and weaknesses combined into a practical attack path. RA-05 provides recurring vulnerability monitoring and scanning; SA-11 provides developer security testing before release; CA-02 assesses control implementation and effectiveness; CA-07 maintains ongoing assurance and tracks findings; SI-02 governs flaw remediation; SI-10 addresses input validation; AC-03 and AC-06 govern access enforcement and least privilege; and SI-04, AU-02 and IR-05 support detection, evidence and incident handling. Neither automated scanning nor a code review is a substitute for a properly scoped penetration test, and a penetration test is not a substitute for those continuing activities.

### Addendum trigger

> **Template note:** Use an addendum when the application cannot be tested at the corporate frequency; a supplier or licence term prohibits or materially restricts testing; production-representative testing cannot be achieved; an applicable tier, interface, role, business workflow or connected component must be excluded; test accounts or independent test access cannot be provided; testing could create unacceptable safety, operational or data risk; a material finding cannot be remediated or independently retested within the standard period; or sensitive test evidence cannot be handled through the approved enterprise process. The addendum must identify the affected scope or constraint, standard approach, implemented approach, rationale, risk, compensating controls, alternative assurance, remediation or retirement plan, owner, approval and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## AC-20 - Use of External Systems

### Control objective and responsibility model

AC-20 governs the use of external systems to access, process, store or transmit organisational information. For this control, an external system is a system that is not owned, operated or sufficiently controlled by the organisation, or for which the organisation cannot establish and verify the required security controls. The term does not simply mean a system located away from a corporate office. A corporately managed Microsoft Windows EUC device remains an organisational system when used remotely through the approved corporate VPN. Conversely, a personally owned computer, supplier-owned workstation, public kiosk, unmanaged mobile device or third-party system is external even if it can reach a corporate service. This controlled master standard prohibits external systems from accessing the covered applications or processing, storing or transmitting their restricted information. Cloud, SaaS, hybrid, Internet-facing and cloud-connected use cases are outside scope. This implementation reflects AC-20 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A, with remote-device considerations informed by NIST SP 800-46 [1][2][9].

### Inherited enterprise controls over external-system use

The following capabilities are inherited when the application uses approved corporate identity, EUC, VPN, network, endpoint-security and information-protection services. They are implemented and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Corporate device policy and ownership. The organisation defines which device classes are authorised to access corporate systems. Access to applications covered by this standard is limited to corporately managed, hardened Microsoft Windows EUC devices. Personally owned, public, unmanaged and supplier-owned user devices are prohibited.
- Device management and compliance. Corporate EUC services enforce approved Windows configuration, patching, endpoint protection, encryption, application control, local firewall, software distribution, inventory and device-compliance requirements. Devices that do not meet the required state may be blocked or restricted.
- Corporate identity and conditional access. Enterprise identity services require unique corporate accounts and apply authentication, MFA and device or access-context policies where defined. Account authentication alone does not override the requirement to use an approved corporate device.
- Corporate VPN restriction. Remote application access is permitted only through the approved VPN client installed on a compliant corporate EUC device. The VPN gateway performs corporate-account, MFA and device-compliance checks and does not provide a route for personal or unmanaged devices.
- Network access control and segmentation. Enterprise network controls restrict application paths to approved corporate network segments and managed access points. Direct Internet access, public-network access, supplier tunnels and alternative remote-access paths are prohibited unless separately authorised.
- Information-protection controls. Enterprise endpoint, email, web, removable-media, printing, data-loss-prevention and encryption controls restrict unauthorised transfer of organisational information to personal storage, consumer services, unmanaged media and other external systems where those capabilities are provided.
- Supplier and third-party access governance. Corporate procurement, security, contract, identity and service-management processes define the conditions under which a supplier may receive a corporate account, managed corporate device or controlled support path. A supplier-owned device is not treated as corporate merely because the supplier is authorised to provide support.
- Monitoring and incident response. Enterprise identity, VPN, endpoint, network, DLP and security-monitoring services detect selected attempts to use unapproved devices, paths, storage services or transfer mechanisms and support investigation and containment.
The application owner must identify and rely on the inherited enterprise controls that restrict external-system use. The application team must not establish a bypass, exception group or alternate interface that permits an unmanaged or non-corporate system to access the application without the required enterprise approval and addendum.

### Minimum application-specific requirements

Because this master standard prohibits external-system access, the application-specific requirements are intentionally concise. Each application must implement the following sensible minimum:

1.  Accept access only through approved corporate paths. Interactive access must originate from a corporately managed Microsoft Windows EUC device connected directly to the corporate network or connected remotely through the approved corporate VPN. The application must not provide an Internet-facing, public, consumer or supplier-managed access path.

2.  Do not treat corporate credentials as sufficient on an external device. A valid corporate username, password, token or MFA event must not by itself allow an unmanaged or non-corporate system to access the application. Device and network-path restrictions must remain effective alongside application authentication and authorisation.

3.  Do not design for processing or storage on external systems. Application functions must not require or encourage users to download restricted information to personal devices, personal email, consumer storage, public collaboration services, unapproved supplier systems or other systems outside organisational control.

4.  Restrict export and transfer functions. Downloads, exports, printing, clipboard use, file transfer, email delivery and other information-release functions must follow the approved corporate information-flow and data-handling controls. The application must not include a direct connector to a personal or unapproved external service.

5.  Protect thick-client installations. Thick-client software must be packaged and installed through the corporate software-distribution process on managed Windows EUC devices. Installation packages, licence files, configuration and locally cached information must not be provided for use on personal, supplier-owned or unmanaged systems.

6.  Restrict supplier and support access. Suppliers and external support personnel must use a corporate identity, an approved corporate device and the standard corporate network or VPN path unless a separately approved support arrangement is documented in the Application Addendum. Direct supplier VPNs, vendor remote-control tools and supplier-owned administration devices are prohibited by default.

7.  Avoid dependence on uncontrolled security safeguards. The application must not rely on anti-malware, encryption, patching, logging, backup, deletion or physical protection provided solely by an external system that the organisation cannot verify and manage.

8.  Fail closed for unapproved access context where the context is available. If enterprise identity, VPN, proxy, device-compliance or network controls provide a trusted indication that the device or path is not approved, the application or its access tier must deny access rather than downgrade to an unrestricted mode.

9.  Record and investigate attempted non-standard access. Relevant attempts to reach the application through unapproved endpoints, device types, supplier paths or external transfer functions must be logged and referred to enterprise monitoring or incident management where technically supported.

10.  Confirm external-system restrictions during design and testing. Architecture review, access testing and penetration testing must confirm that the application has no unintended public route, alternate remote endpoint, unmanaged-device workflow or direct transfer to an unapproved external system.

### Proportionate implementation guidance

A small internal web application will normally inherit most AC-20 protection from the corporate network, VPN, identity and managed-device controls. Its principal obligations are to avoid creating an alternate endpoint, external connector or unmanaged download workflow and to continue enforcing normal application access controls. A thick-client application must remain installable only through corporate software distribution and usable only from a managed Windows EUC device. A multi-tier application should restrict all user and administration paths to approved corporate segments and should keep server-side integrations internal. The application does not need to build its own device-management platform, but it must not undermine or bypass the enterprise platform.

### Expected evidence and assessment artefacts

- Architecture and data-flow documentation showing only approved corporate access and transfer paths
- Cross-reference to enterprise corporate-device, Windows EUC, VPN, identity, network and DLP controls
- Application network and endpoint records showing no public or unapproved external access path
- Thick-client packaging and corporate software-distribution records, where applicable
- Application export, download, printing and information-transfer rules
- Supplier and support access records identifying device ownership, identity and approved connection method
- Test evidence showing that unmanaged or non-corporate device access is denied
- Logs and incident records for attempted use of unapproved devices, paths or external destinations
### Continuous monitoring and measures

- Application endpoints reachable from public, supplier or otherwise non-corporate networks
- Successful application sessions from unmanaged or non-corporate devices
- Supplier access using supplier-owned devices or unapproved remote-control mechanisms
- Application connectors, exports or transfer functions targeting unapproved external services
- Thick-client packages installed outside the corporate software-distribution process
- Restricted information detected in personal email, consumer storage or unmanaged media
- Exceptions that have passed their approved review or expiry date
- Age and outcome of the latest external-system restriction test
### Relationship with related controls

AC-20 determines whether systems outside organisational control may be used to access or handle organisational information. AC-17 governs the approved remote-access path; a remote corporate EUC device using the approved VPN is not an external system for this standard. AC-19 and related mobile-device controls govern managed mobile devices where applicable, while AC-04 controls information flows, SC-07 protects boundaries, MP-family controls govern media, SC-28 protects information at rest, and AU-02 and SI-04 provide logging and monitoring. An interconnected organisational or partner system may also require separate interconnection and boundary controls; AC-20 specifically focuses on the use of systems that are not sufficiently controlled by the organisation.

### Addendum trigger

> **Template note:** Use an addendum when the application must be accessed from a personally owned, supplier-owned, public, unmanaged or otherwise non-corporate system; requires BYOD or mobile-device access not covered by the corporate Windows EUC standard; must transfer, process or store restricted information in an external system; requires a supplier VPN, vendor remote-control tool, non-corporate administration device or direct third-party connection; cannot enforce the corporate device or network-path restriction; requires thick-client installation outside corporate software distribution; or depends on security safeguards that the organisation cannot verify. The addendum must identify the external system, owner, user group, information, access path and purpose; the standard approach; implemented approach; contractual and technical safeguards; risk; compensating controls; monitoring; approval; and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## IA-05 - Authenticator Management

### Control objective and responsibility model

IA-05 requires authenticators to be selected, issued, bound to the correct identity, protected, changed, replaced, revoked and disposed of through controlled lifecycle processes. Authenticators include passwords and passphrases, cryptographic keys, certificates, hardware or software tokens, one-time-password devices, biometric activation factors, recovery codes, API credentials and other secrets used to prove an identity. The control also requires initial authenticator content to be defined, default authenticators to be changed before use, authenticator strength to reflect risk, loss or compromise to be reported and acted upon, and authenticators to be protected from unauthorised disclosure and modification. In this corporate model, the enterprise manages authenticators for workforce identities, Microsoft Windows sign-in, corporate VPN, MFA, privileged access, enterprise PKI and centrally provided machine identities. Each application remains responsible for avoiding unnecessary application-local authenticators and for securely managing any application-owned service credentials, certificates, keys, tokens, emergency credentials or unavoidable local passwords. This implementation reflects IA-05 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A, with current authenticator-lifecycle and password guidance informed by NIST SP 800-63B-4 [1][2][6].

### Inherited enterprise authenticator-management controls

The following capabilities are inherited when the application uses approved corporate identity, EUC, VPN, privileged-access, PKI and secrets-management services. They are implemented and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Corporate workforce authenticators. Enterprise identity services issue, bind, reset, recover, suspend and revoke the authenticators associated with unique corporate accounts using approved identity-verification, service-desk and joiner-mover-leaver processes.
- Password and passphrase controls. Where passwords are used, enterprise identity services define minimum length and permitted content, screen new or changed values against known compromised, commonly used and context-specific values, protect stored verifiers using approved salted and computationally resistant mechanisms, and apply throttling or lockout protections. Routine periodic password change is not required solely because time has elapsed unless corporate policy, compromise evidence or another defined risk condition requires it.
- Multi-factor authenticators. Enterprise identity and VPN services enrol, bind, activate, replace and revoke approved MFA authenticators. Phishing-resistant cryptographic authenticators are preferred for privileged and higher-risk use where supported by corporate technology and policy.
- Microsoft Windows EUC authenticators. Hardened corporate Windows devices use approved sign-in, credential-protection, screen-lock and device-identity mechanisms. Local account and credential behaviour is controlled through the enterprise Windows baseline and device-management service.
- Corporate VPN authenticators. The enterprise VPN uses corporate account authentication, MFA, device certificates or other approved device evidence, and device-compliance checks. The application does not issue or manage VPN credentials.
- Privileged authenticators. Enterprise PAM controls the issue, checkout, rotation, session use, emergency access and revocation of privileged credentials for infrastructure and, where integrated, application administration. Privileged credentials are not used for routine non-privileged activity.
- Enterprise PKI and cryptographic credentials. Corporate certificate and key-management services govern certificate requests, approval, issuance, private-key protection, renewal, revocation, trust anchors and cryptographic module requirements for approved user, device and service use.
- Managed service identities and secrets. Where centrally provided, managed service accounts, workload identities, vaults and secrets-management services generate, store, retrieve, rotate and revoke non-person credentials without exposing reusable secret values to ordinary users or source repositories.
- Monitoring and compromise response. Enterprise identity, MFA, VPN, PAM, PKI and security-monitoring services record enrolment, reset, recovery, failure, revocation and suspicious use, and provide processes for reporting lost, stolen, disclosed or suspected-compromised authenticators.
The application owner must identify the inherited authenticator services used by the application. The application must not maintain a separate user password database, implement its own MFA lifecycle or copy enterprise credentials into application storage where the approved corporate identity service can meet the need.

### Minimum application-specific authenticator-management requirements

Each application must implement the following sensible minimum for authenticators and secrets that the application team owns or controls:

1.  Avoid application-local user authenticators. Interactive users must normally authenticate through the approved corporate identity service. The application must not collect, store or verify a separate user password, MFA secret or recovery code unless a legitimate requirement cannot be met by the enterprise service and the exception is approved in the Application Addendum.

2.  Inventory application-owned authenticators. Maintain a controlled record of service-account credentials, API keys, certificates, private keys, signing keys, database credentials, integration tokens, encryption keys, emergency credentials and any unavoidable local user authenticators. Record the purpose, owning component, environment, accountable owner, storage mechanism, permitted users or processes, rotation or expiry condition and revocation route. Secret values themselves must not appear in the inventory.

3.  Use approved generation and initialisation. Authenticators must be generated with approved random or cryptographic mechanisms and sufficient strength for their use. Default, vendor-supplied, sample, shared or installation credentials must be changed, disabled or replaced before production use. Temporary initial credentials must expire promptly or require immediate replacement at first use.

4.  Bind authenticators to a defined identity and purpose. Each authenticator must be associated with a named human identity or a uniquely governed service, process, device or component identity. A credential must not normally be shared across unrelated applications, tiers, suppliers or development, test and production environments.

5.  Protect authenticators in storage and use. Reusable secrets must be held in the approved enterprise vault, managed identity service, protected certificate store, operating-system credential facility or equivalent approved mechanism. They must not be embedded in source code, scripts, deployment packages, container images, ordinary configuration files, documentation, tickets, logs or monitoring output.

6.  Restrict retrieval and exposure. Applications and deployment tools should retrieve secrets at run time using dedicated, least-privileged identities. Human viewing or export of secret values must be limited to exceptional authorised need and must be logged where the supporting service provides that capability.

7.  Rotate or replace authenticators on risk and lifecycle events. Replace or revoke an authenticator when it is suspected or known to be disclosed, when an authorised holder leaves or changes duties, when ownership changes, when a supplier relationship ends, after unauthorised access, before expiry, after certain recovery or emergency uses, or when the cryptographic method or component is no longer approved. Fixed rotation intervals may also be used where required by the authenticator type, supplier, cryptoperiod or corporate policy.

8.  Provide secure recovery and emergency access. Recovery must verify the requesting identity through an approved process and must not rely solely on knowledge-based questions or information easily obtained about the user. Emergency credentials must be strongly protected, narrowly privileged, monitored, tested, and changed or re-sealed promptly after use.

9.  Revoke and remove authenticators completely. Disabling an application account is not sufficient where a certificate, token, API key, cached credential or service secret can continue to operate independently. All associated authenticators and active sessions must be revoked or rendered unusable when access or the technical identity is withdrawn.

10.  Validate certificates, tokens and cryptographic credentials. Application components must verify certificate chains, names or intended identities, validity periods, revocation status where applicable, token issuer and audience, signature and other required properties. Expired, revoked, untrusted or incorrectly scoped authenticators must be rejected.

11.  Protect password verifiers where a local password is unavoidable. The application must never store a recoverable plaintext password. Passwords must be compared using an approved salted, adaptive, computationally resistant password-hashing mechanism with parameters maintained in accordance with current corporate and NIST guidance. Password hints, security questions and emailing of passwords are prohibited.

12.  Log authenticator-management activity safely. Record creation, enrolment, issue, reset, recovery, rotation, expiry, revocation, failed validation, emergency use and unauthorised retrieval attempts with the acting identity, affected non-secret identifier, action, outcome and time. Logs must never contain passwords, complete tokens, private keys, recovery codes or other reusable secret material.

### Proportionate implementation guidance

A small internal application using corporate single sign-on may have no user authenticators of its own and only one or two service identities stored in the enterprise secrets service. A thick-client application should use the corporate Windows and identity context and must not embed a common application password or reusable API key in the installed package. A multi-tier application should normally use separate workload identities per tier and environment, short-lived tokens or managed identities where available, certificate-based authentication for appropriate service connections, and automated secret rotation. Complexity should be kept proportionate: the preferred design is fewer long-lived secrets, not a larger local credential-management system.

### Expected evidence and assessment artefacts

- Cross-reference to enterprise identity, password, MFA, Windows EUC, VPN, PAM, PKI and secrets-management controls
- Application-owned authenticator and secret inventory excluding actual secret values
- Vault, managed-identity, certificate-store or protected credential configuration
- Evidence that default and installation credentials were changed or disabled before production use
- Service-identity, certificate, token and key issuance, approval, renewal, rotation and revocation records
- Source and configuration scanning results showing no embedded secrets
- Password-verifier design and parameters where an unavoidable local password store exists
- Authenticator recovery, emergency-use and compromise-response procedures and test evidence
- Audit events for authenticator lifecycle and failed or revoked authenticator use
### Continuous monitoring and measures

- Application-owned authenticators without a recorded owner, purpose or revocation route
- Secrets discovered in source code, packages, scripts, configuration, tickets or logs
- Default, shared or installation credentials remaining active in production
- Expired, revoked, untrusted or weak certificates, keys and tokens still accepted
- Long-lived service credentials not rotated or reviewed within their defined lifecycle
- Authenticators shared across applications, tiers or environments without an approved exception
- Disabled accounts or retired services with still-valid tokens, certificates or secrets
- Emergency authenticator use not followed by prompt review and replacement
- Age and outcome of the latest authenticator compromise and recovery test
### Relationship with related controls

IA-05 governs the lifecycle and protection of the authenticators used to prove identity. IA-02 governs the identification and authentication transaction itself. AC-02 governs account lifecycle and eligibility; AC-06 limits the privilege associated with the identity; AC-17 governs VPN authentication and the remote-access path; SC-12 and SC-13 govern cryptographic key establishment and cryptographic protection; SI-07 protects software and information integrity; and AU-02 and SI-04 provide logging and monitoring of authenticator activity. Authenticator management does not replace account disablement, and account disablement does not replace revocation of independently usable authenticators.

### Addendum trigger

> **Template note:** Use an addendum when the application requires a local user password or MFA store; cannot use the approved corporate identity, PAM, PKI or secrets-management service; requires embedded, shared, vendor-known or non-rotatable credentials; uses an authenticator with insufficient strength or no reliable revocation method; cannot change a default credential; requires the same service credential across unrelated applications or environments; cannot validate certificate or token status correctly; stores recoverable passwords; uses knowledge-based recovery; or cannot revoke all authenticators when an account or service is disabled. The addendum must identify the authenticator, identity, component and purpose; the standard approach; implemented approach; rationale; risk; compensating controls; storage and monitoring arrangements; replacement or retirement plan; owner; approval; and review or expiry date.

## AU-02 - Event Logging

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

### Standard implementation

The system defines and implements a logging matrix that identifies auditable events, content, sources, severity, retention, review, and protection. At minimum, logs cover authentication, authorisation failures, account and privilege changes, administrative actions, configuration and code changes, data access/export, security-control events, interface transactions, integrity events, and application errors. Records include reliable timestamps, actor, source, target, action, outcome, correlation/session identifiers, and relevant context without unnecessarily recording sensitive content.

### Architecture-specific application

- Thick clients log security-relevant local events and forward them when connected.
- Web/API layers use structured, correlation-enabled logs across tiers.
- Databases log privileged actions and high-risk data access.
- Internal services enable operating-system, application, identity, network, database and storage logs as supported.
### Expected evidence and assessment artefacts

- Logging requirements/matrix
- Sample logs and field validation
- Retention and access configuration
- Log-source health report
- Audit review records
### Continuous monitoring and measures

- Required event coverage
- Log ingestion delay/drop rate
- Unparsed events
- Audit review completion
### Addendum trigger

> **Template note:** Use an addendum when logging sensitive content could create privacy/security risk, product logs are limited, or retention differs.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## SC-28 - Protection of Information at Rest

### Control objective and responsibility model

SC-28 requires the confidentiality and integrity of defined information at rest to be protected. Information is at rest whenever it is stored rather than actively transmitted, including in databases, files, message stores, application repositories, backups, logs, temporary files, caches, search indexes, exports and locally stored thick-client data. Protection at rest is broader than encryption alone. It also includes access control, segregation, integrity protection, secure configuration, physical and media safeguards, backup protection, retention, secure deletion and management of the cryptographic keys that make encrypted information recoverable. The selected protection must reflect the sensitivity, storage location, exposure and operational use of the information. In this corporate model, the enterprise provides encrypted and access-controlled Microsoft Windows EUC devices, enterprise storage and backup platforms, hosting and physical controls, and central key-management services. Each application remains responsible for identifying every place its information is stored, minimising stored copies, applying application-level access and segregation, using approved storage services, and protecting application-created files, caches, exports, logs, database content and temporary information. This implementation reflects SC-28 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A [1][2].

### Inherited enterprise protection for information at rest

The following capabilities are inherited when the application uses approved corporate EUC, hosting, storage, database, backup, cryptographic and physical-security services. They are implemented and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Corporate Microsoft Windows EUC protection. Hardened corporate EUC devices use centrally managed full-volume or device encryption, secure boot and platform protections where supported, Windows access controls, screen lock, endpoint protection, patching, application control and remote device-management capabilities. Recovery information is protected through the approved enterprise process.
- Server and virtualisation storage protection. Enterprise hosting services protect physical and virtual server storage through controlled administration, access restrictions, approved encryption where required, storage segregation, secure configuration, platform monitoring and data-centre physical safeguards.
- Managed database, file, messaging and platform storage. Where centrally provided, database engines, file services, messaging systems, middleware and other managed platforms apply approved access controls, storage configuration, encryption capabilities, integrity mechanisms, administrative logging and backup integration.
- Enterprise backup and recovery protection. Corporate backup services control backup creation, storage, replication, access, encryption where required, retention, restoration, media handling and secure disposal. Backup administrators do not automatically receive application-level authority to use the restored information.
- Enterprise cryptographic key management. Approved PKI, key-management, hardware-security-module or secrets-management services govern generation, protection, access, rotation, recovery, revocation and destruction of cryptographic keys used by enterprise storage and approved application encryption.
- Physical and media safeguards. Data centres, communications rooms, enterprise storage media and authorised removable media are protected through corporate physical-access, environmental, transport, sanitisation and disposal controls.
- Enterprise information-protection and monitoring services. Where provided, DLP, endpoint monitoring, file classification, malware protection, configuration monitoring and security operations detect selected unauthorised storage, copying, access or alteration of restricted information.
The application owner must identify the inherited storage, backup, encryption and key-management services used by the application and must not create a separate unmanaged storage or cryptographic service where an approved enterprise service can meet the need.

### Minimum application-specific protection requirements

Each application must implement the following sensible minimum for information stores and copies that the application team owns, configures or creates:

1.  Identify all information-at-rest locations. Maintain a concise data-at-rest register or equivalent part of the data-flow documentation covering production and relevant non-production databases, file shares, message stores, application servers, thick-client storage, caches, indexes, logs, temporary files, exports, reports, attachments, backups and recovery copies. Record the information type, sensitivity, owner, location, purpose, retention and inherited protection.

2.  Use approved corporate storage only. Restricted information must be stored only in approved corporate databases, file services, managed application storage or encrypted corporate EUC locations. Personal folders, consumer storage, unapproved local drives, supplier systems and other external storage are prohibited under this master standard.

3.  Minimise copies and persistence. Store only the information needed for the approved function and period. Avoid duplicate datasets, uncontrolled extracts, diagnostic copies, local working files and long-lived caches. Temporary information must be removed promptly when processing completes or the defined recovery period expires.

4.  Enforce application-level access and segregation. Database, file, object, record and application permissions must restrict stored information to authorised users, roles and services. Where the application separates projects, cases, business units, sensitivity levels or other populations, that segregation must remain effective in the underlying store and must not rely solely on hiding functions in the user interface.

5.  Encrypt stored information where required by classification, contract, law, risk or corporate policy. Use approved enterprise storage encryption or application-level encryption appropriate to the threat. Application-level or field-level encryption is required only where inherited volume, database or platform encryption does not adequately address the identified risk, such as privileged-platform exposure, selective data separation or highly sensitive values.

6.  Manage application encryption keys separately from encrypted information. Application-owned keys must use the approved enterprise key-management or secrets service, have a named owner and defined lifecycle, and be restricted to the authorised application identity. Keys must not be embedded in source code, packages, ordinary configuration, database tables beside the ciphertext or user-accessible documentation.

7.  Protect locally stored thick-client information. Thick clients on corporate Windows EUC devices must minimise local data and use approved user or application storage locations protected by Windows access control and device encryption. Credentials, tokens, restricted records and sensitive cache content must not be stored in plaintext or in shared locations. Local data must be cleared or expire according to the defined retention and session model.

8.  Protect logs, exports, reports and attachments. Security and business logs must avoid unnecessary restricted content and be access-controlled against alteration or unauthorised viewing. Exports, generated reports, uploaded attachments and downloaded files must inherit or receive suitable classification, access, encryption, retention and disposal controls rather than becoming ungoverned copies.

9.  Protect non-production and support copies. Restricted production data must not be copied into development, test, training or support environments unless specifically authorised, minimised and protected to an equivalent level. Synthetic, masked or anonymised data should be used where it meets the purpose. Troubleshooting captures and database extracts must be time-limited and securely deleted after use.

10.  Preserve integrity of important stored information. Use database constraints, transactional controls, approved update paths, audit history, checksums, signatures, immutability, versioning or reconciliation where unauthorised or accidental alteration would create material harm. The mechanism must be proportionate; not every ordinary record requires cryptographic signing.

11.  Protect backup and restoration behaviour. Confirm that application information is included in the approved backup and recovery service at the required scope and frequency, that restoration preserves access and security controls, and that restored copies do not remain in temporary or less-protected locations. Application-owned encryption keys required for recovery must be recoverable through the approved key-management process.

12.  Apply retention and secure deletion. Information must be retained only for the authorised business, legal, contractual, records or security period. Deletion, disposal and decommissioning must cover primary data, indexes, temporary files, local caches, exports and application-controlled replicas, with enterprise storage and backup limitations recorded where immediate physical erasure is not technically possible.

13.  Fail safely when at-rest protection is unavailable. The application must not silently store restricted information in plaintext, an unapproved location or an incorrectly permissioned store because encryption, key management or the approved storage service is unavailable. It must stop, queue securely, reject the operation or invoke a documented recovery process appropriate to the business risk.

14.  Test protection and recovery. Before production use and after material storage, encryption or key-management changes, verify access denial, authorised retrieval, encryption status, key availability, backup restoration, retention handling and secure clean-up. Tests must demonstrate that information is protected both during normal operation and following recovery.

### Proportionate implementation guidance

A small internal web application may rely on enterprise database encryption, access control and backup, while maintaining a short data-at-rest register and ensuring that exports, logs and temporary files are controlled. A thick-client application should keep local storage to the minimum and rely on hardened Windows EUC device encryption, protected application storage and server-side records; it should not create a separate local database of restricted information without a documented need. A complex multi-tier application may require separate database roles, encrypted stores, key-managed sensitive fields, protected message persistence, immutable audit records and automated retention. Encryption should address an identified threat and should not be used as a substitute for least privilege, sound access enforcement, secure deletion or backup governance.

### Expected evidence and assessment artefacts

- Application data-at-rest register or storage map, including temporary and non-production locations
- Information classification, ownership, retention and approved-storage decisions
- Database, file, object and application permission configuration
- Storage and application-level encryption configuration and cryptographic design where applicable
- Application key inventory and cross-reference to enterprise key-management evidence
- Thick-client local-storage, cache and clean-up design and test evidence where applicable
- Backup scope, encryption, retention and restoration test records
- Export, report, attachment, log and non-production data-handling controls
- Secure deletion, decommissioning and media-sanitisation records where applicable
- Cross-reference to inherited EUC, hosting, database, storage, backup, physical and DLP controls
### Continuous monitoring and measures

- Restricted information stores or copies absent from the approved data-at-rest register
- Restricted information stored in unapproved or unencrypted locations
- Application encryption keys without a current owner, lifecycle or approved key store
- Plaintext credentials, tokens or restricted cache content on corporate EUC devices or servers
- Excessive, dormant or unauthorised access to databases, files, logs, exports or backups
- Production data present in non-production environments without current approval
- Temporary files, exports, troubleshooting copies or retired data retained beyond the defined period
- Backup or restoration tests that do not preserve required security controls
- Age and outcome of the latest storage, encryption and recovery control review
### Relationship with related controls

SC-28 protects information while stored. AC-03 and AC-06 restrict who and what may access the stored information; AC-04 controls where it may flow; IA-05, SC-12 and SC-13 govern authenticators, cryptographic keys and approved cryptography; CM-06 defines secure storage settings; SI-07 protects integrity; SI-12 governs information management and retention; media-protection controls govern storage media; and AU-02 and SI-04 provide logging and monitoring. Full-device or volume encryption protects against loss of storage media or an offline device, but it does not replace application access controls when the system is running and the storage is mounted.

### Addendum trigger

> **Template note:** Use an addendum when restricted information must be stored on an unapproved, external, supplier-managed or unencrypted system; a thick client requires substantial or persistent local restricted data; an application cannot use approved enterprise storage, backup or key management; required encryption is unsupported; encryption keys must be embedded, shared or stored with the encrypted data; production data must be used in non-production without equivalent safeguards; information cannot be deleted or retained according to the standard schedule; backup copies cannot be encrypted, access-controlled or restored securely; or the application cannot identify all locations in which restricted information persists. The addendum must identify the information, storage location, owner, purpose and duration; the standard approach; implemented approach; rationale; risk; compensating controls; key, backup, retention and deletion arrangements; monitoring; approval; and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## SI-12 - Information Management and Retention

### Control objective and responsibility model

SI-12 requires information to be managed and retained within the system and organisation in accordance with applicable law, regulation, contract, policy, records schedules and operational requirements. The control covers the complete information lifecycle: creation or collection, classification, use, storage, copying, retention, legal or investigation hold, archival, transfer, deletion and disposal. It applies not only to primary business records, but also to logs, messages, attachments, reports, exports, temporary files, caches, backups, test data and other copies. Effective retention management means keeping information for as long as it is legitimately required and no longer, while preserving records that must remain available, complete and trustworthy. In this corporate model, the enterprise provides records-management policy, legal and privacy governance, approved retention schedules, central storage and backup lifecycle controls, audit-log retention, physical media disposal and enterprise sanitisation services. Each application remains responsible for identifying its information types, mapping them to approved retention requirements, implementing lifecycle rules within application-controlled stores, preventing unauthorised destruction, responding to holds, and removing information from application-owned locations when disposal is authorised. This implementation reflects SI-12 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A. Disposal and sanitisation are supported by NIST SP 800-88 Revision 2 [1][2][11].

### Inherited enterprise information-management and retention controls

The following capabilities are inherited when the application uses approved corporate records, legal, privacy, storage, backup, logging, media and disposal services. They are implemented and evidenced by the relevant enterprise service owners rather than duplicated by each application team:

- Corporate information-governance framework. The organisation defines information classifications, records categories, data-owner responsibilities, approved retention schedules, privacy requirements, contractual obligations, minimum and maximum retention periods and authorised disposal routes.
- Legal, regulatory and investigation holds. Legal, records, privacy, security and investigation functions issue and release holds, define their scope and priority, and provide controlled instructions that suspend ordinary deletion where information must be preserved.
- Enterprise storage lifecycle controls. Approved database, file, messaging, archive and document-management services provide configurable retention, access, versioning, archival, deletion and disposal capabilities, with administrative activity restricted and logged.
- Enterprise backup lifecycle. Corporate backup services define backup frequency, retention, expiry, overwrite, media management and restoration controls. Backup retention is governed separately from the application's active record-retention rules and is not used as a permanent archive unless explicitly designed and approved for that purpose.
- Enterprise audit and security-log retention. SIEM, identity, VPN, Windows EUC, network, server, PAM and other shared services retain audit and security information for corporate investigation, monitoring, legal and assurance requirements.
- Corporate EUC and removable-media controls. Hardened Microsoft Windows EUC devices, managed user storage, removable-media restrictions, device return, reassignment and disposal processes reduce uncontrolled local retention and provide approved sanitisation or destruction.
- Media sanitisation and disposal. Enterprise asset, storage and physical-security services select and perform appropriate clearing, purging, destruction or cryptographic erasure based on the information sensitivity, media type and reuse or disposal decision.
- Enterprise privacy and data-subject processes. Where applicable, privacy functions coordinate lawful retention, correction, restriction, access and deletion obligations and determine when another legal or records requirement overrides ordinary deletion.
- Governance monitoring and exception management. Retention exceptions, overdue disposal, unsupported archives, hold failures and other lifecycle risks are recorded, escalated and tracked through enterprise governance processes.
The application owner must identify the inherited records, legal, privacy, storage, backup, logging and disposal services used by the application. The application team must not invent a conflicting retention period or use backup, log or local working storage as an ungoverned archive.

### Minimum application-specific information-management and retention requirements

Each application must implement the following sensible minimum for information and copies that the application team owns, configures or creates:

1.  Maintain an application information and retention register. Identify the principal business records, government or company-restricted information, personal data, transactions, attachments, messages, audit records, reports, exports, indexes, temporary files, caches and other application-created information. Record the owner, purpose, classification, authoritative source, storage location, approved retention rule and disposal trigger.

2.  Map each information type to an approved authority. Every retention period or event must be traceable to an approved corporate records schedule, law, regulation, contract, policy, business requirement or security need. Where several requirements apply, the application owner must obtain a documented decision on the governing rule rather than selecting an arbitrary period.

3.  Collect and retain only what is necessary. Application design must avoid collecting fields, attachments, logs, telemetry or history that are not required for an authorised purpose. Optional data must not become permanent merely because storage is available. Where the purpose ends, ordinary retention must also end unless another approved requirement applies.

4.  Define the authoritative record and control duplicates. Identify which application or repository holds the authoritative record. Reports, exports, caches, replicas, search indexes, message copies and support extracts must not silently acquire a longer lifecycle than the authoritative information. Duplicate copies must have an owner, purpose and disposal rule.

5.  Implement retention by record type or lifecycle event. Where application-controlled, retention must be based on the relevant record class and trigger, such as creation, case closure, contract expiry, final payment, account closure, supersession or another approved event. A single blanket period for all application information is acceptable only where it is authorised and appropriate.

6.  Prevent premature or unauthorised deletion. Ordinary users must not be able to delete, overwrite or alter protected records outside their approved business authority. Retention rules, record locks, immutable states, approval workflow, audit history or equivalent controls must be used where early destruction could create legal, regulatory, contractual, security or operational harm.

7.  Support legal, regulatory, audit and investigation holds. The application must be able to identify and preserve affected information, suspend ordinary deletion for the required scope, record who applied and released the hold, and resume the correct retention lifecycle after release. A hold must include relevant application-controlled copies and exports where they remain under organisational control.

8.  Separate active retention, archive and backup. The application must distinguish information kept for active business use, information placed in an approved archive, and technical backup copies retained for recovery. Backups must not be searched or restored merely to avoid implementing a proper records or archive function, and restored data must re-enter the applicable retention and hold controls.

9.  Control logs and monitoring information. Application logs must retain enough information for security, accountability, operations and investigation without unnecessarily duplicating restricted business content, credentials or personal data. Security-log retention must be aligned with AU-02, SI-04, IR-05 and the enterprise logging standard.

10.  Control thick-client and user-created copies. Locally stored data, offline caches, downloaded files, print outputs and temporary working copies on corporate Windows EUC devices must be minimised, protected and removed when their authorised purpose or retention period ends. The application must not rely solely on users remembering to delete copies where technical lifecycle controls are reasonably available.

11.  Control non-production, support and test information. Restricted production data must not be retained in development, test, training or support environments longer than the approved purpose requires. Synthetic, masked or anonymised information should be used where practicable. Troubleshooting extracts and diagnostic captures must have a named owner, expiry date and verified deletion.

12.  Dispose of information through approved mechanisms. When disposal is authorised and no hold applies, remove information from application-controlled active stores, indexes, caches, temporary locations, exports and replicas. Use the enterprise storage and media sanitisation process for underlying media. Deletion records must be sufficient to demonstrate what rule was applied, when disposal occurred, and whether any unavoidable backup residue remains.

13.  Handle backup and immutable-copy limitations transparently. Where information cannot be removed immediately from backups, write-once media, transaction journals or immutable stores, document the expected expiry and ensure that the residual copy is inaccessible for ordinary business use, remains protected, and is not reintroduced without applying the current deletion or hold state.

14.  Preserve readability and integrity for the required period. Long-lived records must remain retrievable, understandable and trustworthy despite application, schema, format, cryptographic key, software or platform change. Migration, archival format, metadata, checksum, signature, version and key-recovery arrangements must be planned where necessary.

15.  Review retention after material change. Reassess retention and disposal when the application adds a new information type, purpose, interface, report, export, analytics function, legal requirement, supplier component or storage location, or when the business process changes its authoritative record or closure event.

16.  Test retention, hold, deletion and recovery behaviour. Before production use and periodically thereafter, verify that records reach the correct retention state, holds prevent deletion, released holds resume the correct lifecycle, expired information is removed from application-controlled stores, restored data remains governed, and deletion activity produces suitable evidence.

### Proportionate implementation guidance

A small application may satisfy SI-12 with a concise information-and-retention register, a limited number of approved lifecycle rules, controlled deletion, an escalation route for legal holds and periodic review. A thick-client application should avoid persistent local records and should treat corporate EUC storage as a temporary working location unless it is an explicitly approved record store. A complex records, transaction or case application should normally automate record classification, closure events, holds, archival, deletion queues, disposal evidence and reconciliation of failed actions. The application should not create bespoke retention rules where an approved enterprise records service can provide the function.

### Expected evidence and assessment artefacts

- Application information and retention register, including copies, logs, temporary and non-production information
- Approved records schedules, legal, contractual, privacy, security and business authorities mapped to application rules
- Application retention, archival, hold, deletion and disposal configuration
- Role and permission design for record deletion, retention override and hold administration
- Samples showing creation, closure, retention, hold, release, archive and authorised disposal
- Records of local, export, support and non-production copy expiry and verified deletion
- Backup retention and restoration behaviour, including treatment of previously deleted or held information
- Long-term readability, migration, metadata, integrity and key-recovery arrangements where applicable
- Retention and disposal audit records, exception records and failed-deletion remediation
- Cross-reference to inherited records, legal, privacy, backup, logging, storage and media-sanitisation controls
### Continuous monitoring and measures

- Application information types or storage locations without an approved retention rule
- Records deleted before their authorised retention period or while subject to a hold
- Information retained beyond its authorised period without an approved reason
- Temporary, export, thick-client, support or non-production copies past their expiry date
- Failed, incomplete or unverified deletion and archival jobs
- Backup-restored records that do not retain their current deletion or hold status
- Legal or investigation holds not applied to all relevant application-controlled copies
- Long-lived records at risk of becoming unreadable or unverifiable
- Age and outcome of the latest retention, hold, disposal and recovery test
### Relationship with related controls

SI-12 governs how long information is kept, why it is kept and how it is disposed of. SC-28 protects it while stored; AC-03, AC-04 and AC-06 restrict access and flow; AU-02 defines security-relevant event logging and retention inputs; IR-05 may require incident evidence to be preserved; SI-07 protects integrity; media-protection controls govern media storage and sanitisation; and privacy controls govern purpose limitation and personal-data lifecycle. Backup retention does not by itself satisfy records retention, and deletion from the primary database does not complete disposal if uncontrolled application copies remain.

### Addendum trigger

> **Template note:** Use an addendum when the application cannot apply the approved retention schedule or legal hold; requires a blanket retention period that conflicts with record-specific rules; cannot identify or delete all application-controlled copies; relies on user-managed deletion for restricted information; must retain information beyond the authorised period; cannot prevent premature deletion; uses a supplier or legacy component with fixed or unverifiable retention; cannot preserve long-lived records in a readable and trustworthy form; cannot prevent deleted information from becoming active again after restoration; or cannot provide suitable disposal evidence. The addendum must identify the information type, owner, location and lifecycle rule; the standard approach; implemented approach; legal, contractual or operational rationale; risk; compensating controls; hold, backup, migration and disposal arrangements; monitoring; approval; and review or expiry date.

| **Field** | **Generic standard** |
| --- | --- |
| Implementation status | Implemented as the required enterprise pattern; application-specific deviations require an approved addendum and risk acceptance. |
| Control ownership | System Owner (accountable); Information System Security Officer (oversight); named technical control owner (operation); application owner (evidence). |
| Applicability | Applies to all in-boundary components and inherited/common services unless explicitly scoped out with documented rationale. |

## SA-11 - Developer Testing and Evaluation

### Control objective and responsibility model

SA-11 requires developers to plan and perform security and privacy testing and evaluation at an appropriate depth and coverage, document the results, correct identified weaknesses, and provide evidence that the software has been tested before release. Testing must be integrated into the development lifecycle rather than left until the end, and it must cover the software, configuration, interfaces and security functions that the developer controls. The term developer includes internal development teams, maintainers of scripts and configuration, package builders, integrators and suppliers that create or materially modify software for the organisation. In this corporate model, the enterprise provides approved development platforms, source and artefact repositories, build and release services, common security-analysis tools, test-environment controls and assurance governance. Each application remains responsible for defining a proportionate test strategy, testing its code and application-specific configuration, evaluating security functions and misuse cases, resolving findings, and retaining evidence that supports release approval. This implementation reflects SA-11 and the corresponding assessment objectives in NIST SP 800-53 and SP 800-53A, and aligns with the NIST Secure Software Development Framework in SP 800-218 and the technical testing guidance in SP 800-115 [1][2][4][10].

### Inherited enterprise developer-testing and evaluation capabilities

The following capabilities are inherited when the application uses approved corporate development, repository, build, test, release and assurance services. They are implemented and evidenced by the relevant enterprise service owners rather than recreated by each application team:

- Secure development lifecycle and governance. The organisation defines mandatory development, review, testing, release, defect-management and evidence requirements, together with risk-based assurance gates and approval roles.
- Protected source and artefact repositories. Enterprise repositories provide named access, change history, protected branches, review or approval controls, retention, backup and traceability between source, build outputs and releases.
- Approved build and release services. Corporate build agents, package repositories, software-distribution services and release pipelines provide controlled, attributable and repeatable mechanisms for creating and promoting thick-client packages, server-side artefacts, scripts and database migrations.
- Common security-analysis tooling. Where provided, enterprise services supply and maintain static analysis, software-composition analysis, secret detection, malware scanning, artefact scanning, container or package assessment and other automated checks, including current rules and vulnerability information.
- Managed test environments. Enterprise hosting, network, identity and data-management services provide approved development and test environments separated from production, with controlled connectivity, representative platform configuration, logging, backup where required and restrictions on production credentials and restricted information.
- Corporate Microsoft Windows EUC and packaging controls. Developer and tester EUC devices inherit the hardened Windows baseline, endpoint protection and approved tooling. Thick-client software is packaged, signed where required, and distributed through the enterprise software-distribution process.
- Independent assurance and specialist testing. Enterprise security or assurance functions provide or coordinate specialist code review, penetration testing, cryptographic review, architecture review and other independent evaluation where required by risk, policy or significant change.
- Central defect, vulnerability and risk management. Findings are recorded, assigned, prioritised, tracked, accepted or closed through approved defect, vulnerability, risk or POA&M processes, with governance reporting for overdue or material weaknesses.
The application owner must identify the inherited development and assurance services used by the application. The application team must not bypass repository, build, test, signing or release controls by using personal repositories, unmanaged build hosts, unapproved tools or manually substituted production artefacts.

### Minimum application-specific developer testing and evaluation requirements

Each application must implement the following sensible minimum for software, configuration and interfaces that the application team develops, customises, packages or materially maintains:

1.  Maintain a proportionate security test strategy. Define the software components, security functions, trust boundaries, data flows, roles, interfaces, test methods, environments, responsibilities, evidence and release criteria. The strategy may be concise, but it must reflect the application's architecture, information sensitivity, business impact, complexity and rate of change.

2.  Derive tests from security requirements and misuse cases. Translate applicable controls, threat scenarios, abuse cases, previous findings and design assumptions into testable conditions. Include expected authorised use and credible attempts to misuse, bypass or subvert authentication, authorisation, information flow, input validation, logging, integrity, retention and other application security functions.

3.  Perform automated code and dependency analysis where applicable. Organisation-developed or materially modified code must receive proportionate static analysis, software-composition or dependency analysis and secret detection. Results must be reviewed by personnel able to validate findings and understand the code and application context.

4.  Perform developer review of security-relevant changes. Code, scripts, deployment definitions, database migrations and security-relevant configuration must receive peer review or another independent technical review before production promotion. Review must examine both correctness and security impact, not merely coding style.

5.  Test security functions and access boundaries. Verify authentication integration, session handling, role and permission enforcement, least privilege, separation of duties, privileged functions, service identities, data segregation and failure behaviour. Tests must include negative cases showing that unauthorised actions are denied.

6.  Test information handling and application interfaces. Exercise input validation, output handling, file and attachment processing, APIs, messages, batch interfaces, data imports and exports, error handling, concurrency and replay conditions as applicable. Server-side controls must be tested independently of thick-client or browser-side validation.

7.  Test secure configuration and deployment. Confirm that production-intended configuration uses secure defaults, disables non-essential functions, protects secrets, enables required logging, uses approved endpoints and certificates, and can be deployed repeatably from controlled artefacts. Test installation, update, rollback and removal of thick-client packages where applicable.

8.  Use representative but protected test data. Test data must cover relevant boundary, error and business scenarios without unnecessarily using live restricted information. Production data may be used only when specifically authorised, minimised and protected to an equivalent level; synthetic, masked or anonymised information should be used where practical.

9.  Test in an environment representative of production. The test environment must reproduce the material operating system, runtime, middleware, identity integration, database behaviour, network path and security settings needed to draw a reliable conclusion. Differences from production that could affect the result must be documented and addressed.

10.  Define objective release criteria. A release must not be approved solely because testing completed. The application must define which tests must pass, which severities block release, what evidence is required, and who may approve an exception. Known weaknesses accepted for release must be recorded with rationale, compensating controls, owner and review or expiry date.

11.  Correct findings and perform regression testing. Confirmed weaknesses must be corrected according to risk and retested. Regression testing must demonstrate that the correction works and that existing security and business functions remain effective. Repeated findings should trigger root-cause analysis and improvement to design, coding standards, tooling or test coverage.

12.  Preserve traceable test evidence. Retain the tested release or commit, environment, tool and rule versions, test cases, inputs, results, reviewer decisions, identified weaknesses, corrections, retest outcomes and final release decision. Evidence must be sufficient for an assessor to understand the scope, depth, limitations and result.

13.  Evaluate supplier-developed and commercial software proportionately. Obtain available supplier security-test evidence, vulnerability history, secure-development attestations, component or dependency information and remediation commitments. The application team must still test organisation-controlled configuration, integration, roles, data flows and deployment; supplier claims do not replace local evaluation.

14.  Reassess after material change. Repeat affected testing after significant code, dependency, architecture, authentication, authorisation, interface, data model, platform or security-configuration change. The scope may be targeted where change-impact analysis shows that unaffected controls remain valid.

### Proportionate implementation guidance

A small configuration-led or commercially supplied application may use supplier evidence, dependency and package assessment, configuration review, access-control tests, interface tests and controlled user-acceptance security scenarios. A small internally developed application should normally add peer review, static analysis, secret detection, dependency analysis and automated negative tests. A thick-client application must test both the installed Microsoft Windows client and the receiving internal services, including installation, updates, local storage, privilege requirements and server-side revalidation. A complex multi-tier application should normally automate security checks in the pipeline, maintain reusable security regression tests and supplement developer testing with independent penetration or specialist review. Testing depth should be driven by risk and change, not by application size alone.

### Expected evidence and assessment artefacts

- Application security test strategy, plan or matrix linked to requirements and architecture
- Threat, misuse or abuse cases and associated positive and negative security tests
- Peer-review records for code, scripts, configuration and database changes
- Static-analysis, dependency-analysis, secret-detection and artefact-scan results where applicable
- Functional security-test results for authentication, authorisation, input, flow, logging and failure behaviour
- Thick-client installation, update, rollback, local-storage and service-interaction test evidence where applicable
- Test-environment description and documented differences from production
- Defect, vulnerability, exception, correction and regression-retest records
- Release-gate evidence showing the tested artefact and approving authority
- Supplier security evidence and local integration or configuration evaluation where applicable
- Cross-reference to inherited repositories, build, packaging, test environment, analysis tooling and assurance controls
### Continuous monitoring and measures

- Production releases without a current security test plan or traceable test evidence
- Security-relevant changes merged or released without required independent review
- Critical or high developer-test findings open at release without approved risk treatment
- Application components or interfaces omitted from testing without a documented rationale
- Automated security checks disabled, bypassed or materially out of date
- Test environments whose material differences from production are not documented
- Findings closed without correction verification and security regression testing
- Repeated weakness categories indicating inadequate root-cause correction or test coverage
- Age and outcome of the latest application security test strategy review
### Relationship with related controls

SA-11 provides developer-led and development-lifecycle security testing before release. RA-05 supplies ongoing vulnerability and dependency monitoring; CA-08 provides deeper independent adversarial penetration testing; SI-02 governs correction of flaws; SI-10 addresses input validation; SI-07 protects software and information integrity; CM-02, CM-05 and CM-06 define and protect the approved configuration; AC-03 and AC-06 govern access enforcement and least privilege; and CA-07 tracks continuing effectiveness. Developer testing does not replace independent assessment or penetration testing, and those activities do not replace routine developer testing and regression.

### Addendum trigger

> **Template note:** Use an addendum when source code, build definitions, supplier evidence or test access are unavailable; a legacy or supplier-controlled product cannot support applicable automated or manual testing; security-relevant changes cannot receive independent review; the test environment cannot represent production sufficiently; live restricted data is required for testing; a mandatory test or release criterion must be waived; a known material weakness must be released before correction; test evidence cannot be retained; or a component cannot be retested after remediation. The addendum must identify the affected component, release, test or evidence limitation; the standard approach; implemented approach; rationale; risk; compensating controls; alternative assurance; remediation or replacement plan; owner; approval; and review or expiry date.

## 5.1 Secure architecture and engineering

- Threat modelling is performed at initial design and major change, covering trust boundaries, privileged paths, data flows, abuse cases, dependencies, and recovery.
- Production, test, development, and management environments are separated. Restricted production data is not used in lower environments without approval and protection.
- Availability and resilience requirements define redundancy, backup, recovery time and point objectives, dependency failure behaviour, and tested restoration.
- External dependencies and suppliers are assessed for security, privacy, support, incident notification, data location, subcontractors, and exit/portability.
## 5.2 Change and release management

- All changes are traceable to approved requests, reviewed for security impact, tested, approved, deployed through controlled mechanisms, and verifiably completed.
- Changes to security-relevant configuration, access, logging, cryptography, interfaces, and data handling receive heightened review.
- Emergency changes are limited, logged, reviewed promptly, and followed by baseline updates and corrective actions.
## 5.3 Operational security

- Operations teams review dashboards and exceptions, respond to alerts, maintain supported versions, validate backups, and track risks to closure.
- Administrative actions use dedicated identities and managed workstations or jump hosts. Shared privileged credentials are prohibited except controlled break-glass cases.
- Security failures fail safely: authentication, authorisation, logging, integrity, and encryption failures do not silently permit insecure operation.
## 5.4 Privacy and restricted-data safeguards

- Privacy and data-protection reviews are completed when personal or regulated data is processed.
- Data collection, use, sharing, and retention are limited to authorised purposes. High-risk exports and bulk access are monitored and may require approval.
- Application logs, monitoring, and test data avoid unnecessary sensitive content and use masking or tokenization where feasible.
# 6. Application Addendum Requirements

Complete one separately controlled Application Addendum for every deployed application and for each materially distinct deployment. The addendum is attached to, but does not amend, this master standard and becomes part of the assurance or authorisation package. The master document must remain byte-for-byte controlled through the corporate document-management process; only the standard owner may issue a new version.

The approved Application Addendum template is issued as a separate editable document. It must carry the master standard identifier and version, a unique application identifier, ownership and approval details, and a complete cross-reference matrix.

- The addendum must state one of the following for every applicable master section or control: Conforms without deviation; Conforms with application-specific implementation detail; Inherited; Deviates under approved exception; Not applicable with approved rationale; or Deficient and tracked in POA&M/risk register.
- Application teams must not copy the master into a local document and edit it. They must not delete unwanted architecture patterns, rewrite controls, weaken mandatory language, or leave differences undocumented.
- Where a deployment is simpler than the reference architecture, the unused element is recorded as an omission in the addendum, even where the omission lowers risk.
- Where a deployment is more complex, every extra component, trust boundary, protocol, data flow and privileged path is recorded in the addendum and assessed against the same standard.
| **Field** | **Required content** |
| --- | --- |
| Application / deployment | Name, version, environment, owner, business service, identifier |
| Purpose and users | Business function, user populations, privileged roles, thick/thin/web access method and VPN use |
| Data | Categories, CUI registry categories if applicable, privacy/regulated data, markings, retention |
| Boundary and architecture | Diagram, zones, components, management paths, inherited services |
| Interconnections | Source/destination, data, protocol, authentication, encryption, agreement, owner |
| Control specialization | Product names, exact settings, organisation-defined parameters, evidence locations |
| Deviations | Control, generic baseline, actual implementation, reason, risk, compensating safeguards |
| Assessment | Test method, result, assessor, date, evidence, deficiencies |
| POA&M / risk acceptance | Gap, owner, milestone, target date, interim safeguard, approval |
| Approval and expiry | System owner, information owner, ISSO, authorizing official; review/expiration date |

## 6.1 Mandatory addendum contents

| **ID** | **Control** | **Standard** | **Specialized/deviating implementation** | **Reason and risk** | **Compensating safeguards** | **Owner / due / approval** |
| --- | --- | --- | --- | --- | --- | --- |
| DEV-001 | [ID] | [Generic baseline excerpt] | [Actual implementation] | [Legitimate constraint and residual risk] | [Controls and evidence] | [Name / date / authority] |

## 6.2 Deviation and omission rules

| **Connection** | **Direction** | **Information** | **Protocol/port** | **Identity/auth** | **Encryption** | **Boundary controls** | **Agreement/owner** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [Name] | In/Out/Bi | [Data classes] | [Exact] | [Method] | [Method] | [Firewall/gateway/DLP] | [ISA/MOU/contract] |

# 7. Assessment and Evidence Plan

Assessment follows NIST SP 800-53A concepts: examine documentation and records, interview responsible personnel, and test technical mechanisms. The assessor selects depth and coverage based on risk. Evidence must be attributable, current, protected, and reproducible.

| **Evidence domain** | **Representative artefacts** | **Minimum cadence** |
| --- | --- | --- |
| Identity/access | Role matrix, approvals, IAM/PAM reports, access tests | Quarterly; privileged monthly |
| Configuration/change | Baselines, compliance scans, change tickets, pipeline logs | Continuous/monthly and per change |
| Vulnerability/flaw | Scan reports, advisories, patch status, exceptions | Weekly/monthly and per release |
| Logging/monitoring | Logging matrix, source health, alerts, cases, metrics | Continuous; monthly review |
| Boundary/data flow | Diagrams, rules, gateway policies, flow approvals | Quarterly and per change |
| Integrity/malware | EDR, signing, provenance, integrity alerts | Continuous and per release |
| Incident response | Tickets, exercises, reports, corrective actions | Per incident; annual exercise |
| Developer testing | Threat models, SAST/DAST/SCA, reviews, release sign-off | Every release/build as applicable |
| Recovery/retention | Backup tests, restore results, deletion/hold records | Quarterly/annual and schedule-based |

# 8. Plans of Action and Milestones

Deficiencies are recorded in the authoritative POA&M or risk register. Each item includes the affected control, weakness, source, risk, affected assets/data, interim mitigation, owner, milestones, resources, target date, dependencies, validation method, and closure approval. High-risk overdue items are escalated to the System Owner and Authorizing Official.

| **ID** | **Control** | **Weakness / risk** | **Interim mitigation** | **Owner** | **Milestones / target** | **Status** |
| --- | --- | --- | --- | --- | --- | --- |
| POAM-001 | [ID] | [Deficiency and impact] | [Temporary safeguard] | [Name/role] | [Dates] | Open |

# 9. References

[1] NIST Special Publication 800-53, Revision 5, Security and Privacy Controls for Information Systems and Organisations, including Release 5.2.0 updates (2025).

[2] NIST Special Publication 800-53A, Revision 5, Assessing Security and Privacy Controls in Information Systems and Organisations, including Release 5.2.0 updates.

[3] NIST Special Publication 800-53B, Control Baselines for Information Systems and Organisations, Release 5.2.0 (baseline content unchanged in that release).

[4] NIST Special Publication 800-171, Revision 3, Protecting Controlled Unclassified Information in Nonfederal Systems and Organisations (2024).

[5] NIST Special Publication 800-171A, Revision 3, Assessing Security Requirements for Controlled Unclassified Information (2024).

[6] NIST Special Publication 800-37, Revision 2, Risk Management Framework for Information Systems and Organisations.

[7] NIST Special Publication 800-137, Information Security Continuous Monitoring for Federal Information Systems and Organisations.

[8] NIST Special Publication 800-128, Guide for Security-Focused Configuration Management of Information Systems.

[9] FIPS Publication 199, Standards for Security Categorization of Federal Information and Information Systems.

[10] NIST Cybersecurity and Privacy Reference Tool (CPRT) and SP 800-53 control catalogue datasets.

[11] NIST Special Publication 800-88, Revision 2, Guidelines for Media Sanitization (2025).

## 9.1 Research and currency note

This template was prepared against the NIST publications and update notices available as at 22 July 2026. Organisations should verify later releases before adoption. Bibliographic titles are shortened below so that the document remains consistently written in UK English.

# Appendix A - Control Responsibility Assignment

| **Control** | **Enterprise/common provider** | **Application team** | **Shared / notes** |
| --- | --- | --- | --- |
| SI-04 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| CM-06 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| AC-03 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| CM-02 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| AC-06 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| CM-07 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| CA-07 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| IR-05 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| SI-03 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| SC-07 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| AC-04 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| AC-02 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| SI-07 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| IA-02 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| AC-05 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| CM-05 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| RA-05 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| CM-08 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| SI-10 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| SI-02 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| AC-17 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| CA-08 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| AC-20 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| IA-05 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| AU-02 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| SC-28 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| SI-12 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |
| SA-11 | Policy, common tooling, monitoring, standards | Configuration, integration, evidence, exceptions | Final assignment in application addendum |

# Appendix B - Minimum Application Security Evidence Checklist

- ☐ Current system and data-flow diagrams
- ☐ Authoritative component/software/SBOM inventory
- ☐ FIPS 199 or equivalent impact categorization and data inventory
- ☐ User/role/privilege matrix and access reviews
- ☐ Configuration baseline and compliance results
- ☐ Change/release records and protected source/artefact repositories
- ☐ Vulnerability and patch reports with exception status
- ☐ Logging matrix, SIEM onboarding, monitoring health, and sample alerts
- ☐ Internal boundary rules, VPN access paths, segmentation and interconnection approvals
- ☐ Encryption/key management evidence
- ☐ Malware and integrity protection coverage
- ☐ Incident response contacts, procedures, and exercise/incident evidence
- ☐ Penetration test and developer security testing results
- ☐ Backup/restore test and retention/disposal evidence
- ☐ Current POA&M, risk acceptances, and approved addenda
