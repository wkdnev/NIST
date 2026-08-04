# CM-06 Configuration Settings — Application Work Package (Detailed)

## Assumptions

This work package assumes the SSP, SyOps, Software Design, Test, Support and Release documents already exist. The work is limited to incorporating **CM-06-specific** content and implementing any application-specific configuration improvements required for compliance.

---

# A. SSP CM-06 Content

Update the SSP to describe how the application implements secure configuration settings, what configuration is owned by the application, what is inherited from the enterprise and how configuration compliance is maintained.

| Task | Hours |
|---|---:|
| Review existing SSP and identify CM-06 gaps | 2 |
| Define application configuration boundary | 2 |
| Document inherited enterprise configuration controls | 1 |
| Document application-owned security settings | 2 |
| Document configuration governance and ownership | 2 |
| Document approved deviations/exceptions | 1 |
| Reference supporting design, SyOps and test evidence | 2 |
| Peer review and approval | 2 |

**Subtotal: 14 hours**

---

# B. SyOps Configuration Content

Update operational documentation so support teams can maintain secure application configuration.

| Task | Hours |
|---|---:|
| Define configuration ownership | 2 |
| Define configuration change procedure | 2 |
| Define configuration verification after deployment | 2 |
| Define configuration drift monitoring process | 2 |
| Define rollback procedure | 2 |
| Define emergency configuration process | 2 |
| Define periodic configuration review | 2 |
| Review and approval | 2 |

**Subtotal: 16 hours**

---

# C. Software Design

Extend the existing design with application-specific configuration requirements.

| Task | Hours |
|---|---:|
| Review architecture for configurable components | 2 |
| Identify security-sensitive settings | 4 |
| Document approved secure defaults | 4 |
| Document configuration dependencies | 2 |
| Document secrets/configuration separation | 2 |
| Document environment-specific configuration | 2 |
| Document configuration validation approach | 2 |
| Technical review | 2 |

**Subtotal: 20 hours**

---

# D. Configuration Analysis, Implementation and Automation

Review the application against CM-06 and implement missing controls.

| Task | Hours |
|---|---:|
| Perform CM-06 gap analysis | 4 |
| Review all application configuration settings | 6 |
| Remove unnecessary functionality/features | 4 |
| Configure secure defaults | 6 |
| Harden session and security settings | 6 |
| Review authentication-related configuration | 4 |
| Review authorisation configuration | 4 |
| Secure application secrets and keys | 6 |
| Lock down administrative configuration access | 4 |
| Review API and integration configuration | 4 |
| Implement configuration validation | 6 |
| Improve deployment automation/configuration-as-code | 8 |
| Implement configuration drift detection (where practical) | 6 |
| Code review and remediation | 4 |

**Subtotal: 72 hours**

---

# E. Test Documentation and Evidence

Extend existing test evidence to demonstrate CM-06 compliance.

| Task | Hours |
|---|---:|
| Update security test plan | 2 |
| Create configuration verification tests | 4 |
| Verify secure defaults | 2 |
| Verify configuration protection | 2 |
| Verify environment separation | 2 |
| Verify secrets handling | 2 |
| Verify disabled functionality | 2 |
| Verify deployment configuration | 2 |
| Execute testing | 6 |
| Produce evidence and approvals | 4 |

**Subtotal: 28 hours**

---

# F. IT Support Documentation

Update operational support information.

| Task | Hours |
|---|---:|
| Document configuration ownership | 2 |
| Document routine verification activities | 2 |
| Document troubleshooting guidance | 2 |
| Document rollback activities | 2 |
| Document drift investigation | 2 |
| Document release support | 2 |
| Document maintenance schedule | 2 |
| Review and approval | 2 |

**Subtotal: 16 hours**

---

# G. Release and Operational Acceptance

Update release evidence.

| Task | Hours |
|---|---:|
| Verify deployed configuration matches approved baseline | 2 |
| Verify production settings | 2 |
| Verify secrets references | 2 |
| Verify configuration validation completed | 2 |
| Record approved deviations | 1 |
| Operational acceptance review | 2 |

**Subtotal: 11 hours**

---

# H. Project Management and Assurance

Coordinate delivery through existing governance.

| Task | Hours |
|---|---:|
| Planning and scheduling | 2 |
| CM-06 workshops | 4 |
| Track actions and evidence | 4 |
| Coordinate reviews | 2 |
| Risk and issue management | 2 |
| Final readiness review | 2 |

**Subtotal: 16 hours**

---

# Total Estimated Effort

| Deliverable | Hours |
|---|---:|
| SSP | 14 |
| SyOps | 16 |
| Software Design | 20 |
| Configuration Implementation | 72 |
| Test Evidence | 28 |
| IT Support | 16 |
| Release & Acceptance | 11 |
| Project Management | 16 |
| **Total** | **193 hours** |

## Notes

- Estimates assume a mature application with existing SDLC artefacts.
- Activities focus only on **application responsibilities**.
- Enterprise infrastructure, operating systems, network configuration, endpoint hardening, identity platform administration and enterprise monitoring remain inherited responsibilities.
