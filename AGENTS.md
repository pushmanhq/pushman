# AGENTS.md

## Scope

- This public repository is Pushman's product home, public documentation, support surface, and published API contract.
- Document only externally supported behavior. Keep private implementation details, credentials, infrastructure, review material, and unreleased plans out of this repository.
- Product design and unreleased implementation decisions are maintained in the private `pushmanhq/pushman-internal` repository.
- CLI implementation changes belong in `pushmanhq/pushman-cli`.

## Documentation

- Keep the README concise and task-oriented.
- Update public documentation and `api/openapi.yaml` when a supported interface changes.
- Prefer stable website and repository links over local paths or internal repository references.
- Never include tokens, message content, account identifiers, private logs, signing material, or production infrastructure details.

## Git

- Commit messages must use `{type}: {message}`.
- Keep the `type` lowercase and concise.
- Write the `message` as an imperative, specific summary.
- Inspect staged and unstaged changes before every commit.
