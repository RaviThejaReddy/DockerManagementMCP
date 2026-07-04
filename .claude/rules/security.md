# Security

## General

- Never expose secrets.
- Never hardcode credentials.
- Validate all inputs.
- Use secure defaults.

## Docker

- Validate all Docker operations before executing them.
- Restrict destructive actions when required (e.g. force-remove, prune).
- Use least-privilege access for remote hosts.

## Logging

Never log:

- Passwords
- Tokens
- SSH keys
- Any other secret

## Configuration

- Load configuration from environment variables or config files.
- Keep secrets outside source control (never commit `.env`, keys, or certs).

## Code Review

Before merging, confirm:

- Security implications have been reviewed.
- Input validation is present.
- Sensitive information is protected.
