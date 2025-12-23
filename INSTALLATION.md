# CL-Architecture — Installation Guide

This document explains how to install and start using **CL-Architecture**.

---

## System Requirements

Before installing, make sure you have:

- **Node.js** version 18 or higher
- **npm** version 9 or higher

For Go projects:
- **Go** version 1.20 or higher

---

## Installation Methods

CL-Architecture can be used in three different ways.

All methods provide the same CLI features.

---

## Option 1: npx (Recommended)

No installation required.

```bash
npx cl-architecture init
````

Use this if you:

* Want to try CL quickly
* Do not want global installs

---

## Option 2: Global Installation

Install the CLI globally:

```bash
npm install -g cl-architecture
```

Then use:

```bash
cl init
cl create module user
```

Use this if you:

* Use CL often
* Prefer short commands

---

## Option 3: Project Dependency

Install as a dev dependency:

```bash
npm install -D cl-architecture
```

Then use:

```bash
npx cl create module auth
```

Use this if you:

* Want version control per project
* Work in teams

---

## Creating a New Project

```bash
npx cl-architecture init
```

This command:

* Creates a new project folder
* Sets up base structure
* Initializes config files
* Prepares dependency injection

---

## Create a Project with Options

```bash
npx cl-architecture init -n my-api
```

Create a project with a custom name.

```bash
npx cl-architecture init -y
```

Skip all prompts and use defaults.

---

## Verifying Installation

After initialization, your project should contain:

```
src/
 ┣━━ pulse/
 ┣━━ orbit/
 ┣━━ gateway/
 ┣━━ modules/
 ┗━━ test/
```

If this structure exists, installation is successful.

---

## Next Steps

After installation:

1. Create your first module
2. Add routes and controllers
3. Implement business logic in Flow
4. Connect data sources
5. Run and test the application

---

## Troubleshooting

If commands fail:

* Check Node.js version
* Clear npm cache
* Retry using npx

---

## Final Note

CL-Architecture does not run your server.

You still choose:

* Express / Fastify (Node.js)
* Gin / net/http (Go)

CL only controls **how your code is structured**.
