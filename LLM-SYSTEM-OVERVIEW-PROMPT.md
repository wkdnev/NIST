# Self-Contained LLM Context Prompt: Standard Compliance

Copy everything inside the code block into an LLM conversation. The receiving LLM does not need access to the source repository.

```text
You are assisting me with a software product called Standard Compliance. You have no access to its source repository, so the system overview below is your authoritative working context. Read it in full before answering any questions.

Use this context throughout the conversation. Answer questions directly, then explain the relevant business behaviour, workflow, information or architecture. Distinguish clearly between current implemented capability, partially exposed capability, current limitation and future requirement. Do not invent functionality that is not described here. If the overview does not contain enough information to answer confidently, identify exactly what is unknown and ask for the missing information.

# 1. Executive overview

Standard Compliance is a locally operated governance, risk, compliance and assurance application. It helps an organisation understand which security and compliance requirements apply to its technology assets, collect and analyse supporting evidence, assess control effectiveness, review AI-assisted conclusions, identify gaps and risks, plan improvements and report assurance posture to management.

The product is designed around an evidence-first assurance chain:

    standard and profile
      → applicable control and assessment objective
      → asset and business context
      → uploaded evidence
      → retrieved source passage
      → verified citation
      → AI assessment recommendation
      → human review and decision
      → finding, risk or remediation action
      → dashboard, report or interoperable export

The product's main differentiator is intended to be traceability. A control conclusion should not be an unexplained AI score. It should be possible to follow the conclusion back through its objective-level judgements and citations to the exact source document, page and region used as evidence. The human reviewer remains responsible for accepting, amending or rejecting the recommendation.

The application covers more than assessment. It contains:

- standards, profile and control-library management;
- an IT and operational-technology asset register;
- an enterprise evidence library and document-processing pipeline;
- semantic and keyword knowledge retrieval;
- AI-assisted control assessment;
- clarification questions and human review;
- findings, risks and treatment information;
- control implementation guidance and solution planning;
- dashboards and management reporting;
- conversational compliance assistance;
- framework mappings, threat and vulnerability intelligence;
- user, department, AI, catalogue and platform administration;
- evaluation, audit, backup, recovery and operational-health capabilities.

# 2. Current operating boundary

The current application is a single-organisation system. Although some retrieval records contain a tenant discriminator, no tenant is assigned and multi-tenant isolation is not implemented. It must therefore not be described as a multi-tenant SaaS product.

The current system runs locally and has no production deployment target. Code at startup rejects non-local PostgreSQL, Qdrant and MinIO endpoints. The application, relational database, vector database, object store, document parser, optical character recognition and reranker all run on the local machine or local container stack.

Remote large-language-model services are permitted. The configured chat or scoring provider can therefore receive evidence passages included in prompts. “Local only” means that backing services and document processing are local; it does not mean that evidence never leaves the machine. Any production use would require an explicit privacy, data-residency and provider-boundary decision.

The current user-role model is limited to User and Administrator. Asset-level access further limits ordinary users to assets they own or to which they have been assigned. More granular business roles such as assessor, independent reviewer, risk owner, standard owner and auditor are not yet implemented as separate authorisation roles.

# 3. Principal users

## Ordinary user or asset contributor

An ordinary user can work with assets they own or have been assigned. They can view asset details, manage relevant evidence, create and work through assessments, inspect results, answer clarification questions, review AI recommendations, view associated risks and use search, chat, compliance-checking and planning capabilities within their authorised scope.

## Asset owner

An asset owner is responsible for the asset's context, evidence, assessments, gaps, risks and implementation progress. The application recognises business, technical and operational ownership, plus additional asset assignments.

## Assessor and reviewer

The application supports assessor and reviewer activities, although these are not separate platform roles today. Users can run an assessment, inspect source evidence, answer questions, accept a result, amend it, request reassessment and reopen a previously reviewed result. Review actions retain the human decision and rationale alongside the original AI recommendation.

## Risk or remediation owner

Risk and action ownership exists in the business data. Users can review assessment-derived risks, change risk attributes and monitor linked controls, threats and weaknesses. Remediation guidance and actions can be generated and tracked. The current risk-register user interface is less complete than the underlying risk model.

## Executive or assurance stakeholder

The main dashboard presents enterprise-level standards, assets, assessment posture, findings, risks and assessment activity. It is intended to support management oversight and drill-down, although the current role model does not provide a dedicated executive or independent-auditor role.

## Administrator

Administrators manage users, departments, catalogue and profile imports, AI settings, prompt templates, generated artefacts, assessment operations, findings, evidence proposals, mappings, external intelligence, vector maintenance, backups, audit records and platform health.

# 4. Logical architecture

The application uses a layered .NET architecture:

- Domain contains the business entities and enumerations.
- Application contains data-transfer objects, configuration models and service contracts.
- Infrastructure implements relational persistence, identity, evidence storage, document extraction, access rules, dashboards, reviews, audit, backup and external-data ingestion.
- Importers implements OSCAL catalogue and profile imports plus assessment-objective projection and CPRT reconciliation.
- Vector implements knowledge ingestion, dense and sparse indexing, hybrid retrieval, reranking and vector reconciliation.
- AI implements content generation, evidence analysis, assessment scoring, interviews, findings, drift detection, risk linkage, evidence graphs, solution generation, conversational assistance, evaluation and background jobs.
- Web is a Blazor Server application using MudBlazor components. It provides the user interface, HTTP endpoints, authentication and background-job scheduling.

The compile-time dependency direction is deliberately controlled:

    Domain ← Application ← Infrastructure
                         ↖ Importers
                         ↖ Vector
                         ↖ AI
                         ↖ Web

Infrastructure is not allowed to depend directly on the Vector or AI projects. Shared behaviours are exposed through Application interfaces.

## Runtime components

- .NET 10 and C# 14 application runtime.
- Blazor Server with interactive server-side components.
- PostgreSQL for relational business, history and audit data.
- MinIO, using an S3-compatible interface, for original evidence objects.
- Qdrant for the unified knowledge index, with a named dense vector and a sparse vector.
- Hangfire, using PostgreSQL storage, for assessment, ingestion and scheduled background jobs.
- Local Docling document processing for structural extraction and OCR.
- A local cross-encoder reranker using the BGE reranker model.
- Microsoft.Extensions.AI abstractions for OpenAI, Ollama or OpenRouter chat providers.
- OpenAI text-embedding-3-small embeddings with 1,536 dimensions. The Qdrant collection is built around this dimension and cannot be switched casually to an incompatible embedding model.

The local development stack uses non-default ports: PostgreSQL 5440, Qdrant 6343/6344, MinIO 9010/9011, Docling 5051, reranker 8091 and the web application 5104.

# 5. Standards, catalogues, profiles and controls

## Standards and versions

The system stores a Standard and one or more StandardVersion records. A version retains its version identifier, OSCAL version information, title, modification information and relationship to the imported source. Multiple versions can coexist so historical assessments remain tied to the version against which they were performed.

The current data includes or is designed to support NIST SP 800-53, NIST SP 800-171, the NIST Secure Software Development Framework, OSCAL catalogues and profiles, and an operational-technology overlay. The system is not conceptually restricted to these standards.

## Catalogue import

Administrators can import an OSCAL catalogue. The import process previews and validates source material, creates an import job, records its outcome, preserves raw source documents and maps the published hierarchy into relational records. Re-import is designed to be idempotent rather than creating uncontrolled duplicates.

The catalogue model includes:

- standards and versions;
- framework groups or control families;
- controls;
- control enhancements and other child entries;
- control parts and nested prose;
- parameters and organisation-defined values;
- properties and links;
- back-matter resources;
- active and withdrawn status;
- control type, including Family, Control, Enhancement, Requirement, Practice, Task and Objective.

## Profiles and resolved scope

OSCAL profiles can be imported and associated with a standard version. A profile represents a selected and tailored subset of the catalogue. The system supports selections, additions, modifications, exclusions and parameter settings. Profiles may also act as overlays. Profile aliasing provides user-friendly names for known baselines or overlays.

An assessment is scoped from a profile. Family-only and withdrawn records are excluded from assessable totals, as are any explicit scoping exceptions recorded for the assessment.

## Control families and hierarchy

Users can browse standards in a compact table, open a standard version, view its families and drill into a family. Family counts distinguish active requirements from withdrawn material.

The Controls area supports standard, profile and family filtering plus identifier/title search. Controls are presented hierarchically. A parent such as AC-2 can be expanded to show enhancements such as AC-2.1, AC-2.2 and AC-2.3. Enhancements are collapsed by default to keep large control lists manageable.

## Control detail

A control detail page contains tabs for:

- authoritative statement;
- guidance;
- parameters;
- enhancements, when present;
- AI-generated artefacts;
- assessment-related information;
- overview and general solutions;
- asset-specific solutions.

Control prose can render organisation-defined parameter values inline. Users can maintain parameter values and discard or save edits.

## Assessment objectives

The evidence-first programme projects assessment objectives from the imported control-part tree. These objectives reflect OSCAL identifiers and NIST SP 800-53A-style determination statements. The objective, rather than the whole control alone, is the atomic unit used for evidence retrieval and judgement.

The system can import and reconcile CPRT assessment-procedure content and can align generated atomic requirements to official objectives. Identifier validation exists to prevent ambiguous or invalid catalogue references from silently entering assessment and export data.

## AI-generated control material

For a control, the system can generate:

- a simplified requirement;
- one or more practical test cases;
- expected outcomes for test cases;
- atomic requirements;
- a control overview;
- generic implementation solutions;
- a control exemplar;
- a hypothetical-document query used to improve retrieval.

Generated artefacts carry states such as Draft or Approved. Authorised users can accept, reject, delete or regenerate them. Atomic requirements and test cases are displayed as collapsible items so long generated content does not overwhelm the page. Generated content assists understanding and testing; it does not replace the authoritative standard text.

# 6. Assets and organisational context

## Asset register

The application contains an IT/OT asset register. Each Asset can store:

- a unique asset key and name;
- description;
- domain, such as IT or OT;
- kind, such as application or platform;
- operating environment;
- criticality;
- lifecycle status;
- supplier, product version and location;
- regulatory tags;
- personal-data indicators;
- OT-specific context, including Purdue level, safety relevance and operating posture;
- business, technical and operational owners;
- creation and modification information.

The All Assets page presents a compact table with filters for domain, kind, criticality and lifecycle. The My Assets page shows assets owned by or assigned to the signed-in user.

## Access and assignments

An administrator can access all assets. An ordinary user gains asset access through an assignment or by being recorded as a business, technical or operational owner. If no valid relationship exists, access fails closed. Asset assignments can carry an assignment role.

## Business and system context

An asset can have a maintained system-context narrative used by assessors and AI prompts. It can also have structured business areas and business roles. Departments support broader organisational grouping. This context is intended to prevent generic assessment and remediation advice that ignores the asset's actual purpose and operating environment.

## Asset detail

The asset detail experience supports viewing and editing the asset, assigning and removing users, maintaining system context, seeing evidence and assessment relationships, generating asset-specific solutions and exporting solution information. Assets also relate to compliance profiles, control implementation records, risks and business areas.

# 7. Evidence library and supported formats

## Asset-wide evidence model

Evidence is primarily asset-wide rather than unique to one assessment. A document can be uploaded once and reused across authorised assessments of the same asset. An evidence upload may also be associated with an assessment session for context.

The evidence popup or library shows counts for Ready, Processing and Failed items, permits status refresh, supports file and folder upload and allows text to be pasted directly as evidence. Each evidence row shows its business title, source filename, date, processing status and available view/download actions.

## Supported evidence formats

The current accepted-format policy includes:

- Markdown, plain text and log files;
- CSV;
- JSON, YAML and XML;
- HTML and AsciiDoc;
- PDF;
- DOCX;
- XLSX and XLSM;
- PPTX;
- PNG, JPEG, GIF, WebP, TIFF and BMP images;
- VSDX Visio diagrams.

Legacy binary Microsoft formats are deliberately rejected with actionable guidance: DOC must be re-saved as DOCX, XLS as XLSX, PPT as PPTX and VSD as VSDX. ZIP, 7z and RAR archives are not unpacked; users must upload the files inside them.

## Viewing and download

Users can preview supported documents in the application and download the original file when authorised. Preview support includes Office-style formats as well as text, data and image content. The evidence endpoints recheck asset access rather than relying only on the page that generated the link.

# 8. Evidence ingestion and provenance

## Storage and receipt

When evidence is uploaded, the application validates it, records metadata and stores the original object in MinIO. EvidenceBlob separates the stored content from the logical EvidenceUpload. Checksums and content addressing support duplicate detection and integrity. Upload records can be versioned or superseded without erasing the historical source used by prior assessments.

## Processing stages

Evidence processing is asynchronous. The pipeline records individual ingestion stages and their state. Broadly, evidence passes through:

1. receipt and object storage;
2. structural parsing or extraction;
3. OCR or visual interpretation where needed;
4. figure description;
5. structural chunking;
6. embedding;
7. vector indexing;
8. metadata and graph enrichment.

Users can see whether processing is pending, running, ready or failed. Failed evidence can be requeued from an eligible stage. A recurring sweep identifies ingestion work that has stalled.

## Structural parsing

Docling is the main structural parser for PDF, DOCX, XLSX, PPTX, Markdown, HTML, common images, AsciiDoc and CSV. A separate parser handles VSDX packages, reading shapes, text and connectors. A legacy extractor remains as a fallback for supported cases.

The selected OCR engine is Tesseract. EasyOCR was rejected because it repeatedly crashed on the local ARM64 environment. Visual figures can be described by a vision model so that diagrams and images become retrievable text while the source image remains linked.

## Provenance

Derived content retains source provenance where the parser supplies it. This includes page number, structural location and bounding box. A KnowledgeChunk is the canonical searchable piece of text, and each evidence chunk retains its relationship to the upload and evidence version from which it came.

The assessment system can therefore show a citation quote and link it back to the source page or region, rather than citing only a document name.

## Evidence lifecycle

Evidence can carry collection method, classification, effective dates, review dates and expiry information. Freshness rules determine whether it remains suitable for reliance. When evidence changes, expires, is superseded or is removed, the application can mark dependent control results as potentially stale and record the reason.

Evidence deletion is logical under the current governance approach. The platform is designed for tamper evidence and recoverability rather than claiming immutable regulatory WORM storage. An EvidenceEvent log forms a hash-linked lifecycle chain, can be verified and is periodically anchored. Rejected or failed evidence-related events are retained for audit where appropriate.

## Evidence graph

The application extracts cross-references from evidence and builds a typed relational evidence graph. Nodes can represent policies, procedures, implementation descriptions, systems, records and other evidence concepts. Edges represent relationships between them.

The graph can be traversed from a control or evidence chunk to show a chain such as:

    policy → procedure → implementation → operational evidence

The gap detector identifies unresolved references and chains that stop at intent without reaching implementation or proof. Graph extraction runs and identified gaps are recorded.

## Two evidence concepts

Uploaded evidence and EvidenceArtifact are currently distinct concepts. EvidenceUpload is an actual supplied artefact processed through the evidence pipeline. EvidenceArtifact is an agent-proposed pointer or evidence suggestion with a review state. They must not be described as interchangeable.

# 9. Knowledge ingestion and retrieval

## Unified knowledge index

The Qdrant collection is named knowledge_v2. It contains indexed chunks from standards, controls, generated control intelligence and evidence. Each point uses a 1,536-dimensional dense vector plus a sparse representation.

The relational KnowledgeChunk remains the canonical record. The Qdrant point is a searchable projection and must reconcile one-to-one with the relevant relational chunk.

## Hybrid retrieval

Retrieval combines:

- semantic similarity from dense embeddings;
- sparse or lexical relevance;
- fusion of candidate results;
- cross-encoder reranking of the strongest candidates;
- scope and access filters;
- diversity and evidence limits.

Sparse corpus statistics are maintained separately because document-length normalisation depends on corpus-level values. When sparse vectors are rebuilt, statistics must be recomputed first.

## Objective-level retrieval

During assessment, evidence is retrieved separately for each assessment objective. An ObjectiveQueryBuilder constructs focused queries. Retrieval can use control content, objective text, parameters, business context, hypothetical-document queries and control exemplars. Candidate evidence is reranked and capped before it is given to the scorer.

RetrievalSet records provide audit context about what was searched and selected. A retrieval outage throws a distinct operational exception and must not result in a Missing compliance score.

## Search

The Semantic Search page supports keyword and vector search. Users can scope results by standard version, profile or asset. Evidence results must respect asset access. Results expose their source and enough provenance to navigate to the underlying content.

## Vector administration

Administrators can ingest or rebuild knowledge, inspect coverage and reconcile the relational chunk set with live Qdrant points. Orphan vector points can be removed through an explicit reconciliation action. The application also supports deletion or supersession of points by source.

There is not yet an equivalent general MinIO blob reconciler. A failed object deletion is recorded on the evidence upload, but no documented sweep repairs orphan evidence objects.

# 10. Assessment models

The application currently contains two related assessment concepts.

## AssessmentSession

AssessmentSession is the primary user-facing My Assessments workflow. It represents an asset/profile/user assessment workspace and tracks:

- asset and profile;
- owner;
- Guided or AutoScore mode;
- Active, Completed, Abandoned or related session state;
- current scoring operation;
- underlying assessment-run reference;
- current control family;
- total and scored controls;
- open questions;
- creation, last activity and completion times;
- related evidence uploads, interviews and scoping exceptions.

## AssessmentRun

AssessmentRun originated as an ad hoc or scheduled continuous-assessment pass. It has its own scope, trigger, status, progress, model, notes, errors and failed-control list. The administrative Assessment Operations area can create and inspect these runs. The older runner creates DraftFinding records for controls.

The two models now overlap. AssessmentSession wraps or refers to an AssessmentRun for user assessment, while the older AssessmentRunner/finding workflow remains present. The target relationship between them is not fully resolved and must be explained when discussing assessment architecture.

# 11. Creating and scoping an assessment

The My Assessments page lists assessments owned by the user. A user can start a new assessment by selecting:

- an asset they own or can access;
- an imported profile;
- an optional title;
- AutoScore or Guided mode.

AutoScore creates the assessment and lets the user confirm evidence before choosing to score all remaining controls. Guided mode is intended to walk through work in smaller control-family steps.

The session service resolves the selected profile into an assessable scope. Family records and withdrawn controls are not scored. ScopingException records can remove individual controls from the session. An active assessment for the same user, asset and profile can be reused rather than creating an accidental duplicate.

# 12. Assessment execution

## Individual and bulk scoring

The user can score one control or request scoring of all remaining controls. Bulk AutoScore execution is queued through Hangfire's assessment queue. Progress events are published to the interactive UI.

The user can request that the scoring queue stop. Completed results remain saved. The stop prevents further controls being started, although an already in-flight control may finish. The assessment can later resume and process only the remaining controls.

Each scoring request receives a ScoringOperationId. A queued job must match the session's current operation identifier. This fences off an old or superseded Hangfire job so it cannot silently restart cancelled scoring.

## Per-control scoring flow

For each control, the engine broadly performs the following:

1. load the current control, parameters, official assessment objectives and asset context;
2. build a focused query for each objective;
3. retrieve a broad evidence candidate pool through hybrid search;
4. rerank candidates and enforce evidence limits;
5. ask the scorer to judge each objective from the supplied evidence;
6. create objective-level judgements and supporting citations;
7. verify citation quotes against the retrieved source chunks;
8. calculate the control outcome, percentage and confidence;
9. generate concise strengths, weaknesses, rationale and recommended actions;
10. persist an immutable ControlAssessmentResult and related audit records;
11. create clarification questions or a draft risk when appropriate;
12. update assessment progress and notify the UI.

## Result model

A result can include:

- compliance outcome such as Strong, Adequate, Partial, Weak, Missing or Not Applicable;
- numeric score or percentage;
- raw and calibrated confidence;
- evidence-sufficiency information;
- summary rationale;
- what is working;
- what needs attention;
- recommended next steps;
- objective-by-objective judgements;
- citations;
- model and prompt provenance;
- review status, reviewer and decision;
- links to source run, asset, profile and control.

Results are historical records. Reassessment creates a new result rather than rewriting the old result. The application chooses the effective latest result when presenting current posture.

## Failure behaviour

RetrievalUnavailableException and ScorerUnavailableException represent operational inability to assess. Neither carries a compliance score. A control affected by an infrastructure or provider failure is listed in the run's failed-control collection and remains unscored. This prevents an outage from appearing as evidence that a control is Missing.

Model output truncation is also treated as a scoring failure mode rather than a valid verdict. The configured output limits are deliberately high because controls with many objectives can produce large structured responses.

# 13. Citations and assessment provenance

AssessmentCitation records contain the relationship between a result or objective judgement and the evidence chunk used to support it. A citation verifier checks that the claimed quotation actually appears in the retrieved source content.

Verified citations can identify the source document, page and region. Rejected citation attempts are deliberately retained. They show what the model attempted to cite and why it was not accepted, providing evidence of model behaviour rather than deleting the failed attempt.

The assessment audit context includes the retrieval set, objective queries, source chunks, model, prompt or prompt fingerprint, result, citations and later human decision. The goal is reproducibility of the decision context, even if the exact output of a non-deterministic model cannot be reproduced byte for byte.

# 14. Clarification questions

Where evidence is incomplete or ambiguous, the system can create an InterviewExchange containing a focused question for the user. Questions are associated with the session and control.

The user can answer a question or skip it. An answer is attributable to the user and can be retained as evidence. The system can then offer to rescore the affected control. The assessment tracks its number of open questions, and unresolved mandatory questions can prevent completion.

# 15. Human review

The current assessment page presents a compact full-width control list. Families can be collapsed, and parent controls can hide or show enhancements. Each scored row exposes review actions such as Accept Result, Amend Result and Reassess. Selecting the control opens a detailed result dialog rather than replacing the list.

The detailed assessment view contains:

- control identity and title;
- tabs for Assessment, Requirements and Supporting Evidence;
- a verdict area with score, outcome, summary and review state;
- evidence/citation inspection;
- What is working;
- What needs attention;
- Recommended next steps;
- assessment reasoning and additional detail;
- navigation to previous or next result.

The review service supports:

- listing and prioritising review work;
- claiming a result;
- accepting the AI result;
- overriding or amending the result with a human score and reason;
- rejecting it for reassessment;
- reopening a reviewed result with a reason;
- calculating review coverage;
- recomputing review priorities.

The original AI verdict is retained when a human overrides it. Reviewer identity, decision, reason and time form part of the history. Completion or export can be gated by review coverage and sign-off rules.

# 16. Assessment completion, deletion and export

An assessment can be completed only when its required controls have results, the required review work is complete and mandatory clarification questions have been resolved. The presence of gaps does not itself block completion; gaps are legitimate assessment outcomes.

The assessment can also be abandoned or deleted by an authorised user. Deletion removes assessment-specific results and questions according to the implemented lifecycle. Asset-wide evidence remains available. Draft risks created from deleted results are preserved or unlinked according to the current deletion logic rather than silently erasing risk history.

The application can export:

- OSCAL assessment-results; and
- OSCAL plan of action and milestones information.

Exports are built from the session, scope, findings, results and relevant evidence references. Evidence references are intended to resolve to actual retrievable sources. Export may require sign-off, depending on current policy settings.

The assessment drift page compares relevant runs or results and shows changes in scope, evidence or conclusions.

# 17. Findings

Findings form a workflow separate from the user-facing ControlAssessmentResult and Risk models.

The administrative AssessmentRunner can evaluate scoped controls and create DraftFinding records. Administrators can list draft findings, inspect them and approve or reject them. Approval creates or promotes a formal Finding. Formal findings have severity, status and links to the source assessment context. They can be updated and closed.

A finding represents a reviewed assurance issue. A risk represents business exposure and its treatment. They may be related, but they are not interchangeable records.

# 18. Risk register

Risk is a first-class domain record. Assessment gaps can automatically draft a risk through the RiskLinker. The AI-generated draft includes its source result, asset, control and confidence so a human can review it.

A risk can contain:

- title and risk statement;
- rationale;
- category;
- inherent likelihood and impact;
- residual likelihood and impact;
- calculated inherent and residual score;
- status: Draft, Open, Mitigating, Accepted, Transferred or Closed;
- treatment: Mitigate, Accept, Transfer or Avoid;
- owner and target or review dates;
- human review information;
- AI-generated flag, confidence and source provenance;
- source assessment result or run;
- linked controls;
- linked ATT&CK techniques;
- linked CWE weaknesses;
- treatment steps.

The Risk Register page lists up to the current configured result limit, supports status, source and text filtering, identifies AI-drafted and high-residual risks and provides edit and delete actions. It can also perform a filtered bulk deletion after confirmation.

The current UI does not clearly expose creation of a completely manual risk even though the model can represent one. RiskTreatmentStep exists in the domain and persistence model, but full treatment-step management is not exposed in the current risk interface. These are current product gaps, not completed capabilities.

# 19. Remediation and implementation guidance

## Control overview and solutions

The control detail page can generate a concise control overview and generic implementation solutions. These are control-level guidance and are not automatically tailored to a specific asset.

## Asset-specific solutions

AssetControlSolution represents guidance for implementing a control on a particular asset. Asset context and business context are used so that recommendations can reflect the actual system. Users can generate, edit, regenerate and delete asset-specific solutions.

AssetControlImplementation records implementation state. ImplementationAction represents concrete work and can contain an action, detail, responsible business area, estimated hours, notes and completion state.

## Compliance Checker

The Compliance Checker lets a user choose an asset, standard and control family, then inspect the controls and their asset-specific implementation guidance. It supports:

- loading existing solutions and actions;
- editing system and business context;
- generating or regenerating implementation actions;
- generating or regenerating solutions;
- marking actions complete;
- editing actions, notes, responsible area and effort;
- deleting control or family guidance;
- bulk generation;
- category and priority filtering;
- Markdown and CSV export;
- navigation to the broader Solutions Planner.

## Solutions Planner

The Solutions Planner creates a plan for a selected asset and standard/profile/family scope. A SolutionPlan contains SolutionPlanItems with category, priority, effort, status and generated guidance.

Users can create, view, regenerate, archive and delete plans. Background generation progress is polled by the page. Plans can be exported as Markdown, DOCX or PDF. Implementation actions can be exported as CSV, and a separate implementation-plan export is available after user consent where needed.

The plan and compliance-checking features are related but distinct. The checker focuses on control-by-control implementation for an asset. The planner packages multiple recommendations into a coordinated plan.

# 20. Dashboard and management reporting

The home page is the Compliance Dashboard. Its current design uses compact summary cards and denser tabular or chart layouts.

The top-level measures include:

- number of imported standards;
- number of active controls or requirements, families and withdrawn entries;
- number of assets and high-level ownership/criticality status;
- open findings and their severity;
- last refresh time.

## Assessment score

The assessment-score card uses the latest effective scored asset/control results. It shows a weighted percentage plus counts for Strong, Adequate, Partial, Weak and Missing outcomes. Not Applicable and unassessed results are excluded and shown separately. The weighting currently described in the product gives Strong the highest value, then Adequate, Partial, Weak and Missing.

## Risk reporting

The residual-risk card contains a 5×5 likelihood/impact heatmap, counts for open/draft, mitigating, accepted/transferred and overdue risks, a notification for AI-proposed risks awaiting review and a category summary.

## Findings

The open-findings card shows overdue and pending-review totals, a summary when no findings exist and counts for findings in treatment and ready to verify.

## Assessment activity

Assessment activity includes runs in the recent period and counts for completed, failed, pending, marked-running and cancelled work. It also summarises asset-control implementation states. The dashboard notes that recorded run states are not necessarily the live scoring queue.

## Recent runs and operational measures

Recent assessment runs show asset/assessment name, state, evaluation progress and time. Additional dashboard data structures support catalogue, AI, evidence, threat-intelligence and operational summaries, although the exact visible combination can evolve with the page layout.

All dashboard values should be understood as current relational aggregates, not an independent reporting warehouse. Current code supports an optional standard-version filter in the dashboard service.

# 21. Semantic search

The Semantic Search page provides two retrieval modes:

- vector or hybrid semantic search for conceptually related content;
- keyword search for direct text matches.

The user can constrain search by standard version, profile and asset. Search covers indexed knowledge such as controls, generated control material and authorised evidence. Result access must respect asset scope. Result content includes source context rather than an unexplained similarity score alone.

# 22. Agent Chat

Agent Chat is a conversational compliance assistant. A user can create a conversation, select its standard/profile/asset scope and ask questions. The ComplianceAgent retrieves relevant authorised context and asks the configured chat model to answer with citations.

Conversation capabilities include:

- create conversation;
- list the user's conversations;
- open a conversation;
- send and receive messages;
- retain conversation history;
- rename a conversation;
- delete a conversation;
- scope the conversation to relevant standards, profiles and assets.

Chat responses are advisory. They do not directly accept assessment results, approve risks or bypass governed workflows. Retrieved evidence must remain within the user's asset access.

# 23. Framework mappings and control intelligence

The administration area supports several external intelligence sets and mapping types.

## ATT&CK

AttackPattern stores MITRE ATT&CK techniques and related metadata. ControlAttackMapping and more general mapping edges relate controls to techniques. Administrators can refresh ATT&CK content and ingest crosswalk mappings.

## CWE

CweWeakness stores Common Weakness Enumeration information. It can be refreshed, searched and used to enrich vulnerability or risk context. Risks can link directly to CWE records.

## Known Exploited Vulnerabilities

KevEntry stores CISA Known Exploited Vulnerabilities information, including ransomware relevance where available. Administrators can refresh and browse the feed. KEV items can be enriched through CWE relationships.

## NIST CSF

CsfElement stores NIST Cybersecurity Framework functions, categories and subcategories. ControlCsfMapping relates controls to these outcomes. Both the reference content and mappings can be refreshed or ingested.

## CIS

CisSafeguard stores CIS safeguard content, including implementation-group context. Administrators can ingest and browse it.

## ISO 27002

IsoControl stores ISO 27002 reference content. ControlIsoMapping relates controls to ISO content. Administrators can refresh the reference set and ingest mapping sources.

## ITIL practices

ItilPractice and ControlItilAssociation represent service-management practice associations for controls. An AI-assisted administrative process can calculate missing associations across a selected standard, and administrators can monitor progress or stop the run.

## Cross-framework mappings

CrossFrameworkMapping and FrameworkMappingEdge represent relationships between controls or between controls and external framework elements. Relationship types distinguish stronger or weaker correspondence rather than treating all mappings as equivalence.

Mappings can have different provenance: official source, imported crosswalk, generated/inferred or human-reviewed. The source and mapping type are important to interpretation.

## Control dossiers

The forward mapping view searches for a control and builds a ControlDossier showing its related standards, mappings, ATT&CK, CSF, ISO and other intelligence.

The reverse mapping view begins with an external target, such as a technique or framework item, and identifies relevant controls.

## Control synergy

ControlSynergy clusters controls that overlap or may share evidence/remediation. Administrators can rebuild automatic clusters, inspect their members and delete a cluster. A synergy is a reuse aid; it does not remove the distinct obligation represented by each control.

# 24. AI providers and configuration

The system uses a provider-aware chat client. Administrators can choose among configured OpenAI, Ollama and OpenRouter providers and models. The settings page can retrieve model lists from Ollama and OpenRouter where supported.

Chat and embedding configuration are separate. Chat models can change at runtime. The embedding model is effectively pinned because the vector collection uses 1,536 dimensions. Changing it requires a deliberate full re-index and is not an ordinary provider switch.

The current default chat model described by repository instructions is an Ollama-hosted cloud model. It is reached through a local Ollama daemon but still depends on a remote model service.

The AI health service reports provider and supporting-service state. The platform should fail visibly when a provider is unavailable rather than manufacturing a business outcome.

# 25. Prompt and AI-content administration

PromptTemplate stores prompts by purpose and version. Administrators can:

- view prompt types and their versions;
- edit a prompt;
- save edits as a new version;
- activate an approved version;
- restore or compare prior prompt text through the version list.

Only the active prompt for a purpose is used. Assessment and evaluation records retain prompt or build provenance so a later result can be associated with the instructions that produced it.

The Generation administration page can generate simplified requirements, test cases, atomic requirements, overviews and solutions for an individual control or in bulk. It displays counts and recent artefacts, supports stopping bulk work and lets administrators approve or reject generated items.

The AI Parameters page manages organisation context and AI-assisted filling of control parameters across a selected scope. The process can be monitored and stopped.

# 26. AI evaluation and trust

## Evaluation sets

GoldenQuestion represents a curated evaluation case. Cases can cover expected assessment outcomes and retrieval relevance. Administrators can create, edit and delete questions.

## Evaluation runs

An EvalRun contains EvalResult records and captures model, prompt and outcome information. Evaluations can be started through the administrative page, an authenticated endpoint or command-line mode. Reports compare current behaviour with expected results and prior baselines.

## Metrics

The evidence-first programme uses metrics such as:

- exact or adjacent score agreement;
- quadratic-weighted Cohen's kappa;
- performance against the best constant predictor;
- retrieval recall at a specified candidate depth;
- citation correctness;
- parse failure and operational failure rate;
- confidence calibration;
- token use and elapsed time.

Raw exact agreement alone is not considered enough because an imbalanced test set can make a constant predictor look successful.

## Current measured design decisions

The current one-pass scorer prompt is pinned by a fingerprint test to keep evaluation comparable. Two-pass scoring exists but is disabled because measured testing showed lower agreement and higher token/time cost than one-pass scoring. These are measured current decisions, not universal claims about all models.

The confidence calibrator converts model confidence and observable features into a calibrated value and can explain feature contributions. Human-review outcomes can be harvested to extend the evaluation set without copying sensitive customer evidence into documentation.

# 27. Identity and user administration

The application uses ASP.NET Identity with cookie authentication. The login and logout experience is provided through dedicated account routes and endpoints. Password complexity and disabled-user behaviour are configured in the application.

The current roles are User and Admin/Administrator. Administrators can:

- list users;
- create a user with a temporary password;
- edit display name, department and roles;
- disable or re-enable a user;
- reset a password;
- delete a user.

Departments can be created, edited and deleted. The user's profile page displays their own identity and organisational information. Asset access adds a second authorisation layer beyond global role.

# 28. Administration areas

The administration navigation is grouped into hubs.

## Administration hub

Provides entry points to identity, catalogues, AI, assessment operations, cross-framework mappings and platform operations.

## Identity and organisation

- Users.
- Departments.
- Identity hub.

## Standards and catalogues

- Catalogue import.
- Profile import.
- Generated control content.
- AI parameter filling.
- Catalogues hub.

## AI and automation

- AI settings and provider/model selection.
- Prompt templates and versions.
- Evaluation cases and runs.
- AI hub.

## Assessment operations

- Administrative assessment runs.
- Draft and formal findings.
- Proposed evidence review.
- Assessment operations hub.

## Cross-framework mappings and intelligence

- forward control mappings;
- reverse mappings;
- synergy clusters;
- ATT&CK content and mappings;
- CWE;
- KEV;
- NIST CSF content and mappings;
- CIS safeguards;
- ISO 27002 content and mappings;
- ITIL associations;
- cross-mappings hub.

## Platform operations

- platform health;
- vector ingestion, rebuild and reconciliation;
- backup and restore;
- audit log;
- platform hub;
- Hangfire background-job dashboard for authorised administrators.

# 29. Background jobs and scheduled work

Hangfire supports separate default, ingestion and assessment queues.

Evidence ingestion is broken into queued stages so work can resume and individual failures can be diagnosed. Assessment AutoScore is queued separately so large assessments do not block ordinary web requests.

Recurring work includes:

- administrative audit retention;
- stalled-ingestion sweeping;
- CISA KEV refresh;
- other intelligence or mapping refreshes where configured;
- evidence-freshness evaluation;
- evidence-event-chain anchoring.

Some refresh jobs have dedicated administration pages and may be started manually. Jobs record last outcome and errors through their domain records or health views.

# 30. Backup, restore, health and reconciliation

The Backup/Restore administration page can create an application backup and accept a backup file for restoration. Restore modes and safeguards are implemented by dedicated services. Destructive local-stack restoration or reset is treated separately and scripts ask for explicit confirmation.

Platform Health reports important application dependencies and recurring jobs. It includes database and service state, queue/job information and knowledge-index coverage where available.

Vector reconciliation compares relational chunks with Qdrant points. It reports missing or orphan points and can optionally remove vector orphans. The evidence event chain can also be verified.

The local-stack scripts can start services, start the app, snapshot PostgreSQL and Qdrant, restore a snapshot and reset local volumes. Reset and restore are destructive operations and require explicit confirmation.

# 31. HTTP endpoints and interoperability

The user interface is the primary integration surface. The current explicit HTTP endpoints are narrow and purpose-specific:

- health check;
- account login;
- account logout and perform-logout;
- OSCAL assessment-results export for a session;
- OSCAL plan-of-action-and-milestones export for a session;
- evidence download;
- evidence view/preview;
- administrator evaluation run.

The application does not currently expose a broad enterprise REST API for every domain. Integration beyond the available imports, exports and endpoints would require additional work.

Machine-readable or business exports include:

- OSCAL catalogue/profile import;
- OSCAL assessment-results export;
- OSCAL POA&M export;
- Markdown solution-plan export;
- DOCX solution-plan export;
- PDF solution-plan export;
- CSV implementation-action or compliance-checker export;
- original evidence download.

# 32. Command-line and engineering operations

The web project also exposes in-process command modes used for maintenance and evaluation:

- run selected evaluation cases;
- embed pending knowledge;
- benchmark structural parsers over a document directory;
- parse one document and describe figures without persisting it;
- reprocess evidence through the complete ingestion chain;
- recompute sparse corpus statistics;
- re-encode sparse vectors;
- rebuild projected assessment objectives;
- align generated atomic requirements to official objectives, with dry-run and apply modes;
- import CPRT assessment content and reconcile it;
- import selected mapping sources;
- seed and verify the evaluation corpus;
- perform other data-maintenance operations described by current command registration.

These are engineering or administrative tools, not ordinary user journeys.

# 33. Core data model

The major business records are grouped below.

## Standards and controls

- Standard: framework identity.
- StandardVersion: a published/imported version.
- FrameworkGroup: family or grouping.
- Control: family, control, enhancement, requirement, practice, task or objective.
- ControlPart: structured statement/guidance/objective content.
- ControlParameter: organisation-defined or source parameter.
- ControlProperty and ControlLink: metadata and references.
- BackMatterResource: referenced source material.
- Profile and ProfileControl: selected/tailored assessment scope.
- OscalRawDocument: retained imported source.
- ImportJob and ImportRunAudit: import processing and outcome.
- AssessmentObjective: official or projected objective used for judgement.
- CprtElement: imported assessment-procedure content.

## Assets and organisation

- Asset: assessed system or service.
- AssetAssignment: user-to-asset relationship.
- Department: organisational grouping.
- AssetBusinessArea and AssetBusinessRole: asset-specific business context.
- OrganizationContext: broader contextual information used for AI parameter work.
- AssetComplianceProfile: resolved or cached asset profile information.

## Evidence and knowledge

- EvidenceBlob: stored content identity/object reference.
- EvidenceUpload: logical submitted evidence and processing state.
- AssessmentEvidenceVersion: evidence version relationship used by assessment.
- IngestionStageRecord: stage-by-stage pipeline progress.
- EvidenceEvent: append-only lifecycle/integrity event.
- KnowledgeChunk: searchable relational chunk.
- SparseCorpusStat: corpus values used for sparse search.
- EmbeddingJob: indexing work.
- EvidenceArtifact: proposed evidence pointer with review state.
- EvidenceGraphNode, EvidenceGraphEdge and EvidenceGraphGap: typed evidence relationships and missing links.
- EvidenceGraphExtractionRun: graph-build execution record.

## Assessment and review

- AssessmentSession: user assessment workspace.
- AssessmentRun: execution or scheduled pass.
- ControlAssessmentResult: immutable control conclusion.
- AssessmentCitation: source support and verification outcome.
- RetrievalSet: evidence retrieval audit context.
- InterviewExchange: clarification question and answer.
- ScopingException: approved exclusion.
- ControlResultStaleness: reason a result may no longer be current.
- DraftFinding and Finding: separate assurance-issue workflow.

## Risk and remediation

- RiskCategory: categorisation scheme.
- Risk: business exposure and treatment state.
- RiskControlLink, RiskAttackLink and RiskCweLink: related control/intelligence records.
- RiskTreatmentStep: planned treatment activity.
- ControlOverviewSolution: generic guidance.
- AssetControlSolution: asset-tailored guidance.
- AssetControlImplementation: current implementation state.
- ImplementationAction: concrete implementation work.
- SolutionPlan and SolutionPlanItem: coordinated improvement plan.

## AI and evaluation

- AiProviderSetting: provider/model configuration.
- PromptTemplate: versioned prompt.
- LlmInteraction: immutable material AI interaction record.
- SimplifiedRequirement, TestCase, ExpectedTestOutcome and AtomicRequirement: generated control artefacts.
- ControlExemplar and ControlHydeQuery: retrieval aids.
- GoldenQuestion, EvalRun and EvalResult: evaluation data.

## External intelligence and mappings

- AttackPattern and ControlAttackMapping.
- CweWeakness.
- KevEntry.
- CsfElement and ControlCsfMapping.
- CisSafeguard.
- IsoControl and ControlIsoMapping.
- ItilPractice and ControlItilAssociation.
- CrossFrameworkMapping and FrameworkMappingEdge.
- SimilarControlLink.
- ControlSynergy and ControlSynergyMember.

## Identity and audit

- ApplicationUser: identity account.
- AdminActionAudit: administrator audit record.
- ChatConversation and ChatMessage: conversational history.

# 34. Important lifecycle states

## Assessment session

Typical states include Active, Completed and Abandoned, with scoring operation state maintained separately for queue control.

## Assessment run

Run states distinguish Pending, Running, Completed, Failed and Cancelled or equivalent recorded conditions. A marked-running record is not necessarily proof that a live queue worker is still executing it.

## Compliance result

Control outcomes include Strong, Adequate, Partial, Weak, Missing and Not Applicable. Objective judgements separately record whether each testable clause is supported, partially supported, unsupported or unable to be determined.

## Review

Review status and outcome distinguish awaiting review, claimed/in review, accepted, overridden, rejected for reassessment and reopened behaviour.

## Evidence upload

Evidence states distinguish receipt/queued work, processing, ready, failed, deletion/supersession and related pipeline detail.

## Risk

Risk status is Draft, Open, Mitigating, Accepted, Transferred or Closed. Treatment is Mitigate, Accept, Transfer or Avoid.

## Finding

Draft findings have a review state. Formal findings have their own lifecycle, including active/treatment/verification or closure-related states.

## Generated content

Generated control artefacts distinguish Draft from approved or rejected states.

# 35. Security, privacy and audit model

Authentication uses ASP.NET Identity and secure application cookies. Protected pages require authentication, and administration pages require administrator authorisation.

Asset access is enforced by a dedicated service. The evidence view and download paths verify that the requesting user can access the evidence's asset. Retrieval filters also carry asset scope so semantic search and chat do not intentionally expose another asset's evidence.

Administrative actions can be recorded through AdminActionAudit. Evidence has its own append-only event chain. Assessment results, citations, LLM interactions and human review decisions retain more specialised audit history.

A regex-based personal-information sanitizer exists for configured AI or logging uses, but it is not a guarantee that no sensitive evidence reaches a remote provider. Assessment prompts contain evidence excerpts. Provider approval and data handling therefore remain material governance concerns.

The application is single organisation. Tenant fields in the vector/retrieval design are dormant and do not provide active isolation.

# 36. Testing and quality controls

The repository contains three principal test projects:

- a fast unit test suite covering domain and application logic, page behaviour and regressions;
- integration tests using real PostgreSQL, Qdrant and MinIO services through Testcontainers;
- preview/browser-oriented tests for evidence and document viewing.

The unit suite was most recently run during the documentation exercise and passed 717 of 717 tests. The repository documentation reports a substantial integration suite, but its exact current test count was not re-run for this overview and should not be quoted as a newly verified number.

The evidence programme defines test tiers:

- Unit: pure logic.
- Integration: database, object and vector adapters.
- Pipeline: ingest, index, retrieve and cite end to end.
- Evaluation: retrieval and judgement quality against golden sets and real model services.

Integration tests use isolated Testcontainers rather than the persistent local stack. Some evaluation seeding also requires the local Docling parser because the corpus contains non-text formats.

Architecture decisions and phase-gate records document important choices such as parser selection, reranker selection, local service boundaries, evidence retention mode, retrieval design, model comparisons and the measured rejection of two-pass scoring.

# 37. User-interface route catalogue

The main user routes are:

- `/` — enterprise dashboard.
- `/standards` — standards and versions.
- `/standards/{VersionId}/families` — families for a standard version.
- `/standards/{VersionId}/families/{GroupId}` — controls/requirements in a family.
- `/controls` — full control library.
- `/controls/{ControlId}` — control detail and tabs.
- `/search` — semantic and keyword search.
- `/solutions-planning` — solution plans.
- `/compliance-checker` — asset/control implementation guidance and actions.
- `/chat` and `/chat/{ConversationId}` — conversational assistant.
- `/assets` — full asset register.
- `/assets/{Id}` — asset detail.
- `/my-assets` — user's assets.
- `/my-assessments` — user's assessment list.
- `/my-assessments/{SessionId}` — assessment workspace.
- `/my-assessments/{SessionId}/drift` — assessment drift.
- `/risks` — risk register.
- `/profile` — current user's profile.
- `/account/login`, `/account/logout` and `/account/access-denied` — account flow.
- `/Error` and `/not-found` — error handling.

The administration routes include:

- `/admin` — administration hub.
- `/admin/identity` — identity hub.
- `/admin/users` — user administration.
- `/admin/departments` — department administration.
- `/admin/catalogs` — catalogue hub.
- `/admin/import` — catalogue import.
- `/admin/import-profile` — profile import.
- `/admin/generation` — AI-generated control content.
- `/admin/ai-parameters` — organisation context and parameter generation.
- `/admin/ai` — AI hub.
- `/admin/ai-settings` — provider/model configuration.
- `/admin/prompt-templates` — prompt versions and activation.
- `/admin/eval` — golden questions and evaluation runs.
- `/admin/assessment-ops` — assessment-operations hub.
- `/admin/assessments` — administrative runs and scheduling.
- `/admin/findings` — draft and formal findings.
- `/admin/evidence` — proposed evidence review.
- `/admin/cross-mappings` — mappings hub.
- `/admin/mappings` — forward control dossiers.
- `/admin/reverse-mappings` — reverse dossiers.
- `/admin/synergy` — control-overlap clusters.
- `/admin/attack` — ATT&CK content.
- `/admin/attack-mappings` — ATT&CK mappings.
- `/admin/cwe` — CWE content and enrichment.
- `/admin/kev` — known exploited vulnerabilities.
- `/admin/csf` — NIST CSF content.
- `/admin/csf-mappings` — CSF mappings.
- `/admin/cis` — CIS safeguards.
- `/admin/iso-27002` — ISO reference content.
- `/admin/iso-mappings` — ISO mappings.
- `/admin/itil-association` — ITIL association generation.
- `/admin/platform` — platform hub.
- `/admin/health` — service health.
- `/admin/vectors` — knowledge-index operations.
- `/admin/backup-restore` — backup and restore.
- `/admin/audit` — administrator audit log.

# 38. Current product constraints and known gaps

Keep the following facts visible when answering questions:

1. The current application is local-only and has no production deployment architecture.
2. It is single organisation; tenant fields are dormant.
3. Only User and Administrator are active application roles, so fine-grained separation of assessor, reviewer, risk owner and auditor is incomplete.
4. AssessmentSession and the older AssessmentRun/DraftFinding workflow overlap and have not been fully unified.
5. EvidenceUpload and agent-proposed EvidenceArtifact are separate models and workflows.
6. The current Risk Register does not clearly expose manual risk creation even though a non-agent risk is representable.
7. Risk treatment steps exist in the data model but lack a complete user-management experience.
8. Automated information/evidence requests, reminders and escalations are business requirements but are not currently implemented as a complete workflow.
9. There is no integrated service desk, incident-management, problem-management or change-management workflow. The application would need to integrate with an IT service-management tool or add a native workflow.
10. Backup, restore and health features exist, but enterprise availability targets, capacity thresholds, recovery objectives and witnessed recovery exercises are not baselined.
11. Evidence uses governance-mode retention/tamper evidence rather than claiming compliance-mode immutable WORM storage.
12. Evidence excerpts can reach the selected remote LLM provider during scoring.
13. The explicit HTTP API is narrow and is not a complete enterprise integration API.
14. Vector reconciliation exists; a general MinIO orphan-blob reconciler is not documented.
15. Some architecture and design documents describe original intent and may lag current implementation.
16. Repository documents conflict on the formal status of the final measurement phase: the master plan says it is in progress, while the main repository instructions describe it as completed and signed off. This needs one approved source of truth.
17. No production service levels, support model, accessibility conformance result or formal security certification should be inferred from the current codebase.

# 39. Terminology

- Standard: a compliance or control framework.
- Standard version: a specific published/imported edition of a standard.
- Family: a group of related controls.
- Control: a requirement such as AC-2.
- Enhancement: a child requirement that extends a parent control, such as AC-2(3) or its displayed equivalent.
- Profile: a selected and tailored subset of a standard.
- ODP: organisation-defined parameter within a control.
- Assessment objective: a hierarchical testable clause from the control or assessment procedure.
- Determination statement: a leaf objective that can receive an individual judgement.
- Atomic requirement: generated granular wording intended to aid assessment; it is not automatically authoritative.
- Evidence upload: a real file or inline text supplied to the asset evidence library.
- Evidence artifact: an agent-proposed pointer to evidence, subject to review.
- Evidence blob: the stored original content object.
- Knowledge chunk: a searchable passage derived from a source record or evidence.
- Retrieval set: the recorded search context and candidates used for assessment.
- Citation: the relationship between a judgement and a source passage.
- Verified citation: a citation whose claimed quote was checked against the retrieved source.
- Assessment session: the user-facing asset/profile assessment workspace.
- Assessment run: an execution record used by scoring and by the older continuous-assessment workflow.
- Control assessment result: an immutable versioned conclusion for one control.
- Interview exchange: a clarification question and answer associated with an assessment.
- Finding: a reviewed assurance issue.
- Risk: a record of business exposure, ownership and treatment.
- Remediation or implementation action: concrete work intended to improve a control or reduce risk.
- Solution plan: a coordinated collection of recommended improvements for an asset and scope.
- Drift: a change in scope, evidence or control conclusion between assessment states or runs.
- Control dossier: a consolidated forward view of mappings and intelligence related to a control.
- Reverse dossier: a view that begins with an external framework or intelligence item and identifies related controls.
- Golden question/case: a curated example used to evaluate retrieval or assessment quality.
- Calibrated confidence: confidence adjusted using measured relationships between model behaviour and correctness.

# 40. How to answer my follow-up questions

For every later question:

1. Give the direct answer first.
2. Use this overview as the authoritative description of the current application.
3. State whether the answer describes implemented capability, partial capability, a known gap or a future requirement.
4. Keep AssessmentSession separate from AssessmentRun, uploaded evidence separate from proposed evidence, findings separate from risks and AI recommendation separate from human decision.
5. Do not claim multi-tenancy, production readiness, certification, high availability, complete service management or granular role segregation.
6. Do not invent database fields, screens, integrations, business rules or numerical service targets that are not described here.
7. If I ask for a proposed future design, clearly label it as a recommendation and explain how it differs from the current system.
8. If two parts of this overview appear inconsistent, identify the inconsistency rather than silently choosing one.
9. When discussing sensitive evidence, remember that document processing is local but scoring prompts may send evidence excerpts to the selected remote model provider.
10. When discussing AI output, emphasise citations, explainability, measured quality and human approval.
11. When discussing an aggregate score or dashboard, explain the underlying population, exclusions and current-result selection where relevant.
12. If the answer is not contained in this context, say: “The supplied system overview does not establish that,” then identify the information needed to answer.

Confirm that you have understood the system overview. Summarise the system in no more than ten bullets, identify the four most important conceptual distinctions to preserve, and then wait for my questions.
```

