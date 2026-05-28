---
name: gcloud-cli
description: >-
  Comprehensive gcloud CLI command reference for 120+ Google Cloud (GCP) services — Compute
  Engine, GKE/Kubernetes, Cloud Storage, IAM, Cloud SQL, Cloud Run, Cloud Functions,
  Pub/Sub, BigQuery, Spanner, Firestore, networking, KMS, Secret Manager, logging,
  monitoring, and many more. Every GA command is documented with its exhaustive flags, value
  types, choices, defaults, and examples, plus gcloud conventions (--format, --filter,
  --project, auth, config, output). Use this skill whenever the user works with Google Cloud
  via the command line: creating, listing, describing, updating, or deleting any GCP
  resource; writing or debugging gcloud scripts; authenticating or configuring gcloud; or
  asking how to accomplish something in GCP with the CLI. Trigger even when the user says
  only 'GCP' or 'Google Cloud', names a product (GKE, Cloud Run, BigQuery, Cloud SQL,
  Pub/Sub, etc.), or pastes a `gcloud` command, without explicitly saying 'gcloud'.
---

# gcloud CLI Reference

Complete `gcloud` command reference covering **121 Google Cloud services** and **5090 GA commands**. Every command is documented from the gcloud CLI's own help system (version-pinned, official) with full flags, value types, choices, defaults, synopses, and examples.

## How to use this skill

1. Find the service in the index below and open its **`overview.md`** — it has the common workflows, a command-group map, service-specific tips, and links to the official Google documentation the content was sourced from.
2. For a specific command's exhaustive flags, open the linked **command-group file** (e.g. `references/compute/instances.md`) or scan **`index.md`** for the one-line command list.
3. For output shaping, filtering, projects, auth, and other cross-service behavior, see [General gcloud conventions](#general-gcloud-conventions) below.

**Start by reading the `overview.md` for the service you need.**

## Service index

| Service | Reference | Scope | Official docs |
|---------|-----------|-------|---------------|
| `access-approval` | [`access-approval/overview.md`](references/access-approval/overview.md) | manage Access Approval requests and settings — requests, service-account, settings | [docs](https://docs.cloud.google.com/assured-workloads/access-approval/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/access-approval) |
| `access-context-manager` | [`access-context-manager/overview.md`](references/access-context-manager/overview.md) | manage Access Context Manager resources — authorized-orgs, cloud-bindings, levels, perimeters, policies, supported-services | [docs](https://cloud.google.com/access-context-manager/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/access-context-manager) |
| `active-directory` | [`active-directory/overview.md`](references/active-directory/overview.md) | manage Managed Microsoft AD resources — domains, operations, peerings | [docs](https://cloud.google.com/managed-microsoft-ad/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/active-directory) |
| `ai` | [`ai/overview.md`](references/ai/overview.md) | manage entities in Vertex AI — custom-jobs, endpoints, hp-tuning-jobs, index-endpoints, indexes, model-garden, model-monitoring-jobs, models | [docs](https://cloud.google.com/vertex-ai/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/ai) |
| `ai-platform` | [`ai-platform/overview.md`](references/ai-platform/overview.md) | manage AI Platform jobs and models — jobs, local, models, operations, versions | [docs](https://cloud.google.com/ai-platform/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/ai-platform) |
| `alloydb` | [`alloydb/overview.md`](references/alloydb/overview.md) | create and manage AlloyDB databases — backups, clusters, instances, operations, users | [docs](https://cloud.google.com/alloydb/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/alloydb) |
| `anthos` | [`anthos/overview.md`](references/anthos/overview.md) | anthos command Group — auth, config | [docs](https://cloud.google.com/kubernetes-engine/enterprise/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/anthos) |
| `api-gateway` | [`api-gateway/overview.md`](references/api-gateway/overview.md) | manage Cloud API Gateway resources — api-configs, apis, gateways, operations | [docs](https://cloud.google.com/api-gateway/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/api-gateway) |
| `apigee` | [`apigee/overview.md`](references/apigee/overview.md) | manage Apigee resources — apis, applications, deployments, developers, environments, organizations, products | [docs](https://cloud.google.com/apigee/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/apigee) |
| `app` | [`app/overview.md`](references/app/overview.md) | manage your App Engine deployments — domain-mappings, firewall-rules, instances, logs, operations, regions, runtimes, services | [docs](https://cloud.google.com/appengine/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/app) |
| `apphub` | [`apphub/overview.md`](references/apphub/overview.md) | manage App Hub resources — applications, boundary, discovered-services, discovered-workloads, locations, operations, service-projects | [docs](https://cloud.google.com/app-hub/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/apphub) |
| `artifacts` | [`artifacts/overview.md`](references/artifacts/overview.md) | manage Artifact Registry resources — apt, attachments, docker, files, generic, go, locations, operations | [docs](https://cloud.google.com/artifact-registry/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/artifacts) |
| `asset` | [`asset/overview.md`](references/asset/overview.md) | manage the Cloud Asset Inventory — feeds, operations, saved-queries | [docs](https://cloud.google.com/asset-inventory/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/asset) |
| `assured` | [`assured/overview.md`](references/assured/overview.md) | read and manipulate Assured Workloads data controls — operations, workloads | [docs](https://cloud.google.com/assured-workloads/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/assured) |
| `audit-manager` | [`audit-manager/overview.md`](references/audit-manager/overview.md) | enroll resources, audit workloads and generate reports — audit-reports, audit-scopes, enrollments, operations | [docs](https://cloud.google.com/audit-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/audit-manager) |
| `auth` | [`auth/overview.md`](references/auth/overview.md) | manage oauth2 credentials for the Google Cloud CLI — application-default, enterprise-certificate-config | [docs](https://cloud.google.com/sdk/docs/authorizing) · [ref](https://cloud.google.com/sdk/gcloud/reference/auth) |
| `backup-dr` | [`backup-dr/overview.md`](references/backup-dr/overview.md) | manage Backup and DR resources — backup-plan-associations, backup-plan-revisions, backup-plans, backup-vaults, backups, data-source-references, data-sources, locations | [docs](https://cloud.google.com/backup-disaster-recovery/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/backup-dr) |
| `batch` | [`batch/overview.md`](references/batch/overview.md) | manage Batch resources — jobs, tasks | [docs](https://cloud.google.com/batch/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/batch) |
| `beyondcorp` | [`beyondcorp/overview.md`](references/beyondcorp/overview.md) | manage Beyondcorp resources — operations, security-gateways | [docs](https://cloud.google.com/beyondcorp-enterprise/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/beyondcorp) |
| `bigtable` | [`bigtable/overview.md`](references/bigtable/overview.md) | manage your Cloud Bigtable storage — app-profiles, authorized-views, backups, clusters, hot-tablets, instances, logical-views, materialized-views | [docs](https://cloud.google.com/bigtable/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/bigtable) |
| `billing` | [`billing/overview.md`](references/billing/overview.md) | manage billing accounts and associate them with projects — accounts, budgets, projects | [docs](https://cloud.google.com/billing/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/billing) |
| `bms` | [`bms/overview.md`](references/bms/overview.md) | manage Bare Metal Solution resources — instances, networks, nfs-shares, operations, os-images, ssh-keys, volumes | [docs](https://cloud.google.com/bare-metal/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/bms) |
| `bq` | [`bq/overview.md`](references/bq/overview.md) | manage Bq resources — migration-workflows | [docs](https://cloud.google.com/bigquery/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/bq) |
| `builds` | [`builds/overview.md`](references/builds/overview.md) | create and manage builds for Google Cloud Build — connections, repositories, triggers, worker-pools | [docs](https://cloud.google.com/build/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/builds) |
| `certificate-manager` | [`certificate-manager/overview.md`](references/certificate-manager/overview.md) | manage SSL certificates for your Google Cloud projects — certificates, dns-authorizations, issuance-configs, maps, operations, trust-configs | [docs](https://cloud.google.com/certificate-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/certificate-manager) |
| `cloud-shell` | [`cloud-shell/overview.md`](references/cloud-shell/overview.md) | manage Google Cloud Shell | [docs](https://cloud.google.com/shell/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/cloud-shell) |
| `cloudlocationfinder` | [`cloudlocationfinder/overview.md`](references/cloudlocationfinder/overview.md) | manage Cloudlocationfinder resources — cloud-locations | [docs](https://docs.cloud.google.com/location-finder/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/cloudlocationfinder) |
| `colab` | [`colab/overview.md`](references/colab/overview.md) | manage Colab Enterprise resources — executions, runtime-templates, runtimes, schedules | [docs](https://cloud.google.com/colab/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/colab) |
| `compliance-manager` | [`compliance-manager/overview.md`](references/compliance-manager/overview.md) | manage Compliance Manager resources — cloud-control-deployments, cloud-controls, framework-deployments, frameworks, operations | [docs](https://cloud.google.com/security-command-center/docs/compliance-manager) · [ref](https://cloud.google.com/sdk/gcloud/reference/compliance-manager) |
| `components` | [`components/overview.md`](references/components/overview.md) | list, install, update, or remove Google Cloud CLI components — repositories | [docs](https://cloud.google.com/sdk/docs/components) · [ref](https://cloud.google.com/sdk/gcloud/reference/components) |
| `composer` | [`composer/overview.md`](references/composer/overview.md) | create and manage Cloud Composer Environments — environments, operations | [docs](https://cloud.google.com/composer/docs/concepts/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/composer) |
| `compute` | [`compute/overview.md`](references/compute/overview.md) | create and manipulate Compute Engine resources — accelerator-types, addresses, advice, backend-buckets, backend-services, commitments, diagnose, disk-types | [docs](https://cloud.google.com/compute/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/compute) |
| `config` | [`config/overview.md`](references/config/overview.md) | view and edit Google Cloud CLI properties — configurations | [docs](https://cloud.google.com/sdk/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/config) |
| `container` | [`container/overview.md`](references/container/overview.md) | deploy and manage clusters of machines for running containers — ai, attached, aws, azure, bare-metal, binauthz, clusters, fleet | [docs](https://docs.cloud.google.com/kubernetes-engine/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/container) |
| `data-catalog` | [`data-catalog/overview.md`](references/data-catalog/overview.md) | manage Data Catalog resources — entries, entry-groups, tag-templates, tags, taxonomies | [docs](https://cloud.google.com/data-catalog/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/data-catalog) |
| `database-migration` | [`database-migration/overview.md`](references/database-migration/overview.md) | manage Database Migration Service resources — connection-profiles, conversion-workspaces, migration-jobs, objects, operations, private-connections | [docs](https://cloud.google.com/database-migration/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/database-migration) |
| `dataflow` | [`dataflow/overview.md`](references/dataflow/overview.md) | manage Google Cloud Dataflow resources — flex-template, jobs, snapshots, yaml | [docs](https://cloud.google.com/dataflow/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/dataflow) |
| `dataplex` | [`dataplex/overview.md`](references/dataplex/overview.md) | manage Dataplex resources — aspect-types, assets, content, datascans, encryption-config, entries, entry-groups, entry-types | [docs](https://cloud.google.com/dataplex/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/dataplex) |
| `dataproc` | [`dataproc/overview.md`](references/dataproc/overview.md) | create and manage Google Cloud Dataproc clusters and jobs — autoscaling-policies, batches, clusters, jobs, node-groups, operations, workflow-templates | [docs](https://cloud.google.com/dataproc/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/dataproc) |
| `datastore` | [`datastore/overview.md`](references/datastore/overview.md) | manage your Cloud Datastore resources — indexes, operations | [docs](https://cloud.google.com/datastore/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/datastore) |
| `datastream` | [`datastream/overview.md`](references/datastream/overview.md) | manage Cloud Datastream resources — connection-profiles, locations, objects, operations, private-connections, routes, streams | [docs](https://cloud.google.com/datastream/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/datastream) |
| `deploy` | [`deploy/overview.md`](references/deploy/overview.md) | create and manage Cloud Deploy resources — automation-runs, automations, custom-target-types, delivery-pipelines, deploy-policies, job-runs, releases, rollouts | [docs](https://cloud.google.com/deploy/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/deploy) |
| `deployment-manager` | [`deployment-manager/overview.md`](references/deployment-manager/overview.md) | manage deployments of cloud resources — deployments, manifests, operations, resources, types | [docs](https://docs.cloud.google.com/deployment-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/deployment-manager) |
| `design-center` | [`design-center/overview.md`](references/design-center/overview.md) | manage Application Design Center resources — locations, operations, spaces | [docs](https://docs.cloud.google.com/application-design-center/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/design-center) |
| `developer-connect` | [`developer-connect/overview.md`](references/developer-connect/overview.md) | manage Developer Connect resources — connections, insights-configs, operations | [docs](https://cloud.google.com/developer-connect/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/developer-connect) |
| `dns` | [`dns/overview.md`](references/dns/overview.md) | manage your Cloud DNS managed-zones and record-sets — dns-keys, managed-zones, operations, policies, project-info, record-sets, response-policies | [docs](https://cloud.google.com/dns/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/dns) |
| `domains` | [`domains/overview.md`](references/domains/overview.md) | manage domains for your Google Cloud projects — registrations | [docs](https://docs.cloud.google.com/domains/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/domains) |
| `edge-cache` | [`edge-cache/overview.md`](references/edge-cache/overview.md) | manage Media CDN resources — keysets, operations, origins, services | [docs](https://cloud.google.com/media-cdn/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/edge-cache) |
| `edge-cloud` | [`edge-cloud/overview.md`](references/edge-cloud/overview.md) | manage edge-cloud resources — container, networking | [docs](https://docs.cloud.google.com/distributed-cloud/edge/latest/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/edge-cloud) |
| `emulators` | [`emulators/overview.md`](references/emulators/overview.md) | set up your local development environment using emulators — firestore, spanner | [docs](https://cloud.google.com/firestore/docs/emulator) · [ref](https://cloud.google.com/sdk/gcloud/reference/emulators) |
| `endpoints` | [`endpoints/overview.md`](references/endpoints/overview.md) | create, enable and manage API services — configs, operations, services | [docs](https://cloud.google.com/endpoints/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/endpoints) |
| `essential-contacts` | [`essential-contacts/overview.md`](references/essential-contacts/overview.md) | manage Essential Contacts | [docs](https://cloud.google.com/resource-manager/docs/managing-notification-contacts) · [ref](https://cloud.google.com/sdk/gcloud/reference/essential-contacts) |
| `eventarc` | [`eventarc/overview.md`](references/eventarc/overview.md) | manage Eventarc resources — audit-logs-provider, channel-connections, channels, enrollments, google-api-sources, google-channels, locations, message-buses | [docs](https://cloud.google.com/eventarc/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/eventarc) |
| `filestore` | [`filestore/overview.md`](references/filestore/overview.md) | create and manipulate Filestore resources — backups, instances, locations, operations, regions, zones | [docs](https://cloud.google.com/filestore/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/filestore) |
| `firebase` | [`firebase/overview.md`](references/firebase/overview.md) | work with Google Firebase — test | [docs](https://firebase.google.com/docs/test-lab) · [ref](https://cloud.google.com/sdk/gcloud/reference/firebase) |
| `firestore` | [`firestore/overview.md`](references/firestore/overview.md) | manage your Cloud Firestore resources — backups, databases, fields, indexes, locations, operations, user-creds | [docs](https://cloud.google.com/firestore/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/firestore) |
| `functions` | [`functions/overview.md`](references/functions/overview.md) | manage Google Cloud Functions — event-types, logs, regions, runtimes | [docs](https://cloud.google.com/functions/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/functions) |
| `gemini` | [`gemini/overview.md`](references/gemini/overview.md) | manage resources associated with Gemini Code Assist and Gemini Cloud Assist — code-repository-indexes, code-tools-settings, data-sharing-with-google-settings, gemini-gcp-enablement-settings, logging-settings, operations, release-channel-settings | [docs](https://cloud.google.com/gemini/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/gemini) |
| `healthcare` | [`healthcare/overview.md`](references/healthcare/overview.md) | manage Cloud Healthcare resources — consent-stores, datasets, dicom-stores, fhir-stores, hl7v2-stores, operations | [docs](https://cloud.google.com/healthcare-api/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/healthcare) |
| `iam` | [`iam/overview.md`](references/iam/overview.md) | manage IAM service accounts and keys — oauth-clients, policies, policy-bindings, principal-access-boundary-policies, roles, service-accounts, simulator, workforce-pools | [docs](https://cloud.google.com/iam/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/iam) |
| `iap` | [`iap/overview.md`](references/iap/overview.md) | manage IAP policies — oauth-brands, oauth-clients, settings, tcp, web | [docs](https://cloud.google.com/iap/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/iap) |
| `identity` | [`identity/overview.md`](references/identity/overview.md) | manage Cloud Identity Groups and Memberships resources | [docs](https://cloud.google.com/identity/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/identity) |
| `ids` | [`ids/overview.md`](references/ids/overview.md) | manage Cloud IDS — endpoints | [docs](https://cloud.google.com/intrusion-detection-system/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/ids) |
| `immersive-stream` | [`immersive-stream/overview.md`](references/immersive-stream/overview.md) | manage Immersive Stream resources — xr | [docs](https://cloud.google.com/immersive-stream/xr/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/immersive-stream) |
| `infra-manager` | [`infra-manager/overview.md`](references/infra-manager/overview.md) | manage Infra Manager resources — automigrationconfig, deployments, previews, resource-changes, resource-drifts, resources, revisions, terraform-versions | [docs](https://docs.cloud.google.com/infrastructure-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/infra-manager) |
| `kms` | [`kms/overview.md`](references/kms/overview.md) | manage cryptographic keys in the cloud — autokey-config, ekm-config, ekm-connections, import-jobs, inventory, key-handles, keyrings, keys | [docs](https://cloud.google.com/kms/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/kms) |
| `logging` | [`logging/overview.md`](references/logging/overview.md) | manage Cloud Logging — buckets, links, locations, logs, metrics, operations, resource-descriptors, scopes | [docs](https://cloud.google.com/logging/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/logging) |
| `looker` | [`looker/overview.md`](references/looker/overview.md) | manage Looker resources — backups, instances, operations, regions | [docs](https://cloud.google.com/looker/docs/looker-core-overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/looker) |
| `lustre` | [`lustre/overview.md`](references/lustre/overview.md) | manage Lustre resources — instances, operations | [docs](https://cloud.google.com/managed-lustre/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/lustre) |
| `managed-kafka` | [`managed-kafka/overview.md`](references/managed-kafka/overview.md) | administer Managed Service for Apache Kafka clusters, topics, and consumer groups — acls, clusters, connect-clusters, connectors, consumer-groups, operations, topics | [docs](https://cloud.google.com/managed-service-for-apache-kafka/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/managed-kafka) |
| `memcache` | [`memcache/overview.md`](references/memcache/overview.md) | manage Cloud Memorystore Memcached resources — instances, operations, regions | [docs](https://cloud.google.com/memorystore/docs/memcached) · [ref](https://cloud.google.com/sdk/gcloud/reference/memcache) |
| `memorystore` | [`memorystore/overview.md`](references/memorystore/overview.md) | manage Memorystore resources — backup-collections, instances, locations, operations | [docs](https://cloud.google.com/memorystore/docs/valkey) · [ref](https://cloud.google.com/sdk/gcloud/reference/memorystore) |
| `metastore` | [`metastore/overview.md`](references/metastore/overview.md) | manage Dataproc Metastore resources — federations, locations, operations, services | [docs](https://cloud.google.com/dataproc-metastore/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/metastore) |
| `migration` | [`migration/overview.md`](references/migration/overview.md) | the root group for various Cloud Migration teams — vms | [docs](https://cloud.google.com/migrate/virtual-machines/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/migration) |
| `ml` | [`ml/overview.md`](references/ml/overview.md) | use Google Cloud machine learning capabilities — language, speech, video, vision | [docs](https://cloud.google.com/natural-language/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/ml) |
| `model-armor` | [`model-armor/overview.md`](references/model-armor/overview.md) | model Armor is a service offering LLM-agnostic security and AI safety measures to mitigate risks associated with large language models (LLMs) — floorsettings, templates | [ref](https://cloud.google.com/sdk/gcloud/reference/model-armor) |
| `monitoring` | [`monitoring/overview.md`](references/monitoring/overview.md) | manage Cloud Monitoring dashboards — dashboards, policies, snoozes, uptime | [docs](https://cloud.google.com/monitoring/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/monitoring) |
| `netapp` | [`netapp/overview.md`](references/netapp/overview.md) | create and manipulate Cloud NetApp Files resources — active-directories, backup-policies, backup-vaults, host-groups, kms-configs, locations, operations, storage-pools | [docs](https://cloud.google.com/netapp/volumes/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/netapp) |
| `network-connectivity` | [`network-connectivity/overview.md`](references/network-connectivity/overview.md) | manage Network Connectivity resources — hubs, internal-ranges, locations, multicloud-data-transfer-configs, multicloud-data-transfer-supported-services, operations, policy-based-routes, regional-endpoints | [docs](https://cloud.google.com/network-connectivity/docs/network-connectivity-center) · [ref](https://cloud.google.com/sdk/gcloud/reference/network-connectivity) |
| `network-management` | [`network-management/overview.md`](references/network-management/overview.md) | manage Network Management resources — connectivity-tests, operations, vpc-flow-logs-configs | [docs](https://cloud.google.com/network-intelligence-center/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/network-management) |
| `network-security` | [`network-security/overview.md`](references/network-security/overview.md) | manage Network Security resources — address-groups, authorization-policies, authz-policies, backend-authentication-configs, client-tls-policies, dns-threat-detectors, firewall-endpoint-associations, firewall-endpoints | [docs](https://cloud.google.com/firewall/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/network-security) |
| `network-services` | [`network-services/overview.md`](references/network-services/overview.md) | manage Network Services resources — endpoint-policies, gateways, grpc-routes, http-routes, meshes, multicast-consumer-associations, multicast-domain-activations, multicast-domain-groups | [docs](https://docs.cloud.google.com/service-mesh/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/network-services) |
| `notebooks` | [`notebooks/overview.md`](references/notebooks/overview.md) | notebooks Command Group — environments, instances, locations, runtimes | [docs](https://cloud.google.com/vertex-ai/docs/workbench/introduction) · [ref](https://cloud.google.com/sdk/gcloud/reference/notebooks) |
| `observability` | [`observability/overview.md`](references/observability/overview.md) | manage Observability resources — scopes | [docs](https://cloud.google.com/stackdriver/docs/) · [ref](https://cloud.google.com/sdk/gcloud/reference/observability) |
| `oracle-database` | [`oracle-database/overview.md`](references/oracle-database/overview.md) | manage Oracle Database resources — autonomous-database-backups, autonomous-database-character-sets, autonomous-databases, autonomous-db-versions, cloud-exadata-infrastructures, cloud-vm-clusters, database-character-sets, databases | [docs](https://cloud.google.com/oracle/database/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/oracle-database) |
| `org-policies` | [`org-policies/overview.md`](references/org-policies/overview.md) | create and manage Organization Policies | [docs](https://cloud.google.com/resource-manager/docs/organization-policy/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/org-policies) |
| `organizations` | [`organizations/overview.md`](references/organizations/overview.md) | create and manage Google Cloud Platform Organizations | [docs](https://docs.cloud.google.com/resource-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/organizations) |
| `pam` | [`pam/overview.md`](references/pam/overview.md) | manage Privileged Access Manager entitlements and grants — entitlements, grants, operations | [docs](https://cloud.google.com/iam/docs/pam-overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/pam) |
| `parametermanager` | [`parametermanager/overview.md`](references/parametermanager/overview.md) | parameter Manager is a single source of truth to store, access and manage the lifecycle of your application parameters | [docs](https://cloud.google.com/secret-manager/parameter-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/parametermanager) |
| `policy-intelligence` | [`policy-intelligence/overview.md`](references/policy-intelligence/overview.md) | a platform to help better understand, use, and manage policies at scale — simulate, troubleshoot-policy | [docs](https://cloud.google.com/policy-intelligence/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/policy-intelligence) |
| `policy-troubleshoot` | [`policy-troubleshoot/overview.md`](references/policy-troubleshoot/overview.md) | troubleshoot Google Cloud Platform policies | [docs](https://cloud.google.com/policy-intelligence/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/policy-troubleshoot) |
| `privateca` | [`privateca/overview.md`](references/privateca/overview.md) | manage private Certificate Authorities on Google Cloud — certificates, locations, pools, roots, subordinates, templates | [docs](https://cloud.google.com/certificate-authority-service/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/privateca) |
| `projects` | [`projects/overview.md`](references/projects/overview.md) | create and manage project access policies | [docs](https://cloud.google.com/resource-manager/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/projects) |
| `publicca` | [`publicca/overview.md`](references/publicca/overview.md) | manage accounts for Google Trust Services' Certificate Authority — external-account-keys | [docs](https://cloud.google.com/certificate-manager/docs/public-ca) · [ref](https://cloud.google.com/sdk/gcloud/reference/publicca) |
| `pubsub` | [`pubsub/overview.md`](references/pubsub/overview.md) | manage Cloud Pub/Sub topics, subscriptions, and snapshots — lite-operations, lite-reservations, lite-subscriptions, lite-topics, message-transforms, schemas, snapshots, subscriptions | [docs](https://cloud.google.com/pubsub/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/pubsub) |
| `recaptcha` | [`recaptcha/overview.md`](references/recaptcha/overview.md) | manage reCAPTCHA Enterprise Keys — firewall-policies, keys | [docs](https://cloud.google.com/recaptcha/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/recaptcha) |
| `recommender` | [`recommender/overview.md`](references/recommender/overview.md) | manage Cloud recommendations and recommendation rules — insight-type-config, insights, recommendations, recommender-config | [docs](https://cloud.google.com/recommender/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/recommender) |
| `redis` | [`redis/overview.md`](references/redis/overview.md) | manage Cloud Memorystore Redis resources — clusters, instances, operations, regions, zones | [docs](https://cloud.google.com/memorystore/docs/redis) · [ref](https://cloud.google.com/sdk/gcloud/reference/redis) |
| `resource-manager` | [`resource-manager/overview.md`](references/resource-manager/overview.md) | manage Cloud Resources — capabilities, folders, org-policies, tags | [docs](https://cloud.google.com/resource-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/resource-manager) |
| `run` | [`run/overview.md`](references/run/overview.md) | manage your Cloud Run applications — domain-mappings, jobs, multi-region-services, regions, revisions, services | [docs](https://cloud.google.com/run/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/run) |
| `scc` | [`scc/overview.md`](references/scc/overview.md) | manage Cloud SCC resources — assets, bqexports, custom-modules, findings, iac-validation-reports, manage, muteconfigs, notifications | [docs](https://cloud.google.com/security-command-center/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/scc) |
| `scheduler` | [`scheduler/overview.md`](references/scheduler/overview.md) | manage Cloud Scheduler jobs and schedules — cmek-config, jobs, locations, operations | [docs](https://cloud.google.com/scheduler/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/scheduler) |
| `secrets` | [`secrets/overview.md`](references/secrets/overview.md) | manage secrets on Google Cloud — locations, replication, versions | [docs](https://cloud.google.com/secret-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/secrets) |
| `service-directory` | [`service-directory/overview.md`](references/service-directory/overview.md) | command groups for Service Directory — endpoints, locations, namespaces, services | [docs](https://cloud.google.com/service-directory/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/service-directory) |
| `service-extensions` | [`service-extensions/overview.md`](references/service-extensions/overview.md) | manage Service Extensions resources — authz-extensions, lb-edge-extensions, lb-route-extensions, lb-traffic-extensions, wasm-plugin-versions, wasm-plugins | [docs](https://cloud.google.com/service-extensions/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/service-extensions) |
| `services` | [`services/overview.md`](references/services/overview.md) | list, enable and disable APIs and services — api-keys, operations, peered-dns-domains, vpc-peerings | [docs](https://cloud.google.com/service-usage/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/services) |
| `source` | [`source/overview.md`](references/source/overview.md) | cloud git repository commands — project-configs, repos | [docs](https://cloud.google.com/source-repositories/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/source) |
| `source-manager` | [`source-manager/overview.md`](references/source-manager/overview.md) | manage Secure Source Manager resources — instances, locations, operations, repos | [docs](https://cloud.google.com/secure-source-manager/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/source-manager) |
| `spanner` | [`spanner/overview.md`](references/spanner/overview.md) | command groups for Cloud Spanner — backup-schedules, backups, databases, instance-configs, instance-partitions, instances, operations, rows | [docs](https://cloud.google.com/spanner/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/spanner) |
| `sql` | [`sql/overview.md`](references/sql/overview.md) | create and manage Google Cloud SQL databases — backups, databases, export, flags, import, instances, operations, ssl | [docs](https://cloud.google.com/sql/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/sql) |
| `storage` | [`storage/overview.md`](references/storage/overview.md) | create and manage Cloud Storage buckets and objects — batch-operations, buckets, folders, hmac, insights, intelligence-configs, managed-folders, objects | [docs](https://cloud.google.com/storage/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/storage) |
| `tasks` | [`tasks/overview.md`](references/tasks/overview.md) | manage Cloud Tasks queues and tasks — cmek-config, locations, queues | [docs](https://cloud.google.com/tasks/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/tasks) |
| `telco-automation` | [`telco-automation/overview.md`](references/telco-automation/overview.md) | manage Telco Automation resources — operations, orchestration-cluster | [docs](https://cloud.google.com/telecom-network-automation/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/telco-automation) |
| `topic` | [`topic/overview.md`](references/topic/overview.md) | gcloud supplementary help | [docs](https://cloud.google.com/sdk/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/topic) |
| `transcoder` | [`transcoder/overview.md`](references/transcoder/overview.md) | manage Transcoder jobs and job templates — jobs, templates | [docs](https://cloud.google.com/transcoder/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/transcoder) |
| `transfer` | [`transfer/overview.md`](references/transfer/overview.md) | manage Transfer Service jobs, operations, and agents — agent-pools, agents, jobs, operations | [docs](https://cloud.google.com/storage-transfer/docs/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/transfer) |
| `vmware` | [`vmware/overview.md`](references/vmware/overview.md) | manage Google Cloud VMware Engine resources — announcements, datastores, dns-bind-permission, locations, network-peerings, network-policies, networks, node-types | [docs](https://cloud.google.com/vmware-engine/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/vmware) |
| `workbench` | [`workbench/overview.md`](references/workbench/overview.md) | workbench Command Group — instances | [docs](https://cloud.google.com/vertex-ai/docs/workbench/overview) · [ref](https://cloud.google.com/sdk/gcloud/reference/workbench) |
| `workflows` | [`workflows/overview.md`](references/workflows/overview.md) | manage your Cloud Workflows resources — executions | [docs](https://cloud.google.com/workflows/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/workflows) |
| `workspace-add-ons` | [`workspace-add-ons/overview.md`](references/workspace-add-ons/overview.md) | manage Google Workspace Add-ons resources — deployments | [docs](https://developers.google.com/workspace/add-ons) · [ref](https://cloud.google.com/sdk/gcloud/reference/workspace-add-ons) |
| `workstations` | [`workstations/overview.md`](references/workstations/overview.md) | manage Cloud Workstations resources — clusters, configs | [docs](https://cloud.google.com/workstations/docs) · [ref](https://cloud.google.com/sdk/gcloud/reference/workstations) |

> **Release tracks:** this reference covers **GA** commands. Many services also expose additional commands under `gcloud beta <service>` and `gcloud alpha <service>`; each service overview notes where important capabilities are beta/alpha-only.

## Top-level CLI commands (not services)

These manage the CLI itself rather than cloud resources:

- `gcloud init` — interactive first-time setup (auth + default project/region).
- `gcloud auth` — manage credentials. See [`auth/overview.md`](references/auth/overview.md).
- `gcloud config` — view/set CLI properties (project, region, zone, account). See [`config/overview.md`](references/config/overview.md).
- `gcloud components` — install/update/remove CLI components. See [`components/overview.md`](references/components/overview.md).
- `gcloud info` — show CLI environment/diagnostics.  `gcloud version` — show component versions.

---

## General gcloud conventions

These behaviors apply across every `gcloud` command. (Run `gcloud topic <name>` locally for
the authoritative deep-dive on any of these — e.g. `gcloud topic formats`, `gcloud topic filters`.)

### Global flags (available on every command)

```
--project=PROJECT_ID              Override the active project for this command
--account=ACCOUNT                 Use a specific authenticated account
--impersonate-service-account=SA  Run as a service account via short-lived credentials
--billing-project=PROJECT_ID      Project to bill/quota for user-project-enabled APIs
--configuration=NAME              Use a named gcloud configuration
--format=FORMAT                   Output format (see below)
--filter=EXPRESSION               Client-side resource filtering (see below)
--sort-by=FIELDS                  Sort list output by resource fields (e.g. --sort-by=~creationTimestamp)
--limit=N                         Max resources to list
--page-size=N                     Server page size for list calls
--quiet, -q                       Disable interactive prompts; accept defaults (use in scripts)
--verbosity=LEVEL                 debug|info|warning|error|critical (default warning)
--flags-file=YAML                 Read flags from a YAML file
--flatten=KEY                     Flatten a repeated/nested field into separate records
--log-http                        Log raw HTTP requests/responses (debugging)
--user-output-enabled=false       Suppress normal output (keep --format output)
--help                            Full help for the command
```

### Output formats (`--format`)

By default gcloud pretty-prints. Override with `--format`:

```bash
gcloud compute instances list --format=json          # full JSON (machine-readable)
gcloud compute instances list --format=yaml          # YAML
gcloud compute instances list --format=text          # flat key: value lines (great for discovering field names)
gcloud compute instances list --format='table(name, zone, status)'   # custom table columns
gcloud compute instances list --format='value(name)'                 # bare values, one per line (scripting)
gcloud compute instances list --format='csv(name,zone,status)'       # CSV
```

- `value(...)` is the scripting workhorse — no headers, tab/newline separated:
  ```bash
  for i in $(gcloud compute instances list --format='value(name)'); do echo "$i"; done
  ```
- Discover available fields with `--format=text` or `--format=json` on a single resource:
  ```bash
  gcloud compute instances list --limit=1 --format=text
  ```
- Format attributes/transforms exist too, e.g. `--format='table(name, creationTimestamp.date())'`.

### Filtering (`--filter`)

Client-side selection of listed resources. Combine with `AND`, `OR`, `NOT`, parentheses.

```bash
gcloud compute instances list --filter="machineType:f1-micro"          # field contains
gcloud compute instances list --filter="zone ~ us"                     # regex match (~)
gcloud compute instances list --filter="status=RUNNING"                # equality
gcloud compute instances list --filter="tags.items=(web,prod)"         # any of
gcloud compute instances list --filter="tags.items=web AND -status=TERMINATED"
gcloud compute instances list --filter="creationTimestamp>2024-01-01"
```

Operators: `:` (contains/has-key), `=`/`!=`, `<`/`<=`/`>`/`>=`, `~`/`!~` (regex). `--filter` is
applied by the client after retrieval; some commands also support a server-side filter flag.

### Projects, regions, and configurations

```bash
gcloud config set project MY_PROJECT          # default project for all commands
gcloud config set compute/region us-central1  # default region
gcloud config set compute/zone us-central1-a  # default zone
gcloud config list                            # show active config
gcloud config configurations create staging   # named config (switch with --configuration or activate)
gcloud config configurations activate staging
```

Precedence: explicit `--project`/`--region`/`--zone` flag → active configuration property →
environment variable (`CLOUDSDK_CORE_PROJECT`, `CLOUDSDK_COMPUTE_REGION`, …).

### Authentication

```bash
gcloud auth login                              # user login (browser)
gcloud auth list                               # show credentialed accounts; * marks active
gcloud auth application-default login          # set up Application Default Credentials (ADC) for client libraries/Terraform
gcloud auth activate-service-account --key-file=key.json   # authenticate as a service account
gcloud auth print-access-token                 # short-lived OAuth token (e.g. for curl)
```

Prefer `--impersonate-service-account=SA@PROJECT.iam.gserviceaccount.com` over downloading
service-account keys when possible.

### Enabling APIs

Most services require their API to be enabled on the project first:

```bash
gcloud services enable compute.googleapis.com
gcloud services list --enabled
```

Each service `overview.md` notes the API to enable.

### Scripting tips

```bash
set -euo pipefail
PROJECT=$(gcloud config get-value project)
gcloud ... --quiet --format='value(...)'        # no prompts, parseable output
```

- `gcloud` exits non-zero on error — check `$?` or rely on `set -e`.
- Use `--quiet` to auto-confirm destructive operations in automation.
- Many long-running commands accept `--async` (return immediately with an operation) and have a
  matching `operations` subgroup or `--wait`/`wait` command to poll for completion.

### Release tracks: GA / beta / alpha

The same command often exists on multiple tracks:

```bash
gcloud compute instances create ...        # GA  (documented in this skill)
gcloud beta compute instances create ...   # beta: newer features, may change
gcloud alpha compute instances create ...  # alpha: earliest, may change/break
```

This skill documents the **GA** surface. When a capability is beta/alpha-only, the service
overview says so; prepend `beta` or `alpha` to the command (install the component if prompted).

## Sourcing & accuracy

All command and flag data is generated directly from the gcloud CLI's own help system (`gcloud <command> --help`, the canonical source Google publishes at `cloud.google.com/sdk/gcloud/reference`), pinned to the installed SDK version. Per-service conceptual docs, quickstarts, and how-to guides are linked from each service's `overview.md` and `sources.md` (official `cloud.google.com` sources only).
