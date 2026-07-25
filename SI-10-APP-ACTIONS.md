# SI-10 Information Input Validation — Application Actions

## Purpose

For an IT application, SI-10 means the application must **check information received from users, files, interfaces, services and automated processes before using it**, and must reject, constrain, quarantine or safely handle information that does not meet the application’s defined requirements.

The enterprise may provide:

- secure coding standards;
- managed Microsoft Windows end-user computing devices;
- web application firewalls and API gateways;
- malware scanning;
- network boundary controls;
- corporate identity and access management;
- central logging and monitoring;
- vulnerability scanning;
- approved development platforms;
- database platforms; and
- organisation-wide security testing and incident processes.

Those capabilities are inherited.

The application remains responsible for defining and enforcing the validation rules that are specific to its:

- business data;
- workflows;
- records;
- files and attachments;
- thick-client requests;
- browser forms;
- APIs;
- service-to-service calls;
- message queues;
- batch imports;
- database operations;
- reports and templates;
- configuration;
- integration feeds;
- supplier inputs; and
- administrative functions.

NIST SI-10 requires applications to check the validity of information inputs. Its discussion emphasises that validation is based on defined specifications for allowed formats and that inputs include data received from users and other systems. Relevant enhancements address identifying potentially erroneous input, resolving errors, predictable behaviour when invalid input is received and restricting inputs to trusted sources and approved formats.

> **Core principle:** no input should be trusted merely because it comes from an internal user, a corporate device, an authenticated service or another internal application. The application must validate the information itself before acting on it.

---

## 1. Identify every application input path

The application should maintain a clear understanding of all ways information can enter or influence it.

This normally includes:

- browser forms;
- URL paths;
- query parameters;
- HTTP headers;
- cookies;
- thick-client requests;
- API requests;
- service-to-service calls;
- message queues and event streams;
- file uploads;
- attachments;
- archives;
- batch imports;
- database imports;
- report parameters;
- search terms;
- workflow actions;
- administrator consoles;
- configuration files;
- environment variables;
- command-line parameters;
- scheduled jobs;
- integration feeds;
- callback and webhook data;
- supplier support packages;
- data migrations;
- clipboard or drag-and-drop functions;
- generated identifiers;
- scanned documents;
- external device data where applicable;
- imported templates;
- plugins and scripts; and
- data restored from backup or recovery media.

A path should not be omitted because it is “internal”, “admin-only” or rarely used.

## 2. Define an input-validation specification

For each material input, the application should define what is permitted.

The specification should identify:

- field or object name;
- business meaning;
- source;
- expected data type;
- format;
- character set;
- encoding;
- minimum and maximum length;
- numeric range;
- precision;
- permitted values;
- required and optional status;
- null handling;
- whitespace handling;
- date and time rules;
- timezone assumptions;
- identifier format;
- file type;
- schema;
- permitted relationships;
- business rules;
- cross-field rules;
- source trust requirements;
- canonical form;
- error behaviour; and
- security sensitivity.

Validation rules should be based on the approved business and technical specification, not improvised in individual code paths.

## 3. Use allow-list validation

Where practical, the application should define what is valid rather than trying to enumerate every invalid value.

Examples include:

- accepted enumeration values;
- approved file formats;
- valid workflow transitions;
- valid identifier patterns;
- permitted API methods;
- expected JSON or XML schemas;
- approved destination identifiers;
- allowed date formats;
- valid project codes;
- permitted report parameters;
- approved callback destinations; and
- accepted character sets.

Blocklists may supplement validation but should not be the primary control because attackers can often vary encoding, syntax and representation.

## 4. Validate at the trusted server or service layer

Client-side checks improve usability but are not a security boundary.

The application should enforce validation in the trusted component that performs the operation, such as:

- server-side application logic;
- API service;
- message consumer;
- import service;
- batch processor;
- database procedure;
- file-processing service; or
- controlled thick-client back-end service.

The application should assume that:

- browser scripts can be disabled;
- requests can be replayed;
- thick clients can be modified;
- APIs can be called directly;
- hidden fields can be changed;
- local configuration can be edited;
- messages can be forged; and
- user interfaces can be bypassed.

Every material input should be revalidated at the point of use.

## 5. Validate data type and structure

The application should reject values that do not match the expected type or structure.

This includes:

- numbers supplied as arbitrary text;
- malformed dates;
- unexpected arrays or objects;
- duplicate JSON properties;
- invalid XML structure;
- additional unrecognised fields;
- missing mandatory fields;
- incorrect nesting;
- malformed identifiers;
- invalid enumerations;
- truncated data;
- unexpected binary content;
- mixed encodings; and
- malformed protocol messages.

Schema validation should be strict enough to reject unexpected structure rather than silently ignore dangerous fields.

## 6. Validate length, size and quantity

The application should define limits for:

- field length;
- request size;
- file size;
- number of files;
- array length;
- object depth;
- archive depth;
- number of records;
- query result size;
- page size;
- batch size;
- message size;
- report range;
- number of recipients;
- number of workflow actions;
- number of retries;
- number of nested references; and
- expanded archive size.

Limits help prevent:

- buffer and parser failures;
- denial of service;
- memory exhaustion;
- storage exhaustion;
- excessive processing;
- unexpectedly broad exports;
- queue flooding; and
- abuse of bulk functions.

## 7. Validate numeric range and precision

Numeric input should be checked for:

- minimum;
- maximum;
- sign;
- precision;
- scale;
- rounding;
- overflow;
- underflow;
- scientific notation;
- non-finite values;
- leading sign characters;
- locale-specific separators;
- currency precision where applicable;
- unit;
- consistency with related fields; and
- safe conversion between types.

The application should prevent integer overflow, truncation and business-rule bypass caused by extreme or specially represented values.

## 8. Validate dates and times

Date and time input should be checked for:

- valid calendar date;
- approved format;
- timezone;
- daylight-saving assumptions;
- range;
- ordering;
- future or historic limits;
- start and end consistency;
- expiry;
- leap years;
- ambiguous local formats;
- epoch conversion;
- timestamp precision; and
- consistency with workflow state.

The application should not silently reinterpret an invalid or ambiguous date.

## 9. Normalise before validation where necessary

Equivalent values can be represented in different ways.

The application should define safe canonicalisation for:

- Unicode;
- case;
- whitespace;
- line endings;
- path separators;
- hostname representation;
- URL encoding;
- percent encoding;
- HTML entities;
- XML entities;
- numeric representation;
- date representation;
- filename characters;
- internationalised domain names; and
- repeated encoding.

The order matters. The application should not validate one representation and later decode it into a different, unsafe value.

Normalisation should be deliberate and tested. It should not silently alter business-critical information without informing the user.

## 10. Validate character sets and encoding

The application should:

- use defined encodings;
- reject invalid byte sequences;
- avoid ambiguous encoding conversion;
- restrict control characters;
- handle null bytes safely;
- handle bidirectional text safely where relevant;
- define permitted line breaks;
- prevent encoding-based filter bypass;
- preserve legitimate international text; and
- test non-ASCII values.

Validation should not assume that all legitimate organisational data is limited to ASCII unless the business specification explicitly requires it.

## 11. Use context-appropriate output handling as well

Input validation does not replace secure output handling.

The application should also use the protection required by the destination context, such as:

- parameterised database queries;
- HTML output encoding;
- JavaScript-safe encoding;
- URL encoding;
- LDAP-safe construction;
- operating-system command avoidance or safe invocation;
- XML-safe construction;
- CSV and spreadsheet formula protection;
- safe log formatting; and
- safe file-path handling.

A valid surname may still require HTML encoding before display. A valid search term should still be used through a parameterised query.

## 12. Prevent injection

The application should prevent input from being interpreted as commands, queries, code or control syntax.

Relevant injection classes include:

- SQL injection;
- operating-system command injection;
- code injection;
- template injection;
- expression-language injection;
- LDAP injection;
- XML query injection;
- log injection;
- email header injection;
- HTTP response splitting;
- spreadsheet formula injection;
- path injection;
- script injection;
- regular-expression injection;
- configuration injection; and
- message or protocol injection.

Controls should combine:

- strict validation;
- parameterisation;
- safe APIs;
- least privilege;
- context-specific encoding;
- avoidance of dynamic execution; and
- negative security testing.

## 13. Prevent path traversal and unsafe file references

File and path input should be checked for:

- parent-directory sequences;
- absolute paths;
- alternate separators;
- encoded traversal;
- null characters;
- device names;
- symbolic link behaviour;
- network paths;
- drive letters;
- reserved names;
- excessive path length;
- case ambiguities;
- unexpected extensions; and
- canonical path outside the approved storage root.

The application should generate server-side storage identifiers rather than use user-supplied filenames as trusted paths.

## 14. Validate filenames

User-supplied filenames should be treated as metadata, not trusted storage paths.

The application should:

- restrict length;
- remove or reject path components;
- reject control characters;
- handle Unicode safely;
- prevent duplicate confusion;
- restrict extensions;
- verify content separately;
- generate internal object identifiers;
- avoid overwriting existing files;
- protect display contexts;
- prevent spreadsheet or shell metacharacter issues; and
- preserve the original name only where needed for business use.

## 15. Validate file type and content

The application should not rely only on the filename extension or client-provided media type.

It should consider:

- extension;
- declared media type;
- file signature;
- actual structure;
- permitted format;
- active content;
- embedded objects;
- macro content;
- encrypted or password-protected status;
- archive content;
- nested files;
- file size;
- parser safety;
- malformed structure;
- malicious-code scanning; and
- expected business content.

Unsupported, ambiguous, malformed or unscannable content should be rejected or held safely.

## 16. Validate archives

Archive processing should enforce:

- permitted archive types;
- maximum archive size;
- maximum expanded size;
- maximum file count;
- maximum nesting depth;
- duplicate filename handling;
- path traversal protection;
- symbolic-link restrictions;
- encrypted archive policy;
- prohibited file types;
- malicious-code scanning;
- resource limits;
- safe temporary storage; and
- clean-up after failure.

The application should defend against archive bombs and extraction outside the intended directory.

## 17. Validate imported records

Bulk and batch imports should validate:

- file and schema;
- record count;
- field types;
- mandatory fields;
- identifiers;
- referential integrity;
- duplicate records;
- prohibited changes;
- project or information scope;
- permissions;
- business rules;
- record sequencing;
- totals and reconciliation;
- encoding;
- transaction boundaries;
- partial failure; and
- rollback.

The application should not permit an import to bypass validation that applies to ordinary user entry.

## 18. Validate API input

API validation should cover:

- method;
- route;
- headers;
- authentication context;
- content type;
- request schema;
- required and optional fields;
- unexpected fields;
- object identifiers;
- field ownership;
- field-level authorisation;
- pagination;
- filters;
- sorting;
- batch size;
- callback destinations;
- idempotency keys;
- replay data;
- request size;
- rate limits; and
- business rules.

The application should defend against mass assignment by explicitly defining which fields a caller may set.

## 19. Validate message and event input

Messages from enterprise brokers should still be treated as untrusted application input.

The consumer should validate:

- producing identity;
- approved queue or topic;
- schema version;
- message type;
- mandatory fields;
- business context;
- project or partition;
- sequence;
- timestamp;
- replay;
- duplicate delivery;
- correlation identifier;
- message size;
- data classification;
- digital signature or integrity where used;
- expiry;
- authorised operation; and
- dead-letter behaviour.

A message should not alter application state merely because it arrived through an approved broker.

## 20. Validate service-to-service input

Internal services should validate:

- caller identity;
- token audience and scope;
- expected operation;
- request schema;
- data scope;
- destination component;
- transaction identifier;
- replay controls;
- time validity;
- content;
- rate;
- error behaviour; and
- version compatibility.

Network location and mutual TLS establish part of the trust context but do not prove that every supplied field is valid.

## 21. Validate thick-client input

A thick client running on a managed Windows device should not be trusted to enforce security rules by itself.

The server should validate:

- user identity;
- client version where relevant;
- request type;
- field values;
- record identifiers;
- role and project scope;
- workflow transition;
- file content;
- request sequence;
- replay;
- size;
- destination;
- configuration values; and
- privileged operations.

The application should assume that requests can be created without using the official client.

## 22. Validate object and record identifiers

Identifiers should be checked for:

- format;
- existence;
- correct object type;
- ownership;
- project or tenant scope;
- current lifecycle state;
- relationship to the parent object;
- authorised user access;
- non-reuse where required; and
- resistance to enumeration.

A valid identifier is not automatically an authorised identifier.

## 23. Validate cross-field and cross-record consistency

Individual fields may each be valid while the combination is not.

The application should validate relationships such as:

- start date before end date;
- status consistent with workflow stage;
- project consistent with parent record;
- approver different from originator;
- supplier consistent with contract;
- currency consistent with amount fields;
- user consistent with assigned organisation;
- attachment classification consistent with parent record;
- destination consistent with information-handling rules;
- quantity consistent with permitted limits;
- child record consistent with parent ownership; and
- release state consistent with completed approvals.

## 24. Validate workflow transitions

The application should enforce:

- permitted current state;
- permitted next state;
- authorised role;
- required approvals;
- required fields;
- separation of duties;
- record ownership;
- prerequisite tasks;
- valid timing;
- no skipped stages;
- no replay of completed transitions;
- no unauthorised rollback;
- no direct status manipulation; and
- complete audit history.

A submitted status value should not be accepted merely because it is a valid enumeration.

## 25. Validate privileged and administrative input

Administrative interfaces should use at least the same validation standard as user interfaces.

This includes:

- role names;
- permission mappings;
- identity-provider configuration;
- URLs and endpoints;
- certificates;
- file paths;
- regular expressions;
- scripts;
- command parameters;
- scheduling expressions;
- report queries;
- logging configuration;
- retention values;
- feature flags;
- file-type rules; and
- import tools.

Administrative access does not make malformed or dangerous input safe.

## 26. Validate configuration input

Configuration should be checked before activation or deployment.

The application should validate:

- schema;
- mandatory values;
- allowed values;
- endpoint format;
- environment;
- duplicate keys;
- secret references;
- certificate references;
- numeric limits;
- file paths;
- feature dependencies;
- incompatible settings;
- logging requirements;
- production/non-production separation;
- destination allow-lists; and
- safe fallback.

Invalid configuration should fail deployment or remain inactive rather than create a partially secure state.

## 27. Validate redirects, callbacks and URLs

Where the application accepts URLs or destinations, it should validate:

- approved scheme;
- approved host;
- approved port;
- destination allow-list;
- DNS resolution;
- redirects;
- loopback and link-local addresses;
- unapproved internal ranges;
- credentials in URLs;
- path;
- query parameters;
- fragment handling;
- internationalised hostnames;
- maximum length;
- response size;
- timeout; and
- intended business purpose.

This helps prevent open redirects, server-side request forgery and data transfer to arbitrary destinations.

## 28. Validate search and filtering input

Search, sort and filter functions should:

- restrict permitted fields;
- restrict operators;
- limit complexity;
- limit wildcard use;
- limit result scope;
- limit date ranges;
- limit page size;
- enforce project and record access;
- parameterise queries;
- prevent arbitrary query-language injection;
- set timeouts;
- handle invalid syntax safely; and
- avoid detailed internal error disclosure.

## 29. Validate report parameters

Reports can create excessive disclosure or resource consumption.

The application should validate:

- report type;
- permitted user role;
- project or information scope;
- date range;
- field selection;
- recipient;
- output format;
- row limit;
- attachment inclusion;
- grouping;
- sorting;
- scheduled frequency;
- template;
- classification or marking; and
- export approval where required.

## 30. Validate identity and access-management input

Account and access functions should validate:

- target identity;
- identity source;
- role;
- project or group;
- approver;
- start date;
- expiry;
- incompatible roles;
- privileged status;
- service-account owner;
- scope;
- delegation;
- emergency status; and
- account lifecycle state.

The application should prevent arbitrary role names, privilege flags or project identifiers being supplied through a client or API.

## 31. Restrict inputs to trusted sources where required

Some operations should accept input only from approved sources.

Examples include:

- authoritative reference data;
- identity attributes;
- release artefacts;
- security configuration;
- supplier updates;
- vulnerability feeds;
- signing requests;
- workflow approvals;
- payroll or financial reference data;
- project membership;
- certificates;
- recovery packages; and
- cryptographic trust material.

Source controls may include:

- authenticated service identity;
- digital signature;
- approved repository;
- registered API client;
- controlled file-transfer location;
- certificate validation;
- message topic restriction;
- checksum;
- provenance record; and
- change approval.

A trusted source does not remove the need to validate format and content.

## 32. Reject unexpected fields and functions

The application should consider rejecting, rather than ignoring:

- unknown JSON properties;
- unsupported XML elements;
- hidden administrative flags;
- obsolete fields;
- duplicate parameters;
- alternate parameter names;
- deprecated API functions;
- fields not permitted for the caller;
- client-supplied ownership fields;
- client-supplied privilege fields; and
- server-managed timestamps or status fields.

Silently accepting unexpected fields can enable mass assignment, downgrade and future compatibility weaknesses.

## 33. Handle invalid input predictably

When input is invalid, the application should:

- reject the operation;
- preserve transaction integrity;
- avoid partial update;
- avoid unsafe default values;
- avoid executing downstream actions;
- provide a clear but non-sensitive user message;
- log the security-relevant reason;
- identify the affected field where appropriate;
- avoid revealing internal implementation;
- avoid echoing dangerous content unsafely;
- prevent repeated processing;
- support correction; and
- preserve evidence when malicious activity is suspected.

The outcome should be defined and testable.

## 34. Review and resolve input errors

Where NIST enhancement requirements or application risk warrant it, the application should support controlled review and resolution of input errors.

Examples include:

- batch import exceptions;
- rejected authoritative feeds;
- malformed supplier files;
- invalid engineering records;
- failed data migrations;
- message dead-letter queues;
- data-quality exceptions;
- invalid workflow requests; and
- unprocessable attachments.

The process should identify:

- input source;
- reason;
- affected records;
- business impact;
- owner;
- correction authority;
- whether resubmission is allowed;
- whether security escalation is required;
- evidence;
- resolution; and
- prevention of unauthorised manual override.

## 35. Avoid unsafe automatic correction

Automatic correction can create ambiguity or security issues.

The application should be cautious about:

- truncating values;
- removing characters;
- changing identifiers;
- defaulting missing values;
- coercing data types;
- changing dates;
- fixing filenames;
- silently dropping fields;
- changing project assignment;
- converting negative values;
- normalising business text; and
- treating failed parsing as zero, null or false.

Safe normalisation is useful, but material business changes should be visible and controlled.

## 36. Protect error messages

Validation errors should not disclose:

- database queries;
- stack traces;
- source paths;
- internal class names;
- schema internals;
- secrets;
- full tokens;
- server details;
- privileged role names;
- hidden fields;
- sensitive record existence;
- complete rejected content; or
- exploit-relevant parser information.

Detailed diagnostic data should be available only through protected logs or support tools.

## 37. Rate-limit repeated invalid input

Repeated invalid submissions may indicate abuse or can cause resource exhaustion.

The application should consider:

- per-user rate limits;
- per-client limits;
- per-session limits;
- per-endpoint limits;
- request-size limits;
- progressive delay;
- queue limits;
- temporary blocking;
- alerting;
- circuit breaking; and
- support escalation.

Rate limiting should be proportionate and should not permit easy denial of service against legitimate users.

## 38. Prevent parser and validation resource exhaustion

Validation itself can be attacked.

The application should protect against:

- deeply nested JSON or XML;
- entity expansion;
- catastrophic regular expressions;
- huge numeric values;
- decompression bombs;
- recursive object graphs;
- excessively complex schemas;
- oversized images;
- pathological document files;
- excessive redirects;
- long-running validation queries;
- enormous multipart requests; and
- repeated failed conversion.

Controls may include:

- depth limits;
- timeouts;
- memory limits;
- streaming;
- safe parser configuration;
- entity restrictions;
- archive limits;
- bounded regular expressions;
- isolated conversion services; and
- cancellation.

## 39. Protect validation rules and schemas

Validation controls are security-critical configuration.

The application should restrict changes to:

- schemas;
- file-type allow-lists;
- length and range limits;
- regular expressions;
- approved value sets;
- transformation rules;
- parser configuration;
- destination allow-lists;
- workflow rules;
- batch templates;
- import mappings; and
- error handling.

Changes should be:

- approved;
- attributable;
- tested;
- versioned;
- logged;
- reversible; and
- included in CM-02, CM-05 and CM-06 processes.

## 40. Use shared validation components carefully

Reusable validation libraries can improve consistency, but the application should ensure that they:

- are supported;
- are appropriate for the context;
- do not perform unsafe coercion;
- are configured securely;
- are versioned;
- are tested;
- handle Unicode and encoding correctly;
- fail safely;
- do not suppress errors;
- are included in dependency monitoring; and
- do not replace business-rule validation.

A generic string validator cannot determine whether a user is allowed to assign a record to a particular project.

## 41. Validate data after transformation

Information should be revalidated when its form or trust context changes.

Examples include:

- archive extraction;
- document conversion;
- decoding;
- decryption;
- deserialisation;
- format conversion;
- data migration;
- message transformation;
- report generation;
- spreadsheet import;
- image processing;
- copying between projects;
- combining data sources; and
- restoring old records into a new version.

Validation performed before a transformation may not be sufficient for the output.

## 42. Validate data before security-relevant decisions

The application should validate information before using it to determine:

- identity;
- role;
- project;
- access;
- approval;
- destination;
- classification;
- workflow state;
- retention;
- deletion;
- release;
- export;
- payment;
- signing;
- routing;
- logging level;
- feature enablement; or
- code or command execution.

Security decisions should not depend on unchecked client-supplied claims.

## 43. Preserve provenance for imported information

Where input comes from another system or file, the application should retain enough provenance to establish:

- source;
- sender;
- import or transaction identifier;
- time;
- schema or version;
- validation result;
- transformation applied;
- records created or changed;
- approval;
- error status; and
- reconciliation outcome.

Provenance supports incident investigation, correction and accountability.

## 44. Log significant validation activity

The application should generate useful events for:

- rejected input;
- schema failure;
- file-type rejection;
- malformed message;
- invalid identifier;
- cross-project mismatch;
- excessive size;
- prohibited field;
- injection signature or behaviour;
- archive limit breach;
- callback or destination rejection;
- failed transformation;
- repeated invalid input;
- administrative validation-rule change;
- manual override;
- import exception; and
- validation service failure.

Events should include:

- acting user or service;
- source;
- interface;
- validation category;
- target function;
- time;
- outcome;
- correlation identifier;
- component;
- relevant field or object without unnecessary sensitive content; and
- incident or support reference where applicable.

The application should not log full malicious payloads, passwords, tokens or restricted content unnecessarily.

## 45. Monitor validation failures

The application should support detection of:

- repeated injection attempts;
- systematic parameter tampering;
- invalid identifiers across many records;
- repeated cross-project attempts;
- malformed API traffic;
- unusual file-type submissions;
- archive bombs;
- repeated callback rejections;
- sudden increase in import errors;
- supplier feed schema drift;
- validation-rule changes;
- validation disabled;
- high rates of unknown fields;
- parser crashes;
- unusual resource consumption; and
- invalid input followed by successful privileged action.

## 46. Test input validation systematically

Testing should include:

- valid boundary values;
- below-minimum and above-maximum values;
- empty and null values;
- very long values;
- invalid types;
- negative values;
- overflow values;
- Unicode;
- mixed encoding;
- control characters;
- duplicate fields;
- unexpected fields;
- malformed JSON and XML;
- SQL and command metacharacters;
- script content;
- path traversal;
- invalid identifiers;
- unauthorised object references;
- invalid workflow transitions;
- oversized files;
- malformed files;
- mismatched extensions and content;
- nested archives;
- archive bombs;
- invalid API versions;
- mass assignment;
- invalid callbacks;
- replay;
- duplicate messages;
- invalid configuration;
- validation-service failure;
- direct API calls;
- thick-client manipulation; and
- safe error handling.

Testing should verify the server-side result, audit event and transaction state.

## 47. Use automated security testing in the SDLC

For developed or configured applications, the SDLC should include proportionate:

- unit tests for validators;
- property-based or fuzz testing;
- API schema tests;
- negative test suites;
- static analysis;
- dynamic testing;
- dependency scanning;
- parser testing;
- file corpus testing;
- security regression tests;
- penetration testing; and
- release gates for critical validation failures.

NIST’s Secure Software Development Framework recommends integrating practices that reduce software vulnerabilities throughout development rather than relying on end-stage testing alone.

## 48. Fuzz high-risk parsers and interfaces

Fuzz testing is particularly valuable for:

- file parsers;
- document converters;
- image processors;
- protocol decoders;
- API parsers;
- deserialisation functions;
- archive processors;
- thick-client protocol handlers;
- message consumers; and
- complex import routines.

Fuzz testing should be authorised, safely isolated and linked to defect remediation.

## 49. Review validation after change

Validation should be reassessed after:

- new field;
- new file type;
- new API;
- new message version;
- new integration;
- new report;
- new workflow state;
- new thick-client function;
- parser or framework update;
- product upgrade;
- data migration;
- supplier feed change;
- configuration change;
- vulnerability disclosure;
- incident;
- penetration-test finding; or
- change to business rules.

## 50. Manage validation limitations

Where a legacy or commercial product cannot provide the expected validation, record:

- affected input;
- expected rule;
- actual behaviour;
- source;
- function;
- information or business impact;
- exploitability;
- compensating controls;
- monitoring;
- owner;
- approval;
- supplier position;
- remediation, isolation, upgrade or replacement plan; and
- review or expiry date.

Examples include:

- permissive import parser;
- inability to reject unknown fields;
- unsafe automatic coercion;
- weak file validation;
- unbounded report parameter;
- validation only in the thick client;
- inability to limit archive expansion;
- weak API schema enforcement;
- unsupported parser; or
- business-rule validation performed only manually.

The limitation should be recorded in the application addendum or risk process.

---

## Sensible minimum for an ordinary internal application

The estimates below are indicative application-team effort for a typical internal application that already uses corporate SDLC, identity, API, logging and testing services. They exclude enterprise platform engineering and major redevelopment of legacy products.

| Minimum requirement | How this is achieved | Where to record the evidence | Estimated effort |
|---|---|---|---:|
| **1. Identify all input paths and high-risk parsers** | Map browser, thick-client, API, message, file, batch, configuration, report and administrative inputs and identify where inputs can affect security or business state. | Summarise scope in the **SSP SI-10 statement** and maintain detail in the existing **architecture**, **data-flow diagrams**, **interface specifications**, **ConOps** or **SyOps**. | **6–12 hours** |
| **2. Define validation requirements for material inputs** | Specify allowed type, format, length, range, values, schema, source, business rules and failure behaviour. | Record requirements in the **business and security requirements**, **data dictionary**, **API/interface specification**, **file format specification**, **workflow design** and **SSP**. | **12–28 hours** |
| **3. Enforce validation at the trusted server or service layer** | Revalidate all material inputs server-side and prevent reliance on browser, thick-client or caller-side checks. | Capture enforcement points in the **security design**, **technical design**, **SDLC backlog** and **SSP**. Retain evidence in the normal **security test report**. | **16–48 hours** |
| **4. Use allow-list, type, length, range and schema checks** | Apply strict accepted formats, reject unexpected fields, constrain quantity and size, and handle null, encoding and canonicalisation safely. | Record rules in the **data model**, **schema definitions**, **validation library configuration**, **CM-06 configuration** and **test cases**. | **12–32 hours** |
| **5. Prevent injection using safe APIs and context-specific handling** | Use parameterised queries, safe process invocation, output encoding and controlled template construction in addition to validation. | Evidence sits in the **secure coding standard**, **code review**, **SAST results**, **technical design** and **security test report**. | **12–40 hours** |
| **6. Validate files, archives and imports where applicable** | Verify actual format, size, structure, archive limits, paths, active content, malware status, records, reconciliation and rollback. | Record controls in the **file-processing design**, **import specification**, **SI-03 design**, **SyOps**, **test plan** and **security test report**. | **12–36 hours** |
| **7. Validate APIs, messages and service inputs** | Authenticate source, validate schema, permitted fields, identifiers, business scope, replay, duplicates, size and version. | Use the existing **API specification**, **message schema**, **interface control document**, **service design** and **integration/security test report**. | **16–40 hours** |
| **8. Validate identifiers, object relationships and workflow state** | Confirm object existence, ownership, project scope, parent-child relationship, allowed transition, approvals and separation of duties. | Capture requirements in the **data model**, **workflow design**, **AC-03/AC-04/AC-05 specifications**, **SDLC backlog** and **test evidence**. | **12–32 hours** |
| **9. Validate configuration and privileged administrative input** | Check schemas, endpoints, certificate references, ranges, dependencies and prohibited values before security-relevant settings become active. | Record controls in the **CM-06 configuration specification**, **administration design**, **change record**, **deployment tests** and **SSP**. | **8–20 hours** |
| **10. Define predictable invalid-input and error handling** | Reject or safely hold invalid input, prevent partial updates, provide non-sensitive messages, preserve integrity and route correctable errors for controlled resolution. | Record behaviour in the **error-handling design**, **SyOps**, **import or interface runbook**, **SSP** and **resilience/security test report**. | **8–20 hours** |
| **11. Protect validation rules and schemas from unauthorised change** | Version, approve, test, log and restrict changes to schemas, allow-lists, parser settings, mappings and limits. | Use the existing **CM-02 baseline**, **CM-05 change restrictions**, **CM-06 configuration**, **source repository** and **change/release records**. | **6–16 hours** |
| **12. Log and monitor significant validation failures** | Generate events for malformed input, injection attempts, invalid identifiers, file rejection, size breaches, schema drift and validation-rule changes. | Define events in the **SSP AU-02/SI-04/SI-10 sections** and existing **event specification**. Verify through **SIEM onboarding** and the **security test report**. | **6–16 hours** |
| **13. Test boundary, malformed and bypass cases** | Test valid boundaries, invalid types, encoding, unknown fields, injection, paths, files, archives, APIs, workflows, direct calls and service failure. | Add cases to the normal **unit**, **integration**, **security**, **operational acceptance** and **penetration test plans**, retaining outcomes in established reports. | **20–48 hours per major test cycle** |
| **14. Add automated validation regression tests** | Maintain unit, negative, schema, API and high-risk parser tests and run them through the normal build or release pipeline. | Evidence remains in the **test repository**, **CI/CD history**, **release evidence pack**, **defect tracker** and **SA-11 testing records**. | **12–32 hours initially** |
| **15. Review validation after material change** | Reassess rules and tests when fields, interfaces, files, workflows, suppliers, parsers or business rules change. | Add the review to the standard **change-impact assessment**, **security design review**, **release checklist** or **post-implementation review**. | **3–8 hours per material change** |
| **16. Document and manage validation limitations** | Record client-only checks, weak parser behaviour, permissive imports, unsupported schemas or other product constraints with compensating controls and remediation. | Use the existing **risk register**, **problem record** or **application addendum**, referenced from the **SSP SI-10 statement**. | **4–10 hours per limitation** |

### Indicative total

For a typical internal application with several forms, APIs and ordinary file handling, initial application effort is commonly around **150–350 hours**.

A simple commercial application with a small number of well-defined inputs may require less. A custom engineering, records or integration-heavy platform with thick clients, complex files, many APIs, batch imports and configurable workflows may require substantially more.

The estimates should not be added mechanically where work overlaps. SI-10 commonly shares requirements, implementation and evidence with:

- AC-03 access enforcement;
- AC-04 information-flow enforcement;
- AC-05 separation of duties;
- SC-07 boundary protection;
- SI-03 malicious-code protection;
- SI-07 software integrity;
- RA-05 vulnerability monitoring;
- SA-11 developer testing;
- AU-02 event logging; and
- SI-04 system monitoring.

---

## Suggested document placement

To avoid creating disconnected evidence, input-validation information should normally be distributed across established application and SDLC artefacts:

- **SSP:** SI-10 implementation approach, input categories, inherited enterprise services, validation principles, logging, testing and limitations.
- **ConOps or SyOps:** import operations, file handling, error resolution, failed feeds, operational overrides and support responsibilities.
- **Security and solution architecture:** input paths, trust boundaries, parsers, validation services and downstream execution points.
- **Data-flow diagrams:** users, files, APIs, messages, integrations, transformations and storage.
- **Data dictionary and data model:** types, ranges, lengths, enumerations, null handling, ownership and cross-field rules.
- **Business and security requirements:** permitted values, workflow conditions, source restrictions and error behaviour.
- **API specifications:** schemas, methods, fields, limits, object relationships, unexpected-field handling and errors.
- **Interface control documents:** message, file, batch and service input requirements.
- **File and import specifications:** permitted formats, archive limits, record checks, reconciliation and rollback.
- **Workflow design:** valid states, transitions, approvals, record scope and prohibited actions.
- **CM-06 configuration:** schema versions, parser settings, size limits, file types, allow-lists and destination controls.
- **Secure coding standard and technical design:** safe APIs, parameterisation, canonicalisation and output handling.
- **Source and test repositories:** validation logic, unit tests, negative tests, fuzz tests and regression cases.
- **CI/CD and release evidence:** SAST, test results, failed gates and approved artefacts.
- **AU-02 and SI-04 evidence:** validation events, anomalies, alerts and event-flow health.
- **Security and penetration-test reports:** injection, parser, API, file and business-rule findings.
- **Change and release records:** validation-rule changes, schema changes and post-deployment verification.
- **Risk register or application addendum:** weak product validation, unsupported parsers, client-only enforcement and compensating controls.

---

## What remains an enterprise responsibility

The application should normally inherit, rather than reproduce:

- organisation-wide secure coding standards;
- enterprise web application firewall services;
- enterprise API gateway platforms;
- corporate malware-scanning services;
- network boundary protection;
- enterprise identity and authentication;
- managed Windows EUC controls;
- enterprise database-platform hardening;
- centrally managed development and build platforms;
- corporate vulnerability scanning;
- enterprise penetration-testing governance;
- central SIEM and SOC operations;
- organisation-wide incident response;
- enterprise change and release policy; and
- corporate risk and exception governance.

The application team must still:

- identify all application-specific input paths;
- define accepted data and business rules;
- implement trusted server-side validation;
- prevent injection and parser abuse;
- validate files, APIs, messages, identifiers and workflows;
- fail safely;
- protect validation configuration;
- log and test validation behaviour;
- review rules after change; and
- formally manage product limitations.

> **Key dividing line:** the enterprise provides shared security platforms and development standards; the application defines and enforces what constitutes valid information for each application function and refuses to process information that does not satisfy those rules.

---

## References

1. National Institute of Standards and Technology, **NIST SP 800-53 Rev. 5, Release 5.2.0, Security and Privacy Controls for Information Systems and Organizations**, SI-10 Information Input Validation.
2. National Institute of Standards and Technology, **NIST SP 800-53A Rev. 5, Release 5.2.0, Assessing Security and Privacy Controls in Information Systems and Organizations**, SI-10 assessment procedures.
3. National Institute of Standards and Technology, **NIST SP 800-218, Secure Software Development Framework Version 1.1: Recommendations for Mitigating the Risk of Software Vulnerabilities**.
4. National Institute of Standards and Technology, **NIST SP 800-95, Guide to Secure Web Services**.
5. National Institute of Standards and Technology, **NIST Cybersecurity and Privacy Reference Tool**, current SI-10 control and assessment content.
