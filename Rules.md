# CL-Architecture — Design Rules & Standards

## 1. Module Structure

- Each module (`user`, `auth`) must have: `port/`, `flow/`, `source/`, `shape/`, `bridge/`, `rule/`.  
- Modules are **self-contained**; no internal access between modules except through interfaces.

---

## 2. Layer Rules

| Layer | Responsibility |
|-------|----------------|
| Port | Input/Output only. Validate requests and forward to Flow. |
| Flow | Business logic and workflows. Use Sources via interfaces. |
| Source | Data access, DB, cache, external APIs. |
| Bridge | Map entities ↔ DTOs. No business logic. |
| Shape | Define domain models, schema contracts. |
| Pulse | Logging, errors, events, telemetry. |
| Orbit | Config, constants, environment variables. |
| Gateway | Bootstrapping, dependency injection, module registration. |

---

## 3. SOLID & Design Principles

- **SRP**: Each class has one reason to change.  
- **OCP**: Modules are open for extension, closed for modification.  
- **LSP & ISP**: Use interfaces for abstraction; each interface is minimal and specific.  
- **DIP**: Flow depends on abstract Source interfaces, not concrete classes.  
- **DRY**: Shared utilities live in `pulse/utils`.

---

## 4. Flow of Data

Request → Port → Flow → Source → Bridge → Response

yaml
Copy code

- Input validated in `rule/` before Flow.  
- Output mapped in `Bridge` before returning via Port.  
- Flow never accesses DB directly; must go through Source.

---

## 5. Error Handling

- Use `CLException` for all expected errors (validation, not-found, permission).  
- Pulse handles unexpected errors globally.  
- Never throw raw `Error` in Flow or Source.  

---

## 6. Logging & Observability

- All requests get a `traceId`.  
- Logs include module name, flow name, traceId.  
- Pulse layer integrates with Prometheus/OpenTelemetry/Sentry.  
- Never log sensitive info (passwords, tokens).  

---

## 7. Testing

- **Unit tests**: Flow and Rule logic only.  
- **Integration tests**: Full Port → Flow → Source chain.  
- **Contract tests**: External API mocks in Source.  
- Use factories/fixtures, avoid hardcoded test data.

---

## 8. Security

- Input validation in `rule/`.  
- Authorization enforced in Flow.  
- Use parameterized queries / ORM to prevent injections.  
- Secrets from Orbit only, never hard-coded.  
- HTTPS, CORS, Helmet, rate-limiting enforced globally.

---

## 9. Naming

- Classes/interfaces: PascalCase (`UserFlow`)  
- Files: kebab-case (`user-flow.ts`)  
- DTOs: `Shape`/`Bridge` suffix  
- Constants: UPPER_SNAKE_CASE  
- Env: Uppercase + prefix (`APP_PORT`)

---

## 10. Versioning

- Semantic versioning: MAJOR.MINOR.PATCH  
- Major versions introduce structural changes only.  
- Migration guides must be provided on breaking changes.  

---

## 11. Automation & CLI Standards

- CLI generates modules fully following CL-Architecture rules.  
- Files, folders, and naming conventions are **automatically enforced**.  
- Module registration in Gateway is handled by CLI automatically.  

---

## 12. Future Extensions

- Event Bus in Pulse for async messaging  
- Auto-mappers in Bridge  
- Worker-based async Flow execution  
- Plugin hooks for extra module behavior
