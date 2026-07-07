# gcloud org-policies (top-level commands)

### `gcloud org-policies delete`

Delete an organization policy

Deletes an organization policy.

**Synopsis:**
```
gcloud org-policies delete CONSTRAINT
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONSTRAINT
   Name of the org policy constraint. The list of available constraints
   can be found here:
   https://cloud.google.com/resource-manager/docs/organization-policy/org-policy-constraints
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | The current top-level etag of the Policy. If an etag is provided and does not match the current etag of the Policy, deletion will fail with a concurrent error. |


**Examples:**
```bash
To delete the policy associated with the constraint 'gcp.resourceLocations'
and the Project 'foo-project', run:

    $ gcloud org-policies delete gcp.resourceLocations \
        --project=foo-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/delete)

---
### `gcloud org-policies delete-custom-constraint`

Deletes a custom constraint

Deletes a custom constraint.

**Synopsis:**
```
gcloud org-policies delete-custom-constraint CUSTOM_CONSTRAINT
    --organization=ORGANIZATION_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CUSTOM_CONSTRAINT
   Name of the custom constraint.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION_ID |  | Organization ID. |


**Examples:**
```bash
To delete the custom constraint 'custom.myCustomConstraint' associated with
the Organization '1234', run:

    $ gcloud org-policies delete-custom-constraint \
        custom.myCustomConstraint --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/delete-custom-constraint)

---
### `gcloud org-policies describe`

Describe an organization policy

Describes an organization policy.

**Synopsis:**
```
gcloud org-policies describe CONSTRAINT
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--effective] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONSTRAINT
   Name of the org policy constraint. The list of available constraints
   can be found here:
   https://cloud.google.com/resource-manager/docs/organization-policy/org-policy-constraints
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--effective` |  |  | Describe the effective policy. |


**Examples:**
```bash
To describe the policy associated with the constraint
'gcp.resourceLocations' and the Project 'foo-project', run:

    $ gcloud org-policies describe gcp.resourceLocations \
        --project=foo-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/describe)

---
### `gcloud org-policies describe-custom-constraint`

Describe a custom constraint

Describes a custom constraint.

**Synopsis:**
```
gcloud org-policies describe-custom-constraint CUSTOM_CONSTRAINT
    --organization=ORGANIZATION_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CUSTOM_CONSTRAINT
   Name of the custom constraint.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION_ID |  | Organization ID. |


**Examples:**
```bash
To describe the custom constraint 'custom.myCustomConstraint' associated
with the Organization '1234', run:

    $ gcloud org-policies describe-custom-constraint \
        custom.myCustomConstraint --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/describe-custom-constraint)

---
### `gcloud org-policies list`

List the policies set on a resource

Lists the policies set on a resource.

**Synopsis:**
```
gcloud org-policies list
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--show-unset] [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--show-unset` |  |  | Show all available constraints for the resource. |


**Examples:**
```bash
To list the policies set on the Project 'foo-project', run:

    $ gcloud org-policies list --project=foo-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/list)

---
### `gcloud org-policies list-custom-constraints`

Lists the custom constraints set on an organization

Lists the custom constraints set on an organization.

**Synopsis:**
```
gcloud org-policies list-custom-constraints --organization=ORGANIZATION_ID
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [--uri] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--organization` | ORGANIZATION_ID |  | Organization ID. |


**Examples:**
```bash
To list the custom constraints set on the Organization '1234', run:

    $ gcloud org-policies list-custom-constraints --organization=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/list-custom-constraints)

---
### `gcloud org-policies reset`

Reset the policy to the default for the constraint

Resets the policy to the default for the constraint.

**Synopsis:**
```
gcloud org-policies reset CONSTRAINT
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--update-mask=UPDATE_MASK]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CONSTRAINT
   Name of the org policy constraint. The list of available constraints
   can be found here:
   https://cloud.google.com/resource-manager/docs/organization-policy/org-policy-constraints
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-mask` | UPDATE_MASK |  | Field mask used to specify the fields to be overwritten in the policy by the set. The fields specified in the update_mask are relative to the policy, not the full request. The update-mask flag can be empty, or have values policy.spec, policy.dry_run_spec or *. If the policy does not contain the dry_run_spec and update-mask flag is not provided, then it defaults to policy.spec. |


**Examples:**
```bash
To reset the policy associated with the constraint 'gcp.resourceLocations'
and the Project 'foo-project', run:

    $ gcloud org-policies reset gcp.resourceLocations \
        --project=foo-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/reset)

---
### `gcloud org-policies set-custom-constraint`

Set a custom constraint from a JSON or YAML file

Sets a Custom Constraint from a JSON or YAML file. The custom constraint
will be created if it does not exist, or updated if it already exists.

**Synopsis:**
```
gcloud org-policies set-custom-constraint CUSTOM_CONSTRAINT_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
CUSTOM_CONSTRAINT_FILE
   Path to JSON or YAML file that contains the organization policy.
```

**Examples:**
```bash
To set the custom constraint from the file on the path './sample_path',
run:

    $ gcloud org-policies set-custom-constraint ./sample_path
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/set-custom-constraint)

---
### `gcloud org-policies set-policy`

Set an organization policy from a JSON or YAML file

Sets an organization policy from a JSON or YAML file. The policy will be
created if it does not exist, or updated if it already exists.

**Synopsis:**
```
gcloud org-policies set-policy POLICY_FILE [--update-mask=UPDATE_MASK]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_FILE
   Path to JSON or YAML file that contains the organization policy.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--update-mask` | UPDATE_MASK |  | Field mask used to specify the fields to be overwritten in the policy by the set. The fields specified in the update_mask are relative to the policy, not the full request. The update-mask flag can be empty, or have values policy.spec, policy.dry_run_spec or *. If the policy does not contain the dry_run_spec and update-mask flag is not provided, then it defaults to policy.spec. |


**Examples:**
```bash
Organization policy list constraint YAML file example:

    name: projects/PROJECT_ID/policies/CONSTRAINT_NAME
    spec:
      rules:
      - values:
        denied_values:
        - VALUE_A

Organization policy list constraint JSON file example:

    {
      "name": "projects/PROJECT_ID/policies/CONSTRAINT_NAME",
      "spec": {
        "rules": [
          {
            "values": {
                "deniedValues": ["VALUE_A"]
            }
          }
        ]
      }
    }

To set the policy from the file on the path './sample_path', run:

    $ gcloud org-policies set-policy ./sample_path
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/org-policies/set-policy)

---