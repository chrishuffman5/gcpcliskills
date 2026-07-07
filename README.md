# gcpcliskills

A [Claude Code](https://claude.com/claude-code) **plugin** bundling command-reference **skills** for
Google's command-line tools. Each skill routes Claude to accurate, version-pinned command
documentation sourced from each tool's own `--help` and official Google docs.

| Skill | Tool | Scope |
|-------|------|-------|
| [`gcloud-cli`](skills/gcloud-cli/) | `gcloud` + `bq` | 128 GCP services, **5,261 GA commands** (plus the standalone `bq` BigQuery CLI) — exhaustive per-command flag tables, workflows, and official doc links |
| [`adk`](skills/adk/) | `adk` (Python) | Agent Development Kit CLI: create/run/eval/deploy AI agents; launch the dev web UI |
| [`adk-devtools`](skills/adk-devtools/) | `@google/adk-devtools` (TS/JS) | TypeScript ADK SDK + dev-tools CLI (`npx @google/adk-devtools`) |
| [`adk-web`](skills/adk-web/) | ADK Web UI | The Angular developer UI — built-in `adk web` and the standalone `google/adk-web` app |

Repository layout (Claude Code plugin):

```
.claude-plugin/
  plugin.json          # plugin manifest
  marketplace.json     # lets the repo be added as a plugin marketplace
skills/
  gcloud-cli/          # SKILL.md (lean router) + service-index.md + <service>/SKILL.md sub-skills
  adk/                 # SKILL.md
  adk-devtools/        # SKILL.md
  adk-web/             # SKILL.md
```

---

## Installing the skills (the plugin)

In Claude Code, add this repo as a plugin marketplace, then install the plugin:

```text
/plugin marketplace add chrishuffman5/gcpcliskills
/plugin install gcpcliskills@gcpcliskills
```

Once installed, the skills trigger automatically when you ask Claude about the relevant tool
(e.g. *"create a Cloud SQL instance"*, *"deploy this agent to Cloud Run with adk"*).

Alternatively, copy any single skill into your skills directory:

```powershell
Copy-Item -Recurse skills/gcloud-cli "$HOME/.claude/skills/gcloud-cli"
```

---

## Installing the underlying CLIs

Each tool installs differently. Verified install commands (Windows / PowerShell 7; the skills were
built against the versions noted):

### gcloud — Google Cloud CLI
Not on npm/pip; use the dedicated installer.
```powershell
winget install Google.CloudSDK
# or download the installer: https://cloud.google.com/sdk/docs/install
gcloud init        # first-time auth + default project/region
```
Built against **Google Cloud SDK 552.0.0**; service index audited against **575.0.0** (June 2026).

### adk — Agent Development Kit (Python)
On PyPI. Requires Python 3.10+ (3.13 supported).
```powershell
pip install google-adk
adk --version      # provides the `adk` command
```
Built against **google-adk 2.3.0**. Auth: either an AI Studio key (`GOOGLE_API_KEY`) or Vertex AI
(`gcloud auth application-default login` + `GOOGLE_GENAI_USE_VERTEXAI=TRUE`).

### adk-devtools — ADK for TypeScript / JavaScript
On npm. Requires Node.js 24+. This is a **separate runtime** from the Python ADK (parallel
implementations — pick one lane; they don't interoperate).
```powershell
npm install @google/adk            # the JS/TS SDK
npm install -D @google/adk-devtools # the dev-tools CLI
npx @google/adk-devtools --help    # run it via npx
```
> ⚠️ `@google/adk-devtools` registers a bin named **`adk`**, which collides with the Python `adk`
> command. Always invoke the TypeScript CLI via `npx @google/adk-devtools …` (or
> `./node_modules/.bin/adk`) — never a bare `adk` — so it doesn't clash on PATH.
Built against **@google/adk / @google/adk-devtools 1.3.0**.

### ADK Web UI
Two paths:

**Built-in (recommended)** — ships with the Python ADK:
```powershell
pip install google-adk
adk web path/to/agents_dir          # serves the dev UI on http://localhost:8000
```

**Standalone from source** (to customize/contribute to the UI):
```powershell
git clone https://github.com/google/adk-web
cd adk-web
npm install
# in one terminal — run an ADK backend:
adk api_server --allow_origins=http://localhost:4200 --host=0.0.0.0
# in another terminal — serve the Angular UI (then open http://localhost:4200):
npm run serve --backend=http://localhost:8000
```

---

## Sourcing & accuracy

Command and flag data is generated from each tool's own help system (`gcloud … --help`,
`adk … --help`, `npx @google/adk-devtools … --help`) — the canonical source behind the published
references — and cross-checked against official `cloud.google.com` / `adk.dev` /
`github.com/google` documentation, which each skill links in its `sources.md` / Official
documentation section. Coverage is the **GA** surface; beta/alpha is noted where relevant.

## Attribution

Reference content is derived from Google's public documentation and the tools' own help output.
"Google Cloud", "gcloud", "ADK", and product names are trademarks of Google LLC. This is an
unofficial, community reference and is not affiliated with or endorsed by Google.
