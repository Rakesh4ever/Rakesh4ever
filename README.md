<p align="center">
  <img src="assets/banner/github-header.svg" alt="Rakesh Kumar — Senior Java Backend Engineer. Building scalable, secure, distributed systems." width="100%">
</p>

<h1 align="center">Rakesh Kumar</h1>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&pause=1200&color=38BDF8&center=true&vCenter=true&width=640&height=32&lines=Senior+Java+Backend+Engineer;Microservices+Engineer;Distributed+Systems+Engineer;Cloud-Native+Developer" alt="Senior Java Backend Engineer">
</p>

<p align="center">
  10+ years building Java backend systems — Spring Boot microservices, event-driven services, and secure REST APIs.<br>
  Focused on service discovery, JWT authorization, and cloud-native delivery.
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/rakesh-kumar"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  <a href="https://github.com/Rakesh4ever"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white" alt="GitHub"></a>
  <a href="https://financecontrol.net"><img src="https://img.shields.io/badge/FinanceControl.net-0F766E?style=flat-square" alt="FinanceControl.net"></a>
  <a href="https://tithi.live"><img src="https://img.shields.io/badge/Tithi.Live-7C3AED?style=flat-square" alt="Tithi.Live"></a>
</p>

---

## Engineering Focus

| Area | What I work on |
| --- | --- |
| **Microservices** | Independently deployable Spring Boot services that register with Eureka and call each other by name, not host. |
| **Application security** | JWT access and refresh tokens, token revocation on logout, and role/permission checks (`USER`, `MANAGER`, `ADMIN`). |
| **Event-driven systems** | REST endpoints that publish to Apache Kafka topics; RabbitMQ producer to a named exchange. |
| **Java / JVM** | Modern Java (11/17/21), Spring Boot 3/4, and virtual-thread vs platform-thread execution. |
| **API design** | Versioned REST APIs, OpenAPI/Swagger, RFC 7807 error bodies, Spring Data JPA. |
| **Cloud-native delivery** | Docker Compose for local data stores, GitHub Actions to Azure, Maven-based CI. |

---

## Technology Stack

**Languages**  
`Java 11 / 17 / 21` · `TypeScript` · `C`

**Backend**  
`Spring Boot` · `Spring Security` · `Spring WebFlux` · `Spring Data JPA` · `Hibernate`

**Architecture & messaging**  
`Microservices` · `Netflix Eureka` · `REST` · `Apache Kafka` · `RabbitMQ` · `SOAP / WSDL`

**Data**  
`MySQL` · `Apache Cassandra` · `H2`

**Cloud, containers & delivery**  
`Docker` · `Microsoft Azure` · `GitHub Actions` · `Jenkins` · `Maven`

**Security**  
`JWT (HS256)` · `BCrypt` · `method-level authorization`

**Testing & API docs**  
`JUnit 5` · `Mockito` · `MockMvc` · `springdoc-openapi`

<p align="center">
  <img src="https://skillicons.dev/icons?i=java,spring,kafka,rabbitmq,mysql,docker,azure,angular,maven,git,githubactions" alt="Java, Spring, Kafka, RabbitMQ, MySQL, Docker, Azure, Angular, Maven, Git, GitHub Actions">
</p>

---

## Featured Projects

### Spring Boot 3 JWT Security
JWT-based stateless API authentication with refresh tokens, logout revocation, and role-based authorization.

`Java 21` `Spring Boot 4` `Spring Security` `JWT` `MySQL` `JPA` `OpenAPI`

[View repository →](https://github.com/Rakesh4ever/spring-boot-3-jwt-security)

### Microservices Intercommunication
Three Spring Boot services: a Eureka registry, a provider, and a consumer that resolves `hello-server` through a load-balanced `RestTemplate`.

`Spring Cloud` `Eureka` `REST` `Ribbon` `JUnit`

[View repository →](https://github.com/Rakesh4ever/micro-services)

### Kafka Producer
REST endpoint that publishes messages onto an Apache Kafka topic (`kafkaTopic`) after ZooKeeper and the broker are up.

`Spring Kafka` `REST` `Apache Kafka`

[View repository →](https://github.com/Rakesh4ever/KafkaProducer)

### Java Virtual Threads
Compares launch cost of 100,000 virtual threads vs platform threads using `Thread.ofVirtual()` and `Thread.ofPlatform()`.

`Java` `Project Loom` `Concurrency`

[View repository →](https://github.com/Rakesh4ever/JavaVirtualThreads)

### Reactive Cassandra POC
Spring WebFlux + WebClient service that persists entities to Apache Cassandra (Java 11, Spring Boot 2.x).

`WebFlux` `WebClient` `Cassandra` `Swagger`

[View repository →](https://github.com/Rakesh4ever/POC)

### Products
- **[FinanceControl.net](https://financecontrol.net)** — personal-finance platform (budget, SIP, tax, and FX tools).
- **[Tithi.Live](https://tithi.live)** — city-aware Hindu panchang (tithi, nakshatra, rahu kaal, muhurta).

---

## Architecture

Two public repos with the clearest request paths. Components match the code and READMEs — nothing invented.

### JWT security request path

<p align="center">
  <img src="assets/architecture/jwt-security.svg" alt="Client authenticates, then JwtAuthenticationFilter validates the Bearer token against MySQL before role-gated controllers." width="100%">
</p>

```mermaid
sequenceDiagram
    participant Caller
    participant Auth as /api/v1/auth
    participant Filter as JwtAuthenticationFilter
    participant DB as MySQL (user + token)
    participant API as Secured controller

    Caller->>Auth: POST /register or /authenticate
    Auth->>DB: save user, store access token
    Auth-->>Caller: access_token + refresh_token
    Caller->>Filter: GET secured path + Bearer token
    Filter->>DB: load user, confirm token not revoked
    Filter->>API: SecurityContext with role authorities
    API-->>Caller: 200 or 403
```

### Service discovery call path

<p align="center">
  <img src="assets/architecture/micro-services.svg" alt="Caller hits hello-client, which looks up hello-server in Eureka, then calls it by service name." width="100%">
</p>

```mermaid
sequenceDiagram
    participant Caller
    participant Client as hello-client :8072
    participant Eureka as eureka-service :8070
    participant Server as hello-server :8071

    Caller->>Client: GET /rest/hello/client
    Client->>Eureka: where is hello-server?
    Eureka-->>Client: instance localhost:8071
    Client->>Server: GET /rest/hello/server
    Server-->>Client: Hello-from-server
    Client-->>Caller: Hello-from-server
```

---

## GitHub Activity

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats-anuraghazra1.vercel.app/api?username=Rakesh4ever&show_icons=true&theme=tokyonight&hide_border=true">
    <source media="(prefers-color-scheme: light)" srcset="https://github-readme-stats-anuraghazra1.vercel.app/api?username=Rakesh4ever&show_icons=true&theme=default&hide_border=true">
    <img src="https://github-readme-stats-anuraghazra1.vercel.app/api?username=Rakesh4ever&show_icons=true&theme=tokyonight&hide_border=true" alt="GitHub stats for Rakesh4ever" height="160">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats-anuraghazra1.vercel.app/api/top-langs/?username=Rakesh4ever&layout=compact&theme=tokyonight&hide_border=true">
    <source media="(prefers-color-scheme: light)" srcset="https://github-readme-stats-anuraghazra1.vercel.app/api/top-langs/?username=Rakesh4ever&layout=compact&theme=default&hide_border=true">
    <img src="https://github-readme-stats-anuraghazra1.vercel.app/api/top-langs/?username=Rakesh4ever&layout=compact&theme=tokyonight&hide_border=true" alt="Top languages for Rakesh4ever" height="160">
  </picture>
</p>

---

## Currently Exploring

- Modern Java and JVM execution models (virtual threads, Spring Boot 4)
- Distributed-system design around service discovery and messaging
- Cloud-native backend delivery
- AI-assisted software engineering

---

## Certifications & Continuous Learning

Public LinkedIn credentials. Skill assessments are LinkedIn Skill Assessments, not vendor professional exams.

| Certification | Issuer | Year |
| --- | --- | --- |
| [Java](https://www.linkedin.com/in/rakesh-kumar/detail/assessments/Java/report/) | LinkedIn | 2019 |
| [Spring Framework](https://www.linkedin.com/in/rakesh-kumar/detail/assessments/Spring%20Framework/report/) | LinkedIn | 2020 |
| [MySQL](https://www.linkedin.com/in/rakesh-kumar/detail/assessments/MySQL/report/) | LinkedIn | 2020 |
| [Simplifying data pipelines with Apache Kafka](https://courses.cognitiveclass.ai/certificates/4a715cc938e049c38a12034a74a572b7) | IBM Cognitive Class | 2018 |
| [Hadoop Programming](https://www.linkedin.com/in/rakesh-kumar/details/certifications/) | IBM | 2018 |
| [Angular](https://www.linkedin.com/in/rakesh-kumar/detail/assessments/Angular/report/) | LinkedIn | 2021 |

---

## Let's Connect

I'm interested in backend engineering, distributed systems, Java platform work, and cloud-native architecture.

<p align="center">
  <a href="https://www.linkedin.com/in/rakesh-kumar">LinkedIn</a>
  ·
  <a href="https://github.com/Rakesh4ever">GitHub</a>
  ·
  <a href="https://financecontrol.net">FinanceControl.net</a>
  ·
  <a href="https://tithi.live">Tithi.Live</a>
</p>
