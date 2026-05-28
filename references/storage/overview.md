# gcloud storage — Cloud Storage

## Overview

`gcloud storage` is the unified CLI for Google Cloud Storage — globally available, highly
durable object storage for buckets and objects. It covers everyday data movement (`cp`,
`mv`, `rsync`, `cat`), bucket and object lifecycle management, IAM, signed URLs, and
advanced features such as soft delete, batch operations, and storage insights. It is the
modern successor to `gsutil`; for command mappings and behavioral differences, see the
transition guide linked below.

## Quick reference — common workflows

```bash
# 0. Enable the API (once per project)
gcloud services enable storage.googleapis.com

# 1. Create a bucket (Nearline default class, uniform bucket-level access)
gcloud storage buckets create gs://my-bucket \
    --location=us-central1 \
    --default-storage-class=nearline \
    --uniform-bucket-level-access
gcloud storage buckets describe gs://my-bucket --format="json(name,location)"

# 2. Upload, download, and copy objects
gcloud storage cp report.pdf gs://my-bucket/reports/report.pdf   # upload
gcloud storage cp --recursive ./data gs://my-bucket/data         # upload a tree
gcloud storage cp gs://my-bucket/reports/report.pdf ./downloads/ # download
gcloud storage cp gs://src-bucket/file.txt gs://dst-bucket/      # in-cloud copy
gcloud storage ls --long --readable-sizes gs://my-bucket         # list with sizes

# 3. Sync (rsync) a local directory to a bucket
gcloud storage rsync ./local-data gs://my-bucket/data --recursive
# Mirror exactly (delete extra objects at destination); preview first with --dry-run
gcloud storage rsync ./local-data gs://my-bucket/data --recursive \
    --delete-unmatched-destination-objects --dry-run
# Skip log files (Python regex), gzip image uploads in flight
gcloud storage rsync ./site gs://my-bucket/site --recursive \
    --exclude=".*\.log$" --gzip-in-flight=js,css,html

# 4. Set a lifecycle policy on a bucket (lifecycle.json shown below)
gcloud storage buckets update gs://my-bucket --lifecycle-file=lifecycle.json
gcloud storage buckets update gs://my-bucket --clear-lifecycle   # remove it

# 5. Generate a signed URL (time-limited public access, no Google credentials)
gcloud storage sign-url gs://my-bucket/report.pdf --duration=30m \
    --impersonate-service-account=sa@my-project.iam.gserviceaccount.com
# Signed URL for a PUT upload, valid one hour
gcloud storage sign-url gs://my-bucket/upload.txt --http-verb=PUT --duration=1h \
    --headers=content-type=text/plain \
    --impersonate-service-account=sa@my-project.iam.gserviceaccount.com

# 6. Manage bucket IAM and delete a bucket
gcloud storage buckets get-iam-policy gs://my-bucket
gcloud storage buckets add-iam-policy-binding gs://my-bucket \
    --member=user:alice@example.com --role=roles/storage.objectViewer
gcloud storage buckets remove-iam-policy-binding gs://my-bucket \
    --member=user:alice@example.com --role=roles/storage.objectViewer
gcloud storage rm --recursive gs://my-bucket/     # delete all objects + bucket
```

Example `lifecycle.json` (move to Coldline at 90 days, delete at 365):

```json
{
  "rule": [
    {"action": {"type": "SetStorageClass", "storageClass": "COLDLINE"},
     "condition": {"age": 90}},
    {"action": {"type": "Delete"}, "condition": {"age": 365}}
  ]
}
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `storage batch-operations` | [`batch-operations.md`](batch-operations.md) | 5 | manage Cloud Storage batch operations |
| `storage buckets` | [`buckets.md`](buckets.md) | 21 | manage Cloud Storage buckets (incl. `anywhere-caches`, `notifications`) |
| `storage folders` | [`folders.md`](folders.md) | 4 | manage hierarchical-namespace folders |
| `storage hmac` | [`hmac.md`](hmac.md) | 5 | manage service account HMAC keys |
| `storage insights` | [`insights.md`](insights.md) | 14 | manage inventory reports & dataset configs |
| `storage intelligence-configs` | [`intelligence-configs.md`](intelligence-configs.md) | 4 | manage Storage Intelligence configurations |
| `storage managed-folders` | [`managed-folders.md`](managed-folders.md) | 8 | manage managed folders (with IAM) |
| `storage objects` | [`objects.md`](objects.md) | 4 | compose, describe, list, update objects |
| `storage operations` | [`operations.md`](operations.md) | 3 | manage long-running storage operations |

Top-level commands (`cat`, `cp`, `diagnose`, `du`, `hash`, `ls`, `mv`, `restore`, `rm`,
`rsync`, `service-agent`, `sign-url`) are in [`_commands.md`](_commands.md). A one-line
index of all 80 GA commands is in [`index.md`](index.md).

## Common flags & tips

- **gs:// URLs**: paths begin with `gs://BUCKET/OBJECT`. Wildcards: `*` matches within a
  path segment, `**` matches a flat list of objects across levels (e.g.
  `gs://my-bucket/**/*.txt`). Cross-provider URLs like `s3://...` work for `cp`/`rsync`.
- **Recursion**: `-r`/`-R`/`--recursive` for `cp`, `mv`, `ls`, `rm`, `rsync`. For `rm`,
  `--recursive` on a bucket URL (`gs://bucket/`) also deletes the bucket and implies
  `--all-versions`; the `**` wildcard instead targets only live objects.
- **Compression**: on `cp`/`mv`/`rsync` use `--gzip-in-flight=EXT,...` (`-j`) or
  `--gzip-in-flight-all` (`-J`) to gzip on the wire only; `cp`/`mv` also support
  `--gzip-local`/`-z` and `--gzip-local-all`/`-Z` to store compressed objects.
- **Parallelism**: transfers run in parallel by default. `--continue-on-error` (`-c`) only
  takes effect in sequential mode (process & thread count = 1). `gcloud storage diagnose`
  exposes `--process-count`/`--thread-count` for throughput testing.
- **Output control**: `--format` and `--filter` are global (e.g.
  `gcloud storage buckets list --format="json(name)"`,
  `gcloud storage buckets describe gs://my-bucket --format="json(name,location)"`).
  `ls --format=gsutil` mimics legacy `gsutil` output; `ls --long`/`-l` adds sizes and
  `--readable-sizes` makes them human-readable.
- **gsutil relationship**: `gcloud storage` replaces `gsutil`. Many flags/short forms match
  (`-r`, `-n`/`--no-clobber`, `-s`/`--storage-class`), but wildcard handling, output, and
  parallelism differ — consult the transition guide before porting scripts.

## beta / alpha

All 80 commands documented here are GA. Some experimental capabilities may also be exposed
under `gcloud alpha storage` / `gcloud beta storage` (not documented here); the surface and
flags generally mirror the GA group.

## Official documentation

- gcloud CLI reference (storage): https://cloud.google.com/sdk/gcloud/reference/storage — canonical command/flag surface for the `storage` group.
- Cloud Storage product docs home: https://cloud.google.com/storage/docs — entry point for all guides, references, and samples.
- Quickstart with gcloud storage: https://cloud.google.com/storage/docs/discover-object-storage-gcloud — create a bucket, upload/download, list, manage IAM, delete.
- gsutil → gcloud storage transition: https://cloud.google.com/storage/docs/gsutil-transition-to-gcloud — command mapping and behavioral differences.
- Storage classes: https://cloud.google.com/storage/docs/storage-classes — Standard, Nearline, Coldline, Archive and their tradeoffs.
- Object Lifecycle Management: https://cloud.google.com/storage/docs/lifecycle — lifecycle conditions and actions used in `--lifecycle-file`.
- Signed URLs: https://cloud.google.com/storage/docs/access-control/signed-urls — concept behind `gcloud storage sign-url` (max 12 h system key, 7 days SA key).
- IAM roles for Cloud Storage: https://cloud.google.com/storage/docs/access-control/iam-roles — predefined bucket/object roles for `add-iam-policy-binding`.
