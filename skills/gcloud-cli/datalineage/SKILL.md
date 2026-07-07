---
name: gcloud-datalineage
description: >-
  Data Lineage via gcloud (`gcloud datalineage`). Track the flow of data within Google Cloud — config, processes.
---

# gcloud datalineage — Data Lineage

> **Note:** This command group reached the GA track after gcloud SDK 552.0.0. In the product documentation, data lineage is a feature of Dataplex Universal Catalog — renamed **Knowledge Catalog** as of April 10, 2026; the CLI group name remains `gcloud datalineage`.

## Overview

Data Lineage is a service that tracks the flow of data within Google Cloud. The `gcloud datalineage` surface has two parts: **`config`** reads and updates the lineage ingestion configuration — per-integration rules (e.g. BigQuery) that turn automatic lineage generation on or off at project, folder, or organization scope — and **`processes`** manages custom lineage processes (the top-level lineage resource representing an application or pipeline, under which runs and lineage events are recorded). Processes are regional resources addressed with `--location`; deleting a process also deletes all of its associated runs and lineage events. The underlying API is the Data Lineage API (`datalineage.googleapis.com`).

## Quick reference — common workflows

### 1. Enable the API and inspect the lineage configuration

```bash
gcloud services enable datalineage.googleapis.com --project PROJECT_ID

# Configuration for the current project (or --project / --folder / --organization)
gcloud datalineage config describe
gcloud datalineage config describe --organization=789012
```

### 2. Turn lineage ingestion on or off per integration

```bash
# From a JSON/YAML file
gcloud datalineage config update --config=my_config.json

# Inline: enable automatic lineage for BigQuery in my-project
gcloud datalineage config update --project=my-project --config='{"ingestion": {"rules":
[{"integrationSelector": {"integration": "BIGQUERY"},
"lineageEnablement": {"enabled": true}}]}}'
```

### 3. Create a custom lineage process for your pipeline

```bash
gcloud datalineage processes create my-process --location=us-central1 \
    --display-name="My Process" --origin-source-type=custom \
    --origin-name="my-app"
```

### 4. List and inspect processes

```bash
gcloud datalineage processes list --location=us
gcloud datalineage processes describe my-process --location=us-central1
```

### 5. Update or delete a process

```bash
gcloud datalineage processes update my-process --location=us-central1 \
    --display-name="New Name"

# Deletes the process plus all associated runs and lineage events
gcloud datalineage processes delete my-process --location=us-central1 --async
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `datalineage config` | [`config.md`](config.md) | 2 | manage Data Lineage configurations |
| `datalineage processes` | [`processes.md`](processes.md) | 5 | manage Data Lineage processes |

See [`index.md`](index.md) for a one-line index of all 7 commands.

## Common flags & tips

- **Config scope:** `config describe` / `config update` accept **at most one** of `--folder`, `--organization`, `--project`; with none given, the current project is used.
- **`--config` is flexible:** it takes either an inline JSON/YAML string or a path to a file containing it. The payload is an `ingestion.rules` list of `{integrationSelector, lineageEnablement}` objects.
- **Processes are regional:** every `processes` command takes `--location` (or a fully qualified process name that embeds it). Lineage locations include multi-regions like `us` as well as regions like `us-central1`.
- **`--origin-source-type`** (create only, default `custom`) records where lineage originates: `bigquery`, `composer`, `custom`, `data-fusion`, `dataflow`, `dataproc`, `looker-core`, `looker-studio`, `source-type-unspecified`, `vertex-ai`.
- **`processes update --attributes` replaces** any existing attributes rather than merging.
- **Deletion is cascading and long-running:** `processes delete` removes all associated runs and lineage events; use `--async` to return immediately.
- **List commands** support the standard `--filter`, `--limit`, `--page-size`, `--sort-by`, and `--uri` flags.
- **CLI vs product launch stage:** the `config` commands are on the GA CLI track, but the lineage ingestion-control feature they manage is documented as **Preview** in the product docs.

## beta / alpha

`gcloud beta datalineage` and `gcloud alpha datalineage` mirror the same two groups (`config`, `processes`) with no additional subgroups — there is no CLI surface for runs or lineage events on any track; those are managed via the Data Lineage API. Automatic lineage for supported integrations (BigQuery, etc.) requires no CLI interaction beyond the ingestion config.

## Official documentation

- **Product docs:** https://docs.cloud.google.com/dataplex/docs/about-data-lineage — "About data lineage" (concepts, supported integrations, ingestion control at project/folder/organization level).
- **gcloud CLI reference:** https://cloud.google.com/sdk/gcloud/reference/datalineage — the `gcloud datalineage` command group.
