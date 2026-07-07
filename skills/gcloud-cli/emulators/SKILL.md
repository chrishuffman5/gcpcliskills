---
name: gcloud-emulators
description: >-
  Local emulators via gcloud (`gcloud emulators`). Set up your local development environment using emulators — firestore, spanner.
---

# gcloud emulators — Local emulators

## Overview
`gcloud emulators` starts local, in-memory emulators for Google Cloud data services so you can build and test applications without connecting to (or paying for) real cloud resources. Reach for it during local development and CI: point your client libraries at a `*_EMULATOR_HOST` address, run your code, and the emulator behaves like the service. Nothing here touches a cloud project — no API enablement, no IAM, and no billing are required, and no data persists across restarts unless you explicitly export it. The GA group covers **Firestore** and **Spanner**; **Pub/Sub**, **Bigtable**, and **Datastore** emulators live under `gcloud beta emulators`.

## Quick reference — common workflows

### 1. Firestore emulator (Native mode) + connect a client
```bash
# Firestore emulator ships with the gcloud SDK
gcloud components update

# Start on the default localhost:8080
gcloud emulators firestore start

# Or bind to all interfaces on a chosen port
gcloud emulators firestore start --host-port=0.0.0.0:8080

# Point client libraries at the emulator (set BEFORE running your app)
export FIRESTORE_EMULATOR_HOST="localhost:8080"
```

### 2. Firestore in Datastore mode (replaces the legacy datastore emulator)
```bash
gcloud emulators firestore start --database-mode=datastore-mode

export FIRESTORE_EMULATOR_HOST="localhost:8080"
```

### 3. Load security rules / persist Firestore data
```bash
# Apply a Firebase Rules file to all projects
gcloud emulators firestore start --rules=firestore.rules

# Export emulator data on shutdown
gcloud emulators firestore start --export-on-exit=/home/user/emulator-data/

# Re-import that data on the next start
gcloud emulators firestore start \
    --import-data=/home/user/emulator-data/sampleExport.overall_export_metadata
```

### 4. Spanner emulator + env-init workflow
```bash
# Install the Spanner emulator component
gcloud components install cloud-spanner-emulator

# Start the emulator (gRPC on :9010, REST on :9020)
gcloud emulators spanner start

# Print the export commands and apply them in one step (Linux/macOS)
$(gcloud emulators spanner env-init)
# -> sets SPANNER_EMULATOR_HOST=localhost:9010

# Or set it yourself
export SPANNER_EMULATOR_HOST=localhost:9010

# Route gcloud itself at the emulator via a dedicated configuration
gcloud config configurations create emulator
gcloud config set auth/disable_credentials true
gcloud config set project my-project
gcloud config set api_endpoint_overrides/spanner http://localhost:9020/
```

### 5. Spanner abort-retry (fault injection) testing
```bash
# Randomly inject faults so you can exercise transaction retry logic
gcloud emulators spanner start --enable-fault-injection=true
```

### 6. beta emulators — Pub/Sub, Bigtable, Datastore
```bash
# Pub/Sub
gcloud components install pubsub-emulator
gcloud beta emulators pubsub start
$(gcloud beta emulators pubsub env-init)   # sets PUBSUB_EMULATOR_HOST

# Bigtable
gcloud components update beta
gcloud beta emulators bigtable start        # set BIGTABLE_EMULATOR_HOST

# Datastore (legacy; prefer Firestore --database-mode=datastore-mode)
gcloud components install cloud-datastore-emulator
gcloud beta emulators datastore start
$(gcloud beta emulators datastore env-init) # sets DATASTORE_EMULATOR_HOST
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `emulators firestore` | [`firestore.md`](firestore.md) | 1 | manage your local Firestore emulator |
| `emulators spanner` | [`spanner.md`](spanner.md) | 3 | manage your local Spanner emulator |

See [`index.md`](index.md) for a one-line index of all GA commands. The `pubsub`, `bigtable`, and `datastore` subgroups are available under `gcloud beta emulators`.

## Common flags & tips
- **The `env-init` pattern (Spanner).** `gcloud emulators spanner env-init` only *prints* the `export SPANNER_EMULATOR_HOST=...` line; wrap it in `$(...)` to actually apply it to your shell. The beta emulators expose the same `env-init` helper.
- **Client connection is via env vars, not flags.** Emulators are wired to clients through `*_EMULATOR_HOST` environment variables (`FIRESTORE_EMULATOR_HOST`, `SPANNER_EMULATOR_HOST`, `PUBSUB_EMULATOR_HOST`, `BIGTABLE_EMULATOR_HOST`, `DATASTORE_EMULATOR_HOST`). Set them before launching your application, and unset them to talk to the real service again.
- **`--host-port` binding.** Firestore defaults to `localhost:8080`; Spanner defaults to `localhost:9010` (gRPC). Use `--host-port=0.0.0.0:PORT` to accept connections from other machines/containers. IPv6 addresses must be bracketed, e.g. `[2001:db8::1]:8080`.
- **Spanner has two ports.** `--host-port` controls the gRPC port (default 9010); `--rest-port` controls the REST port (default 9020) that gcloud itself uses to talk to the emulator.
- **No persistence by default.** Emulator data is in-memory. For Firestore, use `--export-on-exit=DIR` to dump on shutdown and `--import-data=FILE` to reload on the next start.
- **Docker for Spanner on non-Linux.** A native Spanner binary is provided only for Linux. On other platforms pass `--use-docker` (and specify the host as an IP address); the same `--use-docker` flag applies to `spanner notices`.
- **No auth.** Emulators do not implement authentication, IAM, or permissions. For gcloud-driven Spanner workflows, set `gcloud config set auth/disable_credentials true` in a dedicated configuration.
- **Licenses / notices.** `gcloud emulators firestore start --licenses` prints open-source dependency licenses and exits; `gcloud emulators spanner notices` prints third-party notices.

## beta / alpha
The GA `gcloud emulators` group contains only two subgroups — `firestore` and `spanner`. The remaining emulators are GA-quality tools that are still surfaced only under the beta track:

| Emulator | Command prefix | Status |
|----------|----------------|--------|
| Firestore | `gcloud emulators firestore` | **GA** |
| Spanner | `gcloud emulators spanner` | **GA** |
| Pub/Sub | `gcloud beta emulators pubsub` | **beta** |
| Bigtable | `gcloud beta emulators bigtable` | **beta** |
| Datastore | `gcloud beta emulators datastore` | **beta** |

Beta commands may change without notice. A `gcloud alpha emulators` track also exists but is not documented separately. (The live web reference also exposes a `--edition=standard|enterprise` flag for `gcloud emulators firestore start` that is not yet in this skill's local reference — verify against `gcloud emulators firestore start --help` before relying on it.)

## Official documentation
- **gcloud CLI reference (GA: firestore, spanner):** https://cloud.google.com/sdk/gcloud/reference/emulators
- **gcloud beta reference (adds pubsub, bigtable, datastore):** https://cloud.google.com/sdk/gcloud/reference/beta/emulators
- **Firestore emulator guide:** https://cloud.google.com/firestore/docs/emulator — install, start, connect clients, limitations.
- **Cloud Spanner emulator guide:** https://cloud.google.com/spanner/docs/emulator — install, start, env vars, gcloud config overrides.
- **Pub/Sub emulator guide:** https://cloud.google.com/pubsub/docs/emulator — start via beta, env vars.
- **Bigtable emulator guide:** https://cloud.google.com/bigtable/docs/emulator — start via beta, env vars.
- **Datastore emulator guide:** https://cloud.google.com/datastore/docs/tools/datastore-emulator — start via beta, env vars.
</content>
</invoke>
