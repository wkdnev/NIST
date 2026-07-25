# CA-07 Continuous Monitoring — Application Actions

## Purpose

For an IT application, CA-07 means the application must maintain **ongoing awareness of its own security state**, identify material changes or weaknesses, assess whether application controls remain effective, and ensure that findings are acted upon.

This is broader than system monitoring under SI-04:

- **SI-04** focuses on detecting attacks, misuse, abnormal behaviour and failures through operational monitoring.
- **CA-07** focuses on continuing assurance that the application’s security controls, configuration, vulnerabilities, risks and evidence remain current and effective over time.

The enterprise may provide the corporate continuous-monitoring framework, SOC, SIEM, vulnerability scanners, endpoint detection, network monitoring, governance tooling, risk processes and reporting standards. Those capabilities are inherited. They do not, however, determine whether an application-specific role model remains appropriate, whether a newly introduced API bypasses authorisation, whether a supplier component is still supported, whether an application exception has expired, or whether a control described in the SSP still works as stated.

The application must therefore define its own monitoring scope, measures, assessment frequencies, triggers, owners, evidence sources, thresholds and corrective-action process.

NIST defines continuous monitoring as maintaining ongoing awareness of information security, vulnerabilities and threats to support risk-management decisions. NIST SP 800-137 describes a lifecycle of defining a strategy, establishing the programme, implementing it, analysing and reporting findings, responding to findings, and reviewing and updating the approach. CA-07 applies that concept at the system or application level.

> **Core principle:** an application is not secure merely because it passed an assessment at go-live. It must continue to demonstrate that its controls remain implemented, effective and appropriate as the application, threat environment and business use change.

---

## 1. Define an application-level continuous-monitoring strategy

The application should maintain a concise strategy describing:

- which application controls and risks require ongoing attention;
- what will be monitored or reassessed;
- the source of the evidence;
- the monitoring or assessment method;
- the frequency;
- event-driven triggers;
- the accountable owner;
- thresholds for action;
- reporting routes;
- escalation criteria; and
- how findings will be tracked to closure.

The strategy should be risk-based. Higher-impact, highly privileged, frequently changed or externally supplied components may require more frequent review than stable, low-complexity functions.

The strategy does not need to be a separate document. It can be included in the SSP CA-07 section, supported by the SyOps, risk register, service-management plan, assurance plan and normal SDLC records.

## 2. Maintain a current view of the application

Continuous monitoring depends on knowing what the application currently consists of.

The application should maintain and reconcile:

- system boundary;
- architecture;
- data flows;
- component inventory;
- baseline configuration;
- approved versions;
- interfaces;
- service identities;
- privileged roles;
- information types;
- suppliers;
- security dependencies;
- known exceptions; and
- recovery arrangements.

The application should detect when the SSP, architecture, inventory or other assurance record no longer reflects the deployed solution.

An inaccurate application description weakens every downstream monitoring and risk decision.

## 3. Identify the controls that require ongoing assessment

The application should identify which controls cannot be treated as “implemented once and forgotten”.

Examples include:

- access-control roles and record segregation;
- least privilege;
- separation of duties;
- application security configuration;
- baseline accuracy;
- component and dependency inventory;
- vulnerability and flaw remediation;
- logging and monitoring;
- authenticator and service-secret management;
- input validation;
- software and artefact integrity;
- encryption and information-at-rest protection;
- retention and deletion;
- backup and recovery;
- supplier support status;
- secure development testing;
- penetration-test findings;
- external-system restrictions; and
- privileged and support access.

The application should select suitable measures and evidence for each material control or control group.

## 4. Define meaningful measures

Measures should show whether a control remains implemented and effective, not merely whether an activity occurred.

Useful application measures may include:

- percentage of application components represented in the approved inventory;
- number of deployed versions differing from the approved baseline;
- unsupported components in production;
- critical and high vulnerabilities beyond target remediation dates;
- known weaknesses awaiting retest;
- privileged users without current approval;
- dormant or unused service identities;
- roles or permissions overdue for review;
- application events not reaching the central monitoring service;
- failed logging or forwarding tests;
- unauthorised or expired certificates, keys or tokens;
- production data present in non-production without approval;
- failed backup or restoration tests;
- retention or deletion failures;
- expired exceptions;
- unapproved interfaces or endpoints;
- releases completed without required security evidence; and
- repeat findings indicating ineffective root-cause correction.

Measures should be specific enough to drive action. “Security reviewed regularly” is not a useful measure.

## 5. Use both automated and manual monitoring

Automation should be used where it is reliable and proportionate, but CA-07 is not limited to tooling.

Automated evidence may include:

- vulnerability scan results;
- dependency and software-composition analysis;
- source-code and secret scanning;
- configuration comparison;
- deployment and pipeline checks;
- certificate-expiry monitoring;
- SIEM health and event-flow monitoring;
- package and artefact integrity checks;
- account and role reports;
- backup-job results;
- application health metrics;
- inventory reconciliation;
- policy-as-code results; and
- scheduled test execution.

Manual or semi-manual evidence may include:

- role and access reviews;
- architecture review;
- supplier support review;
- exception review;
- business-process and separation-of-duties review;
- sample transaction review;
- security design review;
- recovery exercises;
- review of operational incidents;
- review of penetration-test findings; and
- validation that the SSP remains accurate.

Automation should reduce effort and increase frequency, but it should not create false confidence where human judgement is required.

## 6. Define risk-based monitoring frequencies

The application should establish monitoring and assessment frequencies based on:

- information sensitivity;
- business impact;
- threat exposure;
- complexity;
- rate of change;
- privilege level;
- supplier dependence;
- history of findings;
- control volatility;
- ease of automation;
- legal or contractual requirement; and
- enterprise policy.

Examples of proportionate frequencies might include:

- continuous or daily health checks for event forwarding and critical integrations;
- per-build or per-release code, dependency and configuration checks;
- weekly or monthly vulnerability and certificate review;
- monthly or quarterly review of overdue findings;
- quarterly or six-monthly privileged-access review;
- annual or risk-triggered role and control review;
- annual recovery testing;
- risk-based penetration testing; and
- immediate review after a major incident or material change.

The exact frequencies should follow corporate policy where defined. The application’s responsibility is to apply and document them to its own controls and risks.

## 7. Define event-driven reassessment triggers

Monitoring should not rely only on a calendar.

The application should reassess affected controls after:

- significant code or configuration change;
- new interface or integration;
- product or dependency upgrade;
- architecture change;
- new information type or higher classification;
- new privileged function;
- change to identity or role design;
- supplier support change;
- new vulnerability or active exploitation information;
- security incident or near miss;
- penetration-test or assessment finding;
- unexpected baseline drift;
- significant business-process change;
- recovery or failover;
- merger, organisational or contract change;
- introduction of new analytics or export capability; and
- change to enterprise security services relied upon by the application.

The reassessment scope may be targeted where change-impact analysis demonstrates that unrelated controls remain unaffected.

## 8. Monitor configuration and baseline integrity

The application should confirm that the deployed state remains consistent with the approved CM-02 baseline and CM-06 configuration.

This should include, where applicable:

- application release version;
- thick-client package version;
- dependency set;
- database schema version;
- enabled modules;
- feature flags;
- security settings;
- logging configuration;
- API and integration endpoints;
- service identities;
- certificates;
- scheduled jobs; and
- privileged roles.

Differences should be investigated and either corrected or authorised through change control.

## 9. Monitor vulnerabilities, flaws and support status

The application should use enterprise vulnerability information but apply application-specific context.

The application team should:

- confirm that all application components and interfaces are within scanning or assessment scope;
- identify which findings apply to the application;
- monitor application code and dependencies;
- review supplier advisories;
- track unsupported or end-of-life components;
- prioritise findings using business and data impact;
- assign owners and target dates;
- verify remediation;
- retest material weaknesses; and
- monitor compensating controls where remediation is deferred.

A scanner result marked “closed” is not sufficient if the vulnerable application path remains exploitable.

## 10. Monitor access and privilege

The application should periodically confirm that application access remains appropriate.

This includes reviewing:

- business roles;
- project or data-partition membership;
- privileged users;
- support access;
- supplier access;
- emergency access;
- service identities;
- API scopes;
- database roles;
- dormant accounts or assignments;
- incompatible role combinations; and
- temporary access past its expiry.

The enterprise may provide account-review tooling, but the application must provide the business context needed to determine whether the access is still justified.

## 11. Monitor application logging and security visibility

The application should confirm that required events continue to be:

- generated;
- correctly timestamped;
- forwarded;
- parsed;
- correlated;
- retained;
- protected; and
- usable by security operations.

The application should identify:

- components that stop producing events;
- parsing failures;
- lost correlation fields;
- excessive or insufficient logging;
- unexpected diagnostic logging;
- sensitive information in logs;
- disabled alerts;
- stale monitoring rules; and
- changes that introduce new security-relevant events.

Monitoring the existence of a log file is not enough; the application should demonstrate investigative usefulness.

## 12. Monitor supplier and third-party components

Where commercial or supplier-controlled products form part of the application, the application should monitor:

- support status;
- security advisories;
- patch availability;
- vulnerability disclosures;
- software and dependency changes;
- licence or contract constraints;
- support access;
- end-of-life dates;
- changes to supported architecture;
- changes to remote or external connectivity;
- available assurance evidence; and
- remediation commitments.

Supplier responsibility does not remove application-owner accountability for understanding and managing the resulting application risk.

## 13. Monitor exceptions and compensating controls

Every application deviation or exception should have:

- a defined scope;
- owner;
- approval;
- compensating controls;
- monitoring requirements;
- review date;
- expiry date; and
- remediation, upgrade, isolation or retirement plan.

The application should identify:

- exceptions past review;
- compensating controls that are no longer operating;
- changed conditions that invalidate the original risk decision;
- exceptions affecting new components or data;
- duplicate or overlapping exceptions; and
- accepted risks with no active treatment plan.

Exceptions should not become permanent merely because they are repeatedly renewed.

## 14. Assess control effectiveness, not only control presence

CA-07 requires more than checking that a setting or document exists.

The application should periodically determine whether controls actually work.

Examples include:

- testing that unauthorised roles are denied;
- confirming removed access no longer works;
- testing that logging reaches the SIEM;
- verifying that disabled functions remain unavailable;
- checking that secrets can be revoked;
- restoring data from backup;
- confirming retention and deletion behaviour;
- testing failure when the identity or policy service is unavailable;
- validating that an alert is actionable;
- checking that a repaired vulnerability cannot still be exploited; and
- testing that a thick client cannot bypass server-side controls.

Control-effectiveness testing should be proportionate and may reuse normal SDLC, operational acceptance, recovery and security-testing activities.

## 15. Analyse findings in application context

The application should interpret monitoring results using:

- information sensitivity;
- affected business process;
- user and service privilege;
- exploitability;
- exposure;
- existing compensating controls;
- number of affected users or records;
- integrity and safety consequences;
- supplier constraints;
- recovery implications; and
- regulatory or contractual impact.

Enterprise severity ratings are an important input, but the application owner should determine the actual application risk.

## 16. Maintain one authoritative findings view

The application should avoid fragmented and conflicting findings lists.

Findings from:

- vulnerability scans;
- penetration tests;
- code analysis;
- access reviews;
- recovery tests;
- audits;
- incidents;
- configuration checks;
- supplier advisories;
- control assessments; and
- operational monitoring

should be linked or consolidated into an authoritative application risk, defect, vulnerability, POA&M or corrective-action record.

Each material finding should include:

- source;
- affected component or control;
- risk and severity;
- owner;
- target date;
- action;
- status;
- evidence;
- exception or acceptance where applicable;
- retest requirement; and
- closure approval.

## 17. Respond to findings

Monitoring without response is not effective continuous monitoring.

The application should:

- triage findings;
- assign accountable owners;
- define remediation or treatment;
- set risk-based target dates;
- apply interim controls where necessary;
- escalate overdue or high-impact issues;
- update the risk register;
- coordinate change and release;
- retest corrections;
- record accepted risk;
- communicate material changes to stakeholders; and
- update the SSP or addendum where the control implementation changes.

Critical findings may require restriction of a feature, interface, identity or release until the risk is controlled.

## 18. Verify closure

A finding should not be closed merely because work was reported as complete.

Closure should demonstrate:

- the affected component or control was corrected;
- the deployed environment contains the correction;
- the original weakness can no longer be reproduced;
- no unacceptable regression was introduced;
- associated documentation and baseline records were updated;
- compensating controls were removed or revised where appropriate; and
- evidence is retained.

Independent verification should be used for material findings where required by risk or corporate policy.

## 19. Report application security posture

The application should provide a concise, periodic view of its current security posture.

A useful posture report may include:

- material changes since the previous report;
- current application baseline and support status;
- critical and high vulnerabilities;
- overdue remediation;
- significant access or privilege findings;
- monitoring and logging health;
- control tests completed and failed;
- open exceptions;
- supplier risks;
- incidents and lessons;
- recovery-test status;
- expired evidence or reviews;
- risk trend;
- decisions required; and
- planned assurance activity.

The report should be suitable for the application owner and governance stakeholders and should avoid overwhelming them with raw scanner or SIEM output.

## 20. Review and improve the monitoring approach

The application should periodically assess whether its monitoring strategy remains useful.

The review should consider:

- measures that do not support decisions;
- duplicated evidence;
- excessive manual effort;
- blind spots;
- recurring findings;
- false assurance from unreliable tools;
- controls that change more frequently than expected;
- new automation opportunities;
- new threats;
- changes to enterprise services;
- changes to application architecture; and
- feedback from assessors, operations and incident response.

The monitoring strategy, measures and frequencies should be updated when they no longer provide timely or meaningful assurance.

## 21. Preserve traceability to the SSP and SDLC

Continuous-monitoring evidence should demonstrate that the implementation described in the SSP remains true.

The application should be able to trace:

- control requirement;
- implementation;
- responsible owner;
- evidence source;
- latest assessment;
- finding;
- remediation;
- retest; and
- current status.

This traceability should be achieved through existing SSP, risk, SDLC, test, release and service-management artefacts rather than a disconnected parallel evidence library.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate scanning, SIEM, identity, risk, change and service-management capabilities. They exclude enterprise platform engineering, SOC operations and major remediation work.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Define an application continuous-monitoring strategy** | Select the application controls, risks, measures, evidence sources, owners, frequencies, triggers, thresholds and reporting routes that require ongoing assurance. | Record the strategy in the **SSP CA-07 section**, supported by the existing **SyOps**, **security-management plan**, **risk register** or **service-management plan**. | **8–16 hours** |
| **2. Maintain current application scope and assurance records** | Reconcile the SSP, architecture, component inventory, baseline, interfaces, data flows, roles, suppliers and exceptions with the deployed application. | Use the existing **SSP**, **architecture**, **CM-02 baseline**, **CM-08 inventory**, **interface records** and **release documentation**. Record discrepancies in normal **change or risk records**. | **8–20 hours initially; 3–8 hours per review** |
| **3. Define practical control-effectiveness measures** | Select a small set of measures showing whether material controls remain effective, such as baseline drift, overdue vulnerabilities, access-review status, logging health and expired exceptions. | Include the measures and thresholds in the **SSP CA-07 section**, **service review pack**, **security dashboard definition** or **risk-management plan**. | **6–12 hours** |
| **4. Establish monitoring and reassessment frequencies** | Apply corporate frequencies and add application-specific frequencies based on risk, change rate, privilege, complexity and supplier dependence. | Record frequencies in the **SSP**, **assurance schedule**, **service calendar**, **SyOps** or normal **governance plan**. | **3–6 hours** |
| **5. Define material-change and incident triggers** | Identify events that require targeted reassessment, such as major releases, new interfaces, identity changes, incidents, new vulnerabilities or supplier changes. | Record triggers in the **SSP**, **SDLC**, **change-impact template**, **incident procedure** or **SyOps**. | **4–8 hours** |
| **6. Monitor baseline, configuration and component accuracy** | Compare deployed versions, dependencies, schemas, settings, modules and endpoints with the approved baseline and inventory. | Use existing **deployment reports**, **release manifests**, **configuration checks**, **component inventory**, **post-implementation reviews** and **service-review evidence**. | **8–20 hours initially; 3–8 hours per review** |
| **7. Monitor vulnerabilities, flaws and support status** | Review applicable scan findings, code and dependency results, supplier advisories, unsupported components, target dates and remediation verification. | Maintain the authoritative status in the normal **vulnerability record**, **risk register**, **defect tracker**, **POA&M** or **release evidence pack**, referenced from the SSP. | **4–12 hours per month or review cycle** |
| **8. Monitor access and privilege** | Review business roles, privileged users, service identities, API scopes, database roles, temporary access and incompatible assignments. | Use established **access-review records**, **role matrix**, **service-account register**, **PAM evidence**, **service reviews** and **risk records**. | **6–16 hours per review** |
| **9. Monitor application logging and security visibility** | Verify that required events are generated, forwarded, parsed, correlated and usable and that failures are visible. | Capture results in existing **SI-04/AU-02 test evidence**, **operational acceptance records**, **SIEM onboarding record**, **service review** or **support ticket**. | **4–10 hours per review** |
| **10. Review supplier, exception and compensating-control status** | Confirm supplier support, advisories, contract constraints, exception dates, compensating controls and remediation plans remain current. | Use the existing **supplier record**, **risk register**, **application addendum**, **contract review**, **problem record** or **service review**. | **4–10 hours per review** |
| **11. Perform targeted control-effectiveness tests** | Reuse access-control tests, monitoring tests, recovery exercises, configuration checks, retention tests and remediation retests to confirm controls still work. | Add cases to the normal **security test plan**, **operational acceptance test**, **recovery test**, **release test report** or **assurance report**. | **12–32 hours per assessment cycle** |
| **12. Maintain one authoritative findings and action view** | Consolidate or link findings from scans, tests, incidents, reviews and suppliers, with owner, target date, treatment, evidence and retest status. | Use the existing **risk register**, **defect/vulnerability tracker**, **POA&M**, **corrective-action register** or **service-management tool**. | **6–12 hours initially; 2–6 hours per update cycle** |
| **13. Report current application security posture** | Produce a concise summary of changes, material findings, overdue actions, exceptions, control health, supplier status and decisions required. | Include the summary in the normal **application service review**, **security review**, **risk committee pack**, **SSP status update** or **authorisation evidence**. | **4–8 hours per report** |
| **14. Verify remediation and update assurance records** | Retest material corrections, confirm deployment, close findings with evidence and update the SSP, baseline, inventory or addendum where necessary. | Retain evidence in the existing **test report**, **change record**, **release pack**, **risk record**, **POA&M** and **SSP change history**. | **4–12 hours per material finding, excluding remediation** |
| **15. Periodically review and improve the monitoring strategy** | Review blind spots, duplicated effort, recurring findings, measure usefulness, frequencies and automation opportunities. | Record decisions in the normal **annual security review**, **service-improvement plan**, **risk review**, **SSP review** or **governance minutes**. | **6–12 hours per annual review** |

### Indicative total

For a typical internal application with established enterprise tooling and reasonably mature SDLC and service-management processes, initial application setup is commonly around **90–180 hours**.

Ongoing application effort is commonly around **20–50 hours per month**, averaged across recurring reviews, reporting, triage and evidence maintenance. This excludes actual remediation engineering and may be substantially lower for a small, stable application or higher for a complex, frequently changing, highly restricted or supplier-dependent solution.

The estimates should not be added mechanically where work overlaps. Continuous monitoring should reuse evidence already produced by release management, vulnerability management, access review, service review, security testing and recovery exercises.

---

## Suggested document placement

To avoid creating disconnected evidence, continuous-monitoring information should normally be distributed across existing application and SDLC artefacts:

- **SSP:** CA-07 strategy, controls monitored, measures, frequencies, triggers, ownership, reporting, inherited services and limitations.
- **ConOps or SyOps:** operational monitoring, support responsibilities, escalation, supplier interaction, failure handling and control-maintenance activities.
- **Security architecture:** monitoring points, evidence flows, trust dependencies and controls requiring periodic validation.
- **Risk register:** material findings, accepted risks, supplier risks, overdue treatment and changes in residual risk.
- **Application addendum:** deviations, non-standard frequencies, missing evidence, compensating controls and review dates.
- **CM-02 baseline and CM-08 inventory:** current components, versions, environments and support status.
- **CM-06 configuration records:** approved security settings and configuration-verification results.
- **Access and role records:** current user, privileged and service access and review outcomes.
- **Vulnerability and defect tooling:** findings, owners, target dates, remediation and retest status.
- **SDLC and release evidence:** code, dependency, configuration, security and regression-test results.
- **Operational acceptance records:** confirmation that monitoring, logging, recovery and support controls work for the released version.
- **Service reviews:** posture summaries, trends, exceptions, overdue findings and decisions.
- **Incident records:** lessons, new monitoring requirements and corrective actions.
- **Recovery test reports:** control behaviour and secure restoration evidence.
- **Supplier records:** support status, advisories, commitments and assurance evidence.
- **Post-implementation and change reviews:** confirmation that material changes did not invalidate controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- the corporate continuous-monitoring policy and governance framework;
- central SOC and SIEM operations;
- enterprise EDR and network monitoring;
- enterprise vulnerability-scanning platforms;
- corporate threat intelligence;
- central identity and PAM monitoring;
- infrastructure and operating-system configuration monitoring;
- enterprise risk, POA&M and service-management tooling;
- corporate control-assessment methodology;
- enterprise assessment and authorisation governance;
- central time synchronisation;
- organisation-wide dashboards and executive reporting;
- corporate incident-management processes;
- enterprise supplier and contract governance; and
- shared control evidence for Windows EUC, servers, networks, hypervisors and managed platforms.

The application team must still:

- define what application-specific controls and risks require continuing assurance;
- supply application context;
- ensure components and interfaces are in scope;
- interpret results;
- maintain application-specific measures;
- respond to findings;
- verify corrections; and
- keep the SSP and related application evidence current.

> **Key dividing line:** the enterprise provides the monitoring framework, shared tooling and oversight; the application continually demonstrates that its own controls, components, risks and evidence remain current and effective.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Security and Privacy Controls for Information Systems and Organizations**, CA-07 Continuous Monitoring.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Assessing Security and Privacy Controls in Information Systems and Organizations**, CA-07 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-137, Information Security Continuous Monitoring for Federal Information Systems and Organizations**.
4. National Institute of Standards and Technology, **NIST SP 800-137A, Assessing Information Security Continuous Monitoring Programs: Developing an ISCM Program Assessment**.
5. National Institute of Standards and Technology, **NIST Risk Management Framework — Monitor Step guidance**.
