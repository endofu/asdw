# Coding Patterns: Effect-TS

- **Error Handling:** All fallible operations MUST return an `Effect.Effect<A, E, R>`. Do not use `try/catch` blocks for business logic; use `Effect.try`, `Effect.catch`, etc.
- **Dependency Injection:** Use `Layer` to provide services and dependencies. Avoid direct instantiation of classes.
- **Concurrency:** Use Effect's built-in concurrency primitives (`Fiber`, `Effect.fork`, `Effect.all`) instead of raw Promises.
- **State Management:** Application state should be managed within Effect services where possible.
