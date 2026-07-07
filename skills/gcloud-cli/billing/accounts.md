# gcloud billing accounts

manage billing accounts

### `gcloud billing accounts add-iam-policy-binding`

Add an IAM policy binding to a Cloud Billing account

Add an IAM policy binding to the IAM policy of a Cloud Billing account. A
binding consists of a member and a role.

**Synopsis:**
```
gcloud billing accounts add-iam-policy-binding ACCOUNT --member=PRINCIPAL
    --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Account resource - Name of the Cloud Billing account for which to add the
IAM policy binding. This represents a Cloud resource.

This must be specified.

  ACCOUNT
     ID of the account or fully qualified identifier for the account.

     To set the account attribute:
     + provide the argument account on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to add the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | Role name to assign to the principal. The role name is the complete path of a predefined role, such as roles/logging.viewer, or the role ID for a custom role, such as organizations/{ORGANIZATION_ID}/roles/logging.viewer. |


**Examples:**
```bash
To add someone@example.com as a Billing Account Administrator for billing
account 123456-789876-543210, run:

    $ gcloud billing accounts add-iam-policy-binding \
        123456-789876-543210 --member='user:someone@example.com' \
        --role='roles/billing.admin'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/accounts/add-iam-policy-binding)

---
### `gcloud billing accounts describe`

Show metadata for a billing account

This command shows info for a billing account, given its ID.

This call can fail for the following reasons:

  o The account specified does not exist.
  o The active user does not have permission to access the given account.

**Synopsis:**
```
gcloud billing accounts describe ACCOUNT_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
ACCOUNT_ID
   Specify a billing account ID. Billing account IDs are of the form
   0X0X0X-0X0X0X-0X0X0X. To see available IDs, run $ gcloud billing
   accounts list.
```

**Examples:**
```bash
To see details for billing account 0X0X0X-0X0X0X-0X0X0X, run:

    $ gcloud billing accounts describe 0X0X0X-0X0X0X-0X0X0X
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/accounts/describe)

---
### `gcloud billing accounts get-iam-policy`

Get the IAM policy for a Cloud Billing account

gcloud billing accounts get-iam-policy displays the IAM policy associated
with a Cloud Billing account. If formatted as JSON, the output can be
edited and used as a policy file for set-iam-policy. The output includes an
"etag" field identifying the version emitted and allowing detection of
concurrent policy updates; see $ {parent} set-iam-policy for additional
details.

**Synopsis:**
```
gcloud billing accounts get-iam-policy ACCOUNT [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Account resource - The Cloud Billing account for which to display the IAM
policy. This represents a Cloud resource.

This must be specified.

  ACCOUNT
     ID of the account or fully qualified identifier for the account.

     To set the account attribute:
     + provide the argument account on the command line.
```

**Examples:**
```bash
To print the IAM policy for a given Cloud Billing account, run:

    $ gcloud billing accounts get-iam-policy my-account
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/accounts/get-iam-policy)

---
### `gcloud billing accounts list`

List all active billing accounts

gcloud billing accounts list lists all billing accounts and subaccounts
owned by the currently authenticated user. Subaccounts have a non-empty
MASTER_ACCOUNT_ID value.

**Synopsis:**
```
gcloud billing accounts list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [--uri]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list only open billing accounts, run:

    $ gcloud billing accounts list --filter=open=true
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/accounts/list)

---
### `gcloud billing accounts remove-iam-policy-binding`

Remove an IAM policy binding from a Cloud Billing account

Remove an IAM policy binding to the IAM policy from a Cloud Billing
account. A binding consists of a member and a role.

**Synopsis:**
```
gcloud billing accounts remove-iam-policy-binding ACCOUNT
    --member=PRINCIPAL --role=ROLE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Account resource - Name of the Cloud Billing account for which to remove
the IAM policy binding. This represents a Cloud resource.

This must be specified.

  ACCOUNT
     ID of the account or fully qualified identifier for the account.

     To set the account attribute:
     + provide the argument account on the command line.
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--member` | PRINCIPAL |  | The principal to remove the binding for. Should be of the form user\|group\|serviceAccount:email or domain:domain. Examples: user:test-user@gmail.com, group:admins@example.com, serviceAccount:test123@example.domain.com, or domain:example.domain.com. Deleted principals have an additional deleted: prefix and a ?uid=UID suffix, where UID is a unique identifier for the principal. Example: deleted:user:test-user@gmail.com?uid=123456789012345678901. Some resources also accept the following special values: * allUsers - Special identifier that represents anyone who is on the internet, with or without a Google account. * allAuthenticatedUsers - Special identifier that represents anyone who is authenticated with a Google account or a service account. |
| `--role` | ROLE |  | The role to remove the principal from. |


**Examples:**
```bash
To remove someone@example.com as a Billing Account Administrator from
billing account 123456-789876-543210, run:

    $ gcloud billing accounts remove-iam-policy-binding \
        123456-789876-543210 --member='user:someone@example.com' \
        --role='roles/billing.admin'
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/accounts/remove-iam-policy-binding)

---
### `gcloud billing accounts set-iam-policy`

Set the IAM policy for a Cloud Billing account

gcloud billing accounts set-iam-policy sets the IAM policy for a Cloud
Billing account given an account ID and a JSON or YAML file that describes
the IAM policy.

Note: Setting the IAM policy for a Cloud Billing account replaces existing
IAM bindings for that account.

**Synopsis:**
```
gcloud billing accounts set-iam-policy ACCOUNT POLICY_FILE
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Account resource - The Cloud Billing account for which to display the IAM
policy. This represents a Cloud resource.

This must be specified.

  ACCOUNT
     ID of the account or fully qualified identifier for the account.

     To set the account attribute:
     + provide the argument account on the command line.

POLICY_FILE
   Path to a local JSON or YAML formatted file containing a valid policy.

   The output of the get-iam-policy command is a valid file, as is any
   JSON or YAML file conforming to the structure of a Policy
   (https://cloud.google.com/iam/reference/rest/v1/Policy).
```

**Examples:**
```bash
The following command reads an IAM policy defined in the JSON file
policy.json and sets it for a Billing account ID 123456-789876-543210:

    $ gcloud billing accounts set-iam-policy 123456-789876-543210 \
        policy.json

See https://cloud.google.com/iam/docs/managing-policies for policy file
format and content details.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/billing/accounts/set-iam-policy)

---