# Conversation Record — Cenovus AI Dev Role Assessment & Self-Upgrade Plan

**Date:** [save date]
**Purpose:** Fit assessment against Cenovus AI Development Engineer role, candid gap analysis, and a phased plan to close gaps before targeting this (or equivalent) seat in the future.

---

## 1. Source Profile

**Current title / identity:** Performance Architect, 21+ years.

**Key skills (as listed):**
Performance Engineering & Optimisation · AI / Agentic AI (LangChain, LangFlow, CrewAI, TensorFlow, Keras, PyTorch) · Cloud (AWS, Azure, IBM Cloud, OpenShift, K8s) · Full-Stack (Java, Python, JS, Spring Boot, React, MongoDB) · DevOps / CI/CD (Docker, Git, Maven, Dynatrace, EFK, Jaeger, K3/K8s, OCP) · Test Automation & Performance (LoadRunner, NeoLoad, JMeter, K6, UFT, Selenium, Cucumber, JUnit) · Enterprise Systems (SAP ECC/S/4HANA, SolMan, ChaRM)

**Credentials:** IBM Certified Expert, PMP.

---

## 2. Target Role (Cenovus AI Development Engineer)

**Mandatory:** Python, SQL.
**Core stack:** Full-stack web (Django / Rails / Laravel archetype), REST APIs, ORM, relational DBs (PostgreSQL, PGVector, Azure PostgreSQL, AWS RDS), React or templated front-end, Docker, GitLab CI/CD, Azure (AI Foundry, AI Search), Databricks / data lakes.
**AI layer:** LLM integration, multi-agent (LangChain/LangGraph, Agno, MCP), RAG, LLM evaluation (DeepEval, LLM-as-a-Judge) — **inside a working application, not standalone**.
**Orchestration:** Prefect, Dagster, notebooks, custom.
**Quality bar:** Automated testing, LLM eval as CI gate, code review, production monitoring.
**Meta:** Strong software-engineering fundamentals over framework familiarity. Adaptivity. Responsible use of agentic coding tools (Copilot, Claude Code).

**What the client explicitly excludes as this role:**
- Data engineering (ETL/ELT, data-warehouse modelling)
- Data science / ML (model training, statistical analysis, notebook workloads)
- Architecture-advisory / configuration-management
- Analytics / reporting

---

## 3. 100-Word "About Me" (draft, for future use once profile is upgraded)

> Software engineer and performance architect with 21+ years in enterprise application development, AI-driven solution design, and cloud-native architecture. Core competency in Python, SQL, full-stack web development (React, Spring Boot, REST APIs, PostgreSQL), and production LLM integration including multi-agent workflows (LangChain, LangGraph, CrewAI) and retrieval-augmented generation. Containerised service deployment (Docker, Kubernetes) across Azure, AWS, and IBM Cloud, with data integration spanning SAP, Oracle, and data-lake environments. Strong software engineering fundamentals: automated testing, LLM evaluation, CI/CD quality gates. Transferable engineering principles and architectural adaptivity across evolving platforms and product domains, without compromise on code quality or delivery standards. IBM Certified Expert. PMP.

*Note: This draft is written against the current profile. It will need restructuring once Phase 1–3 (below) are complete, so the full-stack application work leads and performance architecture becomes supporting depth.*

---

## 4. Candid Fit Verdict

**Not a strong fit as the profile stands.**

| Alignment | Status |
|---|---|
| Python, AI/agent frameworks, cloud, Docker/K8s, enterprise data integration, testing discipline | ✓ Present |
| Full-stack **Python** web application built and owned end-to-end | ✗ Not demonstrated as a primary deliverable |
| ORM, schema design, migrations, transactions (as daily engineering work) | ✗ Not in profile |
| Auth/authz, sessions, caching, background jobs, production day-2 ownership of a web app | ✗ Not in profile |
| AI as a feature **inside a shipped app** (vs. standalone pipeline / ML exercise) | ✗ Current framing is AI-as-subject, not AI-as-feature |
| LLM evaluation in CI (DeepEval, LLM-as-a-Judge) | ✗ Not in profile |
| SQL as a named, primary application-builder skill | △ Implied by SAP/Oracle, not demonstrated in app context |
| Django / Rails / Laravel (or equivalent Python web framework) | ✗ Not in profile |

**Core issue:** The client wants the *application builder* who ships and owns a full-stack product. The profile signals the *performance architect* who tests, optimises, and advises. Both are real. The second is not the seat they are filling.

**Decision:** Do not force-fit now. Close the gaps, then re-engage.

---

## 5. Gap-Closure Plan

### Phase 1 — Python Full-Stack Foundation (Weeks 1–6)

**Objective:** Build, deploy, and operate a working full-stack web application in Python.

- **Framework:** Django (safest mapping to client reference) or FastAPI. Commit to one.
- **Product (pick one concrete example):**
  - Document Q&A system: upload → ingestion → vector search → chat UI → auth → admin → audit log
  - Internal ops dashboard: PostgreSQL schema → REST API → React front-end → RBAC → background jobs → caching
- **Must exercise, explicitly:**
  - Schema design + migrations (Django migrations / Alembic)
  - ORM queries, query optimisation, transactions, N+1 fixes
  - RESTful API design (resource modelling, HTTP semantics, pagination, filtering)
  - Auth/authz (token, role-based, session)
  - Input / API / DB validation
  - Caching (Redis or in-app)
  - Background jobs (Celery / Dramatiq)
  - Error handling + structured logging
  - Front-end (Django templates + HTMX, or React SPA)
- **Deploy:** Docker → cloud VPS or Azure. Git → CI/CD (GitHub Actions or GitLab). Health endpoint + basic monitoring.
- **Run it ≥ 4 weeks.** Change schema. Fix a bug. Add a feature. Hit a concurrency issue. This is the day-2 ownership evidence.
- **Deliverable:** Live running app. GitHub repo with code, migrations, tests, Dockerfile, CI config, README with architecture diagram.

### Phase 2 — AI Layer Integrated Into the App (Weeks 7–12)

**Objective:** Add a real AI feature **inside** the Phase 1 application. Not a standalone script.

- **RAG pipeline in-app:**
  - Ingestion → chunking → embedding → vector store (PGVector or Azure AI Search)
  - `/api/query` endpoint: question → retrieval → LLM → sourced answer
  - Chat / Q&A UI in the front-end
  - Handle: concurrency, rate-limiting, context window, fallback
- **Multi-agent workflow (strong plus):**
  - 2–3 agents (retrieval → synthesis → validation) via LangGraph or CrewAI
  - Exposed through the API for observability
- **LLM evaluation in CI:**
  - Golden Q&A dataset (50–100 cases)
  - DeepEval or LLM-as-a-Judge in the pipeline
  - Score threshold = build gate
  - Score tracking over time
- **Azure specifics (for Cenovus / equivalent):**
  - LLM via Azure AI Foundry / Azure OpenAI
  - Vector store via Azure AI Search
  - Deploy to AKS or App Service
- **Deliverable:** Same running app, now with AI feature in the UI. Eval suite in CI. Score history.

### Phase 3 — Hardening & Depth (Weeks 13–18)

- **Concurrency & performance:** Load-test the AI endpoint (JMeter / K6 — leverage existing strength). Tune: pooling, query plans, cache hit-rate, job throughput.
- **Security:** OWASP on the API. Prompt-injection sanitisation. Secrets management. Rate-limiting.
- **Observability:** OpenTelemetry or equivalent. Error dashboards. Apply Dynatrace / Jaeger experience.
- **Code quality:** Full pytest suite. Type hints. Ruff / mypy. Self-review PRs. One meaningful refactor.
- **Architecture doc:** One page. System diagram. Data flow. Failure modes. Scale path. Rollback strategy for a bad model / prompt change.
- **Deliverable:** A project you can describe in an interview as *"I designed, built, deployed, and am operating this application."*

---

## 6. "Ready to Apply" Checklist

All must be checkable without hedging:

- [ ] Walk through a full-stack Python web app you built, that is running (prod or maintained staging)
- [ ] Show the DB schema, migrations, ORM queries; explain optimisation decisions
- [ ] Demo REST API, auth flow, and front-end as one integrated product
- [ ] Show the AI feature in the UI; trace request through ingestion → retrieval → LLM → response
- [ ] Show the eval suite in CI and a score history
- [ ] Describe a production issue you diagnosed and fixed (bad query, race condition, cache miss, model output regression)
- [ ] Talk about caching, background jobs, concurrency, error handling as things **implemented**, not read about
- [ ] Name the Python web framework, ORM, and vector store you used — and explain why

When all are checked: **restructure the CV** (full-stack app work leads; performance architecture becomes depth; AI is a feature in the product, not a standalone line) and **re-engage** the target role or equivalent.

---

## 7. What NOT to Do

- Pad the current CV to force-fit this role.
- List Django, SQLAlchemy, Celery, or FastAPI because of documentation reading. Client bar: *"clearly demonstrated, not just listed."*
- Frame performance architecture as full-stack application development.
- Rush Phase 1. Six weeks of real engineering time > weekend demo.
- Present the AI work as a subject. In the target role, AI is a **feature layer** on a product the engineer built.

---

## 8. Interview Prep (for when the profile is upgraded)

**Key technical areas to be ready on:**

| Area | What to demonstrate |
|---|---|
| Python + SQL | Schema design, ORM, migrations, query plans, transactions — in the context of the app you built |
| RAG / Multi-agent | Design decisions: chunking, retrieval strategy, agent routing, context management — inside the app |
| LLM evaluation | Golden dataset, DeepEval / LLM-as-a-Judge in CI, score tracking, regression gating |
| Full-stack ownership | Auth, caching, background jobs, concurrency, error handling — as features you implemented |
| Cloud + Deploy | Docker → AKS / App Service, GitLab CI/CD, monitoring, secrets, rollback |
| Data integration | SAP / Oracle / data-lake → normalised PostgreSQL, anti-corruption layer, data-quality validation |
| Agentic coding tools | Copilot / Claude Code usage + the review-and-verify discipline around them |

**Top scenarios to rehearse:**
1. Design a RAG-backed internal Q&A product end-to-end (architecture walkthrough).
2. "Model output is degrading — what do you do?" (diagnostic path, eval regression, retrieval-layer check, post-mortem).
3. "You inherit a codebase with no tests, a 400-line function, a sprint deadline. What first?" (behavioural + engineering judgement).

**Behavioural angles:**
- Adopting a new tech under deadline → frame as *transferable principles*, not "I learned it."
- Disagreement with a teammate → listen, rationale with data, compromise or time-boxed spike, move on.
- Ambiguity in requirements → thin vertical slice, validate with stakeholder, iterate.
- Where AI dev is going in 12–18 months → standardisation (MCP, multi-agent), differentiation in eval + data quality + integration, not the model call.

**Questions to ask the interviewer:**
1. What does LLM eval / regression testing look like today, and where is it heading?
2. How is the team split between greenfield and maintenance?
3. Current state of the data-integration layer — is there a standard ingestion pattern?
4. How is model / prompt versioning and rollout handled (canary, A/B)?
5. Does "done" include the eval suite, or is it separate?
6. How are agentic coding tools used, and what guardrails exist?

**Gap-handling rule:** Never "I haven't done that." → *"I haven't used that specific product; I've built the same capability with [X]. Here's how I'd approach it."*

---

*End of record. Revisit at Phase 2 completion for CV restructure + targeted interview dry-run.*