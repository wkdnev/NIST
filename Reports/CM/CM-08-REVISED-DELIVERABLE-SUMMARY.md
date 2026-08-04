# CM-08 System Component Inventory — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **CM-08-specific content**, completing targeted implementation gaps, and producing focused evidence of compliance.

The estimates also assume that:
- the application already has an established architecture and component inventory;
- an enterprise CMDB, asset management capability and configuration management processes already exist;
- source control, build pipelines and release management are already exist;
- existing document templates and approval routes will be reused;
- no major redesign of the application is required; and
- enterprise-owned asset discovery and inventory services remain outside the application work package.

---

## A. SSP CM-08 Content

Update the existing SSP with a concise CM-08 implementation statement covering the application inventory boundary, component categories, authoritative inventory sources, ownership, reconciliation with the baseline, inventory review arrangements and any known limitations. Reference existing architecture, CMDB, software design and operational documentation rather than duplicating detailed inventory information.

**Estimated effort: 6–10 hours**

---

## B. SyOps Component Inventory Content

Add CM-08-specific operational content to the existing SyOps. Define how the application inventory is maintained, how inventory updates are incorporated into change and release activities, ownership responsibilities, reconciliation activities, periodic reviews, discrepancy management and decommissioning procedures. Extend existing operational processes rather than creating new ones.

**Estimated effort: 6–12 hours**

---

## C. Software Design and Component Inventory Model

Update the existing software design to document the application inventory model. Define inventory scope, component categories, mandatory attributes, logical relationships, authoritative data sources, dependency management, interfaces, service identities, certificates and reconciliation with the approved architecture and CM-02 baseline.

**Estimated effort: 10–20 hours**

---

## D. Inventory Updates, Configuration and Minor Automation

Perform a targeted gap analysis against CM-08 and implement only missing capability. Typical work includes updating component records, improving inventory attributes, linking dependencies, documenting interfaces, recording service identities and certificates, introducing SBOM references where appropriate and automating simple reconciliation where practical using existing enterprise tooling.

**Estimated effort: 12–40 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation with CM-08 verification activities. Demonstrate that application components are accurately inventoried, ownership is defined, versions match the approved baseline, dependencies are identified, inventory records are maintained through change and reconciliation activities are effective.

**Estimated effort: 8–20 hours**

---

## F. IT Support and Service Documentation

Update the existing support documentation with CM-08 operational guidance covering inventory ownership, update procedures, reconciliation activities, discrepancy handling, lifecycle management, retirement activities and periodic inventory reviews.

**Estimated effort: 6–12 hours**

---

## G. Release, Acceptance and Handover Evidence

Add CM-08 checks to the existing release and operational acceptance process. Confirm that deployed components are reflected in the approved inventory, baseline records have been updated, ownership is assigned, dependencies are recorded and release evidence references the correct inventory records.

**Estimated effort: 4–8 hours**

---

## H. Project Management, Review and Assurance

Coordinate the CM-08 activities through the existing project governance arrangements including technical reviews, stakeholder engagement, evidence tracking, approval coordination, risk management and final compliance review.

**Estimated effort: 6–12 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP CM-08 content | **6–10 hours** |
| SyOps content | **6–12 hours** |
| Software design and inventory model | **10–20 hours** |
| Inventory updates and minor automation | **12–40 hours** |
| Test documentation and evidence | **8–20 hours** |
| IT support and service documentation | **6–12 hours** |
| Release, acceptance and handover | **4–8 hours** |
| Project management, review and assurance | **6–12 hours** |
| **Total estimated application effort** | **58–134 hours** |

## Planning interpretation

A mature application with a well-maintained CMDB, current architecture documentation and established release processes is likely to fall near the lower end of the range.

Applications requiring inventory rationalisation, dependency mapping, SBOM generation, significant reconciliation or improved component governance are more likely to fall toward the upper end.

The estimate excludes enterprise CMDB administration, infrastructure discovery tooling, enterprise asset management, vulnerability platform administration and other inherited enterprise configuration management activities.
