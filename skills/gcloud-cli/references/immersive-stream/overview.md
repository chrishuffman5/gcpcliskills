# gcloud immersive-stream — Immersive Stream for XR

## Overview
`gcloud immersive-stream` manages **Immersive Stream for XR**, a Google Cloud managed service that streams GPU-rendered 3D and augmented-reality (AR) experiences to end-user devices over the web, removing the need for high-end local hardware. You package experience assets as a Cloud Storage–backed **content resource**, build it into a tagged version, then serve it from regionally distributed **service instances** that allocate GPU streaming capacity per region. Reach for it when you need to deliver interactive 3D/AR to browsers at scale without shipping a heavy client. All commands live under the single `immersive-stream xr` group.

> **Removal status (re-audited July 2026, SDK 575.0.0):** `immersive-stream` no longer appears in the published gcloud reference — the top-level GROUPS index at `docs.cloud.google.com/sdk/gcloud/reference` omits it and both `.../reference/immersive-stream` and `.../reference/beta/immersive-stream` return HTTP 404. The group still exists in older installed SDKs (verified locally on 552.0.0), so these docs are retained for users on older SDKs, but treat the surface as deprecated/removed going forward and do not recommend it for new work. The command surface documented here was sourced directly from `gcloud --help` (see [`sources.md`](sources.md)).

## Quick reference — common workflows

**0. Enable the API (prerequisite)**
```bash
gcloud services enable stream.googleapis.com
```
_(API identifier follows Google Cloud naming conventions for this service; the product docs that listed it have been removed.)_

**1. Create and build a content resource**
```bash
# Create a content resource backed by a Cloud Storage bucket
gcloud immersive-stream xr contents create my-content \
    --bucket=my-bucket

# Build the content and tag it with a version
gcloud immersive-stream xr contents build my-content \
    --version=my-version

# Confirm the content resource exists
gcloud immersive-stream xr contents describe my-content
```

**2. Create a multi-region service instance**
```bash
# Serve my-content@my-version with capacity in two regions
gcloud immersive-stream xr instances create my-instance \
    --content=my-content --version=my-version \
    --add-region=region=us-west1,capacity=2 \
    --add-region=region=us-east4,capacity=3

# List instances to confirm
gcloud immersive-stream xr instances list
```

**3. Create an instance with an L4 GPU in 3D-only mode**
```bash
# L4 GPU is supported only in 3D-only mode and in select regions;
# both --gpu-class and --mode are fixed at creation and cannot be changed later.
gcloud immersive-stream xr instances create my-instance-l4 \
    --content=my-content --version=my-version \
    --add-region=region=us-west1,capacity=1 \
    --mode=3d \
    --gpu-class=l4
```

**4. Update an instance (one change per command)**
```bash
# Change capacity for an existing region (capacity must be > 0 and within quota)
gcloud immersive-stream xr instances update my-instance \
    --update-region=region=us-west1,capacity=4

# Add a new region
gcloud immersive-stream xr instances update my-instance \
    --add-region=region=us-east4,capacity=1

# Remove a region
gcloud immersive-stream xr instances update my-instance \
    --remove-region=us-east4

# Roll forward to a new content build version
gcloud immersive-stream xr instances update my-instance \
    --version=my-version

# Set a fallback URL for when streaming is unavailable
gcloud immersive-stream xr instances update my-instance \
    --fallback-url="https://www.google.com"
```

**5. Update the content source bucket and rebuild**
```bash
# Point the content resource at a new Cloud Storage bucket
gcloud immersive-stream xr contents update my-content \
    --bucket=my-new-bucket

# Rebuild with a new version tag
gcloud immersive-stream xr contents build my-content \
    --version=my-version
```

**6. Track long-running operations**
```bash
# Run a mutating command without blocking; returns the operation immediately
gcloud immersive-stream xr instances create my-instance \
    --content=my-content --version=my-version \
    --add-region=region=us-west1,capacity=2 \
    --async

# List, describe, or block on an operation
gcloud immersive-stream xr operations list
gcloud immersive-stream xr operations describe operation-123
gcloud immersive-stream xr operations wait operation-123
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `immersive-stream xr` | [`xr.md`](xr.md) | 14 | Manage Immersive Stream for XR content resources, service instances, and operations |

See [`index.md`](index.md) for a one-line index of all 14 commands.

## Common flags & tips
- **Everything is global.** Content, instance, and operation resources only support `--location=global` (the default). There are no zonal/regional resource scopes; per-region capacity is expressed inside `--add-region` / `--update-region`, not via `--location`.
- **Content lifecycle is two-step.** `contents create --bucket=...` registers the Cloud Storage source; `contents build --version=...` produces a tagged, servable build. Instances reference a build via `--content` + `--version`.
- **`--add-region` / `--update-region` are key=value tuples.** Supported keys: `region`, `capacity` (max concurrent streaming sessions), and the autoscaling keys `enable_autoscaling`, `autoscaling_buffer`, `autoscaling_min_capacity`. `--add-region` is repeatable on `instances create`.
- **`instances update` changes one thing at a time.** It accepts exactly one of `--add-region`, `--update-region`, `--remove-region`, `--version`, or `--fallback-url` per invocation. New capacity may not be 0 or exceed your quota.
- **Immutable-at-creation settings.** `--gpu-class` (`t4` default, or `l4`) and `--mode` (`ar` default, or `3d`) are fixed when the instance is created and cannot be updated. `l4` requires `--mode=3d` and is available only in certain regions.
- **Async + operations.** Add `--async` to `contents`/`instances` create, update, build, and delete to return an operation name instead of blocking; then poll with `operations describe` or block with `operations wait`.
- **Filtering/formatting lists:**
  ```bash
  gcloud immersive-stream xr instances list --format="table(name, state)"
  gcloud immersive-stream xr instances list --filter="name:my-instance" --uri
  gcloud immersive-stream xr operations list --sort-by=~name --limit=10
  ```

## beta / alpha
No beta- or alpha-only capabilities are documented. The published `gcloud beta immersive-stream` and `gcloud alpha immersive-stream` reference URLs return 404, and the local reference files cover only GA commands (14 total, all under `gcloud immersive-stream xr`). The autoscaling keys on `--add-region` / `--update-region` are present in the GA `instances create` and `instances update` synopses.

## Official documentation
- **gcloud CLI reference (immersive-stream):** https://cloud.google.com/sdk/gcloud/reference/immersive-stream — top-level CLI reference for this group. _Note: currently redirects to a 404; retained as the canonical reference path._
- **Product docs home (historical):** https://cloud.google.com/immersive-stream/xr/docs — former product documentation landing page. _Note: now 301-redirects to the generic AI/ML docs page; product content has been removed._
- See [`sources.md`](sources.md) for the full citation record of source URLs and their current reachability status.
