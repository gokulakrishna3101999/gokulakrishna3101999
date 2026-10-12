# Gokulakrishna K 👋

I'm a senior backend software engineer from India 🇮🇳, building distributed, fault-tolerant microservices in **Java and Spring Boot**, and extending that rigor into applied AI infrastructure (RAG and MCP).

## About me

- 💼 **Senior Software Engineer (Backend) at CitiusTech**, working with athenahealth on healthcare document reconciliation: DDD-based domain models, hexagonal-architecture integrations, and FHIR-to-vendor messaging.
- ⚙️ Previously **4 years at Zoho CRM**, owning the Module Builder - Fields component used by **250K+ users**.
- 🧱 5 years of experience in system design, Domain-Driven Design, REST APIs, concurrency, and multi-tenant architecture.
- 🔎 Building **SynapseMCP**, an open-source multi-tenant RAG + Model Context Protocol platform.

## Experience

**Senior Software Engineer (Backend), CitiusTech (Client: athenahealth)**, Aug 2025 - Present
- Redesigned core healthcare domain models for Medical Record Release (MRR) document reconciliation using DDD, resolving scalability and data-consistency gaps across independently deployed microservices.
- Built hexagonal-architecture integrations with IAM authentication and idempotency/retry semantics for external Medical Document Platform APIs, sustaining **2K+ documents monthly** in production.
- Developed REST APIs transforming FHIR Audit Events into vendor messages for record-level regulatory compliance.
- Implemented a domain-level validation framework separating terminal from transient failures, cutting retry-related incidents from **~2/week to ~1/month**.
- Introduced MDC-based structured logging with distributed tracing, so cross-service incidents are diagnosed by following a single trace ID.

**Member Technical Staff (Backend Engineer), Zoho CRM**, Aug 2021 - Aug 2025
- Owned the Module Builder - Fields component (**250K+ users**), evolving the field-metadata architecture behind custom modules, layouts, sections, and fields.
- Built dynamic field-limit expansion and on-demand field-type conversion tooling, removing a hard product limit.
- Implemented sandbox support for the full field-configuration lifecycle, reducing production deployment failures by **70%**.
- Engineered Rich Text and Address field types, driving adoption across **15K+ accounts**.
- Optimized hot paths in legacy high-volume CRM workflows and built REST and bulk Java APIs, reducing API latency by **35%**.

## Tools I work with

<p>
  <img src="https://skillicons.dev/icons?i=java,py,cpp,spring,postgres,mysql,redis,react,ts&perline=9" alt="Languages, frameworks and databases" />
  <br />
  <img src="https://skillicons.dev/icons?i=aws,docker,kubernetes,jenkins,maven,gradle,terraform,git,prometheus&perline=9" alt="Cloud, DevOps and observability" />
</p>

Also: Spring AI · Spring Data JPA · JUnit · Struts · RAG · MCP · Embeddings · Hybrid retrieval · AWS (EC2, EKS, SQS, S3, VPC, Lambda) · Amazon CloudWatch

## Featured projects

### [SynapseMCP](https://github.com/gokulakrishna3101999/SynapseMCP)
An enterprise-grade, multi-tenant RAG platform with an integrated MCP server. It bridges proprietary documents with LLMs while keeping tenants strictly isolated, ingestion costs predictable, and answers well grounded. Users get a React 19 SPA for conversational RAG, and external assistants such as Claude Desktop and Cursor can query their isolated knowledge base over MCP.

- **Strict multi-tenancy:** one unified knowledge base per tenant, isolated with PostgreSQL Row-Level Security and JPA discriminator columns.
- **MCP server:** API-key-secured JSON-RPC 2.0 over HTTP/SSE; REST and MCP invoke the same domain services with no HTTP loopback.
- **Hybrid retrieval:** Lucene BM25 and pgvector cosine ANN fused with Reciprocal Rank Fusion, plus LLM reranking, lifting MRR from 0.83 (vector-only) to 0.94 (hybrid) to 1.00 (reranked) on an 18-document golden-query harness.
- **Ingestion:** async five-stage pipeline (extract, chunk, embed, persist, index) with SHA-256 idempotency, size-tiered extraction, and no permanent raw-file storage (staged files are purged after embedding).
- **Query routing:** falls back to web search (Tavily) when local similarity is below 0.70, to prevent hallucinations.
- **Reliability:** per-tenant Bucket4j rate limiting that degrades to an in-JVM limiter during Redis outages; 447+ tests at 94%+ coverage against real PostgreSQL and Redis.
- **Live progress:** upload percentage plus server-side milestones (parsing, chunking, embedding, purging) streamed via SSE.

<img src="https://skillicons.dev/icons?i=java,spring,postgres,redis,react,ts,docker" height="32" alt="Java, Spring Boot, PostgreSQL, Redis, React, TypeScript, Docker" />

`Java 21` `Spring Boot` `Spring AI` `PostgreSQL/pgvector` `Lucene` `Redis` `React 19` `TypeScript` `Docker` `MCP`

### [Edge Gateway & Service Discovery](https://github.com/gokulakrishna3101999/eureka-service)
A standalone, plug-and-play edge service for distributed systems: one process that acts as the single point of contact for a microservice fleet. It is independent of SynapseMCP and can be dropped into any project; downstream services only need to register with Eureka.

- **Service discovery:** embedded Netflix Eureka server with a dashboard.
- **API gateway:** Spring Cloud Gateway Server MVC on Java 21 virtual threads, routing `/api/v1/**` paths to services registered in Eureka, with correlation-ID propagation for tracing.
- **Load balancing:** client-side balancing over `lb://` routes, retrying transient 502/503/504 responses on other healthy instances.
- **Rate limiting:** Redis-backed token bucket keyed by user (falling back to client IP), returning HTTP 429 when exhausted and failing open if Redis is down.
- **Authentication:** stateless OAuth2 JWT resource server with cached JWKS keys; works with providers such as Keycloak, Auth0 or Okta. The gateway forwards lightweight `X-User-Id` and `X-User-Roles` headers to downstream services.
- **Operations:** Actuator health/metrics/Prometheus endpoints, unit tests for the filters, and a hardened non-root Docker image.

<img src="https://skillicons.dev/icons?i=java,spring,redis,docker,maven" height="32" alt="Java, Spring, Redis, Docker, Maven" />

`Java 21` `Spring Boot 3.3` `Spring Cloud Gateway` `Netflix Eureka` `Spring Security` `Redis` `Docker`

## Education

B.E. in Computer Science, Velammal Institute of Technology (2017 - 2021)

## Contact

📧 [gokulakrishna3101999@gmail.com](mailto:gokulakrishna3101999@gmail.com) · [LinkedIn](https://www.linkedin.com/in/gokula-krishna-4878981b1) · [GitHub](https://github.com/gokulakrishna3101999)
