# Usage and limit notices

The Free beta includes 200 accepted sends per account per UTC calendar month. All authorized CLIs share that allowance. Run `pushman usage` to see current usage, the effective allowance, and the reset time.

- One accepted send counts once, even when it targets multiple receiving devices.
- An accepted update using `--key` counts as another send.
- Requests rejected before acceptance do not count. Acceptance is not a guarantee that iOS displayed the notification.
- The counter resets at 00:00 UTC on the first day of the month (09:00 in Korea).
- Support credits, when granted, increase that month's allowance without resetting usage. They expire at the next monthly reset.

## When the allowance is reached

Further sends are rejected until capacity is available again. Pushman attempts one silent service notification per eligible device for that account and month. It uses no sound or badge, consumes no allowance, and is not added to message history. Delivery is best effort and depends on iOS notification permissions and connectivity.

Repeated rejected sends do not generate more notices. Reaching the limit again after receiving credits in the same month does not generate a second notice either. There is no separate 80-percent warning or recovery notification.

The current beta iPhone app also shows a non-interruptive usage notice. After a successful status refresh confirms available capacity, it clears the notice and its own delivered quota notification. An offline app cannot immediately clear Notification Center, and a failed refresh does not falsely mark the problem as resolved. Update the beta app if these controls are missing.

## Getting help

Use the [private support contact](https://app.pushman.whitekiwi.link/support/) for account-specific problems. In the current beta app, copy the account ID from **Settings → Account → Account ID → Copy account ID** when support requests it. Never post account IDs, notification content, or credentials in public issues.
