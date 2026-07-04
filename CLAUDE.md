# DockerOps MCP

Enterprise-grade Docker Engine **MCP server** written in **Python**, for securely managing local and multiple remote Docker environments with AI-assisted diagnostics, governance, monitoring, and automation.

## Tech Stack

- Python 3.12+
- Official Docker Python SDK
- Official MCP Python SDK
- uv (dependency & environment management)
- pytest, Ruff, mypy, Pydantic

## Project Structure

```
src/
├── core/        # config, logging, security, DI, exceptions
├── docker/      # Docker client creation & connection management (local + remote)
├── services/    # business logic: container, image, network, volume, system
├── monitoring/  # container stats, health checks, Docker events
├── mcp/         # MCP server, tool registration, request routing
└── shared/      # models, DTOs, enums, constants, validators, helpers
```

## Common Commands

- `uv sync` — install dependencies
- `uv run pytest` — run the test suite
- `uv run ruff check .` — lint
- `uv run ruff format .` — format
- `uv run mypy src` — type check

## Golden Rules

- **IMPORTANT**: Use the Docker Python SDK for all Docker operations — never shell out to the Docker CLI.
- **IMPORTANT**: Never log or hardcode secrets, tokens, SSH keys, or credentials.
- Follow SOLID, KISS, DRY, and separation of concerns; keep modules small, focused, and loosely coupled.
- Keep MCP tool handlers thin — delegate all business logic to `services/`.
- Validate every input before performing a Docker operation.
- Every bug fix ships with a regression test.
- A task isn't done until Ruff, mypy, and pytest all pass.

## Detailed Guidance

@.claude/rules/architecture.md
@.claude/rules/coding.md
@.claude/rules/docker.md
@.claude/rules/security.md
@.claude/rules/testing.md

## Roadmap

@docs/roadmap.md
