# gcloud iam policies

manage IAM deny policies

### `gcloud iam policies create`

Create a policy on the given attachment point with the given name

Create a policy on the given attachment point with the given name.

**Synopsis:**
```
gcloud iam policies create POLICY_ID --attachment-point=ATTACHMENT_POINT
    --kind=KIND --policy-file=POLICY_FILE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_ID
   Policy ID that is unique for the resource to which the policy is
   attached.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachment-point` | ATTACHMENT_POINT |  | Resource to which the policy is attached. For valid formats, see https://cloud.google.com/iam/help/deny/attachment-point. |
| `--kind` | KIND |  | Policy type. Use denypolicies for deny policies. |
| `--policy-file` | POLICY_FILE |  | Path to the file that contains the policy, in JSON or YAML format. For valid syntax, see https://cloud.google.com/iam/help/deny/policy-syntax. |


**Examples:**
```bash
The following command creates the IAM policy defined at the resource
project 123 of kind denypolicies and id my-deny-policy from the file
policy.json:

    $ gcloud iam policies create my-deny-policy \
        --attachment-point=cloudresourcemanager.googleapis.com/\
    projects/123 --kind=denypolicies --policy-file=policy.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policies/create)

---
### `gcloud iam policies delete`

Delete a policy on the given attachment point with the given name

Delete a policy on the given attachment point with the given name.

**Synopsis:**
```
gcloud iam policies delete POLICY_ID --attachment-point=ATTACHMENT_POINT
    --kind=KIND [--etag=ETAG] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_ID
   Policy ID that is unique for the resource to which the policy is
   attached.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachment-point` | ATTACHMENT_POINT |  | Resource to which the policy is attached. For valid formats, see https://cloud.google.com/iam/help/deny/attachment-point. |
| `--kind` | KIND |  | Policy type. Use denypolicies for deny policies. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Etag that identifies the version of the existing policy. It can be obtained by running gcloud iam policies get. When deleting a policy, if the etag is omitted, the policy is deleted regardless of its current etag. When updating a policy, if the etag is omitted, the update uses the etag provided in the policy file. |


**Examples:**
```bash
The following command deletes the IAM policy defined at the resource
project 123 of kind denypolicies and id my-deny-policy, with etag abc:

    $ gcloud iam policies delete my-deny-policy \
        --attachment-point=cloudresourcemanager.googleapis.com/\
    projects/123 --kind=denypolicies --etag=abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policies/delete)

---
### `gcloud iam policies get`

Get a policy on the given attachment point with the given name

Get a policy on the given attachment point with the given name.

**Synopsis:**
```
gcloud iam policies get POLICY_ID --attachment-point=ATTACHMENT_POINT
    --kind=KIND [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_ID
   Policy ID that is unique for the resource to which the policy is
   attached.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachment-point` | ATTACHMENT_POINT |  | Resource to which the policy is attached. For valid formats, see https://cloud.google.com/iam/help/deny/attachment-point. |
| `--kind` | KIND |  | Policy type. Use denypolicies for deny policies. |


**Examples:**
```bash
The following command gets the IAM policy defined at the resource project
123 of kind denypolicies and id my-deny-policy:

    $ gcloud iam policies get my-deny-policy \
        --attachment-point=cloudresourcemanager.googleapis.com/\
    projects/123 --kind=denypolicies
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policies/get)

---
### `gcloud iam policies list`

List the policies on the given attachment point

List the policies on the given attachment point.

**Synopsis:**
```
gcloud iam policies list --attachment-point=ATTACHMENT_POINT --kind=KIND
    [--page_token=PAGE_TOKEN] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachment-point` | ATTACHMENT_POINT |  | Resource to which the policy is attached. For valid formats, see https://cloud.google.com/iam/help/deny/attachment-point. |
| `--kind` | KIND |  | Policy type. Use denypolicies for deny policies. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--page` | PAGE_TOKEN |  | Page token received from a previous call. Provide this token to retrieve the next page. |


**Examples:**
```bash
The following command lists the IAM policy defined at the resource project
123 of kind denypolicies:

    $ gcloud iam policies list \
        --attachment-point=cloudresourcemanager.googleapis.com/\
    projects/123 --kind=denypolicies
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policies/list)

---
### `gcloud iam policies update`

Update the policy on the given attachment point with the given name

Update the policy on the given attachment point with the given name.

**Synopsis:**
```
gcloud iam policies update POLICY_ID --attachment-point=ATTACHMENT_POINT
    --kind=KIND --policy-file=POLICY_FILE [--etag=ETAG]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
POLICY_ID
   Policy ID that is unique for the resource to which the policy is
   attached.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--attachment-point` | ATTACHMENT_POINT |  | Resource to which the policy is attached. For valid formats, see https://cloud.google.com/iam/help/deny/attachment-point. |
| `--kind` | KIND |  | Policy type. Use denypolicies for deny policies. |
| `--policy-file` | POLICY_FILE |  | Path to the file that contains the policy, in JSON or YAML format. For valid syntax, see https://cloud.google.com/iam/help/deny/policy-syntax. |


**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--etag` | ETAG |  | Etag that identifies the version of the existing policy. It can be obtained by running gcloud iam policies get. When deleting a policy, if the etag is omitted, the policy is deleted regardless of its current etag. When updating a policy, if the etag is omitted, the update uses the etag provided in the policy file. |


**Examples:**
```bash
The following command updates the IAM policy my-deny-policy, which is
attached to the resource project 123 and has the etag abc:

    $ gcloud iam policies update my-deny-policy \
        --attachment-point=cloudresourcemanager.googleapis.com/\
    projects/123 --kind=denypolicies --policy-file=policy.json \
        --etag=abc
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/iam/policies/update)

---