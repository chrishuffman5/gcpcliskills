# gcloud compute — Compute Engine

## Overview

Compute Engine (GCE) is Google Cloud's IaaS for self-managed virtual machine instances running on KVM. Reach for `gcloud compute` to create and operate VMs, persistent/Hyperdisk disks and snapshots, custom images and machine images, VPC networks, subnets, firewall rules and routers/NAT, and the full Cloud Load Balancing stack (backend services, health checks, URL maps, target proxies, forwarding rules). It also covers reservations/commitments, instance groups and autoscaling, Cloud Armor security policies, interconnects/VPN, OS Config/patching, and Cloud TPUs. This is the largest gcloud surface — 790 GA commands across 67 groups.

Enable the API once per project before using any command:

```bash
gcloud services enable compute.googleapis.com
```

## Quick reference — common workflows

### Create a Linux VM and SSH in

```bash
gcloud compute zones list                                    # find a zone

gcloud compute instances create my-vm \
  --zone=us-central1-a \
  --machine-type=e2-medium \
  --image-family=debian-12 \
  --image-project=debian-cloud \
  --boot-disk-size=20GB \
  --boot-disk-type=pd-balanced \
  --tags=http-server

gcloud compute ssh my-vm --zone=us-central1-a               # SSH in (manages keys for you)
gcloud compute instances describe my-vm --zone=us-central1-a
```

### Stop, resize machine type, restart, delete

```bash
gcloud compute instances stop my-vm --zone=us-central1-a
gcloud compute instances set-machine-type my-vm \
  --zone=us-central1-a --machine-type=n2-standard-4         # must be stopped first
gcloud compute instances start my-vm --zone=us-central1-a
gcloud compute instances delete my-vm --zone=us-central1-a  # boot disk auto-deleted by default
```

### Create a data disk, attach it, snapshot it

```bash
gcloud compute disks create my-data-disk \
  --zone=us-central1-a --size=100GB --type=pd-ssd

gcloud compute instances attach-disk my-vm \
  --disk=my-data-disk --zone=us-central1-a

# Prefer `snapshots create` over the older `disks snapshot`
gcloud compute snapshots create my-snap \
  --source-disk=my-data-disk --source-disk-zone=us-central1-a \
  --snapshot-type=STANDARD
gcloud compute snapshots list
```

### Open a firewall rule

```bash
# Allow inbound HTTP to instances tagged http-server
gcloud compute firewall-rules create allow-http \
  --network=default \
  --direction=INGRESS \
  --action=ALLOW \
  --rules=tcp:80 \
  --source-ranges=0.0.0.0/0 \
  --target-tags=http-server

gcloud compute firewall-rules list
gcloud compute firewall-rules describe allow-http
```

### Custom VPC + subnet, then launch a VM in it (no external IP)

```bash
gcloud compute networks create my-vpc \
  --subnet-mode=custom --bgp-routing-mode=regional

gcloud compute networks subnets create my-subnet \
  --network=my-vpc --region=us-central1 --range=10.10.0.0/24

gcloud compute instances create my-vm-2 \
  --zone=us-central1-a --machine-type=e2-medium \
  --network=my-vpc --subnet=my-subnet \
  --image-family=debian-12 --image-project=debian-cloud \
  --no-address
```

### Capture a custom image and launch from it

```bash
gcloud compute instances stop my-vm --zone=us-central1-a    # quiesce the source disk

gcloud compute images create my-custom-image \
  --source-disk=my-vm --source-disk-zone=us-central1-a \
  --description="Custom Debian image with app pre-installed"

gcloud compute instances create my-vm-from-image \
  --zone=us-central1-a --machine-type=e2-medium \
  --image=my-custom-image
```

## Command groups

Groups roughly fall into: **compute/storage** (instances, instance-groups, instance-templates, disks, images, machine-images, snapshots, reservations); **networking** (networks, firewall-rules/-policies, routers, addresses, interconnects, vpn-*); **load balancing** (backend-services, health-checks, url-maps, target-*-proxies, forwarding-rules); **management** (os-config, os-login, operations, project-info); and **reference/read-only** lookups (zones, regions, machine-types, accelerator-types, disk-types).

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `compute accelerator-types` | [`accelerator-types.md`](accelerator-types.md) | 2 | read Compute Engine accelerator types |
| `compute addresses` | [`addresses.md`](addresses.md) | 5 | read and manipulate Compute Engine addresses |
| `compute advice` | [`advice.md`](advice.md) | 1 | provides recommendation on optimal allocation of resources according to a flexible specifications |
| `compute backend-buckets` | [`backend-buckets.md`](backend-buckets.md) | 11 | read and manipulate backend buckets |
| `compute backend-services` | [`backend-services.md`](backend-services.md) | 21 | list, create, and delete backend services |
| `compute commitments` | [`commitments.md`](commitments.md) | 5 | manage Compute Engine commitments |
| `compute diagnose` | [`diagnose.md`](diagnose.md) | 2 | debugging tools for Compute Engine virtual machine instances |
| `compute disk-types` | [`disk-types.md`](disk-types.md) | 2 | read Compute Engine virtual disk types |
| `compute disks` | [`disks.md`](disks.md) | 21 | read and manipulate Compute Engine disks |
| `compute external-vpn-gateways` | [`external-vpn-gateways.md`](external-vpn-gateways.md) | 5 | list, create, delete and update External VPN Gateways |
| `compute firewall-policies` | [`firewall-policies.md`](firewall-policies.md) | 17 | manage Compute Engine organization firewall policies |
| `compute firewall-rules` | [`firewall-rules.md`](firewall-rules.md) | 5 | list, create, update, and delete Compute Engine firewall rules |
| `compute forwarding-rules` | [`forwarding-rules.md`](forwarding-rules.md) | 8 | read and manipulate traffic forwarding rules to network load balancers |
| `compute future-reservations` | [`future-reservations.md`](future-reservations.md) | 6 | manage Compute Engine future reservations |
| `compute health-checks` | [`health-checks.md`](health-checks.md) | 17 | read and manipulate health checks for load balanced instances |
| `compute http-health-checks` | [`http-health-checks.md`](http-health-checks.md) | 5 | read and manipulate HTTP health checks for load balanced instances |
| `compute https-health-checks` | [`https-health-checks.md`](https-health-checks.md) | 5 | read and manipulate HTTPS health checks for load balanced instances |
| `compute images` | [`images.md`](images.md) | 15 | list, create, and delete Compute Engine images |
| `compute instance-groups` | [`instance-groups.md`](instance-groups.md) | 56 | read and manipulate Compute Engine instance groups |
| `compute instance-templates` | [`instance-templates.md`](instance-templates.md) | 9 | read and manipulate Compute Engine instances templates |
| `compute instances` | [`instances.md`](instances.md) | 58 | read and manipulate Compute Engine virtual machine instances |
| `compute instant-snapshots` | [`instant-snapshots.md`](instant-snapshots.md) | 5 | create, list and delete Compute Engine instant snapshots |
| `compute interconnects` | [`interconnects.md`](interconnects.md) | 66 | read and manipulate Compute Engine interconnects |
| `compute machine-images` | [`machine-images.md`](machine-images.md) | 9 | read and manage Compute Engine machine image resources |
| `compute machine-types` | [`machine-types.md`](machine-types.md) | 2 | read Compute Engine virtual machine types |
| `compute migration` | [`migration.md`](migration.md) | 9 | provides Migrate to Virtual Machines (VM migration) service functionality |
| `compute network-attachments` | [`network-attachments.md`](network-attachments.md) | 5 | manage Compute Engine network attachment resources |
| `compute network-edge-security-services` | [`network-edge-security-services.md`](network-edge-security-services.md) | 5 | read and manipulate network edge security services |
| `compute network-endpoint-groups` | [`network-endpoint-groups.md`](network-endpoint-groups.md) | 6 | read and manipulate Compute Engine network endpoint groups |
| `compute network-firewall-policies` | [`network-firewall-policies.md`](network-firewall-policies.md) | 19 | manage Compute Engine network firewall policies |
| `compute network-profiles` | [`network-profiles.md`](network-profiles.md) | 2 | read Compute Engine network profiles |
| `compute networks` | [`networks.md`](networks.md) | 31 | list, create, and delete Compute Engine networks |
| `compute operations` | [`operations.md`](operations.md) | 2 | read and manipulate Compute Engine operations |
| `compute org-security-policies` | [`org-security-policies.md`](org-security-policies.md) | 17 | manage Compute Engine organization security policies |
| `compute os-config` | [`os-config.md`](os-config.md) | 34 | manage OS Config tasks for Compute Engine VM instances |
| `compute os-login` | [`os-login.md`](os-login.md) | 7 | create and manipulate Compute Engine OS Login resources |
| `compute packet-mirrorings` | [`packet-mirrorings.md`](packet-mirrorings.md) | 5 | manage Compute Engine packet mirroring resources |
| `compute preview-features` | [`preview-features.md`](preview-features.md) | 3 | read and manipulate Compute Engine Preview Features |
| `compute project-info` | [`project-info.md`](project-info.md) | 5 | read and manipulate project-level data like quotas and metadata |
| `compute project-zonal-metadata` | [`project-zonal-metadata.md`](project-zonal-metadata.md) | 3 | describe and update project zonal metadata |
| `compute public-advertised-prefixes` | [`public-advertised-prefixes.md`](public-advertised-prefixes.md) | 5 | manage public advertised prefix resources |
| `compute public-delegated-prefixes` | [`public-delegated-prefixes.md`](public-delegated-prefixes.md) | 7 | manage public delegated prefix resources |
| `compute regions` | [`regions.md`](regions.md) | 2 | list Compute Engine regions |
| `compute reservations` | [`reservations.md`](reservations.md) | 17 | manage Compute Engine reservations |
| `compute resource-policies` | [`resource-policies.md`](resource-policies.md) | 12 | manage Compute Engine Resource Policies |
| `compute routers` | [`routers.md`](routers.md) | 34 | list, create, and delete Compute Engine routers |
| `compute routes` | [`routes.md`](routes.md) | 4 | read and manipulate routes |
| `compute security-policies` | [`security-policies.md`](security-policies.md) | 18 | read and manipulate Cloud Armor security policies |
| `compute service-attachments` | [`service-attachments.md`](service-attachments.md) | 5 | manage Compute Engine service attachment resources |
| `compute shared-vpc` | [`shared-vpc.md`](shared-vpc.md) | 8 | configure shared VPC |
| `compute snapshot-settings` | [`snapshot-settings.md`](snapshot-settings.md) | 2 | describe and update Compute Engine snapshot settings |
| `compute snapshots` | [`snapshots.md`](snapshots.md) | 11 | list, describe, and delete Compute Engine snapshots |
| `compute sole-tenancy` | [`sole-tenancy.md`](sole-tenancy.md) | 22 | read and manage Compute Engine sole-tenancy resources |
| `compute ssl-certificates` | [`ssl-certificates.md`](ssl-certificates.md) | 4 | list, create, and delete Compute Engine SSL certificate resources |
| `compute ssl-policies` | [`ssl-policies.md`](ssl-policies.md) | 6 | list, create, delete and update Compute Engine SSL policies |
| `compute storage-pool-types` | [`storage-pool-types.md`](storage-pool-types.md) | 2 | read storage pool types |
| `compute storage-pools` | [`storage-pools.md`](storage-pools.md) | 8 | read and manipulate storage pools |
| `compute target-grpc-proxies` | [`target-grpc-proxies.md`](target-grpc-proxies.md) | 4 | manage Compute Engine target gRPC proxy resources |
| `compute target-http-proxies` | [`target-http-proxies.md`](target-http-proxies.md) | 7 | list, create, and delete target HTTP proxies |
| `compute target-https-proxies` | [`target-https-proxies.md`](target-https-proxies.md) | 7 | list, create, and delete target HTTPS proxies |
| `compute target-instances` | [`target-instances.md`](target-instances.md) | 5 | read and manipulate Compute Engine virtual target instances |
| `compute target-pools` | [`target-pools.md`](target-pools.md) | 11 | control Compute Engine target pools for network load balancing |
| `compute target-ssl-proxies` | [`target-ssl-proxies.md`](target-ssl-proxies.md) | 5 | list, create, and delete target SSL proxies |
| `compute target-tcp-proxies` | [`target-tcp-proxies.md`](target-tcp-proxies.md) | 5 | list, create, and delete target TCP proxies |
| `compute target-vpn-gateways` | [`target-vpn-gateways.md`](target-vpn-gateways.md) | 4 | read and manipulate classic VPN gateways |
| `compute tpus` | [`tpus.md`](tpus.md) | 29 | list, create, and delete Cloud TPUs |
| `compute url-maps` | [`url-maps.md`](url-maps.md) | 15 | list, create, and delete URL maps |
| `compute vpn-gateways` | [`vpn-gateways.md`](vpn-gateways.md) | 6 | read and manipulate Highly Available VPN Gateways |
| `compute vpn-tunnels` | [`vpn-tunnels.md`](vpn-tunnels.md) | 4 | read and manipulate Compute Engine VPN tunnels |
| `compute zones` | [`zones.md`](zones.md) | 2 | list Compute Engine zones |

Top-level commands (`config-ssh`, `connect-to-serial-port`, `scp`, `ssh`, `reset-windows-password`, `sign-url`, `start-iap-tunnel`) live in [`_commands.md`](_commands.md). See [`index.md`](index.md) for a one-line index of all 790 commands.

## Common flags & tips

**Resource location** — most resources are zonal or regional and the scope flag is mandatory (or read from config):
- Zonal resources (instances, zonal disks): `--zone=ZONE`. Set a default with `gcloud config set compute/zone us-central1-a`.
- Regional resources (subnets, addresses, regional disks, routers): `--region=REGION`. Default: `gcloud config set compute/region us-central1`.
- Global resources (networks, firewall-rules, images, health-checks, url-maps, backend-services with `--global`): no zone/region; some commands take `--global` vs `--region` to disambiguate.

**Frequently used create flags:**
- `--machine-type=e2-medium|n2-standard-4|...` — shape of the VM (`gcloud compute machine-types list`).
- `--image-family=debian-12` + `--image-project=debian-cloud` — boot from the latest image in a public family (`ubuntu-os-cloud`, `rhel-cloud`, `windows-cloud`, etc.).
- `--boot-disk-size=`, `--boot-disk-type=pd-balanced|pd-ssd` — boot disk sizing.
- `--network=` / `--subnet=` — place the VM in a VPC/subnet; `--no-address` omits the external IP.
- `--tags=` — network tags used as firewall-rule targets.

**--filter / --format (apply to any `list`/`describe`):**
```bash
gcloud compute instances list --filter="status=RUNNING"
gcloud compute instances list --filter="zone:us-central1-a" \
  --format="table(name, machineType.basename(), status)"
gcloud compute disk-types list --filter="zone:us-central1-a"
gcloud compute machine-types list --filter="zone:us-central1-a"
gcloud compute instances describe my-vm --zone=us-central1-a \
  --format="value(networkInterfaces[0].accessConfigs[0].natIP)"   # public IP only
```

**Other tips:**
- `--async` returns immediately and prints an operation; track it with `gcloud compute operations describe/list`.
- Many destructive commands prompt; add the global `--quiet` to skip confirmation in scripts.
- SSH key management, OS Login, and IAP tunneling are built in: `gcloud compute ssh`, `gcloud compute config-ssh`, `gcloud compute start-iap-tunnel`.

## beta / alpha

Some capabilities are only on the non-GA surfaces (`gcloud beta compute` / `gcloud alpha compute`), which are not documented in these reference files:
- **Regional (scoped) snapshots** — `gcloud beta compute snapshots create --region=...` (Preview).
- Newer **Hyperdisk** and **Confidential Computing** options sometimes land first as beta flags on `instances create` / `disks create`.
- Some advanced scheduling and reservation/preview-feature options.

When a flag you expect is missing from GA, check `gcloud beta compute SUBGROUP --help` (or `alpha`).

## Official documentation

- [Compute Engine product documentation](https://cloud.google.com/compute/docs) — docs home: guides, how-tos, and concepts.
- [Compute Engine overview](https://cloud.google.com/compute/docs/overview) — IaaS definition, machine families, storage types, SLA.
- [Create and start a VM instance](https://cloud.google.com/compute/docs/instances/create-start-instance) — gcloud how-to for launching VMs.
- [Create persistent disk snapshots](https://cloud.google.com/compute/docs/disks/create-snapshots) — recommends `snapshots create` over `disks snapshot`.
- [Machine families resource guide](https://cloud.google.com/compute/docs/machine-resource) — general-purpose, compute-/memory-/storage-/accelerator-optimized families.
- [VPC firewall rules](https://cloud.google.com/compute/docs/firewalls) — components, direction, priority, logging.
- [Compute Engine IAM roles](https://cloud.google.com/compute/docs/access/iam) — predefined roles (`compute.admin`, `compute.instanceAdmin.v1`, etc.).
- [Linux VM quickstart](https://cloud.google.com/compute/docs/quickstart-linux) — end-to-end first VM walkthrough.
- [gcloud compute reference](https://cloud.google.com/sdk/gcloud/reference/compute) — full CLI reference for every command and flag.
