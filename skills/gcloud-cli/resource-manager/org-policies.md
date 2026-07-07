# gcloud resource-manager org-policies

manage Org Policies

### `gcloud resource-manager org-policies allow`

Add values to an Organization Policy allowed_values list policy

Adds one or more values to the specified Organization Policy allowed_values
list policy associated with the specified resource.

**Synopsis:**
```
gcloud resource-manager org-policies allow ORG_POLICY_ID ALLOWED_VALUE
    [ALLOWED_VALUE ...]
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORG_POLICY_ID
   The Org Policy constraint name.

ALLOWED_VALUE [ALLOWED_VALUE ...]
   The values to add to the allowed_values list policy.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Examples:**
```bash
The following command adds devEnv and prodEnv to an Organization Policy
allowed_values list policy for constraint serviceuser.services on project
foo-project:

    $ gcloud resource-manager org-policies allow serviceuser.services \
        --project=foo-project devEnv prodEnv
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/org-policies/allow)

---
### `gcloud resource-manager org-policies delete`

Delete an Organization Policy

Deletes an Organization Policy associated with the specified resource.

**Synopsis:**
```
gcloud resource-manager org-policies delete ORG_POLICY_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORG_POLICY_ID
   The Org Policy constraint name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Examples:**
```bash
The following command clears an Organization Policy for constraint
serviceuser.services on project foo-project:

    $ gcloud resource-manager org-policies delete serviceuser.services \
        --project=foo-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/org-policies/delete)

---
### `gcloud resource-manager org-policies deny`

Add values to an Organization Policy denied_values list policy

Adds one or more values to the specified Organization Policy denied_values
list policy associated with the specified resource.

**Synopsis:**
```
gcloud resource-manager org-policies deny ORG_POLICY_ID DENIED_VALUE
    [DENIED_VALUE ...]
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORG_POLICY_ID
   The Org Policy constraint name.

DENIED_VALUE [DENIED_VALUE ...]
   The values to add to the denied_values list policy.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Examples:**
```bash
The following command adds devEnv and prodEnv to an Organization Policy
denied_values list policy for constraint serviceuser.services on project
foo-project:

    $ gcloud resource-manager org-policies deny serviceuser.services \
        --project=foo-project devEnv prodEnv
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/org-policies/deny)

---
### `gcloud resource-manager org-policies describe`

Describe an Organization Policy

Describes an Organization Policy associated with the specified resource.

**Synopsis:**
```
gcloud resource-manager org-policies describe ORG_POLICY_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [--effective] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORG_POLICY_ID
   The Org Policy constraint name.
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
| `--effective` |  |  | Show the effective policy. |


**Examples:**
```bash
The following command retrieves an Organization Policy for constraint
serviceuser.services on project foo-project:

    $ gcloud resource-manager org-policies describe \
        serviceuser.services --project=foo-project

The following command retrieves the effective Organization Policy for
constraint serviceuser.services on project foo-project:

    $ gcloud resource-manager org-policies describe \
        serviceuser.services --project=foo-project --effective
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/org-policies/describe)

---
### `gcloud resource-manager org-policies disable-enforce`

Turns off enforcement of boolean Organization Policy constraint

Turns off enforcement of a boolean Organization Policy constraint at the
specified resource.

**Synopsis:**
```
gcloud resource-manager org-policies disable-enforce ORG_POLICY_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORG_POLICY_ID
   The Org Policy constraint name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Examples:**
```bash
The following command disables enforcement of the Organization Policy
boolean constraint compute.disableSerialPortAccess on project foo-project:

    $ gcloud resource-manager org-policies disable-enforce \
        compute.disableSerialPortAccess --project=foo-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/org-policies/disable-enforce)

---
### `gcloud resource-manager org-policies enable-enforce`

Turns on enforcement of boolean Organization Policy constraint

Turns on enforcement of a boolean Organization Policy constraint at the
specified resource.

**Synopsis:**
```
gcloud resource-manager org-policies enable-enforce ORG_POLICY_ID
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ORG_POLICY_ID
   The Org Policy constraint name.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Examples:**
```bash
The following command enables enforcement of the Organization Policy
boolean constraint compute.disableSerialPortAccess on project foo-project:

    $ gcloud resource-manager org-policies enable-enforce \
        compute.disableSerialPortAccess --project=foo-project
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/org-policies/enable-enforce)

---
### `gcloud resource-manager org-policies list`

List Organization Policies associated with the specified resource

**Synopsis:**
```
gcloud resource-manager org-policies list
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
| `--show-unset` |  |  | Show available constraints. For more information about constraints, see https://cloud.google.com/resource-manager/docs/organization-policy/understanding-constraints |


**Examples:**
```bash
The following command lists all set Organization Policies associated with
project foo-project:

    $ gcloud resource-manager org-policies list --project=foo-project

The following command lists all available constraints in addition to set
Organization Policies associated with project foo-project:

    $ gcloud resource-manager org-policies list --project=foo-project \
        --show-unset
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/org-policies/list)

---
### `gcloud resource-manager org-policies set-policy`

Set Organization Policy

Sets an Organization Policy associated with the specified resource from a
file that contains the JSON or YAML encoded Organization Policy.

**Synopsis:**
```
gcloud resource-manager org-policies set-policy POLICY_FILE
    (--folder=FOLDER_ID | --organization=ORGANIZATION_ID
      | --project=PROJECT_ID) [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_FILE
   JSON or YAML file with the Organization Policy.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--folder` | FOLDER_ID |  | _[Exactly one of these must be specified:]_ Folder ID. |
| `--organization` | ORGANIZATION_ID |  | _[Exactly one of these must be specified:]_ Organization ID. |
| `--project` | PROJECT_ID |  | _[Exactly one of these must be specified:]_ Project ID. Overrides the default core/project property value for this command invocation. |


**Examples:**
```bash
Organization policy list constraint YAML file example:

    constraint: constraints/CONSTRAINT_NAME
    listPolicy:
      deniedValues:
      - VALUE_A

Organization policy list constraint JSON file example:

    {
      "constraint": "constraints/CONSTRAINT_NAME",
      "listPolicy": {
        "deniedValues": ["VALUE_A"]
      }
    }

The following command sets an Organization Policy for a constraint on
project foo-project from file /tmp/policy.yaml:

    $ gcloud resource-manager org-policies set-policy \
        --project=foo-project /tmp/policy.yaml
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/resource-manager/org-policies/set-policy)

---