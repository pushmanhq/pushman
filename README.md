<p align="center">
  <img src="docs/assets/pushman-icon.png" alt="Pushman" width="128" height="128">
</p>

<h1 align="center">Pushman</h1>

<p align="center">
  Send push notifications from your terminal, scripts, servers, and AI agents to your iPhone.
</p>

<p align="center">
  <a href="https://app.pushman.whitekiwi.link/">Website</a> ·
  <a href="docs/GETTING_STARTED.md">Get started</a> ·
  <a href="https://github.com/pushmanhq/pushman-cli">CLI source</a> ·
  <a href="SUPPORT.md">Support</a>
</p>

```console
$ pushman push "Production deploy finished" --title "Acme API"
Accepted msg_01M0W2RDPVGEVX7D6ZWFK907B2 for 1 device
```

Pushman is a personal push harness for the command line. Install the iPhone app, authorize the CLI once, and turn a command result into a native notification without running your own notification gateway.

> [!NOTE]
> Pushman for iPhone is preparing for its first App Store release. The download badge will appear here when the public listing is available.

## Highlights

- One command for terminals, shell scripts, servers, CI jobs, and local AI agents
- Title, subtitle, body, URL, HTTPS image, sound, group, update key, and monospace presentation
- Browser login or approval from the signed-in iPhone app
- Multiple receiving devices with explicit targeting
- Seven-day synchronized history and delivery diagnostics
- A local stdio MCP server for compatible agent clients
- Native credential storage in the operating-system keyring

## Install the CLI

Homebrew is recommended on macOS and Linux:

```sh
brew install whitekiwi/tap/pushman
pushman login
pushman push "Hello from Pushman"
```

See [Getting Started](docs/GETTING_STARTED.md) for pairing, device selection, updates, and troubleshooting. Source code, release archives, checksums, provenance, and contributor documentation live in [`pushmanhq/pushman-cli`](https://github.com/pushmanhq/pushman-cli).

## Public interfaces

- [`api/openapi.yaml`](api/openapi.yaml) documents the supported HTTP interface used by the CLI.
- [`pushman mcp`](https://github.com/pushmanhq/pushman-cli/blob/main/docs/MCP.md) exposes local stdio tools for compatible AI clients.
- The production service is hosted at `https://api.pushman.whitekiwi.link/v1`.

The iPhone app and hosted service are maintained as private implementations. Publishing the CLI and public contract does not publish service credentials, mobile signing material, or private operational configuration.

## Free beta

During the initial free release, each account can submit up to 200 accepted push requests per calendar month. Messages remain available in synchronized history for seven days. Future paid plans may change allowances without changing the MIT license of the CLI.

## Support and security

Use [Support](SUPPORT.md) for product help and issue routing. Never post notification content, tokens, OAuth data, pairing codes, account identifiers, or unredacted logs publicly. Report suspected vulnerabilities according to [Security Policy](SECURITY.md).

## Repositories

- [`pushmanhq/pushman`](https://github.com/pushmanhq/pushman) — product documentation, public API, support, and roadmap
- [`pushmanhq/pushman-cli`](https://github.com/pushmanhq/pushman-cli) — open-source CLI, MCP server, packaging, and releases
- `pushmanhq/pushman-ios` — private iPhone app implementation
- `pushmanhq/pushman-server` — private hosted-service implementation

Documentation and the public API specification in this repository are available under the [MIT License](LICENSE).
