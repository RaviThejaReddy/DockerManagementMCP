# Architecture

## Principles

- SOLID
- KISS
- DRY
- Separation of Concerns
- Dependency Injection
- Modular design

Keep modules small, focused, and loosely coupled.

## High-Level Architecture

```text
                +----------------------+
                |      MCP Client      |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |      MCP Server      |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |      Services        |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |   Docker Clients     |
                +----------+-----------+
                           |
        +------------------+------------------+
        |                                     |
        v                                     v
+----------------------+           +----------------------+
| Local Docker Engine  |           | Remote Docker Hosts  |
+----------------------+           +----------------------+
```

## Request Flow

```text
User → MCP Tool → Service → Docker Client → Docker Engine → Response
```

## Module Responsibilities

### `core/`

Shared infrastructure: configuration, logging, security, exception handling,
dependency injection, common utilities.

### `docker/`

Docker connectivity: client creation, local connection, remote connections,
connection management.

### `services/`

Business logic for Docker operations (container, image, network, volume,
system). Each service should:

- Validate inputs
- Execute Docker SDK operations
- Return structured results
- Raise meaningful exceptions

### `monitoring/`

Runtime information: container statistics, resource usage, health status,
Docker events.

### `mcp/`

MCP server implementation: server setup, tool registration, tool handlers,
request routing, service orchestration. Keep handlers thin by delegating
business logic to services.

### `shared/`

Reusable components: models, DTOs, enums, constants, validators, helpers.

## Development Guidelines

- Use Python type hints throughout.
- Use the Official Docker Python SDK instead of shell commands.
- Support local and multiple remote Docker engines.
- Keep Docker operations isolated within service modules.
- Avoid duplicated code.
- Do not hardcode configuration.
- Never expose secrets in logs.
- Handle errors with meaningful exceptions.

## Design Goals

Simple, readable code · modular architecture · easy to test · easy to extend
· secure by default · production-ready foundation.
