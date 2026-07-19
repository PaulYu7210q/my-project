# my-project

Public GitHub Actions runner for Go `grokcli-2api`. Pulls private source, runs native Go plus local Python registration/captcha sidecars, exposes the configured Cloudflare tunnel, then checkpoints PostgreSQL state.

## Secrets

| Secret | Required | Purpose |
|--------|----------|---------|
| `PRIVATE_REPO_TOKEN` | yes | PaulYu7210q PAT: checkout private `grokcli-2api`; relay dispatch |
| `DB_STORAGE_TOKEN` | yes | jjjjllll111 PAT: read/write `jjjjllll111/db-storage` |
| `GROK2API_ADMIN_PASSWORD` | yes | Initializes admin access on a fresh PostgreSQL database |
| `CF_TUNNEL_TOKEN` | yes | Tunnel connector token (`eyJ...`), not Cloudflare API token (`cfat_...`) |

## Runtime

The runner uses Go 1.24, builds `bin/grok2api` and `bin/grok2api-migrate`, applies Go SQL migrations, starts the Turnstile solver and registration sidecar on loopback, then waits for `/ready`.

`https://xai.logincore.me/ready` is the public readiness URL.

## Backup

The authoritative durable state is `grok2api.dump` in `jjjjllll111/db-storage`.

No dump means a fresh PostgreSQL schema with zero accounts. The old `data.sqlite` file is not imported automatically. Add a deliberate legacy import only when the source data and migration path are verified.

## Trigger

Actions -> **Run Service** -> Run workflow

## Repositories

- `PaulYu7210q/grokcli-2api` (private source)
- `jjjjllll111/db-storage` (private PostgreSQL backup)
