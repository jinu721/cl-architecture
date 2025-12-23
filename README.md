# CL-Architecture (Core-Line Architecture)

A strict, production-ready backend architecture for clarity, control, and scale.

---

## What is CL-Architecture?

**CL-Architecture (Core-Line Architecture)** is a backend architecture **standard**, not a framework.

It defines clear rules for how backend code should be structured, written, and connected so teams can build scalable systems without chaos.

It works with:
- **TypeScript / Node.js (MERN backends)**
- **Go (REST APIs, services, microservices)**

---

## Why CL-Architecture?

Most backend projects become hard to maintain because of:

- Fat controllers
- Business logic mixed with database logic
- Validation scattered across layers
- Inconsistent DTOs and responses
- Weak production logging
- Poor dependency injection
- No shared rules across teams

CL-Architecture solves these problems by enforcing structure, discipline, and automation.

---

## Core Idea: The Core Line

Every request follows one clear, linear path:

```

Route → Controller (Port) → Flow → Source → Flow → Response

````

No shortcuts.  
No cross-layer calls.  
No hidden logic.

---

## What CL-Architecture Gives You

- Modular, self-contained features
- Clear separation of concerns
- Thin and clean controllers
- Input and output DTO rules
- Centralized validation
- Production-ready logging
- Proper dependency injection
- CLI-driven consistency

---

## Is This a Framework?

No.

CL-Architecture:
- Does not replace Express, Fastify, or Gin
- Does not use decorators or magic
- Does not lock you into a runtime

It is a discipline-first backend architecture standard.

---

## Getting Started

### Initialize a new project

```bash
npx cl-architecture init
````

### Create a module

```bash
npx cl-architecture create module user
```

---

## How People Use It

### Option 1: npx (no install)

```bash
npx cl-architecture init
npx cl-architecture create module auth
```

### Option 2: Global install

```bash
npm install -g cl-architecture
cl init
cl create module user
```

### Option 3: Project dependency

```bash
npm install -D cl-architecture
npx cl create module payment
```

---

## Documentation

* `docs/INTRODUCTION.md` — Architecture concepts
* `docs/RULES.md` — Architecture rules
* `docs/CLI.md` — CLI commands
* `docs/INSTALLATION.md` — Setup guide
* `docs/EXAMPLES.md` — TypeScript and Go examples

---

## When to Use CL-Architecture

Best for:

* Medium to large backend projects
* Long-term systems
* Team-based development
* Production environments

Not recommended for:

* Small scripts
* Quick prototypes
* One-file APIs

---

## Final Note

CL-Architecture works only if the rules are followed.

Break the rules → architecture breaks
Follow the rules → system scales

