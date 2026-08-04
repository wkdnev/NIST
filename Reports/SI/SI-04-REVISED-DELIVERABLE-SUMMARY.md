# SI-04 System Monitoring — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **SI-04-specific content**, completing targeted implementation gaps, and producing focused evidence of compliance.

The estimates also assume that:

- the application already generates useful logs;
- an enterprise SIEM or log-collection service is available;
- source control, change control and release management are already in place;
- existing document templates and approval routes will be reused;
- no major redesign of the application is required; and
- enterprise-owned monitoring services remain outside the application work package.

---

## A. SSP SI-04 Content

Update the existing SSP with a concise SI-04 implementation statement covering the application monitoring scope, inherited enterprise services, application-specific event generation, forwarding to the enterprise monitoring service, monitoring-failure handling, protection of logging configuration, testing, review arrangements and any known limitations. Existing architecture, SyOps, test and support documents should be referenced rather than duplicated.

**Estimated effort: 6–12 hours**

---

## B. SyOps Monitoring and Response Content

Add SI-04-specific operational content to the existing SyOps. This should define ownership, routine monitoring-health checks, alert triage, investigation support, escalation, containment actions, monitoring-failure response, use of diagnostic logging and recurring review. The work should build on existing support, incident and service-management procedures.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Monitoring Specification

Update the existing software design with the SI-04 monitoring architecture, application event catalogue, event schema, correlation approach, detection use cases, monitoring-health checks, protection requirements and resilience behaviour. Where these already exist, the activity should focus on documenting and aligning them with SI-04 rather than creating a new design.

**Estimated effort: 12–24 hours**

---

## D. Code, Configuration and Software Changes

Complete a short gap analysis against the SI-04 design and implement only the missing capability. Likely work may include adding a small number of security-relevant events, standardising event fields, adding correlation identifiers, improving event forwarding, adding a monitoring-health check, protecting logging configuration or supporting a small number of application-specific alerts. Where the application already has structured logging and SIEM integration, this effort should remain limited.

**Estimated effort: 16–60 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation with targeted SI-04 test cases. Testing should confirm that required events are generated correctly, forwarded and parsed by the enterprise monitoring service, do not expose secrets, support application-specific detection, and provide visible failure handling where logging or forwarding is disrupted. Evidence should be added to the existing security or operational acceptance test pack.

**Estimated effort: 12–24 hours**

---

## F. IT Support and Service Documentation

Update the existing support and service documentation with SI-04-specific monitoring content. This should include monitored components, health checks, common failure scenarios, troubleshooting, escalation, event interpretation, restoration of event forwarding, recurring maintenance and known limitations. Existing support structures and contact models should be reused.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Add SI-04 checks to the existing release and operational acceptance process. This should confirm that the released application version is producing the expected events, forwarding them correctly, using the approved schema, supporting required alerts, and has no unintended debug logging or sensitive-data leakage. Any residual risks should be recorded before handover.

**Estimated effort: 6–12 hours**

---

## H. Project Management, Review and Assurance

Coordinate the SI-04 updates through the existing project governance process. This includes a small number of design and review meetings, action tracking, evidence collation, approval coordination, risk management and final readiness review. A separate governance process should not be created.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP SI-04 content | **6–12 hours** |
| SyOps content | **8–16 hours** |
| Software design and monitoring specification | **12–24 hours** |
| Code, configuration and software changes | **16–60 hours** |
| Test documentation and evidence | **12–24 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **6–12 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **76–180 hours** |

## Planning interpretation

A project with mature logging, existing SIEM integration and only minor documentation gaps is likely to fall near the lower end of the range.

A project requiring several new security events, correlation changes, monitoring-health functionality or SIEM rule updates is more likely to fall toward the upper end.

The estimate excludes enterprise SIEM engineering, SOC operational effort, major application redevelopment, unrelated defect remediation and supplier commercial costs.
