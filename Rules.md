# CL-Architecture — Rules & Guarantees

This document defines the **non-negotiable rules** of CL-Architecture.

These rules exist to:
- Prevent architecture decay
- Enforce consistency across teams
- Keep code clean as the system grows

If these rules are broken, **CL-Architecture is not being used correctly**.

---

## 1. Core-Line Rule (MANDATORY)

Every request must follow this exact flow:

```

Route
→ Controller (Port)
→ Flow (Business Logic)
→ Source (DB / External APIs)
→ Flow
→ Response

````

### Forbidden:
- Controller calling Source
- Flow accessing request/response objects
- Source calling Flow
- Skipping layers

---

## 2. Layer Responsibilities (STRICT)

Each layer has **one job only**.

### Port (Controller)
- Read request data
- Call Flow
- Return standardized response

❌ No business logic  
❌ No DB logic  
❌ No try/catch  
❌ No response formatting  

---

### Flow (Business Logic)
- Contains application rules
- Coordinates operations
- Uses interfaces only

❌ No HTTP logic  
❌ No DB queries  
❌ No framework code  

---

### Source (Data Access)
- Database operations
- External API calls
- Cache access

❌ No business decisions  
❌ No request handling  

---

### Shape (Domain)
- Domain models
- Entities
- Core data structures

❌ No logic  
❌ No framework imports  

---

### Bridge (DTO & Mapping)
- Input DTOs
- Output DTOs
- Data transformation

❌ No business logic  

---

### Rule (Validation)
- Request validation
- Input schemas

❌ No business rules  

---

### Pulse (Core Systems)
- Logger
- Error handling
- Events
- Monitoring

Shared across all modules.

---

### Orbit (Configuration)
- Environment variables
- App config
- Constants

No logic allowed.

---

### Gateway (Bootstrap)
- App startup
- Dependency injection wiring
- Module registration

All wiring happens here.

---

## 3. Controller Rules (VERY IMPORTANT)

Controllers must be:
- Thin
- Predictable
- Repeatable

Controllers do ONLY:
1. Read input
2. Call Flow
3. Return response

---

## 4. Async Handler Rule (DRY)

All controllers must use a **single async handler**.

```ts
export const asyncHandler =
  (fn) =>
  (req, res, next) =>
    Promise.resolve(fn(req, res, next)).catch(next);
````

No try/catch blocks in controllers.

---

## 5. Response Rules

### Success Response

* One global success format
* Same shape everywhere

```ts
{
  success: true,
  message: string,
  data: any
}
```

---

### Error Handling

* One global error handler
* Clean message to client
* Full error logged internally

Never expose stack traces to users.

---

## 6. DTO Rules (MANDATORY)

CL-Architecture enforces **three DTO types**:

| DTO Type     | Purpose            |
| ------------ | ------------------ |
| Input DTO    | Request validation |
| Flow DTO     | Business input     |
| Response DTO | API output         |

Rules:

* Flow never receives raw request data
* Flow never returns DB models
* Controllers never touch domain objects

---

## 7. Validation Rules

* Validation happens **before Flow**
* Validation lives in Rule layer
* Flow trusts validated data

No duplicate validation inside Flow.

---

## 8. Response Mapping Rules

* Never return DB entities directly
* Always map to Response DTO
* Mapping belongs to Bridge layer

This prevents:

* Data leaks
* Breaking API changes
* Security issues

---

## 9. Logging Rules (Production)

* No `console.log`
* Structured logs only
* Request ID included
* Log level based on environment

Logger is provided by Pulse layer.

---

## 10. Dependency Injection Rules

* No `new` inside Flow
* Flow depends on interfaces
* Concrete implementations wired in Gateway

Allowed:

* Manual DI
* Inversify-style DI

Not allowed:

* Service locators
* Hidden containers

---

## 11. Route Rules

* Routes belong to module context
* Routes only define paths
* No logic inside routes

Routes connect HTTP to Controllers only.

---

## 12. What CL-Architecture Guarantees

If rules are followed, you get:

* Clean controllers
* Stable business logic
* Replaceable data sources
* Safe refactoring
* Easy testing
* Consistent APIs
* Team-wide discipline

