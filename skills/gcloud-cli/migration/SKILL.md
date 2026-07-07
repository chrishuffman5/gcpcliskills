---
name: gcloud-migration
description: >-
  Migrate to Virtual Machines via gcloud (`gcloud migration`). The root group for various Cloud Migration teams — vms.
---

# gcloud migration — Migrate to Virtual Machines

## Overview
`gcloud migration` is the root group for Google Cloud migration tooling; the GA surface exposes Migrate to Virtual Machines (formerly Velostrata), which migrates VM instances and disks from VMware on-premises, AWS, Azure, and Google Distributed Cloud VMware Engine into Compute Engine VMs or Persistent Disk volumes. Reach for it when you need to import virtual disk images (VMDK/VHD) or machine images (OVA/OVF) staged in Cloud Storage into Compute Engine. The GA commands cover image imports, machine image imports, and listing the target projects an import can land in.

## Quick reference — common workflows

### 1. Enable the API and list target projects
```bash
# Primary API required for all gcloud migration vms commands
gcloud services enable vmmigration.googleapis.com

# Target projects are defined per customer project in the global location
gcloud migration vms target-projects list
```

### 2. Import a virtual disk image (VMDK/VHD) to Compute Engine
```bash
# Stage the disk image in Cloud Storage first, then create the import resource
gcloud migration vms image-imports create my-image-import \
    --source-file=gs://my-images-bucket/my-ubuntu22.04.vmdk \
    --image-name=my-ubuntu-image \
    --location=us-central1 \
    --target-project=projects/my-project/locations/global/targetProjects/my-target-project \
    --project=my-project

# Track progress via the nested import job, then list all imports in the region
gcloud migration vms image-imports describe my-image-import --location=us-central1
gcloud migration vms image-imports list --location=us-central1
```

### 3. Import a machine image (OVA/OVF) to Compute Engine
```bash
gcloud migration vms machine-image-imports create my-machine-image-import \
    --source-file=gs://my-images-bucket/ub-14.04.5.ova \
    --machine-image-name=my-ubuntu-machine-image \
    --location=us-central1 \
    --target-project=projects/my-project/locations/global/targetProjects/my-target-project \
    --project=my-project

gcloud migration vms machine-image-imports describe my-machine-image-import --location=us-central1
```

### 4. Import a machine image with machine type, network and encryption
```bash
gcloud migration vms machine-image-imports create my-machine-image-import \
    --source-file=gs://my-images-bucket/server.ova \
    --machine-image-name=my-server-machine-image \
    --location=us-central1 \
    --machine-type=n2-standard-4 \
    --network-interface=network=my-vpc,subnetwork=my-subnet \
    --labels=env=prod,team=infra \
    --kms-key=projects/my-project/locations/us-central1/keyRings/my-ring/cryptoKeys/my-key \
    --target-project=projects/my-project/locations/global/targetProjects/my-target-project \
    --project=my-project
```

### 5. Import a disk image without OS adaptation (bring-your-own-image)
```bash
gcloud migration vms image-imports create my-raw-image-import \
    --source-file=gs://my-images-bucket/disk.raw.tar.gz \
    --image-name=my-raw-image \
    --location=us-central1 \
    --skip-os-adaptation \
    --single-region-storage \
    --target-project=projects/my-project/locations/global/targetProjects/my-target-project \
    --project=my-project
```

### 6. Clean up an import resource after completion
```bash
# Deleting the import resource does NOT delete the imported image / machine image
gcloud migration vms image-imports delete my-image-import --location=us-central1
gcloud migration vms machine-image-imports delete my-machine-image-import --location=us-central1
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `migration vms` | [`vms.md`](vms.md) | 9 | Migrate to Virtual Machines (VM migration) service functionality: `image-imports` (create/delete/describe/list), `machine-image-imports` (create/delete/describe/list), and `target-projects list` |

See [`index.md`](index.md) for a one-line index of all 9 commands.

## Common flags & tips
- **Resource location is required for most commands.** Supply `--location=LOCATION` (a region such as `us-central1`), provide a fully qualified resource name, or set the `compute/region` property. `target-projects list` is the exception — target projects always live in the `global` location.
- **Source must be in Cloud Storage.** `--source-file` takes a `gs://...` path; stage the VMDK/VHD/OVA/OVF (or `.raw.tar.gz`) there before creating the import. Grant the Migrate to Virtual Machines service account (`service-PROJECT_NUMBER@gcp-sa-vmmigration.iam.gserviceaccount.com`) `roles/storage.objectViewer` on that bucket.
- **Target project path format:** `--target-project=projects/PROJECT/locations/global/targetProjects/TARGET`. List valid values with `gcloud migration vms target-projects list`.
- **Naming defaults:** the resulting image/machine image defaults to the import name; override with `--image-name` (image-imports) or `--machine-image-name` (machine-image-imports).
- **OS adaptation:** `--skip-os-adaptation` imports the disk as-is; otherwise tune adaptation with `--adaptation-modifiers`, `--boot-conversion`, `--generalize`, `--license-type`, and `--rootfs-uuid`. `--additional-licenses` and `--single-region-storage` apply to both import types.
- **Machine-image-only flags:** `--machine-type`, `--network-interface=network=...,subnetwork=...,networkTier=...` (repeatable for multiple NICs), `--tags`, shielded-VM options (`--secure-boot`, `--enable-vtpm`, `--enable-integrity-monitoring`), and `--service-account`/`--scopes`.
- **Encryption:** protect imported images with a Cloud KMS key via `--kms-key=projects/.../cryptoKeys/KEY`.
- **Filtering/format on list:** the `list` commands accept the standard `--filter`, `--limit`, `--page-size`, `--sort-by`, and `--uri` flags, e.g. `gcloud migration vms image-imports list --location=us-central1 --filter="name~ubuntu" --format="table(name)"`.

## beta / alpha
- `gcloud alpha migration` adds a subgroup not present in GA: `gcloud alpha migration vms disk-migrations`, which manages disk migration operations (`cancel`, `create`, `delete`, `describe`, `fetch-inventory`, `list`, `run`, `update`).
- `target-projects list` is available in both GA and alpha; the `--target-project` flag help text points to the alpha command for listing target projects.
- There is no documented `gcloud beta migration` group — alpha is the pre-GA track for this service.

## Official documentation
- [Migrate to Virtual Machines documentation home](https://cloud.google.com/migrate/virtual-machines/docs) — product concepts, setup, and how-to guides.
- [Migrate to Virtual Machines 5.0 docs](https://cloud.google.com/migrate/virtual-machines/docs/5.0) — versioned documentation home for the current release.
- [Enabling Migrate to Virtual Machines services](https://cloud.google.com/migrate/virtual-machines/docs/5.0/get-started/enable-services) — required APIs and initial setup.
- [VM migration lifecycle](https://cloud.google.com/migrate/virtual-machines/docs/5.0/discover/lifecycle) — the six phases from onboarding to finalize.
- [Import virtual disk images](https://cloud.google.com/migrate/virtual-machines/docs/5.0/migrate/image_import) — importing VMDK/VHD/QCOW2 disks via gcloud.
- [Import machine images](https://cloud.google.com/migrate/virtual-machines/docs/5.0/migrate/machine-image-import) — importing OVA/OVF machine images via gcloud.
- [gcloud migration CLI reference](https://cloud.google.com/sdk/gcloud/reference/migration) — full command/flag reference.
- [gcloud alpha migration CLI reference](https://cloud.google.com/sdk/gcloud/reference/alpha/migration) — alpha-only subcommands (e.g. `disk-migrations`).
