# GMS & GQ Domain Data (WORK IN PROGRESS - OCT 13 10:30)
This document is a work in progress and subject to rapid change. Its purpose is to define, test, refine, and iterate as the first data products are developed.

## Vision, Strategy & Purpose

### Vision & Goals
We are shifting our focus from **collecting data** to **creating value with data**. In the past, much of our information lived in silos, quality signals were unclear, access was cumbersome, and assets were built for one-off use. Our vision is to publish **clean, well-described data products** that people trust, can find easily, and can reuse across teams and processes. Quality is **systematically enforced**—not negotiated per project—so that the same dataset is safe for analytics, regulatory needs, and AI. Standards let us **scale without heroics**, while clear end‑to‑end ownership ensures accountability for meaning, quality, and change. Most importantly, we focus on **business outcomes**: faster decisions, fewer reconciliations, and more time spent acting on insights instead of hunting for them. We move from raw **volume** to durable **value**.

### Guiding Principles
- **Data as a product (quality by design).** Treat datasets like products with customers. Each product has an explicit purpose, an owner, a contract (schema, semantics, SLOs), documentation, and observability. Designing for trust and reuse up front prevents rework and makes adoption straightforward for analysts, applications, and AI.

- **Domain‑oriented business ownership.** The people closest to the process define the language, rules, and timelines. Domains publish their own data products and are accountable for quality and meaning. This reduces translation errors, shortens decision cycles, and aligns data change to business change.

- **Federated, globally aligned governance (computational).** We keep one set of enterprise standards (naming, access, lineage, privacy/GxP, quality KPIs) and **encode them as automated checks**. Domains stay autonomous, while the platform enforces policy consistently in CI/CD and at query time. Compliance scales because governance is executed by code, not by meetings.

- **Highly automated, AI‑enabled self‑serve platform.** Common rails for ingestion, transformation, testing, documentation, lineage, access control, and cost/quality observability are provided as self‑service. Automation captures metadata by default, flags drift and anomalies early, and speeds safe releases. AI assists with harmonization and anomaly detection, raising the baseline for quality across products.

### Primary and Secondary Use of Data

In manufacturing and quality, **primary use** means data are recorded to run operations through transactions: batches executed in MES, QC results in LIMS, deviations and CAPAs in QMS, material and supplier records in ERP, and equipment data in CMMS. This is data captured and controlled for the process and task it was originally created to serve under GMP/GDP and local procedures - where applicable. Regulators such as EMA distinguishes this operational processing from any other reuse.

**Secondary use** is everything we do with those operational data beyond their original intent—cross‑site trending and CPV, APR/PQR, stability and specification trend analysis, supplier performance analytics, deviation/CAPA effectiveness reviews, inspection‑readiness packs, enterprise decision‑making and so forth. For each of these, suitability must be shown as **fitness for purpose** for the specific question, with checks along the evidence lifecycle from requirements through processing, publication, selection, and consumption.

Secondary use is challenging because the data were captured for another reason; masking identifiers can remove signals needed for some checks; and linking sources to improve completeness introduces matching and coherence risks. These realities require explicit documentation, measurable quality indicators, and re‑assessment when data are repurposed.

### From “Volume” to “Value”

We convert heterogeneous operational records into consumption‑ready, inspection‑ready **data products** that are easy to discover, trustworthy to reuse, and clearly fit for the intended decision. The pipeline rests on five key components aligned with regulators guidance such as EMA’s quality dimensions—**reliability, extensiveness, coherence, timeliness, and relevance**—and with its separation of foundational, intrinsic, and question‑specific determinants.

#### Business Rules

Operational rules are encoded as executable checks so data arrive **correct, complete, unique, timely, and coherent** before they flow downstream. In GMS & GQ this covers Critical Data Elements for Batches, Materials, Product Specifications, Samples, Tests, Equipment, Deviations, and CAPAs; conformance to specifications and status sequencing; referential integrity from Batch→Step→Equipment and Sample→Test→Result; deduplication; and freshness SLOs for release‑critical flows. These controls are intrinsic measurements of quality and reflect the kind of automated plausibility and conformance checks expected for datasets used in decisions.

#### Business Glossary

A shared vocabulary removes ambiguity across sites and systems. Terms such as **Batch**, **OOS**, **OOT**, **Specification**, **CoA**, **CAPA**, **Stage**, and **Site** carry one governed meaning, with ownership, usage notes, and mappings to the fields and rules that implement them. Publishing these semantics in the catalog helps assess fitness for purpose without revealing the data themselves and strengthens the coherence of any secondary‑use analysis.

#### Golden Master Data Management

Mastered identifiers and reference values allow us to link records reliably across LIMS, MES, QMS, and ERP. Material and product masters (with specifications), sites and equipment, methods, suppliers, units, statuses, and reason codes are matched, merged, and versioned with auditable survivorship. This improves **uniqueness**, **coherence** and **interoperability** and reduces the linkage errors that often appear when multiple sources are combined for secondary use.

#### Semantics & Ontology

We model the core entities and relationships of GMS & GQ—*Batch → Process Step → Equipment*, *Sample → Test → Result → Specification*, *Deviation → CAPA → Effectiveness*—and align them to shared code systems. This harmonisation enables interoperability across products while documenting any precision trade‑offs introduced by mappings (for example, timestamp granularity reduced when moving to a common model). Transparency about these trade‑offs is critical.

#### Data Cleansing & Harmonisation

Unit conversions, code normalisation, time‑zone handling, deduplication, logic for late‑arriving data, and justified imputations are implemented as reproducible pipelines with **lineage**. Transformations, tests, KPIs, and provenance are recorded so consumers—and auditors—can understand what changed and why. Pipelines surface incident trends and provide objective evidence that data remain fit for their stated use.

#### Data Cleansing & Harmonisation

TBD - lorem ipsum


#### The Data Product

Each product is a governed, reusable asset — API/SQL plus a rich catalog entry—that declares **intended uses**, ownership and stewardship, **refresh and availability SLOs**, schema and semantics, rule thresholds, versioning, and **lineage** from source to product. Intrinsic quality telemetry dimensions is published with the product, so fitness‑for‑purpose can be judged quickly for CPV, APR/PQR, stability trending, deviation/CAPA analytics, or inspection queries. Metadata that influence conclusions are treated as data and versioned.


#### Conclusion
Our concept replaces ad‑hoc extracts with **accountable data products** delivered inside clear **bounded contexts** and operated on a **self‑serve platform** under **federated, computational governance**. The aim is simple: make high‑quality, well‑owned, and interoperable data easy to discover and safe to reuse at scale.

**Bounded contexts give clarity and speed.** We organize around natural business seams—Quality, Manufacturing, Supply Chain—so that within each context, language and rules are unambiguous. Terms like “batch,” “deviation,” or “release” mean one thing inside the context. Ownership is real: Data Trustees safeguard meaning and rules; Product Owners manage the backlog and quality; Stewards keep operations healthy; System Owners ensure the originating systems remain fit‑for‑purpose. Because change is contained within a context, evolution is faster and safer.

**Data products are purposeful interfaces, not just tables.** A data product packages everything a consumer needs to use a concept confidently: the curated data, the code that shapes it, and the policies that govern it. It exposes a stable interface (SQL and/or APIs), comes with documentation, examples, lineage, and versioning, and makes guarantees about schema, semantics, timeliness, and quality. Consumers do not have to reverse‑engineer pipelines or reconcile inconsistent meanings across systems—the product encodes those concerns so others can move faster and safer.

**Contracts turn trust into something we can execute.** Every product declares a contract: canonical schema; critical data elements; mappings to controlled vocabularies and Golden Masters; validation and parsing rules; thresholds for completeness, validity, and freshness; access policies; and lineage expectations. Because the contract is machine‑readable, the platform can auto‑generate tests, enforce policies, route failed records to a dead‑letter queue, and publish telemetry on how the product is performing. Ambiguity is made explicit and enforceable; quality moves from slideware to code.

**The self‑serve platform removes toil and ensures consistency.** Teams build on shared rails for ingestion, transformation, testing, documentation, catalog registration, lineage capture, access control, and CI/CD. Conventions (naming, versioning, folder/DB layout), templates, and generators keep products consistent; observability is standardized so cost, freshness, and quality look the same across domains. Automation—profiling, schema‑drift detection, data‑quality checks, policy gating—lets domain teams focus on business logic rather than plumbing.

**Governance is federated and enforced by code.** Central policy sets the rules; domains decide how to meet them; the platform verifies compliance. Access is controlled with attribute‑based policies; privacy and GxP constraints are checked in pipelines and at query time; releases are gated by tests for completeness, validity, and lineage coverage. When a gate fails, diagnostics are immediate and actionable. This model keeps compliance strong while preserving domain agility, and it scales because the effort to govern the next ten products is similar to the effort to govern the last ten.

**Everything is observable and comparable.** Each product emits telemetry across key quality dimensions—availability, timeliness, completeness, validity, integrity, uniqueness, traceability, semantics, and more. These roll up into a clear maturity signal (e.g., a five‑star rating) that is published with the product in the catalog. Consumers get an honest view of fitness for purpose; Trustees and owners get an objective backlog prioritized by impact; leadership gets a cross‑domain view of where investment unlocks the most value.

**Semantics make reuse real and unlock AI.** Enumerations, codes, and labels are anchored in shared Golden Masters; token mappings are transparent and governed. Where meanings must diverge by context, those differences are declared instead of hidden. The payoff is fewer reconciliations, fewer disagreeing dashboards, and datasets that are genuinely **AI‑ready**—models can learn in one context and apply insight in another without brittle one‑off translations.

**Change is designed in.** Products are versioned; interfaces evolve in a backward‑compatible way when possible; deprecations are clear and time‑boxed. Contracts, pipelines, and policies are automated, so change is **safer**—schema drift is detected early, breaking changes fail fast, and promotions across environments are confident and auditable.

**Discoverability and adoption are first‑class outcomes.** Every product is registered in the catalog with ownership, purpose, contracts, examples, and maturity. Consumers should quickly find the right product, understand it, and start using it. If a product is not yet fit, the maturity score and contact information make the path to improvement clear and collaborative.

**Economics are visible.** The platform attaches basic unit economics—storage, compute, refresh cost, adoption—to each product. We keep what’s used and valuable, retire what’s redundant, and invest where quality improvements reduce rework, speed cycle times, or lower compliance risk. This keeps the ecosystem healthy as it grows.

In short, we replace ad‑hoc data movement with **owned, observable, and reusable data products** inside clear **bounded contexts**, delivered on a **self‑serve platform**, governed by **code**, and measured with **objective quality signals**. That is how we move Takeda from raw data **volume** to sustained business **value**—and keep it there as we scale.

## Data Governance

### Roles & Responsibilities

Delivering high-quality, trusted data at scale requires close collaboration between core personas—each with distinct responsibilities across the data lifecycle. Together, they form a closed loop of **design**, **build**, and **operational** excellence.

![Domain-oriented structure with sub-domains, standards & principles, and roles](takeda_data_domain_model.png)

*Figure: Domain model showing bounded contexts (e.g., Quality, Manufacturing, Supply Chain), standards & principles (Golden Masters, ontologies, quality rules, mappings), and key roles (Data Domain Lead, Data Trustees, Data Product Owner, Data Stewards, Data System Owner).*

| Role | Scope | Core Responsibilities |
|---|---|---|
| **Data Domain Lead** | Domain‑wide oversight & decision authority | Owns domain strategy, arbitrates sub‑domains, approves investments & SLAs, ensures regulatory/business alignment | 
| **Data Trustee** | Sub‑domain design authority | Defines/approves rules (CDEs, uniqueness, SLAs), owns glossary/ontology, semantic alignment, arbitration | 
| **GMS&Q Data Product Owner** | Build/delivery | Backlog, acceptance criteria, validated pipelines, adoption | 
| **Data Steward** | Operate (site/local) | Execute checks, log incidents, maintain metadata, train users | 
| **System Owner** | Systems where data originates | Uptime, validation, access controls, audit trails, DR | 
| **Data Consumer** | Use & feedback | Governed consumption, report anomalies, support reuse | 

Closed‑loop execution: **Design → Build → Operate → Consume → Improve**.

#### Data Domain Lead
**Scope:** Oversight & Decision Authority – Across Entire Domain  
The Data Domain Lead is the accountable leader for all data quality activities within a domain (e.g., Quality, Manufacturing, Supply Chain). They hold final decision-making authority and ensure alignment with business strategy, regulatory requirements, and enterprise standards. Acting as the “voice of the domain,” they arbitrate between sub-domains, set investment priorities, and report on data quality performance at the domain level.

**Responsibilities:**
- Own and approve the domain-wide data strategy and roadmap.
- Oversee and arbitrate conflicts across sub-domains (e.g., Quality Control vs. Quality Assurance).
- Sign off on budgets, investments, and priorities related to data products.
- Ensure regulatory compliance and business alignment of domain data practices.
- Chair domain-level governance forums and represent the domain in enterprise councils.
- Act as final escalation point for unresolved data issues.

**Skills & Competencies:**
- Senior leader with strong business acumen and regulatory knowledge.
- Proven ability to balance trade-offs across competing priorities.
- Skilled communicator and influencer at executive level.

#### Data Trustee (Sub-domain level)
**Scope:** Design – Global Function, close to GBPO  
The Data Trustee is the strategic authority for a sub-domain (e.g., QC Results, QA Master Data). They define what “good data” looks like, approve rules and standards, and ensure alignment with the broader domain strategy. Trustees act as design authorities, owning glossaries, ontologies, and policies that shape data quality expectations.

**Responsibilities:**
- Define and approve global sub-domain rules (CDEs, uniqueness, SLAs).
- Own business glossaries, taxonomies, and ontologies.
- Establish entity resolution and master data mapping within the sub-domain.
- Arbitrate cross-functional needs at sub-domain level.
- Sign off on sub-domain data definitions and standards.
- Partner with Stewards for issue resolution and continuous improvement.

**Special Note on GBPO/BPO Alignment:**
- A Trustee must be directly linked to the GBPO — in some cases, the Trustee is the GBPO. In this setup, the role can typically be covered with ~25% workload, since responsibilities overlap with process ownership.
- If a Trustee is accountable for a whole sub-domain, they must be connected to all relevant BPOs. In this case, the scope requires a full-time role to ensure effective arbitration, alignment, and governance across the end-to-end process.

**Skills & Competencies:**
- Strategic thinker with enterprise-wide perspective.
- Skilled in semantic alignment and data governance.
- Strong communicator and influencer across global functions.

#### GMSGQ Data Product Owner
**Scope:** Build – DD&T, Data & Digital  
The Data Product Owner acts as the product manager for data products and pipelines, accountable for delivering scalable, high-quality data services that meet business needs. They sit at the build and delivery level, translating domain and trustee requirements into actionable backlogs, managing PODs, and ensuring adoption through continuous improvement.

**Responsibilities:**
- Translate domain needs into roadmaps, stories, and acceptance criteria.
- Manage sprints, capacity, and POD delivery.
- Deliver and maintain data pipelines, APIs, schemas, and reusable data products.
- Ensure technical qualification, validation, and documentation.
- Collect and analyze user feedback, adoption metrics, and product improvements.
- Collaborate closely with Trustees and Architects to align technical solutions with business rules.

**Skills & Competencies:**
- Fluent in business workflows and user requirements.
- Experienced in Agile delivery and backlog management.
- Skilled in stakeholder alignment across business and IT.
- Strong technical documentation and validation capabilities.

#### Data Steward
**Scope:** Operate – Functional / Site / Local Execution  
The Data Steward is the frontline guardian of data quality, embedded in business operations (e.g., QC, manufacturing, supply chain). They ensure accuracy, completeness, and usability of data at the point of capture, acting as the first line of defense in daily execution. Stewards provide feedback upstream and help bridge the gap between requirements and practice.

**Responsibilities:**
- Perform data quality checks (field accuracy, completeness, duplication).
- Log incidents and lead root-cause analysis.
- Maintain metadata: dictionaries, lineage, glossaries.
- Align local/site data to global standards and harmonization rules.
- Execute backup, restore, and uptime monitoring where applicable.
- Train and support end-users in proper data entry and adherence to standards.
- Provide operational feedback to Trustees and Product Owners.

**Skills & Competencies:**
- Deep knowledge of local processes and systems.
- Skilled in troubleshooting and data curation.
- Effective communicator and trainer of frontline users.

#### System Owner (Data Custodians) – Application Manager or Technical System Owner
**Scope:** System Accountability – Platforms & Applications Where Data Originates  
The System Owner is accountable for the lifecycle, compliance, and fitness-for-purpose of the IT systems, applications, or platforms that generate and manage data. While they do not “own” the business meaning of the data (that lies with Trustees), they ensure the system is available, secure, validated, and technically capable of supporting data quality requirements. They operate as an “open loop role” — focusing on system integrity, validation, and controls — and work in close coordination with Trustees, Product Owners, and Stewards to guarantee reliable data capture and management.

**Responsibilities:**
- Ensure system availability, stability, and compliance (e.g., uptime SLAs, disaster recovery).
- Own system validation and qualification (especially in GxP-regulated environments).
- Implement technical controls for access, authentication, audit trails, and backups.
- Maintain system configuration, upgrades, and patching to sustain performance.
- Ensure data integrity controls are embedded (e.g., timestamps, PK/FK enforcement, audit trails).
- Act as primary contact for incidents impacting system performance or data availability.
- Coordinate with Trustees on implementing business rules within the system.
- Provide evidence of compliance for audits and inspections.

**Skills & Competencies:**
- Deep knowledge of the system architecture, interfaces, and configurations.
- Expertise in validation, security, and compliance frameworks (e.g., GxP, FDA 21 CFR Part 11).
- Strong coordination skills with both IT and business data stakeholders.
- Problem-solving and incident management in technical domains.

#### Data Consumer
**Scope:** Use – Data-driven Decision Making  
The Data Consumer is any individual who uses data products and datasets to perform analyses, make operational or strategic decisions, or fulfill regulatory and reporting needs. While primarily a beneficiary of data quality, the Consumer also has defined responsibilities: to respect access rights, follow governance guidance, and provide feedback that helps maintain and improve data quality.

**Responsibilities:**
- Consume data only through approved, governed channels (catalogs, APIs, dashboards).
- Follow data usage guidelines, including compliance with confidentiality, security, and regulatory requirements.
- Provide feedback on data quality, usability, and relevance to Stewards and Trustees.
- Report anomalies, suspected errors, or access issues via defined escalation paths.
- Support reuse by referencing and citing data products consistently.

**Skills & Competencies:**
- Literacy in data interpretation and basic governance principles.
- Awareness of regulatory and business compliance requirements relevant to their role.
- Ability to identify and communicate quality issues or needs.

**Commitment:** Part-time, as required by business function. Integral to the “closed loop” by ensuring data quality is validated in practice and continuously improved.

## Data Quality Framework
### Overview
Our framework extends classical data‑quality ideas (accuracy, completeness, consistency, etc.) into an **end‑to‑end, AI‑ready** model that also measures **availability, interoperability, traceability, connectedness, findability, semantics, and reproducibility**. It aligns with regulatory expectations (e.g., ALCOA/ALCOA+, FDA/EMA) while addressing the realities of **big data in data lakes**. The goal is not only to detect defects but to **design for quality** and make maturity visible.

**Legend:** ● = strong/explicit coverage · ○ = partial/indirect coverage · – = not primary

| Dimension        | Open Data | FAIR | ISO 8000 | ALCOA | ALCOA+ | ALCOA++ | FDA | EMA | China NMPA | Russia MoH |
|------------------|:---------:|:----:|:--------:|:-----:|:------:|:-------:|:---:|:---:|:----------:|:----------:|
| **Connected**    |    ○     |  ○   |    ○     |   ○   |   ○    |    ○    |  ●  |  ●  |     ●      |     ●      |
| **Availability** |    ○     |  ○   |    ○     |   ○   |   ○    |    ○    |  ●  |  ●  |     ●      |     ●      |
| **Findable**     |    ●     |  ●   |    ○     |   –   |   –    |    –    |  ○  |  ○  |     ○      |     ○      |
| **Accessibility**|    ●     |  ●   |    ○     |   ○   |   ○    |    ○    |  ●  |  ●  |     ●      |     ●      |
| **Interoperability** |  ○   |  ●   |    ○     |   –   |   –    |    –    |  ○  |  ○  |     ○      |     ○      |
| **Reusable**     |    ○     |  ●   |    ○     |   –   |   –    |    –    |  ○  |  ○  |     ○      |     ○      |
| **Integrity**    |    ○     |  ○   |    ●     |   ●   |   ●    |    ●    |  ●  |  ●  |     ●      |     ●      |
| **Traceability** |    ○     |  ○   |    ○     |   ●   |   ●    |    ●    |  ●  |  ●  |     ●      |     ●      |
| **Timeliness**   |    ○     |  ○   |    ○     |   ●   |   ●    |    ●    |  ●  |  ●  |     ●      |     ●      |
| **Validity**     |    ○     |  ○   |    ●     |   ○   |   ○    |    ○    |  ●  |  ●  |     ●      |     ●      |
| **Uniqueness**   |    ○     |  ○   |    ●     |   –   |   –    |    –    |  ○  |  ○  |     ○      |     ○      |
| **Accuracy**     |    ○     |  ○   |    ●     |   ●   |   ●    |    ●    |  ●  |  ●  |     ●      |     ●      |
| **Consistency**  |    ○     |  ○   |    ●     |   ○   |   ○    |    ○    |  ●  |  ●  |     ●      |     ●      |
| **Completeness** |    ○     |  ○   |    ●     |   –   |   –    |    –    |  ●  |  ●  |     ●      |     ●      |

### Concept
Data quality matures progressively. Rather than pursuing perfection everywhere, we **raise the floor** with platform guardrails and product contracts, then **raise the ceiling** where business value demands it. Maturity accumulates as products adopt shared semantics, enforce rules automatically, and publish trustworthy telemetry. The destination is a mesh of **ontologically linked domains** with consistently high‑quality data, ready for predictive analytics and GenAI at scale.

![Maturity curve from ad‑hoc data to high‑quality, AI‑ready domains](dq_maturity_arrow2.png)

### Priority & Focus
We sequence improvements to maximize impact. First, the **big rocks**; then a push to converge every product to a reliable **3‑star baseline** before pursuing higher‑order dimensions.

#### Focus on big rocks
- **Availability & Timeliness** — pipelines run and data is fresh within SLOs.
- **Completeness & Validity** — CDEs and rules enforced so consumers don’t shoulder cleaning.
- **Uniqueness & Integrity** — duplicates removed and relationships enforced.
- **Consistency** — schemas, formats, and reference values stabilized.
- **Accessibility** — governed, auditable access via approved channels.
- **Interoperability (baseline)** — shared structures and minimal semantics so products connect.

#### 3‑star as the first objective
A **3‑star** baseline means each product is **available, complete on critical fields, valid by rule, unique where required, and consistent**, with **baseline interoperability** plus documented ownership and contracts.

![FY25 focus on achieving a 3‑star baseline across priority dimensions](dq_fy25_focus.png)


The 5‑Star model defines maturity from basic **availability** to **semantic, reproducible, AI‑ready** data. Star ratings are derived from platform telemetry and shown in catalogs/dashboards.

| ★ Level | Title | Description | Platform Indicators |
|---|---|---|---|
| ★ | **Available** | Basic presence, access and freshness | Uptime ≥90%, pipelines run, access configured |
| ★★ | **Structured & Complete** | Source‑aligned, machine‑readable, complete/unique | Schema enforcement, ≥98% critical completeness, PKs enforced |
| ★★★ | **Validated & Harmonized** | Global masters & rule‑based validation; reusable | GM mappings, rule engines, cross‑table consistency |**
**| ★★★★ | **Traceable & Connected** | End‑to‑end lineage; cross‑system relationships | Real‑time lineage, FK enforcement, integration KPIs |
| ★★★★★ | **Semantic & Reproducible** | Ontology‑driven semantics; versioned, reproducible pipelines | Ontology/URIs, AI‑aided rules, immutable versioned runs |


### Data Quality Dimensions

> For each dimension below: **Description**, **KPI**, and **Controls** with ★ to ★★★★★ maturity levels. These definitions are authoritative and drive telemetry expectations and dashboards.

#### Availability
**Description:** Degree to which data and systems are up and ready for use during expected service windows. Foundational to business continuity.  
**KPI:** **Data Uptime (%)** — target expressed as SLA.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Data Uptime (“Nines”) | Uptime % and SLA targets | No SLA | <90% | 95% | 99% | 99.9% | 99.99%+ |
| Backup & Restore | Data backup and recovery | No backups | Ad hoc | Manual | Auto scheduled | Full DR | Instant recovery/failover |
| Digitization Coverage | % of real‑world domains digitized | 0–20% | 20–40% | 40–70% | 70–90% | 90–98% | 98–100% |

#### Accessibility
**Description:** How easily and reliably **authorized** users can retrieve and use data.  
**KPI:** **Access Rate (%)** — successful access attempts / total.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Access Rights | Security & access management | None | Manual | Basic RBAC | Standardized access | Dynamic policies | Self‑service access |
| Authentication | Standards | None | Workspace‑level | Catalog‑level | Schema/Table‑level | Column‑level | Row‑level ABAC |
| Access Monitoring | Monitoring of access | None | Manual logs | Basic audit trails | Regular audits | Real‑time monitoring | Predictive analysis |

#### Timeliness
**Description:** Data is captured and made available within required timeframes.  
**KPI:** **Average Data Latency (time to availability)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Data Update Frequency | Refresh cadence | Outdated | Manual | 1×/day | Many/day | Near‑real‑time | Real‑time |
| Pipeline Observability | Freshness & delay monitoring | None | Manual | Scheduled reports | Automated alerts | Streaming health tracking | Predictive detection |

#### Accuracy
**Description:** Correctness of data values and metadata; includes pre‑ and post‑transformation accuracy.  
**KPI:** **Error Rate (%)** (before/after cleanup).

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Field Value Correctness | Reflects reality | Not measured | Manual fixes | Basic field validation | Rule‑based detection | Multi‑source reconciliation | AI‑based detection |
| Anomaly Detection | Detect unusual values | None | Manual | Scripted | Scripted (CDEs) | Statistical | ML‑based |
| Automated Correctness Healing | Intelligent value correction | None | Manual | Basic scripts (regex) | Ref data rule‑based | AI suggestions | Self‑learning autonomous correction |

#### Completeness
**Description:** Required fields are populated per Trustee‑approved rules.  
**KPI:** **Completeness Score (%)** (CDE targets often ≥98%).

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Field Completeness Monitoring | Required fields populated | Not measured | Manual spot checks | Scripted profiling | Automated + alerts | Historical null pattern analysis | Predictive null risk |
| Critical Data Element Enforcement | Required element enforcement | Not measured | Technical validation | Partial field validation | Rule‑based CDE detection | Multi‑source reconciliation | AI‑based detection |

#### Uniqueness
**Description:** Each entity is represented once; duplicates removed.  
**KPI:** **Uniqueness Rate (% unique)** (or **Non‑Unique Count**).

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Duplicate Records | Detection/removal | Rampant | Manual | PK checks | Systematic dedup | Fuzzy matching | Predictive dedup |
| Primary Key Enforcement | Unique identifiers | No PKs | Manual PK checks | Some PKs enforced | Full constraints | Domain‑unique IDs | Cross‑domain unique IDs |

#### Integrity
**Description:** Soundness and trustworthiness across the lifecycle; relationships and auditability.  
**KPI:** **Integrity Score (0–100)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Foreign Key Relationships | Referential integrity | None | Manual linking | Some FK constraints | Enforced FK/PK | Cross‑system integrity | Dynamic integrity |
| Change Tracking | Tracking data changes | None | Manual logs | Timestamps only | Full audit trails | Immutable audit history | GxP‑compliant immutable |
| Reference Data Integrity | Golden source consistency | None | Manual curation | Periodic validation | Scheduled checks | Automated validation | Dynamic reference updates |

#### Validity (Conformity)
**Description:** Data adheres to schema rules, formats, ranges, and business logic.  
**KPI:** **Validity Rate (% records conforming)**; minimum **≥80%** for critical elements.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Business Rule Validation | Business logic checks | None | Basic rule | CDE rule coverage | Context‑specific rules | AI‑derived rules | Endorsed AI‑derived rules |

#### Reusability
**Description:** Standardized, documented, machine‑readable data ready for reuse across use cases.  
**KPI:** **Reusability Index (% datasets reused)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Data Documentation | Docs for reuse | None | Ad hoc | Critical datasets documented | Full dataset docs | Living documentation | Automated product documentation |
| Data Productization | Designed for reuse | None | Raw tables | Proprietary format (e.g., LIMS) | Real‑world entity data product | Full marketplaces | Federated productized assets |

#### Consistency
**Description:** Uniform structures & formats across systems; shared reference structures.  
**KPI:** **Consistency Rate (% aligned)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Schema Consistency | Uniformity across systems | None | Manual checks | Basic controls | Schema registry | Schema evolution monitoring | Real‑time drift correction |
| Format Consistency | Standard formats | None | Manual standardization | Critical fields standardized | Full formatting enforcement | Business rule standardization | Dynamic format validation |

#### Interoperability
**Description:** Effective exchange & interpretation across systems; both syntactic and semantic.  
**KPI:** **System Compatibility Rate (% successful integrations)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| API Integration | Connecting systems | No APIs | Manual file transfer | SQL access | Real‑time APIs | AI‑ready + semantic enrichment | Event‑driven access |
| Exchange Standards | Shared formats | No standards | Custom | Tagged markup | Binary JSON | Domain‑specific semantics | Ontology & embeddings |

#### Traceability
**Description:** Track full journey from source to use; audit‑ready and reproducible.  
**KPI:** **Lineage Coverage (% flows with lineage)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Data Lineage | Source→transform→destination | None | Manual notes | Static mapping | Full lineage tools | Real‑time lineage | Immutable dynamic lineage |
| Audit Trails | Transformation tracking | None | Manual logs | Critical system logs | Systematic audit trails | Immutable trails | “Blockchain‑grade” logs |

#### Findability
**Description:** Ease of discovering and **re‑discovering** trusted data via rich metadata and catalogs.  
**KPI:** **Findability Rate (% successful searches)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Metadata Availability | Metadata for datasets | No metadata | Manual notes | Basic static catalogs | Dynamic searchable catalogs | Semantic metadata search | AI‑powered discovery |
| Data Catalog Presence | Central catalog | No catalog | Spreadsheet lists | Static catalog | Managed catalog | Semantic search integrated | Federated catalogs |

#### Connectivity
**Description:** Degree of meaningful links across datasets, systems, and domains (URIs/FKs).  
**KPI:** **Connectivity Score (% with valid links)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Entity Relationships | Relationship modeling | No relationships | Manual linking | Static mapping | Dynamic entity models | Knowledge graph construction | Real‑time knowledge graphs |

#### Semantic
**Description:** Standardization of meaning across datasets using controlled vocabularies and automated harmonization.  
**KPI:** **Semantic Alignment Rate (% tokens harmonized)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Semantic Harmonization | Codes/labels alignment | None | Manual per dataset | Controlled vocabularies applied | Automated semantic matching | Ontology‑driven harmonization | Dynamic AI‑driven harmonization |

#### Reproducibility
**Description:** Identical inputs yield identical outputs across teams, tools, and time.  
**KPI:** **Reproducibility Index (% consistent results)**.

| Control | Aspect | No ★ | ★ | ★★ | ★★★ | ★★★★ | ★★★★★ |
|---|---|---|---|---|---|---|---|
| Process Reproducibility | Ability to reproduce | None | Manual rework | Documented repeatability | Standardized workflows | Automated reproducible pipelines | Immutable, versioned pipelines |

---

## Core Semantics & Quality Telemetry

### Central Semantics (CORE)
```sql
CREATE SCHEMA IF NOT EXISTS CORE;

CREATE TABLE IF NOT EXISTS CORE.golden_master_catalog (
  gm_domain STRING,        -- e.g., 'QUALITY_EVENT_SEVERITY'
  code STRING,             -- canonical code
  label STRING,
  description STRING
) USING DELTA;

CREATE TABLE IF NOT EXISTS CORE.token_mapping (
  domain STRING,           -- 'BOOLEAN' or GM domain
  scope_level STRING,      -- 'RECORD'|'TABLE'|'GLOBAL'
  schema_name STRING,
  table_name STRING,
  column_name STRING,
  record_pk STRING,
  token_normalized STRING, -- normalized source token
  mapped_value STRING,     -- boolean or GM code
  mapping_version INT,
  effective_from TIMESTAMP,
  effective_to TIMESTAMP,
  priority INT,
  notes STRING
) USING DELTA;
```

### Quality Telemetry (CORE)
```sql
CREATE TABLE IF NOT EXISTS CORE.dq_run (
  dq_date DATE,
  domain STRING,                 -- e.g., 'QUALITY'
  sub_domain STRING,             -- e.g., 'Quality Management'
  data_product_name STRING,      -- e.g., 'Quality Events'
  version STRING,                -- contract version
  -- Dimension metrics (normalized 0..1)
  availability_rate DOUBLE,
  accessibility_rate DOUBLE,
  timeliness_rate DOUBLE,
  accuracy_rate DOUBLE,
  completeness_rate DOUBLE,
  uniqueness_rate DOUBLE,
  integrity_rate DOUBLE,
  validity_rate DOUBLE,
  reusability_rate DOUBLE,
  consistency_rate DOUBLE,
  interoperability_rate DOUBLE,
  traceability_rate DOUBLE,
  findability_rate DOUBLE,
  connectivity_rate DOUBLE,
  semantic_rate DOUBLE,
  reproducibility_rate DOUBLE,
  -- Derived maturity
  dq_star_rating INT,            -- 1..5
  dq_notes STRING,
  created_ts TIMESTAMP
) USING DELTA;
```

### Star Derivation (reference implementation)
```sql
-- Example scoring (weights may be tuned by Trustees per sub-domain)
WITH s AS (
  SELECT *,
    /* minimum gates for stars */
    CASE
      WHEN availability_rate < 0.90 OR timeliness_rate < 0.60 THEN 1
      WHEN completeness_rate < 0.98 OR uniqueness_rate < 0.98 THEN 2
      WHEN semantic_rate < 0.70 OR validity_rate < 0.80 THEN 3
      WHEN traceability_rate < 0.80 OR integrity_rate < 0.85 THEN 4
      ELSE 5
    END AS gate_star
  FROM CORE.dq_run
)
SELECT domain, data_product_name,
       GREATEST(gate_star, 1) AS dq_star_rating
FROM s;
```

---

## Data Contracts (Business & Technical)

### Business Contract (example)
```json
{
  "domain": "Quality",
  "sub_domain": "Quality Management",
  "data_product_name": "Quality Events",
  "governance": {
    "data_trustee": "TBD",
    "owner_team": "Quality POD",
    "sla": { "availability": "99.9%", "update_frequency": "hourly" }
  },
  "business_description": "Quality events with severity, regulatory and customer impact."
}
```

### Technical Contract (example)
```json
{
  "schema": "QUALITY",
  "product_name": "dp_quality_management_events_v1",
  "contract_version": "1.0.0",
  "raw_sources": [
    {"schema": "LAKE", "table": "raw_quality_events_lf", "format": "long"},
    {"schema": "HUB",  "table": "raw_quality_events_wf", "format": "wide"}
  ],
  "primary_key": "event_id",
  "soft_gate_threshold": 0.005,
  "published_tables": [
    {
      "name": "events",
      "published_table": "QUALITY.dp_quality_management_events_v1",
      "columns": {
        "gm": [
          {"raw": "severity_raw", "out_code": "severity_code", "gm_domain": "QUALITY_EVENT_SEVERITY"}
        ],
        "booleans": [
          {"raw": "is_regulatory_raw", "out": "is_regulatory"},
          {"raw": "is_customer_impact_raw", "out": "is_customer_impact"}
        ],
        "passthrough": [
          {"raw": "description", "out": "description"}
        ]
      }
    }
  ]
}
```

## GMS & GQ Data Domains

### Supply Chain  Domain
### Manufacturing Domain
### Engineering Domain
### Environment, Health & Safety Domain
### Strategy & Business Excellence Domain
### GMS Finance Domain
### Quality Domain
#### Quality Management (Sub-Domain)

##### Governance
##### Overview

The **Quality Management Sub-Domain** harmonizes all quality events—**Deviation, CAPA, Lab Investigation, Change Control, Complaint**—and their **Task** activities into a system-neutral, comsumption-ready model. It:

- standardizes **shared event headers** in a single master table
- keeps **type-specific attributes** in per-type event detail tables
- models **Tasks as a Detail level (child)** of events (1:N) with a consolidated task-detail table
- centralizes all **enums/reference values** in a single **Golden Master** reference table (with crosswalks) to ensure consistent, enterprise labels
- publishes curated **views** for self-service analytics and APIs

```
Quality (Domain)
└─ Management (Subdomain)
   ├─ Event (Master)
   │  ├─ Event Detail: Deviation (1:1)
   │  ├─ Event Detail: CAPA (1:1)
   │  ├─ Event Detail: Lab Investigation (1:1)
   │  ├─ Event Detail: Change Control (1:1)
   │  ├─ Event Detail: Complaint (1:1)
   │  ├─ Item: Root Cause (1:N)
   │  ├─ Item: Impacted Location (1:N)
   │  └─ Detail (Child): Task (1:N)
   │        └─ Task Detail (1:1)
   └─ Core: Golden Master Reference + Crosswalks
```


| **Category** | **Data Product** | **Purpose / Description** | **Table Name** | **Version** | **Latest** |
|---|---|---|---|---|---|
| **Master** | Quality Events | Canonical header for all events (all types). | `dp_quality_management_event` | v1.0 | ✅ |
| **Event Detail (1:1)** | Deviation Detail | Deviation-specific attributes. | `dp_quality_management_event_detail_deviation` | v1.0 | ✅ |
| **Event Detail (1:1)** | CAPA Detail | CAPA-specific attributes. | `dp_quality_management_event_detail_capa` | v1.0 | ✅ |
| **Event Detail (1:1)** | Lab Investigation Detail | Lab Investigation-specific attributes. | `dp_quality_management_event_detail_lab_investigation` | v1.0 | ✅ |
| **Event Detail (1:1)** | Change Control Detail | Change Control-specific attributes. | `dp_quality_management_event_detail_change_control` | v1.0 | ✅ |
| **Event Detail (1:1)** | Complaint Detail | Complaint-specific attributes. | `dp_quality_management_event_detail_complaint` | v1.0 | ✅ |
| **Item (1:N)** | Root Cause Items | Root cause list per event (Deviation/LI). | `dp_quality_management_item_root_cause` | v1.0 | ✅ |
| **Item (1:N)** | Impacted Location Items | Impacted locations list per event. | `dp_quality_management_item_impacted_location` | v1.0 | ✅ |
| **Detail (child, 1:N)** | Task (Detail level) | Task records under an event (Investigation, CAPA Task, LI Task, CC Tasks, SME/RA, Extension). | `dp_quality_management_event_detail_task` | v1.0 | ✅ |
| **Detail (1:1)** | Task Detail | Consolidated attributes by task type. | `dp_quality_management_event_detail_task_detail` | v1.0 | ✅ |
| **Core Reference** | Golden Master | All enums/ref values with speaking codes & golden labels. | `core.dp_quality_management_ref` | v1.0 | ✅ |
| **Core Crosswalk** | Golden Crosswalk | Namespaced source values → golden labels. | `core.dp_quality_management_ref_crosswalk` | v1.0 | ✅ |



##### Business Glossary and Data Element Definitions
###### Quality Event
| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| Quality Record ID | Unique identifier for the quality event. | `record_id` | BIGINT (PK) |
| Event Type | Type of quality event (Deviation, CAPA, etc.). | `event_type_id` | BIGINT (FK → ref_type='EVENT_TYPE') |
| Workflow Status | Current workflow status of the record. | `status_id` | BIGINT (FK → ref_type='STATUS') |
| Record Title | Title summarizing the event or activity. | `title` | STRING |
| Date Opened | Date when the record was initiated. | `opened_date` | DATE |
| Target Completion Date | Planned date for completion. | `target_date` | DATE |
| Original Closure Date | First recorded closure date. | `original_closed_date` | DATE |
| Date Closed | Actual closure date. | `closed_date` | DATE |
| Workflow Name | Workflow or process name. | `project_name` | STRING |
| Originator | Person who created the record. | `originator_name` | STRING |
| Responsible Person | Current owner responsible. | `assigned_to_name` | STRING |
| Responsible Email | Email address of owner. | `assigned_to_email` | STRING |
| Responsible UID | Directory/HR system identifier. | `assigned_to_uid` | STRING |
| Operational Unit | Business area or site. | `operational_unit_id` | BIGINT (FK → ref_type='OPERATIONAL_UNIT') |
| Owning Department | Department accountable for record. | `owning_dept_id` | BIGINT (FK → ref_type='DEPARTMENT') |
| Owning Group | Group/team accountable. | `owning_group_id` | BIGINT (FK → ref_type='GROUP') |
| Attachments | List of attached documents. | `attachments_list` | STRING |
| Pending Approvers | Users pending approval. | `pending_approver_names` | STRING |
| Last Status Change | Timestamp of the last state transition. | `current_state_ts` | TIMESTAMP |
| Last Updated | Timestamp of the last field update. | `record_updated_ts` | TIMESTAMP |

###### Deviation

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| CAPA Required | Indicates if CAPA is required. | `capa_required_flag` | BOOLEAN |
| Clinical Study Affected | Indicates if clinical study is impacted. | `clinical_study_affected_flag` | BOOLEAN |
| Clinical Study Number | Identifier of the impacted study. | `clinical_study_number` | STRING |
| Customer Product Impact | Potential impact to customer product(s). | `customer_product_potential_impact_flag` | BOOLEAN |
| Event Party | Responsible function/party. | `event_party_id` | BIGINT (FK → ref_type='EVENT_PARTY') |
| Event Scope | Scope of the deviation (site, process, product). | `event_scope_id` | BIGINT (FK → ref_type='EVENT_SCOPE') |
| Deviation Type | Deviation classification. | `deviation_event_type_id` | BIGINT (FK → ref_type='DEV_EVENT_TYPE') |
| Initial Risk Classification | Initial assessed risk. | `risk_classification_initial_id` | BIGINT (FK → ref_type='RISK_CLASS') |
| Final Risk Classification | Final confirmed risk. | `risk_classification_final_id` | BIGINT (FK → ref_type='RISK_CLASS') |
| GxP Area | Regulatory domain impacted (GMP, GDP, etc.). | `gxp_area_id` | BIGINT (FK → ref_type='GXP_AREA') |
| Impact on Other Lots | Whether other lots are impacted. | `impact_on_other_lots_flag` | BOOLEAN |
| Report to Authority | Whether reporting to a health authority is required. | `report_to_health_authority_flag` | BOOLEAN |
| Pharmacovigilance Impact | Whether PV impact exists. | `pharmacovigilance_impact_flag` | BOOLEAN |
| Scientific Misconduct Suspected | Flags potential scientific misconduct. | `scientific_misconduct_suspected_flag` | BOOLEAN |
| Serious Breach | Indicates a serious breach. | `serious_breach_flag` | BOOLEAN |
| Shared or Local | Whether deviation is shared or local. | `shared_or_local_id` | BIGINT (FK → ref_type='SHARED_LOCAL') |
| QA Closure Approved On | Date QA approved closure. | `qa_closure_approval_on` | DATE |
| Deviation Owner | Responsible deviation owner. | `deviation_owner_name` | STRING |
| Investigation Lead | Lead investigator name. | `investigation_lead_name` | STRING |
| Therapeutic Area | Business therapeutic area. | `therapeutic_area_id` | BIGINT (FK → ref_type='THERAPEUTIC_AREA') |

###### Corrective and Preventive Action

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| CAPA Type | Type of CAPA. | `capa_type_id` | BIGINT (FK → ref_type='CAPA_TYPE') |
| CAPA Effective | Indicates whether CAPA verified as effective. | `capa_effective_flag` | BOOLEAN |
| Effectiveness Check Required | Whether an effectiveness check is required. | `ec_required_flag` | BOOLEAN |
| CAPA Category | Category of CAPA. | `capa_category_id` | BIGINT (FK → ref_type='CAPA_CATEGORY') |
| Implementation Date | Date CAPA actions implemented. | `implementation_date` | DATE |
| Plan Approval Date | Date CAPA plan was approved. | `plan_approval_date` | DATE |
| CAPA Owner | Responsible CAPA owner. | `owner_name` | STRING |
| Effectiveness Validated | Whether effectiveness validation was performed. | `validation_of_effectiveness_flag` | BOOLEAN |

###### Lab Investigation

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| Investigation Type | Type of laboratory investigation. | `li_type_id` | BIGINT (FK → ref_type='LI_TYPE') |
| Test Article | Material or sample under test. | `assay_test_article` | STRING |
| Result Classification | Result outcome classification (Pass/Fail/Invalid). | `result_classification_id` | BIGINT (FK → ref_type='RESULT_CLASS') |
| Lab Error Identified | Whether a lab error confirmed. | `laboratory_error_identified_flag` | BOOLEAN |
| Phase 2 Required | Indicates if extended investigation required. | `phase2_required_flag` | BOOLEAN |
| Stability Storage Period | Duration of sample storage. | `stability_storage_period` | STRING |
| Storage Condition | Environmental storage condition. | `storage_condition` | STRING |
| Test Date | Date of the laboratory test. | `test_date` | DATE |
| Test Performed By | Person performing the test. | `test_performed_by` | STRING |
| Root Cause Identified | Whether root cause was identified. | `root_cause_identified_flag` | BOOLEAN |
| Justification for No CAPA | Rationale when CAPA not initiated. | `justification_for_no_capa` | STRING |

###### Change Control

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| Change Classification | Classification of change (Minor, Major, Critical). | `change_classification_id` | BIGINT (FK → ref_type='CHANGE_CLASS') |
| Change Scope | Functional or system scope of the change. | `change_scope_id` | BIGINT (FK → ref_type='CHANGE_SCOPE') |
| Change Party | Function or group initiating the change. | `change_party_id` | BIGINT (FK → ref_type='CHANGE_PARTY') |
| Emergency Change | Whether the change was processed as an emergency. | `emergency_change_flag` | BOOLEAN |
| Implementation Date | Date the change was implemented. | `implementation_date` | DATE |
| Quality Approval Date | Date Quality approved closure. | `approval_date_quality` | DATE |
| GxP Area | Impacted GxP domain. | `gxp_area_id` | BIGINT (FK → ref_type='GXP_AREA') |
| Regulatory Reference | Related regulatory reference or submission. | `regulatory_event_reference` | STRING |
| CMB Impacted | Whether the Change Management Board involved. | `cmb_impacted_flag` | BOOLEAN |

###### Complaint

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| Complaint Type | Type of complaint. | `complaint_type_id` | BIGINT (FK → ref_type='COMPLAINT_TYPE') |
| Product Code | Internal product identifier. | `product_code` | STRING |
| Lot Number | Manufacturing batch or lot number. | `lot_number` | STRING |
| Market Country | Country where complaint originated. | `market_country_id` | BIGINT (FK → ref_type='COUNTRY') |
| Reportable to Authority | Whether complaint reportable to authority. | `reportability_flag` | BOOLEAN |
| Complaint Confirmed | Whether complaint was validated. | `complaint_confirmed_flag` | BOOLEAN |
| Patient/User Injury | Whether patient or user was injured. | `patient_injury_flag` | BOOLEAN |
| Due Diligence Completed | Whether all required assessments were performed. | `due_diligence_complete_flag` | BOOLEAN |
| Root Cause Code | Code for identified root cause. | `root_cause_code` | STRING |
| Closure Date | Date complaint closed. | `closure_date` | DATE |

###### Item Root Cause

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| Quality Record ID | Parent event record identifier. | `record_id` | BIGINT (FK → event) |
| Row Number | Sequential number of record. | `rowno` | INT |
| Root Cause Type | Type of root cause. | `root_cause_type_id` | BIGINT (FK → ref_type='RC_TYPE') |
| Root Cause Category | Category of root cause. | `root_cause_category_id` | BIGINT (FK → ref_type='RC_CATEGORY') |
| Root Cause Subcategory | Detailed subcategory. | `root_cause_subcategory_id` | BIGINT (FK → ref_type='RC_SUBCATEGORY') |
| Operational Unit | Area responsible for record. | `operational_unit_id` | BIGINT (FK → ref_type='OPERATIONAL_UNIT') |
| Owning Group | Team responsible. | `owning_group_id` | BIGINT (FK → ref_type='GROUP') |
| Owning Department | Department accountable. | `owning_dept_id` | BIGINT (FK → ref_type='DEPARTMENT') |

###### Item Impacted Location

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| Quality Record ID | Parent event record identifier. | `record_id` | BIGINT (FK → event) |
| Row Number | Sequential number within event. | `seq_no` | INT |
| Location Type | Type of location. | `location_type_id` | BIGINT (FK → ref_type='LOCATION_TYPE') |
| Impacted Location Name | Name of the impacted site or facility. | `impacted_location_name` | STRING |
| Data Source | Origin of information. | `data_source` | STRING |
| Source Number | Reference identifier. | `source_number` | STRING |
| Address Details | Address or site location details. | `address_details` | STRING |
| External Reference Number | External reference code. | `external_reference_number` | STRING |
| Change Implementation Date | Date change implemented at site. | `impacted_loc_change_imp_date` | DATE |
| Information Required | Whether more information required. | `information_required_flag` | BOOLEAN |
| Informed On | Date stakeholders informed. | `informed_on` | DATE |
| Agreement to Proceed | Whether agreement obtained. | `agreement_to_proceed_flag` | BOOLEAN |
| Agreed On | Date of agreement. | `agreed_on` | DATE |
| Comment | Additional remarks. | `comment` | STRING |

###### Detail Task

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| Task ID | Unique task identifier. | `task_id` | BIGINT (PK) |
| Parent Event ID | Identifier of parent quality event. | `parent_id` | BIGINT (FK → event) |
| Task Type | Type of task. | `task_type_id` | BIGINT (FK → ref_type='TASK_TYPE') |
| Task Status | Workflow status. | `status_id` | BIGINT (FK → ref_type='STATUS') |
| Title | Task title or summary. | `title` | STRING |
| Date Opened | Task creation date. | `opened_date` | DATE |
| Target Completion Date | Planned completion date. | `target_date` | DATE |
| Original Closure Date | Original closure date. | `original_closed_date` | DATE |
| Date Closed | Actual closure date. | `closed_date` | DATE |
| Workflow Name | Workflow definition name. | `project_name` | STRING |
| Assigned To | Responsible person. | `assigned_to_name` | STRING |
| Operational Unit | Executing unit or site. | `operational_unit_id` | BIGINT (FK → ref_type='OPERATIONAL_UNIT') |
| Owning Department | Accountable department. | `owning_dept_id` | BIGINT (FK → ref_type='DEPARTMENT') |
| Owning Group | Accountable team. | `owning_group_id` | BIGINT (FK → ref_type='GROUP') |
| Execution Date | Date task executed. | `execution_date` | DATE |
| Canceled By | Person who canceled task. | `canceled_by` | STRING |
| Closed By | Person who closed task. | `closed_by` | STRING |
| Work Summary | Summary of task performed. | `work_summary` | STRING |
| Last Status Change | Timestamp of last change. | `current_state_ts` | TIMESTAMP |
| Last Updated | Last modification timestamp. | `record_updated_ts` | TIMESTAMP |

###### Detail Task Details

| **Business Name** | **Description** | **Technical Column** | **Data Type** |
|---|---|---|---|
| Task Description | Description or instruction for the task. | `task_description` | STRING |
| Assessment Text | Narrative for SME/RA assessment. | `assessment_text` | STRING |
| Task Owner | Responsible task owner. | `task_owner_name` | STRING |
| Quality Approver | QA approver name. | `quality_approver_name` | STRING |
| Change Owner | Owner of related change. | `change_owner_name` | STRING |
| Task Classification | Classification of the task. | `task_classification_id` | BIGINT (FK → ref_type='TASK_CLASS') |
| Task Number | Task identifier. | `task_number` | STRING |
| Applicable Country | Country associated with task. | `applicable_country_id` | BIGINT (FK → ref_type='COUNTRY') |
| Device RA Impact | Whether device RA impact exists. | `device_ra_impact_flag` | BOOLEAN |
| RA Impact | Whether RA impact exists. | `impact_flag` | BOOLEAN |
| Assessment Target Date | Target date for assessment completion. | `assessment_target_date` | DATE |
| Sent to RA Tracking On | Date sent to RA tracking. | `sent_to_ra_tracking_on` | DATE |
| RA Coordinator | RA coordinator responsible. | `ra_coordinator` | STRING |
| Sent to RA Tracking By | Person who sent record. | `sent_to_ra_tracking_by` | STRING |
| Additional Notification | List of additional notification recipients. | `additional_notification` | STRING |
| Extension Request Number | Reference to extension request. | `extension_request_no` | STRING |
| Current Due Date | Current due date. | `current_due_date` | DATE |
| Requested Due Date | Requested extended due date. | `requested_due_date` | DATE |
| Extension Approved By | Approver of extension. | `extension_approved_by` | STRING |
| Optional Approver 1 | First optional approver. | `optional_approver_1` | STRING |
| Optional Approver 2 | Second optional approver. | `optional_approver_2` | STRING |
| Optional Approver 3 | Third optional approver. | `optional_approver_3` | STRING |
| Optional Approver 4 | Fourth optional approver. | `optional_approver_4` | STRING |
| Quality Approval | Indicates whether quality approval granted. | `quality_approval_flag` | BOOLEAN |

#### Access Options

##### API Endpoints
| **Alias** | **Endpoint** | **Description** |
|---|---|---|
| Quality Events | `GET /api/v1/quality-events?event_type=DEVIATION` | Canonical endpoint for all events. |
| Deviation | `GET /api/v1/deviations` | Alias for event_type=DEVIATION. |
| CAPA | `GET /api/v1/capas` | Alias for event_type=CAPA. |
| Lab Investigation | `GET /api/v1/lab-investigations` | Alias for event_type=LAB_INVESTIGATION. |
| Change Control | `GET /api/v1/change-controls` | Alias for event_type=CHANGE_CONTROL. |
| Complaint | `GET /api/v1/complaints` | Alias for event_type=COMPLAINT. |
| Tasks | `GET /api/v1/quality-events/{record_id}/tasks` | All tasks for a given event. |
| Root Causes | `GET /api/v1/quality-events/{record_id}/root-causes` | Root cause list. |

##### Data Views
| **View Name** | **Description** |
|---|---|
| `dv_quality_event_summary` | Aggregated event summary with golden labels. |
| `dv_quality_event_detail` | Flattened event + detail join. |
| `dv_quality_item_root_cause` | Analytical view for root causes. |
| `dv_quality_item_impacted_location` | Analytical view for impacted sites. |
| `dv_quality_event_detail_task` | Summary of tasks with event linkage. |
| `dv_quality_event_detail_task_detail` | Detailed task-level analytics view. |

#### Quality Rules
| **Rule Type** | **Definition** | **Example** |
|---|---|---|
| Completeness | Required fields are populated. | `record_id`, `event_type_id`, `status_id` must not be NULL. |
| Validity | Values exist in ref master. | `status_id` must map to ref_type='STATUS'. |
| Correctness | Dates in logical order. | `opened_date <= closed_date`. |
| Accuracy | Boolean flags must be true/false only. | `capa_required_flag in (TRUE,FALSE)`. |
| Consistency | FK relationships are valid. | `parent_id in tasks` must exist in `events`. |
| Timeliness | Updates recorded within SLA. | `record_updated_ts within 24h of source change`. |


#### Data Cleansing
- Standardize enumerations via Golden Master lookup.
- Deduplicate records on `(record_id, project_name)`.
- Normalize text casing and trim whitespace.
- Validate date order (`opened_date ≤ closed_date`).
- Default booleans to FALSE if null.
- Validate references and lineage stamps.

## Data Platform


### Data Cleansing

This defines a **contract‑driven** cleansing engine for the GMS & GQ data mesh. It integrates a **semantic, versioned URI scheme** for data types, formats, conversions, units of measure, and golden master entities, and provides **dual‑quality** outputs (Mapped vs. Verified) with strict **scope precedence**.

---

#### Overview

##### Purpose
Normalize heterogeneous raw strings into **typed, standardized, and traceable** data elements suitable for enterprise analytics and data products. The engine:
- Applies **formatting** (e.g., `XXXXXX → XX-XXX-X`) and **unit conversions** (e.g., `1000 g → 1.0 kg`).
- Resolves tokens to canonical **vocabulary/GM codes** using **namespace mappings**.
- Publishes **dual quality** outputs for each element:
  - **Mapped**: any eligible rule (quality = `MAPPED` or `VERIFIED`).
  - **Verified**: only trustee‑verified mapping **and** verified GM/URI target (quality = `VERIFIED` and `is_verified=TRUE`).
- Enforces **scope precedence** for mappings: `RECORD → PRODUCT → DOMAIN → GLOBAL`.
- Emits audit columns and writes per‑cell failures to a central **DLQ**.

##### URI Scheme
URIs are semantic, versioned, and machine‑resolvable. The engine recognizes and uses the following namespaces:

```
https://uri.takeda.io/
 ├── datatype/
 ├── format/
 ├── conversion/
 ├── uom/
 └── goldenmaster/
```

Examples:
- Data types: `https://uri.takeda.io/datatype/boolean/v1`
- Formats: `https://uri.takeda.io/format/material/xx-xxx-x/v1`
- Conversions: `https://uri.takeda.io/conversion/gram-to-kilogram/v1`
- UOM: `https://uri.takeda.io/uom/kilogram/v1`
- Golden Master: `https://uri.takeda.io/goldenmaster/manufacturing/site/site_code/v1`

> The engine stores these as **URIs** to ensure **lineage**, **governance**, and **machine interoperability** across domains.

---

#### Concepts

##### Normalization
`normalized_token = lower(trim(raw_value))` prior to any mapping/regex match.

##### Namespace Mappings
Rules that map normalized tokens to **target codes or values**, with **scope precedence** and **quality level**:
- Scopes (highest→lowest): **RECORD → PRODUCT → DOMAIN → GLOBAL**.
- Quality: `MAPPED` or `VERIFIED`.
- Tie‑breakers: `priority DESC`, then `effective_from DESC`.

##### Golden Masters & Typed Vocabularies
- **BOOLEAN** is treated like a vocabulary with codes `TRUE`/`FALSE`.
- Enumerations/reference lists (e.g., `SITE`, `QUALITY_EVENT_SEVERITY`) are **Golden Masters** (GM).
- **Verified outputs** require: (a) chosen mapping is `VERIFIED`, and (b) the target **GM/URI** has `is_verified=TRUE`.

##### Formatting
Source patterns are standardized to enterprise formats (e.g., material number `XX-XXX-X`). A format is identified by a **format URI** (e.g., `https://uri.takeda.io/format/material/xx-xxx-x/v1`). The contract may embed the regex transformation used by the engine for that standard.

##### Conversions
Numeric values with units (e.g., `"2500 g"`) are converted to a **target UOM** (e.g., kg) using a **conversion URI** (e.g., `https://uri.takeda.io/conversion/gram-to-kilogram/v1`). The engine can use a **conversion catalog** with factors/offsets and validates targets via **UOM URIs**.

##### Outputs
For each element **X**, the published table includes the columns **in this strict order**:

1. `X_raw`  
2. `X` (mapped value)  
3. `X_parse_status` ∈ {`PARSED_OK`, `EMPTY`, `UNPARSABLE`, `BAD_FORMAT`, `BAD_CONVERSION`}  
4. `X_verified` (verified value)  
5. `X_verified_parse_status`  

#### Data Contract

##### Structure
- `data_products[]`: multiple products in one contract.
- Each product has its own `primary_key`.
- Each `data_element` defines: `technical_name`, `business_name`, `description`, `data_type`, source, cleansing vocabulary, optional formatting, optional conversion.

**Example (excerpt)**
```json
{
  "schema": "DEMO_QM",
  "contract_version": "1.5.0",
  "soft_gate_threshold": 0.01,

  "raw_sources": [
    { "schema": "DEMO_LAKE", "table": "qm_events_long", "format": "long" },
    { "schema": "DEMO_HUB",  "table": "qm_events_wide", "format": "wide" }
  ],

  "long_format_rules": [
    {
      "source_table": "DEMO_LAKE.qm_events_long",
      "pivot": { "index": ["event_uid", "description_text"], "name_col": "attribute_name", "value_col": "attribute_value" }
    }
  ],

  "data_products": [
    {
      "technical_name": "dp_qm_events_v1",
      "name": "Quality Events",
      "description": "Quality events with severity, regulatory indicator, site, serial and mass.",
      "primary_key": "event_uid",
      "data_product": {
        "published_table": "DEMO_QM.dp_qm_events_v1",
        "input_shape": "wide",
        "data_elements": [
          {
            "technical_name": "reg_indicator",
            "business_name": "Regulatory Indicator",
            "description": "Whether event is regulatory relevant.",
            "data_type": "BOOLEAN",
            "source": { "from_raw": "reg_indicator_raw" },
            "cleansing": { "vocabulary": "BOOLEAN" },
            "datatype_uri": "https://uri.takeda.io/datatype/boolean/v1"
          },
          {
            "technical_name": "severity_code",
            "business_name": "Severity",
            "description": "Event severity.",
            "data_type": "STRING",
            "source": { "from_raw": "severity_token_raw" },
            "cleansing": { "vocabulary": "QUALITY_EVENT_SEVERITY" },
            "goldenmaster_uri": "https://uri.takeda.io/goldenmaster/quality/severity/code/v1"
          },
          {
            "technical_name": "site_code",
            "business_name": "Manufacturing Site",
            "description": "Canonical site code.",
            "data_type": "STRING",
            "source": { "from_raw": "site_text_raw" },
            "cleansing": { "vocabulary": "SITE" },
            "goldenmaster_uri": "https://uri.takeda.io/goldenmaster/manufacturing/site/site_code/v1"
          },
          {
            "technical_name": "serial_number",
            "business_name": "Serial Number",
            "description": "Normalized serial number format.",
            "data_type": "STRING",
            "source": { "from_raw": "serial_plain_raw" },
            "formatting": {
              "source_format_uri": "https://uri.takeda.io/format/material/xx-xxx-x/v1",
              "target_format_uri": "https://uri.takeda.io/format/material/xx-xxx-x/v1",
              "regex_pattern": "(..)(...)(.)",
              "regex_replacement": "\\\\1-\\\\2-\\\\3"
            }
          },
          {
            "technical_name": "mass_kg",
            "business_name": "Mass (kg)",
            "description": "Mass normalized to kilograms.",
            "data_type": "DOUBLE",
            "source": { "from_raw": "mass_raw" },
            "conversion": {
              "conversion_uri": "https://uri.takeda.io/conversion/gram-to-kilogram/v1",
              "target_uom_uri": "https://uri.takeda.io/uom/kilogram/v1",
              "default_unit_token": "g"
            }
          },
          {
            "technical_name": "description_text",
            "business_name": "Description",
            "description": "Event narrative.",
            "data_type": "STRING",
            "source": { "from_raw": "description_text" },
            "cleansing": { "passthrough": true },
            "datatype_uri": "https://uri.takeda.io/datatype/string/v1"
          }
        ]
      }
    }
  ]
}
```

##### CORE Schema

###### Golden Masters
```sql
CREATE SCHEMA IF NOT EXISTS DEMO_CORE;

CREATE TABLE IF NOT EXISTS DEMO_CORE.golden_master_catalog (
  uri         STRING,
  gm_domain   STRING,
  code        STRING,
  label       STRING,
  is_verified BOOLEAN
);
```

###### Namespace Mapping
```sql
CREATE TABLE IF NOT EXISTS DEMO_CORE.namespace_mapping (
  vocabulary             STRING,
  scope_level            STRING,    -- 'GLOBAL' | 'DOMAIN' | 'PRODUCT' | 'RECORD'
  domain_schema          STRING,
  product_technical_name STRING,
  column_name            STRING,
  record_pk              STRING,
  token_normalized       STRING,
  is_regex               BOOLEAN,
  regex_pattern          STRING,
  regex_flags            STRING,
  mapped_value           STRING,
  mapping_version        INT,
  effective_from         TIMESTAMP,
  effective_to           TIMESTAMP,
  priority               INT,
  notes                  STRING,
  quality_level          STRING,    -- 'MAPPED' | 'VERIFIED'
  verified_by            STRING,
  verified_at            TIMESTAMP
);
```

###### Conversion Rules
```sql
CREATE TABLE IF NOT EXISTS DEMO_CORE.conversion_rules (
  conversion_uri STRING,
  from_uom_uri   STRING,
  to_uom_uri     STRING,
  factor         DOUBLE,
  offset         DOUBLE,
  is_verified    BOOLEAN
);
```

###### DLQ & Run Log
```sql
CREATE TABLE IF NOT EXISTS DEMO_CORE.dlq (...);
CREATE TABLE IF NOT EXISTS DEMO_CORE.dq_run (...);
```

---

#### Examples / Seeds

##### Golden Masters
```sql
-- BOOLEAN
INSERT INTO DEMO_CORE.golden_master_catalog VALUES
 ('https://uri.takeda.io/datatype/boolean/v1','BOOLEAN','TRUE','Boolean True', TRUE),
 ('https://uri.takeda.io/datatype/boolean/v1','BOOLEAN','FALSE','Boolean False', TRUE);

-- Severity
INSERT INTO DEMO_CORE.golden_master_catalog VALUES
 ('https://uri.takeda.io/goldenmaster/quality/severity/code/v1','QUALITY_EVENT_SEVERITY','MINOR','Minor', TRUE),
 ('https://uri.takeda.io/goldenmaster/quality/severity/code/v1','QUALITY_EVENT_SEVERITY','MAJOR','Major', TRUE),
 ('https://uri.takeda.io/goldenmaster/quality/severity/code/v1','QUALITY_EVENT_SEVERITY','CRITICAL','Critical', TRUE);

-- Sites
INSERT INTO DEMO_CORE.golden_master_catalog VALUES
 ('https://uri.takeda.io/goldenmaster/manufacturing/site/site_code/v1','SITE','NEU','Neuchâtel', TRUE),
 ('https://uri.takeda.io/goldenmaster/manufacturing/site/site_code/v1','SITE','MBO','Mass Bio Ops', TRUE),
 ('https://uri.takeda.io/goldenmaster/manufacturing/site/site_code/v1','SITE','VIE','Vienna', TRUE);

-- Serial format
INSERT INTO DEMO_CORE.golden_master_catalog VALUES
 ('https://uri.takeda.io/format/material/xx-xxx-x/v1','SERIAL_FORMAT','XX-XXX-X','Serial dash pattern', TRUE);

-- UOM
INSERT INTO DEMO_CORE.golden_master_catalog VALUES
 ('https://uri.takeda.io/uom/gram/v1','UOM','g','Gram', TRUE),
 ('https://uri.takeda.io/uom/kilogram/v1','UOM','kg','Kilogram', TRUE),
 ('https://uri.takeda.io/uom/tonne/v1','UOM','t','Tonne', TRUE);
```

##### Conversions
```sql
INSERT INTO DEMO_CORE.conversion_rules VALUES
 ('https://uri.takeda.io/conversion/gram-to-kilogram/v1',
  'https://uri.takeda.io/uom/gram/v1',
  'https://uri.takeda.io/uom/kilogram/v1',
  0.001, 0.0, TRUE);

INSERT INTO DEMO_CORE.conversion_rules VALUES
 ('https://uri.takeda.io/conversion/gram-to-kilogram/v1',
  'https://uri.takeda.io/uom/tonne/v1',
  'https://uri.takeda.io/uom/kilogram/v1',
  1000.0, 0.0, TRUE);
```

##### Namespace Mapping
```sql
-- BOOLEAN
INSERT INTO DEMO_CORE.namespace_mapping
(vocabulary, scope_level, token_normalized, is_regex, mapped_value, mapping_version,
 effective_from, priority, quality_level, verified_by, verified_at, notes)
VALUES
 ('BOOLEAN','GLOBAL','yes',false,'TRUE',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'yes→TRUE'),
 ('BOOLEAN','GLOBAL','no', false,'FALSE',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'no→FALSE'),
 ('BOOLEAN','GLOBAL','true',false,'TRUE',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'true→TRUE'),
 ('BOOLEAN','GLOBAL','false',false,'FALSE',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'false→FALSE');

-- BOOLEAN (PRODUCT mapped)
INSERT INTO DEMO_CORE.namespace_mapping
(vocabulary, scope_level, product_technical_name, column_name, token_normalized, is_regex, mapped_value,
 mapping_version, effective_from, priority, quality_level, notes)
VALUES
 ('BOOLEAN','PRODUCT','dp_qm_events_v1','reg_indicator_raw','y',false,'TRUE',1,current_timestamp(),5,'MAPPED','product-level y→TRUE');

-- Severity
INSERT INTO DEMO_CORE.namespace_mapping
(vocabulary, scope_level, token_normalized, is_regex, mapped_value, mapping_version,
 effective_from, priority, quality_level, verified_by, verified_at, notes)
VALUES
 ('QUALITY_EVENT_SEVERITY','GLOBAL','minor',false,'MINOR',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'minor'),
 ('QUALITY_EVENT_SEVERITY','GLOBAL','maj',  false,'MAJOR',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'maj'),
 ('QUALITY_EVENT_SEVERITY','GLOBAL','critical',false,'CRITICAL',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'critical');

-- Severity (PRODUCT mapped)
INSERT INTO DEMO_CORE.namespace_mapping
(vocabulary, scope_level, product_technical_name, column_name, token_normalized, is_regex, mapped_value,
 mapping_version, effective_from, priority, quality_level, notes)
VALUES
 ('QUALITY_EVENT_SEVERITY','PRODUCT','dp_qm_events_v1','severity_token_raw','sev3',false,'CRITICAL',1,current_timestamp(),10,'MAPPED','sev3→CRITICAL product');

-- SITE (VERIFIED globals + record override)
INSERT INTO DEMO_CORE.namespace_mapping
(vocabulary, scope_level, token_normalized, is_regex, mapped_value, mapping_version,
 effective_from, priority, quality_level, verified_by, verified_at, notes)
VALUES
 ('SITE','GLOBAL','neuchatel',false,'NEU',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'NEU'),
 ('SITE','GLOBAL','vienna',   false,'VIE',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'VIE'),
 ('SITE','GLOBAL','mass bio ops',false,'MBO',1,current_timestamp(),0,'VERIFIED','trustee:QA',current_timestamp(),'MBO');

INSERT INTO DEMO_CORE.namespace_mapping
(vocabulary, scope_level, product_technical_name, column_name, record_pk, is_regex, regex_pattern,
 mapped_value, mapping_version, effective_from, priority, quality_level, verified_by, verified_at, notes)
VALUES
 ('SITE','RECORD','dp_qm_events_v1','site_text_raw','E777',true,'^hq$', 'MBO',1,current_timestamp(),50,'VERIFIED','trustee:QA',current_timestamp(),'HQ→MBO record');
```

##### Demo Sources (Wide + Long)

```sql
CREATE SCHEMA IF NOT EXISTS DEMO_QM;
CREATE SCHEMA IF NOT EXISTS DEMO_LAKE;
CREATE SCHEMA IF NOT EXISTS DEMO_HUB;

CREATE TABLE IF NOT EXISTS DEMO_LAKE.qm_events_long (
  event_uid STRING,
  attribute_name STRING,
  attribute_value STRING,
  description_text STRING
);

INSERT INTO DEMO_LAKE.qm_events_long VALUES
 ('E001','reg_indicator_raw','yes','deviation noted'),
 ('E001','severity_token_raw','minor','deviation noted'),
 ('E001','site_text_raw','Neuchatel','deviation noted'),
 ('E001','serial_plain_raw','AB1234','deviation noted'),
 ('E001','mass_raw','1000 g','deviation noted'),

 ('E002','reg_indicator_raw','true','out of spec'),
 ('E002','severity_token_raw','maj','out of spec'),
 ('E002','site_text_raw','Vienna','out of spec'),
 ('E002','serial_plain_raw','CD5678','out of spec'),
 ('E002','mass_raw','0.002 t','out of spec');

CREATE TABLE IF NOT EXISTS DEMO_HUB.qm_events_wide (
  event_uid STRING,
  reg_indicator_raw STRING,
  severity_token_raw STRING,
  site_text_raw STRING,
  serial_plain_raw STRING,
  mass_raw STRING,
  description_text STRING
);

INSERT INTO DEMO_HUB.qm_events_wide VALUES
 ('E003','y','sev3','Mass Bio Ops','EF9012','1.3kg','batch failure'),
 ('E004','TRUE','urgent','HQ','GH0001','2500 g','temp excursion'),
 ('E005','','false','','JK0003','','missing doc'),
 ('E777','yes','critical','HQ','LM0007','750 g','executive audit');
```

---

##### Published Table — Examples

###### Example Boolean & Severity

| event_uid | **reg_indicator_raw** | **reg_indicator** | **reg_indicator_parse_status** | **reg_indicator_verified** | **reg_indicator_verified_parse_status** | **severity_token_raw** | **severity_code** | **severity_parse_status** | **severity_code_verified** | **severity_verified_parse_status** |
|---|---|---|---|---|---|---|---|---|---|---|
| E003 | y    | true | PARSED_OK | NULL | UNPARSABLE | sev3    | CRITICAL | PARSED_OK | NULL | UNPARSABLE |
| E004 | TRUE | true | PARSED_OK | true | PARSED_OK  | urgent  | NULL     | UNPARSABLE | NULL | UNPARSABLE |
| E005 |      | NULL | EMPTY     | NULL | EMPTY      | false   | NULL     | EMPTY      | NULL | EMPTY      |
| E777 | yes  | true | PARSED_OK | true | PARSED_OK  | critical| CRITICAL | PARSED_OK  | CRITICAL | PARSED_OK |

###### Example Site & Serial Number

| event_uid | **site_text_raw** | **site_code** | **site_parse_status** | **site_code_verified** | **site_verified_parse_status** | **serial_plain_raw** | **serial_number** | **serial_number_parse_status** | **serial_number_verified** | **serial_number_verified_parse_status** |
|---|---|---|---|---|---|---|---|---|---|---|
| E003 | Mass Bio Ops | MBO | PARSED_OK | MBO | PARSED_OK | EF9012 | EF-901-2 | PARSED_OK | EF-901-2 | PARSED_OK |
| E004 | HQ           | NULL| UNPARSABLE | NULL| UNPARSABLE | GH0001 | GH-000-1 | PARSED_OK | GH-000-1 | PARSED_OK |
| E005 |              | NULL| EMPTY      | NULL| EMPTY      | JK0003 | JK-000-3 | PARSED_OK | JK-000-3 | PARSED_OK |
| E777 | HQ           | MBO | PARSED_OK  | MBO | PARSED_OK  | LM0007 | LM-000-7 | PARSED_OK | LM-000-7 | PARSED_OK |

###### Example Mass (Conversions)

| event_uid | **mass_raw** | **mass_kg** | **mass_kg_parse_status** | **mass_kg_verified** | **mass_kg_verified_parse_status** |
|---|---|---:|---|---:|---|
| E003 | 1.3kg  | 1.3  | PARSED_OK | 1.3  | PARSED_OK |
| E004 | 2500 g | 2.5  | PARSED_OK | 2.5  | PARSED_OK |
| E005 |        | NULL | EMPTY     | NULL | EMPTY     |
| E777 | 750 g  | 0.75 | PARSED_OK | 0.75 | PARSED_OK |

#### Engine Code (PySpark)

```python
from pyspark.sql import functions as F, Window

def normalize(col):
    return F.lower(F.trim(F.col(col)))

def precedence(scope_col):
    return (F.when(F.col(scope_col)=="RECORD", F.lit(1))
             .when(F.col(scope_col)=="PRODUCT", F.lit(2))
             .when(F.col(scope_col)=="DOMAIN",  F.lit(3))
             .otherwise(F.lit(4)))

def mapping_base(vocabulary):
    return (spark.table("DEMO_CORE.namespace_mapping")
            .where(F.col("vocabulary")==vocabulary)
            .where((F.col("effective_to").isNull()) | (F.col("effective_to")>=F.current_timestamp()))
            .where(F.col("mapping_version")==1))

def choose_mapping(df_norm, pk, schema_name, product_name, raw_col, vcol, vocabulary, quality_mode):
    base = mapping_base(vocabulary)
    if quality_mode == "VERIFIED":
        base = base.where(F.col("quality_level")=="VERIFIED")
    else:
        base = base.where(F.col("quality_level").isin("MAPPED","VERIFIED"))

    exact = base.where(F.coalesce(F.col("is_regex"), F.lit(False))==F.lit(False)) \
        .select("scope_level","domain_schema","product_technical_name","column_name","record_pk",
                "token_normalized","mapped_value","priority","effective_from")

    j_exact = (df_norm.alias("r").join(
        exact.alias("m"),
        (F.col(vcol)==F.col("m.token_normalized")) &
        (
          (F.col("m.scope_level")=="GLOBAL") |
          ((F.col("m.scope_level")=="DOMAIN")  & (F.col("m.domain_schema")==schema_name) & (F.col("m.column_name")==raw_col)) |
          ((F.col("m.scope_level")=="PRODUCT") & (F.col("m.product_technical_name")==product_name) & (F.col("m.column_name")==raw_col)) |
          ((F.col("m.scope_level")=="RECORD")  & (F.col("m.product_technical_name")==product_name) & (F.col("m.column_name")==raw_col) & (F.col("m.record_pk")==F.col(f"r.{pk}")))
        ),
        "left"
    ).selectExpr(f"r.{pk} as entity_pk","m.scope_level","m.priority","m.effective_from","m.mapped_value"))

    regex = base.where(F.coalesce(F.col("is_regex"), F.lit(False))==F.lit(True)) \
        .select("scope_level","domain_schema","product_technical_name","column_name","record_pk",
                "regex_pattern","regex_flags","mapped_value","priority","effective_from")

    j_regex = (df_norm.alias("r").crossJoin(F.broadcast(regex).alias("m"))
        .where(
          (
            (F.col("m.scope_level")=="GLOBAL") |
            ((F.col("m.scope_level")=="DOMAIN")  & (F.col("m.domain_schema")==schema_name) & (F.col("m.column_name")==raw_col)) |
            ((F.col("m.scope_level")=="PRODUCT") & (F.col("m.product_technical_name")==product_name) & (F.col("m.column_name")==raw_col)) |
            ((F.col("m.scope_level")=="RECORD")  & (F.col("m.product_technical_name")==product_name) & (F.col("m.column_name")==raw_col) & (F.col("m.record_pk")==F.col(f"r.{pk}")))
          ) &
          (F.col(vcol).rlike(F.col("m.regex_pattern")))
        )
        .selectExpr(f"r.{pk} as entity_pk","m.scope_level","m.priority","m.effective_from","m.mapped_value"))

    candidates = j_exact.unionByName(j_regex, allowMissingColumns=True)

    w = Window.partitionBy("entity_pk").orderBy(
        precedence("scope_level"), F.col("priority").desc(), F.col("effective_from").desc()
    )
    return (candidates.withColumn("rn", F.row_number().over(w))
                      .where(F.col("rn")==1)
                      .select("entity_pk","mapped_value"))

def convert_to_kg(raw_col):
    num = F.regexp_extract(F.col(raw_col), r'([-+]?\d*\.?\d+)', 0).cast("double")
    unit = F.lower(F.regexp_extract(F.col(raw_col), r'([a-zA-Z]+)', 0))

    unit_norm = (F.when(unit.isin('g','gram','grams'), 'g')
                   .when(unit.isin('kg','kilogram','kilograms'), 'kg')
                   .when(unit.isin('t','ton','tonne','tonnes'), 't')
                   .otherwise(F.lit(None)))

    uom = (spark.table("DEMO_CORE.golden_master_catalog")
                 .where(F.col("gm_domain")=="UOM")
                 .select(F.col("code").alias("uom_code"), F.col("uri").alias("uom_uri")))

    df = (spark.range(1).selectExpr("0 as dummy")
            .withColumn("val", num)
            .withColumn("uom_code", unit_norm))

    df = df.join(uom, "uom_code", "left")

    conv = (spark.table("DEMO_CORE.conversion_rules")
                .where(F.col("to_uom_uri")=="https://uri.takeda.io/uom/kilogram/v1"))

    df = df.join(conv, df.uom_uri==conv.from_uom_uri, "left")

    kg = (F.when(df.uom_code.isNull(), F.lit(None).cast("double"))
            .when(df.from_uom_uri.isNull() & (df.uom_code=='kg'), df.val)
            .when(df.from_uom_uri.isNotNull(), df.val*df.factor + df.offset)
            .otherwise(F.lit(None).cast("double")))

    verified = F.coalesce(df.is_verified, F.lit(False))

    return df.select(kg.alias("kg"), verified.alias("conv_verified")).limit(1)

def run_contract(contract: dict):
    schema   = contract["schema"]
    version  = contract["contract_version"]
    product  = contract["data_products"][0]
    product_name = product["technical_name"]
    pk      = product["primary_key"]
    pubtbl  = product["data_product"]["published_table"]
    elems   = product["data_product"]["data_elements"]

    dfs = []
    for src in contract["raw_sources"]:
        tbl = f"{src['schema']}.{src['table']}"
        df  = spark.table(tbl)
        if src.get("format")=="long":
            rule = next(r for r in contract.get("long_format_rules", []) if r["source_table"].upper()==tbl.upper())
            df = df.groupBy(*rule["pivot"]["index"]).pivot(rule["pivot"]["name_col"]).agg(F.first(rule["pivot"]["value_col"]))
        dfs.append(df)

    raw_union = dfs[0]
    for d in dfs[1:]:
        raw_union = raw_union.unionByName(d, allowMissingColumns=True)

    norm = raw_union
    for e in elems:
        src = e["source"]
        if "from_raw" in src:
            norm = norm.withColumn(f"v__{src['from_raw']}", normalize(src["from_raw"]))

    stg = norm.select(pk, *[e["source"]["from_raw"] for e in elems if "from_raw" in e["source"]])

    select_cols = [pk]
    for e in elems:
        tname = e["technical_name"]
        dtype = e["data_type"].lower()
        raw_col = e["source"]["from_raw"]
        vcol = f"v__{raw_col}"
        is_passthrough = e.get("cleansing",{}).get("passthrough", False)
        vocabulary = e.get("cleansing",{}).get("vocabulary")

        select_cols.append(F.col(raw_col).alias(f"{tname}_raw"))

        if is_passthrough:
            stg = stg.withColumn(tname, F.col(raw_col).cast(dtype))
            stg = stg.withColumn(f"{tname}_parse_status",
                                 F.when(F.col(raw_col).isNull() | (F.col(raw_col)==""), "EMPTY").otherwise("PARSED_OK"))
            stg = stg.withColumn(f"{tname}_verified", F.col(tname))
            stg = stg.withColumn(f"{tname}_verified_parse_status", F.col(f"{tname}_parse_status"))
            select_cols += [F.col(tname), F.col(f"{tname}_parse_status"),
                            F.col(f"{tname}_verified"), F.col(f"{tname}_verified_parse_status")]
            continue

        fmt = e.get("formatting")
        if tname == "serial_number" and fmt:
            stg = stg.withColumn(f"__fmt_val_{tname}",
                        F.when(F.col(raw_col).isNull() | (F.col(raw_col)==""), F.lit(None))
                         .otherwise(F.regexp_replace(F.col(raw_col), fmt["regex_pattern"], fmt["regex_replacement"])))

            stg = stg.withColumn(f"__fmt_ok_{tname}",
                        (F.length(F.regexp_extract(F.col(raw_col), fmt["regex_pattern"], 0))>0))

        conv = e.get("conversion")
        if tname == "mass_kg" and conv:
            mass_conv = convert_to_kg(raw_col)
            stg = stg.withColumn("__mass_val",
                                 F.when(F.col(raw_col).isNull() | (F.col(raw_col)==""), F.lit(None))
                                  .otherwise(F.lit(mass_conv.collect()[0]["kg"]) ))
            stg = stg.withColumn("__mass_verified",
                                 F.when(F.col(raw_col).isNull() | (F.col(raw_col)==""), F.lit(False))
                                  .otherwise(F.lit(mass_conv.collect()[0]["conv_verified"]) ))

        chosen_any = choose_mapping(norm, pk, schema, product_name, raw_col, vcol, vocabulary, "ANY") if vocabulary else None
        if chosen_any is not None:
            stg = stg.join(chosen_any, stg[pk]==chosen_any.entity_pk, "left").drop("entity_pk")

        chosen_ver = choose_mapping(norm, pk, schema, product_name, raw_col, vcol, vocabulary, "VERIFIED") if vocabulary else None
        if chosen_ver is not None:
            stg = stg.join(chosen_ver.withColumnRenamed("mapped_value","mapped_value_ver"),
                           stg[pk]==chosen_ver.entity_pk, "left").drop("entity_pk")

        if vocabulary == "BOOLEAN" or dtype=="boolean":
            stg = (stg.withColumn(tname,
                       F.when(F.col(vcol).isNull() | (F.col(vcol)==""), F.lit(None).cast("boolean"))
                        .when(F.col("mapped_value")=="TRUE",  F.lit(True))
                        .when(F.col("mapped_value")=="FALSE", F.lit(False))
                        .otherwise(F.lit(None).cast("boolean")))
                   .withColumn(f"{tname}_parse_status",
                       F.when(F.col(vcol).isNull() | (F.col(vcol)==""), "EMPTY")
                        .when(F.col("mapped_value").isNotNull(), "PARSED_OK")
                        .otherwise("UNPARSABLE"))
                   .withColumn(f"{tname}_verified",
                       F.when(F.col(vcol).isNull() | (F.col(vcol)==""), F.lit(None).cast("boolean"))
                        .when(F.col("mapped_value_ver")=="TRUE",  F.lit(True))
                        .when(F.col("mapped_value_ver")=="FALSE", F.lit(False))
                        .otherwise(F.lit(None).cast("boolean")))
                   .withColumn(f"{tname}_verified_parse_status",
                       F.when(F.col(vcol).isNull() | (F.col(vcol)==""), "EMPTY")
                        .when(F.col("mapped_value_ver").isNotNull(), "PARSED_OK")
                        .otherwise("UNPARSABLE"))
            )
        elif tname == "serial_number" and fmt:
            stg = (stg.withColumn(tname, F.col(f"__fmt_val_{tname}").cast("string"))
                   .withColumn(f"{tname}_parse_status",
                       F.when(F.col(raw_col).isNull() | (F.col(raw_col)==""), "EMPTY")
                        .when(F.col(f"__fmt_ok_{tname}")==True, "PARSED_OK")
                        .otherwise("BAD_FORMAT"))
                   .withColumn(f"{tname}_verified", F.col(tname))
                   .withColumn(f"{tname}_verified_parse_status", F.col(f"{tname}_parse_status"))
            )
        elif tname == "mass_kg" and conv:
            stg = (stg.withColumn(tname, F.col("__mass_val").cast("double"))
                   .withColumn(f"{tname}_parse_status",
                       F.when(F.col(raw_col).isNull() | (F.col(raw_col)==""), "EMPTY")
                        .when(F.col("__mass_val").isNotNull(), "PARSED_OK")
                        .otherwise("BAD_CONVERSION"))
                   .withColumn(f"{tname}_verified",
                       F.when(F.col("__mass_verified")==True, F.col("__mass_val").cast("double"))
                        .otherwise(F.lit(None).cast("double")))
                   .withColumn(f"{tname}_verified_parse_status",
                       F.when(F.col(raw_col).isNull() | (F.col(raw_col)==""), "EMPTY")
                        .when((F.col("__mass_verified")==True) & F.col("__mass_val").isNotNull(), "PARSED_OK")
                        .otherwise("BAD_CONVERSION"))
            )
        else:
            stg = (stg.withColumn(tname, F.when(F.col("mapped_value").isNotNull(), F.col("mapped_value")).otherwise(F.lit(None).cast("string")))
                   .withColumn(f"{tname}_parse_status",
                       F.when(F.col(vcol).isNull() | (F.col(vcol)==""), "EMPTY")
                        .when(F.col("mapped_value").isNotNull(), "PARSED_OK")
                        .otherwise("UNPARSABLE"))
                   .withColumn(f"{tname}_verified",
                       F.when(F.col("mapped_value_ver").isNotNull(), F.col("mapped_value_ver")).otherwise(F.lit(None).cast("string")))
                   .withColumn(f"{tname}_verified_parse_status",
                       F.when(F.col(vcol).isNull() | (F.col(vcol)==""), "EMPTY")
                        .when(F.col("mapped_value_ver").isNotNull(), "PARSED_OK")
                        .otherwise("UNPARSABLE"))
            )

        select_cols += [F.col(tname), F.col(f"{tname}_parse_status"),
                        F.col(f"{tname}_verified"), F.col(f"{tname}_verified_parse_status")]

        stg = stg.drop("mapped_value","mapped_value_ver")

    out_df = (stg.select(*select_cols)
                .withColumn("data_product_version", F.lit(version))
                .withColumn("_ingestion_ts", F.current_timestamp()))

    spark.sql(f"CREATE SCHEMA IF NOT EXISTS {schema}")
    spark.sql(f"CREATE TABLE IF NOT EXISTS {pubtbl} AS SELECT * FROM (SELECT 1 as __init) WHERE 1=0")
    out_df.write.mode("overwrite").saveAsTable(pubtbl)

    return out_df
```

### Catalogs
### Naming Conventions
- **Data products:** `dp_<subdomain>_<entity>_[detail|item]`
- **Views:** `dv_<subdomain>_<entity>_[detail|item]`
- **Columns:** `snake_case`
  - Booleans: `_flag`
  - Dates: `_date`
  - Foreign Keys: `_id`


### Catalog & Schema Layout
| **Catalog** | **Purpose** |
|---|---|
| `us_gmsgq_core` | Golden Master references & crosswalks. |
| `us_gmsgq_prd` | Production Quality Management data products. |
| `us_gmsgq_dev` | Development workspace / sandbox. |

**Schemas:**
- `core` – reference tables.
- `quality` – event, detail, and item data products.
- `analytics` – published data views.
- `staging` – raw to hub ingestion layers.

# URI Schema  
**Base URI:** `https://uri.takeda.io/`  

This schema standardizes URIs across **data types**, **formats**, **unit conversions**, **unit of measure definitions**, and **golden master entities**.  
All URIs are **semantic**, **versioned**, **machine-resolvable**, and **aligned with data mesh and FAIR data principles**.

---

## Global Namespace Structure

```
https://uri.takeda.io/
 ├── datatype/
 ├── format/
 ├── conversion/
 ├── uom/
 └── goldenmaster/
```

---

## Data Types

> Canonical logical data types used enterprise-wide.

**Base URI:**  
```
https://uri.takeda.io/datatype/
```

| Type | URI | Description |
|------|-----|-------------|
| Boolean | `https://uri.takeda.io/datatype/boolean/v1` | True/False flag |
| Integer | `https://uri.takeda.io/datatype/integer/v1` | Whole numbers |
| Decimal | `https://uri.takeda.io/datatype/decimal/v1` | Fixed-point or floating-point values |
| String | `https://uri.takeda.io/datatype/string/v1` | Text values |
| Date | `https://uri.takeda.io/datatype/date/v1` | `YYYY-MM-DD` |
| Timestamp | `https://uri.takeda.io/datatype/timestamp/v1` | `YYYY-MM-DDThh:mm:ssZ` |
| Enum | `https://uri.takeda.io/datatype/enum/v1` | Discrete coded values |

---

## Data Formats

> Defines how standardized fields are formatted, parsed, or validated.

**Base URI:**  
```
https://uri.takeda.io/format/
```

| Format | URI | Example | Description |
|---------|-----|----------|-------------|
| Date (ISO) | `https://uri.takeda.io/format/date/iso8601/v1` | `2025-10-13` | ISO date |
| Timestamp | `https://uri.takeda.io/format/timestamp/iso8601/v1` | `2025-10-13T09:00:00Z` | ISO timestamp |
| Material Number | `https://uri.takeda.io/format/material/xx-xxx-x/v1` | `12-345-6` | Normalized material code |
| Batch ID | `https://uri.takeda.io/format/batchid/alphanumeric/v1` | `BATCH-000123` | Standardized batch pattern |
| Email | `https://uri.takeda.io/format/email/rfc5322/v1` | `user@takeda.com` | RFC-compliant email |

---

## Conversions

> Defines canonical **unit or value conversions** (physical or logical).

**Base URI:**  
```
https://uri.takeda.io/conversion/
```

| Conversion | URI | Formula / Mapping |
|-------------|-----|-------------------|
| Gram → Kilogram | `https://uri.takeda.io/conversion/gram-to-kilogram/v1` | `1 kg = 1000 g` |
| Milligram → Gram | `https://uri.takeda.io/conversion/milligram-to-gram/v1` | `1 g = 1000 mg` |
| Celsius → Kelvin | `https://uri.takeda.io/conversion/celsius-to-kelvin/v1` | `K = °C + 273.15` |
| USD → EUR | `https://uri.takeda.io/conversion/usd-to-eur/v1` | FX rate lookup |
| Uppercase → Lowercase | `https://uri.takeda.io/conversion/string-upper-to-lower/v1` | `LOWER(value)` |

---

## Units of Measure (UOM)

> Defines **standard unit systems** and **measurement references** (based on UCUM / SI).

**Base URI:**  
```
https://uri.takeda.io/uom/
```

| Unit | URI | Description |
|-------|-----|-------------|
| Gram | `https://uri.takeda.io/uom/gram/v1` | Mass unit |
| Kilogram | `https://uri.takeda.io/uom/kilogram/v1` | SI base mass unit |
| Milligram | `https://uri.takeda.io/uom/milligram/v1` | Subunit of gram |
| Liter | `https://uri.takeda.io/uom/liter/v1` | Volume unit |
| Milliliter | `https://uri.takeda.io/uom/milliliter/v1` | Subunit of liter |
| Celsius | `https://uri.takeda.io/uom/degree-celsius/v1` | Temperature |
| Kelvin | `https://uri.takeda.io/uom/kelvin/v1` | SI base temperature |
| Percent | `https://uri.takeda.io/uom/percent/v1` | Dimensionless ratio |

---

## Golden Master Catalog

> **Verified reference entities** used across domains and systems.  
> Each attribute has a stable, versioned URI.

**Base URI:**  
```
https://uri.takeda.io/goldenmaster/
```

**Pattern:**  
```
https://uri.takeda.io/goldenmaster/{domain}/{entity}/{attribute}/v1
```

| Entity | URI | Description |
|---------|-----|-------------|
| Material | `https://uri.takeda.io/goldenmaster/supplychain/material/material_id/v1` | Master material ID |
| Plant | `https://uri.takeda.io/goldenmaster/manufacturing/plant/plant_code/v1` | Manufacturing plant code |
| Country | `https://uri.takeda.io/goldenmaster/global/country/iso_code/v1` | ISO 3166 country code |
| Product | `https://uri.takeda.io/goldenmaster/product/product_number/v1` | Product master record |
| Supplier | `https://uri.takeda.io/goldenmaster/procurement/supplier/supplier_id/v1` | Vendor registry entry |

---

## Data Product Lineage Example

| Layer | Example URI | Purpose |
|--------|--------------|---------|
| **Raw** | `https://uri.takeda.io/raw/sap/material/material_id/v1` | Extracted from SAP |
| **Product (parsed)** | `https://uri.takeda.io/product/supplychain/material/material_id_parsed/v1` | Normalized format |
| **Domain (verified)** | `https://uri.takeda.io/domain/supplychain/material/material_id_verified/v1` | Validated vs Golden Master |
| **Global (published)** | `https://uri.takeda.io/global/supplychain/material/material_id/v1` | Enterprise-wide publication |

---

## Namespace Mapping Example (JSON)

```json
{
  "namespace_mapping": {
    "record_uri": "https://uri.takeda.io/raw/sap/material/material_id/v1",
    "golden_master_ref": "https://uri.takeda.io/goldenmaster/supplychain/material/material_id/v1",
    "datatype_ref": "https://uri.takeda.io/datatype/string/v1",
    "format_ref": "https://uri.takeda.io/format/material/xx-xxx-x/v1",
    "conversion_ref": "https://uri.takeda.io/conversion/gram-to-kilogram/v1",
    "uom_ref": "https://uri.takeda.io/uom/kilogram/v1"
  }
}
```

---

# Naming Conventions

| Rule | Description |
|------|--------------|
| **Lowercase + hyphens** | For readability and consistency |
| **Versioned suffix `/vX`** | Semantic version control |
| **No abbreviations** | Use full words (`conversion`, not `conv`) |
| **Immutable URIs** | Once published, only deprecated via `/deprecated/vX` |
| **Uniform hierarchy** | Consistent path logic across all domains |

---

# Future Extensions

| Namespace | Planned Scope |
|------------|----------------|
| `/quality/` | Deviation, CAPA, change control reference models |
| `/event/` | Standard event schemas |
| `/metric/` | KPI and measurement models |
| `/policy/` | Data governance and access policies |



## Catalog & Exposure
- **Catalog registration** renders business/technical contracts and current **star rating**.
- **Access patterns**: SQL in lakehouse, governed APIs, and OLAP models (as defined per product).

---

## Appendix — Abbreviations
ABAC, API, BPO, CDE, DQ, DR, FK, GBPO, GxP, KPI, LIMS, ML, PK, RBAC, SLA, URI, etc.

# Code to establish the first data product

DLT pipeline so it’s fully executable in us_gmsgq_domain_dev.quality, now including:
Item data products (Root Cause, Impacted Location)
Core reference products (Golden Master + Crosswalk) with seed content
Cleaning & type casts (booleans, dates, trims)
Clear list of exactly what gets created
Note on Unity Catalog & DLT target: A single DLT pipeline can publish to one target (catalog.schema). To keep this pipeline “exclusively” in us_gmsgq_domain_dev, all tables (including “core” refs) land in us_gmsgq_domain_dev.quality. If you require refs in a separate schema (e.g., us_gmsgq_domain_dev.core), run a tiny second DLT pipeline with target="us_gmsgq_domain_dev.core" and move the 2 ref tables there — I can provide that too.

## Data Product Contract
Put this file in your repo as contracts/quality_management.yml.
It’s human-readable and machine-enforceable (your DLT code below reads and applies it).

```yaml
# ==============================================================================
# Data Contract — Quality Management (Enterprise Data Mesh, DLT-Ready)
# ==============================================================================
# Purpose:
#   Contract-driven definition of Quality Management data products (master, details,
#   items) with explicit source ingestion metadata for wide/long inputs so a DLT
#   runner can create pipelines: read → normalize (pivot for long) → cleanse →
#   publish.
#
# Conventions:
#   - "data_elements" (not "columns").
#   - Reference vocabularies resolved via CORE catalogs:
#       <core_schema>.golden_master_catalog
#       <core_schema>.namespace_mapping
#   - Dual quality & scope precedence handled by the platform cleansing engine.
#   - "from_raw" supports:
#       * wide column: { ref: <source_id>, column: <raw_col_name> }
#       * long attribute: { ref: <source_id>, attribute_key: <name_in_long> }
#   - Each product declares ingest.sources[] and optional long_pivot rules.
# ==============================================================================

contract_version: "1.0.0"

product:
  domain: "Quality Management"
  name: "quality_events"
  version: "1.0.0"
  owner:
    team: "GMSGQ Data Engineering"
    email: "qm-data@takeda.com"
  sla:
    freshness_minutes: 60
    completeness_threshold: 0.99
    fk_validity_threshold: 0.995
    availability_pct_month: 99.5

namespaces:
  core_schema: "us_gmsgq_domain_dev.core"
  quality_schema: "us_gmsgq_domain_dev.quality"

# ------------------------------------------------------------------------------
# Global Raw Sources (may be reused by multiple products)
# ------------------------------------------------------------------------------
# NOTE: These describe physical raw landing/curated tables and their shapes.
raw_sources:
  # ---------------- Master / Shared ----------------
  - id: ev_long
    fqn: "us_gmsgq_domain_dev.lake.qm_event_long"
    format: "long"
    keys: ["record_id", "event_type"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["record_id", "event_type"]

  - id: ev_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_event_wide"
    format: "wide"
    keys: ["record_id", "event_type"]

  # ---------------- Detail sources (1:1) ----------------
  - id: dev_long
    fqn: "us_gmsgq_domain_dev.lake.qm_deviation_detail_long"
    format: "long"
    keys: ["record_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["record_id"]

  - id: dev_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_deviation_detail_wide"
    format: "wide"
    keys: ["record_id"]

  - id: capa_long
    fqn: "us_gmsgq_domain_dev.lake.qm_capa_detail_long"
    format: "long"
    keys: ["record_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["record_id"]

  - id: capa_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_capa_detail_wide"
    format: "wide"
    keys: ["record_id"]

  - id: li_long
    fqn: "us_gmsgq_domain_dev.lake.qm_lab_inv_detail_long"
    format: "long"
    keys: ["record_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["record_id"]

  - id: li_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_lab_inv_detail_wide"
    format: "wide"
    keys: ["record_id"]

  - id: cc_long
    fqn: "us_gmsgq_domain_dev.lake.qm_change_control_detail_long"
    format: "long"
    keys: ["record_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["record_id"]

  - id: cc_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_change_control_detail_wide"
    format: "wide"
    keys: ["record_id"]

  - id: comp_long
    fqn: "us_gmsgq_domain_dev.lake.qm_complaint_detail_long"
    format: "long"
    keys: ["record_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["record_id"]

  - id: comp_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_complaint_detail_wide"
    format: "wide"
    keys: ["record_id"]

  # ---------------- Items (1:N) ----------------
  - id: rc_long
    fqn: "us_gmsgq_domain_dev.lake.qm_root_cause_item_long"
    format: "long"
    keys: ["record_id", "event_type", "root_cause_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["record_id", "event_type", "root_cause_id"]

  - id: rc_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_root_cause_item_wide"
    format: "wide"
    keys: ["record_id", "event_type", "root_cause_id"]

  - id: il_long
    fqn: "us_gmsgq_domain_dev.lake.qm_impacted_location_item_long"
    format: "long"
    keys: ["record_id", "event_type", "location_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["record_id", "event_type", "location_id"]

  - id: il_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_impacted_location_item_wide"
    format: "wide"
    keys: ["record_id", "event_type", "location_id"]

  # ---------------- Tasks (1:N) ----------------
  - id: task_long
    fqn: "us_gmsgq_domain_dev.lake.qm_task_detail_long"
    format: "long"
    keys: ["task_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["task_id"]

  - id: task_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_task_detail_wide"
    format: "wide"
    keys: ["task_id"]

  - id: task_det_long
    fqn: "us_gmsgq_domain_dev.lake.qm_task_detail_expanded_long"
    format: "long"
    keys: ["task_id"]
    long_format:
      name_col: "attribute_name"
      value_col: "attribute_value"
      index: ["task_id"]

  - id: task_det_wide
    fqn: "us_gmsgq_domain_dev.hub.qm_task_detail_expanded_wide"
    format: "wide"
    keys: ["task_id"]

# ------------------------------------------------------------------------------
# CORE catalogs (authoritative reference & crosswalk)
# ------------------------------------------------------------------------------
core_catalogs:
  golden_master_catalog:
    table_fqn: "us_gmsgq_domain_dev.core.golden_master_catalog"
    version: "v1.0"
    latest: true
  namespace_mapping:
    table_fqn: "us_gmsgq_domain_dev.core.namespace_mapping"
    version: "v1.0"
    latest: true

# ------------------------------------------------------------------------------
# Tables index (for discoverability)
# ------------------------------------------------------------------------------
tables_index:
  - { category: "Master", data_product: "Quality Events", purpose: "Canonical header for all events (all types).", table_name: "dp_quality_management_event", version: "v1.0", latest: true }
  - { category: "Event Detail (1:1)", data_product: "Deviation Detail", purpose: "Deviation-specific attributes.", table_name: "dp_quality_management_event_detail_deviation", version: "v1.0", latest: true }
  - { category: "Event Detail (1:1)", data_product: "CAPA Detail", purpose: "CAPA-specific attributes.", table_name: "dp_quality_management_event_detail_capa", version: "v1.0", latest: true }
  - { category: "Event Detail (1:1)", data_product: "Lab Investigation Detail", purpose: "Lab Investigation-specific attributes.", table_name: "dp_quality_management_event_detail_lab_investigation", version: "v1.0", latest: true }
  - { category: "Event Detail (1:1)", data_product: "Change Control Detail", purpose: "Change Control-specific attributes.", table_name: "dp_quality_management_event_detail_change_control", version: "v1.0", latest: true }
  - { category: "Event Detail (1:1)", data_product: "Complaint Detail", purpose: "Complaint-specific attributes.", table_name: "dp_quality_management_event_detail_complaint", version: "v1.0", latest: true }
  - { category: "Item (1:N)", data_product: "Root Cause Items", purpose: "Root cause list per event (Deviation/LI).", table_name: "dp_quality_management_item_root_cause", version: "v1.0", latest: true }
  - { category: "Item (1:N)", data_product: "Impacted Location Items", purpose: "Impacted locations list per event.", table_name: "dp_quality_management_item_impacted_location", version: "v1.0", latest: true }
  - { category: "Detail (child, 1:N)", data_product: "Task (Detail level)", purpose: "Task records under an event (...)", table_name: "dp_quality_management_event_detail_task", version: "v1.0", latest: true }
  - { category: "Detail (1:1)", data_product: "Task Detail", purpose: "Consolidated attributes by task type.", table_name: "dp_quality_management_event_detail_task_detail", version: "v1.0", latest: true }
  - { category: "Core Reference", data_product: "Golden Master", purpose: "All enums/ref values & labels.", table_name: "core.golden_master_catalog", version: "v1.0", latest: true }
  - { category: "Core Crosswalk", data_product: "Golden Crosswalk", purpose: "Namespaced values → golden labels.", table_name: "core.namespace_mapping", version: "v1.0", latest: true }

# ------------------------------------------------------------------------------
# Contracts (DATA PRODUCTS) — with source/from_raw mappings
# ------------------------------------------------------------------------------

contracts:

  # ============================================================================
  # MASTER: Quality Events
  # ============================================================================
  - entity: "dp_quality_management_event"
    schema: "quality"
    table_name: "dp_quality_management_event"
    version: "v1.0"
    latest: true
    primary_key: ["record_id", "event_type"]

    ingest:
      preferred_shape: "wide"       # runner should prefer wide when present
      sources:
        - { ref: "ev_wide", required: false, weight: 100 }
        - { ref: "ev_long", required: false, weight: 50 }
      long_pivot:
        ref: "ev_long"
        index: ["record_id", "event_type"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "record_id_not_null", expression: "record_id IS NOT NULL", severity: "drop" }
      - { name: "opened_date_not_null", expression: "opened_date IS NOT NULL", severity: "drop" }
      - { name: "date_order_ok", expression: "(closed_date IS NULL) OR (opened_date <= closed_date)", severity: "drop" }
      - { name: "event_type_resolves", expression: "event_type IS NULL OR event_type IN (__GM.EVENT_TYPE.codes__)", severity: "warn" }
      - { name: "status_resolves", expression: "status_name IS NULL OR status_name IN (__GM.STATUS.codes__)", severity: "warn" }

    data_elements:
      - technical_name: "record_id"
        business_name: "Record ID"
        description: "Unique identifier of the quality event record."
        data_type: "BIGINT"
        source:
          from_raw:
            - { ref: "ev_wide", column: "record_id" }
            - { ref: "ev_long", attribute_key: "record_id" }

      - technical_name: "event_type"
        business_name: "Event Type"
        description: "Type of quality event."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "event_type" }
            - { ref: "ev_long", attribute_key: "event_type" }
        cleansing:
          vocabulary: "EVENT_TYPE"
          goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/event_type/v1"

      - technical_name: "status_name"
        business_name: "Status"
        description: "Workflow status of the event."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "status_name" }
            - { ref: "ev_long", attribute_key: "status_name" }
        cleansing:
          vocabulary: "STATUS"
          goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/status/v1"

      - technical_name: "title"
        business_name: "Title"
        description: "Event title as maintained in the source system."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "title" }
            - { ref: "ev_long", attribute_key: "title" }

      - technical_name: "opened_date"
        business_name: "Opened Date"
        description: "Date when the event was opened."
        data_type: "DATE"
        source:
          from_raw:
            - { ref: "ev_wide", column: "opened_date" }
            - { ref: "ev_long", attribute_key: "opened_date" }

      - technical_name: "target_date"
        business_name: "Target Date"
        description: "Target closure or response date."
        data_type: "DATE"
        source:
          from_raw:
            - { ref: "ev_wide", column: "target_date" }
            - { ref: "ev_long", attribute_key: "target_date" }

      - technical_name: "original_closed_date"
        business_name: "Original Closed Date"
        description: "Originally scheduled closed date before any changes."
        data_type: "DATE"
        source:
          from_raw:
            - { ref: "ev_wide", column: "original_closed_date" }
            - { ref: "ev_long", attribute_key: "original_closed_date" }

      - technical_name: "closed_date"
        business_name: "Closed Date"
        description: "Actual event closure date if closed."
        data_type: "DATE"
        source:
          from_raw:
            - { ref: "ev_wide", column: "closed_date" }
            - { ref: "ev_long", attribute_key: "closed_date" }

      - technical_name: "originator_name"
        business_name: "Originator"
        description: "Person who initiated the event."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "originator_name" }
            - { ref: "ev_long", attribute_key: "originator_name" }

      - technical_name: "assigned_to_name"
        business_name: "Assigned To"
        description: "Current responsible person for the event."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "assigned_to_name" }
            - { ref: "ev_long", attribute_key: "assigned_to_name" }

      - technical_name: "assigned_to_email"
        business_name: "Assigned To Email"
        description: "Email address of the current responsible person."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "assigned_to_email" }
            - { ref: "ev_long", attribute_key: "assigned_to_email" }
        formatting:
          source_format_uri: "https://uri.takeda.io/format/email/rfc5322/v1"
          target_format_uri: "https://uri.takeda.io/format/email/rfc5322/v1"
          regex_pattern: "^[^@\\s]+@[^@\\s]+\\.[^@\\s]+$"
          regex_replacement: "$0"

      - technical_name: "current_state_ts"
        business_name: "Current State Timestamp"
        description: "Timestamp of the last state change."
        data_type: "TIMESTAMP"
        source:
          from_raw:
            - { ref: "ev_wide", column: "current_state_ts" }
            - { ref: "ev_long", attribute_key: "current_state_ts" }

      - technical_name: "record_updated_ts"
        business_name: "Record Updated Timestamp"
        description: "Timestamp of the last update to the record."
        data_type: "TIMESTAMP"
        source:
          from_raw:
            - { ref: "ev_wide", column: "record_updated_ts" }
            - { ref: "ev_long", attribute_key: "record_updated_ts" }

      - technical_name: "operational_unit"
        business_name: "Operational Unit"
        description: "Operational unit associated with the record."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "operational_unit" }
            - { ref: "ev_long", attribute_key: "operational_unit" }
        cleansing:
          vocabulary: "OPERATIONAL_UNIT"
          goldenmaster_uri: "https://uri.takeda.io/goldenmaster/organization/operational_unit/v1"

      - technical_name: "owning_dept"
        business_name: "Owning Department"
        description: "Department owning the record."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "owning_dept" }
            - { ref: "ev_long", attribute_key: "owning_dept" }
        cleansing:
          vocabulary: "DEPARTMENT"
          goldenmaster_uri: "https://uri.takeda.io/goldenmaster/organization/department/v1"

      - technical_name: "owning_group"
        business_name: "Owning Group"
        description: "Group or team owning the record."
        data_type: "STRING"
        source:
          from_raw:
            - { ref: "ev_wide", column: "owning_group" }
            - { ref: "ev_long", attribute_key: "owning_group" }
        cleansing:
          vocabulary: "GROUP"
          goldenmaster_uri: "https://uri.takeda.io/goldenmaster/organization/group/v1"

  # ============================================================================
  # EVENT DETAIL (1:1): Deviation
  # ============================================================================
  - entity: "dp_quality_management_event_detail_deviation"
    schema: "quality"
    table_name: "dp_quality_management_event_detail_deviation"
    version: "v1.0"
    latest: true
    primary_key: ["record_id"]
    foreign_keys:
      - { column: "record_id", references: { entity: "dp_quality_management_event", key: "record_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "dev_wide", required: false, weight: 100 }
        - { ref: "dev_long", required: false, weight: 50 }
      long_pivot:
        ref: "dev_long"
        index: ["record_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "record_id_not_null", expression: "record_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "record_id", business_name: "Record ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "dev_wide", column: "record_id" }, { ref: "dev_long", attribute_key: "record_id" } ] } }
      - { technical_name: "deviation_category", business_name: "Deviation Category", data_type: "STRING",
          source: { from_raw: [ { ref: "dev_wide", column: "deviation_category" }, { ref: "dev_long", attribute_key: "deviation_category" } ] },
          cleansing: { vocabulary: "DEVIATION_CATEGORY", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/deviation_category/v1" } }
      - { technical_name: "detected_phase", business_name: "Detected Phase", data_type: "STRING",
          source: { from_raw: [ { ref: "dev_wide", column: "detected_phase" }, { ref: "dev_long", attribute_key: "detected_phase" } ] },
          cleansing: { vocabulary: "PHASE", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/phase/v1" } }
      - { technical_name: "batch_number", business_name: "Batch Number", data_type: "STRING",
          source: { from_raw: [ { ref: "dev_wide", column: "batch_number" }, { ref: "dev_long", attribute_key: "batch_number" } ] } }
      - { technical_name: "gxp_relevance_flag", business_name: "GxP Relevant", data_type: "BOOLEAN",
          source: { from_raw: [ { ref: "dev_wide", column: "gxp_relevance_flag" }, { ref: "dev_long", attribute_key: "gxp_relevance_flag" } ] },
          cleansing: { vocabulary: "BOOLEAN", goldenmaster_uri: "https://uri.takeda.io/datatype/boolean/v1" } }

  # ============================================================================
  # EVENT DETAIL (1:1): CAPA
  # ============================================================================
  - entity: "dp_quality_management_event_detail_capa"
    schema: "quality"
    table_name: "dp_quality_management_event_detail_capa"
    version: "v1.0"
    latest: true
    primary_key: ["record_id"]
    foreign_keys:
      - { column: "record_id", references: { entity: "dp_quality_management_event", key: "record_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "capa_wide", required: false, weight: 100 }
        - { ref: "capa_long", required: false, weight: 50 }
      long_pivot:
        ref: "capa_long"
        index: ["record_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "record_id_not_null", expression: "record_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "record_id", business_name: "Record ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "capa_wide", column: "record_id" }, { ref: "capa_long", attribute_key: "record_id" } ] } }
      - { technical_name: "capa_classification", business_name: "CAPA Classification", data_type: "STRING",
          source: { from_raw: [ { ref: "capa_wide", column: "capa_classification" }, { ref: "capa_long", attribute_key: "capa_classification" } ] },
          cleansing: { vocabulary: "CAPA_CLASSIFICATION", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/capa_classification/v1" } }
      - { technical_name: "effectiveness_check_due", business_name: "Effectiveness Check Due", data_type: "DATE",
          source: { from_raw: [ { ref: "capa_wide", column: "effectiveness_check_due" }, { ref: "capa_long", attribute_key: "effectiveness_check_due" } ] } }
      - { technical_name: "effectiveness_status", business_name: "Effectiveness Status", data_type: "STRING",
          source: { from_raw: [ { ref: "capa_wide", column: "effectiveness_status" }, { ref: "capa_long", attribute_key: "effectiveness_status" } ] },
          cleansing: { vocabulary: "EFFECTIVENESS_STATUS", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/effectiveness_status/v1" } }

  # ============================================================================
  # EVENT DETAIL (1:1): Lab Investigation
  # ============================================================================
  - entity: "dp_quality_management_event_detail_lab_investigation"
    schema: "quality"
    table_name: "dp_quality_management_event_detail_lab_investigation"
    version: "v1.0"
    latest: true
    primary_key: ["record_id"]
    foreign_keys:
      - { column: "record_id", references: { entity: "dp_quality_management_event", key: "record_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "li_wide", required: false, weight: 100 }
        - { ref: "li_long", required: false, weight: 50 }
      long_pivot:
        ref: "li_long"
        index: ["record_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "record_id_not_null", expression: "record_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "record_id", business_name: "Record ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "li_wide", column: "record_id" }, { ref: "li_long", attribute_key: "record_id" } ] } }
      - { technical_name: "oos_category", business_name: "OOS Category", data_type: "STRING",
          source: { from_raw: [ { ref: "li_wide", column: "oos_category" }, { ref: "li_long", attribute_key: "oos_category" } ] },
          cleansing: { vocabulary: "OOS_CATEGORY", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/oos_category/v1" } }
      - { technical_name: "test_method", business_name: "Test Method", data_type: "STRING",
          source: { from_raw: [ { ref: "li_wide", column: "test_method" }, { ref: "li_long", attribute_key: "test_method" } ] } }
      - { technical_name: "sample_id", business_name: "Sample ID", data_type: "STRING",
          source: { from_raw: [ { ref: "li_wide", column: "sample_id" }, { ref: "li_long", attribute_key: "sample_id" } ] } }

  # ============================================================================
  # EVENT DETAIL (1:1): Change Control
  # ============================================================================
  - entity: "dp_quality_management_event_detail_change_control"
    schema: "quality"
    table_name: "dp_quality_management_event_detail_change_control"
    version: "v1.0"
    latest: true
    primary_key: ["record_id"]
    foreign_keys:
      - { column: "record_id", references: { entity: "dp_quality_management_event", key: "record_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "cc_wide", required: false, weight: 100 }
        - { ref: "cc_long", required: false, weight: 50 }
      long_pivot:
        ref: "cc_long"
        index: ["record_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "record_id_not_null", expression: "record_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "record_id", business_name: "Record ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "cc_wide", column: "record_id" }, { ref: "cc_long", attribute_key: "record_id" } ] } }
      - { technical_name: "change_category", business_name: "Change Category", data_type: "STRING",
          source: { from_raw: [ { ref: "cc_wide", column: "change_category" }, { ref: "cc_long", attribute_key: "change_category" } ] },
          cleansing: { vocabulary: "CHANGE_CATEGORY", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/change_category/v1" } }
      - { technical_name: "change_risk_level", business_name: "Change Risk Level", data_type: "STRING",
          source: { from_raw: [ { ref: "cc_wide", column: "change_risk_level" }, { ref: "cc_long", attribute_key: "change_risk_level" } ] },
          cleansing: { vocabulary: "RISK_LEVEL", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/risk_level/v1" } }
      - { technical_name: "implementation_date", business_name: "Implementation Date", data_type: "DATE",
          source: { from_raw: [ { ref: "cc_wide", column: "implementation_date" }, { ref: "cc_long", attribute_key: "implementation_date" } ] } }

  # ============================================================================
  # EVENT DETAIL (1:1): Complaint
  # ============================================================================
  - entity: "dp_quality_management_event_detail_complaint"
    schema: "quality"
    table_name: "dp_quality_management_event_detail_complaint"
    version: "v1.0"
    latest: true
    primary_key: ["record_id"]
    foreign_keys:
      - { column: "record_id", references: { entity: "dp_quality_management_event", key: "record_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "comp_wide", required: false, weight: 100 }
        - { ref: "comp_long", required: false, weight: 50 }
      long_pivot:
        ref: "comp_long"
        index: ["record_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "record_id_not_null", expression: "record_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "record_id", business_name: "Record ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "comp_wide", column: "record_id" }, { ref: "comp_long", attribute_key: "record_id" } ] } }
      - { technical_name: "complaint_category", business_name: "Complaint Category", data_type: "STRING",
          source: { from_raw: [ { ref: "comp_wide", column: "complaint_category" }, { ref: "comp_long", attribute_key: "complaint_category" } ] },
          cleansing: { vocabulary: "COMPLAINT_CATEGORY", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/complaint_category/v1" } }
      - { technical_name: "reporting_market", business_name: "Reporting Market", data_type: "STRING",
          source: { from_raw: [ { ref: "comp_wide", column: "reporting_market" }, { ref: "comp_long", attribute_key: "reporting_market" } ] },
          cleansing: { vocabulary: "MARKET", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/commercial/market/v1" } }
      - { technical_name: "reported_date", business_name: "Reported Date", data_type: "DATE",
          source: { from_raw: [ { ref: "comp_wide", column: "reported_date" }, { ref: "comp_long", attribute_key: "reported_date" } ] } }

  # ============================================================================
  # ITEM (1:N): Root Cause Items
  # ============================================================================
  - entity: "dp_quality_management_item_root_cause"
    schema: "quality"
    table_name: "dp_quality_management_item_root_cause"
    version: "v1.0"
    latest: true
    primary_key: ["record_id", "event_type", "root_cause_id"]
    foreign_keys:
      - { column: "record_id", references: { entity: "dp_quality_management_event", key: "record_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "rc_wide", required: false, weight: 100 }
        - { ref: "rc_long", required: false, weight: 50 }
      long_pivot:
        ref: "rc_long"
        index: ["record_id", "event_type", "root_cause_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "record_id_not_null", expression: "record_id IS NOT NULL", severity: "drop" }
      - { name: "root_cause_id_not_null", expression: "root_cause_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "record_id", business_name: "Record ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "rc_wide", column: "record_id" }, { ref: "rc_long", attribute_key: "record_id" } ] } }
      - { technical_name: "event_type", business_name: "Event Type", data_type: "STRING",
          source: { from_raw: [ { ref: "rc_wide", column: "event_type" }, { ref: "rc_long", attribute_key: "event_type" } ] } }
      - { technical_name: "root_cause_id", business_name: "Root Cause ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "rc_wide", column: "root_cause_id" }, { ref: "rc_long", attribute_key: "root_cause_id" } ] } }
      - { technical_name: "root_cause_category", business_name: "Root Cause Category", data_type: "STRING",
          source: { from_raw: [ { ref: "rc_wide", column: "root_cause_category" }, { ref: "rc_long", attribute_key: "root_cause_category" } ] },
          cleansing: { vocabulary: "ROOT_CAUSE_CATEGORY", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/root_cause_category/v1" } }
      - { technical_name: "root_cause_text", business_name: "Root Cause Text", data_type: "STRING",
          source: { from_raw: [ { ref: "rc_wide", column: "root_cause_text" }, { ref: "rc_long", attribute_key: "root_cause_text" } ] } }

  # ============================================================================
  # ITEM (1:N): Impacted Location Items
  # ============================================================================
  - entity: "dp_quality_management_item_impacted_location"
    schema: "quality"
    table_name: "dp_quality_management_item_impacted_location"
    version: "v1.0"
    latest: true
    primary_key: ["record_id", "event_type", "location_id"]
    foreign_keys:
      - { column: "record_id", references: { entity: "dp_quality_management_event", key: "record_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "il_wide", required: false, weight: 100 }
        - { ref: "il_long", required: false, weight: 50 }
      long_pivot:
        ref: "il_long"
        index: ["record_id", "event_type", "location_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "record_id_not_null", expression: "record_id IS NOT NULL", severity: "drop" }
      - { name: "location_id_not_null", expression: "location_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "record_id", business_name: "Record ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "il_wide", column: "record_id" }, { ref: "il_long", attribute_key: "record_id" } ] } }
      - { technical_name: "event_type", business_name: "Event Type", data_type: "STRING",
          source: { from_raw: [ { ref: "il_wide", column: "event_type" }, { ref: "il_long", attribute_key: "event_type" } ] } }
      - { technical_name: "location_id", business_name: "Location ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "il_wide", column: "location_id" }, { ref: "il_long", attribute_key: "location_id" } ] } }
      - { technical_name: "site_code", business_name: "Site Code", data_type: "STRING",
          source: { from_raw: [ { ref: "il_wide", column: "site_code" }, { ref: "il_long", attribute_key: "site_code" } ] },
          cleansing: { vocabulary: "SITE", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/manufacturing/site/site_code/v1" } }
      - { technical_name: "area_name", business_name: "Area Name", data_type: "STRING",
          source: { from_raw: [ { ref: "il_wide", column: "area_name" }, { ref: "il_long", attribute_key: "area_name" } ] } }

  # ============================================================================
  # DETAIL (child, 1:N): Task (Detail level)
  # ============================================================================
  - entity: "dp_quality_management_event_detail_task"
    schema: "quality"
    table_name: "dp_quality_management_event_detail_task"
    version: "v1.0"
    latest: true
    primary_key: ["task_id"]
    foreign_keys:
      - { column: "record_id", references: { entity: "dp_quality_management_event", key: "record_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "task_wide", required: false, weight: 100 }
        - { ref: "task_long", required: false, weight: 50 }
      long_pivot:
        ref: "task_long"
        index: ["task_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "task_id_not_null", expression: "task_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "task_id", business_name: "Task ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "task_wide", column: "task_id" }, { ref: "task_long", attribute_key: "task_id" } ] } }
      - { technical_name: "record_id", business_name: "Record ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "task_wide", column: "record_id" }, { ref: "task_long", attribute_key: "record_id" } ] } }
      - { technical_name: "event_type", business_name: "Event Type", data_type: "STRING",
          source: { from_raw: [ { ref: "task_wide", column: "event_type" }, { ref: "task_long", attribute_key: "event_type" } ] } }
      - { technical_name: "task_type", business_name: "Task Type", data_type: "STRING",
          source: { from_raw: [ { ref: "task_wide", column: "task_type" }, { ref: "task_long", attribute_key: "task_type" } ] },
          cleansing: { vocabulary: "TASK_TYPE", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/task_type/v1" } }
      - { technical_name: "status_name", business_name: "Status", data_type: "STRING",
          source: { from_raw: [ { ref: "task_wide", column: "status_name" }, { ref: "task_long", attribute_key: "status_name" } ] },
          cleansing: { vocabulary: "STATUS", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/status/v1" } }
      - { technical_name: "assigned_to_name", business_name: "Assigned To", data_type: "STRING",
          source: { from_raw: [ { ref: "task_wide", column: "assigned_to_name" }, { ref: "task_long", attribute_key: "assigned_to_name" } ] } }
      - { technical_name: "assigned_to_email", business_name: "Assigned To Email", data_type: "STRING",
          source: { from_raw: [ { ref: "task_wide", column: "assigned_to_email" }, { ref: "task_long", attribute_key: "assigned_to_email" } ] },
          formatting: { source_format_uri: "https://uri.takeda.io/format/email/rfc5322/v1", target_format_uri: "https://uri.takeda.io/format/email/rfc5322/v1",
                        regex_pattern: "^[^@\\s]+@[^@\\s]+\\.[^@\\s]+$", regex_replacement: "$0" } }
      - { technical_name: "opened_date", business_name: "Opened Date", data_type: "DATE",
          source: { from_raw: [ { ref: "task_wide", column: "opened_date" }, { ref: "task_long", attribute_key: "opened_date" } ] } }
      - { technical_name: "target_date", business_name: "Target Date", data_type: "DATE",
          source: { from_raw: [ { ref: "task_wide", column: "target_date" }, { ref: "task_long", attribute_key: "target_date" } ] } }
      - { technical_name: "closed_date", business_name: "Closed Date", data_type: "DATE",
          source: { from_raw: [ { ref: "task_wide", column: "closed_date" }, { ref: "task_long", attribute_key: "closed_date" } ] } }
      - { technical_name: "quality_approval_flag", business_name: "Quality Approval", data_type: "BOOLEAN",
          source: { from_raw: [ { ref: "task_wide", column: "quality_approval_flag" }, { ref: "task_long", attribute_key: "quality_approval_flag" } ] },
          cleansing: { vocabulary: "BOOLEAN", goldenmaster_uri: "https://uri.takeda.io/datatype/boolean/v1" } }

  # ============================================================================
  # DETAIL (1:1): Task Detail (consolidated per task_type)
  # ============================================================================
  - entity: "dp_quality_management_event_detail_task_detail"
    schema: "quality"
    table_name: "dp_quality_management_event_detail_task_detail"
    version: "v1.0"
    latest: true
    primary_key: ["task_id"]
    foreign_keys:
      - { column: "task_id", references: { entity: "dp_quality_management_event_detail_task", key: "task_id" } }

    ingest:
      preferred_shape: "wide"
      sources:
        - { ref: "task_det_wide", required: false, weight: 100 }
        - { ref: "task_det_long", required: false, weight: 50 }
      long_pivot:
        ref: "task_det_long"
        index: ["task_id"]
        name_col: "attribute_name"
        value_col: "attribute_value"

    expectations:
      - { name: "task_id_not_null", expression: "task_id IS NOT NULL", severity: "drop" }

    data_elements:
      - { technical_name: "task_id", business_name: "Task ID", data_type: "BIGINT",
          source: { from_raw: [ { ref: "task_det_wide", column: "task_id" }, { ref: "task_det_long", attribute_key: "task_id" } ] } }
      - { technical_name: "task_type", business_name: "Task Type", data_type: "STRING",
          source: { from_raw: [ { ref: "task_det_wide", column: "task_type" }, { ref: "task_det_long", attribute_key: "task_type" } ] },
          cleansing: { vocabulary: "TASK_TYPE", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/task_type/v1" } }

      # Investigation task specifics
      - { technical_name: "investigation_summary", business_name: "Investigation Summary", data_type: "STRING",
          source: { from_raw: [ { ref: "task_det_wide", column: "investigation_summary" }, { ref: "task_det_long", attribute_key: "investigation_summary" } ] } }
      - { technical_name: "investigation_outcome", business_name: "Investigation Outcome", data_type: "STRING",
          source: { from_raw: [ { ref: "task_det_wide", column: "investigation_outcome" }, { ref: "task_det_long", attribute_key: "investigation_outcome" } ] },
          cleansing: { vocabulary: "INVESTIGATION_OUTCOME", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/investigation_outcome/v1" } }

      # CAPA task specifics
      - { technical_name: "capa_action_type", business_name: "CAPA Action Type", data_type: "STRING",
          source: { from_raw: [ { ref: "task_det_wide", column: "capa_action_type" }, { ref: "task_det_long", attribute_key: "capa_action_type" } ] },
          cleansing: { vocabulary: "CAPA_ACTION_TYPE", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/capa_action_type/v1" } }
      - { technical_name: "effectiveness_result", business_name: "Effectiveness Result", data_type: "STRING",
          source: { from_raw: [ { ref: "task_det_wide", column: "effectiveness_result" }, { ref: "task_det_long", attribute_key: "effectiveness_result" } ] },
          cleansing: { vocabulary: "EFFECTIVENESS_RESULT", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/effectiveness_result/v1" } }

      # Change Control task specifics
      - { technical_name: "approval_route", business_name: "Approval Route", data_type: "STRING",
          source: { from_raw: [ { ref: "task_det_wide", column: "approval_route" }, { ref: "task_det_long", attribute_key: "approval_route" } ] },
          cleansing: { vocabulary: "APPROVAL_ROUTE", goldenmaster_uri: "https://uri.takeda.io/goldenmaster/quality/approval_route/v1" } }
      - { technical_name: "implementation_window_start", business_name: "Implementation Start", data_type: "TIMESTAMP",
          source: { from_raw: [ { ref: "task_det_wide", column: "implementation_window_start" }, { ref: "task_det_long", attribute_key: "implementation_window_start" } ] } }
      - { technical_name: "implementation_window_end", business_name: "Implementation End", data_type: "TIMESTAMP",
          source: { from_raw: [ { ref: "task_det_wide", column: "implementation_window_end" }, { ref: "task_det_long", attribute_key: "implementation_window_end" } ] } }

```

## Data Product DLT runner script

```python

# Databricks Delta Live Tables runner
# Build DLT tables from a YAML data contract (wide/long ingestion, namespace mappings, dual quality)

import json, yaml, re
from functools import partial
from typing import Dict, List, Any

from pyspark.sql import functions as F, Window
from pyspark.sql import DataFrame
import dlt

# ========================
# 0) Load Contract (dbutils/secrets or file)
# ========================
# Option A: paste YAML into a DBFS file and point here:
CONTRACT_PATH = spark.conf.get("pipeline.contract.path", "dbfs:/contracts/quality_events_contract.yaml")

with open(CONTRACT_PATH.replace("dbfs:/", "/dbfs/"), "r", encoding="utf-8") as f:
    CONTRACT: Dict[str, Any] = yaml.safe_load(f)

CORE_SCHEMA   = CONTRACT["namespaces"]["core_schema"]          # e.g. "us_gmsgq_domain_dev.core"
QUALITY_SCHEMA= CONTRACT["namespaces"]["quality_schema"]       # e.g. "us_gmsgq_domain_dev.quality"

RAW_SOURCES   = { src["id"]: src for src in CONTRACT.get("raw_sources", []) }
CONTRACTS     = CONTRACT.get("contracts", [])

# ========================
# 1) Helper functions
# ========================

def normalize(col: str):
    return F.lower(F.trim(F.col(col)))

def precedence(scope_col: str):
    return (F.when(F.col(scope_col)=="RECORD", F.lit(1))
             .when(F.col(scope_col)=="PRODUCT", F.lit(2))
             .when(F.col(scope_col)=="DOMAIN",  F.lit(3))
             .otherwise(F.lit(4)))

def mapping_base(vocabulary: str) -> DataFrame:
    return (spark.table(f"{CORE_SCHEMA}.namespace_mapping")
            .where(F.col("vocabulary")==F.lit(vocabulary))
            .where((F.col("effective_to").isNull()) | (F.col("effective_to")>=F.current_timestamp()))
            .where((F.col("mapping_version").isNull()) | (F.col("mapping_version")==1)))

def choose_mapping(df_norm: DataFrame,
                   pk: str,
                   domain_schema: str,
                   product_name: str,
                   raw_col: str,
                   vcol: str,
                   vocabulary: str,
                   quality_mode: str) -> DataFrame:
    """
    Return mapping candidates resolved by scope/priority/effective_from.
    quality_mode: 'ANY' (MAPPED+VERIFIED) or 'VERIFIED' (strict)
    """
    base = mapping_base(vocabulary)
    if quality_mode == "VERIFIED":
        base = base.where(F.col("quality_level")=="VERIFIED")
    else:
        base = base.where(F.col("quality_level").isin("MAPPED","VERIFIED"))

    exact = base.where(F.coalesce(F.col("is_regex"), F.lit(False))==F.lit(False)) \
      .select("scope_level","domain_schema","product_technical_name","column_name","record_pk",
              "token_normalized","mapped_value","priority","effective_from")

    j_exact = (df_norm.alias("r").join(
        exact.alias("m"),
        (F.col(vcol)==F.col("m.token_normalized")) &
        (
          (F.col("m.scope_level")=="GLOBAL") |
          ((F.col("m.scope_level")=="DOMAIN")  & (F.col("m.domain_schema")==domain_schema) & (F.col("m.column_name")==raw_col)) |
          ((F.col("m.scope_level")=="PRODUCT") & (F.col("m.product_technical_name")==product_name) & (F.col("m.column_name")==raw_col)) |
          ((F.col("m.scope_level")=="RECORD")  & (F.col("m.product_technical_name")==product_name) & (F.col("m.column_name")==raw_col) & (F.col("m.record_pk")==F.col(f"r.{pk}")))
        ),
        "left"
    ).selectExpr(f"r.{pk} as entity_pk","m.scope_level","m.priority","m.effective_from","m.mapped_value"))

    regex = base.where(F.coalesce(F.col("is_regex"), F.lit(False))==F.lit(True)) \
      .select("scope_level","domain_schema","product_technical_name","column_name","record_pk",
              "regex_pattern","regex_flags","mapped_value","priority","effective_from")

    j_regex = (df_norm.alias("r").crossJoin(F.broadcast(regex).alias("m"))
        .where(
          (
            (F.col("m.scope_level")=="GLOBAL") |
            ((F.col("m.scope_level")=="DOMAIN")  & (F.col("m.domain_schema")==domain_schema) & (F.col("m.column_name")==raw_col)) |
            ((F.col("m.scope_level")=="PRODUCT") & (F.col("m.product_technical_name")==product_name) & (F.col("m.column_name")==raw_col)) |
            ((F.col("m.scope_level")=="RECORD")  & (F.col("m.product_technical_name")==product_name) & (F.col("m.column_name")==raw_col) & (F.col("m.record_pk")==F.col(f"r.{pk}")))
          ) &
          (F.col(vcol).rlike(F.col("m.regex_pattern")))
        )
        .selectExpr(f"r.{pk} as entity_pk","m.scope_level","m.priority","m.effective_from","m.mapped_value"))

    candidates = j_exact.unionByName(j_regex, allowMissingColumns=True)
    w = Window.partitionBy("entity_pk").orderBy(precedence("scope_level"),
                                                F.col("priority").desc(),
                                                F.col("effective_from").desc())
    return (candidates.withColumn("rn", F.row_number().over(w))
                      .where(F.col("rn")==1)
                      .select("entity_pk","mapped_value"))

def apply_expectations(df: DataFrame, expectations: List[Dict[str, Any]]):
    """Attach DLT expectations based on severity."""
    if not expectations: return df
    out = df
    for exp in expectations:
        name = exp["name"]
        expr = exp["expression"]
        sev  = exp.get("severity","warn").lower()
        if   sev == "fail":
            out = dlt.expect_or_fail(name, expr)(out)
        elif sev == "drop":
            out = dlt.expect_or_drop(name, expr)(out)
        else:
            out = dlt.expect(name, expr)(out)
    return out

def load_source(src_id: str) -> DataFrame:
    src = RAW_SOURCES[src_id]
    return spark.table(src["fqn"])

def pivot_long(src: Dict[str, Any], df: DataFrame) -> DataFrame:
    lf = src["long_format"]
    idx = lf["index"]
    name_col = lf["name_col"]
    value_col= lf["value_col"]
    return df.groupBy(*[F.col(c) for c in idx]).pivot(name_col).agg(F.first(value_col))

def build_input_frames(ingest: Dict[str, Any]) -> Dict[str, DataFrame]:
    """Return dict with keys: 'wide', 'longwide' (long pivoted), and 'union' preference."""
    sources = ingest.get("sources", [])
    frames = {}
    for s in sources:
        df = load_source(s["ref"])
        src_def = RAW_SOURCES[s["ref"]]
        if src_def["format"] == "long":
            df_w = pivot_long(src_def, df)
            frames.setdefault("longwide", []).append(df_w)
        else:
            frames.setdefault("wide", []).append(df)
    # union per shape
    if "wide" in frames:
        frames["wide"] = frames["wide"][0] if len(frames["wide"])==1 else frames["wide"][0].unionByName(*frames["wide"][1:], allowMissingColumns=True)
    if "longwide" in frames:
        frames["longwide"] = frames["longwide"][0] if len(frames["longwide"])==1 else frames["longwide"][0].unionByName(*frames["longwide"][1:], allowMissingColumns=True)
    return frames

def resolve_from_raw(col_cfg: Dict[str, Any], frames: Dict[str, DataFrame]) -> F.Column:
    """
    col_cfg looks like:
      source:
        from_raw:
          - { ref: "ev_wide", column: "status_name" }
          - { ref: "ev_long", attribute_key: "status_name" }
    We will attempt in provided order; if unavailable, return null.
    """
    raw_defs = col_cfg.get("source",{}).get("from_raw", [])
    # We assume caller has already joined/aliased frames into a single df with the union/preferred shape.
    # Here we only return the final column expression name to select from that df.
    # By convention, runner will materialize fields from the chosen "base_df".
    # So we just pick the first available column name.
    for item in raw_defs:
        colname = item.get("column") or item.get("attribute_key")
        if colname:
            return F.col(colname)
    # fallback: null
    return F.lit(None)

def with_dual_quality_for_vocab(df: DataFrame,
                                pk: str,
                                domain_schema: str,
                                product_name: str,
                                raw_expr: F.Column,
                                raw_alias: str,
                                technical_name: str,
                                vocabulary: str,
                                dtype: str) -> DataFrame:
    """
    Adds: X_raw, X, X_parse_status, X_verified, X_verified_parse_status
    """
    vcol = f"__norm__{raw_alias}"
    df = df.withColumn(f"{technical_name}_raw", raw_expr)
    df = df.withColumn(vcol, normalize(f"{technical_name}_raw"))

    # Build a minimal norm df for mapping joins
    norm = df.select(F.col(pk).alias("__pk"), F.col(vcol).alias("__v"))
    # ANY quality
    m_any = choose_mapping(norm, "__pk", domain_schema, product_name, raw_alias, "__v", vocabulary, "ANY") \
              .withColumnRenamed("entity_pk","__pk").withColumnRenamed("mapped_value","__mv_any")
    # VERIFIED only
    m_ver = choose_mapping(norm, "__pk", domain_schema, product_name, raw_alias, "__v", vocabulary, "VERIFIED") \
              .withColumnRenamed("entity_pk","__pk").withColumnRenamed("mapped_value","__mv_ver")

    df = df.join(F.broadcast(m_any),  df[pk]==m_any["__pk"], "left").drop("__pk")
    df = df.join(F.broadcast(m_ver),  df[pk]==m_ver["__pk"], "left").drop("__pk")

    # Cast boolean or keep string
    if vocabulary == "BOOLEAN" or dtype.lower()=="boolean":
        mapped      = F.when(F.col(vcol).isNull() | (F.col(vcol)==""), F.lit(None)) \
                       .when(F.col("__mv_any")=="TRUE",  F.lit(True)) \
                       .when(F.col("__mv_any")=="FALSE", F.lit(False)) \
                       .otherwise(F.lit(None))
        mapped_ver  = F.when(F.col(vcol).isNull() | (F.col(vcol)==""), F.lit(None)) \
                       .when(F.col("__mv_ver")=="TRUE",  F.lit(True)) \
                       .when(F.col("__mv_ver")=="FALSE", F.lit(False)) \
                       .otherwise(F.lit(None))
        df = df.withColumn(technical_name, mapped.cast("boolean"))
        df = df.withColumn(f"{technical_name}_verified", mapped_ver.cast("boolean"))
    else:
        df = df.withColumn(technical_name, F.when(F.col("__mv_any").isNotNull(), F.col("__mv_any")))
        df = df.withColumn(f"{technical_name}_verified", F.when(F.col("__mv_ver").isNotNull(), F.col("__mv_ver")))

    df = df.withColumn(f"{technical_name}_parse_status",
          F.when(F.col(f"{technical_name}_raw").isNull() | (F.col(f"{technical_name}_raw")==""), "EMPTY")
           .when(F.col(technical_name).isNotNull(), "PARSED_OK")
           .otherwise("UNPARSABLE"))

    df = df.withColumn(f"{technical_name}_verified_parse_status",
          F.when(F.col(f"{technical_name}_raw").isNull() | (F.col(f"{technical_name}_raw")==""), "EMPTY")
           .when(F.col(f"{technical_name}_verified").isNotNull(), "PARSED_OK")
           .otherwise("UNPARSABLE"))

    return df.drop(vcol, "__mv_any", "__mv_ver")

def apply_element(df: DataFrame,
                  pk: str,
                  domain_schema: str,
                  product_name: str,
                  element: Dict[str, Any]) -> DataFrame:
    tname = element["technical_name"]
    dtype = element["data_type"]
    cleansing = element.get("cleansing", {})
    vocabulary = cleansing.get("vocabulary")
    raw_expr = resolve_from_raw(element, {})  # expression (will read from base df columns)
    raw_alias = tname + "_raw_src"

    if vocabulary:
        return with_dual_quality_for_vocab(df, pk, domain_schema, product_name,
                                           raw_expr.alias(raw_alias), raw_alias, tname, vocabulary, dtype)
    else:
        # passthrough + statuses
        df = df.withColumn(f"{tname}_raw", raw_expr)
        df = df.withColumn(tname, F.col(f"{tname}_raw").cast(dtype.lower()))
        df = df.withColumn(f"{tname}_parse_status",
                           F.when(F.col(f"{tname}_raw").isNull() | (F.col(f"{tname}_raw")==""), "EMPTY")
                            .otherwise("PARSED_OK"))
        df = df.withColumn(f"{tname}_verified", F.col(tname))
        df = df.withColumn(f"{tname}_verified_parse_status", F.col(f"{tname}_parse_status"))
        return df

def pick_base_frame(ingest_cfg: Dict[str, Any], frames: Dict[str, DataFrame]) -> DataFrame:
    pref = (ingest_cfg.get("preferred_shape") or "wide").lower()
    # Choose: wide first, else longwide; if both, union with wide precedence (wide columns will shadow)
    if pref == "wide":
        if "wide" in frames: return frames["wide"]
        if "longwide" in frames: return frames["longwide"]
    else:
        if "longwide" in frames: return frames["longwide"]
        if "wide" in frames: return frames["wide"]
    # empty fallback (no sources): create dummy df
    return spark.createDataFrame([], schema = "dummy string")

def resolve_pk(contract_item: Dict[str, Any]) -> str:
    pk = contract_item.get("primary_key", [])
    if not pk:
        raise ValueError(f"Primary key not set for entity {contract_item['entity']}")
    # For compound PKs, we’ll use the first column as entity id for mapping joins (record-level scope).
    return pk[0]

# ========================
# 2) Dynamic DLT table builders
# ========================

def build_product_table(contract_item: Dict[str, Any]):
    """
    Creates a DLT table with the final schema and expectations.
    Uses closures so each product gets a unique function + table name.
    """
    entity   = contract_item["entity"]
    schema   = contract_item["schema"]
    table    = contract_item["table_name"]
    version  = contract_item.get("version","v1.0")
    latest   = contract_item.get("latest", True)
    pk_col   = resolve_pk(contract_item)
    ingest   = contract_item.get("ingest", {})
    elements = contract_item.get("data_elements", [])
    expectations = contract_item.get("expectations", [])

    tbl_fqn = f"{QUALITY_SCHEMA}.{table}" if schema == "quality" else f"{schema}.{table}"

    # ---------- define the DLT table dynamically ----------
    @dlt.table(
        name = tbl_fqn,
        comment = f"{entity} ({version}) — autogenerated by contract runner; latest={latest}"
    )
    def _dynamic_builder_for_table() -> DataFrame:
        frames = build_input_frames(ingest)
        base_df = pick_base_frame(ingest, frames)

        # normalize all possible raw fields: create normalized helpers for columns used by mappings
        # (We do per-element below as we need their raw aliases anyway.)

        # Apply each element
        df = base_df
        for e in elements:
            df = apply_element(df, pk_col, CONTRACT["namespaces"]["quality_schema"], entity, e)

        # Keep only PK + ordered element outputs
        select_cols = [F.col(pk_col)]
        for e in elements:
            t = e["technical_name"]
            select_cols += [
                F.col(f"{t}_raw").alias(f"{t}_raw"),
                F.col(t).alias(t),
                F.col(f"{t}_parse_status").alias(f"{t}_parse_status"),
                F.col(f"{t}_verified").alias(f"{t}_verified"),
                F.col(f"{t}_verified_parse_status").alias(f"{t}_verified_parse_status"),
            ]

        out = df.select(*select_cols) \
                .withColumn("data_product_version", F.lit(version)) \
                .withColumn("_ingestion_ts", F.current_timestamp())

        # Attach DLT expectations
        out = apply_expectations(out, expectations)
        return out

# Register a DLT table for each product in the contract
for item in CONTRACTS:
    build_product_table(item)


```