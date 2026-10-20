<p align="center">
  <img src="docs/assets/pushman-icon.png" alt="Pushman" width="128" height="128">
</p>

<h1 align="center">Pushman</h1>

<p align="center">
  Send push notifications from your terminal, scripts, servers, and AI agents to your iPhone.
</p>

<p align="center">
  <a href="https://pushman.io/">Website</a> ·
  <a href="docs/GETTING_STARTED.md">Get started</a> ·
  <a href="docs/MCP.md">ChatGPT and MCP</a> ·
  <a href="https://github.com/pushmanhq/pushman-cli">CLI source</a> ·
  <a href="https://github.com/pushmanhq/skills">Agent skills</a> ·
  <a href="SUPPORT.md">Support</a>
</p>

```console
$ pushman push "Production deploy finished" --title "Acme API"
Accepted msg_01M0W2RDPVGEVX7D6ZWFK907B2 for 1 device
```

Pushman connects terminals and AI clients to your iPhone. Install the receiving
app, authorize the CLI or connect hosted OAuth, and turn a requested result into
a native notification through the hosted service.

> [!NOTE]
> Pushman is in public beta and free to try. The iPhone app is preparing for its first App Store release; the download badge will appear here when the public listing is available.

## Highlights

- One command for terminals, shell scripts, servers, CI jobs, and local AI agents
- Title, subtitle, body, URL, HTTPS image, sound, group, update key, and monospace presentation
- Browser login or approval from the signed-in iPhone app
- Multiple receiving devices with explicit targeting
- Seven-day synchronized history and delivery diagnostics
- Hosted OAuth MCP for ChatGPT and compatible native clients, plus local stdio MCP
- Native credential storage in the operating-system keyring

## Install the CLI

Homebrew is recommended on macOS and Linux:

```sh
brew install whitekiwi/tap/pushman
export PUSHMAN_API_URL=https://api.pushman.io/v1
pushman login
pushman push "Hello from Pushman"
```

See [Getting Started](docs/GETTING_STARTED.md) for pairing, device selection, updates, and troubleshooting. Source code, release archives, checksums, provenance, and contributor documentation live in [`pushmanhq/pushman-cli`](https://github.com/pushmanhq/pushman-cli).

On Windows, download the x64 or ARM64 installer from [CLI v0.5.0](https://github.com/pushmanhq/pushman-cli/releases/tag/v0.5.0), verify its checksum and build provenance, then install it for your Windows user. Go and administrator access are not required. See the [CLI installation guide](https://github.com/pushmanhq/pushman-cli/blob/main/docs/INSTALL.md) for verification, updates, removal, and the optional ZIP channel. The native `pushman.exe` sends to the iPhone app and also provides local stdio MCP.

## Public interfaces

- [`api/openapi.yaml`](api/openapi.yaml) documents the supported HTTP interface used by the CLI.
- [Hosted OAuth MCP](docs/MCP.md) connects through account consent without a CLI.
- [`pushman mcp`](https://github.com/pushmanhq/pushman-cli/blob/main/docs/MCP.md) exposes 17 local stdio tools for compatible AI clients in CLI v0.5.0.
- The production service is hosted at `https://api.pushman.io/v1`.

Existing CLI releases still default to the previous API origin. Set
`PUSHMAN_API_URL=https://api.pushman.io/v1` in every CLI and local MCP process
until using a release with the updated default, then log in at that endpoint.
Credentials remain separate for each endpoint; the old login is not copied.
Changing the hosted MCP URL requires a new OAuth connection. Existing installed
iPhone apps also retain their compiled endpoint until updated.

The iPhone app and hosted service are maintained as private implementations. Publishing the CLI and public contract does not publish service credentials, mobile signing material, or private operational configuration.

## Free beta

During the initial free release, each account can submit up to 200 accepted push requests per UTC calendar month, plus any current-month support credits. Messages remain available in synchronized history for seven days. See [usage and limit notices](docs/USAGE.md) for counting, reset times, and the quiet limit notification. Future paid plans may change allowances without changing the MIT license of the CLI.

## Support and security

Use [Support](SUPPORT.md) for product help and issue routing. Never post notification content, tokens, OAuth data, pairing codes, account identifiers, or unredacted logs publicly. Report suspected vulnerabilities according to [Security Policy](SECURITY.md).

## Repositories

- [`pushmanhq/pushman`](https://github.com/pushmanhq/pushman) — product documentation, public API, support, and roadmap
- [`pushmanhq/pushman-cli`](https://github.com/pushmanhq/pushman-cli) — open-source CLI, MCP server, packaging, and releases
- [`pushmanhq/skills`](https://github.com/pushmanhq/skills) — maintained skills, hosted OAuth plugin ZIP, and local Codex/Claude marketplaces
- `pushmanhq/pushman-ios` — private iPhone app implementation
- `pushmanhq/pushman-server` — private hosted-service implementation

Documentation and the public API specification in this repository are available under the [MIT License](LICENSE).
