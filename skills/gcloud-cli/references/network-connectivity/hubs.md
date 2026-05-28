# gcloud network-connectivity hubs

manage Network Connectivity Center hubs

### `gcloud network-connectivity hubs accept-spoke`

Accept a spoke into a hub

Accept a proposed or previously rejected VPC spoke. By accepting a spoke,
you permit connectivity between the associated VPC network and other VPC
networks that are attached to the same hub.

**Synopsis:**
```
gcloud network-connectivity hubs accept-spoke HUB --spoke=SPOKE [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to accept the spoke into. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--spoke` | SPOKE |  | URI of the spoke to accept |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To accept a spoke named my-spoke into a hub named my-hub, run:

    $ gcloud network-connectivity hubs accept-spoke my-hub \
       --spoke="https://networkconnectivity.googleapis.com/v1/projects/\
    spoke-project/locations/global/spokes/my-spoke"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/accept-spoke)

---
### `gcloud network-connectivity hubs accept-spoke-update`

Accept a proposal to update a spoke in a hub

Accept a proposed or previously rejected VPC spoke update. By accepting a
spoke update, you permit updating connectivity between the associated VPC
network and other VPC networks that are attached to the same hub.

**Synopsis:**
```
gcloud network-connectivity hubs accept-spoke-update HUB --spoke=SPOKE
    --spoke-etag=SPOKE_ETAG [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to accept the spoke update. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--spoke` | SPOKE |  | URI of the spoke to accept update |
| `--spoke-etag` | SPOKE_ETAG |  | Etag of the spoke to accept update |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To accept updating a spoke named my-spoke with etag in a hub named my-hub,
run:

    $ gcloud network-connectivity hubs accept-spoke-update my-hub \
         --spoke="projects/spoke-project/locations/global/hubs/my-spoke" \
     --spoke-etag=etag
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/accept-spoke-update)

---
### `gcloud network-connectivity hubs add-iam-policy-binding`

Add an IAM policy binding to the IAM policy of a hub resource

Add an IAM policy binding to the IAM policy of a hub resource. One binding
consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud network-connectivity hubs add-iam-policy-binding HUB
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - The hub that you want to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To grant a user the roles/networkconnectivity.groupUser role on the hub
called my-hub, run the following command:

    $ gcloud network-connectivity hubs add-iam-policy-binding my-hub \
        --member="user:username@gmail.com" \
        --role="roles/networkconnectivity.groupUser"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/add-iam-policy-binding)

---
### `gcloud network-connectivity hubs create`

Create a new hub

Create a new hub with the given name.

**Synopsis:**
```
gcloud network-connectivity hubs create HUB [--async]
    [--description=DESCRIPTION] [--export-psc] [--labels=[KEY=VALUE,...]]
    [--policy-mode=POLICY_MODE] [--preset-topology=PRESET_TOPOLOGY]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to be created. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Description of the hub. |
| `--export-psc` |  |  | This boolean controls whether Private Service Connect transitivity is enabled for the hub. |
| `--labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to add. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |
| `--policy-mode` | one of: policy-mode-unspecified, preset |  | Policy mode of the hub. POLICY_MODE must be one of: policy-mode-unspecified, preset. |
| `--preset-topology` | one of: hybrid-inspection, mesh, preset-topology-unspecified, star |  | Topology of the hub. Only applicable when --policy-mode=PRESET. PRESET_TOPOLOGY must be one of: hybrid-inspection, mesh, preset-topology-unspecified, star. |


**Examples:**
```bash
To create a hub with the name my-hub and the description optional
description, run:

    $ gcloud network-connectivity hubs create my-hub \
        --description="optional description"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/create)

---
### `gcloud network-connectivity hubs delete`

Delete a hub

Delete the specified hub.

**Synopsis:**
```
gcloud network-connectivity hubs delete HUB [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to be deleted. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete a hub named my-hub, run:

    $ gcloud network-connectivity hubs delete my-hub
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/delete)

---
### `gcloud network-connectivity hubs describe`

Describe a hub

Retrieve and display details about a hub.

**Synopsis:**
```
gcloud network-connectivity hubs describe HUB [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to be described. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Examples:**
```bash
To display details about a hub named my-hub, run:

    $ gcloud network-connectivity hubs describe my-hub
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/describe)

---
### `gcloud network-connectivity hubs get-iam-policy`

Get the IAM policy for a hub resource

Get the IAM policy of a hub. If formatted as JSON, the output can be edited
and used as a policy file for set-iam-policy.

**Synopsis:**
```
gcloud network-connectivity hubs get-iam-policy HUB [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - The hub for which you want the IAM policy. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Examples:**
```bash
To get the IAM policy for a hub named my-hub, run:

    $ gcloud network-connectivity hubs get-iam-policy my-hub
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/get-iam-policy)

---
### `gcloud network-connectivity hubs list`

List hubs

Retrieve and display a list of all hubs in the specified project.

**Synopsis:**
```
gcloud network-connectivity hubs list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all hubs, run:

    $ gcloud network-connectivity hubs list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/list)

---
### `gcloud network-connectivity hubs list-spokes`

List hub spokes

Retrieve and display a list of all spokes associated with a hub.

**Synopsis:**
```
gcloud network-connectivity hubs list-spokes HUB
    [--spoke-locations=[LOCATION,...]] [--view=VIEW; default="basic"]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub associated with the returned list of
spokes. This represents a Cloud resource. (NOTE) Some attributes are not
given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--spoke-locations` | [LOCATION,...] |  | A comma separated list of locations. The locations can be set to 'global' and/or Google Cloud supported regions. To see the names of regions, see Viewing a list of available regions (https://cloud.google.com/compute/docs/regions-zones/viewing-regions-zones#viewing_a_list_of_available_regions). |
| `--view` | one of: basic, detailed | basic | Enumeration to control which spoke fields are included in the response. VIEW must be one of: basic, detailed. |


**Examples:**
```bash
To list all spokes in the us-central1 region and the global location, run:

    $ gcloud network-connectivity hubs list-spokes HUB \
     --spoke-locations=us-central1,global
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/list-spokes)

---
### `gcloud network-connectivity hubs query-status`

Query the status of Private Service Connect propagation for a hub

Query the status of Private Service Connect propagation for a hub.

**Synopsis:**
```
gcloud network-connectivity hubs query-status HUB [--group-by=GROUP_BY]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to query Private Service Connect
propagation for. This represents a Cloud resource. (NOTE) Some attributes
are not given arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--group-by` | GROUP_BY |  | Comma-separated list of resource field key names to group by. Aggregated values will be displayed for each group. If --group-by is set, the value of the --sort-by flag must be the same as or a subset of the --group-by flag. Accepted values are: * 'psc_propagation_status.source_spoke' * 'psc_propagation_status.source_group' * 'psc_propagation_status.source_forwarding_rule' * 'psc_propagation_status.target_spoke' * 'psc_propagation_status.target_group' * 'psc_propagation_status.code' |


**Examples:**
```bash
To query the Private Service Connect propagation status of a hub, run:

    $ gcloud network-connectivity hubs query-status HUB

To query the Private Service Connect propagation status of a hub grouped by
source spoke and code, run:

    $ gcloud network-connectivity hubs query-status HUB \
    --group-by="psc_propagation_status.source_spoke,psc_propagation_\
    status.code"

To query the Private Service Connect propagation status of a hub sorted by
the source forwarding rule, run:

    $ gcloud network-connectivity hubs query-status HUB \
    --sort-by="psc_propagation_status.source_forwarding_rule"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/query-status)

---
### `gcloud network-connectivity hubs reject-spoke`

Reject a spoke from a hub

Reject a VPC spoke. By rejecting a spoke, you prevent or remove
connectivity between the associated VPC network and any other VPC networks
that are attached to the same hub.

**Synopsis:**
```
gcloud network-connectivity hubs reject-spoke HUB --spoke=SPOKE [--async]
    [--details=DETAILS] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to reject the spoke from. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--spoke` | SPOKE |  | URI of the spoke to reject |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--details` | DETAILS |  | Additional details behind the rejection |


**Examples:**
```bash
To reject a spoke named my-spoke from a hub named my-hub with reason
my-reason, run:

    $ gcloud network-connectivity hubs reject-spoke my-hub \
         --spoke="https://networkconnectivity.googleapis.com/v1/projects/\
     spoke-project/locations/global/spokes/my-spoke" --details=my-reason
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/reject-spoke)

---
### `gcloud network-connectivity hubs reject-spoke-update`

Reject a proposal to update a spoke in a hub

Reject a VPC spoke update proposal. By rejecting a spoke update, you
prevent updating the connectivity between the associated VPC network and
any other VPC networks that are attached to the same hub.

**Synopsis:**
```
gcloud network-connectivity hubs reject-spoke-update HUB --spoke=SPOKE
    --spoke-etag=SPOKE_ETAG [--async] [--details=DETAILS]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to reject the spoke update. This represents
a Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--spoke` | SPOKE |  | URI of the spoke to reject update |
| `--spoke-etag` | SPOKE_ETAG |  | Etag of the spoke to reject update |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--details` | DETAILS |  | Additional details behind the rejection |


**Examples:**
```bash
To reject updating a spoke named my-spoke with etag in a hub named my-hub
with reason my-reason, run:

    $ gcloud network-connectivity hubs reject-spoke-update my-hub \
         --spoke="projects/spoke-project/locations/global/hubs/my-spoke" \
     --spoke-etag=etag --details=my-reason
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/reject-spoke-update)

---
### `gcloud network-connectivity hubs remove-iam-policy-binding`

Remove an IAM policy binding from the IAM policy of a hub resource

Remove an IAM policy binding from the IAM policy of a hub resource.

**Synopsis:**
```
gcloud network-connectivity hubs remove-iam-policy-binding HUB
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - The hub that you want to update. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove the roles/networkconnectivity.groupUser role from a user of the
hub my-hub, run:

    $ gcloud network-connectivity hubs remove-iam-policy-binding \
        my-hub --member="user:username@gmail.com" \
        --role="roles/networkconnectivity.groupUser"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/remove-iam-policy-binding)

---
### `gcloud network-connectivity hubs set-iam-policy`

Set the IAM policy of a hub resource

Replace the existing IAM policy of a hub resource with a policy encoded in
a JSON or YAML file.

**Synopsis:**
```
gcloud network-connectivity hubs set-iam-policy HUB POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - The hub for which to set the IAM policy. This represents a
Cloud resource. (NOTE) Some attributes are not given arguments in this
group but can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To replace the IAM policy of a hub resource with the policy defined in a
file called policy.json, run:

    $ gcloud network-connectivity hubs set-iam-policy my-hub policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/set-iam-policy)

---
### `gcloud network-connectivity hubs update`

Update a hub

Update the details of a hub.

**Synopsis:**
```
gcloud network-connectivity hubs update HUB [--async]
    [--description=DESCRIPTION] [--export-psc]
    [--update-labels=[KEY=VALUE,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Hub resource - Name of the hub to be updated. This represents a Cloud
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument hub on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  HUB
     ID of the hub or fully qualified identifier for the hub.

     To set the hub attribute:
     + provide the argument hub on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | New description of the hub. |
| `--export-psc` |  |  | Whether Private Service Connect transitivity is enabled for the hub. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a hub named my-hub, run:

    $ gcloud network-connectivity hubs update my-hub \
        --description="The new description of my-hub".
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/update)

---

## `gcloud network-connectivity hubs groups` — manage Network Connectivity Center groups
### `gcloud network-connectivity hubs groups add-iam-policy-binding`

Add an IAM policy binding to the IAM policy of a group resource

Add an IAM policy binding to the IAM policy of a group resource. One
binding consists of a member, a role, and an optional condition.

**Synopsis:**
```
gcloud network-connectivity hubs groups add-iam-policy-binding
    (GROUP : --hub=HUB) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Group resource - The group that you want to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument group on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GROUP
     ID of the group or fully qualified identifier for the group.

     To set the group attribute:
     + provide the argument group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --hub=HUB
     Id of the hub.

     To set the hub attribute:
     + provide the argument group on the command line with a fully
       specified name;
     + provide the argument --hub on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To grant a user the roles/networkconnectivity.groupUser role on the group
called my-group in the hub called my-hub', run the following command:

    $ gcloud network-connectivity hubs groups add-iam-policy-binding \
        my-group --member="user:username@gmail.com" \
        --role="roles/networkconnectivity.groupUser" --hub="my-hub"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/groups/add-iam-policy-binding)

---
### `gcloud network-connectivity hubs groups describe`

Describe a group

Retrieve and display details about a group.

**Synopsis:**
```
gcloud network-connectivity hubs groups describe (GROUP : --hub=HUB)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Group resource - Name of the group to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument group on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GROUP
     ID of the group or fully qualified identifier for the group.

     To set the group attribute:
     + provide the argument group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --hub=HUB
     Id of the hub.

     To set the hub attribute:
     + provide the argument group on the command line with a fully
       specified name;
     + provide the argument --hub on the command line.
```

**Examples:**
```bash
To display details about a group named my-group, run:

    $ gcloud network-connectivity hubs groups describe my-group
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/groups/describe)

---
### `gcloud network-connectivity hubs groups get-iam-policy`

Get the IAM policy for a group resource

Get the IAM policy of a group. If formatted as JSON, the output can be
edited and used as a policy file for set-iam-policy.

**Synopsis:**
```
gcloud network-connectivity hubs groups get-iam-policy (GROUP : --hub=HUB)
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Group resource - The group for which you want the IAM policy. The
arguments in this group can be used to specify the attributes of this
resource. (NOTE) Some attributes are not given arguments in this group but
can be set in other ways.

To set the project attribute:
 * provide the argument group on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GROUP
     ID of the group or fully qualified identifier for the group.

     To set the group attribute:
     + provide the argument group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --hub=HUB
     Id of the hub.

     To set the hub attribute:
     + provide the argument group on the command line with a fully
       specified name;
     + provide the argument --hub on the command line.
```

**Examples:**
```bash
To get the IAM policy for a group named my-group in the hub named my-hub,
run:

    $ gcloud network-connectivity hubs groups get-iam-policy my-group \
        --hub="my-hub"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/groups/get-iam-policy)

---
### `gcloud network-connectivity hubs groups list`

List groups

Retrieve and display a list of all groups in the specified hub.

**Synopsis:**
```
gcloud network-connectivity hubs groups list [--hub=HUB]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hub` | HUB |  | _[* set the property core/project.]_ ID of the hub or fully qualified identifier for the hub. To set the hub attribute: + provide the argument --hub on the command line; + if hub is empty, will use the wildcard '-' to indicate all hubs. |


**Examples:**
```bash
To list all groups across all hubs, run:

    $ gcloud network-connectivity hubs groups list --hub=-

To list all groups in hub my-hub, run:

    $ gcloud network-connectivity hubs groups list --hub=my-hub
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/groups/list)

---
### `gcloud network-connectivity hubs groups remove-iam-policy-binding`

Remove an IAM policy binding from the IAM policy of a group resource

Remove an IAM policy binding from the IAM policy of a group resource.

**Synopsis:**
```
gcloud network-connectivity hubs groups remove-iam-policy-binding
    (GROUP : --hub=HUB) --member=PRINCIPAL --role=ROLE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Group resource - The group that you want to update. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument group on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GROUP
     ID of the group or fully qualified identifier for the group.

     To set the group attribute:
     + provide the argument group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --hub=HUB
     Id of the hub.

     To set the hub attribute:
     + provide the argument group on the command line with a fully
       specified name;
     + provide the argument --hub on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove the roles/networkconnectivity.groupUser role from a user of the
group my-group in the hub my-hub, run:

    $ gcloud network-connectivity hubs groups \
        remove-iam-policy-binding my-group \
        --member="user:username@gmail.com" \
        --role="roles/networkconnectivity.groupUser" --hub="my-hub"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/groups/remove-iam-policy-binding)

---
### `gcloud network-connectivity hubs groups set-iam-policy`

Set the IAM policy of a group resource

Replace the existing IAM policy of a group resource with a policy encoded
in a JSON or YAML file.

**Synopsis:**
```
gcloud network-connectivity hubs groups set-iam-policy (GROUP : --hub=HUB)
    POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Group resource - The hub for which to set the IAM policy. The arguments in
this group can be used to specify the attributes of this resource. (NOTE)
Some attributes are not given arguments in this group but can be set in
other ways.

To set the project attribute:
 * provide the argument group on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GROUP
     ID of the group or fully qualified identifier for the group.

     To set the group attribute:
     + provide the argument group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --hub=HUB
     Id of the hub.

     To set the hub attribute:
     + provide the argument group on the command line with a fully
       specified name;
     + provide the argument --hub on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
To replace the IAM policy of a group resource with the policy defined in a
file called policy.json, run:

    $ gcloud network-connectivity hubs groups set-iam-policy my-group \
        policy.json --hub="my-hub"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/groups/set-iam-policy)

---
### `gcloud network-connectivity hubs groups update`

Update a group

Update the details of a group.

**Synopsis:**
```
gcloud network-connectivity hubs groups update (GROUP : --hub=HUB)
    [--async] [--description=DESCRIPTION] [--update-labels=[KEY=VALUE,...]]
    [--add-auto-accept-projects=[AUTO-ACCEPT-PROJECTS,...]
      | --clear-auto-accept-projects
      | --remove-auto-accept-projects=[AUTO-ACCEPT-PROJECTS,...]]
    [--clear-labels | --remove-labels=[KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Group resource - Name of the group to update. The arguments in this group
can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument group on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  GROUP
     ID of the group or fully qualified identifier for the group.

     To set the group attribute:
     + provide the argument group on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --hub=HUB
     The hub Id.

     To set the hub attribute:
     + provide the argument group on the command line with a fully
       specified name;
     + provide the argument --hub on the command line.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | New description of the group. |
| `--update-labels` | [KEY=VALUE,...] |  | List of label KEY=VALUE pairs to update. If a label exists, its value is modified. Otherwise, a new label is created. Keys must start with a lowercase character and contain only hyphens (-), underscores (_), lowercase characters, and numbers. Values must contain only hyphens (-), underscores (_), lowercase characters, and numbers. |


**Examples:**
```bash
To update the description of a group named my-group, in the hub my-hub,
run:

    $ gcloud network-connectivity hubs groups update my-group \
        --hub=my-hub --description="new group description"

To add the project my-project to the auto-accept list of a group named
my-group in the hub my-hub, run:

    $ gcloud network-connectivity hubs groups update my-group \
        --hub=my-hub --add-auto-accept-projects=my-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/groups/update)

---

## `gcloud network-connectivity hubs route-tables` — manage Network Connectivity Center route tables
### `gcloud network-connectivity hubs route-tables describe`

Describe a route table

Retrieve and display details about a route table.

**Synopsis:**
```
gcloud network-connectivity hubs route-tables describe
    (ROUTE_TABLE : --hub=HUB) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Route table resource - Name of the route table to describe. The arguments
in this group can be used to specify the attributes of this resource.
(NOTE) Some attributes are not given arguments in this group but can be
set in other ways.

To set the project attribute:
 * provide the argument route_table on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTE_TABLE
     ID of the route table or fully qualified identifier for the route
     table.

     To set the route_table attribute:
     + provide the argument route_table on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --hub=HUB
     Id of the hub.

     To set the hub attribute:
     + provide the argument route_table on the command line with a fully
       specified name;
     + provide the argument --hub on the command line.
```

**Examples:**
```bash
To display details about a route table named my-route-table, run:

    $ gcloud network-connectivity hubs route-tables describe \
        my-route-table
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/route-tables/describe)

---
### `gcloud network-connectivity hubs route-tables list`

List route tables

Retrieve and display a list of all route tables in the specified hub.

**Synopsis:**
```
gcloud network-connectivity hubs route-tables list [--hub=HUB]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--hub` | HUB |  | _[* set the property core/project.]_ ID of the hub or fully qualified identifier for the hub. To set the hub attribute: + provide the argument --hub on the command line; + if hub is empty, will use the wildcard '-' to indicate all hubs. |


**Examples:**
```bash
To list all route tables across all hubs, run:

    $ gcloud network-connectivity hubs route-tables list --hub=-

To list all route tables in hub my-hub, run:

    $ gcloud network-connectivity hubs route-tables list --hub=my-hub
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/route-tables/list)

---

## `gcloud network-connectivity hubs route-tables routes` — manage Network Connectivity Center routes
### `gcloud network-connectivity hubs route-tables routes describe`

Describe a route

Retrieve and display details about a route.

**Synopsis:**
```
gcloud network-connectivity hubs route-tables routes describe
    (ROUTE : --hub=HUB --route_table=ROUTE_TABLE) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Route resource - Name of the route to describe. The arguments in this
group can be used to specify the attributes of this resource. (NOTE) Some
attributes are not given arguments in this group but can be set in other
ways.

To set the project attribute:
 * provide the argument route on the command line with a fully specified
   name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  ROUTE
     ID of the route or fully qualified identifier for the route.

     To set the route attribute:
     + provide the argument route on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --hub=HUB
     Id of the hub.

     To set the hub attribute:
     + provide the argument route on the command line with a fully
       specified name;
     + provide the argument --hub on the command line.

  --route_table=ROUTE_TABLE
     Id of the route table.

     To set the route_table attribute:
     + provide the argument route on the command line with a fully
       specified name;
     + provide the argument --route_table on the command line.
```

**Examples:**
```bash
To display details about a route named my-route, run:

    $ gcloud network-connectivity hubs route-tables routes describe \
        my-route
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/route-tables/routes/describe)

---
### `gcloud network-connectivity hubs route-tables routes list`

List routes

Retrieve and display a list of all routes in the specified route table.

**Synopsis:**
```
gcloud network-connectivity hubs route-tables routes list
    [--effective-location=EFFECTIVE_LOCATION]
    [--hub=HUB --route_table=ROUTE_TABLE] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--effective-location` | EFFECTIVE_LOCATION |  | The effective location/region to limit the list of routes. The effective location must be a valid region name. To list valid region names, use 'gcloud compute regions list'. |


**Examples:**
```bash
To list all routes across all route tables, run:

    $ gcloud network-connectivity hubs route-tables routes list \
        --hub=- --route_table=-

To list all routes in route table my-route-table, run:

    $ gcloud network-connectivity hubs route-tables routes list \
        --hub=my-hub --route_table=my-route-table

To list all routes in route table my-route-table, effective at a
location/region run:

    $ gcloud network-connectivity hubs route-tables routes list \
        --hub=my-hub --route_table=my-route-table \
        --effective-location=location
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/network-connectivity/hubs/route-tables/routes/list)

---