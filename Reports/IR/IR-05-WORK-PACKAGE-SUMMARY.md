# IR-05 Incident Monitoring — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process, enterprise incident-management process and project governance. The work is therefore limited to adding or updating **IR-05-specific content**, improving application-specific incident-monitoring and response readiness where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already uses the enterprise SOC, SIEM and incident-management platform;
- enterprise incident policy, severity definitions, forensic capability, legal/privacy escalation and corporate communications are inherited;
- existing application logging, monitoring, change, recovery and support processes will be reused;
- existing document templates, approval routes and incident records will be reused rather than creating parallel artefacts;
- no major redesign of the enterprise monitoring or incident-management platforms is required; and
- enterprise incident command, forensic investigation and organisation-wide reporting remain outside the application work package.

---

## A. SSP IR-05 Content

Update the existing SSP with a concise IR-05 implementation statement describing how the application supports incident monitoring and the enterprise incident-response process. Document the application-specific incident scenarios, evidence sources, monitoring and escalation approach, application roles and responsibilities, incident-recording arrangements, containment and recovery support, corrective-action tracking, review arrangements, inherited enterprise services and any known monitoring or response limitations.

**Estimated effort: 6–10 hours**

---

## B. SyOps Incident Monitoring and Response Content

Update the existing SyOps with operational procedures for application incident monitoring and response support. Include application incident roles and contacts, triage information, escalation routes, evidence locations, application-specific containment options, approval authorities, evidence-preservation requirements, supplier involvement, degraded or restricted service arrangements, secure recovery, return-to-service criteria, corrective-action handling and periodic review of the incident-monitoring arrangements.

**Estimated effort: 8–16 hours**

---

## C. Security Design, Event and Incident-Monitoring Specification

Extend the existing security or solution design to define the application evidence and monitoring needed to support IR-05. Document security-relevant event sources, correlation identifiers, event context, forwarding to the approved enterprise monitoring service, evidence-retention dependencies, short-lived or volatile evidence, affected components and trust boundaries, incident scoping information, containment points and the relationships to AU-02, SI-04, CM-02, CM-06, CM-08 and recovery controls.

**Estimated effort: 12–24 hours**

---

## D. Incident Monitoring, Triage and Response Readiness Implementation

Review the application against IR-05 requirements and implement any required improvements. Activities may include defining application-specific incident scenarios and severity mappings, improving security-relevant event generation and correlation, validating SIEM forwarding and parsing, establishing application triage information, identifying safe containment actions, ensuring affected users, records, services, components and integrations can be scoped, defining preservation methods for logs and volatile evidence, preparing recovery and return-to-service checks, confirming supplier escalation routes, and ensuring corrective actions can be tracked through existing defect, risk, POA&M, change or service-management processes.

**Estimated effort: 20–48 hours**

---

## E. Test, Exercise and Evidence

Extend the existing test and assurance documentation to demonstrate that application incident-monitoring arrangements work in practice. Testing or exercises should verify that required events are generated and correlated, monitoring feeds are usable by the SOC, application specialists can interpret alerts, affected scope and business impact can be established, evidence can be preserved, containment options are understood and executable, recovery can restore a trusted state, return-to-service criteria can be applied, and corrective actions can be verified. Evidence should be incorporated into existing security test reports, operational exercises, incident-response exercises and recovery-test records.

**Estimated effort: 12–24 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for supporting application incidents. Include alert and incident escalation, technical triage, collection of application-specific facts, use of application and supplier contacts, evidence handling, containment support, restricted or read-only operating modes, emergency changes, recovery support, monitoring of containment effectiveness, tracking of follow-up actions and escalation of unavailable evidence or response limitations.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Operational Readiness Evidence

Enhance the existing release and operational acceptance process with IR-05-specific readiness checks. Confirm that new or changed functionality has appropriate monitoring, required events are available to the approved monitoring service, incident contacts and containment options remain current, evidence and recovery dependencies are understood, application baselines and configuration can support investigation and recovery, supplier escalation remains valid, and any incident-monitoring limitations or accepted risks have been documented.

**Estimated effort: 6–12 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the IR-05 activities through the existing governance process. Activities include incident-monitoring gap analysis, stakeholder and SOC workshops, coordination with application support, business owners, suppliers and recovery teams, evidence tracking, exercise planning, review of monitoring limitations, risk and corrective-action management, approval coordination and final compliance review. Existing governance forums and enterprise incident processes should be reused rather than creating a parallel application incident-management structure.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP IR-05 content | **6–10 hours** |
| SyOps incident monitoring and response content | **8–16 hours** |
| Security design, event and incident-monitoring specification | **12–24 hours** |
| Incident monitoring, triage and response readiness implementation | **20–48 hours** |
| Test, exercise and evidence | **12–24 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and operational readiness | **6–12 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **80–166 hours** |

## Planning interpretation

A mature application with useful security logging, established SIEM integration, documented recovery arrangements, known support contacts and an existing enterprise incident-response process is likely to fall near the lower end of the estimate.

Applications requiring new or improved application event generation, correlation across multiple tiers, stronger incident scoping capability, defined containment mechanisms, volatile-evidence preservation, supplier-response arrangements, recovery-readiness improvements or dedicated incident exercises are more likely to fall toward the upper end.

The estimate covers **initial application readiness and evidence work**. It does not include the effort required to investigate and remediate an actual security incident, which is event-dependent and may be substantially greater.

The estimate excludes enterprise SOC operations, incident command, SIEM platform administration, forensic investigation, legal and privacy response, corporate communications, organisation-wide incident reporting, enterprise threat intelligence and other inherited enterprise incident-response responsibilities.
