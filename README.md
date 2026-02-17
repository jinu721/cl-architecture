# CL-Architecture (Core-Line Architecture)

**The Universal Standard for High-Performance Backend Engineering.**

CL-Architecture is not just a folder structure—it is a **Discipline-First Backend Standard** designed to eliminate technical debt, enforce linear execution, and guarantee scale. It transforms your development process from "freestyle coding" into a professional, industrial-grade engineering protocol.

---

## The Core-Line Philosophy

Most backend systems decay because logic leaks across layers. CL-Architecture stops this by enforcing the **Core-Line**: a single, non-negotiable path that every request must follow.

```
Route → Port (Controller) → Flow (Service) → Source (Repository) → Flow → Response
```

No shortcuts. No cross-layer calls. No hidden complexity.

---

## Why CL-Architecture?

### 1. Total Execution Discipline
The "Core-Line" rule ensures that you always know exactly where code belongs. 
*   **Port**: I/O Handling only.
*   **Flow**: Pure Business Logic only.
*   **Source**: Data Persistence only.
*   **Link**: External SDK Isolation only (Vendor Neutrality).

### 2. Zero-Trust Engineering
CL-Architecture protects the codebase from the developer.
*   **Automated Git Hooks**: The CLI installs pre-commit and commit-msg hooks to enforce linting and Conventional Commits.
*   **Rule Enforcement**: Architecture rules are checked automatically. If the code breaks the "Core-Line," it cannot be committed.

### 3. Vendor Neutrality (Isolation)
Never be trapped by a library again. Every third-party SDK (JWT, Stripe, Mailers) is isolated in the **Link** layer. Changing a vendor requires zero changes to your business logic.

### 4. Professional Git Strategy
Every CL project follows **Rule 13 (Atomic Commits)** and a strict **Main/Dev Branching** model. Your repository history becomes a searchable, professional chronological log of your engineering decisions.

---

## Quick Start

### 1. Initialize Modern Architecture
```bash
npx cl-architecture init --naming=custom
```
*Choose between **Core-Line Custom** (Port/Flow/Source/Link) or **Industry Standard** (Controller/Service/Repository/Provider).*

### 2. Generate a Module
```bash
npx cl-architecture create module user
```

---

## Global Compatibility

CL-Architecture is **Language-Agnostic** and works seamlessly with:
*   **Node.js / TypeScript** (Express, Fastify, NestJS)
*   **Go** (Standard Lib, Gin, Fiber)
*   **Python** (FastAPI, Django)
*   **Java / C#** (Spring Boot, .NET Core)

---

## Deep Dive Documentation

*   [INTRODUCTION.md](docs/INTRODUCTION.md) — The Core Concepts
*   [RULES.md](docs/RULES.md) — The Non-Negotiable Laws
*   [CLI.md](docs/CLI.md) — The Automation Guide
*   [ECOSYSTEM.md](docs/ECOSYSTEM.md) — Language & Framework Adaptation
*   [COMPARISON.md](docs/COMPARISON.md) — CL vs. Clean Architecture & Repo Pattern
*   [EXAMPLES.md](docs/EXAMPLES.md) — Real-world code samples

---

## The Final Note

CL-Architecture is a discipline. 
**Follow the rules → The system scales.**
**Break the rules → The architecture fails.**

Built for engineers who value precision over speed, and quality over shortcuts.
