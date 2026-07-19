# my-project

Public GitHub Actions runner. Pulls private `grokcli-2api`, backups to `jjjjllll111/db-storage`.

## Secrets

| Secret | Required | Purpose |
|--------|----------|---------|
| `PRIVATE_REPO_TOKEN` | yes | PAT (PaulYu7210q) — checkout private `grokcli-2api` + re-dispatch workflow |
| `DB_STORAGE_TOKEN` | yes | PAT (jjjjllll111) — read/write `jjjjllll111/db-storage` backups |
| `GROK2API_ADMIN_PASSWORD` | yes | Admin password |
| `CF_TUNNEL_TOKEN` | yes | **Tunnel connector token** (`eyJ...` from Cloudflare Zero Trust → Tunnels → Configure → Install). NOT API token (`cfat_...`) |

## Tunnel

Public URL: https://xai.logincore.me/  
`cloudflared tunnel run --token <CF_TUNNEL_TOKEN>` needs the connector token, not Account API Token.

## Trigger

Actions → **Run Service** → Run workflow

## Deps

- `PaulYu7210q/grokcli-2api` (private source)
- `jjjjllll111/db-storage` (backup: data.zip + grok2api.dump)
