# Getting started

Pushman requires the iPhone app and the `pushman` command-line client. The iPhone app is preparing for its first public App Store release.

## 1. Install the CLI

Homebrew is recommended on macOS and Linux:

```sh
brew install whitekiwi/tap/pushman
pushman version
```

Other verified installation methods are documented in the [CLI installation guide](https://github.com/pushmanhq/pushman-cli/blob/main/docs/INSTALL.md).

On Windows, choose the x64 or ARM64 setup installer from [CLI v0.4.2](https://github.com/pushmanhq/pushman-cli/releases/tag/v0.4.2). Verify its exact SHA-256 entry and GitHub build provenance before running it. The installer adds an Installed apps entry and offers to add the CLI to your user PATH; open a new terminal after installation. Neither Go nor administrator access is required. The installers are currently unsigned, so Windows may show a publisher or SmartScreen warning. Follow the [CLI installation guide](https://github.com/pushmanhq/pushman-cli/blob/main/docs/INSTALL.md) for verification and installation discovery with `Get-Command pushman.exe -All`. ZIP installation remains available. Windows support here means sending to the iPhone app, not a Windows notification receiving app.

## 2. Authorize this machine

Use browser-assisted login on a personal terminal:

```sh
pushman login
```

Use `pushman login --no-browser` over SSH. It prints a short-lived code and verification URL without trying to open a local browser.

Alternatively, approve the CLI from an already signed-in iPhone:

```sh
pushman pair
```

Both methods create an account-scoped sender authorization stored in the operating-system keyring. They do not expose your Apple or Google credential to the CLI.

## 3. Send a notification

```sh
pushman push "Database backup completed"
pushman push "Deploy completed" --title "Production" --url "https://example.com/runs/42"
printf '%s\n' "Build failed" | pushman push --title "CI"
```

Use `pushman help push` for every supported notification field. Use `--json` for automation and `--quiet` when only the exit status matters.

For non-ASCII piped bodies in a Windows PowerShell 5.1 console, align `$OutputEncoding` and console input encoding to UTF-8 for the operation, then restore them as shown in the [CLI installation guide](https://github.com/pushmanhq/pushman-cli/blob/main/docs/INSTALL.md). PowerShell 7 uses UTF-8 native pipelines. For `cmd.exe`, redirect a UTF-8 body file with `pushman.exe push - --json < body.txt`. Quote URL arguments containing `&`.

## 4. Inspect and manage access

```sh
pushman status
pushman devices
pushman history
pushman usage
pushman doctor
```

Run `pushman logout` to revoke the current CLI and remove its local credential. Removing the executable alone does not revoke an authorization.

In CLI v0.3.0 and later, `pushman history show <message-id>` displays message revisions newest first. Revision numbers and the API/MCP machine-readable order are unchanged. Reusing `--key` updates one logical message and retains its revision history; `--group` groups system notifications but does not merge messages in the app's inbox.

The current beta iPhone inbox starts with the newest 20 messages and loads more as you scroll. Refresh returns to the newest page; a failed next page keeps existing messages visible and offers a retry. See [usage and limit notices](USAGE.md) for monthly counting and reset behavior.

## Updates

Homebrew installations can update safely with:

```sh
pushman self-update
```

The command only updates an executable owned by the official Pushman Homebrew formula. Go and archive installations must be updated using their original installation method.

On Windows, stop running CLI/MCP processes, verify the newer setup installer, run it against the same installation, then check `version` in a new terminal. A previously verified installer can restore an earlier version. Remove Pushman CLI through Windows Installed apps; removal retains account authorization, so run `logout` first if you also want to revoke it. ZIP and Go installations use their original update/removal method. `self-update` does not update Windows installations.

The current release is [CLI v0.4.2](https://github.com/pushmanhq/pushman-cli/releases/tag/v0.4.2), with macOS/Linux archives, Windows ZIPs and installers, checksums and build provenance. Go installations use the canonical module path:

```sh
go install github.com/pushmanhq/pushman-cli/cmd/pushman@v0.4.2
```

Contributors should use the isolated `pushman-dev` / `pdev` build described in the [contributing guide](https://github.com/pushmanhq/pushman-cli/blob/main/CONTRIBUTING.md), keeping development credentials and endpoints separate from the installed client.

## AI clients

After authorizing the CLI, expose Pushman over local stdio:

```sh
codex mcp add pushman -- pushman mcp
# or
claude mcp add --scope user pushman -- pushman mcp
```

Sending changes external state and consumes the account allowance. Agent clients should request confirmation unless the user explicitly supplied the exact notification to send.

For a Windows desktop client, use the absolute path from `(Get-Command pushman.exe).Source`, JSON-escape its backslashes, and set `args: ["mcp"]`. Restart the desktop client after PATH changes. The [MCP guide](https://github.com/pushmanhq/pushman-cli/blob/main/docs/MCP.md) includes configuration examples. Run the host under the Windows identity/session that authorized the CLI; a process-scoped automation token permits sending but does not grant MCP read access.

## Troubleshooting

Start with:

```sh
pushman doctor
```

Share only the CLI or app version, operating system, visible error code, expected result, and redacted output. Follow [Support](../SUPPORT.md) for the correct reporting channel.
