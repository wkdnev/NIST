# CM-06 Configuration Settings — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **CM-06-specific content**, implementing targeted configuration improvements where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already has documented architecture and deployment processes;
- enterprise operating systems, infrastructure, identity services and platform hardening are inherited;
- existing document templates and approval routes will be reused;
- secure deployment pipelines already exist;
- no major application redesign is required; and
- enterprise configuration standards remain outside the application work package.

---

## A. SSP CM-06 Content

Update the existing SSP with a concise CM-06 implementation statement describing the application's approach to secure configuration settings. Document the configuration boundary, inherited enterprise controls, application-owned settings, configuration ownership, review arrangements, approved deviations and references to the authoritative technical configuration sources.

**Estimated effort: 6–10 hours**

---

## B. SyOps Configuration Management Content

Update the existing SyOps with operational procedures for maintaining secure configuration throughout the application lifecycle. Include configuration ownership, environment management, deployment responsibilities, configuration verification, drift management, operational reviews, exception handling and restoration procedures following configuration failures.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Configuration Specification

Extend the software design to define the application's security-relevant configuration model. Document approved settings, security rationale, configuration dependencies, environment differences, secrets handling, interface configuration, administrative settings, deployment mechanisms, configuration protection and verification methods.

**Estimated effort: 12–24 hours**

---

## D. Configuration Analysis, Implementation and Automation

Review the current application configuration against the approved CM-06 baseline and implement any required improvements. Activities may include defining secure defaults, removing unnecessary functionality, strengthening session and authentication settings, improving secrets management, restricting administrative functions, automating deployment configuration, introducing configuration-as-code where appropriate, implementing configuration validation and addressing configuration drift.

**Estimated effort: 20–60 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to verify that approved security settings operate as intended. Testing should confirm secure defaults, configuration protection, environment separation, secrets handling, disabled functionality, access restrictions, configuration verification, deployment validation and behaviour under incorrect or unauthorised configuration changes. Evidence should be incorporated into existing security and operational test documentation.

**Estimated effort: 12–24 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for maintaining the approved application configuration. Include configuration ownership, routine verification activities, troubleshooting, rollback procedures, drift detection, configuration reviews, exception management, release support and ongoing maintenance responsibilities.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release process with CM-06-specific acceptance checks. Confirm that the deployed configuration matches the approved baseline, secure defaults remain enabled, production settings differ appropriately from non-production, secrets are correctly referenced, configuration verification has completed successfully and any approved deviations have been documented.

**Estimated effort: 6–12 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the CM-06 activities through the existing governance process. Activities include configuration gap analysis, planning, stakeholder reviews, design assurance, evidence tracking, approval coordination, risk management and final compliance review. Existing governance processes should be reused rather than creating additional project artefacts.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP CM-06 content | **6–10 hours** |
| SyOps content | **8–16 hours** |
| Software design and configuration specification | **12–24 hours** |
| Configuration analysis, implementation and automation | **20–60 hours** |
| Test documentation and evidence | **12–24 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **6–12 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **80–178 hours** |

## Planning interpretation

A mature application that already follows corporate deployment standards and has well-controlled configuration management is expected to fall near the lower end of the estimate.

Projects requiring rationalisation of configuration settings, removal of insecure defaults, automation of configuration management, improved secrets handling or implementation of configuration validation and drift detection are more likely to fall toward the upper end.

The estimate excludes enterprise operating-system hardening, infrastructure configuration, network configuration, enterprise identity management, enterprise secrets-management platforms, CMDB administration and other inherited enterprise configuration management responsibilities.
