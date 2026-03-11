
# n8n Codespaces Starter

Run **n8n** fully in the cloud using **GitHub Codespaces** — no local admin rights, no Docker install needed.

## Quick Start

1. **Create a GitHub repo** (e.g., `n8n-codespace-starter`).
2. Upload these files to your repo (or push via Git).
3. Click **Code → Create codespace on main**.
4. Wait for the container to build (1–3 minutes). It auto-installs n8n.
5. In the Codespaces terminal, run:
   ```bash
   n8n
   # or
   npm run start
   ```
6. When port **5678** opens, click **Open in Browser** to access the n8n UI.

> Tip: If you want basic auth, copy `.env.example` to `.env` and set username/password before starting n8n.

## Environment variables (optional but recommended)
Create a `.env` file in the repo root:

```
# Core
N8N_HOST=0.0.0.0
N8N_PORT=5678

# Security
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=change_me

# Editor / Webhook (Codespaces handles public URL automatically)
N8N_DIAGNOSTICS_ENABLED=false
N8N_TELEMETRY_ENABLED=false
```

n8n will auto-read `.env` if present.

## Import the sample workflow
1. Start n8n → **Workflows → Import from File**.
2. Choose `workflows/sample-hello-varun.json`.
3. Execute via REST:
   ```bash
   curl -X POST "$N8N_URL/webhook/hello-varun"         -H 'Content-Type: application/json'         -d '{"name":"varun"}'
   ```
   You should see an uppercase name echoed back with a timestamp.

## Persistence & Backups
- Codespaces keeps your data while the Codespace exists. If you delete the Codespace, local data is gone.
- Regularly **Export** your workflows (top-right menu in n8n) or push exported JSON files into `workflows/` and commit.

## Troubleshooting
- If `n8n` is not found, try `npx n8n` once, or re-open terminal.
- If the port doesn’t open: **Ports** tab → make **5678** public → open in browser.
- If you enabled BASIC auth and forgot password, update `.env` and re-run `n8n`.

---
Happy automating! 🚀
