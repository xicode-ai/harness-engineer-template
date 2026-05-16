# TDD Adapter: Python

## Detection

- `pyproject.toml`
- `requirements.txt`
- `setup.py`

## Test Strategy

- Prefer existing pytest or unittest conventions.
- Place tests under existing `tests/` layout.
- Use fixtures consistent with the repository.

## Commands

- Focused pytest: `python -m pytest tests/path/test_file.py::test_name -q`
- Regression pytest: `python -m pytest`

## Review Risks

- Global state between tests.
- Environment-dependent tests.
- Mocking implementation details instead of behavior.
