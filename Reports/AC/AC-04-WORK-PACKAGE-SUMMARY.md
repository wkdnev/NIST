# AC-04 Information Flow Enforcement — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **AC-04-specific content**, implementing targeted application information-flow controls where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already has an established access-control model and documented architecture, interfaces and data flows;
- enterprise network segmentation, firewalls, managed file transfer, DLP, corporate identity, VPN, endpoint controls and central monitoring are inherited;
- existing document templates, approval routes, security testing and release processes will be reused;
- existing information-classification, data-handling, privacy and records-management policies are available to the application team;
- no major application redesign or wholesale replacement of reporting, integration or data-processing platforms is required; and
- enterprise DLP engineering, network implementation and organisation-wide data-handling governance remain outside the application work package.

---

## A. SSP AC-04 Content

Update the existing SSP with a concise AC-04 implementation statement describing how the application controls where information may move, through which paths, in what form and under which conditions. Document the key information types and communities, permitted and prohibited flows, trusted enforcement points, inherited enterprise controls, project or data-partition boundaries, export and integration restrictions, production-to-non-production movement, logging and monitoring arrangements, review frequency and any approved limitations or exceptions.

**Estimated effort: 6–10 hours**

---

## B. SyOps Information-Flow Management Content

Update the existing SyOps with operational procedures for managing application information flows. Include report and export handling, notifications, support and supplier disclosures, production-to-non-production transfers, file and interface operations, masking or sanitisation activities, temporary or exceptional flows, failure handling, flow-review responsibilities, removal of obsolete flows and escalation where the application cannot enforce the required information-handling rule.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Information-Flow Specification

Extend the existing software or security design to define the application's information-flow model. Document information types, sources and destinations; project, programme, case or tenant boundaries; trusted data and handling attributes; server-side enforcement points; search, reporting and export behaviour; APIs, messages and file transfers; notification paths; lower-environment movement; supplier and support flows; masking, redaction and sanitisation rules; preservation of markings and provenance; flow-policy configuration; and fail-secure behaviour when a flow decision or transformation cannot be completed reliably.

**Estimated effort: 16–28 hours**

---

## D. Information-Flow Analysis, Implementation and Enforcement

Review the application against AC-04 requirements and implement any required improvements. Activities may include mapping all material information-flow paths, defining approved source-to-destination rules, distinguishing access permission from transfer permission, enforcing project and data-partition boundaries, applying trusted attributes to flow decisions, implementing deny-by-default behaviour, strengthening server-side flow enforcement, restricting search and discovery leakage, controlling reports, exports, downloads, printing and clipboard functions, tightening APIs, messages and file transfers, preventing uncontrolled production-to-non-production movement, minimising support and supplier disclosure, protecting logs and diagnostics, preserving markings and provenance, controlling copying and derived records, applying masking or sanitisation, preventing inference or aggregation leakage, re-evaluating flows after context changes and protecting flow-policy configuration.

**Estimated effort: 44–120 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to demonstrate that permitted information flows work correctly and prohibited or indirect flows are blocked. Testing should verify project or partition isolation, search and autocomplete leakage, report and export filtering, attachment handling, scheduled report recipients, API over-fetching, message-consumer separation, file-transfer restrictions, production-to-non-production controls, supplier disclosure, masking and sanitisation, preservation of markings, copied or cloned records, logs and error messages, stale cached outputs, unauthorised destinations, flow-control failure and administrative override. Testing should validate the actual information received rather than only the visible user-interface behaviour.

**Estimated effort: 20–44 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for maintaining application information-flow controls in service. Include troubleshooting of blocked or unexpected transfers, management of reports and export destinations, notification issues, support and supplier disclosures, lower-environment data movement, handling of failed masking or transformation, investigation of cross-project leakage, review of flow-policy changes, removal of retired integrations and recipients, and escalation of unsupported information-flow restrictions through the existing risk process.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release and operational acceptance process with AC-04-specific checks. Confirm that approved flows, recipients, report fields, export settings, API and integration scopes, message consumers, file-transfer destinations, lower-environment restrictions, masking or sanitisation rules, classification and project attributes, logging and monitoring are implemented as designed; obsolete flows have been removed; and any accepted limitations or exceptions have been documented and approved.

**Estimated effort: 8–16 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the AC-04 activities through the existing governance process. Activities include information-flow gap analysis, stakeholder and information-owner workshops, agreement of permitted and prohibited flows, coordination with application, data, integration, support and enterprise security teams, design assurance, evidence tracking, alignment with AC-03, AC-05, AC-06, SC-07, SC-28, AU-02 and SI-04 activities, risk and exception management, approval coordination and final compliance review. Existing governance forums and artefacts should be reused rather than creating additional project documentation.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP AC-04 content | **6–10 hours** |
| SyOps information-flow management content | **8–16 hours** |
| Software design and information-flow specification | **16–28 hours** |
| Information-flow analysis, implementation and enforcement | **44–120 hours** |
| Test documentation and evidence | **20–44 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **8–16 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **118–266 hours** |

## Planning interpretation

A mature application with a single information community, limited reporting and export capability, well-defined integrations, established project or data segregation and reliable server-side enforcement is likely to fall near the lower end of the estimate.

Applications with multiple projects or information communities, broad reporting and analytics, numerous exports and integrations, complex masking or sanitisation requirements, thick-client data handling, supplier interfaces, lower-environment data movement or weak existing segregation are more likely to fall toward the upper end.

The estimate excludes enterprise network and firewall implementation, DLP platform engineering, corporate email and web gateways, managed file-transfer infrastructure, enterprise proxy and Internet-egress controls, identity and MFA services, central SIEM and SOC operations, enterprise backup infrastructure, organisation-wide privacy and records-management policy and other inherited enterprise information-flow responsibilities.
