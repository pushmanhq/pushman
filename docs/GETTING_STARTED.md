# Getting started

Pushman requires the iPhone app and the `pushman` command-line client. The iPhone app is preparing for its first public App Store release.

## 1. Install the CLI

Homebrew is recommended on macOS and Linux:

```sh
brew install whitekiwi/tap/pushman
pushman version
```

Other verified installation methods are documented in the [CLI installation guide](https://github.com/pushmanhq/pushman-cli/blob/main/docs/INSTALL.md).

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

## 4. Inspect and manage access

```sh
pushman status
pushman devices
pushman history
pushman usage
pushman doctor
```

Run `pushman logout` to revoke the current CLI and remove its local credential. Removing the executable alone does not revoke an authorization.

The current beta iPhone inbox starts with the newest 20 messages and loads more as you scroll. Refresh returns to the newest page; a failed next page keeps existing messages visible and offers a retry. See [usage and limit notices](USAGE.md) for monthly counting and reset behavior.

## Updates

Homebrew installations can update safely with:

```sh
pushman self-update
```

The command only updates an executable owned by the official Pushman Homebrew formula. Go and archive installations must be updated using their original installation method.

## AI clients

After authorizing the CLI, expose Pushman over local stdio:

```sh
codex mcp add pushman -- pushman mcp
# or
claude mcp add --scope user pushman -- pushman mcp
```

Sending changes external state and consumes the account allowance. Agent clients should request confirmation unless the user explicitly supplied the exact notification to send.

## Troubleshooting

Start with:

```sh
pushman doctor
```

Share only the CLI or app version, operating system, visible error code, expected result, and redacted output. Follow [Support](../SUPPORT.md) for the correct reporting channel.
