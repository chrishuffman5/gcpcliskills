# gcloud access-context-manager levels

manage Access Context Manager levels

### `gcloud access-context-manager levels create`

Create a new access level

Create a new access level in a given access policy.

**Synopsis:**
```
gcloud access-context-manager levels create (LEVEL : --policy=POLICY)
    --title=TITLE
    (--custom-level-spec=CUSTOM_LEVEL_SPEC
      | [--basic-level-spec=BASIC_LEVEL_SPEC
      : --combine-function=COMBINE_FUNCTION; default="and"]) [--async]
    [--description=DESCRIPTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Level resource - The access level to create. The arguments in this group
can be used to specify the attributes of this resource.

This must be specified.

  LEVEL
     ID of the level or fully qualified identifier for the level.

     To set the level attribute:
     + provide the argument level on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument level on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--title` | TITLE |  | Short human-readable title of the access level. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |
| `--description` | DESCRIPTION |  | Long-form description of access level. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/levels/create)

---
### `gcloud access-context-manager levels delete`

Delete an access level

Delete an access level in a given access policy.

**Synopsis:**
```
gcloud access-context-manager levels delete (LEVEL : --policy=POLICY)
    [--async] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Level resource - The access level you want to delete. The arguments in
this group can be used to specify the attributes of this resource.

This must be specified.

  LEVEL
     ID of the level or fully qualified identifier for the level.

     To set the level attribute:
     + provide the argument level on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument level on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--async` |  |  | Return immediately, without waiting for the operation in progress to complete. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/levels/delete)

---
### `gcloud access-context-manager levels describe`

Show details about an access level

Show details about an access level in a given access policy.

**Synopsis:**
```
gcloud access-context-manager levels describe (LEVEL : --policy=POLICY)
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Level resource - The access level you want to show details about. The
arguments in this group can be used to specify the attributes of this
resource.

This must be specified.

  LEVEL
     ID of the level or fully qualified identifier for the level.

     To set the level attribute:
     + provide the argument level on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument level on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Examples:**
```bash
To show the details of the access policy my-policy, run:

    $ gcloud access-context-manager levels describe my-policy
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/levels/describe)

---
### `gcloud access-context-manager levels list`

List access levels

List access levels.

**Synopsis:**
```
gcloud access-context-manager levels list [--policy=POLICY]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--policy` | POLICY |  | _[for. This represents a Cloud resource.]_ ID of the policy or fully qualified identifier for the policy. To set the policy attribute: + provide the argument --policy on the command line; + set the property access_context_manager/policy; + automatically, if the current account belongs to an organization with exactly one access policy.. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/levels/list)

---
### `gcloud access-context-manager levels replace-all`

Replace all existing access levels

Replace all existing access level in specified access policy with access
levels specified in a file.

**Synopsis:**
```
gcloud access-context-manager levels replace-all [POLICY]
    --source-file=SOURCE_FILE [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Policy resource - The access policy that contains the levels you want to
replace. This represents a Cloud resource.

  [POLICY]
     ID of the policy or fully qualified identifier for the policy.

     To set the policy attribute:
     + provide the argument policy on the command line;
     + set the property access_context_manager/policy;
     + automatically, if the current account belongs to an organization
       with exactly one access policy..
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--source-file` | SOURCE_FILE |  | Path to a file containing a list of access levels. An access level file is a YAML-formatted list of access levels, which are YAML objects representing a Basic or Custom level as described in the API reference. For example: - name: accessPolicies/my_policy/accessLevels/my_level title: My Basic Level description: Basic level for foo. basic: combiningFunction: AND conditions: - ipSubnetworks: - 192.168.100.14/24 - 2001:db8::/48 - members - user1:user1@example.com - name: accessPolicies/my_policy/accessLevels/my_other_level title: My Other Custom Level description: Custom level for bar. custom: expr: expression: "origin.region_code in ['US', 'CA']" For more information about the alpha version, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1alpha/accessPolicies.accessLevels For other versions, see: https://cloud.google.com/access-context-manager/docs/reference/rest/v1/accessPolicies.accessLevels |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | An etag which specifies the version of the Access Policy. Only etags that represent the latest version of the Access Policy will be accepted. |


**Examples:**
```bash
To replace all levels within a policy, using etag:

    $ gcloud access-context-manager levels replace-all \
        my-policy-number \
        --source-file=path-to-file-containing-all-replacement-access-lev\
    els.yaml --etag=optional-latest-etag-of-policy

To replace all levels within a policy, without using etag:

    $ gcloud access-context-manager levels replace-all \
        my-policy-number \
        --source-file=path-to-file-containing-all-replacement-access-lev\
    els.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/levels/replace-all)

---
### `gcloud access-context-manager levels update`

Update an existing access level

Update an existing access level.

**Synopsis:**
```
gcloud access-context-manager levels update (LEVEL : --policy=POLICY)
    [--description=DESCRIPTION] [--title=TITLE]
    [--custom-level-spec=CUSTOM_LEVEL_SPEC
      | --basic-level-spec=BASIC_LEVEL_SPEC
      --combine-function=COMBINE_FUNCTION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Level resource - The access level to update. The arguments in this group
can be used to specify the attributes of this resource.

This must be specified.

  LEVEL
     ID of the level or fully qualified identifier for the level.

     To set the level attribute:
     + provide the argument level on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --policy=POLICY
     The ID of the access policy.

     To set the policy attribute:
     + provide the argument level on the command line with a fully
       specified name;
     + provide the argument --policy on the command line;
     + set the property access_context_manager/policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--description` | DESCRIPTION |  | Long-form description of access level. |
| `--title` | TITLE |  | Short human-readable title of the access level. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/levels/update)

---

## `gcloud access-context-manager levels conditions` — manage Access Context Manager level conditions
### `gcloud access-context-manager levels conditions list`

List conditions for an access level

List conditions for a basic access level.

**Synopsis:**
```
gcloud access-context-manager levels conditions list
    (--level=LEVEL : --policy=POLICY) [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--level` | LEVEL |  | _[This must be specified.]_ ID of the level or fully qualified identifier for the level. To set the level attribute: + provide the argument --level on the command line. This flag argument must be specified if any of the other arguments in this group are specified. |
| `--policy` | POLICY |  | _[This must be specified.]_ The ID of the access policy. To set the policy attribute: + provide the argument --level on the command line with a fully specified name; + provide the argument --policy on the command line; + set the property access_context_manager/policy; + automatically, if the current account belongs to an organization with exactly one access policy.. |


[Official reference](https://cloud.google.com/sdk/gcloud/reference/access-context-manager/levels/conditions/list)

---