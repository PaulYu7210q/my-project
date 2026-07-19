# my-project

Public GitHub Actions runner. Pulls private `grokcli-2api` and runs it (winrunner pattern).

## Secrets (repo Settings → Secrets)

| Secret | Required | Purpose |
|--------|----------|---------|
| `PRIVATE_REPO_TOKEN` | yes | PAT with `repo` + `workflow` — checkout private `grokcli-2api` + `db-storage`, push backups, re-dispatch |
| `GROK2API_ADMIN_PASSWORD` | yes | Admin password for the app |
| `CF_TUNNEL_TOKEN` | yes | Cloudflare tunnel token |

## Trigger

Actions → **Run Service** → Run workflow

Relay auto-restarts after success (30s delay).

## Private deps

- `PaulYu7210q/grokcli-2api` (app source)
- `PaulYu7210q/db-storage` (data.zip + grok2api.dump)
