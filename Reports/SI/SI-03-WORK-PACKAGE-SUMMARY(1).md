# SI-03 Malicious Code Protection — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **SI-03-specific content**, implementing targeted malicious-code protection improvements where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already operates within the approved corporate environment and can consume enterprise malware-protection services;
- enterprise endpoint protection, EDR, malware-scanning platforms, SIEM, SOC, software-distribution protection and incident response are inherited;
- existing document templates, repositories, build/release processes and approval routes will be reused;
- application file handling, integrations, packages and dependencies are already identifiable from the existing architecture and SDLC artefacts;
- no major redesign of enterprise malware-protection platforms or extensive supplier redevelopment is required; and
- enterprise malware signatures, scanning-engine maintenance, endpoint controls and organisation-wide malicious-code response remain outside the application work package.

---

## A. SSP SI-03 Content

Update the existing SSP with a concise SI-03 implementation statement describing how the application prevents, detects, contains and supports removal of malicious code. Document the application-specific entry, processing and exit points; inherited enterprise protection services; permitted and restricted content; scanning and quarantine approach; handling of suspicious, unsupported or unscannable content; failure behaviour when scanning is unavailable; protection of packages, dependencies and execution paths; monitoring and escalation arrangements; review frequency; and any approved limitations or exceptions.

**Estimated effort: 6–10 hours**

---

## B. SyOps Malicious-Code Protection Content

Update the existing SyOps with operational procedures for handling potentially malicious or untrusted content. Include scanning and quarantine workflows, permitted content rules, scanner timeout and failure handling, user and support messaging, controlled release or disposal of quarantined content, operational response to detections, temporary restriction of affected functions, package or integration withdrawal, evidence handling, supplier escalation, recovery activities and escalation into the enterprise incident-response process.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Malicious-Code Protection Specification

Extend the existing software or security design to define the application's malicious-code protection architecture. Document upload, import, API, integration, messaging, preview, conversion, extraction, export and download paths; scanning points; trust transitions; staging and quarantine locations; file-type and active-content restrictions; parser isolation; thick-client and release-package controls; scripts, plugins and dependency handling; execution-path restrictions; scanner interfaces and result states; event generation; and safe behaviour when scanning or content inspection is unavailable.

**Estimated effort: 12–24 hours**

---

## D. Malicious-Code Protection Analysis, Integration and Implementation

Review the application against SI-03 requirements and implement any required improvements. Activities may include identifying all malicious-code entry and exit points, performing an application-specific threat assessment, integrating approved enterprise scanning services at relevant processing points, scanning content before trusted use, isolating untrusted or pending content, implementing explicit clean, malicious, suspicious, unsupported and scanner-failure states, restricting accepted file and active-content types, preventing bypass through browser, thick-client, API, batch, support and administrative paths, hardening preview and conversion services, preventing execution from upload or temporary locations, protecting thick-client installers, dependencies, plugins, build and release artefacts, and ensuring application-owned scanning integrations remain supported and current.

**Estimated effort: 24–68 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to demonstrate that malicious-code controls operate safely and cannot be bypassed. Testing should verify clean and blocked content, mismatched file types, encrypted or nested archives, scan invocation, rejection and quarantine, scanner timeout or unavailability, unsupported content, API and batch bypass attempts, quarantine access restrictions, parser and conversion failure behaviour, thick-client package verification, plugin controls, generated-file safety, event forwarding, alerting, user messaging, temporary-content clean-up and retesting following remediation. Approved harmless anti-malware test artefacts and failure simulations should be used rather than live malware.

**Estimated effort: 16–32 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for operating and troubleshooting the application's malicious-code controls. Include investigation of failed or delayed scans, quarantine handling, escalation of detections, scanner-service outages, repeated suspicious submissions, approved overrides where they exist, support for contaminated packages or integrations, evidence preservation, containment and remediation support, restoration of normal service, scanner-integration compatibility checks and management of unsupported content or supplier limitations.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release and operational acceptance process with SI-03-specific checks. Confirm that required scanner integrations are active, approved content restrictions and failure behaviours are configured, quarantine operates correctly, thick-client and application packages have been scanned and integrity-checked, dependencies and plugins are controlled, build and release artefacts come from approved sources, relevant detection and failure events reach central monitoring, prohibited execution or bypass paths are unavailable, and any accepted limitations or exceptions have been documented.

**Estimated effort: 8–16 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the SI-03 activities through the existing governance process. Activities include malicious-code protection gap analysis, stakeholder and security-service workshops, coordination with application support, build/release teams and suppliers, design assurance, evidence tracking, risk and exception management, alignment with related CM, RA, SA, AU, SI and IR controls, approval coordination and final compliance review. Existing governance forums and artefacts should be reused rather than creating additional project documentation.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP SI-03 content | **6–10 hours** |
| SyOps malicious-code protection content | **8–16 hours** |
| Software design and malicious-code protection specification | **12–24 hours** |
| Malicious-code protection analysis, integration and implementation | **24–68 hours** |
| Test documentation and evidence | **16–32 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **8–16 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **90–198 hours** |

## Planning interpretation

A mature application with limited file handling, established enterprise malware-scanning integration, controlled build and artefact repositories, no unnecessary scripting or plugin capability and existing security testing is likely to fall near the lower end of the estimate.

Applications with extensive upload or import functionality, archives, document conversion, active content, thick-client packages, custom plugins, numerous integrations, complex build dependencies, supplier-controlled components or inconsistent scanning across multiple application paths are more likely to fall toward the upper end.

The estimate excludes enterprise endpoint anti-malware and EDR operation, malware signature and engine maintenance, corporate email and web filtering, central sandbox and malware-analysis services, SIEM and SOC operations, enterprise software-distribution platform protection, corporate forensic capability and other inherited enterprise malicious-code protection responsibilities.
