# gcloud access-context-manager authorized-orgs

manage Access Context Manager authorized organizations descriptions

### `gcloud access-context-manager authorized-orgs create`

Create a new authorized organizations description

Create a new authorized organizations description in a given access policy.

**Synopsis:**
```
gcloud access-context-manager authorized-orgs create
    (AUTHORIZED_ORGS_DESC : --policy=POLICY) --asset_type=ASSET_TYPE
    --authorization_direction=AUTHORIZATION_DIRECTION
    --authorization_type=AUTHORIZATION_TYPE [--async] [--orgs=[ORGS,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized orgs desc resource - The authorized organizations description
to create. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  AUTHORIZED_ORGS_DESC
     ID of the authorized-orgs-desc or fully qualified identifier for the
     authorized-orgs-desc.

     To set the authorized_orgs_desc attribute:
     + provide the argument authorized_orgs_desc on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument authorized_orgs_desc on the command line
       with a fully specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--asset` | one of: asset-type-credential-strength, asset-type-device, asset-type-unspecified |  | The asset type of this authorized organizations description. For example, device, or credential strength. ASSET_TYPE must be one of: asset-type-credential-strength, asset-type-device, asset-type-unspecified. |
| `--authorization` | one of: authorization-direction-from, authorization-direction-to, authorization-direction-unspecified |  | Authorization direction of this authorization relationship. Specifies whether to allow specified organizations to evaluate this organization's traffic, or allow specified organizations traffic to be evaluated by this org. AUTHORIZATION_DIRECTION must be one of: authorization-direction-from, authorization-direction-to, authorization-direction-unspecified. |
| `--authorization` | one of: authorization-type-trust, authorization-type-unspecified |  | The authorization type of the authorized organizations description. For example, trust, troubleshooting or logging. AUTHORIZATION_TYPE must be one of: authorization-type-trust, authorization-type-unspecified. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--orgs` | [ORGS,...] |  | Comma-separated list of organizations (in the following format: organizations/<organizationnumber>). |


**Examples:**
```bash
To create a new authorized organizations description:

    $ gcloud access-context-manager authorized-orgs create \
        --orgs=organizations/12345 --policy=9876543
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/authorized-orgs/create)

---
### `gcloud access-context-manager authorized-orgs delete`

Delete an authorized organizations description

Delete an authorized organizations description in a given access policy.

**Synopsis:**
```
gcloud access-context-manager authorized-orgs delete
    (AUTHORIZED_ORGS_DESC : --policy=POLICY) [--async]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized orgs desc resource - The authorized organizations description
you want to delete. The arguments in this group can be used to specify the
attributes of this resource.

This must be specified.

  AUTHORIZED_ORGS_DESC
     ID of the authorized-orgs-desc or fully qualified identifier for the
     authorized-orgs-desc.

     To set the authorized_orgs_desc attribute:
     + provide the argument authorized_orgs_desc on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument authorized_orgs_desc on the command line
       with a fully specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


**Examples:**
```bash
To delete an existing authorized organizations description, run:

    $ gcloud access-context-manager authorized-orgs delete \
        my_authorized_orgs_desc_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/authorized-orgs/delete)

---
### `gcloud access-context-manager authorized-orgs describe`

Show details about an authorized organizations description

Show details about an existing authorized organizations description.

**Synopsis:**
```
gcloud access-context-manager authorized-orgs describe
    (AUTHORIZED_ORGS_DESC : --policy=POLICY) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized orgs desc resource - The authorized organizations description
for which you want to show details. The arguments in this group can be
used to specify the attributes of this resource.

This must be specified.

  AUTHORIZED_ORGS_DESC
     ID of the authorized-orgs-desc or fully qualified identifier for the
     authorized-orgs-desc.

     To set the authorized_orgs_desc attribute:
     + provide the argument authorized_orgs_desc on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument authorized_orgs_desc on the command line
       with a fully specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Examples:**
```bash
To get details about an existing authorized organizations description, run:

    $ gcloud access-context-manager authorized-orgs describe \
        my_authorized_orgs_desc_id
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/authorized-orgs/describe)

---
### `gcloud access-context-manager authorized-orgs list`

List authorized organizations descriptions

List all authorized organizations descriptions in an access policy object.

**Synopsis:**
```
gcloud access-context-manager authorized-orgs list [--policy=POLICY]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy` | POLICY |  | _[Cloud resource.]_ ID of the policy or fully qualified identifier for the policy. To set the policy attribute: + provide the argument --policy on the command line; + set the property access_context_manager/policy; + automatically, if the current account belongs to an organization with exactly one access policy.. |


**Examples:**
```bash
To list authorized organizations description in an access policy, run:

    $ gcloud access-context-manager authorized-orgs list

This command prints out a list of authorized organizations descriptions in
a tabular form:

    NAME
    my_authorized_orgs_desc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/authorized-orgs/list)

---
### `gcloud access-context-manager authorized-orgs update`

Update the organizations for an existing authorized organizations description

This command updates an authorized organizations description.

**Synopsis:**
```
gcloud access-context-manager authorized-orgs update
    (AUTHORIZED_ORGS_DESC : --policy=POLICY)
    [--add-orgs=[ORGS,...] | --clear-orgs | --remove-orgs=[ORGS,...]
      | --set-orgs=[ORGS,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Authorized orgs desc resource - The authorized orgs desc to update. The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  AUTHORIZED_ORGS_DESC
     ID of the authorized_orgs_desc or fully qualified identifier for the
     authorized_orgs_desc.

     To set the authorized_orgs_desc attribute:
     + provide the argument authorized_orgs_desc on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument authorized_orgs_desc on the command line
       with a fully specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--add-orgs` | [ORGS,...] |  | _[At most one of these can be specified:]_ Append the given values to the current orgs. |
| `--clear-orgs` |  |  | _[At most one of these can be specified:]_ Empty the current orgs. |
| `--remove-orgs` | [ORGS,...] |  | _[At most one of these can be specified:]_ Remove the given values from the current orgs. |
| `--set-orgs` | [ORGS,...] |  | _[At most one of these can be specified:]_ Completely replace the current orgs with the given values. |


**Examples:**
```bash
To update the organizations for an authorized organizations description:

    $ gcloud access-context-manager authorized-orgs update \
        my-authorized-orgs \
        --add-orgs="organizations/123,organizations/456"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/authorized-orgs/update)

---