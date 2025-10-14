# CL-Architecture 
**Version:** 1.0.0  
**Tagline:** “The modern, modular, and automated backend architecture pattern built for clarity, control, and scalability.”

---

## Overview

**CL-Architecture** (Core-Line Architecture) is a next-generation backend pattern for Node.js / TypeScript backends.  
It provides:

- Modular, self-contained feature structure  
- Enforced design principles: SOLID, DRY, CQRS, Dependency Inversion  
- Built-in core utilities: logging, error handling, mapping, monitoring  
- Automated CLI generation for modules and boilerplate  
- Testable, scalable, and enterprise-ready design

---

## Core Philosophy

| Principle | Description |
|------------|-------------|
| **Linear Flow** | Data and logic move clearly along the “Core Line”. |
| **Isolation by Context** | Each module owns its data, logic, and validation. |
| **Automation by Convention** | File structure, naming, and wiring are standardized. |
| **Abstraction by Contract** | Layers interact only through typed interfaces. |
| **Observability First** | Logging, tracing, and metrics are core. |
| **Testable by Design** | Every layer is unit-testable. |
| **Future-Ready** | Built for AI agents, event buses, distributed systems. |

---

## Layers

| Layer | Role |
|-------|------|
| **Port** | Entry layer (HTTP, GraphQL, CLI, WebSocket). |
| **Flow** | Business logic and workflows. |
| **Source** | Data access: DB, cache, external APIs. |
| **Shape** | Domain models, entities, schemas. |
| **Bridge** | DTOs / transformation layer. |
| **Pulse** | Core systems: logging, error, events, telemetry. |
| **Orbit** | Config, environment, constants. |
| **Gateway** | Application entry point, dependency registration. |

---

## Folder Structure

```
src/
┣━━ pulse/
┣━━ orbit/
┣━━ gateway/
┣━━ modules/
│ ┣━━ user/
│ │ ┣━━ port/
│ │ ┣━━ flow/
│ │ ┣━━ source/
│ │ ┣━━ shape/
│ │ ┣━━ bridge/
│ │ ┗━━ rule/
│ ┗━━ auth/
┣━━ framework/
┗━━ test/

```

---

## Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Class / Interface | PascalCase | `UserFlow`, `IUserSource` |
| File | kebab-case | `user-flow.ts` |
| DTO / Model | PascalCase + suffix | `UserShape`, `CreateUserBridge` |
| Command / Query | Verb + Noun | `CreateUserFlow`, `GetUserFlow` |
| Constants | UPPER_SNAKE_CASE | `MAX_LOGIN_ATTEMPTS` |
| Env variables | Uppercase prefix | `APP_PORT`, `DB_URL` |

---

## Automation CLI (Example)

```bash
npx cl-cli create module user
Generates module structure automatically:

/modules/user with all subfolders

Base files (port, flow, source, bridge, shape, rule)

Registers module in gateway

Adds stub tests
