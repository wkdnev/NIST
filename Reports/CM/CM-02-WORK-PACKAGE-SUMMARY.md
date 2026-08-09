# CM-02 Baseline Configuration — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **CM-02-specific content**, establishing or improving the application baseline where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already has documented architecture, component information and established release processes;
- source control, artefact repositories, build or packaging processes and change control already exist;
- enterprise operating systems, infrastructure, identity services, managed EUC and shared-platform baselines are inherited;
- existing document templates, approval routes and operational processes will be reused;
- no major application redesign or wholesale replacement of the build and deployment toolchain is required; and
- enterprise configuration-management policy, infrastructure baselines and platform administration remain outside the application work package.

---

## A. SSP CM-02 Content

Update the existing SSP with a concise CM-02 implementation statement describing how the application establishes, approves, maintains and uses its authoritative baseline configuration. Document the application baseline boundary, inherited enterprise baselines, configuration-item approach, authoritative baseline source, environment coverage, links to CM-06 secure configuration, review and update arrangements, deployment verification, drift management and any approved limitations or deviations.

**Estimated effort: 6–10 hours**

---

## B. SyOps Baseline Management Content

Update the existing SyOps with operational procedures for maintaining the approved application baseline throughout its lifecycle. Include baseline ownership, release and environment management, controlled change, emergency-change reconciliation, post-deployment verification, drift investigation, rollback and recovery arrangements, retirement of superseded components, support responsibilities and periodic baseline review.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Baseline Specification

Extend the existing software or solution design to define the structure of the application baseline. Document the configuration items that make up the solution, component and dependency relationships, environment-specific differences, database schema and migration versions, thick-client packages where applicable, interfaces, runtime and framework dependencies, configuration references, build and deployment artefacts, recovery dependencies and the identifiers needed to reproduce and verify an approved release.

**Estimated effort: 12–24 hours**

---

## D. Baseline Establishment, Build and Configuration Control

Review the existing release and configuration-management arrangements against CM-02 and implement any required improvements. Activities may include defining practical configuration items, establishing one authoritative baseline record, assigning release and artefact identifiers, linking secure configuration and dependency records, incorporating database and thick-client packages, improving reproducibility of builds or supplier installation packages, protecting release artefacts and baseline records, strengthening release tagging and integrity controls, ensuring configuration-only and dependency-only changes follow change control, and updating the baseline after material change, emergency fixes, upgrades or retirement.

**Estimated effort: 24–64 hours**

---

## E. Test, Deployment Verification and Evidence

Extend the existing test and assurance documentation to demonstrate that the approved baseline can be verified against the deployed application. Testing and evidence should confirm the expected application, package, dependency, configuration and schema versions across relevant tiers and nodes; verify build or package provenance where applicable; confirm that deployment matches the approved release; identify and reconcile baseline drift; validate rollback or recovery to a known approved state; and record any discrepancies, exceptions and corrective actions in the existing test, release, change or risk records.

**Estimated effort: 16–32 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for maintaining and troubleshooting the application baseline in service. Include how support staff identify the approved release, verify deployed versions, investigate baseline mismatches, handle emergency fixes, manage rollback and recovery, recognise and escalate unapproved drift, remove or retire superseded components, retain previous approved artefacts where required, and support periodic baseline accuracy reviews.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release and operational acceptance process with CM-02-specific checks. Confirm that the release has an approved baseline identifier, required components and dependencies are known, secure configuration has been applied, database and interface versions are correct, testing and vulnerability treatment are complete, rollback and recovery are viable, artefacts are protected and traceable, deviations are recorded, and post-deployment verification confirms that production matches the authorised baseline.

**Estimated effort: 8–16 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the CM-02 activities through the existing governance process. Activities include baseline gap analysis, stakeholder and technical reviews, agreement of configuration-item boundaries, evidence tracking, release and baseline approval coordination, risk and deviation management, alignment with CM-06 and CM-08 records, and final compliance review. Existing governance forums and artefacts should be reused rather than creating separate project documentation.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP CM-02 content | **6–10 hours** |
| SyOps baseline management content | **8–16 hours** |
| Software design and baseline specification | **12–24 hours** |
| Baseline establishment, build and configuration control | **24–64 hours** |
| Test, deployment verification and evidence | **16–32 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **8–16 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **90–194 hours** |

## Planning interpretation

A mature application with established source and artefact repositories, controlled release manifests, reproducible build or packaging processes, current component records and reliable post-deployment verification is likely to fall near the lower end of the estimate.

Applications requiring creation or rationalisation of the authoritative baseline, improved configuration-item identification, dependency or database version control, thick-client package baselining, stronger artefact protection, improved build reproducibility, drift detection or recovery-baseline work are more likely to fall toward the upper end.

The estimate excludes enterprise operating-system and infrastructure baselines, managed Windows EUC baselines, network and firewall baselines, hypervisor and shared-platform baselines, enterprise identity and MFA baselines, enterprise PKI and secrets-platform baselines, infrastructure asset management, enterprise vulnerability tooling and other inherited enterprise configuration-management responsibilities.
