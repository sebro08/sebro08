# Sebastián Rodríguez

Estudiante de Ingeniería en Computación en el TEC, Costa Rica. Me interesa entender cómo encajan las piezas de un sistema: de la API y la base de datos hasta el despliegue y la interfaz.

Ahora mismo: construyendo una plataforma cloud-native en **Azure + Terraform** y aprendiendo **Angular + TypeScript** en el frontend.

📍 San José, Costa Rica · ✉️ seb08rs@gmail.com · [LinkedIn](https://www.linkedin.com/in/sebastián-rodríguez-sánchez)


<p align="center">
  <img src="./assets/request-flow.svg" alt="Una petición viaja desde Angular por la API, la caché, las bases de datos y la capa analítica" width="100%">
</p>

---

## 1. Reserva Inteligente de Restaurantes

Plataforma distribuida para restaurantes, reservas y pedidos, con una capa transaccional (OLTP) y otra analítica (OLAP) sobre los mismos datos.

```mermaid
flowchart LR
    C[Cliente] --> N[Nginx<br/>balanceo]
    N --> A[API REST<br/>Node + Express + TS]
    A --> K[Keycloak<br/>OAuth2 / JWT]
    A --> R[(Redis<br/>caché)]
    A --> E[(Elasticsearch<br/>búsqueda)]
    A --> P[(PostgreSQL)]
    A --> M[(MongoDB<br/>sharded)]
    P & M --> AF[Airflow]
    AF --> S[Spark]
    S --> H[(Hive / HDFS<br/>Data Warehouse)]
    H --> MB[Metabase<br/>dashboards]
    P & M --> G[(Neo4j<br/>rutas y grafos)]
```

- **Motor de base de datos intercambiable:** `DB_TYPE=postgres` o `mongodb` y el sistema cambia de motor sin tocar código, gracias a una abstracción de repositorios con `RepositoryFactory`.
- **Alta disponibilidad:** MongoDB con sharding (config servers, routers, replica sets) con inicialización automática.
- **Pipeline analítico:** ETL orquestado con Airflow, procesado con Spark, esquema estrella en Hive sobre HDFS (Parquet), dashboards en Metabase.
- **Despliegue:** Docker Compose por perfiles, y manifiestos de Kubernetes.
- **API documentada** con Swagger.

**Stack:** TypeScript · Node.js · Express · PostgreSQL · MongoDB · Redis · Elasticsearch · Keycloak · Docker · Kubernetes · Nginx · Airflow · Spark · Hive · Neo4j · Metabase

[Ver repositorio →](https://github.com/sebro08/Reserva-Inteligente-de-Restaurantes)

---

## 2. Plataforma de análisis deportivo · *en desarrollo*

Plataforma cloud-native de análisis deportivo, pensada desde el inicio para desplegarse como infraestructura como código.

```mermaid
flowchart LR
    U[Cliente] --> API[API REST<br/>TypeScript + Fastify]
    API --> PG[(PostgreSQL)]
    API --> RD[(Redis)]
    GH[GitHub Actions] -.-> TF[Terraform]
    TF -.-> AZ[Azure Container Apps]
```

Las líneas punteadas son la parte que viene (CI/CD y despliegue en Azure).

- **Hecho (fases 1–3):** estructura del proyecto, API con Fastify, PostgreSQL y Redis con Docker Compose, migraciones SQL versionadas, health checks y tests.
- **Siguiente:** infraestructura con Terraform, pipeline en GitHub Actions y despliegue en Azure Container Apps.
- La arquitectura está documentada en `docs/architecture.md`.

**Stack:** TypeScript · Fastify · PostgreSQL · Redis · Docker · Terraform · GitHub Actions · Azure Container Apps

[Ver repositorio →](https://github.com/sebro08/NOMBRE-DEL-REPO)

---

## 3. Sistema de Administración de Juntas Directivas

Aplicación full-stack para el ciclo completo de una sesión de junta: convocatoria por correo, agenda, asistencia, decisiones y tareas en vivo, y acta final en PDF. Proyecto de equipo.

```mermaid
flowchart LR
    U[Usuario] --> F[Angular 19<br/>guard + interceptor JWT]
    F -->|REST| B[Express 5 + TypeScript]
    B --> O[TypeORM]
    O --> D[(MySQL 8)]
    B --> M[Nodemailer]
    B --> P[PDFKit<br/>actas]
```

- **Tres tipos de punto de agenda** (informativo, estratégico y de aprobación) creados con un patrón Factory y guardados en una sola tabla con herencia.
- **Consultas con patrón Visitor:** sesiones en las que un miembro estuvo ausente, actas por expositor o por responsable.
- **Adapter** para tratar a un miembro de junta como usuario del sistema.
- **Notificaciones**, tareas con responsable, votaciones y archivos adjuntos por punto.

**Stack:** Angular 19 · Angular Material · TypeScript · Express · TypeORM · MySQL · JWT · Docker

[Ver repositorio →](https://github.com/sebro08/admin-proyecto-g2)

---

## 4. AP-LABS · gestión de laboratorios del TEC

Aplicación en **Kotlin** (proyecto Gradle) para gestionar los laboratorios del TEC. Después la rehice como aplicación web en TypeScript ([AP-LABS2](https://github.com/sebro08/AP-LABS2)) para comparar ambos enfoques.

**Stack:** Kotlin · Gradle

[Ver repositorio →](https://github.com/sebro08/AP-LABS)

---

## Tecnologías

**Lenguajes**  
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E) ![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white) ![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=ffdd54) ![C++](https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

**Frontend y móvil**  
![Angular](https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white) ![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB) ![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)

**Backend y autenticación**  
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white) ![Fastify](https://img.shields.io/badge/Fastify-000000?style=for-the-badge&logo=fastify&logoColor=white) ![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white) ![Keycloak](https://img.shields.io/badge/Keycloak-4D4D4D?style=for-the-badge&logo=keycloak&logoColor=white)

**Bases de datos y búsqueda**  
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white) ![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=for-the-badge&logo=elasticsearch&logoColor=white) ![Neo4j](https://img.shields.io/badge/Neo4j-4581C3?style=for-the-badge&logo=neo4j&logoColor=white) ![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)

**Datos y analítica**  
![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=for-the-badge&logo=apacheairflow&logoColor=white) ![Spark](https://img.shields.io/badge/Spark-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white) ![Hive](https://img.shields.io/badge/Hive-FDEE21?style=for-the-badge&logo=apachehive&logoColor=black) ![Metabase](https://img.shields.io/badge/Metabase-509EE3?style=for-the-badge&logo=metabase&logoColor=white)

**Infraestructura y despliegue**  
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white) ![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white) ![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=for-the-badge&logo=terraform&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white) ![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)

**Diseño y organización**  
![Figma](https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white) ![Canva](https://img.shields.io/badge/Canva-00C4CC?style=for-the-badge&logo=canva&logoColor=white) ![Notion](https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white)

---

## Qué he usado y dónde

| Tecnología | Dónde la usé |
|---|---|
| TypeScript, Node.js, Express, Fastify | Reserva Inteligente, plataforma deportiva, Juntas Directivas, AP-LABS2 |
| MySQL, TypeORM | Juntas Directivas |
| PostgreSQL, MongoDB (sharding) | Reserva Inteligente (intercambiables); PostgreSQL en la plataforma deportiva |
| Redis, Elasticsearch | Caché y búsqueda |
| Keycloak (OAuth2 / JWT) | Autenticación y roles en Reserva Inteligente |
| JWT, bcrypt | Autenticación en Juntas Directivas |
| Docker, Kubernetes, Nginx | Despliegue y balanceo de carga |
| Terraform, GitHub Actions, Azure | Plataforma deportiva |
| Airflow, Spark, Hive, Neo4j, Metabase | Pipeline analítico de Reserva Inteligente |
| Kotlin | AP-LABS |
| Java, JFlex, CUP | [Compiladores e intérpretes](https://github.com/sebro08/CompiladoresJFlex) |
| C++, Python, MySQL, Oracle | Cursos de la carrera |
| Figma, Canva | Diseño y prototipos |

---

¿Feedback sobre algún repo o ganas de colaborar? Abre un issue o escríbeme.
