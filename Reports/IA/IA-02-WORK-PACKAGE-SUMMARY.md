# IA-02 Identification and Authentication (Organisational Users) — Revised Deliverable Summary and Effort

## Assumptions

These estimates assume the project already has an established SSP, SyOps, software design, test documentation, IT support documentation, release process and project governance. The work is therefore limited to adding or updating **IA-02-specific content**, implementing targeted application identification and authentication improvements where gaps exist, and producing focused evidence of compliance.

The estimates also assume that:

- the application already uses, or can integrate with, approved enterprise identity, federation and multi-factor authentication services;
- enterprise identity proofing, corporate directory services, MFA, federation/SSO, authenticator lifecycle, PAM, managed Windows EUC and VPN authentication are inherited;
- existing document templates, identity registrations, secrets/certificate services, approval routes and monitoring processes will be reused;
- the application already has an identifiable organisational-user population and established account/role model;
- no major replacement of the enterprise identity platform or extensive product redevelopment is required; and
- enterprise identity assurance, authenticator issuance and organisation-wide identity governance remain outside the application work package.

---

## A. SSP IA-02 Content

Update the existing SSP with a concise IA-02 implementation statement describing how organisational users are uniquely identified and authenticated before application access is granted. Document the organisational-user population, approved identity providers and authentication paths, application identity mapping, authentication strength requirements, privileged and support authentication, session approach, fallback or local authentication where applicable, inherited enterprise controls, logging and monitoring arrangements, periodic reconciliation and any approved limitations or exceptions.

**Estimated effort: 6–10 hours**

---

## B. SyOps Authentication and Session Management Content

Update the existing SyOps with operational procedures for user sign-in, sign-out and authentication support. Include normal and privileged authentication, step-up or reauthentication, thick-client sign-in, support impersonation, identity-provider outage handling, fallback or emergency authentication, session timeout and revocation, failed or ambiguous identity mapping, authentication-service failures, trust-material rollover, operational escalation and restoration of normal service.

**Estimated effort: 8–16 hours**

---

## C. Software Design and Authentication Specification

Extend the existing software or security design to define the application's identification and authentication architecture. Document approved identity providers and protocols, relying-party or client registrations, issuer and audience validation, subject and claim mapping, redirect and callback controls, token and assertion validation, authentication-context requirements, thick-client authentication, trusted server-side enforcement points, session binding and expiry, step-up or reauthentication triggers, secrets and certificate references, fallback or local authentication, and fail-secure behaviour when authentication evidence is invalid, stale or ambiguous.

**Estimated effort: 14–28 hours**

---

## D. Identification, Authentication and Session Control Implementation

Review the application against IA-02 requirements and implement any required improvements. Activities may include eliminating anonymous, shared or generic user access; integrating the approved enterprise identity provider; correcting relying-party or client configuration; validating token signatures, issuer, audience, expiry, nonce, state and authentication context; mapping each enterprise identity to one stable application account; enforcing authentication consistently across browser, thick-client, API, report, file, administrative, support and recovery paths; implementing stronger authentication for privileged or sensitive functions; improving session binding, timeout, sign-out and revocation; restricting local and fallback authentication; protecting redirects, callbacks and trust material; preventing implicit trust based on network location; controlling support impersonation; and removing obsolete authentication routes, registrations and trust anchors.

**Estimated effort: 36–96 hours**

---

## E. Test Documentation and Evidence

Extend the existing test documentation to demonstrate that identification and authentication controls operate correctly and cannot be bypassed. Testing should cover valid organisational users, users without application access, disabled identities, wrong issuer or audience, altered, expired or not-yet-valid tokens, invalid signatures, missing or ambiguous identity mappings, insufficient authentication strength, direct API and deep-link bypass attempts, thick-client manipulation, unauthenticated downloads, redirect and callback attacks, session fixation and replay, sign-out and revocation, role or account changes during active sessions, key rollover, identity-provider outage, fallback access, privileged reauthentication, support impersonation and authentication-event forwarding. Evidence should demonstrate end-to-end behaviour rather than merely showing the identity-provider login page.

**Estimated effort: 20–40 hours**

---

## F. IT Support and Service Documentation

Update the support documentation with procedures for operating and troubleshooting application authentication. Include identity-mapping failures, disabled-user issues, federation and token validation errors, authentication-context problems, sign-in and sign-out faults, stale sessions, callback or redirect errors, certificate and key expiry, identity-provider outages, fallback access, privileged authentication, support impersonation, local-account exceptions, reconciliation discrepancies and escalation of systemic authentication failures.

**Estimated effort: 8–16 hours**

---

## G. Release, Acceptance and Handover Evidence

Enhance the existing release and operational acceptance process with IA-02-specific checks. Confirm that the released application trusts only approved identity providers, production registrations and callback addresses are correct, token and assertion validation is active, identity mappings are unambiguous, all interactive access paths require authentication, privileged functions invoke the required authentication strength, session settings and sign-out operate correctly, application trust material is current and protected, authentication events reach central monitoring, and any local, fallback or product limitations have been documented and approved.

**Estimated effort: 8–16 hours**

---

## H. Project Management, Review and Assurance

Coordinate delivery of the IA-02 activities through the existing governance process. Activities include authentication gap analysis, organisational-user and interface review, workshops with enterprise identity, PAM, application support and security teams, identity-registration and trust-material coordination, design assurance, evidence tracking, identity reconciliation, exception and risk management, alignment with AC-02, AC-03, AC-06, IA-05, AC-17, AU-02, SI-04, SC-07 and CA-07 activities, approval coordination and final compliance review. Existing governance forums and artefacts should be reused rather than creating additional project documentation.

**Estimated effort: 8–16 hours**

---

# Revised Total Estimate

| Deliverable | Estimated effort |
|---|---:|
| SSP IA-02 content | **6–10 hours** |
| SyOps authentication and session management content | **8–16 hours** |
| Software design and authentication specification | **14–28 hours** |
| Identification, authentication and session control implementation | **36–96 hours** |
| Test documentation and evidence | **20–40 hours** |
| IT support and service documentation | **8–16 hours** |
| Release, acceptance and handover | **8–16 hours** |
| Project management, review and assurance | **8–16 hours** |
| **Total estimated application effort** | **108–238 hours** |

## Planning interpretation

A mature application with proven enterprise federation, stable identity mapping, standard authentication libraries, consistent authentication across all interfaces, effective session management and established security testing is likely to fall near the lower end of the estimate.

Applications with custom or legacy federation, thick-client authentication, local account stores, weak token validation, multiple access paths, privileged step-up requirements, offline capability, complex session behaviour, fallback authentication or poor identity reconciliation are more likely to fall toward the upper end.

The estimate excludes enterprise identity proofing and enrolment, authoritative workforce identity status, corporate directory and credential-service operation, enterprise MFA and federation platform operation, authenticator issuance and lifecycle management, managed Windows and VPN authentication, enterprise PAM and PKI platform operation, central identity threat detection and other inherited enterprise identification and authentication responsibilities.
