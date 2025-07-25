# Testing Rules: Vitest

- **Test Runner:** Vitest (`vitest` or `bun test`).
- **File Naming:** Test files must end in `.test.ts` or `.spec.ts`.
- **Location:** Test files should be co-located with the source files they are testing.
- **Mocking:** Use `vi.mock()` for mocking modules and dependencies.
- **Assertions:** Use the built-in `expect` assertion library.
