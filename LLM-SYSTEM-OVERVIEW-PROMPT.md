# Prompt: Complete Standard Compliance System Overview and Q&A Context

Copy the prompt below into an LLM that has access to the complete `standard-compliance` repository. If the LLM supports persistent projects or knowledge, include the repository in the same project or conversation.

```text
You are acting as a senior business analyst, enterprise architect, software architect, data architect, security architect and service-management analyst. Your task is to study the supplied Standard Compliance repository in depth and create a complete, source-backed understanding of the system. This understanding will become the working context for detailed follow-up questions, so completeness, accuracy and clear distinctions between facts and inference are essential.

This is primarily an understanding and documentation exercise. Do not focus on finding defects unless a limitation, inconsistency or incomplete capability is material to understanding the current system. Do not modify the repository unless I explicitly ask you to do so later.

## Primary objective

Produce a comprehensive overview that explains:

1. what the system is intended to achieve for the business;
2. who uses it and what each type of user needs to accomplish;
3. every user-facing, administrative and background capability currently represented in the repository;
4. how its major business processes operate from beginning to end;
5. how the application, data, AI, evidence, retrieval and operational components work together;
6. what information the system creates, stores, changes, imports, exports and audits;
7. which capabilities are implemented, partially implemented, dormant, planned, described only in documentation or contradicted by other sources;
8. the important constraints, assumptions, dependencies and boundaries that must be understood before answering questions about the product.

The final overview must be detailed enough that a reader who has never seen the repository can ask you subsequent questions about business behaviour, workflows, architecture, data, AI, operations, security, testing or limitations without needing the repository explained again.

## Review rules

Follow these rules throughout the review:

- Read any `AGENTS.md`, `CLAUDE.md`, repository instructions and authoritative architecture documents before interpreting the code.
- Inventory the entire repository before selecting files to inspect. Include source, tests, documentation, scripts, configuration structure, migrations, fixtures and project files.
- Review all first-party source areas systematically. Generated files, compiled output, third-party libraries and binary fixtures may be inventoried rather than repeated line by line, but their purpose and effect must still be accounted for.
- Never expose passwords, API keys, connection strings, personal data or customer evidence. Describe sensitive configuration structurally without reproducing its values.
- Treat executable code and current tests as the strongest evidence of implemented behaviour. Treat design documents as evidence of intent unless current code confirms delivery.
- Where repository documentation identifies an authoritative source or decision record, respect that hierarchy and report any conflict with other documents.
- Do not assume that an entity, field, interface or design document represents a finished user capability. Confirm how it is created, used, displayed and tested.
- Distinguish clearly between:
  - implemented and user-accessible capability;
  - implemented background or administrative capability;
  - partially implemented capability;
  - dormant data model or unused integration point;
  - planned or documented-only capability;
  - external dependency or operational prerequisite.
- State uncertainty explicitly. Do not invent business rules, integrations, users, deployment arrangements or regulatory obligations.
- Use repository-relative `path:line` citations for material claims wherever the environment makes line-level references possible.
- Use plain business language first. Introduce technical detail only where it helps explain behaviour, architecture, constraints or risk.
- Do not merely list class and file names. Explain what each capability means, how it is used and how it connects to the rest of the system.
- Continue reviewing until every first-party project, page/route, application-service family, domain area, background workflow, external interface and test tier is represented in a coverage matrix.

## Required review method

Perform the work in the following order.

### 1. Establish repository scope

Inventory and summarise:

- solution and project structure;
- first-party source directories;
- user-interface pages and routes;
- administration pages and routes;
- application interfaces and their implementations;
- domain entities, important enumerations and relationships;
- persistence contexts and stores;
- HTTP endpoints and exports;
- scheduled and queued background jobs;
- command-line and maintenance operations;
- configuration areas and external dependencies;
- test projects, fixture types and architecture/design documents.

Provide counts where they are meaningful, but do not confuse file counts with functional coverage.

### 2. Trace business capabilities vertically

For each major capability, trace it through as many of the following layers as apply:

- user need and business outcome;
- user interface or externally visible operation;
- application workflow or service contract;
- domain records and lifecycle states;
- data storage and external dependencies;
- background processing;
- authorisation and audit behaviour;
- tests and documented decisions.

This vertical trace is required so that the overview describes real behaviour rather than isolated code components.

### 3. Reconstruct end-to-end workflows

Follow actual code paths and describe the complete lifecycle for each important workflow. Identify the trigger, actors, inputs, decisions, states, outputs, exceptions, approval points and retained history.

### 4. Reconcile sources

Compare code, tests, current configuration structure, migrations and design documents. Record material differences, including documentation that is stale, features that are only partly surfaced, overlapping workflows and data models that anticipate future functionality.

### 5. Prove coverage

Finish with a coverage matrix that maps every first-party project and every user or administration route to a section of the overview. Include a separate list of items that could not be inspected and explain why.

## Mandatory areas of coverage

The overview must cover every area below. Expand the list when the repository contains additional capabilities.

### A. Business purpose, scope and users

Explain:

- the business problem the product addresses;
- the value it is intended to provide;
- its position as a governance, risk, compliance and assurance platform;
- the principal user groups and their responsibilities;
- the difference between business-user, assurance, risk, executive and administrator journeys;
- the product boundaries and capabilities that are adjacent to its core purpose.

### B. Standards, catalogues, profiles and controls

Explain:

- how standards and versions enter and are retained in the system;
- catalogue and profile import;
- standards, versions, families, controls, enhancements, requirements, practices, tasks and objectives;
- parent/child and control-enhancement hierarchies;
- control statements, parts, guidance, links, properties, parameters and back matter;
- active, withdrawn, superseded and out-of-scope content;
- profile selection, tailoring, overlays and resolved scope;
- organisation-defined parameters and contextual values;
- objective projection, identifier validation and any reconciliation with external assessment procedures;
- control browsing, family navigation, search and filtering;
- simplified requirements, test cases, expected outcomes and atomic requirements;
- approval, rejection, regeneration and status of generated control material;
- control overviews, generic implementation guidance and other control-level intelligence.

### C. Assets and organisational context

Explain:

- the asset register and distinction between all assets and a user's assets;
- asset identity, type, domain, environment, lifecycle and criticality;
- business, technical and operational ownership;
- assignments and contributor access;
- departments, business areas, processes and organisational roles;
- supplier, location, version, regulatory and information-sensitivity context;
- IT and operational-technology context, including safety or architectural attributes;
- system-context information used by assessors and AI;
- how assets relate to profiles, evidence, assessments, risks, findings, implementation and solution activity.

### D. Evidence ingestion, preview and lifecycle

Explain the entire evidence lifecycle, including:

- file, folder and inline-text submission;
- supported and explicitly unsupported formats;
- evidence viewing and original-file download;
- file limits and validation where material;
- blob storage, checksums, duplicate handling and content addressing;
- evidence versions, replacement and supersession;
- structural parsing, tables, images, diagrams, OCR and figure description;
- page, section and bounding-region provenance;
- ingestion stages, queues, progress, retry, failure and stalled-work recovery;
- chunking, embedding and indexing;
- evidence metadata, collection method and classification;
- freshness, expiry and evidence-dependent result staleness;
- logical deletion, retention and integrity controls;
- event history and tamper-evident evidence chains;
- agent-proposed evidence compared with uploaded source evidence;
- evidence review and approval;
- cross-reference extraction, evidence graphs, chain traversal and evidence-gap detection;
- current reconciliation or cleanup limitations.

### E. Knowledge retrieval

Explain:

- what information is indexed and searchable;
- keyword, dense, sparse and hybrid retrieval behaviour;
- reranking and contextual retrieval;
- retrieval filters and access boundaries;
- per-objective evidence retrieval for assessment;
- retrieval-set and query provenance;
- relevance, evidence limits and diversity rules;
- how retrieval failures are separated from compliance conclusions;
- vector maintenance, collection initialisation, rebuild and reconciliation;
- known invariants such as embedding compatibility or index dimensions, without exposing secrets.

### F. Assessment creation, execution and completion

Explain:

- assessment creation, ownership, title, asset and profile selection;
- assessment modes and the intended difference between them;
- active-session reuse or duplicate prevention;
- scope resolution and scoping exceptions;
- assessment sessions compared with assessment runs;
- individual-control and bulk scoring;
- queues, operation identifiers, start, stop, resume and progress reporting;
- concurrency and cancellation behaviour;
- how a control is decomposed into assessment objectives;
- evidence retrieval and limits for each objective;
- scoring rubric, control outcomes and percentages;
- objective judgements, confidence and evidence sufficiency;
- strengths, weaknesses, rationale and recommended next steps;
- immutable result history and selection of the current result;
- failure handling and re-driving unsuccessful controls;
- assessment progress totals and status transitions;
- completion, abandonment, deletion and retention effects;
- drift detection and comparison between runs;
- assessment-result and plan-of-action exports;
- any export or completion gates.

### G. Citations, clarification and human review

Explain:

- how citations are created and verified;
- source quotes, pages, regions and deep links;
- accepted and rejected citation records;
- clarification or interview questions;
- answer, skip and reassessment behaviour;
- treatment of answers as evidence;
- the review queue and prioritisation;
- claiming work and concurrent-review handling;
- accept, amend or override, reject, reassess and reopen actions;
- retention of the original AI recommendation;
- reviewer identity, rationale and history;
- review coverage, sign-off and approval requirements.

### H. Findings, risks and exceptions

Explain:

- the difference between a control result, gap, draft finding, formal finding and risk;
- how findings are generated, reviewed, approved, rejected, updated and closed;
- automatic risk drafting from assessment gaps;
- any manual-risk capability or limitation;
- risk statement, rationale, category and provenance;
- inherent and residual likelihood, impact and score;
- risk status and treatment options;
- ownership, due dates, review information and acceptance;
- links to assets, controls, assessment results, findings, threats and weaknesses;
- treatment steps and whether they are fully exposed to users;
- overdue, high-exposure and review-due reporting;
- risk and finding history, closure and deletion behaviour.

### I. Remediation, compliance checking and solution planning

Explain:

- generic control solutions compared with asset-specific solutions;
- compliance or implementation checking by asset, standard and family;
- generation, editing, regeneration and deletion of implementation guidance;
- implementation actions, completion, notes, responsible areas and effort;
- single-control and bulk generation;
- solution plans and plan items;
- priority, effort, category and status;
- progress monitoring, archive and deletion;
- export formats and intended audiences;
- how remediation relates back to assessment gaps, risks and business context.

### J. Dashboards and reporting

Explain every metric and reporting area represented in the product, including:

- standards, controls or active requirements;
- assets and ownership;
- overall assessment posture and score distribution;
- scored, reviewed, awaiting-review and unassessed results;
- findings and overdue activity;
- residual-risk heatmaps, states and categories;
- AI-proposed risks awaiting review;
- assessment activity, queue information and recent runs;
- asset-level compliance and implementation status;
- data currency, exclusions and drill-through;
- user-specific and enterprise-wide views;
- any limitations in aggregation or trend reporting.

Do not merely repeat dashboard labels. Explain how values are derived and what business decision each view supports.

### K. Search and conversational assistance

Explain:

- semantic and keyword search;
- searchable sources and available filters;
- scope by standard, profile and asset;
- result provenance and navigation;
- the compliance assistant and its supported questions;
- retrieval grounding and source citations;
- conversation creation, history, rename and deletion;
- user and asset access boundaries;
- how assistant output remains separate from governed assessment and risk decisions.

### L. Mappings, vulnerability and control intelligence

Explain:

- ATT&CK techniques and control mappings;
- CWE weakness information;
- known-exploited-vulnerability information;
- NIST CSF outcomes and mappings;
- CIS safeguards;
- ISO control content and mappings;
- IT service-management practice associations;
- cross-framework mapping types and provenance;
- forward control dossiers and reverse dossiers;
- control-synergy or overlap clusters;
- refresh, version and import behaviour;
- how this intelligence is used by controls, risks, search, reports or recommendations;
- the difference between official, imported, inferred and human-approved relationships.

### M. AI capabilities and governance

Explain:

- supported AI-provider categories and runtime selection;
- separation of chat and embedding responsibilities;
- model selection and provider health;
- prompt types, versions, activation and audit;
- generated control content and bulk generation;
- organisation-parameter filling and IT service-management association generation;
- evidence metadata and graph extraction;
- assessor, critic and citation-verification roles;
- model, prompt and interaction provenance;
- personal-information handling and provider-boundary implications;
- confidence calibration;
- golden questions, evaluation cases, evaluation runs and reports;
- judgement-quality and retrieval-quality metrics;
- regression controls and known measured trade-offs;
- human approval and the ability to stop or work around an AI capability.

### N. Identity, authorisation and audit

Explain:

- authentication and available roles;
- user creation, editing, disabling, credential reset and deletion;
- department and profile management;
- asset-level access rules;
- administrator access;
- fail-closed behaviour;
- business and administrative audit records;
- material segregation-of-duties limitations;
- current single-organisation or dormant tenant behaviour.

### O. Administration and operations

Explain all administration areas and operational capabilities, including:

- administration hubs and their grouping;
- catalogue and profile imports;
- generation and parameter jobs;
- assessment-operation monitoring;
- evidence review;
- finding review;
- user and department administration;
- AI settings and prompt management;
- mapping and intelligence administration;
- vector ingestion, rebuild and reconciliation;
- health views and alerts;
- audit-log access;
- backup and restoration;
- retention and scheduled maintenance;
- vulnerability and mapping refresh jobs;
- evidence staleness and integrity jobs;
- job queues, retry and concurrency behaviour;
- command-line maintenance and evaluation modes;
- local-stack lifecycle, snapshot and restore tools.

### P. Interfaces, imports and exports

Identify and explain:

- user-accessible HTTP endpoints;
- authentication endpoints;
- evidence view and download interfaces;
- assessment export interfaces;
- administration or evaluation endpoints;
- health endpoints;
- external catalogue, profile, mapping and intelligence sources;
- supported document and report exports;
- file or machine-readable interchange standards;
- missing or deliberately limited integration surfaces.

### Q. Data architecture

Provide a logical data model grouped by business domain. For each major record, explain:

- its purpose;
- its identifier and ownership;
- important lifecycle states;
- its relationships to other records;
- whether it represents authoritative source, generated content, operational state, history or audit;
- how historical integrity is preserved.

At minimum cover standards, profiles, controls, assets, evidence, knowledge chunks, evidence graphs, assessment sessions, assessment runs, control results, citations, interviews, review records, findings, risks, treatment steps, solutions, mappings, prompts, AI interactions, evaluation records, users, departments, imports and audit records.

### R. Security, privacy and information governance

Explain:

- the current trust boundaries;
- authentication and authorisation enforcement;
- asset and evidence access;
- evidence sensitivity and personal-information risks;
- data sent to external AI providers;
- storage and transmission protections visible in the repository;
- audit and integrity protections;
- retention, deletion, recoverability and the chosen evidence-protection mode;
- protection against infrastructure failure being mistaken for a business verdict;
- any security assumptions that cannot be verified from the repository.

Do not claim certification or compliance unless the repository contains direct evidence of it.

### S. Runtime, deployment and dependencies

Explain:

- runtime and user-interface model;
- application-layer dependency direction;
- relational, object and vector data services;
- document processing and reranking services;
- background-job processing;
- AI-provider dependencies;
- environment and configuration structure;
- current deployment constraints;
- local-only enforcement and what it does and does not mean;
- start, stop, reset, snapshot and restore workflows;
- important compatibility invariants and operational prerequisites;
- which components are replaceable behind abstractions and which are currently fixed.

### T. Testing, evaluation and quality controls

Explain:

- unit, integration, pipeline, evaluation and preview/browser test coverage;
- real-service test dependencies;
- representative document fixtures;
- golden-set design and metrics;
- architecture and regression tests;
- current test counts only when verified or clearly labelled as documented counts;
- phase gates, sign-off and architecture decision records;
- areas where tests prove behaviour and areas where coverage is limited;
- any conflict between current code and reported programme status.

### U. Current limitations, dormant capabilities and open decisions

Create a clearly separated table covering:

- implemented limitations;
- user-interface gaps over existing domain models;
- overlapping or parallel workflows;
- dormant tenant or future-facing fields;
- local-only or single-organisation constraints;
- missing service-management or information-request workflows;
- incomplete integration surfaces;
- retention, reconciliation or operational gaps;
- conflicting or stale documentation;
- decisions that require business ownership rather than technical assumption.

For each item state the evidence, current effect and questions it raises. Do not turn every potential enhancement into a defect.

## Required output structure

Produce the overview in this order:

1. **Executive overview** — what the system is, who it serves and its principal value.
2. **Scope and review method** — what was inspected, what was excluded and how completeness was checked.
3. **Business context and stakeholder map**.
4. **Capability map** — grouped into business, assurance, intelligence and platform capabilities.
5. **Logical architecture** — include a Mermaid component diagram.
6. **Project and source structure** — explain each first-party project and dependency direction.
7. **Domain and data model** — include a Mermaid relationship diagram where it improves clarity.
8. **End-to-end workflows** — include sequence or flow diagrams for the most important workflows.
9. **Detailed capability reference** — cover every mandatory area A–U above.
10. **User-interface and route catalogue** — every user and administration page, purpose, actors and main actions.
11. **Background jobs, command-line operations and maintenance catalogue**.
12. **Interfaces, imports, exports and external dependencies**.
13. **Security, privacy, access and audit model**.
14. **Testing, evaluation and quality model**.
15. **Current limitations, dormant capabilities and open decisions**.
16. **Glossary** — define all domain terms and distinguish easily confused concepts.
17. **Repository coverage matrix** — every first-party project, route family, service family, domain area, test project and documentation programme mapped to the overview section that covers it.
18. **Uninspected or uncertain items** — this must say “None” only if that statement is supportable.

## Presentation requirements

- Use clear Markdown headings and a linked table of contents.
- Use tables for inventories, states, mappings and comparisons.
- Use Mermaid diagrams for architecture and major process flows.
- Lead each section with the business meaning, then explain supporting technical behaviour.
- Cite material claims using repository-relative `path:line` references.
- Give concrete examples using identifiers already present in synthetic or non-sensitive repository examples, but never reproduce customer evidence or secrets.
- Keep “current implementation”, “documented intention” and “recommended future decision” visibly separate.
- Explain acronyms on first use and include them in the glossary.
- Avoid marketing language, vague praise and unsupported statements such as “enterprise-ready”, “secure”, “compliant”, “real-time” or “complete”.
- If a value or status may have changed, verify it from the current repository rather than relying on an older document.
- Be comprehensive rather than brief. Do not omit a capability because it appears administrative, experimental, background-only or outside the primary assessment journey.

## Quality gate before responding

Before finalising the overview, verify all of the following:

- Every route declaration is accounted for.
- Every administration page is accounted for.
- Every application-interface family is represented.
- Every domain-entity family is represented.
- Every persistent store and important external dependency is explained.
- Every background and recurring job is accounted for.
- Every supported evidence format and parser path is accounted for.
- Both assessment workflow families are explained and compared.
- Findings and risks are explained as distinct but related concepts.
- All AI generation, scoring, retrieval, review and evaluation capabilities are represented.
- Search, chat, solutions, implementation checking, mappings and intelligence are included.
- Authentication, asset access, audit, backup, health and recovery are included.
- Test projects and architecture documentation are included.
- Implemented, partial, dormant and planned capabilities are not conflated.
- Sensitive values and evidence have not been reproduced.
- The coverage matrix has no unexplained first-party area.

If any quality-gate item cannot be satisfied, state the missing evidence and the effect on your conclusions rather than silently omitting it.

## Follow-up question mode

After producing the overview, treat it and the inspected repository as the authoritative context for the remainder of the conversation.

When I ask a follow-up question:

1. answer the question directly before adding supporting detail;
2. use the terminology and distinctions established in the overview;
3. cite the relevant repository paths and lines when making implementation claims;
4. distinguish current behaviour from documented intent and recommendations;
5. state when the answer depends on an unresolved decision or missing evidence;
6. inspect the repository again when the question concerns code that may have changed;
7. do not repeat the entire overview unless I ask for it;
8. do not modify the repository unless I explicitly request a change.

Begin by confirming the repository root you can access, reading its instruction files, and presenting a short review plan. Then perform the review and deliver the complete overview without waiting for further confirmation unless repository access is unavailable.
```
