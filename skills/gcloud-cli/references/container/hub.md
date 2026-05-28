# gcloud container hub

centrally manage features and services on all your Kubernetes clusters with fleet

### `gcloud container hub create`

Create a fleet

This command can fail for the following reasons:
  o The project specified does not exist.
  o The project specified already has a fleet.
  o The active account does not have permission to access the given
    project.

**Synopsis:**
```
gcloud container hub create [--async] [--display-name=DISPLAY_NAME]
    [--labels=[KEY=VALUE,...]]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE
      --binauthz-policy-bindings=[name=BINAUTHZ_POLICY]
      --security-posture=SECURITY_POSTURE
      --workload-vulnerability-scanning=WORKLOAD_VULNERABILITY_SCANNING]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Display name of the fleet to be created (optional). 4-30 characters, alphanumeric and [ '"!-] only. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a fleet in project example-foo-bar-1 with display name my-fleet,
run:

    $ gcloud container hub create --display-name=my-fleet \
        --project=example-foo-bar-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/create)

---
### `gcloud container hub delete`

Delete a fleet

This command can fail for the following reasons:
  o The project specified does not exist.
  o The project specified already has a fleet.
  o The active account does not have permission to access the given
    project.

**Synopsis:**
```
gcloud container hub delete [--async] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a fleet in project example-foo-bar-1, run:

    $ gcloud container hub delete --project=example-foo-bar-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/delete)

---
### `gcloud container hub describe`

Show fleet info

This command can fail for the following reasons:
  o The project specified does not exist.
  o The project specified does not have a fleet.
  o The active account does not have permission to access the given
    project.

**Synopsis:**
```
gcloud container hub describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To print metadata for the fleet in project example-foo-bar-1, run:

    $ gcloud container hub describe --project=example-foo-bar-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/describe)

---
### `gcloud container hub list`

List fleets visible to the user in an organization

This command can fail for the following reasons:
  o The org or project specified does not exist.
  o The user does not have access to the project specified.

**Synopsis:**
```
gcloud container hub list [--organization=ORGANIZATION_ID]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists fleets in organization 12345:

    $ gcloud container hub list --organization=12345
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/list)

---
### `gcloud container hub update`

Update a fleet

This command can fail for the following reasons:
  o The project specified does not exist.
  o The project specified already has a fleet.
  o The active account does not have permission to access the given
    project.

**Synopsis:**
```
gcloud container hub update [--async] [--display-name=DISPLAY_NAME]
    [--update-labels=[KEY=VALUE,...]]
    [--binauthz-evaluation-mode=BINAUTHZ_EVALUATION_MODE
      --binauthz-policy-bindings=[name=BINAUTHZ_POLICY]
      --security-posture=SECURITY_POSTURE
      --workload-vulnerability-scanning=WORKLOAD_VULNERABILITY_SCANNING]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--display-name` | DISPLAY_NAME |  | Display name of the fleet to be created (optional). 4-30 characters, alphanumeric and [ '"!-] only. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the display name of the fleet in project example-foo-bar-1 to
updated-name, run:

    $ gcloud container hub update --display-name=updated-name \
        --project=example-foo-bar-1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/update)

---

## `gcloud container hub cloudrun` — manage the CloudRun feature
### `gcloud container hub cloudrun apply`

Deploy or update the CloudRun feature

Deploy or update a user-specified config file of the CloudRun custom
resource. The config file should be a YAML file.

**Synopsis:**
```
gcloud container hub cloudrun apply
    (--gke-cluster=LOCATION/CLUSTER_NAME | --gke-uri=GKE_URI
      | [--context=CONTEXT : --kubeconfig=KUBECONFIG]) [--config=CONFIG]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gke-cluster` | LOCATION/CLUSTER_NAME |  | _[Exactly one of these must be specified:]_ The location/name of the GKE cluster. The location can be a zone or a region for e.g us-central1-a/my-cluster. |
| `--gke-uri` | GKE_URI |  | _[Exactly one of these must be specified:]_ The URI of a GKE cluster that you want to register to Hub; for example, 'https://container.googleapis.com/v1/projects/my-project/locations/us-central1-a/clusters/my-cluster'. To obtain the URI, you can run 'gcloud container clusters list --uri'. Note that this should only be provided if the cluster being registered is a GKE cluster. The service will validate the provided URI to confirm that it maps to a valid GKE cluster." |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config` | CONFIG |  | The path to CloudRun custom resource config file. |


**Examples:**
```bash
To apply the CloudRun YAML file, run:

    $ gcloud container hub cloudrun apply \
        --kubeconfig=/path/to/kubeconfig \
        --config=/path/to/cloud-run-cr.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/cloudrun/apply)

---
### `gcloud container hub cloudrun describe`

Describe the status of the CloudRun feature

**Synopsis:**
```
gcloud container hub cloudrun describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To get the detailed current status of the CloudRun Feature in Anthos
clusters, run:

    $ gcloud container hub cloudrun describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/cloudrun/describe)

---
### `gcloud container hub cloudrun disable`

Disable the CloudRun feature

This command disables the CloudRun feature in Anthos clusters.

**Synopsis:**
```
gcloud container hub cloudrun disable [--force] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Force disablement. Bypasses any prompts for confirmation. When disabling the entire feature, proceeds even if the feature is in use. Might result in unexpected behavior. |


**Examples:**
```bash
To disable the CloudRun Feature, run:

    $ gcloud container hub cloudrun disable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/cloudrun/disable)

---
### `gcloud container hub cloudrun enable`

Enable the CloudRun feature

This command enables the CloudRun feature in Anthos clusters.

**Synopsis:**
```
gcloud container hub cloudrun enable [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To enable the CloudRun Feature, run:

    $ gcloud container hub cloudrun enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/cloudrun/enable)

---

## `gcloud container hub clusterupgrade` — configure the Fleet clusterupgrade feature
### `gcloud container hub clusterupgrade create`

Create the clusterupgrade feature for a fleet within a given project

Create the clusterupgrade feature for a fleet within a given project.

**Synopsis:**
```
gcloud container hub clusterupgrade create
    [--default-upgrade-soaking=DEFAULT_UPGRADE_SOAKING]
    [--upstream-fleet=UPSTREAM_FLEET]
    [--add-upgrade-soaking-override=ADD_UPGRADE_SOAKING_OVERRIDE
      --upgrade-selector=[name=NAME],[version=VERSION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--default-upgrade-soaking` | DEFAULT_UPGRADE_SOAKING |  | Note: This flag only applies to Rollout Sequencing v1, not Rollout Sequencing v2 (which uses custom stages). If using Rollout Sequencing v1 and this flag is not provided, a default value of 7 days will be used. Configures the default soaking duration for each upgrade propagating through the current fleet to become "COMPLETE". Soaking begins after all clusters in the fleet are on the target version, or after 30 days if all cluster upgrades are not complete. Once an upgrade state becomes "COMPLETE", it will automatically be propagated to the downstream fleet. Max is 30 days. To configure Rollout Sequencing for a fleet, this attribute must be set. To do this while specifying a default soaking duration of 7 days, run: $ gcloud container hub clusterupgrade create \ --default-upgrade-soaking=7d |
| `--upstream-fleet` | UPSTREAM_FLEET |  | The upstream fleet. GKE will finish upgrades on the upstream fleet before applying the same upgrades to the current fleet. To configure the upstream fleet, run: $ gcloud container hub clusterupgrade create \ --upstream-fleet={upstream_fleet} |


**Examples:**
```bash
To create the clusterupgrade feature for the current fleet, run:

    $ gcloud container hub clusterupgrade create \
        --default-upgrade-soaking=DEFAULT_UPGRADE_SOAKING
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/clusterupgrade/create)

---
### `gcloud container hub clusterupgrade describe`

Describe the clusterupgrade feature for a fleet within a given project

Describe the Fleet clusterupgrade feature used for configuring fleet-based
rollout sequencing.

**Synopsis:**
```
gcloud container hub clusterupgrade describe
    [--show-linked-cluster-upgrade] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-linked-cluster-upgrade` |  |  | Shows the cluster upgrade feature information for the current fleet as well as information for all other fleets linked in the same rollout sequence (provided that the caller has permission to view the upstream and downstream fleets). This displays cluster upgrade information for fleets in the current fleet's rollout sequence in order of furthest upstream to downstream. To view the cluster upgrade feature information for the rollout sequence containing the current fleet, run: $ gcloud container hub clusterupgrade describe \ --show-linked-cluster-upgrade |


**Examples:**
```bash
To view the cluster upgrade feature information for the current fleet, run:

    $ gcloud container hub clusterupgrade describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/clusterupgrade/describe)

---
### `gcloud container hub clusterupgrade update`

Update the clusterupgrade feature for a fleet within a given project

Update the clusterupgrade feature for a fleet within a given project.

**Synopsis:**
```
gcloud container hub clusterupgrade update
    [--default-upgrade-soaking=DEFAULT_UPGRADE_SOAKING]
    [--remove-upgrade-soaking-overrides
      | --add-upgrade-soaking-override=ADD_UPGRADE_SOAKING_OVERRIDE
      --upgrade-selector=[name=NAME],[version=VERSION]]
    [--reset-upstream-fleet | --upstream-fleet=UPSTREAM_FLEET]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--default-upgrade-soaking` | DEFAULT_UPGRADE_SOAKING |  | Note: This flag only applies to Rollout Sequencing v1, not Rollout Sequencing v2 (which uses custom stages). If using Rollout Sequencing v1 and this flag is not provided, a default value of 7 days will be used. Configures the default soaking duration for each upgrade propagating through the current fleet to become "COMPLETE". Soaking begins after all clusters in the fleet are on the target version, or after 30 days if all cluster upgrades are not complete. Once an upgrade state becomes "COMPLETE", it will automatically be propagated to the downstream fleet. Max is 30 days. To configure Rollout Sequencing for a fleet, this attribute must be set. To do this while specifying a default soaking duration of 7 days, run: $ gcloud container hub clusterupgrade update \ --default-upgrade-soaking=7d |


**Examples:**
```bash
To update the clusterupgrade feature for the current fleet, run:

    $ gcloud container hub clusterupgrade update \
        --default-upgrade-soaking=DEFAULT_UPGRADE_SOAKING
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/clusterupgrade/update)

---

## `gcloud container hub config-management` — use the Config Management feature
### `gcloud container hub config-management describe`

Describe the Config Management feature

Describe the Config Management feature.

**Synopsis:**
```
gcloud container hub config-management describe [GCLOUD_WIDE_FLAG ...]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/config-management/describe)

---
### `gcloud container hub config-management disable`

Disable the Config Management feature

Disable the Config Management feature entirely, or disable specific
configuration on the feature.

gcloud container hub config-management disable without flags deletes the
Config Management feature, which unmanages and leaves existing Config Sync
installations on membership clusters. Running the command without flags
exits silently if the feature does not exist. Specify flags to disable
configuration on parts of the feature without deleting it.

**Synopsis:**
```
gcloud container hub config-management disable [--force]
    [--fleet-default-member-config | --uninstall --all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Force disablement. Bypasses any prompts for confirmation. When disabling the entire feature, proceeds even if the feature is in use. Might result in unexpected behavior. |


**Examples:**
```bash
To disable the Config Management feature entirely, run:

    $ gcloud container hub config-management disable

To unmanage Config Sync only on select memberships, run:

    $ gcloud container hub config-management disable \
        --memberships=example-membership-1,example-membership-2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/config-management/disable)

---

## `gcloud container hub dataplane-v2-encryption` — manage Dataplane V2 Encryption Feature
### `gcloud container hub dataplane-v2-encryption describe`

Describes the status of the Dataplane V2 Encryption Feature resource

This command gets the detailed status of the Dataplane V2 Encryption
Feature in a fleet.

**Synopsis:**
```
gcloud container hub dataplane-v2-encryption describe
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To describe the Dataplane V2 Encryption Feature, run:

    $ gcloud container hub dataplane-v2-encryption describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/dataplane-v2-encryption/describe)

---
### `gcloud container hub dataplane-v2-encryption disable`

Disables the Dataplane V2 Encryption Feature

This command disables the Dataplane V2 Encryption Feature in a fleet.

**Synopsis:**
```
gcloud container hub dataplane-v2-encryption disable [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Force disablement. Bypasses any prompts for confirmation. When disabling the entire feature, proceeds even if the feature is in use. Might result in unexpected behavior. |


**Examples:**
```bash
To disable the Dataplane V2 Encryption Feature, run:

    $ gcloud container hub dataplane-v2-encryption disable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/dataplane-v2-encryption/disable)

---
### `gcloud container hub dataplane-v2-encryption enable`

Enables the Dataplane V2 Encryption Feature

This command enables the Dataplane V2 Encryption Feature in a fleet.

**Synopsis:**
```
gcloud container hub dataplane-v2-encryption enable [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To enable the Dataplane V2 Encryption Feature, run:

    $ gcloud container hub dataplane-v2-encryption enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/dataplane-v2-encryption/enable)

---

## `gcloud container hub features` — manage Hub Feature resources
### `gcloud container hub features list`

List enabled features

List enabled fleet features in a project.

**Synopsis:**
```
gcloud container hub features list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + global is the only supported location. |


**Examples:**
```bash
To list all enabled fleet features in a project, run:

    $ gcloud container hub features list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/features/list)

---

## `gcloud container hub fleetobservability` — manage Fleet Observability Feature
### `gcloud container hub fleetobservability describe`

Describes the status of the Fleet Observability Feature resource

This command gets the detailed status of the Fleet Observability Feature in
a fleet.

**Synopsis:**
```
gcloud container hub fleetobservability describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To describe the Fleet Observability Feature, run:

    $ gcloud container hub fleetobservability describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/fleetobservability/describe)

---
### `gcloud container hub fleetobservability disable`

Disables the Fleet Observability Feature

This command disables Fleet Observability Feature in a fleet.

**Synopsis:**
```
gcloud container hub fleetobservability disable [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Force disablement. Bypasses any prompts for confirmation. When disabling the entire feature, proceeds even if the feature is in use. Might result in unexpected behavior. |


**Examples:**
```bash
To disable the Fleet Observability Feature, run:

    $ gcloud container hub fleetobservability disable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/fleetobservability/disable)

---
### `gcloud container hub fleetobservability enable`

Enables the Fleet Observability Feature

This command enables Fleet Observability Feature in a fleet.

**Synopsis:**
```
gcloud container hub fleetobservability enable [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To enable the Fleet Observability Feature, run:

    $ gcloud container hub fleetobservability enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/fleetobservability/enable)

---
### `gcloud container hub fleetobservability update`

Updates the Fleet Observability Feature resource

This command updates the Fleet Observability Feature in a fleet.

**Synopsis:**
```
gcloud container hub fleetobservability update
    [--logging-config=LOGGING_CONFIG] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--logging-config` | LOGGING_CONFIG |  | Path of the YAML(or JSON) file that contains the logging configurations. The JSON file is formatted as follows, with camelCase field naming: { "loggingConfig": { "defaultConfig": { "mode": "COPY" }, "fleetScopeLogsConfig": { "mode": "MOVE" } } } The YAML file is formatted as follows, with camelCase field naming: --- loggingConfig: defaultConfig: mode: COPY fleetScopeLogsConfig: mode: MOVE |


**Examples:**
```bash
To describe the Fleet Observability Feature, run:

    $ gcloud container hub fleetobservability update \
        --logging-config=LOGGING-CONFIG
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/fleetobservability/update)

---

## `gcloud container hub identity-service` — manage Identity Service Feature
### `gcloud container hub identity-service apply`

Update the Identity Service Feature

This command updates the Identity Service Feature in a fleet.

**Synopsis:**
```
gcloud container hub identity-service apply
    (--fleet-default-member-config=FLEET_DEFAULT_MEMBER_CONFIG
      [(--config=CONFIG | --origin=ORIGIN)
      : [--membership=MEMBERSHIP : --location=LOCATION]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-default-member-config` | FLEET_DEFAULT_MEMBER_CONFIG |  | _[At least one of these must be specified:]_ The path to an identity-service.yaml configuration file. |


**Examples:**
```bash
To apply an Identity Service configuration to a membership, run:

    $ gcloud container hub identity-service apply \
        --membership=MEMBERSHIP_NAME \
        --config=/path/to/identity-service.yaml

To create or modify a fleet-level default membership configuration, run:

    $ gcloud container hub identity-service apply \
        --fleet-default-member-config=/path/to/identity-service.yaml

To apply an existing fleet-level default membership configuration to a
membership, run:

    $ gcloud container hub identity-service apply --origin=fleet \
        --membership=MEMBERSHIP_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/identity-service/apply)

---
### `gcloud container hub identity-service delete`

Delete a resource from the Identity Service Feature

Deletes a resource from the Identity Service Feature.

**Synopsis:**
```
gcloud container hub identity-service delete
    [--fleet-default-member-config]
    [--membership=MEMBERSHIP : --location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-default-member-config` |  |  | If specified, deletes the default membership configuration present in your fleet. To delete the default membership configuration present in your fleet, run: $ gcloud container hub identity-service delete \ --fleet-default-member-config |


**Examples:**
```bash
To delete the Identity Service configuration from a membership, run:

    $ gcloud container hub identity-service delete \
        --membership=MEMBERSHIP_NAME

To delete the fleet-level default membership configuration, run:

    $ gcloud container hub identity-service delete \
        --fleet-default-member-config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/identity-service/delete)

---
### `gcloud container hub identity-service describe`

Prints the status of all clusters with Identity Service installed

Prints the status of the Identity Service Feature resource in a fleet.

**Synopsis:**
```
gcloud container hub identity-service describe [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To describe the status of the Identity Service configuration, run:

    $ gcloud container hub identity-service describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/identity-service/describe)

---
### `gcloud container hub identity-service disable`

Disable Identity Service Feature

This command disables the Identity Service Feature in a fleet.

**Synopsis:**
```
gcloud container hub identity-service disable [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Force disablement. Bypasses any prompts for confirmation. When disabling the entire feature, proceeds even if the feature is in use. Might result in unexpected behavior. |


**Examples:**
```bash
To disable the Identity Service Feature, run:

    $ gcloud container hub identity-service disable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/identity-service/disable)

---
### `gcloud container hub identity-service enable`

Enable the Identity Service Feature

This command enables the Identity Service Feature in a fleet.

**Synopsis:**
```
gcloud container hub identity-service enable
    [--fleet-default-member-config=FLEET_DEFAULT_MEMBER_CONFIG]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-default-member-config` | FLEET_DEFAULT_MEMBER_CONFIG |  | The path to an identity-service.yaml identity configuration file. If specified, this configuration would be the default Identity Service configuration for all memberships in your fleet. It could be overridden with a membership-specific configuration by using the the Apply command with the --config argument. To enable the Identity Service Feature with a fleet-level default membership configuration, run: $ gcloud container hub identity-service enable \ --fleet-default-member-config=/path/to/identity-service.yaml |


**Examples:**
```bash
To enable the Identity Service Feature, run:

    $ gcloud container hub identity-service enable

To enable the Identity Service Feature with a fleet-level default
membership configuration, run:

    $ gcloud container hub identity-service enable \
        --fleet-default-member-config=/path/to/identity-service.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/identity-service/enable)

---

## `gcloud container hub ingress` — manage Multi-cluster Ingress Feature
### `gcloud container hub ingress describe`

Describe the status of Multi-cluster Ingress Feature resource

This command describes the status of Multi-cluster Ingress Feature resource
in fleet.

**Synopsis:**
```
gcloud container hub ingress describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To describe the Ingress Feature, run:

    $ gcloud container hub ingress describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/ingress/describe)

---
### `gcloud container hub ingress disable`

Disable Multi-cluster Ingress Feature

This command disables Multi-cluster Ingress Feature in a fleet.

**Synopsis:**
```
gcloud container hub ingress disable [--force] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Force disablement. Bypasses any prompts for confirmation. When disabling the entire feature, proceeds even if the feature is in use. Might result in unexpected behavior. |


**Examples:**
```bash
To disable the Ingress Feature, run:

    $ gcloud container hub ingress disable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/ingress/disable)

---
### `gcloud container hub ingress enable`

Enable Multi-cluster Ingress Feature

This command enables Multi-cluster Ingress Feature in a fleet.

**Synopsis:**
```
gcloud container hub ingress enable
    [--config-membership=CONFIG_MEMBERSHIP : --location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-membership` | CONFIG_MEMBERSHIP |  | _[* set the property core/project.]_ ID of the membership or fully qualified identifier for the membership. To set the membership attribute: + provide the argument --config-membership on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location for the membership. To set the location attribute: + provide the argument --config-membership on the command line with a fully specified name; + provide the argument --location on the command line; + set the property gkehub/location. |


**Examples:**
```bash
To enable the Ingress Feature, run:

    $ gcloud container hub ingress enable \
        --config-membership=CONFIG_MEMBERSHIP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/ingress/enable)

---
### `gcloud container hub ingress update`

Update Multi-cluster Ingress Feature

This command updates Multi-cluster Ingress Feature in a fleet.

**Synopsis:**
```
gcloud container hub ingress update
    [--config-membership=CONFIG_MEMBERSHIP : --location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--config-membership` | CONFIG_MEMBERSHIP |  | _[* set the property core/project.]_ ID of the membership or fully qualified identifier for the membership. To set the membership attribute: + provide the argument --config-membership on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--location` | LOCATION |  | _[* set the property core/project.]_ Location for the membership. To set the location attribute: + provide the argument --config-membership on the command line with a fully specified name; + provide the argument --location on the command line; + set the property gkehub/location. |


**Examples:**
```bash
To update the Ingress Feature, run:

    $ gcloud container hub ingress update \
        --config-membership=CONFIG_MEMBERSHIP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/ingress/update)

---

## `gcloud container hub memberships` — manage memberships of all your GKE and other Kubernetes clusters with fleets
### `gcloud container hub memberships delete`

Delete a membership

This command deletes the Fleet Membership resource corresponding to the
cluster.

This command is intended to delete stale Fleet Membership resources as
doing so on a fully registered cluster will skip uninstalling the Connect
Agent and and orphan in-cluster resources and agent connections to Google.
To completely unregister the cluster, consider using the command: gcloud
container hub memberships unregister.

**Synopsis:**
```
gcloud container hub memberships delete (MEMBERSHIP : --location=LOCATION)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The cluster membership to delete. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument membership on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument membership on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument membership on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
First retrieve the ID of the membership using the command below. The output
of this command lists all the fleet's members, with their unique IDs in the
Names column:

    $ gcloud container hub memberships list

Delete a membership from the active project's fleet:

    $ gcloud container hub memberships delete MEMBERSHIP_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/delete)

---
### `gcloud container hub memberships describe`

Describe a membership

Describe a membership in a fleet.

**Synopsis:**
```
gcloud container hub memberships describe
    (MEMBERSHIP : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The cluster membership to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument membership on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument membership on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument membership on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
First retrieve the ID of the membership using the command below. The output
of this command lists all the fleet's members, with their unique IDs in the
NAME column:

    $ gcloud container hub memberships list

Then describe it:

    $ gcloud container hub memberships describe MEMBERSHIP
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/describe)

---
### `gcloud container hub memberships generate-gateway-rbac`

Generate RBAC policy files for connected clusters by the user

gcloud container hub memberships generate-gateway-rbac generates RBAC
policies to be used by Connect Gateway API.

Upon success, this command will write the output RBAC policy to the
designated local file in dry run mode.

Override RBAC policy: Y to override previous RBAC policy, N to stop. If
overriding the --role, Y will clean up the previous RBAC policy and then
apply the new one.

**Synopsis:**
```
gcloud container hub memberships generate-gateway-rbac
    (--anthos-support | --groups=GROUPS | --users=USERS) [--apply]
    [--context=CONTEXT] [--kubeconfig=KUBECONFIG] [--membership=MEMBERSHIP]
    [--rbac-output-file=RBAC_OUTPUT_FILE] [--revoke] [--role=ROLE]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--anthos-support` |  |  | _[Exactly one of these must be specified:]_ If specified, this command will generate RBAC policy file for anthos support. |
| `--groups` | GROUPS |  | _[Exactly one of these must be specified:]_ Group email address or third-party IAM group principal. |
| `--users` | USERS |  | _[Exactly one of these must be specified:]_ User's email address, service account email address, or third-party IAM subject principal. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--apply` |  |  | If specified, this command will generate RBAC policy and apply to the specified cluster. |
| `--context` | CONTEXT |  | The cluster context as it appears in the kubeconfig file. You can get this value from the command line by running command: kubectl config current-context. |
| `--kubeconfig` | KUBECONFIG |  | The kubeconfig file containing an entry for the cluster. Defaults to $KUBECONFIG if it is set in the environment, otherwise defaults to $HOME/.kube/config. |
| `--membership` | MEMBERSHIP |  | Membership name to assign RBAC policy with. |
| `--rbac-output-file` | RBAC_OUTPUT_FILE |  | If specified, this command will execute in dry run mode and write to the file specified with this flag: the generated RBAC policy will not be applied to Kubernetes clusters,instead it will be written to the designated local file. |
| `--revoke` |  |  | If specified, this command will revoke the RBAC policy for the specified users. |
| `--role` | ROLE |  | Namespace scoped role or cluster role. |


**Examples:**
```bash
The current implementation supports multiple modes:

Dry run mode to generate the RBAC policy file, and write to local
directory:

    $ gcloud container hub memberships generate-gateway-rbac \
        --membership=my-cluster \
        --users=foo@example.com,\
    test-acct@test-project.iam.gserviceaccount.com \
        --role=clusterrole/cluster-admin --rbac-output-file=./rbac.yaml

Dry run mode to generate the RBAC policy, and print on screen:

    $ gcloud container hub memberships generate-gateway-rbac \
        --membership=my-cluster \
        --users=foo@example.com,\
    test-acct@test-project.iam.gserviceaccount.com \
        --role=clusterrole/cluster-admin

Anthos support mode, generate the RBAC policy file with read-only
permission for TSE/Eng to debug customers' clusters:

    $ gcloud container hub memberships generate-gateway-rbac \
        --membership=my-cluster --anthos-support

Apply mode, generate the RBAC policy and apply it to the specified cluster:

    $ gcloud container hub memberships generate-gateway-rbac \
        --membership=my-cluster \
        --users=foo@example.com,\
    test-acct@test-project.iam.gserviceaccount.com \
        --role=clusterrole/cluster-admin --context=my-cluster-context \
        --kubeconfig=/home/user/custom_kubeconfig --apply

Revoke mode, revoke the RBAC policy for the specified users:

    $ gcloud container hub memberships generate-gateway-rbac \
        --membership=my-cluster \
        --users=foo@example.com,\
    test-acct@test-project.iam.gserviceaccount.com \
        --role=clusterrole/cluster-admin --context=my-cluster-context \
        --kubeconfig=/home/user/custom_kubeconfig --revoke

The role to be granted to the users can either be cluster-scoped or
namespace-scoped. To grant a namespace-scoped role to the users in dry run
mode, run:

    $ gcloud container hub memberships generate-gateway-rbac \
        --membership=my-cluster \
        --users=foo@example.com,\
    test-acct@test-project.iam.gserviceaccount.com \
        --role=role/mynamespace/namespace-reader

The users provided can be using a Google identity (only email) or using
external identity providers (starting with
"principal://iam.googleapis.com"):

    $ gcloud container hub memberships generate-gateway-rbac \
        --membership=my-cluster \
        --users=foo@example.com,principal://iam.googleapis.com/\
    locations/global/workforcePools/pool/subject/user \
        --role=clusterrole/cluster-admin --context=my-cluster-context \
        --kubeconfig=/home/user/custom_kubeconfig --apply

The groups can be provided as a Google identity (only email) or an external
identity (starting with "principalSet://iam.googleapis.com"):

    $ gcloud container hub memberships generate-gateway-rbac \
        --membership=my-cluster \
        --groups=group@example.com,principalSet://iam.googleapis.com/\
    locations/global/workforcePools/pool/group/ExampleGroup \
        --role=clusterrole/cluster-admin --context=my-cluster-context \
        --kubeconfig=/home/user/custom_kubeconfig --apply
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/generate-gateway-rbac)

---
### `gcloud container hub memberships get-credentials`

Fetch credentials for a fleet-registered cluster to be used in Connect Gateway

gcloud container hub memberships get-credentials updates the kubeconfig
file with the appropriate credentials and endpoint information to send
kubectl commands to a fleet-registered and -connected cluster through the
Connect Gateway service.

It takes a project, passed through by set defaults or flags. By default,
credentials are written to $HOME/.kube/config. You can provide an alternate
path by setting the KUBECONFIG environment variable. If KUBECONFIG contains
multiple paths, the first one is used.

Upon success, this command will switch the current context to the target
cluster if other contexts are already present in the kubeconfig file.

**Synopsis:**
```
gcloud container hub memberships get-credentials
    (MEMBERSHIP_NAME : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The group of arguments defining a membership. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MEMBERSHIP_NAME on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP_NAME
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument MEMBERSHIP_NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the membership resource, e.g. us-central1. If not
     specified, attempts to automatically choose the correct region.

     To set the location attribute:
     + provide the argument MEMBERSHIP_NAME on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.
```

**Examples:**
```bash
Get the Gateway kubeconfig for a globally registered cluster:

    $ gcloud container hub memberships get-credentials my-cluster
    $ gcloud container hub memberships get-credentials my-cluster \
        --location=global

Get the Gateway kubeconfig for a cluster registered in us-central1:

    $ gcloud container hub memberships get-credentials my-cluster \
        --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/get-credentials)

---
### `gcloud container hub memberships list`

List memberships

List memberships in a fleet.

**Synopsis:**
```
gcloud container hub memberships list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | _[* set the property core/project.]_ ID of the location or fully qualified identifier for the location. To set the location attribute: + provide the argument --location on the command line; + By default, all the locations are listed. |


**Examples:**
```bash
List memberships in the active project's fleet:

    $ gcloud container hub memberships list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/list)

---
### `gcloud container hub memberships register`

Register a cluster with a fleet

This command registers a cluster with the fleet by:

    1. Creating a Fleet Membership resource corresponding to the cluster.
    2. Adding in-cluster Kubernetes Resources that make the cluster exclusive
       to one fleet.
    3. Installing the Connect agent into this cluster (optional for GKE).

A successful registration implies that the cluster is now exclusive to a
single Fleet. If the cluster is already registered to another Fleet, the
registration will not be successful.

To register a GKE cluster, use --gke-cluster or --gke-uri flag (no
--kubeconfig flag is required). Connect agent will not be installed by
default for GKE clusters. To install it, specify --install-connect-agent.
The default value for --location is the same as the cluster's region or
zone, can be specified as global.

Anthos clusters on VMware, bare metal, AWS, and Azure are registered with a
fleet when the clusters are created. To register Amazon EKS clusters, see
Attach your EKS cluster
(https://cloud.google.com/anthos/clusters/docs/multi-cloud/attached/eks/how-to/attach-cluster).
To regiser Microsoft Azure clusters, see Attach your AKS cluster
(https://cloud.google.com/anthos/clusters/docs/multi-cloud/attached/aks/how-to/attach-cluster).

To register a third-party cluster, use --context flag (with an optional
--kubeconfig flag). Connect agent will always be installed for these
clusters.

If Connect agent is to be installed, its authentication needs to be
configured by --enable-workload-identity or --service-account-key-file. For
the latter case, the corresponding service account must have been granted
gkehub.connect permissions. For more information about Connect agent, go
to:
https://cloud.google.com/anthos/multicluster-management/connect/overview/

Rerunning this command against the same cluster with the same
MEMBERSHIP_NAME and target fleet is successful, and will upgrade the
Connect agent if it is supposed to be installed and a newer version is
available. Rerunning with --enable-workload-identity ensures that Workload
Identity is enabled on the cluster.

**Synopsis:**
```
gcloud container hub memberships register
    (MEMBERSHIP_NAME : --location=LOCATION)
    (--gke-cluster=LOCATION/CLUSTER_NAME | --gke-uri=GKE_URI
      | [--context=CONTEXT : --kubeconfig=KUBECONFIG])
    [--install-connect-agent] [--internal-ip]
    [--manifest-output-file=MANIFEST_OUTPUT_FILE] [--proxy=PROXY]
    [--service-account-key-file=SERVICE_ACCOUNT_KEY_FILE
      | [--enable-workload-identity : --has-private-issuer
      | --public-issuer-url=PUBLIC_ISSUER_URL]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The group of arguments defining a membership. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MEMBERSHIP_NAME on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP_NAME
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument MEMBERSHIP_NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location for the membership resource, e.g. us-central1. If not
     specified, defaults to global. Not supported for GKE clusters, whose
     membership location will be the location of the cluster.

     To set the location attribute:
     + provide the argument MEMBERSHIP_NAME on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gke-cluster` | LOCATION/CLUSTER_NAME |  | _[Exactly one of these must be specified:]_ The location/name of the GKE cluster. The location can be a zone or a region for e.g us-central1-a/my-cluster. |
| `--gke-uri` | GKE_URI |  | _[Exactly one of these must be specified:]_ The URI of a GKE cluster that you want to register to Hub; for example, 'https://container.googleapis.com/v1/projects/my-project/locations/us-central1-a/clusters/my-cluster'. To obtain the URI, you can run 'gcloud container clusters list --uri'. Note that this should only be provided if the cluster being registered is a GKE cluster. The service will validate the provided URI to confirm that it maps to a valid GKE cluster." |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--install-connect-agent` |  |  | If set to True for a GKE cluster, Connect agent will be installed in the cluster. No-op for Non-GKE clusters, where Connect agent will always be installed. |
| `--internal-ip` |  |  | Whether to use the internal IP address of the cluster endpoint. |
| `--manifest-output-file` | MANIFEST_OUTPUT_FILE |  | The full path of the file into which the Connect agent installation manifest should be stored. If this option is provided, then the manifest will be written to this file and will not be deployed into the cluster by gcloud, and it will need to be deployed manually. |
| `--proxy` | PROXY |  | The proxy address in the format of http[s]://{hostname}. The proxy must support the HTTP CONNECT method in order for this connection to succeed. |


**Examples:**
```bash
Register a non-GKE cluster referenced from a specific kubeconfig file, and
install the Connect agent:

    $ gcloud container hub memberships register my-cluster \
        --context=my-cluster-context \
        --kubeconfig=/home/user/custom_kubeconfig \
        --service-account-key-file=/tmp/keyfile.json

Register a non-GKE cluster referenced from the default kubeconfig file, and
install the Connect agent:

    $ gcloud container hub memberships register my-cluster \
        --context=my-cluster-context \
        --service-account-key-file=/tmp/keyfile.json

Register a non-GKE cluster, and install a specific version of the Connect
agent:

    $ gcloud container hub memberships register my-cluster \
        --context=my-cluster-context \
        --version=gkeconnect_20190802_02_00 \
        --service-account-key-file=/tmp/keyfile.json

Register a non-GKE cluster and output a manifest that can be used to
install the Connect agent by kubectl:

    $ gcloud container hub memberships register my-cluster \
        --context=my-cluster-context \
        --manifest-output-file=/tmp/manifest.yaml \
        --service-account-key-file=/tmp/keyfile.json

Register a GKE cluster referenced from a GKE URI:

    $ gcloud container hub memberships register my-cluster \
        --gke-uri=my-cluster-gke-uri

Register a GKE cluster referenced from a GKE URI, and install the Connect
agent using service account key file:

    $ gcloud container hub memberships register my-cluster \
        --gke-uri=my-cluster-gke-uri --install-connect-agent \
        --service-account-key-file=/tmp/keyfile.json

Register a GKE cluster and output a manifest that can be used to install
the Connect agent by kubectl:

    $ gcloud container hub memberships register my-cluster \
        --gke-uri=my-cluster-gke-uri --enable-workload-identity \
        --install-connect-agent \
        --manifest-output-file=/tmp/manifest.yaml

Register a GKE cluster first, and install the Connect agent later.

    $ gcloud container hub memberships register my-cluster \
        --gke-cluster=my-cluster-region-or-zone/my-cluster

    $ gcloud container hub memberships register my-cluster \
        --gke-cluster=my-cluster-region-or-zone/my-cluster \
        --install-connect-agent --enable-workload-identity

Register a GKE cluster, and install a specific version of the Connect
agent:

    $ gcloud container hub memberships register my-cluster \
        --gke-cluster=my-cluster-region-or-zone/my-cluster \
        --install-connect-agent --version=20220819-00-00 \
        --service-account-key-file=/tmp/keyfile.json

Register a GKE cluster and output a manifest that can be used to install
the Connect agent:

    $ gcloud container hub memberships register my-cluster \
        --gke-uri=my-cluster-gke-uri --install-connect-agent \
        --manifest-output-file=/tmp/manifest.yaml \
        --service-account-key-file=/tmp/keyfile.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/register)

---
### `gcloud container hub memberships unregister`

Unregister a cluster from a fleet

This command unregisters a cluster with the fleet by:

    1. Deleting the Fleet Membership resource for this cluster (a.k.a
       `gcloud container hub memberships delete`).
    2. Removing the corresponding in-cluster Kubernetes Resources that make the
       cluster exclusive to one fleet (a.k.a `kubectl delete memberships
       membership`).
    3. [Optional for GKE cluster] Uninstalling the Connect agent from this
       cluster (a.k.a `kubectl delete on the gke-connect namespace`).

The unregister command makes additional internal checks to ensure that all
three steps can be safely done to properly clean-up in-Fleet and in-cluster
resources.

To unregister a GKE cluster use --gke-cluster or --gke-uri flag (no
--kubeconfig flag is required).

To unregister a third-party cluster use --context flag (with an optional
--kubeconfig`s flag).

To only delete the Fleet Membership resource, consider using the command:
gcloud container hub memberships delete. This command is intended to delete
stale Fleet Membership resources as doing so on a fully registered cluster
will skip some of the steps above and orphan in-cluster resources and agent
connections to Google.

**Synopsis:**
```
gcloud container hub memberships unregister
    (MEMBERSHIP_NAME : --location=LOCATION)
    (--gke-cluster=LOCATION/CLUSTER_NAME | --gke-uri=GKE_URI
      | [--context=CONTEXT : --kubeconfig=KUBECONFIG])
    [--uninstall-connect-agent] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The group of arguments defining a membership. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MEMBERSHIP_NAME on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP_NAME
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument MEMBERSHIP_NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the membership resource, e.g. us-central1. If not
     specified, defaults to global.

     To set the location attribute:
     + provide the argument MEMBERSHIP_NAME on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--gke-cluster` | LOCATION/CLUSTER_NAME |  | _[Exactly one of these must be specified:]_ The location/name of the GKE cluster. The location can be a zone or a region for e.g us-central1-a/my-cluster. |
| `--gke-uri` | GKE_URI |  | _[Exactly one of these must be specified:]_ The URI of a GKE cluster that you want to register to Hub; for example, 'https://container.googleapis.com/v1/projects/my-project/locations/us-central1-a/clusters/my-cluster'. To obtain the URI, you can run 'gcloud container clusters list --uri'. Note that this should only be provided if the cluster being registered is a GKE cluster. The service will validate the provided URI to confirm that it maps to a valid GKE cluster." |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--uninstall-connect-agent` |  |  | If set to True for a GKE cluster, Connect agent will be uninstalled from the cluster. No-op for third-party clusters, where Connect agent will always be uninstalled. |


**Examples:**
```bash
Unregister a third-party cluster referenced from a specific kubeconfig
file:

    $ gcloud container hub memberships unregister my-membership \
        --context=my-cluster-context \
        --kubeconfig=/home/user/custom_kubeconfig

Unregister a third-party cluster referenced from the default kubeconfig
file:

    $ gcloud container hub memberships unregister my-membership \
        --context=my-cluster-context

Unregister a GKE cluster referenced from a GKE URI:

    $ gcloud container hub memberships unregister my-membership \
        --gke-uri=my-cluster-gke-uri

Unregister a GKE cluster referenced from a GKE Cluster location and name:

    $ gcloud container hub memberships unregister my-membership \
        --gke-cluster=my-cluster-region-or-zone/my-cluster

Unregister a GKE cluster and uninstall Connect agent:

    $ gcloud container hub memberships unregister my-membership \
        --gke-cluster=my-cluster-region-or-zone/my-cluster \
        --uninstall-connect-agent
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/unregister)

---
### `gcloud container hub memberships update`

Update a membership

Update an existing membership in a fleet.

**Synopsis:**
```
gcloud container hub memberships update (MEMBERSHIP : --location=LOCATION)
    [--async] [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - membership resource representing a cluster in Fleet.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument membership on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument membership on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument membership on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
First retrieve the ID of the membership using the command below. The output
of this command lists all the fleet's members, with their unique IDs in the
NAME column:

    $ gcloud container hub memberships list

Update a membership for a cluster:

    $ gcloud container hub memberships update MEMBERSHIP_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/update)

---

## `gcloud container hub memberships bindings` — membership Bindings for permissions
### `gcloud container hub memberships bindings create`

Create a Membership Binding

This command can fail for the following reasons:
  o The Membership Binding already exists.
  o The caller does not have permission to access the given Membership.
  o The Scope or the Membership does not exist.
  o The caller did not specify the location (--location) if referring to
    location other than global.

**Synopsis:**
```
gcloud container hub memberships bindings create
    (BINDING : --location=LOCATION --membership=MEMBERSHIP) --scope=SCOPE
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Binding resource - The group of arguments defining a Membership Binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument BINDING on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BINDING
     ID of the binding or fully qualified identifier for the binding.

     To set the binding attribute:
     + provide the argument BINDING on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location for the binding.

     To set the location attribute:
     + provide the argument BINDING on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.

  --membership=MEMBERSHIP
     Name of the binding.

     To set the membership attribute:
     + provide the argument BINDING on the command line with a fully
       specified name;
     + provide the argument --membership on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope` | SCOPE |  | ID of the scope or fully qualified identifier for the scope. To set the scope attribute: * provide the argument --scope on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create a membership binding BINDING_NAME in global membership
MEMBERSHIP_NAME for scope SCOPE_NAME, run:

    $ gcloud container hub memberships bindings create BINDING_NAME \
        --membership=MEMBERSHIP_NAME --scope=SCOPE_NAME

To create a Binding BINDING_NAME associated with regional membership
MEMBERSHIP_NAME, provide the location LOCATION_NAME for the Membership
where the Binding belongs along with membership name and associated Scope
SCOPE_NAME.

    $ gcloud container hub memberships bindings create BINDING_NAME \
        --membership=MEMBERSHIP_NAME --scope=SCOPE_NAME \
        --location=LOCATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/bindings/create)

---
### `gcloud container hub memberships bindings delete`

Delete a Membership Binding

This command can fail for the following reasons:
  o The Membership specified does not exist.
  o The Membership Binding specified does not exist.
  o The caller does not have permission to access the given Membership.
  o The caller did not specify the location (--location) if referring to
    location other than global.

**Synopsis:**
```
gcloud container hub memberships bindings delete
    (BINDING : --location=LOCATION --membership=MEMBERSHIP)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Binding resource - The group of arguments defining a Membership Binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument BINDING on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BINDING
     ID of the binding or fully qualified identifier for the binding.

     To set the binding attribute:
     + provide the argument BINDING on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location for the binding.

     To set the location attribute:
     + provide the argument BINDING on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.

  --membership=MEMBERSHIP
     Name of the binding.

     To set the membership attribute:
     + provide the argument BINDING on the command line with a fully
       specified name;
     + provide the argument --membership on the command line.
```

**Examples:**
```bash
To delete Membership Binding BINDING_NAME in global Membership
MEMBERSHIP_NAME for a global membership:

    $ gcloud container hub memberships bindings delete BINDING_NAME \
        --membership=MEMBERSHIP_NAME

To delete a Binding BINDING_NAME associated with regional membership
MEMBERSHIP_NAME, provide the location LOCATION_NAME for the Membership
where the Binding belongs along with the membership name.

    $ gcloud container hub memberships bindings delete BINDING_NAME \
        --membership=MEMBERSHIP_NAME --location=LOCATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/bindings/delete)

---
### `gcloud container hub memberships bindings describe`

Show Membership-Binding info

This command can fail for the following reasons:
  o The Membership specified does not exist.
  o The Membership Binding specified does not exist in the project.
  o The caller does not have permission to access the Membership Binding.
  o The caller did not specify the location (--location) if referring to
    location other than global.

**Synopsis:**
```
gcloud container hub memberships bindings describe
    (BINDING : --location=LOCATION --membership=MEMBERSHIP)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Binding resource - The group of arguments defining a Membership Binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument BINDING on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BINDING
     ID of the binding or fully qualified identifier for the binding.

     To set the binding attribute:
     + provide the argument BINDING on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location for the binding.

     To set the location attribute:
     + provide the argument BINDING on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.

  --membership=MEMBERSHIP
     Name of the binding.

     To set the membership attribute:
     + provide the argument BINDING on the command line with a fully
       specified name;
     + provide the argument --membership on the command line.
```

**Examples:**
```bash
To print metadata for the membership Binding BINDING_NAME in a global
membership MEMBERSHIP_NAME, run:

    $ gcloud container hub memberships bindings describe BINDING_NAME \
        --membership=MEMBERSHIP_NAME

To print metadata for the Binding BINDING_NAME associated with regional
membership MEMBERSHIP_NAME, provide the location LOCATION_NAME for the
Membership where the Binding belongs along with membership name.

    $ gcloud container hub memberships bindings describe BINDING_NAME \
        --membership=MEMBERSHIP_NAME --location=LOCATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/bindings/describe)

---
### `gcloud container hub memberships bindings list`

List Bindings in a Membership

This command can fail for the following reasons:
  o The Membership specified does not exist.
  o The user does not have access to the Membership specified.
  o The caller did not specify the location (--location) if referring to
    location other than global.

**Synopsis:**
```
gcloud container hub memberships bindings list --membership=MEMBERSHIP
    [--location=LOCATION; default="global"] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--membership` | MEMBERSHIP |  | Name of the Membership to list Bindings from. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | global | Name of the Membership location to list Bindings from. |


**Examples:**
```bash
The following command lists Bindings in global Membership MEMBERSHIP_NAME:

    $ gcloud container hub memberships bindings list \
        --membership=MEMBERSHIP_NAME

To list all the bindings associated with regional membership
MEMBERSHIP_NAME, provide the location LOCATION_NAME for the Membership
where the Binding belongs along with membership name.

    $ gcloud container hub memberships bindings list \
        --membership=MEMBERSHIP_NAME --location=LOCATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/bindings/list)

---
### `gcloud container hub memberships bindings update`

Update the Binding in a Membership

This command can fail for the following reasons:
  o The Membership specified does not exist.
  o The Binding does not exist in the Membership.
  o The caller does not have permission to access the Membership/Binding.
  o The Scope specified does not exist.
  o The caller did not specify the location (--location) if referring to
    location other than global.

**Synopsis:**
```
gcloud container hub memberships bindings update
    (BINDING : --location=LOCATION --membership=MEMBERSHIP) --scope=SCOPE
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Binding resource - The group of arguments defining a Membership Binding.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument BINDING on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  BINDING
     ID of the binding or fully qualified identifier for the binding.

     To set the binding attribute:
     + provide the argument BINDING on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location for the binding.

     To set the location attribute:
     + provide the argument BINDING on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.

  --membership=MEMBERSHIP
     Name of the binding.

     To set the membership attribute:
     + provide the argument BINDING on the command line with a fully
       specified name;
     + provide the argument --membership on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope` | SCOPE |  | ID of the scope or fully qualified identifier for the scope. To set the scope attribute: * provide the argument --scope on the command line. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the binding BINDING_NAME in global membership MEMBERSHIP_NAME in
the active project:

    $ gcloud container hub memberships bindings update BINDING_NAME \
        --membership=MEMBERSHIP_NAME

To update a Binding BINDING_NAME associated with regional membership
MEMBERSHIP_NAME, provide the location LOCATION_NAME for the Membership
where the Binding belongs along with membership name and associated Scope
SCOPE_NAME.

    $ gcloud container hub memberships bindings update BINDING_NAME \
        --membership=MEMBERSHIP_NAME --scope=SCOPE_NAME \
        --location=LOCATION_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/bindings/update)

---

## `gcloud container hub memberships support-access` — membership used for support access
### `gcloud container hub memberships support-access describe`

Describe support access for the specified membership

**Synopsis:**
```
gcloud container hub memberships support-access describe
    (MEMBERSHIP_NAME : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The group of arguments defining a membership. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MEMBERSHIP_NAME on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP_NAME
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument MEMBERSHIP_NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the membership resource, e.g. us-central1. If not
     specified, defaults to global.

     To set the location attribute:
     + provide the argument MEMBERSHIP_NAME on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.
```

**Examples:**
```bash
To describe support access for membership my-membership run:

    $ gcloud container hub memberships support-access describe \
        my-membership
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/support-access/describe)

---
### `gcloud container hub memberships support-access disable`

Disable support access for the specified membership

**Synopsis:**
```
gcloud container hub memberships support-access disable
    (MEMBERSHIP_NAME : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The group of arguments defining a membership. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MEMBERSHIP_NAME on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP_NAME
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument MEMBERSHIP_NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the membership resource, e.g. us-central1. If not
     specified, defaults to global.

     To set the location attribute:
     + provide the argument MEMBERSHIP_NAME on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.
```

**Examples:**
```bash
To disable support access for membership my-membership run:

    $ gcloud container hub memberships support-access disable \
        my-membership
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/support-access/disable)

---
### `gcloud container hub memberships support-access enable`

Enable support access for the specified membership

**Synopsis:**
```
gcloud container hub memberships support-access enable
    (MEMBERSHIP_NAME : --location=LOCATION) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The group of arguments defining a membership. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MEMBERSHIP_NAME on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP_NAME
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument MEMBERSHIP_NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the membership resource, e.g. us-central1. If not
     specified, defaults to global.

     To set the location attribute:
     + provide the argument MEMBERSHIP_NAME on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.
```

**Examples:**
```bash
To enable support access for membership my-membership run:

    $ gcloud container hub memberships support-access enable \
        my-membership
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/support-access/enable)

---
### `gcloud container hub memberships support-access get-yaml`

Generates YAML for anthos support RBAC policies

**Synopsis:**
```
gcloud container hub memberships support-access get-yaml
    (MEMBERSHIP_NAME : --location=LOCATION)
    [--rbac-output-file=RBAC_OUTPUT_FILE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Membership resource - The group of arguments defining a membership. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument MEMBERSHIP_NAME on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  MEMBERSHIP_NAME
     ID of the membership or fully qualified identifier for the
     membership.

     To set the membership attribute:
     + provide the argument MEMBERSHIP_NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location of the membership resource, e.g. us-central1. If not
     specified, defaults to global.

     To set the location attribute:
     + provide the argument MEMBERSHIP_NAME on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--rbac-output-file` | RBAC_OUTPUT_FILE |  | If specified, the generated RBAC policy will be written to the designated local file. |


**Examples:**
```bash
To generate the YAML for support access RBAC policies with membership
my-membership, run:

    $ gcloud container hub memberships support-access get-yaml \
        my-membership
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/memberships/support-access/get-yaml)

---

## `gcloud container hub mesh` — manage Service Mesh Feature
### `gcloud container hub mesh describe`

Describe the status of Service Mesh Feature resource

Describe the status of Service Mesh Feature resource in a fleet.

**Synopsis:**
```
gcloud container hub mesh describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To describe the Service Mesh Feature, run:

    $ gcloud container hub mesh describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/mesh/describe)

---
### `gcloud container hub mesh disable`

Disable Service Mesh Feature

Disable the Service Mesh Feature in a fleet.

**Synopsis:**
```
gcloud container hub mesh disable [--fleet-default-member-config] [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-default-member-config` |  |  | If specified, deletes the default membership configuration present in your fleet. To delete the fleet-level default Membership configuration present in your fleet, run: $ gcloud container hub mesh disable --fleet-default-member-config |
| `--force` |  |  | Disable this feature, even if it is currently in use. Force disablement may result in unexpected behavior. |


**Examples:**
```bash
To disable the Service Mesh Feature, run:

    $ gcloud container hub mesh disable

To delete the fleet-level default Membership configuration, run:

    $ gcloud container hub mesh disable --fleet-default-member-config
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/mesh/disable)

---
### `gcloud container hub mesh enable`

Enable Service Mesh Feature

Enable the Service Mesh Feature in a fleet.

**Synopsis:**
```
gcloud container hub mesh enable
    [--fleet-default-member-config=FLEET_DEFAULT_MEMBER_CONFIG]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-default-member-config` | FLEET_DEFAULT_MEMBER_CONFIG |  | The path to a service-mesh.yaml configuration file. To enable the Service Mesh Feature with a fleet-level default membership configuration, run: $ gcloud container hub mesh enable \ --fleet-default-member-config=/path/to/service-mesh.yaml |


**Examples:**
```bash
To enable the Service Mesh Feature, run:

    $ gcloud container hub mesh enable

To enable the Service Mesh Feature with a fleet-level default Membership
configuration, run:

    $ gcloud container hub mesh enable \
        --fleet-default-member-config=/path/to/service-mesh.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/mesh/enable)

---
### `gcloud container hub mesh update`

Update the configuration of the Service Mesh Feature

Update the Service Mesh Feature Spec of a Membership.

**Synopsis:**
```
gcloud container hub mesh update
    (--fleet-default-member-config=FLEET_DEFAULT_MEMBER_CONFIG
      | [(--origin=ORIGIN --config-api=CONFIG_API
      | --control-plane=CONTROL_PLANE | --management=MANAGEMENT)
      : [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]])
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-default-member-config` | FLEET_DEFAULT_MEMBER_CONFIG |  | _[Exactly one of these must be specified:]_ The path to a service-mesh.yaml configuration file. To enable the Service Mesh Feature with a fleet-level default membership configuration, run: $ gcloud container hub mesh update \ --fleet-default-member-config=/path/to/service-mesh.yaml |


**Examples:**
```bash
To update the control plane management of comma separated Memberships like
membership1,membership2, run:

    $ gcloud container hub mesh update \
        --memberships=membership1,membership2 \
        --control-plane=CONTROL_PLANE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/mesh/update)

---

## `gcloud container hub multi-cluster-services` — manage Multi-cluster Services Feature
### `gcloud container hub multi-cluster-services describe`

Describe the status of the Multi-cluster Services Feature resource

This command gets the detailed status of the Multi-cluster Services Feature
in a fleet.

**Synopsis:**
```
gcloud container hub multi-cluster-services describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To describe the Multi-cluster Services Feature, run:

    $ gcloud container hub multi-cluster-services describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/multi-cluster-services/describe)

---
### `gcloud container hub multi-cluster-services disable`

Disable the Multi-cluster Services Feature

This command disables the Multi-cluster Services Feature in a fleet.

**Synopsis:**
```
gcloud container hub multi-cluster-services disable [--force]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | Force disablement. Bypasses any prompts for confirmation. When disabling the entire feature, proceeds even if the feature is in use. Might result in unexpected behavior. |


**Examples:**
```bash
To disable the Multi-cluster Services Feature, run:

    $ gcloud container hub multi-cluster-services disable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/multi-cluster-services/disable)

---
### `gcloud container hub multi-cluster-services enable`

Enable the Multi-cluster Services Feature

This command enables the Multi-cluster Services Feature in a fleet.

**Synopsis:**
```
gcloud container hub multi-cluster-services enable [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To enable the Multi-cluster Services Feature, run:

    $ gcloud container hub multi-cluster-services enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/multi-cluster-services/enable)

---

## `gcloud container hub operations` — manage Anthos fleet long-running operations
### `gcloud container hub operations describe`

Describe a long-running operation

Describe a long-running operation.

**Synopsis:**
```
gcloud container hub operations describe
    (OPERATION : --location=LOCATION; default="global")
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - operation to describe. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the name attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION; default="global"
     Google Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To describe a long-running operation in location us-west1, run:

    $ gcloud container hub operations describe OPERATION \
        --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/operations/describe)

---
### `gcloud container hub operations list`

List long-running operations

List long-running operations.

**Synopsis:**
```
gcloud container hub operations list [--location=LOCATION; default="-"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION | - | The location name. |


**Examples:**
```bash
To list all operations in location us-west1, run:

    $ gcloud container hub operations list --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/operations/list)

---
### `gcloud container hub operations wait`

Poll a long-running operation for completion

Poll a long-running operation for completion.

**Synopsis:**
```
gcloud container hub operations wait
    (OPERATION : --location=LOCATION; default="global")
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Operation resource - operation to wait. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument operation on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  OPERATION
     ID of the operation or fully qualified identifier for the operation.

     To set the name attribute:
     + provide the argument operation on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION; default="global"
     Google Cloud location for the operation.

     To set the location attribute:
     + provide the argument operation on the command line with a fully
       specified name;
     + provide the argument --location on the command line.
```

**Examples:**
```bash
To wait for an operation in location us-west1 to complete, run:

    $ gcloud container hub operations wait OPERATION --location=us-west1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/operations/wait)

---

## `gcloud container hub packages` — manage Fleet Packages resources
### `gcloud container hub packages create`

Create Package Rollouts Fleet Package

Create Package Rollouts Fleet Package.

**Synopsis:**
```
gcloud container hub packages create NAME --source=SOURCE
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Resource name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Source file containing Fleet Package configuration. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To create Fleet Package cert-manager-app, run:

    $ gcloud container hub packages create cert-manager-app \
         --source=source.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/create)

---
### `gcloud container hub packages delete`

Delete Package Rollouts Fleet Package

Delete Package Rollouts Fleet Package.

**Synopsis:**
```
gcloud container hub packages delete (FLEET_PACKAGE : --location=LOCATION)
    [--force] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Fleet package resource - The Fleet Package to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument fleet_package on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  FLEET_PACKAGE
     ID of the fleet-package or fully qualified identifier for the
     fleet-package.

     To set the fleet-package attribute:
     + provide the argument fleet_package on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud zone or region for the fleet-package.

     To set the location attribute:
     + provide the argument fleet_package on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property config_delivery/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If true, force deletion of any child resources. Otherwise, attempting to delete a Fleet Package with children will fail. |


**Examples:**
```bash
To delete Fleet Package cert-manager-app in us-central1, run:

    $ gcloud container hub packages delete cert-manager-app \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/delete)

---
### `gcloud container hub packages describe`

Describe Package Rollouts Fleet Package

Describe Package Rollouts Fleet Package.

**Synopsis:**
```
gcloud container hub packages describe
    (FLEET_PACKAGE : --location=LOCATION) [--show-cluster-status]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Fleet package resource - The Fleet Package to describe. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument fleet_package on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  FLEET_PACKAGE
     ID of the fleet-package or fully qualified identifier for the
     fleet-package.

     To set the fleet-package attribute:
     + provide the argument fleet_package on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud zone or region for the fleet-package.

     To set the location attribute:
     + provide the argument fleet_package on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property config_delivery/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-cluster-status` |  |  | Show more information about the Fleet Package. |


**Examples:**
```bash
To view Fleet Package cert-manager-app in us-central1, run:

    $ gcloud container hub packages describe cert-manager-app \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/describe)

---
### `gcloud container hub packages list`

List Package Rollouts Fleet Packages

List Package Rollouts Fleet Packages.

**Synopsis:**
```
gcloud container hub packages list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To list all Fleet Packages in us-central1, run:

    $ gcloud container hub packages list --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/list)

---
### `gcloud container hub packages update`

Update Package Rollouts Fleet Package

Update Package Rollouts Fleet Package.

**Synopsis:**
```
gcloud container hub packages update (FLEET_PACKAGE : --location=LOCATION)
    --source=SOURCE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Fleet package resource - The Fleet Package to create. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument fleet_package on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  FLEET_PACKAGE
     ID of the fleet-package or fully qualified identifier for the
     fleet-package.

     To set the fleet-package attribute:
     + provide the argument fleet_package on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Google Cloud zone or region for the fleet-package.

     To set the location attribute:
     + provide the argument fleet_package on the command line with a
       fully specified name;
     + provide the argument --location on the command line;
     + set the property config_delivery/location.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source` | SOURCE |  | Source file containing Fleet Package configuration. |


**Examples:**
```bash
To update Fleet Package cert-manager-app, run:

    $ gcloud container hub packages update cert-manager-app \
         --source=my_source.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/update)

---

## `gcloud container hub packages resource-bundles` — commands for managing Package Rollouts Resource Bundles
### `gcloud container hub packages resource-bundles create`

Create Package Rollouts Resource Bundle

Create Package Rollouts Resource Bundle.

**Synopsis:**
```
gcloud container hub packages resource-bundles create NAME
    [--description=DESCRIPTION] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Resource name.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Resource description. |
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To create Resource Bundle cert-manager in us-central1, run:

    $ gcloud container hub packages resource-bundles create \
         cert-manager --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/create)

---
### `gcloud container hub packages resource-bundles delete`

Delete Package Rollouts Resource Bundle

Delete Package Rollouts Resource Bundle.

**Synopsis:**
```
gcloud container hub packages resource-bundles delete NAME [--force]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Resource name.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If true, force deletion of any child resources. Otherwise, attempting to delete a Resource Bundle with children will fail. |
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To delete Resource Bundle cert-manager in us-central1, run:

    $ gcloud container hub packages resource-bundles delete \
         cert-manager --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/delete)

---
### `gcloud container hub packages resource-bundles describe`

Describe Package Rollouts Resource Bundle

Describe Package Rollouts Resource Bundle.

**Synopsis:**
```
gcloud container hub packages resource-bundles describe NAME
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Resource name.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To describe Resource Bundle cert-manager in us-central1, run:

    $ gcloud container hub packages resource-bundles describe \
         cert-manager --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/describe)

---
### `gcloud container hub packages resource-bundles list`

List Package Rollouts Resource Bundles

List Package Rollouts Resource Bundles.

**Synopsis:**
```
gcloud container hub packages resource-bundles list [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To list Resource Bundles in us-central1, run:

    $ gcloud container hub packages resource-bundles list \
         --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/list)

---
### `gcloud container hub packages resource-bundles update`

Update Package Rollouts Resource Bundle

Update Package Rollouts Resource Bundle.

**Synopsis:**
```
gcloud container hub packages resource-bundles update NAME
    [--description=DESCRIPTION] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Resource name.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Resource description. |
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To update Resource Bundle cert-manager in us-central1, run:

    $ gcloud container hub packages resource-bundles update \
         cert-manager --location=us-central1 ...
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/update)

---

## `gcloud container hub packages resource-bundles releases` — commands for managing Package Rollouts Releases
### `gcloud container hub packages resource-bundles releases create`

Create Package Rollouts Release

Create Package Rollouts Release.

**Synopsis:**
```
gcloud container hub packages resource-bundles releases create
    --resource-bundle=RESOURCE_BUNDLE --source=SOURCE --version=VERSION
    [--lifecycle=LIFECYCLE] [--location=LOCATION]
    [--variants-pattern=VARIANTS_PATTERN; default="*"]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-bundle` | RESOURCE_BUNDLE |  | Resource Bundle name. |
| `--source` | SOURCE |  | Source file or directory to create the Release from. e.g. --source=manifest.yaml, --source=/manifests-dir/ Can optionally be paired with the --variants-pattern arg to create multiple variants of a Release. |
| `--version` | VERSION |  | Version of the Release to create. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--lifecycle` | LIFECYCLE |  | Lifecycle of the Release. |
| `--location` | LOCATION |  | Google Cloud zone or region. |
| `--variants-pattern` | VARIANTS_PATTERN | * | Glob pattern to Variants of the Release, to be paired with the --source arg. ex: --source=/manifests-dir/ --variants-pattern=**, --source=/manifests-dir/ --variants-pattern=us-*.yaml, --source=/manifests/dir/ --variants-pattern=*/*.yaml |


**Examples:**
```bash
To create Release v1.0.0 for Resource Bundle my-bundle in us-central1, run:

    $ gcloud container hub packages resource-bundles releases create \
        --version=v1.0.0 --resource-bundle=my-bundle \
        --source=manifest.yaml

To create a Release with multiple variants in one directory, run:

    $ gcloud container hub packages resource-bundles releases create \
        --version=v1.0.0 --resource-bundle=my-bundle \
        --source=/manifests/ --variants-pattern=manifest-*.yaml

To create a Release with multiple variants across multiple directories, ex:

    $ gcloud container hub packages resource-bundles releases create \
        --version=v1.0.0 --resource-bundle=my-bundle \
        --source=/manifests/ --variants-pattern=dir-*/
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/releases/create)

---
### `gcloud container hub packages resource-bundles releases delete`

Delete Package Rollouts Release

Delete Package Rollouts Release.

**Synopsis:**
```
gcloud container hub packages resource-bundles releases delete RELEASE
    --resource-bundle=RESOURCE_BUNDLE [--force] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RELEASE
   Release identifier, either a version or tag.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-bundle` | RESOURCE_BUNDLE |  | Resource Bundle name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--force` |  |  | If true, force deletion of any child resources. Otherwise, attempting to delete a Release with children will fail. |
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To delete Release v1.0.0 of cert-manager in us-central1, run:

    $ gcloud container hub packages resource-bundles releases delete \
         v1.0.0 --location=us-central1 --resource-bundle=cert-manager
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/releases/delete)

---
### `gcloud container hub packages resource-bundles releases describe`

Describe Package Rollouts Release

Describe Package Rollouts Release.

**Synopsis:**
```
gcloud container hub packages resource-bundles releases describe RELEASE
    --resource-bundle=RESOURCE_BUNDLE [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RELEASE
   Release identifier, either a version or tag.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-bundle` | RESOURCE_BUNDLE |  | Resource Bundle name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To view release v1.0.0 of cert-manager in us-central1, run:

    $ gcloud container hub packages resource-bundles releases describe \
         v1.0.0 --location=us-central1 --resource-bundle=cert-manager
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/releases/describe)

---
### `gcloud container hub packages resource-bundles releases list`

List Releases of a Resource Bundle

List Releases of a Resource Bundle.

**Synopsis:**
```
gcloud container hub packages resource-bundles releases list
    --resource-bundle=RESOURCE_BUNDLE [--location=LOCATION]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-bundle` | RESOURCE_BUNDLE |  | Resource Bundle name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To list all Releases for bundle cert-manager in us-central1, run:

    $ gcloud container hub packages resource-bundles releases list \
         --resource-bundle=cert-manager --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/releases/list)

---
### `gcloud container hub packages resource-bundles releases update`

Update Package Rollouts Release

Update Package Rollouts Release.

**Synopsis:**
```
gcloud container hub packages resource-bundles releases update RELEASE
    --resource-bundle=RESOURCE_BUNDLE [--lifecycle=LIFECYCLE]
    [--location=LOCATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
RELEASE
   Release identifier, either a version or tag.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--resource-bundle` | RESOURCE_BUNDLE |  | Resource Bundle name. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--lifecycle` | LIFECYCLE |  | Lifecycle of the Release. |
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To update Release v1.0.0 for Resource Bundle my-bundle in us-central1, run:

    $ gcloud container hub packages resource-bundles releases update \
         --version=v1.0.0 --resource-bundle=my-bundle \
         --lifecycle=PUBLISHED
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/resource-bundles/releases/update)

---

## `gcloud container hub packages rollouts` — commands for managing Rollouts
### `gcloud container hub packages rollouts abort`

Abort Rollout resource

Abort Rollout resource.

**Synopsis:**
```
gcloud container hub packages rollouts abort
    (ROLLOUT : --fleet-package=FLEET_PACKAGE --location=LOCATION)
    [--reason=REASON] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The rollout to abort. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --fleet-package=FLEET_PACKAGE
     Fleet Package name.

     To set the fleet-package attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --fleet-package on the command line.

  --location=LOCATION
     Google Cloud zone or region for the rollout.

     To set the location attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property config_delivery/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reason` | REASON |  | Reason for aborting rollout. |


**Examples:**
```bash
To abort Rollout 20240318 for cert-manager-app in us-central1, run:

    $ gcloud container hub packages rollouts abort 20240318 \
         --fleet-package=cert-manager-app --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/rollouts/abort)

---
### `gcloud container hub packages rollouts describe`

Describe Rollout resource

Describe Rollout resource.

**Synopsis:**
```
gcloud container hub packages rollouts describe NAME
    --fleet-package=FLEET_PACKAGE [--less] [--location=LOCATION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAME
   Resource name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-package` | FLEET_PACKAGE |  | Parent Fleet Package of the Rollout. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--less` |  |  | Show less verbose output. |
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To view Rollout 20240318 for cert-manager-app in us-central1, run:

    $ gcloud container hub packages rollouts describe 20240318 \
         --fleet-package=cert-manager-app --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/rollouts/describe)

---
### `gcloud container hub packages rollouts list`

List Rollouts of a Fleet Package

List Rollouts of a Fleet Package.

**Synopsis:**
```
gcloud container hub packages rollouts list --fleet-package=FLEET_PACKAGE
    [--less] [--location=LOCATION] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-package` | FLEET_PACKAGE |  | Parent Fleet Package of the Rollout. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--less` |  |  | Show less verbose output. |
| `--location` | LOCATION |  | Google Cloud zone or region. |


**Examples:**
```bash
To list all Rollouts for Fleet Package cert-manager-app in us-central1,
run:

    $ gcloud container hub packages rollouts list \
         --fleet-package=cert-manager-app --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/rollouts/list)

---
### `gcloud container hub packages rollouts resume`

Resume suspended Rollout

Resume suspended Rollout.

**Synopsis:**
```
gcloud container hub packages rollouts resume
    (ROLLOUT : --fleet-package=FLEET_PACKAGE --location=LOCATION)
    [--reason=REASON] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The rollout to resume. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --fleet-package=FLEET_PACKAGE
     Fleet Package name.

     To set the fleet-package attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --fleet-package on the command line.

  --location=LOCATION
     Google Cloud zone or region for the rollout.

     To set the location attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property config_delivery/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reason` | REASON |  | Reason for resuming rollout. |


**Examples:**
```bash
To resume Rollout 20240318 for cert-manager-app in us-central1, run:

    $ gcloud container hub packages rollouts resume 20240318 \
         --fleet-package=cert-manager-app --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/rollouts/resume)

---
### `gcloud container hub packages rollouts suspend`

Suspend in-progress Rollout

Suspend in-progress Rollout.

**Synopsis:**
```
gcloud container hub packages rollouts suspend
    (ROLLOUT : --fleet-package=FLEET_PACKAGE --location=LOCATION)
    [--reason=REASON] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rollout resource - The rollout to suspend. The arguments in this group can
be used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument rollout on the command line with a fully
   specified name;
 * set the property core/project.

This must be specified.

  ROLLOUT
     ID of the rollout or fully qualified identifier for the rollout.

     To set the rollout attribute:
     + provide the argument rollout on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --fleet-package=FLEET_PACKAGE
     Fleet Package name.

     To set the fleet-package attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --fleet-package on the command line.

  --location=LOCATION
     Google Cloud zone or region for the rollout.

     To set the location attribute:
     + provide the argument rollout on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property config_delivery/location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--reason` | REASON |  | Reason for suspending rollout. |


**Examples:**
```bash
To suspend Rollout 20240318 for cert-manager-app in us-central1, run:

    $ gcloud container hub packages rollouts suspend 20240318 \
         --fleet-package=cert-manager-app --location=us-central1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/packages/rollouts/suspend)

---

## `gcloud container hub policycontroller` — manage Policy Controller Feature
### `gcloud container hub policycontroller describe`

Describe Policy Controller feature

**Synopsis:**
```
gcloud container hub policycontroller describe
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |


**Examples:**
```bash
To describe the Policy Controller feature:

    $ gcloud container hub policycontroller describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/describe)

---
### `gcloud container hub policycontroller detach`

Detach Policy Controller Feature

Detaches Policy Controller. This will halt all administration of the Policy
Controller installation by the GKE Fleet. It will not uninstall it from the
cluster. To re-attach Policy Controller, use the enable command.

**Synopsis:**
```
gcloud container hub policycontroller detach
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |


**Examples:**
```bash
To detach Policy Controller, run:

    $ gcloud container hub policycontroller detach

To re-attach Policy Controller, use the enable command:

    $ gcloud container hub policycontroller enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/detach)

---
### `gcloud container hub policycontroller disable`

Disable (Uninstall) Policy Controller

Uninstalls Policy Controller.

**Synopsis:**
```
gcloud container hub policycontroller disable
    [--fleet-default-member-config | --all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--fleet-default-member-config` |  |  | _[At most one of these can be specified:]_ Removes the fleet default configuration for policy controller. Memberships configured with the fleet default will maintain their current configuration. $ gcloud container hub policycontroller disable \ --fleet-default-member-config |


**Examples:**
```bash
To uninstall Policy Controller, run:

    $ gcloud container hub policycontroller disable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/disable)

---
### `gcloud container hub policycontroller enable`

Enable Policy Controller Feature

Enables the Policy Controller Feature in a fleet.

**Synopsis:**
```
gcloud container hub policycontroller enable
    [--all-memberships | [--memberships=[MEMBERSHIPS,...]
      : --location=LOCATION] --audit-interval=AUDIT_INTERVAL
      --constraint-violation-limit=CONSTRAINT_VIOLATION_LIMIT --no-content
      --no-default-bundles --version=VERSION --clear-exemptable-namespaces
      | --exemptable-namespaces=EXEMPTABLE_NAMESPACES --log-denies
      | --no-log-denies --monitoring=MONITORING
      | --no-monitoring --mutation | --no-mutation --referential-rules
      | --no-referential-rules
      | --fleet-default-member-config=FLEET_DEFAULT_MEMBER_CONFIG
      | --no-fleet-default-member-config] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |
| `--audit-interval` | AUDIT_INTERVAL |  | _[o set the property gkehub/location.]_ How often Policy Controller will audit resources, in seconds. |
| `--constraint-violation-limit` | CONSTRAINT_VIOLATION_LIMIT |  | _[o set the property gkehub/location.]_ The number of violations stored on the constraint resource. Must be greater than 0. |
| `--no-content` |  |  | _[o set the property gkehub/location.]_ If set, Policy content, including the template library and policy bundles, will not be installed. |
| `--no-default-bundles` |  |  | _[o set the property gkehub/location.]_ If set, skip installing the default bundle of policy-essentials. |
| `--version` | VERSION |  | _[o set the property gkehub/location.]_ The version of Policy Controller to install; defaults to latest version. |
| `--clear-exemptable-namespaces` |  |  | _[At most one of these can be specified:]_ Removes any namespace exemptions, enabling Policy Controller on all namespaces. Setting this flag will overwrite currently exempted namespaces, not append. |
| `--exemptable-namespaces` | EXEMPTABLE_NAMESPACES |  | _[At most one of these can be specified:]_ Namespaces that Policy Controller should ignore, separated by commas if multiple are supplied. |
| `--log-denies` |  |  | _[At most one of these can be specified:]_ If set, log all denies and dry run failures. (To disable, use --no-log-denies) |
| `--no-log-denies` |  |  | _[At most one of these can be specified:]_ If set, disable all log denies. |
| `--monitoring` | MONITORING |  | _[At most one of these can be specified:]_ Monitoring backend options Policy Controller should export metrics to, separated by commas if multiple are supplied. Setting this flag will overwrite currently enabled backends, not append. Options: prometheus, cloudmonitoring |
| `--no-monitoring` |  |  | _[At most one of these can be specified:]_ Include this flag to disable the monitoring configuration of Policy Controller. |
| `--mutation` |  |  | _[At most one of these can be specified:]_ If set, enable support for mutation. (To disable, use --no-mutation) |
| `--no-mutation` |  |  | _[At most one of these can be specified:]_ Disables mutation support. |
| `--referential-rules` |  |  | _[At most one of these can be specified:]_ If set, enable support for referential constraints. (To disable, use --no-referential-rules) |
| `--no-referential-rules` |  |  | _[At most one of these can be specified:]_ Disables referential rules support. |
| `--fleet-default-member-config` | FLEET_DEFAULT_MEMBER_CONFIG |  | _[At most one of these can be specified:]_ The path to a policy-controller.yaml configuration file. If specified, this configuration will become the default Policy Controller configuration for all memberships in your fleet. It can be overridden with a membership-specific configuration by using the the Update command. To enable the Policy Controller Feature with a fleet-level default membership configuration, run: $ gcloud container hub policycontroller enable \ --fleet-default-member-config=/path/to/policy-controller.yaml |
| `--no-fleet-default-member-config` |  |  | _[At most one of these can be specified:]_ Removes the fleet default configuration for policy controller. Memberships configured with the fleet default will maintain their current configuration. $ gcloud container hub policycontroller enable \ --no-fleet-default-member-config |


**Examples:**
```bash
To enable the Policy Controller Feature, run:

    $ gcloud container hub policycontroller enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/enable)

---
### `gcloud container hub policycontroller suspend`

Suspend Policy Controller Feature

Suspends the Policy Controller. This will disable all kubernetes webhooks
on the configured cluster, thereby removing admission and mutation
functionality. Audit functionality will remain in place.

**Synopsis:**
```
gcloud container hub policycontroller suspend
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |


**Examples:**
```bash
To suspend Policy Controller, run:

    $ gcloud container hub policycontroller suspend

To re-enable Policy Controller webhooks, use the enable command:

    $ gcloud container hub policycontroller enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/suspend)

---
### `gcloud container hub policycontroller update`

Updates the configuration of Policy Controller Feature

Updates the configuration of the Policy Controller installation

**Synopsis:**
```
gcloud container hub policycontroller update
    [--all-memberships | [--memberships=[MEMBERSHIPS,...]
      : --location=LOCATION] --origin=ORIGIN
      | --audit-interval=AUDIT_INTERVAL
      --constraint-violation-limit=CONSTRAINT_VIOLATION_LIMIT
      --version=VERSION --clear-exemptable-namespaces
      | --exemptable-namespaces=EXEMPTABLE_NAMESPACES --log-denies
      | --no-log-denies --monitoring=MONITORING
      | --no-monitoring --mutation | --no-mutation --referential-rules
      | --no-referential-rules] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |
| `--origin` | ORIGIN |  | _[At most one of these can be specified:]_ If --origin=FLEET will set the configuration of the membership to the fleet default. ORIGIN must be (only one value is supported): FLEET. |
| `--audit-interval` | AUDIT_INTERVAL |  | _[At most one of these can be specified:]_ How often Policy Controller will audit resources, in seconds. |
| `--constraint-violation-limit` | CONSTRAINT_VIOLATION_LIMIT |  | _[At most one of these can be specified:]_ The number of violations stored on the constraint resource. Must be greater than 0. |
| `--version` | VERSION |  | _[At most one of these can be specified:]_ The version of Policy Controller to install; defaults to latest version. |


**Examples:**
```bash
To change the installed version, run:

    $ gcloud container hub policycontroller update --version=VERSION

To modify the audit interval to 120 seconds, run:

    $ gcloud container hub policycontroller update --audit-interval=120
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/update)

---

## `gcloud container hub policycontroller content` — manage Policy Controller content

## `gcloud container hub policycontroller content bundles` — manage Policy Controller content bundles
### `gcloud container hub policycontroller content bundles remove`

Removes a bundle installation for Policy Controller content

Google-defined policy bundles of constraints can be installed onto Policy
Controller installations. This command removes those bundles.

**Synopsis:**
```
gcloud container hub policycontroller content bundles remove BUNDLE_NAME
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BUNDLE_NAME
   The constraint bundle to remove from Policy Controller.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |


**Examples:**
```bash
To remove a policy bundle:

    $ gcloud container hub policycontroller content bundles remove \
        cis-k8s-v1.5.1
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/content/bundles/remove)

---
### `gcloud container hub policycontroller content bundles set`

Sets bundle installation for Policy Controller content

Google-defined policy bundles of constraints can be installed onto Policy
Controller installations.

The namespace exclusion flag (--exempted-namespaces) will specify a set of
namespaces that the installed bundle will ignore. Subsequent calls with the
same bundle name and this flag will overwrite what namespaces are being
ignored. Using --no-exempted-namespaces or specifying no namespaces with
--exempted-namespaces will remove all namespaces from the ignore list.

To uninstall a bundle, use the remove command.

**Synopsis:**
```
gcloud container hub policycontroller content bundles set BUNDLE_NAME
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [--exempted-namespaces=EXEMPTED_NAMESPACES | --no-exempted-namespaces]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
BUNDLE_NAME
   The constraint bundle to install in Policy Controller.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |
| `--exempted-namespaces` | EXEMPTED_NAMESPACES |  | _[At most one of these can be specified:]_ Exempted namespaces are ignored by Policy Controller when applying constraints added by this bundle. |
| `--no-exempted-namespaces` |  |  | _[At most one of these can be specified:]_ Removes all exempted namespaces from the specified bundle. |


**Examples:**
```bash
To install a policy bundle:

    $ gcloud container hub policycontroller content bundles set \
        cis-k8s-v1.5.1

To install a policy bundle, while ignoring (exempting) certain namespaces
from being affected by the bundle:

    $ gcloud container hub policycontroller content bundles set \
        cis-k8s-v1.5.1 \
        --exempted-namespaces=kube-system,gatekeeper-system

To remove all exempted namespaces from a particular bundles ignore list:

    $ gcloud container hub policycontroller content bundles set \
        cis-k8s-v1.5.1 --no-exempted-namespaces
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/content/bundles/set)

---

## `gcloud container hub policycontroller content templates` — manage Policy Controller content templates
### `gcloud container hub policycontroller content templates disable`

Disable template installation for Policy Controller content

The Google-defined template library can be installed onto Policy Controller
installations. This command removes that template library.

**Synopsis:**
```
gcloud container hub policycontroller content templates disable
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |


**Examples:**
```bash
To remove the template library:

    $ gcloud container hub policycontroller content templates disable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/content/templates/disable)

---
### `gcloud container hub policycontroller content templates enable`

Installs the template library for Policy Controller

Google-defined template library can be installed onto Policy Controller
installations. To uninstall the template library, use the disable command.

**Synopsis:**
```
gcloud container hub policycontroller content templates enable
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-memberships` |  |  | _[At most one of these can be specified:]_ If supplied, apply to all Policy Controllers memberships in the fleet. |


**Examples:**
```bash
To install a template library:

    $ gcloud container hub policycontroller content templates enable
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/content/templates/enable)

---

## `gcloud container hub policycontroller deployment` — configure Policy Controller component deployments
### `gcloud container hub policycontroller deployment remove`

Removes configuration properties from Policy Controller components

Remove customizations of on-cluster components in Policy Controller. These
components are managed as individual kubernetes deployments (e.g.
'admission') in the gatekeeper-system namespace.

When removing a 'toleration' property, it must match exactly, including the
key, value and effect flag (if originally specified).

**Synopsis:**
```
gcloud container hub policycontroller deployment remove DEPLOYMENT PROPERTY
    [VALUE] [--effect=EFFECT]
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DEPLOYMENT
   The PolicyController deployment component (i.e, "admission", "audit" or
   "mutation" from which to remove configuration.

PROPERTY
   Property to be removed.

[VALUE]
   This is only required to remove a toleration. It should not be included
   for any other property.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--effect` | one of: NoSchedule, PreferNoSchedule, NoExecute |  | Applies only to "toleration" property. To be removed, tolerations must match exactly, including the effect setting. EFFECT must be one of: NoSchedule, PreferNoSchedule, NoExecute. |


**Examples:**
```bash
To remove the replica count for a component:

    $ gcloud container hub policycontroller deployment remove \
        admission replica-count

To remove the replica count for a component across all fleet memberships:

    $ gcloud container hub policycontroller deployment remove \
        admission replica-count --all-memberships

To remove a toleration with key 'my-key' on a component:

    $ gcloud container hub policycontroller deployment remove \
        admission toleration my-key

To remove a toleration with key 'my-key' and 'my-value' on a component:

    $ gcloud container hub policycontroller deployment remove \
        admission toleration my-key=my-value

To remove a toleration with key 'my-key' and 'my-value' on a component,
along with the effect 'NoSchedule':

    $ gcloud container hub policycontroller deployment remove \
        admission toleration my-key=my-value --effect=NoSchedule

To remove a memory limit:

    $ gcloud container hub policycontroller deployment remove audit \
        memory-limit

To remove a memory request:

    $ gcloud container hub policycontroller deployment remove mutation \
        memory-request

To remove a cpu limit:

    $ gcloud container hub policycontroller deployment remove \
        admission cpu-limit

To remove a cpu request:

    $ gcloud container hub policycontroller deployment remove audit \
        cpu-request

To remove the anti-affinity configuration:

    $ gcloud container hub policycontroller deployment remove \
        admission pod-affinity
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/deployment/remove)

---
### `gcloud container hub policycontroller deployment set`

Sets configuration of the Policy Controller components

Customizes on-cluster components of Policy Controller. Supported properties
may be set with this command, or removed with 'remove'. These components
are managed as individual kubernetes deployments (e.g. 'admission') in the
gatekeeper-system namespace.

When setting cpu or memory limits and requests, Kubernetes-standard
resource units are used.

All properties set using this command will overwrite previous properties,
with the exception of tolerations which can only be added, and any number
may be added. To edit a toleration, use 'remove' to first delete it, and
then 'set' the desired toleration.

**Synopsis:**
```
gcloud container hub policycontroller deployment set DEPLOYMENT PROPERTY
    VALUE [--effect=EFFECT]
    [--all-memberships
      | [--memberships=[MEMBERSHIPS,...] : --location=LOCATION]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
DEPLOYMENT
   The PolicyController deployment component (e.g. "admission", "audit" or
   "mutation") upon which to set configuration.

PROPERTY
   Property to be set.

VALUE
   The value to set the property to. Valid input varies based on the
   property being set.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--effect` | one of: NoSchedule, PreferNoSchedule, NoExecute |  | Applies only to "toleration" property. EFFECT must be one of: NoSchedule, PreferNoSchedule, NoExecute. |


**Examples:**
```bash
To set the replica count for a component:

    $ gcloud container hub policycontroller deployment set admission \
        replica-count 3

To set the replica count for a component across all fleet memberships:

    $ gcloud container hub policycontroller deployment set admission \
        replica-count 3 --all-memberships

To set a toleration with key 'my-key' on a component (which is an 'Exists'
operator):

    $ gcloud container hub policycontroller deployment set admission \
        toleration my-key

To set a toleration with key 'my-key' and 'my-value' on a component (which
is an 'Equal' operator):

    $ gcloud container hub policycontroller deployment set admission \
        toleration my-key=my-value

To set a toleration with key 'my-key' and 'my-value' on a component, along
with the effect 'NoSchedule' (which is an 'Equal' operator):

    $ gcloud container hub policycontroller deployment set admission \
        toleration my-key=my-value --effect=NoSchedule

To set a memory limit:

    $ gcloud container hub policycontroller deployment set audit \
        memory-limit 4Gi

To set a memory request:

    $ gcloud container hub policycontroller deployment set mutation \
        memory-request 2Gi

To set a cpu limit:

    $ gcloud container hub policycontroller deployment set admission \
        cpu-limit 500m

To set a cpu request:

    $ gcloud container hub policycontroller deployment set audit \
        cpu-request 250m

To set anti-affinity to achieve high availability on the mutation
deployment:

    $ gcloud container hub policycontroller deployment set mutation \
        pod-affinity anti
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/policycontroller/deployment/set)

---

## `gcloud container hub rbacrolebindingactuation` — manage RbacRoleBinding Actuation
### `gcloud container hub rbacrolebindingactuation describe`

Describe the status of the RbacRoleBinding Actuation Feature in a fleet

**Synopsis:**
```
gcloud container hub rbacrolebindingactuation describe
    [GCLOUD_WIDE_FLAG ...]
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/rbacrolebindingactuation/describe)

---
### `gcloud container hub rbacrolebindingactuation update`

Update RbacRoleBinding Actuation Feature

This command updates RbacRoleBinding Actuation Feature in a fleet.

**Synopsis:**
```
gcloud container hub rbacrolebindingactuation update
    (--add-allowed-custom-role=ADD_ALLOWED_CUSTOM_ROLE
      | --allowed-custom-roles=[ROLES,...]
      | --remove-allowed-custom-role=REMOVE_ALLOWED_CUSTOM_ROLE)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-allowed-custom-role` | ADD_ALLOWED_CUSTOM_ROLE |  | _[Exactly one of these must be specified:]_ Add a single custom role to the allowed custom roles list. |
| `--allowed-custom-roles` | [ROLES,...] |  | _[Exactly one of these must be specified:]_ The list of allowed custom roles that can be used in scope RBACRoleBindings. |
| `--remove-allowed-custom-role` | REMOVE_ALLOWED_CUSTOM_ROLE |  | _[Exactly one of these must be specified:]_ Remove a single custom role from the allowed custom roles list. |


**Examples:**
```bash
To update the RbacRoleBinding Actuation Feature, run:

    $ gcloud container fleet rbacrolebinding-actuation update \
        --allowed-custom-roles=role1,role2

    $ gcloud container fleet rbacrolebinding-actuation update \
        --add-allowed-custom-role=role1

    $ gcloud container fleet rbacrolebinding-actuation update \
        --remove-allowed-custom-role=role2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/rbacrolebindingactuation/update)

---

## `gcloud container hub scopes` — manage scopes of all your GKE fleets
### `gcloud container hub scopes add-iam-policy-binding`

Add IAM policy binding to a Fleet Scope

Add an IAM policy binding to the IAM policy of a Fleet Scope. One binding
consists of a member, and a role.

**Synopsis:**
```
gcloud container hub scopes add-iam-policy-binding SCOPE --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - The scope for which to add IAM policy binding to. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * global is the only supported location.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add an IAM policy binding for the role of 'roles/gkehub.scopeUser' for
the user 'test-user@gmail.com' with scope 'my-scope', run:

    $ gcloud container hub scopes add-iam-policy-binding my-scope \
        --member='user:test-user@gmail.com' \
        --role='roles/gkehub.scopeUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/add-iam-policy-binding)

---
### `gcloud container hub scopes create`

Create a new fleet scope

Create a Fleet Scope resource.

**Synopsis:**
```
gcloud container hub scopes create SCOPE [--async]
    [--labels=[KEY=VALUE,...]] [--namespace-labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - The fleet scope resourse to be created. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * global is the only supported location.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--namespace-labels` | [KEY=VALUE,...] |  | List of scope-level label KEY=VALUE pairs to add. |


**Examples:**
```bash
Create a new scope SCOPE_NAME in the active project's fleet:

    $ gcloud container hub scopes create SCOPE_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/create)

---
### `gcloud container hub scopes delete`

Delete a fleet scope

This command deletes a Fleet Scope resource .

**Synopsis:**
```
gcloud container hub scopes delete (SCOPE : --location=LOCATION) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - The fleet scope to delete. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument scope on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
First retrieve the ID of the scope using the command below. The output of
this command lists all the fleet's scopes, with their unique IDs in the
Names column:

    $ gcloud container hub scopes list

Delete a scope from the active project's fleet:

    $ gcloud container hub scopes delete SCOPE_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/delete)

---
### `gcloud container hub scopes describe`

Describe a fleet scope

Describe a Fleet Scope.

**Synopsis:**
```
gcloud container hub scopes describe (SCOPE : --location=LOCATION)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - The scope to describe. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument scope on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Examples:**
```bash
First retrieve the ID of the scope using the command below. The output of
this command lists all the fleet's members, with their unique IDs in the
Names column:

    $ gcloud container hub scopes list

Then describe it:

    $ gcloud container hub scopes describe SCOPE_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/describe)

---
### `gcloud container hub scopes get-iam-policy`

Get the IAM policy for a Fleet Scope

This command gets the IAM policy for a scope.

**Synopsis:**
```
gcloud container hub scopes get-iam-policy SCOPE [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - The scope for which to display the IAM policy. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * global is the only supported location.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given scope, run:

    $ gcloud container hub scopes get-iam-policy my-scope
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/get-iam-policy)

---
### `gcloud container hub scopes list`

List fleet scopes in a project permitted to be viewed by the caller

This command can fail for the following reasons:
  o The project specified does not exist.
  o The user does not have access to the project specified.

**Synopsis:**
```
gcloud container hub scopes list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
The following command lists scopes in the active project:

    $ gcloud container hub scopes list

The following command lists scopes in project PROJECT_ID:

    $ gcloud container hub scopes list --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/list)

---
### `gcloud container hub scopes list-memberships`

List memberships bound to a fleet scope

This command can fail for the following reasons:
  o The scope specified does not exist.
  o The user does not have access to the specified scope.

**Synopsis:**
```
gcloud container hub scopes list-memberships SCOPE [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - The group of arguments defining the Fleet Scope. This
represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument SCOPE on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument SCOPE on the command line with a fully specified
   name;
 * global is the only supported location.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument SCOPE on the command line.
```

**Examples:**
```bash
The following command lists memberships bound to scope SCOPE in project
PROJECT_ID:

    $ gcloud container hub scopes list-memberships SCOPE \
        --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/list-memberships)

---
### `gcloud container hub scopes remove-iam-policy-binding`

Remove IAM policy binding of a Fleet Scope

Remove an IAM policy binding from the IAM policy of a scope. One binding
consists of a member, and a role.

**Synopsis:**
```
gcloud container hub scopes remove-iam-policy-binding SCOPE
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - The scope for which to remove IAM policy binding from.
This represents a Cloud resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * global is the only supported location.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove an IAM policy binding for the role of 'roles/gkehub.scopeUser'
for the user 'test-user@gmail.com' with scope 'my-scope', run:

    $ gcloud container hub scopes remove-iam-policy-binding my-scope \
        --member='user:test-user@gmail.com' \
        --role='roles/gkehub.scopeUser'

See https://cloud.google.com/iam/docs/managing-policies for details of
policy role and member types.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/remove-iam-policy-binding)

---
### `gcloud container hub scopes update`

Update a scope

Update an existing Fleet Scope.

**Synopsis:**
```
gcloud container hub scopes update (SCOPE : --location=LOCATION)
    [--update-labels=[KEY=VALUE,...]]
    [--update-namespace-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-namespace-labels | --remove-namespace-labels=[KEY,...]]
    [--default-upgrade-soaking=DEFAULT_UPGRADE_SOAKING
      --remove-upgrade-soaking-overrides
      | --add-upgrade-soaking-override=ADD_UPGRADE_SOAKING_OVERRIDE
      --upgrade-selector=[name=NAME],[version=VERSION]
      --reset-upstream-scope | --upstream-scope=UPSTREAM_SCOPE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Scope resource - fleet scope resource. The arguments in this group can be
used to specify the attributes of this resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument scope on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  SCOPE
     ID of the scope or fully qualified identifier for the scope.

     To set the scope attribute:
     + provide the argument scope on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     The location name.

     To set the location attribute:
     + provide the argument scope on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + global is the only supported location.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--update-namespace-labels` | [KEY=VALUE,...] |  | List of scope-level label KEY=VALUE pairs to update in the cluster namespace. If a label exists, its value is modified. Otherwise, a new label is' created. |


**Examples:**
```bash
First retrieve the ID of the scope using the command below.

    $ gcloud container hub scopes list

Update a scope.

    $ gcloud container hub scopes update SCOPE_NAME
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/update)

---

## `gcloud container hub scopes namespaces` — fleet namespaces are the fleet equivalent of k8s cluster namespaces
### `gcloud container hub scopes namespaces create`

Create a fleet namespace

This command can fail for the following reasons:
  o The project specified does not exist.
  o The project has a fleet namespace with the same name.
  o The caller does not have permission to access the given project.

**Synopsis:**
```
gcloud container hub scopes namespaces create (NAMESPACE : --scope=SCOPE)
    [--labels=[KEY=VALUE,...]] [--namespace-labels=[KEY=VALUE,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The group of arguments defining the Fleet Namespace.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * global is the only supported location.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument NAMESPACE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --scope=SCOPE
     the

     To set the scope attribute:
     + provide the argument NAMESPACE on the command line with a fully
       specified name;
     + provide the argument --scope on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--namespace-labels` | [KEY=VALUE,...] |  | List of namespace-level label KEY=VALUE pairs to add. |


**Examples:**
```bash
To create a fleet namespace with name NAMESPACE in the active project, run:

    $ gcloud container hub scopes namespaces create NAMESPACE

To create a fleet namespace in fleet scope SCOPE in project PROJECT_ID with
name NAMESPACE, run:

    $ gcloud container hub scopes namespaces create NAMESPACE \
        --scope=SCOPE --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/namespaces/create)

---
### `gcloud container hub scopes namespaces delete`

Delete a fleet namespace

This command can fail for the following reasons:
  o The project specified does not exist.
  o The namespace specified does not exist.
  o The caller does not have permission to access the given project or
    namespace.

**Synopsis:**
```
gcloud container hub scopes namespaces delete (NAMESPACE : --scope=SCOPE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The group of arguments defining the Fleet Namespace.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * global is the only supported location.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument NAMESPACE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --scope=SCOPE
     the

     To set the scope attribute:
     + provide the argument NAMESPACE on the command line with a fully
       specified name;
     + provide the argument --scope on the command line.
```

**Examples:**
```bash
To delete fleet namespace NAMESPACE in the active project:

    $ gcloud container hub scopes namespaces delete NAMESPACE

To delete fleet namespace NAMESPACE in project PROJECT_ID:

    $ gcloud container hub scopes namespaces delete NAMESPACE \
        --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/namespaces/delete)

---
### `gcloud container hub scopes namespaces describe`

Show fleet namespace info

This command can fail for the following reasons:
  o The project specified does not exist.
  o The namespace specified does not exist in the project.
  o The caller does not have permission to access the project or
    namespace.

**Synopsis:**
```
gcloud container hub scopes namespaces describe (NAMESPACE : --scope=SCOPE)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The group of arguments defining the Fleet Namespace.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * global is the only supported location.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument NAMESPACE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --scope=SCOPE
     the

     To set the scope attribute:
     + provide the argument NAMESPACE on the command line with a fully
       specified name;
     + provide the argument --scope on the command line.
```

**Examples:**
```bash
To print metadata for the namespace NAMESPACE in the active project, run:

    $ gcloud container hub scopes namespaces describe NAMESPACE

To print metadata for the namespace NAMESPACE in project PROJECT_ID, run:

    $ gcloud container hub scopes namespaces describe NAMESPACE \
        --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/namespaces/describe)

---
### `gcloud container hub scopes namespaces get-credentials`

Fetch credentials for a membership with a particular namespace

**Synopsis:**
```
gcloud container hub scopes namespaces get-credentials NAMESPACE
    [--membership=MEMBERSHIP] [--membership-location=MEMBERSHIP_LOCATION]
    [--set-namespace-in-config=SET_NAMESPACE_IN_CONFIG]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
NAMESPACE
   Name of the namespace for which to get access to memberships.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--membership` | MEMBERSHIP |  | Membership ID to get credentials from. If not provided, a prompt will offer a list of memberships in the fleet. |
| `--membership-location` | MEMBERSHIP_LOCATION |  | The location of the membership resource, e.g. us-central1. If not specified, defaults to global. |
| `--set-namespace-in-config` | SET_NAMESPACE_IN_CONFIG |  | If true, the default namespace for the context in the generated kubeconfig will be set to the Fleet namespace (i.e. the name given as the positional argument in this command). Otherwise, no default namespace will be set, functioning the same as gcloud container fleet memberships get-credentials. |


**Examples:**
```bash
Get the Connect Gateway kubeconfig for global membership MEMBERSHIP, using
namespace NAMESPACE in the config:

    $ gcloud container hub scopes namespaces get-credentials NAMESPACE \
        --membership=MEMBERSHIP --membership-location=global \
        --set-namespace-in-config=true

Get the Connect Gateway kubeconfig for global membership MEMBERSHIP:

    $ gcloud container hub scopes namespaces get-credentials NAMESPACE \
        --membership=MEMBERSHIP --membership-location=global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/namespaces/get-credentials)

---
### `gcloud container hub scopes namespaces list`

List fleet namespaces in a project

This command can fail for the following reasons:
  o The project specified does not exist.
  o The user does not have access to the project specified.

**Synopsis:**
```
gcloud container hub scopes namespaces list --scope=SCOPE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope` | SCOPE |  | _[This must be specified.]_ ID of the scope or fully qualified identifier for the scope. To set the scope attribute: + provide the argument --scope on the command line. |


**Examples:**
```bash
The following command lists namespaces in the active project:

    $ gcloud container hub scopes namespaces list

The following command lists namespaces in project PROJECT_ID:

    $ gcloud container hub scopes namespaces list --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/namespaces/list)

---
### `gcloud container hub scopes namespaces update`

Update a fleet namespace

This command can fail for the following reasons:
  o The project specified does not exist.
  o The fleet namespace does not exist in the project.
  o The caller does not have permission to access the project or
    namespace.

**Synopsis:**
```
gcloud container hub scopes namespaces update (NAMESPACE : --scope=SCOPE)
    [--update-labels=[KEY=VALUE,...]]
    [--update-namespace-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--clear-namespace-labels | --remove-namespace-labels=[KEY,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Namespace resource - The group of arguments defining the Fleet Namespace.
The arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

To set the location attribute:
 * provide the argument NAMESPACE on the command line with a fully
   specified name;
 * global is the only supported location.

This must be specified.

  NAMESPACE
     ID of the namespace or fully qualified identifier for the namespace.

     To set the namespace attribute:
     + provide the argument NAMESPACE on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --scope=SCOPE
     the

     To set the scope attribute:
     + provide the argument NAMESPACE on the command line with a fully
       specified name;
     + provide the argument --scope on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--update-namespace-labels` | [KEY=VALUE,...] |  | List of namespace-level label KEY=VALUE pairs to update in the cluster namespace. If a label exists, its value is modified. Otherwise, a new label is' created. |


**Examples:**
```bash
To update the namespace NAMESPACE in the active project:

    $ gcloud container hub scopes namespaces update NAMESPACE

To update the namespace NAMESPACE in project PROJECT_ID:

    $ gcloud container hub scopes namespaces update NAMESPACE \
        --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/namespaces/update)

---

## `gcloud container hub scopes rbacrolebindings` — fleet scope RBAC RoleBindings for permissions
### `gcloud container hub scopes rbacrolebindings create`

Create an RBAC RoleBinding

This command can fail for the following reasons:
  o The RBAC RoleBinding already exists.
  o The caller does not have permission to access the given scope.

**Synopsis:**
```
gcloud container hub scopes rbacrolebindings create
    (NAME : --location=LOCATION --scope=SCOPE)
    (--custom-role=CUSTOM_ROLE | --role=ROLE) (--group=GROUP | --user=USER)
    [--labels=[KEY=VALUE,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rbacrolebinding resource - The group of arguments defining an
RBACRoleBinding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the rbacrolebinding or fully qualified identifier for the
     rbacrolebinding.

     To set the rbacrolebinding attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location for the rbacrolebinding.

     To set the location attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.

  --scope=SCOPE
     Name of the rbacrolebinding.

     To set the scope attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --scope on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--custom-role` | CUSTOM_ROLE |  | _[Exactly one of these must be specified:]_ Custom role to assign to principal. |
| `--role` | one of: admin, edit, view |  | _[Exactly one of these must be specified:]_ Predefined role to assign to principal (admin, edit, view). ROLE must be one of: admin, edit, view. |
| `--group` | GROUP |  | _[Exactly one of these must be specified:]_ Group for the RoleBinding. |
| `--user` | USER |  | _[Exactly one of these must be specified:]_ User for the RoleBinding. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To create an admin RBAC RoleBinding RBRB in scope SCOPE for user
person@google.com, run:

    $ gcloud container hub scopes rbacrolebindings create RBRB \
        --scope=SCOPE --role=admin --user=person@google.com

To create a viewer RBAC RoleBinding RBRB in scope SCOPE for group
people@google.com, run:

    $ gcloud container hub scopes rbacrolebindings create RBRB \
        --scope=SCOPE --role=viewer --group=people@google.com

To create an RBAC RoleBinding with a custom role custom-role in scope SCOPE
for user person@google.com, run:

    $ gcloud container hub scopes rbacrolebindings create RBRB \
        --scope=SCOPE --role=admin --user=person@google.com \
        --custom-role=custom-role
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/rbacrolebindings/create)

---
### `gcloud container hub scopes rbacrolebindings delete`

Delete a fleet scope RBAC RoleBinding

This command can fail for the following reasons:
  o The RoleBinding specified does not exist.
  o The caller does not have permission to access the given RoleBinding.

**Synopsis:**
```
gcloud container hub scopes rbacrolebindings delete
    (NAME : --location=LOCATION --scope=SCOPE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rbacrolebinding resource - The group of arguments defining an
RBACRoleBinding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the rbacrolebinding or fully qualified identifier for the
     rbacrolebinding.

     To set the rbacrolebinding attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location for the rbacrolebinding.

     To set the location attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.

  --scope=SCOPE
     Name of the rbacrolebinding.

     To set the scope attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --scope on the command line.
```

**Examples:**
```bash
To delete RBAC RoleBinding RBRB in scope SCOPE in the active project:

    $ gcloud container hub scopes rbacrolebindings delete RBRB \
        --scope=SCOPE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/rbacrolebindings/delete)

---
### `gcloud container hub scopes rbacrolebindings describe`

Show fleet scope RBAC RoleBinding information

This command can fail for the following reasons:
  o The RoleBinding specified does not exist in the project.
  o The caller does not have permission to access the RoleBinding.

**Synopsis:**
```
gcloud container hub scopes rbacrolebindings describe
    (NAME : --location=LOCATION --scope=SCOPE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rbacrolebinding resource - The group of arguments defining an
RBACRoleBinding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the rbacrolebinding or fully qualified identifier for the
     rbacrolebinding.

     To set the rbacrolebinding attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location for the rbacrolebinding.

     To set the location attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.

  --scope=SCOPE
     Name of the rbacrolebinding.

     To set the scope attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --scope on the command line.
```

**Examples:**
```bash
To print metadata for RBAC RoleBinding RBRB in the scope SCOPE, run:

    $ gcloud container hub scopes rbacrolebindings describe RBRB \
        --scope=SCOPE
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/rbacrolebindings/describe)

---
### `gcloud container hub scopes rbacrolebindings list`

List RBAC RoleBindings in a fleet scope

This command can fail for the following reasons:
  o The scope specified does not exist.
  o The user does not have access to the specified scope.

**Synopsis:**
```
gcloud container hub scopes rbacrolebindings list --scope=SCOPE
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--scope` | SCOPE |  | Name of the fleet scope to list RBAC RoleBindings from. |


**Examples:**
```bash
The following command lists RBAC RoleBindings in scope SCOPE in project
PROJECT_ID:

    $ gcloud container hub scopes rbacrolebindings list --scope=SCOPE \
        --project=PROJECT_ID
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/rbacrolebindings/list)

---
### `gcloud container hub scopes rbacrolebindings update`

Update a fleet scope RBAC RoleBinding

This command can fail for the following reasons:
  o The RoleBinding does not exist in the project.
  o The caller does not have permission to access the RoleBinding.

**Synopsis:**
```
gcloud container hub scopes rbacrolebindings update
    (NAME : --location=LOCATION --scope=SCOPE)
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]]
    [--custom-role=CUSTOM_ROLE | --role=ROLE] [--group=GROUP | --user=USER]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Rbacrolebinding resource - The group of arguments defining an
RBACRoleBinding. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument NAME on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  NAME
     ID of the rbacrolebinding or fully qualified identifier for the
     rbacrolebinding.

     To set the rbacrolebinding attribute:
     + provide the argument NAME on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --location=LOCATION
     Location for the rbacrolebinding.

     To set the location attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --location on the command line;
     + set the property gkehub/location.

  --scope=SCOPE
     Name of the rbacrolebinding.

     To set the scope attribute:
     + provide the argument NAME on the command line with a fully
       specified name;
     + provide the argument --scope on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the RBAC RoleBinding RBRB in scope SCOPE in the active project to
the viewer role:

    $ gcloud container hub scopes rbacrolebindings update RBRB \
        --scope=SCOPE --role=viewer

To update the RBAC RoleBinding RBRB in scope SCOPE in the active project to
the custom role custom-role:

    $ gcloud container hub scopes rbacrolebindings update RBRB \
        --scope=SCOPE --custom-role=custom-role

To update the RBAC RoleBinding RBRB in scope SCOPE in the active project to
the user someone@google.com:

    $ gcloud container hub scopes rbacrolebindings update RBRB \
        --scope=SCOPE --user=someone@google.com
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/container/hub/scopes/rbacrolebindings/update)

---