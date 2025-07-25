# Testing Rules: Pytest

- **Test Runner:** Pytest (`pytest`).
- **File Naming:** Test files must be prefixed with `test_`.
- **Function Naming:** Test functions must be prefixed with `test_`.
- **Fixtures:** Use `@pytest.fixture` to provide dependencies and test data.
- **Mocking:** Use the `pytest-mock` plugin (the `mocker` fixture).
- **Assertions:** Use plain `assert` statements.
