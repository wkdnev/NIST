# AC-03 Access Enforcement — Application Work Package (Detailed)

## Assumptions

This work package assumes the SSP, SyOps, Software Design, Test documentation, IT Support documentation, Release documentation and project governance already exist. The work is limited to incorporating **AC-03-specific** content, implementing any application-specific access enforcement improvements, and producing the evidence required to demonstrate compliance.

---

# A. SSP AC-03 Content

Update the SSP to describe how the application enforces authorised access to information, functions and resources, where access decisions are made, which enterprise services are inherited, and how application-specific authorisation is implemented.

| Task | Hours |
|---|---:|
| Review SSP and identify AC-03 gaps | 2 |
| Define application access control boundary | 2 |
| Document inherited enterprise identity services | 1 |
| Document application authorisation model | 4 |
| Describe enforcement points and deny-by-default approach | 3 |
| Document privileged and service access approach | 2 |
| Document exceptions and limitations | 1 |
| Peer review and approval | 2 |

**Subtotal: 17 hours**

---

# B. SyOps Access Control Content

Update the SyOps with operational procedures for maintaining application access controls.

| Task | Hours |
|---|---:|
| Define access administration responsibilities | 2 |
| Document user provisioning workflow | 2 |
| Document privileged access procedures | 2 |
| Document emergency/delegated access process | 2 |
| Define periodic access review activities | 2 |
| Define investigation of access failures | 2 |
| Document revocation and deprovisioning activities | 2 |
| Review and approval | 2 |

**Subtotal: 16 hours**

---

# C. Software Design

Update the software design to define how authorisation is implemented.

| Task | Hours |
|---|---:|
| Review protected application resources | 4 |
| Define RBAC/ABAC/relationship model | 6 |
| Document server-side enforcement architecture | 4 |
| Define workflow and object-level controls | 4 |
| Define service identity authorisation | 3 |
| Document policy decision points | 3 |
| Define access failure behaviour | 2 |
| Technical review | 2 |

**Subtotal: 28 hours**

---

# D. Access Enforcement Implementation

Implement or improve application access enforcement.

| Task | Hours |
|---|---:|
| Perform AC-03 gap analysis | 4 |
| Review all protected resources | 4 |
| Implement server-side authorisation checks | 12 |
| Remove client-side trust assumptions | 6 |
| Implement deny-by-default behaviour | 4 |
| Configure least-privilege permissions | 6 |
| Implement object and record-level security | 12 |
| Implement workflow/state enforcement | 8 |
| Implement separation of duties where required | 8 |
| Secure privileged administrative functions | 6 |
| Restrict service identities and API scopes | 6 |
| Protect against direct-object reference manipulation | 8 |
| Ensure consistent enforcement across APIs, UI and batch | 8 |
| Implement fail-closed behaviour | 4 |
| Protect authorisation configuration | 4 |
| Code review and remediation | 6 |

**Subtotal: 116 hours**

---

# E. Test Documentation and Evidence

Extend the existing test suite to demonstrate AC-03 compliance.

| Task | Hours |
|---|---:|
| Update security test plan | 2 |
| Develop positive role tests | 4 |
| Develop negative access tests | 4 |
| Test object-level access | 4 |
| Test workflow restrictions | 4 |
| Test API manipulation and direct-object attacks | 6 |
| Test service identities | 4 |
| Test fail-closed behaviour | 2 |
| Execute testing | 8 |
| Produce evidence and approvals | 4 |

**Subtotal: 42 hours**

---

# F. IT Support Documentation

Update operational support documentation for access enforcement.

| Task | Hours |
|---|---:|
| Document access support responsibilities | 2 |
| Document troubleshooting procedures | 2 |
| Document privileged support activities | 2 |
| Document access review activities | 2 |
| Document investigation procedures | 2 |
| Document operational maintenance | 2 |
| Review and approval | 2 |

**Subtotal: 14 hours**

---

# G. Release and Operational Acceptance

Update release evidence to demonstrate compliant access enforcement.

| Task | Hours |
|---|---:|
| Verify deployed access configuration | 2 |
| Verify role model implementation | 2 |
| Verify privileged functions | 2 |
| Verify service identities | 2 |
| Record accepted exceptions | 1 |
| Operational acceptance review | 2 |

**Subtotal: 11 hours**

---

# H. Project Management and Assurance

Coordinate delivery through existing governance.

| Task | Hours |
|---|---:|
| Planning and scheduling | 2 |
| Technical workshops | 4 |
| Evidence tracking | 4 |
| Design and peer reviews | 2 |
| Risk and issue management | 2 |
| Final compliance review | 2 |

**Subtotal: 16 hours**

---

# Total Estimated Effort

| Deliverable | Hours |
|---|---:|
| SSP | 17 |
| SyOps | 16 |
| Software Design | 28 |
| Access Enforcement Implementation | 116 |
| Test Documentation | 42 |
| IT Support | 14 |
| Release & Acceptance | 11 |
| Project Management | 16 |
| **Total** | **260 hours** |

## Notes

- Estimates assume an existing mature SDLC and application documentation.
- Activities cover **application responsibilities only**.
- Enterprise authentication, identity lifecycle, MFA, PAM, directory services, SIEM and infrastructure controls remain inherited.
- The largest effort is implementing and validating robust server-side access enforcement across all application interfaces, workflows, APIs and service identities, as required by AC-03.
