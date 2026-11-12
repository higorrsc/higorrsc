# Hi, I'm Higor Rodrigues 👋

**Software Engineer | Backend Engineering | Python | AI Engineering | Software Architecture**

I design and build backend systems that combine **domain-driven software architecture, data engineering, distributed systems, and artificial intelligence**.

My focus is building reliable business applications, integrating AI capabilities into conventional software systems, and exploring how AI-assisted engineering can improve the software development lifecycle.

My portfolio showcases practical implementations of these concepts through original projects, emphasizing architectural design, explicit business rules, automated testing, and technical documentation.

---

# 🚀 Portfolio

My portfolio consists of original projects designed to explore different software engineering challenges, from statistical analysis and complex domain modeling to AI-powered applications and financial systems.

The projects emphasize:

- Domain-Driven Design (DDD)
- Clean Architecture and SOLID
- Explicit business rules and domain invariants
- API and database design
- Automated testing
- Infrastructure and containerization
- Technical documentation and architecture decisions

The objective is not simply to build applications, but to demonstrate how software is designed, modeled, implemented, tested, and documented.

## 1. Supply Chain Anomaly Management

**Statistical Analysis · Domain Services · REST API · Operational Analytics**

An API focused on processing inventory movements and identifying abnormal stock behavior.

The system analyzes historical patterns and applies statistical concepts such as standard deviation to identify anomalies and generate alerts for unexpected movements.

A Streamlit application consumes the API and provides an operational dashboard for visualizing detected anomalies.

**Key concepts and technologies:**

- Domain-Driven Design and Domain Services
- Statistical anomaly detection
- Historical data analysis
- REST API and Pydantic
- PostgreSQL
- Automated testing
- Docker and Streamlit

**Architecture**

```text
       Streamlit Dashboard
               │
               ▼
           REST API
               │
               ▼
           Use Cases
               │
               ▼
        Domain Services
               │
        Anomaly Analysis
               │
               ▼
           PostgreSQL
```

The architecture separates business rules from infrastructure and API concerns, allowing anomaly detection logic to be tested independently.

👉 [View repository](https://github.com/higorrsc/supply-chain-anomaly-management)

---

## 2. Personnel Competency Analysis

**Python · Django · Clean Architecture · DDD · CQRS**

A personnel competency analytics and career progression system designed to model complex domain relationships, lifecycle rules, and competency evaluation processes.

The domain models relationships between:

- Collaborators and competency paths.
- Path enrollments with single-active-path invariants.
- Competency paths, levels, and weighted requirements.
- Periodic evaluations with explicit lifecycle transitions.
- Competency measurements using a proficiency scale.

Django is used as an outer framework adapter, providing administrative interfaces, API endpoints, and relational persistence.

The core domain and business rules remain independent of Django.

**Architectural highlights:**

- Framework-independent domain logic.
- Explicit Command and Query Use Cases.
- CQRS with dedicated Read Model Ports.
- Domain Services for competency gap analysis and promotion eligibility.
- SQL Views using window functions and aggregations for temporal analysis.
- Explicit dependency injection and composition root.
- Database constraints and transaction boundaries.

**Technology stack:**

- Python 3.15 and `uv`
- Django 6 and Django REST Framework
- Pydantic v2
- PostgreSQL
- Pytest
- Ruff and Pyrefly
- GitHub Actions

**Testing and quality:**

- 664 automated tests covering unit, integration, API, and E2E scenarios.
- 98% test coverage.
- Static analysis and CI quality gates.

**Architectural overview**

```text
┌─────────────────────────────────────────────┐
│          Presentation & Infrastructure      │
│                                             │
│   DRF API · Django Admin · Django ORM       │
│             PostgreSQL / SQL Views          │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│                 Application                 │
│                                             │
│       Command & Query Use Cases             │
│          Pydantic DTOs · Ports              │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│             Domain (Pure Python)            │
│                                             │
│     Aggregates · Value Objects              │
│     Invariants · Domain Services            │
└─────────────────────────────────────────────┘
```

The main architectural objective is to demonstrate that adopting a full-featured framework like Django does not require coupling business rules to the framework itself.

👉 [View repository](https://github.com/higorrsc/competency-analytics)

---

## 3. Strategic Indicators — SDD & AI

**Spec-Driven Development · AI Agents · DDD · Clean Architecture · BDD**

An enterprise-oriented financial intelligence platform built with Python and AI-assisted software engineering, designed to transform corporate budget and cost allocation data into actionable strategic insights.

The application combines deterministic financial calculations, anomaly detection, scenario simulations, and multi-provider AI agents to generate executive-level insights, recommendations, and strategic indicators.

### Core capabilities

- **Financial Governance:** Hierarchical cost center management and budget consolidation.
- **Cost Allocation:** Exact-penny financial allocation using the Largest Remainder Method.
- **Budget Intelligence:** Planned vs. Actual analysis, execution rates, and threshold-based alerts.
- **What-If Simulations:** Scenario analysis for supplier inflation and allocation changes.
- **Anomaly Detection:** Identification of unusual allocation patterns and potential budget dumping.
- **AI-Powered Insights:** Executive summaries and actionable recommendations using Pydantic AI, with support for Ollama, Google Gemini, and OpenAI.
- **Executive Reporting:** Structured PDF reports generated from financial intelligence.

### Specification-Driven Development

The development process follows a specification-first approach using **OpenSpec**.

Business capabilities, domain rules, and acceptance criteria are defined before implementation. Specifications serve as the reference for both development and validation.

The workflow establishes traceability between:

- Business requirements and domain rules.
- Living capability specifications.
- Change proposals and implementation artifacts.
- API contracts and Pydantic schemas.
- Acceptance criteria and automated tests.

**Development workflow**

```text
       Business Requirements
                │
                ▼
         OpenSpec Proposals
                │
                ▼
       Living Specifications
                │
                ▼
       AI-Assisted Engineering
                │
                ▼
       Clean Architecture
                │
                ▼
        Implementation
                │
                ▼
        Automated Tests
                │
         ┌──────┴──────┐
         │             │
        PASS          FAIL
         │             │
         ▼             ▼
      Validate     Failure Analysis
         │             │
         ▼             ▼
       Deliver     Refinement Cycle
                       │
                       └──► Tests
```

### Architecture and engineering

The application is organized around Domain-Driven Design and Clean Architecture, with independently organized bounded contexts:

- `budgeting` — Cost centers and budget targets.
- `allocation` — Suppliers, contracts, measurements, and cost allocation.
- `indicators` — Budget variance calculations and scenario simulations.
- `intelligence` — Anomaly detection and AI-powered insights.
- `shared` — Cross-cutting domain and infrastructure components.

Engineering principles include:

- SOLID and Dependency Inversion.
- Framework-independent domain logic.
- Repository and service abstractions using Python Protocols.
- Explicit use cases and dependency injection.
- Asynchronous persistence with SQLAlchemy.
- Multi-provider AI adapters through abstraction ports.
- Deterministic test doubles for external dependencies.

### AI-Assisted Software Engineering

AI coding agents are integrated into a development workflow guided by formal specifications rather than unrestricted code generation.

The objective is to use AI as an engineering accelerator while preserving architectural consistency, explicit business rules, and implementation quality.

### Testing and validation

- Unit tests for domain rules, calculations, entities, and use cases.
- Integration tests for asynchronous persistence and repositories.
- API tests for HTTP contracts and endpoint behavior.
- BDD with executable Gherkin scenarios using `pytest-bdd`.
- Static analysis with Ruff and Pyrefly.
- Specification validation with OpenSpec.

External AI dependencies can be replaced with deterministic test doubles, allowing business behavior to be validated without relying on external LLM services.

**Technology stack:**

`Python` · `FastAPI` · `Pydantic` · `Pydantic AI` · `SQLAlchemy` · `PostgreSQL` · `Alembic` · `OpenAPI` · `OpenSpec` · `pytest` · `pytest-bdd` · `Docker` · `uv`

The central engineering experiment is exploring how formal specifications, domain-driven design, automated testing, and AI-assisted development can work together to build reliable software.

👉 [View repository](https://github.com/higorrsc/strategic-indicators-ai)

---

## 4. Contract Measurement & Cost Allocation

<sub>PLANNED PROJECT · DEVELOPMENT QUEUE</sub>

**Financial Modeling · Domain Modeling · Data Architecture · Enterprise Systems**

A planned project focused on contract measurement management and financial cost allocation across hierarchical organizational structures.

The proposed domain addresses challenges such as:

- Contract and supplier management.
- Measurement bulletin lifecycle and validation.
- Hierarchical cost center structures.
- Financial distribution across organizational units.
- Business rules governing measurement and approval workflows.
- Integration with corporate data sources.

The project is intended to explore complex domain modeling and financial data processing, with particular attention to maintaining consistency between contract measurements, organizational structures, and financial allocations.

Its architectural and technology decisions will be defined as the project moves into specification and development.

This project is currently in the development queue and is not yet implemented.

---

# 🧠 Engineering Principles

Across my projects, I focus on a consistent set of engineering principles.

### Domain First

Business rules should be explicit, understandable, and independent of technical implementation details.

### Separation of Concerns

Infrastructure, frameworks, application logic, and domain rules should not become unnecessarily coupled.

### Testability

Important business behavior should be executable and testable independently of infrastructure.

### Explicit Architecture

Architectural decisions should be documented rather than hidden inside implementation details.

### Documentation as a Deliverable

Documentation is part of the software, not an afterthought.

My projects aim to provide setup instructions, architecture diagrams, API documentation, test instructions, technical decisions, trade-offs, and practical examples.

---

# 🏛️ Software Architecture

I'm particularly interested in architectures that allow business rules to remain independent from frameworks and infrastructure.

Architectural approaches and patterns I work with include:

- Domain-Driven Design (DDD)
- Clean Architecture
- Hexagonal Architecture
- SOLID
- Dependency Inversion
- Repository Pattern
- Unit of Work
- Value Objects
- Entities and Aggregates
- Domain Services
- Use Cases
- CQRS

A recurring architectural model in my projects is:

```text
       Presentation
        API / Admin
             │
             ▼
        Application
          Use Cases
             │
             ▼
           Domain
       Business Rules
       Entities
       Value Objects
       Domain Services
             │
             ▼
       Infrastructure
       Database
       External APIs
       Messaging
```

Architecture is treated as a tool for managing complexity rather than a fixed template. Its implementation varies according to the problem and the needs of the domain.

---

# 🐍 Backend Engineering

Python is my primary language for backend development.

**Core ecosystem:**

- Python
- FastAPI
- Django
- Django REST Framework
- SQLAlchemy
- Pydantic
- Pytest
- Celery
- `uv`

**Application areas:**

- REST APIs and business applications.
- Data processing and ETL.
- Automation.
- Database integration.
- Distributed systems.
- AI-powered applications.
- Testing and software quality.

---

# 🤖 Artificial Intelligence & AI Engineering

I'm focused on practical applications of artificial intelligence in software engineering and business systems.

**Areas of interest and development:**

- LLM applications.
- AI agents and agentic workflows.
- Retrieval-Augmented Generation (RAG).
- Embeddings and semantic search.
- Vector databases and `pgvector`.
- Prompt engineering.
- Multi-provider LLM integration.
- Spec-Driven Development.
- AI-assisted software development.

My main interest is combining AI capabilities with conventional software engineering:

```text
          Artificial Intelligence
                    +
              Domain Modeling
                    +
           Software Architecture
                    +
               APIs & Data
                    +
            Automated Testing
```

The goal is to build AI-enabled systems that remain maintainable, testable, observable, and aligned with business requirements.

---

# 🗄️ Databases & Data Engineering

I have experience working with relational databases and complex SQL-based systems.

**Technologies and concepts:**

- PostgreSQL
- SQL Server
- SQLite
- SQL
- Common Table Expressions (CTEs)
- Database Views
- Stored Procedures
- Window Functions
- Database modeling and migrations
- Hierarchical data
- Vector search

I'm particularly interested in understanding when database-side processing is appropriate and when business logic should remain in the application or domain layer.

---

# 🐳 Infrastructure & DevOps

Infrastructure and automation are important parts of building and operating reliable software systems.

**Tools and technologies:**

- Docker and Docker Compose
- AWS
- Terraform
- CI/CD and GitHub Actions
- Kubernetes
- Ansible
- GitOps
- API Gateways
- RabbitMQ and Apache Kafka
- gRPC
- OpenTelemetry
- Prometheus
- Istio

My technical interests include infrastructure as code, container orchestration, distributed communication, observability, and automated delivery pipelines.

---

# 🧪 Testing & Software Quality

Testing is treated as part of the design process rather than only a final verification step.

Practices and tools include:

- Unit testing.
- Integration testing.
- API testing.
- Domain testing.
- Acceptance testing.
- Behavior-Driven Development (BDD).
- Contract testing.
- Pytest.
- Static analysis.
- CI quality gates.

For AI-assisted development, automated tests become particularly important because they provide an objective feedback mechanism for generated code.

---

# 🎓 Education & Technical Training

## MBA — Software Engineering with AI

Currently pursuing an MBA focused on Software Engineering and Artificial Intelligence.

Areas of study include:

- Artificial Intelligence and LLMs.
- Retrieval-Augmented Generation (RAG).
- Prompt Engineering.
- Software Architecture.
- System Design.
- AI-assisted development.
- Software Engineering.

Repositories prefixed with `fc-mba-*` contain projects, challenges, and experiments related to this training.

## Full Cycle 3.0

Completed the Full Cycle 3.0 Developer Training, with practical projects and studies involving:

- Domain-Driven Design.
- Clean and Hexagonal Architecture.
- Microservices and Event-Driven Architecture.
- GraphQL and gRPC.
- Apache Kafka and RabbitMQ.
- Kubernetes and Istio.
- API Gateway.
- Terraform and Ansible.
- GitOps and CI/CD.
- OpenTelemetry and Prometheus.

Repositories prefixed with `fc-hrsc-*` document projects and exercises from this training.

## Full-stack Python Development

Completed a Full-stack Python Developer training covering:

- Python and Django.
- Django REST Framework.
- JavaScript and TypeScript.
- React and Vue.
- HTML and CSS.
- REST APIs.
- SQL.

Repositories prefixed with `ebac-*` contain projects and exercises from this training.

---

# 📚 Learning Repositories

My GitHub also contains repositories created during courses, training programs, experiments, and technical studies.

They represent different stages of my learning journey.

The portfolio projects above are the primary representation of my current technical direction, while the learning repositories provide additional context about the technologies and concepts I have studied.

---

# 📈 Technical Direction

My current technical direction can be summarized as:

```text
             Backend Engineering
                     │
          ┌──────────┼──────────┐
          │          │          │
          ▼          ▼          ▼
      Software    Domain      Data &
     Architecture Modeling   Databases
          │          │          │
          └──────────┼──────────┘
                     │
                     ▼
            Distributed Systems
                     │
                     ▼
            Artificial Intelligence
                     │
               ┌─────┼─────┐
               │     │     │
               ▼     ▼     ▼
              LLMs  RAG  AI Agents
                     │
                     ▼
             AI-Assisted Engineering
```

My goal is to continue developing software systems that combine strong engineering foundations with practical applications of artificial intelligence.

---

# 📫 Contact

I'm always interested in connecting with people working on software engineering, backend development, architecture, distributed systems, data, and AI applications.

- **LinkedIn:** [Higor Rodrigues](https://www.linkedin.com/in/higorrsc/)
- **GitHub:** [@higorrsc](https://github.com/higorrsc)

---

> Build software. Model the problem. Test the behavior. Document the decisions.
