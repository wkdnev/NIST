# CM-07 Least Functionality — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **CM-07-specific content**, implementing targeted least-functionality improvements where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already has documented architecture, component information and established deployment processes;
- enterprise Windows EUC, server operating systems, network controls, managed database platforms, endpoint protection and shared infrastructure baselines are inherited;
- existing document templates, configuration records and approval routes will be reused;
- secure development, testing, logging, change and release processes already exist;
- no major product replacement or extensive supplier redevelopment is required; and
- enterprise platform hardening, infrastructure service reduction and corporate allow-listing remain outside the application work package.

---

## A. SSP CM-07 Content

Update the existing SSP with a concise CM-07 implementation statement describing how the application identifies essential functionality and removes, disables or restricts unnecessary capability. Document the application functionality boundary, inherited enterprise controls, enabled and prohibited capability approach, treatment of modules, interfaces, protocols, administrative and diagnostic functions, thick-client capabilities where applicable, post-release verification, periodic review arrangements and any approved exceptions.

**Estimated effort: 6–10 hours**

---

## B. SyOps Least-Functionality Content

Update the existing SyOps with operational procedures for maintaining the approved functional scope of the application. Include administration of enabled and disabled features, support and diagnostic functionality, temporary troubleshooting capabilities, background jobs, plugins and extensions, import/export functions, restricted interfaces, outbound connections, restoration of the approved state after support activity, review after upgrades or material change, and escalation of functionality that cannot be removed.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Approved Functionality Specification

Extend the existing software or solution design to define the application's approved functionality model. Document the essential business functions, enabled and prohibited modules, services, interfaces, protocols, APIs, administrative capabilities, file and content handling, import/export and bulk-processing functions, scripting or extension mechanisms, background jobs, thick-client components, outbound destinations, resource limits, and the configuration or deployment controls used to prevent unauthorised re-enablement.

**Estimated effort: 12–24 hours**

---

## D. Least-Functionality Analysis, Implementation and Hardening

Review the application against CM-07 requirements and implement any required improvements. Activities may include identifying essential and non-essential functions, disabling or removing unused modules and services, removing default, sample, test and development capability, restricting interfaces and protocol methods, limiting file and executable handling, constraining import, export and bulk functions, restricting administrative and diagnostic features, disabling unnecessary scripting, macros, plugins and extensions, minimising thick-client packages, removing obsolete scheduled jobs, restricting outbound connections, applying proportionate resource limits, and protecting feature flags, configuration and deployment mechanisms from unauthorised re-enablement.

**Estimated effort: 22–68 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to demonstrate that prohibited or unnecessary functionality is unavailable and approved functionality remains usable. Testing should verify disabled modules, removed sample or development components, inaccessible administrative and diagnostic routes, rejected unused API methods and protocols, blocked file types, restricted scripting and plugins, constrained import/export and bulk operations, standard-user thick-client behaviour, disabled or obsolete jobs, denied outbound connections, direct invocation of hidden functions, and post-deployment alignment with the approved functionality set. Evidence should be incorporated into the existing security and operational test documentation.

**Estimated effort: 14–30 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for maintaining least functionality in service. Include how support staff identify the approved enabled capability set, manage temporary diagnostic functions, investigate unexpected modules, services, jobs or endpoints, restore the approved state after troubleshooting, review functionality following upgrades and supplier changes, remove obsolete components, recognise unauthorised re-enablement, and escalate non-removable or risky functionality through the existing risk process.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release and operational acceptance process with CM-07-specific checks. Confirm that only approved modules, services, interfaces, plugins, jobs and capabilities are present; default, test and debug functionality has been removed or disabled; thick-client packages contain only required components; outbound destinations and high-impact functions are restricted; prohibited functionality cannot be directly invoked; and any unavoidable functionality or supplier constraints have been formally documented and approved.

**Estimated effort: 6–12 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the CM-07 activities through the existing governance process. Activities include least-functionality gap analysis, stakeholder confirmation of essential business capability, technical and supplier reviews, coordination with CM-02, CM-06, CM-08 and AC-06 activities, evidence tracking, exception and risk management, approval coordination and final compliance review. Existing governance forums and artefacts should be reused rather than creating additional project documentation.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP CM-07 content | **6–10 hours** |
| SyOps least-functionality content | **8–16 hours** |
| Software design and approved functionality specification | **12–24 hours** |
| Least-functionality analysis, implementation and hardening | **22–68 hours** |
| Test documentation and evidence | **14–30 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **6–12 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **84–192 hours** |

## Planning interpretation

A mature application with a clearly understood business scope, limited optional functionality, controlled product configuration, established release hardening and effective negative security testing is likely to fall near the lower end of the estimate.

Applications requiring removal of numerous optional modules, legacy services or diagnostic features, tighter control of scripting and plugins, thick-client package rationalisation, restriction of import/export or outbound capability, or remediation of supplier-controlled functions that cannot readily be disabled are more likely to fall toward the upper end.

The estimate excludes enterprise Windows and server operating-system feature baselines, network and firewall service reduction, managed database-platform hardening, hypervisor and shared-platform functionality, corporate software-distribution controls, enterprise application allow-listing, infrastructure monitoring and other inherited enterprise responsibilities.
