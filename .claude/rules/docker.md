# Docker Guidelines

## General

- Always use the Official Docker Python SDK.
- Do not execute Docker CLI commands from application code.
- Keep Docker logic inside `docker/` and `services/`.

## Connections

- Support the local Docker Engine.
- Support multiple remote Docker hosts.
- Reuse Docker client connections when possible.

## Services

Create one service per resource, each with a single responsibility:

- Container
- Image
- Network
- Volume
- System

## Error Handling

- Validate inputs before calling the SDK.
- Catch Docker SDK exceptions.
- Raise meaningful application exceptions instead of leaking SDK internals.

## Best Practices

- Prefer SDK APIs over custom implementations.
- Avoid unnecessary Docker API calls.
- Return structured data (Pydantic models / DTOs), not raw SDK objects.
