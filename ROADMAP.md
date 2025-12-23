# CL-Architecture — Roadmap

This document outlines the planned evolution of **CL-Architecture**.

The roadmap focuses on **stability first**, then **tooling**, then **advanced enforcement**.

---

## Versioning Strategy

CL-Architecture follows **Semantic Versioning**:

- **Patch (x.y.Z)** → bug fixes
- **Minor (x.Y.z)** → new features, backward compatible
- **Major (X.y.z)** → breaking changes

---

## v1.x — Foundation (Current)

### Goals
- Establish core architecture rules
- Provide a reliable CLI
- Support TypeScript and Go
- Avoid framework lock-in

### Features
- Project initialization
- Module generation
- Standard folder structure
- Controller, Flow, Source separation
- DTO rules
- Validation placement
- Logging and error handling structure
- Manual and Inversify-style DI support
- Interactive CLI prompts
- `-y` fast mode

### Non-Goals
- No runtime framework
- No magic decorators
- No opinionated HTTP server
- No heavy abstractions

---

## v1.1 — CLI Improvements

### Planned
- Better CLI error messages
- Improved prompts
- Configurable defaults
- Safer overwrite detection

---

## v1.2 — Validation & Linting

### Planned
- `cl lint` command
- Detect layer violations
- Validate module structure
- Check forbidden imports

---

## v1.3 — Code Generation Enhancements

### Planned
- Generate individual flows
- Generate sources and repositories
- Generate DTOs independently
- Regenerate missing files safely

---

## v2.0 — Enforcement & Intelligence

### Planned
- Architecture doctor (`cl doctor`)
- Rule violation reports
- Optional CI integration
- Architecture health checks
- Improved Go support

### Breaking Changes Expected
- Stricter CLI enforcement
- Mandatory config file
- Reduced customization options

---

## Long-Term Vision

CL-Architecture aims to become:

- A trusted backend architecture standard
- A reference for clean backend design
- A bridge between TypeScript and Go ecosystems
- A tool that prevents architecture decay

---

## Contribution Direction

Future contributions should focus on:
- Improving CLI stability
- Enhancing documentation
- Adding safe enforcement tools
- Providing real-world examples

---
