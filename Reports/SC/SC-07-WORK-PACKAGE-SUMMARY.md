# SC-07 Boundary Protection — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **SC-07-specific content**, implementing targeted application boundary-protection improvements where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already operates within the approved corporate network and uses established enterprise network, firewall, identity, PKI, proxy and monitoring services;
- enterprise perimeter protection, network segmentation, routing, VPN, managed firewalls, secure DNS, load balancers and network monitoring are inherited;
- existing architecture, interface, data-flow, change and release artefacts will be reused;
- secure development, testing, logging and operational support processes already exist;
- no major enterprise network redesign or extensive supplier product redevelopment is required; and
- enterprise firewall implementation, routing administration and shared network-boundary operations remain outside the application work package.

---

## A. SSP SC-07 Content

Update the existing SSP with a concise SC-07 implementation statement describing how the application defines and protects its trust boundaries and managed interfaces. Document the application boundary, inherited enterprise controls, key trust transitions, approved communication paths, application-layer enforcement, production/non-production separation, privileged and supplier access paths, outbound restrictions, monitoring arrangements, review frequency and any approved boundary-protection exceptions.

**Estimated effort: 6–10 hours**

---

## B. SyOps Boundary and Connectivity Content

Update the existing SyOps with operational procedures for maintaining approved application communication paths. Include support and administrative connectivity, supplier access, approved endpoints and destinations, handling of temporary connectivity, communication failures and degraded modes, certificate or identity failures, monitoring of unexpected flows, removal of obsolete interfaces, recovery and failover connectivity, and escalation of boundary-control exceptions.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Communication-Flow Specification

Extend the existing software or security design to define the application's boundary-protection architecture. Document application components, tiers and trust zones; user, service, data and administrative paths; approved communication flows; APIs, messages and file transfers; thick-client communications; service-to-service authentication; database access patterns; production/non-production separation; outbound destinations; redirects, callbacks and webhooks; encryption and validation requirements; monitoring points; and safe behaviour when boundary-control dependencies fail.

**Estimated effort: 16–28 hours**

---

## D. Boundary Protection Analysis, Implementation and Enforcement

Review the application against SC-07 requirements and implement any required improvements. Activities may include defining the application boundary and trust transitions, rationalising communication flows, applying deny-by-default at application interfaces, strengthening server-side identity and authorisation, preventing ordinary clients from directly reaching data or privileged interfaces, securing thick-client communications, restricting APIs, queues and file-transfer paths, authenticating service-to-service calls, constraining outbound destinations and callbacks, preventing server-side request forgery and arbitrary proxying, separating production and non-production, tightening supplier and administrative access, validating information crossing boundaries, protecting communications in transit and removing obsolete connectivity.

**Estimated effort: 36–100 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to demonstrate that approved communications succeed and prohibited paths fail safely. Testing should verify direct service and database access restrictions, unknown or incorrectly scoped API clients, invalid service identities and certificates, blocked methods and destinations, message replay, malformed or oversized payloads, file-transfer controls, outbound URL manipulation, redirects and callbacks, server-side request forgery attempts, production/non-production crossover, supplier and administrative access, logical project or tenant boundaries, fail-closed behaviour, logging and recovery or failover paths. Evidence should be incorporated into existing security, integration and operational test documentation.

**Estimated effort: 20–40 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for operating and troubleshooting application boundary controls. Include approved communication paths, endpoint and certificate troubleshooting, service-to-service failures, temporary support connectivity, supplier-access handling, investigation of blocked or unexpected flows, safe response to gateway, broker, DNS or policy-service failures, removal of obsolete connectivity, post-change verification and escalation where an application interface cannot meet the required boundary model.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release and operational acceptance process with SC-07-specific checks. Confirm that deployed endpoints, routes, service identities, API clients, message paths, file transfers and outbound destinations match the approved design; production and non-production remain separated; privileged and supplier interfaces are restricted; transport protection and certificate validation operate correctly; obsolete connectivity has been removed; relevant boundary events reach central monitoring; and any accepted exceptions have been documented.

**Estimated effort: 8–16 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the SC-07 activities through the existing governance process. Activities include boundary and communication-flow gap analysis, architecture and stakeholder workshops, coordination with enterprise network, identity, PKI, security operations and supplier teams, evidence tracking, connectivity and exception reviews, alignment with related AC, CM, SC and SI controls, risk management, approval coordination and final compliance review. Existing governance forums and artefacts should be reused rather than creating additional project documentation.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP SC-07 content | **6–10 hours** |
| SyOps boundary and connectivity content | **8–16 hours** |
| Software design and communication-flow specification | **16–28 hours** |
| Boundary protection analysis, implementation and enforcement | **36–100 hours** |
| Test documentation and evidence | **20–40 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **8–16 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **110–242 hours** |

## Planning interpretation

A mature application with a well-defined architecture, limited interfaces, no direct client-to-database access, established service authentication, controlled outbound connectivity and reliable end-to-end security testing is likely to fall near the lower end of the estimate.

Applications with thick clients, many APIs or message flows, legacy direct database access, numerous integrations, supplier support paths, complex project or data segregation, unrestricted outbound capabilities or weak production/non-production separation are more likely to fall toward the upper end.

The estimate excludes enterprise firewall and routing implementation, corporate perimeter protection, VPN and remote-access infrastructure, enterprise proxies and secure web gateways, central DNS and IP-address management, network IDS/IPS, managed load-balancer operation, enterprise PKI administration, corporate network-flow monitoring and other inherited enterprise boundary-protection responsibilities.
