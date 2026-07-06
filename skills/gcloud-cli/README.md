# gcpcliskills — gcloud CLI Skill

A comprehensive [Claude](https://claude.com/claude-code) **skill** providing a complete `gcloud`
command reference for **128 Google Cloud services** and **5,261 GA commands**, plus the standalone
**`bq`** BigQuery CLI. It is the GCP counterpart to
[`awscliskills`](https://github.com/chrishuffman5/awscliskills).

The root [`SKILL.md`](SKILL.md) is a **router**: it indexes every service and routes a request to
the right per-service reference, which contains exhaustive command documentation.

## Structure

```
SKILL.md                       # Router: service index + official doc links + gcloud conventions
references/<service>/
  overview.md                  # Product summary, common-workflow recipes, tips, beta/alpha notes, citations
  index.md                     # One-line index of every command in the service
  sources.md                   # Verified official cloud.google.com documentation URLs
  <command-group>.md           # Exhaustive per-command reference: synopsis + every flag
                               #   (type, choices, default, description) + examples
```

Each command page mirrors the style of the AWS CLI skill: synopsis, a full flags table, positional
arguments, real examples, and a link to the official `cloud.google.com/sdk/gcloud/reference` page.

## Using it

**Claude Code** — install the packaged skill, or drop this folder into your skills directory:

```bash
# from a packaged artifact
# (the .skill file is a zip of this repo)

# or as a local skill
cp -r . ~/.claude/skills/gcloud-cli
```

Then just ask Claude things like *"create a Cloud SQL Postgres instance with HA in us-central1"* or
*"deploy this image to Cloud Run with auth required"* — the router triggers and consults the right
reference.

## Sourcing & accuracy

All command and flag data is generated directly from the gcloud CLI's own help system
(`gcloud <command> --help`), which is the canonical source Google publishes at
`cloud.google.com/sdk/gcloud/reference`. The content was generated against **Google Cloud SDK
552.0.0** and the service index re-audited against **SDK 575.0.0** (June 30, 2026): services new
to GA since 552 (`agent-registry`, `apihub`, `biglake`, `datalineage`, `service-health`,
`vector-search`, `workload-identity`) are documented from the current published reference, and
`immersive-stream` is flagged as removed. Per-service conceptual docs, quickstarts, and how-to
guides are linked from each service's `overview.md` / `sources.md` (official Google sources only).

Coverage is the **GA** command surface; each service notes where important capabilities are only
available under `gcloud beta` / `gcloud alpha`.

## Regenerating on a new SDK version

The skill is generated, not hand-maintained. To refresh after a `gcloud components update`, re-run
the dump → render → router pipeline (deterministic), then optionally re-run the research/authoring
enrichment for services whose command surface changed.

## Attribution

Command reference content is derived from Google Cloud's public documentation and the gcloud CLI
help system. "Google Cloud", "gcloud", and product names are trademarks of Google LLC. This is an
unofficial, community reference and is not affiliated with or endorsed by Google.
