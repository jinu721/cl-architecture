# CL-Architecture — CLI Guide

The CL-Architecture CLI is a **core part of the system**.

It exists to:
- Enforce architecture rules
- Generate correct structure
- Remove manual setup
- Keep teams consistent

The CLI is **opinionated by design**.

---

## CLI Philosophy

- Convention over configuration
- Defaults follow best practices
- Less questions, more correctness
- Generated code follows CL rules strictly

If the CLI generates it, it is **CL-compliant**.

---

## CLI Installation Options

You can use the CLI in three ways:

1. npx (no install)
2. Global install
3. Project dependency

All options provide the same commands.

---

## Core Commands

### Initialize a New Project

```bash
npx cl-architecture init
````

This command:

* Creates a new project
* Sets up base folder structure
* Initializes config files
* Prepares DI and gateway setup

---

### Initialize with Options

```bash
npx cl-architecture init -n my-api
```

Create project with a custom name.

```bash
npx cl-architecture init -y
```

Skip all prompts and use defaults.

---

## Create a Module

```bash
npx cl-architecture create module user
```

This creates a **self-contained module** with CL structure.

Generated structure:

```
modules/user/
 ┣━━ port/
 ┣━━ flow/
 ┣━━ source/
 ┣━━ shape/
 ┣━━ bridge/
 ┗━━ rule/
```

---

## Interactive Module Creation

By default, the CLI asks a small set of questions:

```
Include validation? (Y/n)
Include input DTO? (Y/n)
Include response DTO? (Y/n)
Include repository? (Y/n)
Include logger hooks? (Y/n)
Include tests? (Y/n)
Include DI bindings? (Y/n)
```

Defaults are **YES**.

---

## Skip Prompts (Fast Mode)

```bash
npx cl-architecture create module auth -y
```

This generates a module with all recommended options.

---

## What the CLI Generates

For each module, the CLI can generate:

* Controller (Port)
* Routes
* Flow (business logic)
* Source interface and implementation
* Input DTO
* Response DTO
* Validation schema
* Response mapper
* Test stubs
* DI bindings
* Gateway registration

All files follow CL naming rules.

---

## CLI Output Example

```
✔ Project initialized
✔ Module "user" created
✔ Controller generated
✔ Flow generated
✔ Source created
✔ DTOs added
✔ Validation added
✔ Routes registered
✔ DI wired
✔ Tests scaffolded
```

---

## CLI Rules Enforcement

The CLI ensures:

* Controllers stay thin
* Flow has no framework imports
* Source is isolated
* DTOs are separated
* Validation is placed correctly

Manual structure changes are discouraged.

---

## Planned CLI Commands (Future)

```bash
cl create flow CreateUser
cl create source UserSource
cl lint
cl doctor
```

These commands will:

* Generate missing parts
* Validate architecture rules
* Detect violations

---

## CLI Scope (v1)

In version 1.x, the CLI focuses on:

* Project initialization
* Module creation
* Correct wiring
* Consistent structure

Advanced features come in later versions.

---

## Final Note

The CLI is not optional.

Using CL-Architecture without the CLI is possible,
but **using the CLI is strongly recommended** to keep the system correct.
