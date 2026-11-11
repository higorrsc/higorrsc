# Hi, I'm Higor Rodrigues 👋

**Software Engineer | Python | Backend | Software Architecture | AI**

I build backend systems focused on **business domains, software architecture, data processing, distributed systems, and artificial intelligence**.

My portfolio is centered around four original projects designed to explore different software engineering challenges — from statistical anomaly detection and complex domain modeling to AI-assisted development and financial data processing.

---

## 🚀 Portfolio

My main portfolio consists of four original projects.

Each project is developed with a focus on:

- Domain modeling
- Clean Architecture
- SOLID
- Automated testing
- API design
- Database modeling
- Docker
- Technical documentation
- Architecture diagrams
- Explicit technical decisions

The goal is not simply to build applications, but to demonstrate **how software is designed, modeled, implemented, tested, and documented**.

---

## 1. Supply Chain Anomaly Management

**Statistical analysis · Domain Services · REST API · Operational Analytics**

[![Repository](https://img.shields.io/badge/GitHub-Repository-181717?logo=github)](https://github.com/higorrsc/supply-chain-anomaly-management)

An API focused on processing **inventory movements** and identifying abnormal stock behavior.

The system analyzes historical patterns and uses statistical concepts such as **standard deviation** to identify anomalies, generating alerts for unexpected movements.

A Streamlit application consumes the API and provides an operational dashboard for visualizing the detected anomalies.

### Main concepts

- Domain-Driven Design
- Domain Services
- Statistical anomaly detection
- Historical data analysis
- REST API
- Pydantic
- Automated testing
- PostgreSQL
- Docker
- Streamlit

### Architecture

The project separates business rules from infrastructure and API concerns, allowing the anomaly detection logic to be tested independently.

```text
                    ┌──────────────────┐
                    │    Streamlit     │
                    │    Dashboard     │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     REST API     │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    Use Cases     │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │  Domain Services │
                    │                  │
                    │ Anomaly Analysis │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    PostgreSQL    │
                    └──────────────────┘
```

👉 **[View repository](https://github.com/higorrsc/supply-chain-anomaly-management)**

---

## 2. Personnel Competency Analysis

**Django · Clean Architecture · Domain-Driven Design · CQRS · Complex Relationships**

[![Repository](https://img.shields.io/badge/GitHub-Repository-181717?logo=github)](https://github.com/higorrsc/competency-analytics)

A personnel competency analytics and career progression system designed to model complex domain relationships and lifecycle rules between:

```text
Collaborator
      │
      ├──► Path Enrollments (Single Active Path Invariant)
      │         │
      │         ▼
      │    Competency Paths & Levels (Core / Complementary Weights)
      │
      └──► Periodic Evaluations (Draft → Submitted → Accepted / Contested)
                │
                ▼
          Competency Measurements (Proficiency Scale 1–5)
```

The project leverages Django where its framework capabilities provide high value as an outer adapter:

- **Django Admin** (customized administrative interfaces, inlines, and domain-driven actions)
- **Django REST Framework** (RESTful API controllers, serializers, and OpenAPI/Swagger documentation)
- **Django ORM & Migrations** (relational persistence, constraints, and transaction boundaries)

At the same time, **the core domain and business rules remain 100% independent from Django**.

For example:

- **Competency Gap Analysis & Promotion Eligibility** are implemented through pure, framework-free Domain Services (`GapAnalysisService`) and Use Cases rather than being coupled to
Django Views, Serializers, or ORM Models.
- **Temporal Competency History & Path Progression** follow **CQRS**, using dedicated Read Model Ports (`Protocol`) backed by optimized SQL Database Views (`LAG()` window functions
and aggregations).

### Main concepts

- Python 3.15 & `uv`
- Clean Architecture & Domain-Driven Design (DDD)
- SOLID & Explicit Composition Root (DI Container)
- CQRS (Segregated Command & Query Use Cases + Read Model Ports)
- Pydantic v2 (Strict Input/Request & Output/Response DTOs)
- Django 6 & Django REST Framework (DRF)
- Django Admin
- PostgreSQL & Optimized SQL Views (Window Functions)
- Automated testing (`Pytest` — 664 unit, integration, API, and E2E tests with 98% coverage)
- Static analysis & CI Quality Gate (`Ruff`, `Pyrefly`, GitHub Actions)

### Architectural principle

```text
┌───────────────────────────────────────────────────────────┐
│                Presentation & Infrastructure              │
│                                                           │
│   DRF API · Django Admin · Django ORM · SQL Views (PG)    │
└─────────────────────────────┬─────────────────────────────┘
                              │
                              ▼
┌───────────────────────────────────────────────────────────┐
│                        Application                        │
│                                                           │
│    Command & Query Use Cases · Pydantic DTOs · Ports      │
└─────────────────────────────┬─────────────────────────────┘
                              │
                              ▼
┌───────────────────────────────────────────────────────────┐
│                    Domain (Pure Python)                   │
│                                                           │
│   Aggregates · Value Objects · Invariants · Gap Service   │
└───────────────────────────────────────────────────────────┘
```

The objective is to demonstrate that adopting a full-featured framework like Django does not require coupling business rules to the framework itself.

👉 **[View repository](https://github.com/higorrsc/competency-analytics)**

---

# 3. Strategic Indicators — SDD & AI

**Spec-Driven Development · AI Agents · OpenAPI · BDD · LLM**

A project focused on exploring **Spec-Driven Development combined with AI-assisted software engineering**.

The application crosses process data with artificial intelligence to generate **executive-level insights and strategic indicators**.

The main experiment is not only the resulting application, but the development process itself.

## Specification First

The API is specified before implementation.

Possible approaches include:

- OpenAPI / Swagger
- BDD
- `pytest-bdd`
- `behave`

The specification defines:

- Endpoints
- HTTP methods
- Request schemas
- Response schemas
- Pydantic models
- Business rules
- Acceptance criteria

```text
             Specification
                  │
                  ▼
          ┌───────────────┐
          │    OpenAPI    │
          │   / BDD Specs │
          └───────┬───────┘
                  │
                  ▼
            AI Development
                  │
                  ▼
          ┌───────────────┐
          │ Controllers   │
          │ Use Cases     │
          │ Repositories  │
          └───────┬───────┘
                  │
                  ▼
              Test Suite
                  │
           ┌──────┴──────┐
           │             │
         PASS           FAIL
           │             │
           ▼             ▼
        Complete       Error Log
                         │
                         ▼
                    AI Correction
                         │
                         └──────► Test
```

## AI-assisted development

An AI coding agent is given the specification and instructed to implement the application based exclusively on the defined behavior.

Potential tools include:

- Cursor
- Aider
- GitHub Copilot
- Other coding agents

The agent is expected to respect:

- SOLID
- Clean Architecture
- Defined interfaces
- API contracts
- Acceptance criteria
- Existing tests

## Validation loop

Generated code is validated through automated tests.

When a test fails:

1. Capture the failure.
2. Provide the error/log to the agent.
3. Let the agent analyze the failure.
4. Apply the correction.
5. Execute the test suite again.
6. Repeat until the specified behavior is satisfied.

This project therefore explores the relationship between:

**Specification → AI Agent → Implementation → Tests → Feedback → Refinement**

---

# 4. Contract Measurement & Cost Allocation

**Financial Modeling · Data Architecture · Cost Allocation · Enterprise Systems**

A system focused on **contract measurement and financial cost allocation between hierarchical Cost Centers**.

The project models the domain of contract measurements while addressing complex data-processing and financial allocation requirements.

A central problem is the distribution of financial values across hierarchical organizational structures.

```text
                 Cost Center
                     │
          ┌──────────┴──────────┐
          ▼                     ▼
      Cost Center           Cost Center
          │                     │
      ┌───┴───┐                 ▼
      ▼       ▼             Cost Center
     ...     ...
```

Depending on the volume and characteristics of the data, complex database processing can be used where appropriate.

Possible database components include:

- Views
- Stored Procedures
- Complex SQL queries
- CTEs
- Hierarchical queries

Python repositories abstract these database operations from the application layer.

### Architecture

```text
┌─────────────────────┐
│      Frontend       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│        API          │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│      Use Cases      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│      Domain         │
│                     │
│ Contract Measurement│
│ Cost Allocation     │
│ Business Rules      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│    Repositories     │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│      Database       │
│                     │
│ SQL / Views / SPs   │
└─────────────────────┘
```

The project can also include a Power BI layer for analytical consumption.

```text
Database
    │
    ▼
Data Model
    │
    ▼
Power BI
    │
    ├── DAX
    ├── KPIs
    ├── Dashboards
    └── Interactive Analysis
```

The repository documentation includes screenshots and demonstrations of the dashboards and explains the modeling and allocation decisions.

---

# 🧠 Engineering Principles

Across the four projects, I focus on a common set of engineering principles.

### Domain First

Business rules should be explicit and understandable.

### Separation of Concerns

Infrastructure, frameworks, application logic, and domain rules should not become unnecessarily coupled.

### Testability

Important business behavior should be executable and testable independently of infrastructure.

### Explicit Architecture

Architectural decisions should be documented rather than hidden inside implementation details.

### Documentation as a Deliverable

Documentation is part of the software, not an afterthought.

Each portfolio project aims to provide:

- Local setup instructions
- Docker Compose configuration
- Architecture diagrams
- Context diagrams
- API documentation
- Test instructions
- Technical decisions
- Trade-offs
- Examples
- Screenshots where applicable

---

# 🏛️ Architecture

I'm particularly interested in architectures that allow business rules to remain independent from frameworks and infrastructure.

Some of the approaches I work with include:

- Domain-Driven Design
- Clean Architecture
- Hexagonal Architecture
- SOLID
- Dependency Inversion
- Repository Pattern
- Unit of Work
- Value Objects
- Entities
- Aggregates
- Domain Services
- Use Cases

A recurring architectural model in my projects is:

```text
                 ┌───────────────────┐
                 │   Presentation    │
                 │   API / Admin     │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │   Application     │
                 │     Use Cases     │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │      Domain       │
                 │                   │
                 │ Business Rules    │
                 │ Entities          │
                 │ Value Objects     │
                 │ Domain Services   │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │  Infrastructure  │
                 │                   │
                 │ Database          │
                 │ External APIs     │
                 │ Messaging         │
                 └───────────────────┘
```

The exact architecture varies according to the problem. Architecture is treated as a tool for managing complexity rather than a fixed template.

---

# 🐍 Backend

Python is my primary language for backend development.

My main ecosystem includes:

- Python
- FastAPI
- Django
- Django REST Framework
- SQLAlchemy
- Pydantic
- Pytest
- Celery
- `uv`

I use Python for:

- REST APIs
- Business applications
- Data processing
- ETL
- Automation
- Distributed systems
- AI applications
- RAG
- Testing

---

# 🤖 Artificial Intelligence

I'm currently exploring practical applications of AI in software engineering and business systems.

Areas of interest include:

- LLM applications
- RAG
- Embeddings
- Semantic Search
- Vector databases
- `pgvector`
- Prompt Engineering
- AI agents
- Spec-Driven Development
- AI-assisted software development

One of my main interests is combining AI with conventional software engineering:

```text
AI
+
Domain Modeling
+
Software Architecture
+
APIs
+
Databases
+
Automated Tests
```

---

# 🗄️ Databases

I have experience working with relational databases and complex SQL-based systems.

Technologies and concepts include:

- PostgreSQL
- SQL Server
- SQLite
- SQL
- CTEs
- Views
- Stored Procedures
- Database modeling
- Database migrations
- Hierarchical data
- Vector search

I am particularly interested in understanding when database-side processing is appropriate and when business logic should remain in the application/domain layer.

---

# 🐳 Infrastructure & DevOps

I have hands-on experience with containerized and cloud-native environments.

Technologies and concepts include:

- Docker
- Docker Compose
- Kubernetes
- Terraform
- Ansible
- GitOps
- CI/CD
- API Gateways
- RabbitMQ
- Apache Kafka
- gRPC
- OpenTelemetry
- Prometheus
- Istio

---

# 🧪 Testing & Quality

Testing is treated as part of the design process rather than only a final verification step.

I work with:

- Unit tests
- Integration tests
- API tests
- Domain tests
- Acceptance tests
- BDD
- Pytest
- Contract testing
- CI pipelines
- Static analysis

For AI-assisted development, automated tests become particularly important because they provide an objective feedback mechanism for generated code.

---

# 🎓 Education & Technical Training

## MBA — Software Engineering with AI

Currently pursuing an MBA focused on **Software Engineering and Artificial Intelligence**.

Current areas of study include:

- Artificial Intelligence
- LLMs
- RAG
- Prompt Engineering
- Software Architecture
- System Design
- AI-assisted development
- Software Engineering

Repositories prefixed with `fc-mba-*` contain projects, challenges, and experiments related to this training.

---

## Full Cycle 3.0

Completed the **Full Cycle 3.0 Developer Training**, with hands-on projects involving:

- Domain-Driven Design
- Clean Architecture
- Hexagonal Architecture
- Microservices
- Event-Driven Architecture
- GraphQL
- gRPC
- Apache Kafka
- RabbitMQ
- Kubernetes
- Istio
- API Gateway
- Terraform
- Ansible
- GitOps
- CI/CD
- OpenTelemetry
- Prometheus

Repositories prefixed with `fc-hrsc-*` document projects and exercises from this training.

---

## Full-stack Python Development

Completed a **Full-stack Python Developer** training covering:

- Python
- Django
- Django REST Framework
- JavaScript
- TypeScript
- React
- Vue
- HTML
- CSS
- REST APIs
- SQL

Repositories prefixed with `ebac-*` contain projects and exercises from this training.

---

# 📚 Learning Repositories

My GitHub also contains repositories created during courses, training programs, experiments, and technical studies.

They represent different stages of my learning journey.

The portfolio projects above are the primary representation of my current technical direction, while the learning repositories provide additional context about the technologies and concepts I have studied.

---

# 🛠️ Technology Stack

<p align="left">

<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="40" title="Python"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/django/django-plain.svg" width="40" title="Django"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/fastapi/fastapi-original.svg" width="40" title="FastAPI"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" width="40" title="PostgreSQL"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/microsoftsqlserver/microsoftsqlserver-plain.svg" width="40" title="SQL Server"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" width="40" title="Docker"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kubernetes/kubernetes-plain.svg" width="40" title="Kubernetes"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" width="40" title="Git"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" width="40" title="GitHub"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/go/go-original.svg" width="40" title="Go"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" width="40" title="TypeScript"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" width="40" title="React"/>
<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" width="40" title="Linux"/>

</p>

---

# 📈 Technical Direction

My current technical direction can be summarized as:

```text
Backend Engineering
        │
        ├── Software Architecture
        │
        ├── Domain Modeling
        │
        ├── Distributed Systems
        │
        ├── Data & Databases
        │
        └── Artificial Intelligence
                  │
                  ├── LLMs
                  ├── RAG
                  ├── Semantic Search
                  └── AI-assisted Development
```

The four portfolio projects are designed to explore these areas through concrete software systems rather than isolated technology demonstrations.

---

# 📫 Contact

If you're interested in software engineering, backend development, architecture, distributed systems, data, or AI applications, feel free to connect.

- GitHub: [@higorrsc](https://github.com/higorrsc)

---

> **Build software. Model the problem. Test the behavior. Document the decisions.**
