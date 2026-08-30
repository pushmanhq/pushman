# Notification fields

`pushman push` accepts a body plus optional presentation and routing fields.

| Field | CLI option | Behavior |
| --- | --- | --- |
| Body | positional argument or stdin | Primary notification content |
| Title | `--title` | Notification title |
| Subtitle | `--subtitle` | Native iOS subtitle |
| URL | `--url` | Opens when the notification is tapped; HTTPS and registered app schemes are supported |
| Image | `--image` | Public HTTPS JPEG or PNG URL downloaded by the iPhone app |
| Sound | `--sound default\|none` | Plays the default sound or delivers silently |
| Group | `--group` | Groups related notifications |
| Update key | `--key` | Replaces or updates a logically equivalent notification |
| Monospace | `--monospace` | Presents the body using monospace styling in the app |
| Device | `--device` | Targets a receiving-device nickname; repeatable |

Pushman generates the immutable message ID. Callers do not supply it. Message history expires after seven days, while delivery acceptance counts toward the monthly account allowance.

For exact validation rules and schemas, see the [public OpenAPI contract](../api/openapi.yaml). For command syntax, run `pushman help push` using the installed CLI version.
