# gcloud backup-dr — Backup and DR Service

## Overview

`gcloud backup-dr` manages Google Cloud Backup and DR Service — centralized, policy-driven
data protection for Google Cloud workloads (Compute Engine VMs and disks, Cloud SQL, AlloyDB,
Filestore, VMware Engine, databases, and file systems). The CLI manages backup vaults with
enforced (immutable) retention, backup plans with scheduled rules, backup plan associations
that bind a plan to a protected resource, management servers (for the management console),
and restore operations. Reach for it to enforce retention policy, run scheduled or on-demand
backups, and restore protected resources. The GA surface has 40 commands across 12 groups.

## Quick reference — common workflows

### 1. Enable the API and initialize service configuration

```bash
gcloud services enable backupdr.googleapis.com

# Initialize default service config for a resource type in a location
gcloud backup-dr service-config init \
    --project=MY_PROJECT \
    --location=us-central1 \
    --resource-type="compute.googleapis.com/Instance"

# See where Backup and DR is available
gcloud backup-dr locations list
```

### 2. Create a backup vault (enforced retention)

```bash
# Vault with a 1-month minimum enforced retention (relative-time format: p1d, p1m, p1m1d)
gcloud backup-dr backup-vaults create my-vault \
    --location=us-central1 \
    --backup-min-enforced-retention="p1m" \
    --description="Production backup vault"

gcloud backup-dr backup-vaults list --location=us-central1
gcloud backup-dr backup-vaults describe my-vault --location=us-central1
```

### 3. Create a backup plan and associate it with a resource

```bash
# A plan targets one resource type and stores backups in a vault; rules define schedule + retention
gcloud backup-dr backup-plans create my-backup-plan \
    --project=MY_PROJECT \
    --location=us-central1 \
    --resource-type="compute.googleapis.com/Instance" \
    --backup-vault=my-vault \
    --backup-rule="rule-id=daily-rule,retention-days=30,recurrence=DAILY,backup-window-start=2,backup-window-end=14"

# Bind the plan to a specific VM (--resource is the resource URI)
gcloud backup-dr backup-plan-associations create my-bpa \
    --project=MY_PROJECT \
    --location=us-central1 \
    --backup-plan=my-backup-plan \
    --resource=projects/MY_PROJECT/zones/us-central1-a/instances/my-vm \
    --resource-type="compute.googleapis.com/Instance"

gcloud backup-dr backup-plan-associations describe my-bpa --location=us-central1
```

### 4. Trigger an on-demand backup and monitor it

```bash
gcloud backup-dr backup-plan-associations trigger-backup my-bpa \
    --project=MY_PROJECT \
    --location=us-central1 \
    --backup-rule-id=daily-rule

gcloud backup-dr operations list
gcloud backup-dr backups list --backup-vault=my-vault --location=us-central1
```

### 5. Restore a Compute Engine VM from a backup

```bash
# Find the backup (scope by data source + vault)
gcloud backup-dr backups list \
    --backup-vault=my-vault \
    --data-source=my-data-source \
    --location=us-central1

# Restore the backup to a new instance
gcloud backup-dr backups restore compute BACKUP_ID \
    --project=MY_PROJECT \
    --location=us-central1 \
    --backup-vault=my-vault \
    --data-source=my-data-source \
    --name=restored-vm \
    --target-project=MY_PROJECT \
    --target-zone=us-central1-a
```

### 6. Inspect backup protection status

```bash
# Backup plan associations for a resource type in a location
gcloud backup-dr backup-plan-associations fetch-for-resource-type \
    compute.googleapis.com/Instance \
    --location=us-central1

# Protection summary metadata for resources in a location
gcloud backup-dr resource-backup-config list --location=us-central1

# Data sources within a vault
gcloud backup-dr data-sources list --backup-vault=my-vault --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `backup-dr backup-plan-associations` | [`backup-plan-associations.md`](backup-plan-associations.md) | 7 | manage Backup and DR backup plan associations |
| `backup-dr backup-plan-revisions` | [`backup-plan-revisions.md`](backup-plan-revisions.md) | 2 | view Backup and DR backup plan revisions |
| `backup-dr backup-plans` | [`backup-plans.md`](backup-plans.md) | 5 | manage Backup and DR backup plans |
| `backup-dr backup-vaults` | [`backup-vaults.md`](backup-vaults.md) | 5 | manage Backup and DR backup vaults |
| `backup-dr backups` | [`backups.md`](backups.md) | 7 | manage Backup and DR backups (incl. `restore compute` / `restore disk`) |
| `backup-dr data-source-references` | [`data-source-references.md`](data-source-references.md) | 3 | command group for Backup and DR Data Source References |
| `backup-dr data-sources` | [`data-sources.md`](data-sources.md) | 2 | view Backup and DR data sources |
| `backup-dr locations` | [`locations.md`](locations.md) | 1 | manage Backup and DR locations |
| `backup-dr management-servers` | [`management-servers.md`](management-servers.md) | 4 | manage Backup and DR management server |
| `backup-dr operations` | [`operations.md`](operations.md) | 2 | manage Backup and DR operations |
| `backup-dr resource-backup-config` | [`resource-backup-config.md`](resource-backup-config.md) | 1 | show protection summary for resources in a location and project |
| `backup-dr service-config` | [`service-config.md`](service-config.md) | 1 | manage Backup and DR Service configuration |

See [`index.md`](index.md) for a one-line index of all 40 commands.

## Common flags & tips

- **Location is required almost everywhere.** Most commands take `--location` (or accept a
  fully qualified resource name). `list` commands default to all locations when `--location`
  is omitted; `service-config init` and `resource-backup-config list` require `--location`.
- **Resource type format.** `--resource-type` values are API-typed, e.g.
  `compute.googleapis.com/Instance` or `sqladmin.googleapis.com/Instance`. The reference help
  renders this as `compute.<UNIVERSE_DOMAIN>.com/Instance` — substitute `googleapis.com` for
  standard Google Cloud.
- **Enforced retention syntax.** `--backup-min-enforced-retention` on `backup-vaults` uses
  relative-time format: `p1d`, `p1m`, `p1m1d` (also accepts e.g. `1d`). Once `--effective-time`
  is reached the period is locked and can only be extended; use
  `backup-vaults update --unlock-backup-min-enforced-retention` to remove the lock.
- **Backup-rule sub-properties** (in `--backup-rule`): `rule-id`, `retention-days`,
  `recurrence` (HOURLY/DAILY/WEEKLY/MONTHLY/YEARLY), `backup-window-start`, `backup-window-end`
  (start/end must be 6 hours apart), plus `hourly-frequency`, `days-of-week`, `days-of-month`,
  `months`, `week-day-of-month`, `time-zone`. `backup-plans update` also accepts
  `--add-backup-rule`, `--remove-backup-rule=RULE-ID`, and `--backup-rules-from-file`.
- **Async behavior is mixed.** `backup-plans`, `backup-plan-associations`, and `backups`
  commands default to `--async` (use `--no-async` to wait). `backup-vaults` and
  `service-config init` default to waiting and expose `--no-async` to wait explicitly.
- **Identifying a backup** for `backups describe/delete/update/restore` requires the trio
  `--backup-vault`, `--data-source`, and `--location` (or a fully qualified backup name).
- **Cross-project associations.** `backup-plan-associations` commands accept
  `--workload-project` to manage associations in a project different from the backup plan.
- **Useful filters/formats:**
  ```bash
  gcloud backup-dr backup-vaults list --location=us-central1 --format="table(name,state)"
  gcloud backup-dr resource-backup-config list --location=us-central1 \
      --filter="backup_configured=true" --sort-by="target_resource_display_name"
  gcloud backup-dr operations list --filter="done=false"
  ```

## beta / alpha

- `gcloud beta backup-dr` and `gcloud alpha backup-dr` expose the same 12 command groups as GA.
  Commands are marked as potentially changing without notice. Use these tiers to access pre-GA
  API features; no alpha/beta-exclusive command groups exist on the current 40-command surface.
- The `--network` flag on `management-servers create` is **DEPRECATED** in the GA reference —
  private service access is now configured separately.

## Official documentation

- [Backup and DR Service docs home](https://cloud.google.com/backup-disaster-recovery/docs) — product guides, getting started, concepts, and how-tos.
- [Access control (IAM)](https://cloud.google.com/backup-disaster-recovery/docs/access-control) — predefined roles (`backupdr.admin`, `backupdr.editor`, `backupdr.viewer`, vault-specific, service agent) and permissions.
- [gcloud backup-dr CLI reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr) — all 12 GA command groups (40 commands).
- [backup-vaults create reference](https://cloud.google.com/sdk/gcloud/reference/backup-dr/backup-vaults/create) — flags, enforced-retention syntax, examples.
- [gcloud beta backup-dr reference](https://cloud.google.com/sdk/gcloud/reference/beta/backup-dr) — beta surface.
- [gcloud alpha backup-dr reference](https://cloud.google.com/sdk/gcloud/reference/alpha/backup-dr) — alpha surface.
