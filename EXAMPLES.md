# CL-Architecture — Examples

This document shows **simple, real examples** of how CL-Architecture looks in practice.

Examples are provided for:
- TypeScript (Node.js)
- Go

The goal is to show **flow and structure**, not full apps.

---

## Example 1: TypeScript (Node.js)

### Feature: Create User

---

### Folder Structure

```

modules/user/
┣━━ port/
│   ┣━━ user.controller.ts
│   ┗━━ user.routes.ts
┣━━ flow/
│   ┗━━ create-user.flow.ts
┣━━ source/
│   ┣━━ user.source.ts
│   ┗━━ user.repository.ts
┣━━ bridge/
│   ┣━━ create-user.input.ts
│   ┣━━ user.response.ts
│   ┗━━ user.mapper.ts
┣━━ rule/
│   ┗━━ create-user.rule.ts
┗━━ shape/
┗━━ user.entity.ts

````

---

### Route (Context Only)

```ts
// user.routes.ts
router.post("/", createUserController);
````

---

### Controller (Port)

```ts
// user.controller.ts
export const createUserController = asyncHandler(async (req, res) => {
  const input = CreateUserRule.parse(req.body);
  const user = await createUserFlow.execute(input);
  return success(res, toUserResponse(user), "User created");
});
```

---

### Validation (Rule)

```ts
// create-user.rule.ts
export const CreateUserRule = z.object({
  email: z.string().email(),
  password: z.string().min(8),
});
```

---

### Flow (Business Logic)

```ts
// create-user.flow.ts
export class CreateUserFlow {
  constructor(private userSource: IUserSource) {}

  async execute(input: CreateUserInput) {
    return this.userSource.create(input);
  }
}
```

---

### Source (Data Access)

```ts
// user.source.ts
export interface IUserSource {
  create(input: CreateUserInput): Promise<User>;
}
```

```ts
// user.repository.ts
export class UserRepository implements IUserSource {
  async create(input) {
    return db.user.create({ data: input });
  }
}
```

---

### Response Mapping (Bridge)

```ts
// user.mapper.ts
export const toUserResponse = (user) => ({
  id: user.id,
  email: user.email,
});
```

---

## Example 2: Go

### Feature: Create User

---

### Folder Structure

```
user/
 ┣━━ port/
 │   ┗━━ handler.go
 ┣━━ flow/
 │   ┗━━ create_user.go
 ┣━━ source/
 │   ┗━━ repository.go
 ┣━━ bridge/
 │   ┗━━ dto.go
 ┣━━ rule/
 │   ┗━━ validation.go
 ┗━━ shape/
     ┗━━ entity.go
```

---

### Handler (Port)

```go
func CreateUserHandler(flow *CreateUserFlow) http.HandlerFunc {
  return func(w http.ResponseWriter, r *http.Request) {
    input := ParseAndValidate(r)
    user, err := flow.Execute(input)
    if err != nil {
      HandleError(w, err)
      return
    }
    WriteSuccess(w, MapToResponse(user))
  }
}
```

---

### Flow (Business Logic)

```go
type CreateUserFlow struct {
  repo UserRepository
}

func (f *CreateUserFlow) Execute(input CreateUserInput) (User, error) {
  return f.repo.Create(input)
}
```

---

### Source (Repository)

```go
type UserRepository interface {
  Create(input CreateUserInput) (User, error)
}
```

---

### Key Takeaways from Examples

* Controllers/Handlers are thin
* Validation happens before Flow
* Flow contains business logic only
* Source handles data access
* DTOs protect boundaries
* Same rules apply to TS and Go


