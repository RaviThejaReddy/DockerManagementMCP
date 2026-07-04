# Coding Standards

## General

- Python 3.12+
- Follow SOLID, KISS, and DRY.
- Write readable code over clever code.

## Style

- Use type hints everywhere.
- Keep functions small and focused.
- Keep classes focused on one responsibility.
- Prefer composition over inheritance.

## Naming

- Use descriptive names.
- `snake_case` for functions and variables.
- `PascalCase` for classes.
- `UPPER_CASE` for constants.

## Structure

- Organize code by feature, not by layer-only.
- Avoid circular dependencies.
- Keep business logic inside `services/`, never inside MCP handlers.

## Quality Gate

Before committing or considering a task done:

- `uv run ruff check .` passes
- `uv run mypy src` passes
- `uv run pytest` passes
- No duplicated code
