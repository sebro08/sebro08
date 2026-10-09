# Sebastián Rodríguez

Computer Engineering student at the Costa Rica Institute of Technology (TEC). I like understanding how the pieces of a system fit together: from the API and the database to deployment and the interface.

Right now: building a cloud-native platform on **Azure + Terraform** and learning **Angular + TypeScript** on the frontend.

📍 San José, Costa Rica · ✉️ seb08rs@gmail.com · [LinkedIn](https://www.linkedin.com/in/sebastián-rodríguez-sánchez)


<p align="center">
  <img src="./assets/request-flow.svg" alt="A request travels from Angular through the API, the cache, the databases and the analytics layer" width="100%">
</p>

---

## 1. Smart Restaurant Reservations

*(repo: Reserva Inteligente de Restaurantes)*

Distributed platform for restaurants, reservations and orders, with a transactional layer (OLTP) and an analytical layer (OLAP) on the same data.

```mermaid
flowchart LR
    C[Client] --> N[Nginx<br/>load balancing]
    N --> A[REST API<br/>Node + Express + TS]
    A --> K[Keycloak<br/>OAuth2 / JWT]
    A --> R[(Redis<br/>cache)]
    A --> E[(Elasticsearch<br/>search)]
    A --> P[(PostgreSQL)]
    A --> M[(MongoDB<br/>sharded)]
    P & M --> AF[Airflow]
    AF --> S[Spark]
    S --> H[(Hive / HDFS<br/>Data Warehouse)]
    H --> MB[Metabase<br/>dashboards]
    P & M --> G[(Neo4j<br/>routes & graphs)]
```

- **Swappable database engine:** `DB_TYPE=postgres` or `mongodb` and the system switches engines with no code changes, thanks to a repository abstraction built around a `RepositoryFactory`.
- **High availability:** MongoDB with sharding (config servers, routers, replica sets) and automatic initialization.
- **Analytics pipeline:** ETL orchestrated with Airflow, processed with Spark, star schema in Hive on HDFS (Parquet), dashboards in Metabase.
- **Deployment:** Docker Compose profiles, plus Kubernetes manifests.
- **API documented** with Swagger.

**Stack:** TypeScript · Node.js · Express · PostgreSQL · MongoDB · Redis · Elasticsearch · Keycloak · Docker · Kubernetes · Nginx · Airflow · Spark · Hive · Neo4j · Metabase

<p align="center">
  <a href="https://github.com/sebro08/Reserva-Inteligente-de-Restaurantes">
    <img src="./assets/card-reserva.svg" alt="Smart Restaurant Reservations: view repository" width="430">
  </a>
</p>

---

## 2. Sports Analytics Platform · *in development*

Cloud-native sports analytics platform, designed from day one to be deployed as infrastructure as code.

```mermaid
flowchart LR
    U[Client] --> API[REST API<br/>TypeScript + Fastify]
    API --> PG[(PostgreSQL)]
    API --> RD[(Redis)]
    GH[GitHub Actions] -.-> TF[Terraform]
    TF -.-> AZ[Azure Container Apps]
```

Dotted lines show what comes next (CI/CD and deployment on Azure).

- **Done (phases 1–3):** project structure, Fastify API, PostgreSQL and Redis with Docker Compose, versioned SQL migrations, health checks and tests.
- **Next:** infrastructure with Terraform, a GitHub Actions pipeline and deployment to Azure Container Apps.
- The architecture is documented in `docs/architecture.md`.

**Stack:** TypeScript · Fastify · PostgreSQL · Redis · Docker · Terraform · GitHub Actions · Azure Container Apps

<p align="center">
  <a href="https://github.com/sebro08/Sports-Pulse">
    <img src="./assets/card-deportivo.svg" alt="Sports Analytics Platform: view repository" width="430">
  </a>
</p>

---

## 3. Board Meeting Management System

*(repo: Juntas-directivas)*

Full-stack application covering the whole lifecycle of a board meeting: email invitations, agenda, attendance, live decisions and tasks, and the final minutes as a PDF. Team project.

```mermaid
flowchart LR
    U[User] --> F[Angular 19<br/>guard + JWT interceptor]
    F -->|REST| B[Express 5 + TypeScript]
    B --> O[TypeORM]
    O --> D[(MySQL 8)]
    B --> M[Nodemailer]
    B --> P[PDFKit<br/>minutes]
```

- **Three agenda item types** (informative, strategic and approval) created with a Factory pattern and stored in a single table using table inheritance.
- **Queries built with the Visitor pattern:** meetings a member missed, and minutes by presenter or by task owner.
- **Adapter** to treat a board member as a regular system user.
- **Notifications**, tasks with owners, voting and file attachments per agenda item.

**Stack:** Angular 19 · Angular Material · TypeScript · Express · TypeORM · MySQL · JWT · Docker

<p align="center">
  <a href="https://github.com/sebro08/Juntas-directivas">
    <img src="./assets/card-juntas.svg" alt="Board Meeting Management System: view repository" width="430">
  </a>
</p>

---

## 4. AP-LABS · TEC lab management

**Kotlin** application (Gradle project) to manage the laboratories at TEC. I later rebuilt it as a TypeScript web application ([AP-LABS2](https://github.com/sebro08/AP-LABS2)) to compare both approaches.

**Stack:** Kotlin · Gradle

<p align="center">
  <a href="https://github.com/sebro08/AP-LABS">
    <img src="./assets/card-aplabs.svg" alt="AP-LABS: view repository" width="430">
  </a>
</p>

---

## Technologies

**Languages**  
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E) ![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white) ![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=ffdd54) ![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)

**Frontend**  
![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)

**Backend & authentication**  
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white) ![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white) ![Keycloak](https://img.shields.io/badge/Keycloak-4D4D4D?style=for-the-badge&logo=keycloak&logoColor=white)

**Databases & search**  
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white) ![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=for-the-badge&logo=elasticsearch&logoColor=white) ![Neo4j](https://img.shields.io/badge/Neo4j-4581C3?style=for-the-badge&logo=neo4j&logoColor=white) ![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)

**Data & analytics**  
![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=for-the-badge&logo=apacheairflow&logoColor=white) ![Spark](https://img.shields.io/badge/Spark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white)

**Infrastructure & deployment**  
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white) ![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)

**Design & organization**  
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white) ![Canva](https://img.shields.io/badge/Canva-00C4CC?style=for-the-badge&logo=canva&logoColor=white) ![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)

---

## What I've used and where

| Technology | Where I used it |
|---|---|
| TypeScript, Node.js, Express | Smart Restaurant Reservations, Sports Analytics Platform, Board Meeting Management, AP-LABS2 |
| MySQL, TypeORM | Board Meeting Management |
| PostgreSQL, MongoDB (sharding) | Smart Restaurant Reservations (swappable); PostgreSQL in the Sports Analytics Platform |
| Redis, Elasticsearch | Caching and search |
| Keycloak (OAuth2 / JWT) | Authentication and roles in Smart Restaurant Reservations |
| JWT, bcrypt | Authentication in Board Meeting Management |
| Docker, Kubernetes, Nginx | Deployment and load balancing |
| GitHub Actions, Azure | Sports Analytics Platform |
| Airflow, Spark, Neo4j | Analytics pipeline in Smart Restaurant Reservations |
| Kotlin | AP-LABS |
| Java, JFlex, CUP | [Compilers and interpreters](https://github.com/sebro08/CompiladoresJFlex) |
| C++, Python, MySQL, Oracle | University coursework |
| Figma, Canva | Design and prototyping |

---

Feedback on a repo, or interested in collaborating? Open an issue or get in touch.