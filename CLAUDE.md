# GCP CLI Plugin

Command-reference skills for Google's CLIs: `gcloud` (128 GCP services, 5,261 GA commands),
the standalone `bq` BigQuery CLI, and the Agent Development Kit toolchain — delivered as a
lean router skill plus per-service sub-skills.

## How it works

- `skills/gcloud-cli/SKILL.md` is the registered router: gcloud conventions (`--format`,
  `--filter`, config, auth, scripting, troubleshooting) plus a routing protocol. It is the only
  gcloud skill description loaded at session start.
- Each service is a bundled sub-skill at `skills/gcloud-cli/<gcloud-group>/SKILL.md` (e.g.
  `compute/`, `run/`, `storage/`, `iam/`). The router reads only the service you need — the full
  catalog never loads up front, which keeps context small.
- Within a service, command-group files alongside `SKILL.md` (e.g. `instances.md`, `buckets.md`)
  hold the full per-command synopses, flags, types, choices, defaults, and examples; `index.md`
  is the one-line command list and `sources.md` the official documentation URLs.
- `skills/gcloud-cli/service-index.md` is the full name → sub-skill lookup, read only when the
  gcloud group name isn't already known (e.g. "which service is Media CDN?").
- `skills/gcloud-cli/bq-cli/` documents the standalone `bq` BigQuery CLI (distinct from
  `gcloud bq`, which is Migration Service only).
- `skills/adk/`, `skills/adk-devtools/`, and `skills/adk-web/` are standalone skills for the
  Python ADK CLI, the TypeScript ADK dev tools, and the ADK developer web UI.

## Usage

Just ask about any GCP service via the CLI ("create a Cloud SQL instance", "deploy to Cloud
Run", "set up a GKE cluster") or about building ADK agents. The router loads the matching
sub-skill on demand.

## Sourcing

All command/flag data comes from each tool's own `--help` output (the canonical source behind
`cloud.google.com/sdk/gcloud/reference`) and official Google documentation only. Generated
against SDK 552.0.0; index audited against 575.0.0. See "Sourcing & accuracy" in the router
SKILL.md.
