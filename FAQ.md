# CL-Architecture — Frequently Asked Questions

---

## Is CL-Architecture a framework?

No.

CL-Architecture is an **architecture standard**, not a framework.

You still choose:
- Express / Fastify (Node.js)
- Gin / net/http (Go)

CL only controls **how your code is structured and how logic flows**.

---

## Can I use CL-Architecture with NestJS?

Technically yes, but it is **not recommended**.

NestJS already enforces its own architecture using decorators and modules.  
CL-Architecture is designed to be **framework-agnostic and explicit**.

Using both together adds unnecessary complexity.

---

## Is CL-Architecture only for large projects?

No, but it shines most in:
- Medium to large projects
- Long-term systems
- Team environments

For very small scripts or quick prototypes, CL may feel heavy.

---

## Do I have to use the CLI?

You can use CL without the CLI, but it is **strongly recommended**.

The CLI:
- Enforces correct structure
- Prevents rule violations
- Saves setup time
- Keeps teams consistent

Manual setup increases the risk of breaking rules.

---

## Can I customize folder names or layers?

No.

CL-Architecture is **opinionated by design**.

Changing names or layers breaks:
- CLI automation
- Team consistency
- Architecture guarantees

If you need full freedom, CL is not the right choice.

---

## How is this different from Clean Architecture?

Clean Architecture:
- Explains principles
- Leaves structure open

CL-Architecture:
- Enforces exact structure
- Defines strict rules
- Provides automation

CL can be seen as **Clean Architecture with discipline and tooling**.

---

## How is this different from MVC?

MVC:
- Allows logic to leak into controllers and models
- Has no strict enforcement

CL-Architecture:
- Enforces linear flow
- Prevents cross-layer calls
- Keeps controllers thin

---

## Can I use any database or ORM?

Yes.

CL-Architecture does not care about:
- SQL or NoSQL
- Prisma, TypeORM, GORM
- Raw queries or ORMs

All data access stays inside the **Source layer**.

---

## Does CL support microservices?

Yes.

CL-Architecture works well for:
- Monoliths
- Modular monoliths
- Microservices

Each service follows the same rules and structure.

---

## Is CL suitable for Go?

Yes.

CL-Architecture fits Go very well because:
- Go prefers explicit code
- Go avoids magic
- Go teams value clear structure

Same rules, different syntax.

---

## What happens if rules are broken?

If rules are broken:
- Architecture guarantees are lost
- Code becomes harder to maintain
- CLI checks may fail (future versions)

CL is strict by design.

---

## Who should NOT use CL-Architecture?

CL may not be a good fit if:
- You prefer flexible or experimental structures
- You want heavy framework features
- You are building very small, throwaway code

---

## Final Answer

CL-Architecture is for teams that value:
- Discipline
- Clarity
- Long-term maintainability

If that matches your goals, CL is a strong choice.
